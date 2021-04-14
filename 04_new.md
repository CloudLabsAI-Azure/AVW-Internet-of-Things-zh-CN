# ��ϰ 4��Azure IoT Edge ����

## Ӧ�ó���

���Ŵ����豸�Ĳ��𣬴������������ռ������͵��ƶˡ��Ƿ��п��ܽ��������� Edge��

Fabrikam, Inc. ϣ��ʹ�� IoT Edge �����豸����һЩ���������Ե���ڽ��м�ʱ����һ���������Խ����͵��ƶˡ��������������� IoT Edge ������ȷ�����Ǽ�ʹ�ڱ�������ܲ������£�Ҳ�ܹ��������ݲ�Ѹ��������Ӧ��

��������ǽ��� Azure IoT Edge ���������ԭ����ơ����ȣ��㽫���豸����һ��������ģ�飬���ڼ���ƽ���¶ȣ����ڳ������̿���ֵʱ���ɾ���֪ͨ��

## ����

�ڴ���ϰ�У��㽫�� Edge �豸����һ��������ģ�飬���ڳ������̿���ֵʱ���ɾ���֪ͨ������Ϊ���ṩ��Ԥ�����Ļ��� Linux �� Azure VM������������Ϊ���ڱ�ʵ���ҵ� IoT Edge �豸��

�ڴ���ϰ�У��㽫�����������

* ���ӵ� IoT Edge VM
* �� Edge �豸��� Edge ģ��
* �� Azure ������ Edge ģ�鲿�� Edge �豸

Azure IoT Edge�����������е��Ʒ�������豸�ϳ��������ʱ�����ϡ�����ʱ�����������豸�ϵĹ�����������������һ����������Щ�������ض�˳��������һ���Դ����˵��˷�����IoT Edge �� IoT ���Ĺ���Azure IoT Edge ʹ���ܹ��ڱ�Ե�豸�����й������ɣ���Щ����������ʹ���Ʒ��񿪷��ġ�����������ʹ���� docker ���ݵ����������ģ�顣��Щģ��������˹�����Ӧ�ó���Azure ����͵���������Ҳ������ҵ���߼����й� IoT Edge ����ϸ��Ϣ���ɵ������������ӣ�```https://docs.microsoft.com/en-us/azure/iot-edge/about-iot-edge```

## ���������ϵ�ṹ
 
  ![ʵ���� 04 ��ϵ�ṹ](media/lab4_architecture.png)

### ���� 1�����ӵ� IoT Edge VM

�ڴ������У��㽫���ӵ� IoT Edge VM������֤ Azure IoT Edge �Ƿ������豸�����С�

1. �� Azure �Ż��˵��ϣ�����**����Դ�顱**��
 
1. ��**��iot-{deployment-id}��**��Դ���У����� IoT Edge �����**��linuxagentvm-{deployment-id}��**��

1. ��**��������**���񶥲�������**�����ӡ�**��Ȼ�󵥻�**��SSH��**��

1. ��**�����ӡ�**�����еġ�**4.��������ʾ�����������ӵ���� VM��**�£�����ʾ�����

    ����һ�������������������ʾ�� SSH ������а��� VM �� IP ��ַ�͹���Ա�û�����������ĸ�ʽӦ������ `ssh demouser@52.170.205.79`��

    > **��ע**���㸴�Ƶ�ʾ��������� **-i <private key path>**����ʹ���ı��༭��ɾ���ⲿ�����Ȼ�󽫸��º������Ƶ������塣
 
1. ͨ�������� **```https://shell.azure.com```** ��ѡ��**��Bash��**�� Azure Cloud Shell��

1. ����**����ʾ�߼����á�**��Ȼ���ṩ������ϸ��Ϣ��

   * ��Դ�飺ѡ��**��ʹ�����С�**->**��iot-{deployment-id}��**
   * �洢�ʻ���ѡ��**���½���**������**��cloudstore{deployment-id}��**
   * �ļ�����ѡ��**���½���**������**��blob��**
   
     >   **��ע**��- �ɴӻ�����ϸ��Ϣҳ���ȡ **deployment-id** ��ϸ��Ϣ��
        
   ![Azure �Ż���Ļ��ͼ����ʾ���ڴ����洢�ʻ���ѡ��·����](media/storageaccount01.png)

1. �� Azure Cloud Shell ������ʾ������ճ�������ı��༭���и��µ� `ssh` ���Ȼ�� **Enter**��

