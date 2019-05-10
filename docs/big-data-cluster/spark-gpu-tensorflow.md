---
title: Поддержка GPU и TensorFlow
titleSuffix: SQL Server big data clusters
description: Развертывание кластера больших данных с поддержкой GPU и использовать TensorFlow в записных книжках Studio данных Azure.
author: inchiosa
ms.author: marinch
ms.reviewer: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 2d31736ee4dd68857e3afce678b6dd806701a82b
ms.sourcegitcommit: d5cd4a5271df96804e9b1a27e440fb6fbfac1220
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64774955"
---
# <a name="deploy-a-big-data-cluster-with-gpu-support-and-run-tensorflow"></a>Развертывание кластера больших данных с поддержкой GPU и запустите TensorFlow

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье показано, как развернуть кластер больших данных в Azure Kubernetes Service (AKS), поддерживающий пулов узлов с поддержкой GPU для ресурсоемких рабочих нагрузок. После этого выполнить примеры записных книжек в Azure Data Studio, которые выполняют классификация изображений с помощью TensorFlow для графического Процессора.

## <a name="prerequisites"></a>предварительные требования

- [Средства работы с большими данными](deploy-big-data-tools.md):
  - **mssqlctl**
  - **kubectl**
  - **Azure Data Studio**
  - **Расширение SQL Server 2019**
  - **Azure CLI**

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="create-an-aks-cluster"></a>Создание кластера AKS

Далее используется Azure CLI для создания кластера AKS, поддерживающий графических процессоров.

1. В командной строке выполните следующую команду и следуйте инструкциям на экране, чтобы войти в свою подписку Azure:

    ```azurecli
    az login
    ```

1. Создайте группу ресурсов с помощью **Создание группы az** команды. В следующем примере создается группа ресурсов, с именем `sqlbigdatagroupgpu` в `eastus` расположение.

   ```azurecli
   az group create --name sqlbigdatagroupgpu --location eastus
   ```

