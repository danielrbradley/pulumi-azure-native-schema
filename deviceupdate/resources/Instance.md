Device Update instance details.
API Version: 2022-10-01.
Previous API Version: 2020-03-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates or updates Instance
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var instance = new AzureNative.DeviceUpdate.Instance("instance", new()
    {
        AccountName = "contoso",
        DiagnosticStorageProperties = new AzureNative.DeviceUpdate.Inputs.DiagnosticStoragePropertiesArgs
        {
            AuthenticationType = "KeyBased",
            ConnectionString = "string",
            ResourceId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/adu-resource-group/providers/Microsoft.Storage/storageAccounts/testAccount",
        },
        EnableDiagnostics = false,
        InstanceName = "blue",
        IotHubs = new[]
        {
            new AzureNative.DeviceUpdate.Inputs.IotHubSettingsArgs
            {
                ResourceId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Devices/IotHubs/blue-contoso-hub",
            },
        },
        Location = "westus2",
        ResourceGroupName = "test-rg",
    });

});


```

```go
package main

import (
	deviceupdate "github.com/pulumi/pulumi-azure-native-sdk/deviceupdate"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := deviceupdate.NewInstance(ctx, "instance", &deviceupdate.InstanceArgs{
			AccountName: pulumi.String("contoso"),
			DiagnosticStorageProperties: &deviceupdate.DiagnosticStoragePropertiesArgs{
				AuthenticationType: pulumi.String("KeyBased"),
				ConnectionString:   pulumi.String("string"),
				ResourceId:         pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/adu-resource-group/providers/Microsoft.Storage/storageAccounts/testAccount"),
			},
			EnableDiagnostics: pulumi.Bool(false),
			InstanceName:      pulumi.String("blue"),
			IotHubs: []deviceupdate.IotHubSettingsArgs{
				{
					ResourceId: pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Devices/IotHubs/blue-contoso-hub"),
				},
			},
			Location:          pulumi.String("westus2"),
			ResourceGroupName: pulumi.String("test-rg"),
		})
		if err != nil {
			return err
		}
		return nil
	})
}

```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.deviceupdate.Instance;
import com.pulumi.azurenative.deviceupdate.InstanceArgs;
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
        var instance = new Instance("instance", InstanceArgs.builder()        
            .accountName("contoso")
            .diagnosticStorageProperties(Map.ofEntries(
                Map.entry("authenticationType", "KeyBased"),
                Map.entry("connectionString", "string"),
                Map.entry("resourceId", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/adu-resource-group/providers/Microsoft.Storage/storageAccounts/testAccount")
            ))
            .enableDiagnostics(false)
            .instanceName("blue")
            .iotHubs(Map.of("resourceId", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Devices/IotHubs/blue-contoso-hub"))
            .location("westus2")
            .resourceGroupName("test-rg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const instance = new azure_native.deviceupdate.Instance("instance", {
    accountName: "contoso",
    diagnosticStorageProperties: {
        authenticationType: "KeyBased",
        connectionString: "string",
        resourceId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/adu-resource-group/providers/Microsoft.Storage/storageAccounts/testAccount",
    },
    enableDiagnostics: false,
    instanceName: "blue",
    iotHubs: [{
        resourceId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Devices/IotHubs/blue-contoso-hub",
    }],
    location: "westus2",
    resourceGroupName: "test-rg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

instance = azure_native.deviceupdate.Instance("instance",
    account_name="contoso",
    diagnostic_storage_properties=azure_native.deviceupdate.DiagnosticStoragePropertiesArgs(
        authentication_type="KeyBased",
        connection_string="string",
        resource_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/adu-resource-group/providers/Microsoft.Storage/storageAccounts/testAccount",
    ),
    enable_diagnostics=False,
    instance_name="blue",
    iot_hubs=[azure_native.deviceupdate.IotHubSettingsArgs(
        resource_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Devices/IotHubs/blue-contoso-hub",
    )],
    location="westus2",
    resource_group_name="test-rg")

```

```yaml
resources:
  instance:
    type: azure-native:deviceupdate:Instance
    properties:
      accountName: contoso
      diagnosticStorageProperties:
        authenticationType: KeyBased
        connectionString: string
        resourceId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/adu-resource-group/providers/Microsoft.Storage/storageAccounts/testAccount
      enableDiagnostics: false
      instanceName: blue
      iotHubs:
        - resourceId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.Devices/IotHubs/blue-contoso-hub
      location: westus2
      resourceGroupName: test-rg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:deviceupdate:Instance blue /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.DeviceUpdate/accounts/contoso/instances/blue 
```