1. ��ϵͳ��ʾ**���Ƿ�ȷʵҪ��������?��**ʱ�������� `yes` ���� **Enter**��

1. ��ϵͳ��ʾ��������ʱ��������**��Password.1!!��**���� **Enter**��

   ![�������ӵ� linuxagent �������](media/vmlogin.png)

1. ���Ӻ��ն�������ʾ������Ϊ��ʾ Linux VM �����ƣ�����������ʾ��

    ```cmd/sh
    demouser@linuxagentvm-{deployment-id}:~$
    ```

    �⽫ָ���������ӵ��ĸ� VM��

    > **��Ҫ˵����**������ʱ��ϵͳ���ܻ���ʾ Edge VM �� OS δ��ɸ��¡�  �ڱ�ʵ�����У����ǽ����Ը���ʾ�����������У���ʼ��ȷ�� Edge �豸��������״̬��

1. Ҫȷ������ VM �ϰ�װ Azure IoT Edge ����ʱ���������������

    ```cmd/sh
    iotedge version
    ```

    ���������������ϵ�ǰ��װ�� Azure IoT Edge ����ʱ�汾��
    IoT Edge �豸���Ѱ�װ IoT Edge ����ʱ��IoT Edge ����ʱ��һ�����򼯺ϣ����Խ��豸ת��Ϊ IoT Edge �豸���� IoT Edge ����ʱ����Ĺ�ͬ�����£�IoT Edge �豸���Խ���Ҫ�ڱ�Ե�����еĴ��룬���� IoT ���Ĵ��ݽ����

### ���� 2���� Edge �豸��� Edge ģ��

�ڴ���ϰ�У��㽫���һ��ģ���¶ȴ�������Ϊ�Զ��� IoT Edge ģ�飬�����䲿�� IoT Edge �豸�����С�

IoT Edge ģ������������ʽʵ�ֵĿ�ִ�г������

ͨ�� IoT Edge ģ�飬���Խ��ƹ������ɲ��� IoT �豸��ֱ�����С�IoT Edge ģ������ IoT Edge �������С���㵥Ԫ��ʹ�� IoT Edge ģ�飬�������豸�ϣ��������У��������ݡ�ͨ�������ֹ�������ת�Ƶ���Ե������豸���Ի����ٵ�ʱ�����Ʒ�����Ϣ��������ض��¼�������Ӧ��

1. ���б�Ҫ����ʹ����� Azure �ʻ�ƾ�ݵ�¼ Azure �Ż���
 
1. ����Դ������ϣ�����**��iothub-{deployment-id}��**���Դ� IoT ���ġ�

1. ��**��IoT ���ġ�**����ѡ���࣬����**���Զ��豸����**�µ�**��IoT Edge��**��

1. �ڡ�IoT Edge �豸���б��У�����**��turbine-06��**��

1. ��**��turbine-06��**����ѡ��ϣ�ע��**��ģ�顱**ѡ���ʾ�˵�ǰΪ���豸���õ�ģ���б�

    Ŀǰ���� IoT Edge �豸ֻ������ Edge ���� (`$edgeAgent`) ģ��� Edge ���� (`$edgeHub`) ģ�飬��Щģ���� IoT Edge ����ʱ��һ���֡�

1. ��**��turbine-06��**����ѡ�����������**������ģ�顱**��

1. ��**�����豸 turbine-06 ������ģ�顱**����ѡ��ϣ��ҵ�**��IoT Edge ģ�顱**���֡�

1. ��**��IoT Edge ģ�顱**�µ���**����ӡ�**��Ȼ�󵥻�**��IoT Edge ģ�顱**��

1. ��**����� IoT Edge ģ�顱**�����У���**��IoT Edge ģ�����ơ�**������**��turbinesensor��**

    ���ǽ��Զ���ģ������Ϊ��turbinesensor��

1. ��**��ӳ�� URI��**�£�����**��asaedgedockerhubtest/asa-edge-test-module:simulated-temperature-sensor��**

    > **��ע**����ӳ���� Docker Hub �ϵ��ѷ���ӳ���ɲ�Ʒ���ṩ����֧�ִ˲��Գ�����

1. Ҫ������ѡѡ����뵥��**��ģ���������á�**��

1. ҪΪģ������ָ���������ԣ����������� JSON��

    ```json
    {
        "EnableProtobufSerializer": false,
        "EventGeneratingSettings": {
            "IntervalMilliSec": 500,
            "PercentageChange": 2,
            "SpikeFactor": 2,
            "StartValue": 68,
            "SpikeFrequency": 20
        }
    }
    ```

    �� JSON ͨ������ Edge ģ���ģ�������������������� Edge ģ�顣

1. �ڱ���ѡ��ײ�������**����ӡ�**��

1. ��**�����豸 turbine-06 ������ģ�顱**����ѡ��ײ�������**����һ��: ·�� >��**��

1. ���Կ�����������һ��Ĭ��·�ɡ�

    * ���ƣ�**route**
    * ֵ��`FROM /messages/* INTO $upstream`

    ��·�ɽ������� IoT Edge �豸������ģ���������Ϣ���͵� IoT ����

1. ����**���鿴 + ������**��

1. ��**������**�£���һ���Ӳ鿴��ʾ�Ĳ����嵥�� 

    ���Կ�����IoT Edge �豸�Ĳ����嵥ʹ�� JSON ��ʽ����ʹ��ǳ������Ķ���

    `properties.desired` �����µ� `modules` ���������˽����� IoT Edge �豸�� IoT Edge ģ�顣���������ģ���ӳ�� URI�������κ�����ע���ƾ�ݡ�

    ```json
    {
        "modulesContent": {
            "$edgeAgent": {
                "properties.desired": {
                    "modules": {
                        "turbinesensor": {
                            "settings": {
                                "image": "asaedgedockerhubtest/asa-edge-test-module:simulated-temperature-sensor",
                                "createOptions": ""
                            },
                            "type": "docker",
                            "version": "1.0",
                            "status": "running",
                            "restartPolicy": "always"
                        },
    ```

    JSON ���·��� **$edgeHub** ���֣����а��� Edge ���ĵ��������ԡ��˲��ֻ�����ģ���͵� IoT ���ĵ��¼�·�ɵ�·�����á�

    ```json
        "$edgeHub": {
            "properties.desired": {
                "routes": {
                  "route": "FROM /messages/* INTO $upstream"
                },
                "schemaVersion": "1.0",
                "storeAndForwardConfiguration": {
                    "timeToLiveSecs": 7200
                }
            }
        },
    ```

    JSON ���������Ƕ�Ӧ **turbinesensor** ģ��Ĳ��֣����� `properties.desired` ���ְ����˱�Եģ�����õ��������ԡ�

    ```json
                },
                "turbinesensor": {
                    "properties.desired": {
                        "EnableProtobufSerializer": false,
                        "EventGeneratingSettings": {
                            "IntervalMilliSec": 500,
                            "PercentageChange": 2,
                            "SpikeFactor": 2,
                            "StartValue": 68,
                            "SpikeFrequency": 20
                        }
                    }
                }
            }
        }
    ```

1. Ҫ����豸ģ������ã��뵥������ѡ��ײ���**��������**��

1. ��**��turbine-06��**����ѡ��е�**��ģ�顱**�£�ע��**��turbinesensor��**�����г���

    > **��ע**�����ܱ��뵥��**��ˢ�¡�**���ܵ�һ�ο�����ģ���г���

    �����ע�⵽��δ���� **turbinesensor** ������ʱ״̬��

1. �ڱ���ѡ�����������**��ˢ�¡�**��

1. ���Կ��� **turbinesensor** ģ���**������ʱ״̬��**��������Ϊ**���������С�**��

    �����δ�����ֵ�����Ե�һ�£�Ȼ���ٴ�ˢ�±���ѡ���
 
1. ��һ�� Cloud Shell �Ự�������δ�򿪣���

    ����������ӵ� `vm-iot-edge-{deployment-id}` �������������ǰһ��ʹ�� **SSH** ���ӡ�

1. Ҫ�г���ǰ�� IoT Edge �豸�����е�ģ�飬���� Cloud Shell ������ʾ���������������

    ```cmd/sh
    iotedge list
    ```

1. ��������������������ʾ�� 

    ```cmd/sh
    demouser@linuxagentvm-{deployment-id}:~$ iotedge list
    NAME             STATUS           DESCRIPTION      CONFIG
    edgeHub          running          Up a minute      mcr.microsoft.com/azureiotedge-hub:1.0
    edgeAgent        running          Up 26 minutes    mcr.microsoft.com/azureiotedge-agent:1.0
    turbinesensor    running          Up 34 seconds    asaedgedockerhubtest/asa-edge-test-module:simulated-temperature-sensor
    ```

    ��ע�⣬`turbinesensor` ��Ϊ�������е�ģ��֮һ�г���

