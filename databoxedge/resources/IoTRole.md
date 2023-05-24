Compute role.
API Version: 2022-03-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### RolePut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var ioTRole = new AzureNative.DataBoxEdge.IoTRole("ioTRole", new()
    {
        DeviceName = "testedgedevice",
        HostPlatform = "Linux",
        IoTDeviceDetails = new AzureNative.DataBoxEdge.Inputs.IoTDeviceInfoArgs
        {
            Authentication = new AzureNative.DataBoxEdge.Inputs.AuthenticationArgs
            {
                SymmetricKey = new AzureNative.DataBoxEdge.Inputs.SymmetricKeyArgs
                {
                    ConnectionString = new AzureNative.DataBoxEdge.Inputs.AsymmetricEncryptedSecretArgs
                    {
                        EncryptionAlgorithm = "AES256",
                        EncryptionCertThumbprint = "348586569999244",
                        Value = "Encrypted<<HostName=iothub.azure-devices.net;DeviceId=iotDevice;SharedAccessKey=2C750FscEas3JmQ8Bnui5yQWZPyml0/UiRt1bQwd8=>>",
                    },
                },
            },
            DeviceId = "iotdevice",
            IoTHostHub = "iothub.azure-devices.net",
        },
        IoTEdgeDeviceDetails = new AzureNative.DataBoxEdge.Inputs.IoTDeviceInfoArgs
        {
            Authentication = new AzureNative.DataBoxEdge.Inputs.AuthenticationArgs
            {
                SymmetricKey = new AzureNative.DataBoxEdge.Inputs.SymmetricKeyArgs
                {
                    ConnectionString = new AzureNative.DataBoxEdge.Inputs.AsymmetricEncryptedSecretArgs
                    {
                        EncryptionAlgorithm = "AES256",
                        EncryptionCertThumbprint = "1245475856069999244",
                        Value = "Encrypted<<HostName=iothub.azure-devices.net;DeviceId=iotEdge;SharedAccessKey=2C750FscEas3JmQ8Bnui5yQWZPyml0/UiRt1bQwd8=>>",
                    },
                },
            },
            DeviceId = "iotEdge",
            IoTHostHub = "iothub.azure-devices.net",
        },
        Kind = "IOT",
        Name = "IoTRole1",
        ResourceGroupName = "GroupForEdgeAutomation",
        RoleStatus = "Enabled",
        ShareMappings = new[] {},
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.databoxedge.IoTRole;
import com.pulumi.azurenative.databoxedge.IoTRoleArgs;
import java.util.List;
import java.util.ArrayList;
import java.util.Map;
import java.io.File;
import java.nio.file.Files;
import java.nio.file.Paths;

public class App {
    public static void main(String[] args) {
        Pulumi.run(App::stack);
    }

    public static void stack(Context ctx) {
        var ioTRole = new IoTRole("ioTRole", IoTRoleArgs.builder()        
            .deviceName("testedgedevice")
            .hostPlatform("Linux")
            .ioTDeviceDetails(Map.ofEntries(
                Map.entry("authentication", Map.of("symmetricKey", Map.of("connectionString", Map.ofEntries(
                    Map.entry("encryptionAlgorithm", "AES256"),
                    Map.entry("encryptionCertThumbprint", "348586569999244"),
                    Map.entry("value", "Encrypted<<HostName=iothub.azure-devices.net;DeviceId=iotDevice;SharedAccessKey=2C750FscEas3JmQ8Bnui5yQWZPyml0/UiRt1bQwd8=>>")
                )))),
                Map.entry("deviceId", "iotdevice"),
                Map.entry("ioTHostHub", "iothub.azure-devices.net")
            ))
            .ioTEdgeDeviceDetails(Map.ofEntries(
                Map.entry("authentication", Map.of("symmetricKey", Map.of("connectionString", Map.ofEntries(
                    Map.entry("encryptionAlgorithm", "AES256"),
                    Map.entry("encryptionCertThumbprint", "1245475856069999244"),
                    Map.entry("value", "Encrypted<<HostName=iothub.azure-devices.net;DeviceId=iotEdge;SharedAccessKey=2C750FscEas3JmQ8Bnui5yQWZPyml0/UiRt1bQwd8=>>")
                )))),
                Map.entry("deviceId", "iotEdge"),
                Map.entry("ioTHostHub", "iothub.azure-devices.net")
            ))
            .kind("IOT")
            .name("IoTRole1")
            .resourceGroupName("GroupForEdgeAutomation")
            .roleStatus("Enabled")
            .shareMappings()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const ioTRole = new azure_native.databoxedge.IoTRole("ioTRole", {
    deviceName: "testedgedevice",
    hostPlatform: "Linux",
    ioTDeviceDetails: {
        authentication: {
            symmetricKey: {
                connectionString: {
                    encryptionAlgorithm: "AES256",
                    encryptionCertThumbprint: "348586569999244",
                    value: "Encrypted<<HostName=iothub.azure-devices.net;DeviceId=iotDevice;SharedAccessKey=2C750FscEas3JmQ8Bnui5yQWZPyml0/UiRt1bQwd8=>>",
                },
            },
        },
        deviceId: "iotdevice",
        ioTHostHub: "iothub.azure-devices.net",
    },
    ioTEdgeDeviceDetails: {
        authentication: {
            symmetricKey: {
                connectionString: {
                    encryptionAlgorithm: "AES256",
                    encryptionCertThumbprint: "1245475856069999244",
                    value: "Encrypted<<HostName=iothub.azure-devices.net;DeviceId=iotEdge;SharedAccessKey=2C750FscEas3JmQ8Bnui5yQWZPyml0/UiRt1bQwd8=>>",
                },
            },
        },
        deviceId: "iotEdge",
        ioTHostHub: "iothub.azure-devices.net",
    },
    kind: "IOT",
    name: "IoTRole1",
    resourceGroupName: "GroupForEdgeAutomation",
    roleStatus: "Enabled",
    shareMappings: [],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

io_t_role = azure_native.databoxedge.IoTRole("ioTRole",
    device_name="testedgedevice",
    host_platform="Linux",
    io_t_device_details=azure_native.databoxedge.IoTDeviceInfoResponseArgs(
        authentication={
            "symmetricKey": {
                "connectionString": azure_native.databoxedge.AsymmetricEncryptedSecretArgs(
                    encryption_algorithm="AES256",
                    encryption_cert_thumbprint="348586569999244",
                    value="Encrypted<<HostName=iothub.azure-devices.net;DeviceId=iotDevice;SharedAccessKey=2C750FscEas3JmQ8Bnui5yQWZPyml0/UiRt1bQwd8=>>",
                ),
            },
        },
        device_id="iotdevice",
        io_t_host_hub="iothub.azure-devices.net",
    ),
    io_t_edge_device_details=azure_native.databoxedge.IoTDeviceInfoResponseArgs(
        authentication={
            "symmetricKey": {
                "connectionString": azure_native.databoxedge.AsymmetricEncryptedSecretArgs(
                    encryption_algorithm="AES256",
                    encryption_cert_thumbprint="1245475856069999244",
                    value="Encrypted<<HostName=iothub.azure-devices.net;DeviceId=iotEdge;SharedAccessKey=2C750FscEas3JmQ8Bnui5yQWZPyml0/UiRt1bQwd8=>>",
                ),
            },
        },
        device_id="iotEdge",
        io_t_host_hub="iothub.azure-devices.net",
    ),
    kind="IOT",
    name="IoTRole1",
    resource_group_name="GroupForEdgeAutomation",
    role_status="Enabled",
    share_mappings=[])

```

```yaml
resources:
  ioTRole:
    type: azure-native:databoxedge:IoTRole
    properties:
      deviceName: testedgedevice
      hostPlatform: Linux
      ioTDeviceDetails:
        authentication:
          symmetricKey:
            connectionString:
              encryptionAlgorithm: AES256
              encryptionCertThumbprint: '348586569999244'
              value: Encrypted<<HostName=iothub.azure-devices.net;DeviceId=iotDevice;SharedAccessKey=2C750FscEas3JmQ8Bnui5yQWZPyml0/UiRt1bQwd8=>>
        deviceId: iotdevice
        ioTHostHub: iothub.azure-devices.net
      ioTEdgeDeviceDetails:
        authentication:
          symmetricKey:
            connectionString:
              encryptionAlgorithm: AES256
              encryptionCertThumbprint: '1245475856069999244'
              value: Encrypted<<HostName=iothub.azure-devices.net;DeviceId=iotEdge;SharedAccessKey=2C750FscEas3JmQ8Bnui5yQWZPyml0/UiRt1bQwd8=>>
        deviceId: iotEdge
        ioTHostHub: iothub.azure-devices.net
      kind: IOT
      name: IoTRole1
      resourceGroupName: GroupForEdgeAutomation
      roleStatus: Enabled
      shareMappings: []

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:databoxedge:IoTRole IoTRole1 /subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/roles/IoTRole1 
```