1. Создание кластера Kubernetes в AKS при помощи [создать az aks](https://docs.microsoft.com/cli/azure/aks) команды. В следующем примере создается кластер Kubernetes с именем `gpucluster` в `sqlbigdatagroupgpu` группы ресурсов.

   ```azurecli
   az aks create --name gpucluster --resource-group sqlbigdatagroupgpu --generate-ssh-keys --node-vm-size Standard_NC6s_v3 --node-count 3 --node-osdisk-size 50 --kubernetes-version 1.11.9 --location eastus
   ```

   > [!NOTE]
   > Этот кластер использует **Standard_NC6s_v3** [размер виртуальной машины, оптимизированных для GPU](https://docs.microsoft.com/azure/virtual-machines/linux/sizes-gpu), которая является одной из специализированные виртуальные машины с одним или несколькими графическими процессорами NVIDIA. Дополнительные сведения см. в разделе [использования GPU для интенсивных вычислительных рабочих нагрузок в службе Azure Kubernetes (AKS)](https://docs.microsoft.com/azure/aks/gpu-cluster).

1. Чтобы настроить kubectl для подключения к кластеру Kubernetes, выполните [az aks get-credentials](https://docs.microsoft.com/cli/azure/aks?view=azure-cli-latest#az-aks-get-credentials) команды.

   ```azurecli
   az aks get-credentials --overwrite-existing --resource-group=sqlbigdatagroupgpu --name gpucluster
   ```

## <a name="apply-yaml-manifest"></a>Применить манифест YAML

1. Используйте **kubectl** создать пространство имен Kubernetes с именем `gpu-resources`.

   ```bash
   kubectl create namespace gpu-resources
   ```

1. Сохраните содержимое ниже yaml-файл в файл с именем **nvidia устройства plugin-ds.yaml**. Сохраните файл в рабочий каталог на компьютере, на которых запущена **kubectl** из.

   Обновление `image: nvidia/k8s-device-plugin:1.11` посередине вниз манифест, подлежащий соответствует вашей версии Kubernetes. Например, при запуске кластера AKS Kubernetes версии 1.12 обновить тег, который `image: nvidia/k8s-device-plugin:1.12`.

   ```yaml
   apiVersion: extensions/v1beta1
   kind: DaemonSet
   metadata:
     labels:
       kubernetes.io/cluster-service: "true"
     name: nvidia-device-plugin
     namespace: gpu-resources
   spec:
     template:
       metadata:
         # Mark this pod as a critical add-on; when enabled, the critical add-on scheduler
         # reserves resources for critical add-on pods so that they can be rescheduled after
         # a failure.  This annotation works in tandem with the toleration below.
         annotations:
           scheduler.alpha.kubernetes.io/critical-pod: ""
         labels:
           name: nvidia-device-plugin-ds
       spec:
         tolerations:
         # Allow this pod to be rescheduled while the node is in "critical add-ons only" mode.
         # This, along with the annotation above marks this pod as a critical add-on.
         - key: CriticalAddonsOnly
           operator: Exists
         containers:
         - image: nvidia/k8s-device-plugin:1.11 # Update this tag to match your Kubernetes version
           name: nvidia-device-plugin-ctr
           securityContext:
             allowPrivilegeEscalation: false
             capabilities:
               drop: ["ALL"]
           volumeMounts:
             - name: device-plugin
               mountPath: /var/lib/kubelet/device-plugins
         volumes:
           - name: device-plugin
             hostPath:
               path: /var/lib/kubelet/device-plugins
         nodeSelector:
           beta.kubernetes.io/os: linux
           accelerator: nvidia
   ```

1. Сейчас использование kubectl apply команду, чтобы создать DaemonSet. **NVIDIA устройства plugin-ds.yaml** должно быть в рабочем каталоге, когда вы выполните следующую команду:

   ```bash
   kubectl apply -f nvidia-device-plugin-ds.yaml
   ```

## <a name="deploy-the-big-data-cluster"></a>Развертывание кластера больших данных

Для развертывания кластера больших данных SQL Server 2019 (Предварительная версия), который поддерживает графические процессоры, необходимо развернуть из реестра определенные docker и репозиторий. Следующие переменные среды отличаются для развертывания GPU:

| Переменная среды | Значение |
|---|---|
| **DOCKER_REGISTRY** | `marinchcreus3.azurecr.io` |
| **DOCKER_REPOSITORY** | `ctp25-8-0-61-gpu` |
| **DOCKER_USERNAME** | `<your username, gpu-specific credentials provided by Microsoft>` |
| **DOCKER_PASSWORD** | `<your password, gpu-specific credentials provided by Microsoft>` |

Используйте **mssqlctl** для развертывания кластера, выберите конфигурацию aks-dev-test.json и поставок, настраиваемые значения выше, при появлении запроса.

```bash
mssqlctl cluster create
```

> [!TIP]
> Имя по умолчанию кластера больших данных — `mssql-cluster`.

Также можно настроить дополнительные развертывания, передав файл конфигурации развертывания. Дополнительные сведения см. в разделе [руководство по развертыванию](deployment-guidance.md#customconfig).

## <a name="run-the-tensorflow-example"></a>Запустите пример TensorFlow

Следующие два примеры записных книжек демонстрируются две модели классификации изображений обучения на одном узле кластера Spark с помощью TensorFlow для графического Процессора.

| Скачивание записной книжки | Описание |
|---|---|
| [**tf-cuda8.ipynb**](https://aka.ms/AA4jdgd) | Использует CUDA 8, CUDNN 6 и TensorFlow 1.4.0.  |
| [**tf-cuda9.ipynb**](https://aka.ms/AA4ixzr) | Использует CUDA 9, CUDNN 7 и TensorFlow 1.12.0. |

Поместите файл соответствующие записной книжки на локальный компьютер и затем откройте и запустите его в Azure Data Studio, используя ядро PySpark3. Если у вас нет необходимости в более старой версии CUDA или TensorFlow, выберите CUDA 9 и CUDNN 7/TensorFlow 1.12.0. Дополнительные сведения о том, как использовать записные книжки с кластерами больших данных, см. в разделе [использованию записных книжек в предварительной версии SQL Server 2019](notebooks-guidance.md).

> [!NOTE]
> Обратите внимание на то, что записные книжки установки программного обеспечения в системе. Это возможно, так как записные книжки в настоящее время работает с правами привилегированного пользователя в CTP-версии 2.5.

После установки библиотеки графического Процессора NVIDIA и TensorFlow для графического Процессора, записные книжки список доступных устройств GPU. Затем они помещаются и оценить модель TensorFlow для распознавания рукописных цифр, с помощью набора данных MNIST. После проверки доступного пространства на диске, они скачайте и запустите пример классификации изображений CIFAR 10 из [ https://github.com/tensorflow/models.git ](https://github.com/tensorflow/models.git). Выполнив пример CIFAR 10 на кластерах со разных GPU, можно наблюдать за увеличения скорости, предлагаемых каждого поколения GPU, доступных в Azure.

## <a name="clean-up-resources"></a>Очистка ресурсов

Чтобы удалить кластер больших данных, используйте следующую команду:

```bash
mssqlctl cluster delete --name gpubigdatacluster
```

Предыдущая команда не удаляет кластер AKS. Чтобы удалить кластер AKS и связанные с ней ресурсы, используйте следующую команду:

```azurecli
az group delete -n sqlbigdatagroupgpu
```

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах SQL Server 2019 больших данных (Предварительная версия) см. в разделе [Каковы кластеров SQL Server 2019 больших данных?](big-data-cluster-overview.md).