1. Ҫ�鿴ģ����־���������������

    ```cmd/sh
    iotedge logs turbinesensor
    ```

    ��������������������ʾ��

    ```cmd/sh
    demouser@linuxagentvm-{deployment-id}:~$ iotedge logs turbinesensor
    11/14/2019 18:05:02 - Send Json Event : {"machine":{"temperature":41.199999999999925,"pressure":1.0182182583425192},"ambient":{"temperature":21.460937846433808,"humidity":25},"timeCreated":"2019-11-14T18:05:02.8765526Z"}
    11/14/2019 18:05:03 - Send Json Event : {"machine":{"temperature":41.599999999999923,"pressure":1.0185790159334602},"ambient":{"temperature":20.51992724976499,"humidity":26},"timeCreated":"2019-11-14T18:05:03.3789786Z"}
    11/14/2019 18:05:03 - Send Json Event : {"machine":{"temperature":41.999999999999922,"pressure":1.0189397735244012},"ambient":{"temperature":20.715225311096397,"humidity":26},"timeCreated":"2019-11-14T18:05:03.8811372Z"}
    ```

    `iotedge logs` �������ڲ鿴�κ� Edge ģ���ģ����־��

1. ģ���¶ȴ�����ģ�齫�ڷ��� 500 ����Ϣ��ֹͣ���С���ͨ���������������������

    ```cmd/sh
    iotedge restart turbinesensor
    ```

    ���ڲ���Ҫ������ģ�飬��������Ժ�����ֹͣ����ң�⣬��ô�뷵�� Cloud Shell��ͨ�� SSH ���ӵ� Edge VM��Ȼ�����д����������������ú󣬸�ģ�齫�ٴο�ʼ����ң�⡣

### ���� 3���� IoT Edge ģ�����ʽ���� Azure ������

���ڣ�**turbinesensor** ģ������ IoT Edge �豸�ϲ�������У����ǿ������һ��������ģ�飬������ IoT Edge �豸�ϴ�����Ϣ��Ȼ���ٽ���Ϣ���͵� IoT ���ġ�

#### �����������ҵ

1. ����Դ������У�����**��iot-{deployment-id}��**��ѡ����������ҵ**��iotedge-streamjob-{deployment-id}��**��

1. Ȼ���ڱ���ѡ�����**����ҵ���ˡ�**�£�ѡ��**�����롱**������֤�Ƿ�����Ѷ����������ҵ**��temperature��**��

1. Ȼ����**����ҵ���ˡ�**��ѡ��**�������**������֤�Ƿ�����Ѷ���������ҵ**��alert��**��

1. ��**�����á�**�µ���ർ���˵��У��������洢�ʻ����á���Ȼ��ȷ������Ӵ洢�ʻ� otstorage{deployment-id}��

#### ������������ҵ

1. �� Azure �Ż��У�������**��iothub-{deployment-id}��**IoT ������Դ��

1. ����ർ���˵���**���Զ��豸����**�£�����**��IoT Edge��**��

1. ��**���豸 ID��**�£�����**��turbine-06��**��

1. ��**��turbine-06��**���񶥲�������**������ģ�顱**��

1. ��**�����豸 turbine-06 ������ģ�顱**�����У��ҵ�**��IoT Edge ģ�顱**���֡�

1. ��**��IoT Edge ģ�顱**�µ���**����ӡ�**��Ȼ�󵥻�**��Azure ������ģ�顱**��

1. ��**��Edge ����**�����е�**�����ġ�**�£�ȷ��ѡ�����ڱ��γ���ʹ�õĶ��ġ�

1. ��**��Edge ��ҵ��**�����б��У�ȷ��ѡ��**��iotedge-streamjob-{deployment-id}��**��������ҵ��

    > **��ע**�����ܴ����Ѿ�ѡ����ҵ����**�����桱**��ť���ڽ���״̬���������ʱ�����ٴδ�**��Edge ��ҵ��**�����б����ٴ�ѡ��**��iotedge-streamjob-{deployment-id}��** ��ҵ��Ȼ��**�����桱**��ťӦ�þͻ��Ϊ����״̬��

1. �ڴ���ײ�������**�����桱**��

    ���������ҪһЩʱ�䡣

1. ���豸��**����ģ��ĵײ������ֻ�-06** ��Ƭ�����**�鿴 + ����**��

1. ��**�鿴 + ����**��ǩ�ϣ�ע��**�����嵥** JSON ���Ѹ��°� Stream Analytics ģ��͸����õ�·�ɶ�����и��¡�

1. �ڵ�Ƭ�ײ����**����**��

1. ��ע�⣬Edge ������ɹ��������µ� ASA ģ�齫��**��IoT Edge ģ�顱**�������г�

1. ��**��IoT Edge ģ�顱**�£�����**��iotedge-streamjob-{deployment-id}��**��

    ���Ǹո���ӵ� Edge �豸��������ģ�顣

1. ��**������ IoT Edge ģ�顱**�����У���ע��**��ӳ�� URI��**ָ��һ����׼ Azure ������ӳ��

    ```text
    mcr.microsoft.com/azure-stream-analytics/azureiotedge:1.0.7
    ```

    ���ǲ��� IoT Edge �豸�ϵ�ÿһ�� ASA ��ҵ��ʹ�õ�ͬһӳ��

    > **��ע**��  ���õ�**ӳ�� URI** ĩβ�İ汾�Ž���ӳ����������ģ��ʱ�ĵ�ǰ���°汾��

1. ��������Ĭ��ֵ��Ȼ��ر�**��IoT Edge �Զ���ģ�顱**����

1. ��**�����豸 turbine-06 ������ģ�顱**�����У�����**����һ��: ·�� >��**��

    ���Կ�����ʾ������·�ɡ�

1. �������Ĭ��·���滻Ϊ��������·�ɣ�
   
   > **��ע**��ȷ���� `iotstreamjob-edge-{deployment-id}` ռλ���滻Ϊ Azure ��������ҵģ������ơ�
   
    * ·�� 1
        * ���ƣ�**telemetryToCloud**
        * ֵ��`FROM /messages/modules/turbinesensor/* INTO $upstream`
    * ·�� 2
        * ���ƣ�**alertsToReset**
        * ֵ��`FROM /messages/modules/iotedge-streamjob-{deployment-id}/* INTO BrokeredEndpoint("/modules/turbinesensor/inputs/control")`
    * ·�� 3
        * ���ƣ�**telemetryToAsa**
        * ֵ��`FROM /messages/modules/turbinesensor/* INTO BrokeredEndpoint("/modules/iotedge-streamjob-{deployment-id}/inputs/temperature")`

    > **��ע**�����Ե���**����һ����**�鿴ģ�鼰�����Ƶ��б�Ȼ�󵥻�**����һ����**���ص��˲��衣

    �������·�����£�

    * **telemetryToCloud** ·�ɽ����� `turbinesensor` ģ�������������Ϣ���͵� Azure IoT ���ġ�
    * **alertsToReset** ·�ɽ�����������ģ����������о�����Ϣ���͵� **turbinesensor** ģ������롣
    * **telemetryToAsa** ·�ɽ����� `turbinesensor` ģ�������������Ϣ���͵�������ģ�����롣

1. ���豸��**����ģ��ĵײ������ֻ�-06** ��Ƭ�����**�鿴 + ����**��

1. ��**�鿴 + ����**��ǩ�ϣ�ע��**�����嵥** JSON ���Ѹ��°� Stream Analytics ģ��͸����õ�·�ɶ�����и��¡�

1. ע�� `turbinesensor` ģ���¶ȴ�����ģ��� JSON ���ã�

    ```json
    "turbinesensor": {
        "settings": {
            "image": "asaedgedockerhubtest/asa-edge-test-module:simulated-temperature-sensor",
            "createOptions": ""
        },
        "type": "docker",
        "version": "1.0",
        "status": "running",
        "restartPolicy": "always"
    },
    ```

1. ע��֮ǰ���õ�·�ɵ� JSON ���ã��Լ���Щ·���� JSON �������е����÷�ʽ��

    ```json
    "$edgeHub": {
        "properties.desired": {
            "routes": {
                "telemetryToCloud": "FROM /messages/modules/turbinesensor/* INTO $upstream",
                "alertsToReset": "FROM /messages/modules/iotedge-streamjob-{deployment-id}/* INTO BrokeredEndpoint(\\\"/modules/turbinesensor/inputs/control\\\")",
                "telemetryToAsa": "FROM /messages/modules/turbinesensor/* INTO BrokeredEndpoint(\\\"/modules/iotedge-streamjob-{deployment-id}/inputs/temperature\\\")"
            },
            "schemaVersion": "1.0",
            "storeAndForwardConfiguration": {
                "timeToLiveSecs": 7200
            }
        }
    },
    ```

1. �ڵ�Ƭ�ײ����**����**��

#### �鿴����

1. �ص���ͨ�� **SSH** ���ӵ� **IoT Edge �豸**ʱ������ **Cloud Shell** �Ự��  

    > **��ע**����������ѹرջ�ʱ�����������ӡ���֮ǰһ������ `SSH` �����¼��

1. ��������ʾ����������������鿴�豸�ϲ����ģ���б�

    ```cmd/sh
    iotedge list
    ```

    ���µ�������ģ�鲿�� IoT Edge �豸������Ҫһ����ʱ�䡣��������ͻ�����ڸ�������б�����С�

    ```cmd/sh
    demouser@linuxagentvm-{deployment-id}:~$ iotedge list
    NAME                       STATUS           DESCRIPTION      CONFIG
    iotedge-streamjob-232539   running          Up a minute      mcr.microsoft.com/azure-stream-analytics/azureiotedge:1.0.5
    edgeAgent                  running          Up 6 hours       mcr.microsoft.com/azureiotedge-agent:1.0
    edgeHub                    running          Up 4 hours       mcr.microsoft.com/azureiotedge-hub:1.0
    turbinesensor              running          Up 4 hours       asaedgedockerhubtest/asa-edge-test-module:simulated-temperature-sensor
    ``` 

    > **��ע**��  ���������ģ��û�г������б��У���ȴ�һ�����ӣ�Ȼ������һ�Ρ��� IoT Edge �豸�ϸ���ģ�鲿�������Ҫһ����ʱ�䡣

1. ����������ʾ����������������鿴 `turbinesensor` ģ��� Edge �豸���͵�ң�⣺

    ```cmd/sh
    iotedge logs turbinesensor
    ```

1. ��һ���ӹ۲������
 
    ���¼����������������ʾ��

    ```cmd/sh
    11/14/2019 22:26:44 - Send Json Event : {"machine":{"temperature":231.599999999999959,"pressure":1.0095600761599359},"ambient":{"temperature":21.430643635304012,"humidity":24},"timeCreated":"2019-11-14T22:26:44.7904425Z"}
    11/14/2019 22:26:45 - Send Json Event : {"machine":{"temperature":531.999999999999957,"pressure":1.0099208337508767},"ambient":{"temperature":20.569532965342297,"humidity":25},"timeCreated":"2019-11-14T22:26:45.2901801Z"}
    Received message
    Received message Body: [{"command":"reset"}]
    Received message MetaData: {"MessageId":null,"To":null,"ExpiryTimeUtc":"0001-01-01T00:00:00","CorrelationId":null,"SequenceNumber":0,"LockToken":"e0e778b5-60ff-4e5d-93a4-ba5295b995941","EnqueuedTimeUtc":"0001-01-01T00:00:00","DeliveryCount":0,"UserId":null,"MessageSchema":null,"CreationTimeUtc":"0001-01-01T00:00:00","ContentType":"application/json","InputName":"control","ConnectionDeviceId":"turbine-06","ConnectionModuleId":"vm-iot-edge-CP1119","ContentEncoding":"utf-8","Properties":{},"BodyStream":{"CanRead":true,"CanSeek":false,"CanWrite":false,"CanTimeout":false}}
    Resetting temperature sensor..
    11/14/2019 22:26:45 - Send Json Event : {"machine":{"temperature":320.4,"pressure":0.99945886361358849},"ambient":{"temperature":20.940019742324957,"humidity":26},"timeCreated":"2019-11-14T22:26:45.7931201Z"}
    ```
 
1. �ڹ۲� **turbinesensor** ���͵��¶�ң��ʱ����ע����������ҵ�� `machine.temperature` ��ƽ��ֵ���� `72` ʱ���͵� **reset** �����������������ҵ��ѯ�����õĲ�����

�ڱ���ϰ�У���ʹ���� Azure IoT Edge ���������� Edge �豸�ϵ���Ϣ��
