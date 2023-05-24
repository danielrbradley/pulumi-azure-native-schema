The preview of Virtual Machine Cloud Management from the Azure supports deploying and managing VMs on your Azure Stack Edge device from Azure Portal. 
For more information, refer to: https://docs.microsoft.com/en-us/azure/databox-online/azure-stack-edge-gpu-virtual-machine-overview
By using this feature, you agree to the preview legal terms. See the https://azure.microsoft.com/en-us/support/legal/preview-supplemental-terms/ for additional details.
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
    var cloudEdgeManagementRole = new AzureNative.DataBoxEdge.CloudEdgeManagementRole("cloudEdgeManagementRole", new()
    {
        DeviceName = "testedgedevice",
        Name = "IoTRole1",
        ResourceGroupName = "GroupForEdgeAutomation",
    });

});


```

```go
package main

import (
	databoxedge "github.com/pulumi/pulumi-azure-native-sdk/databoxedge"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := databoxedge.NewCloudEdgeManagementRole(ctx, "cloudEdgeManagementRole", &databoxedge.CloudEdgeManagementRoleArgs{
			DeviceName:        pulumi.String("testedgedevice"),
			Name:              pulumi.String("IoTRole1"),
			ResourceGroupName: pulumi.String("GroupForEdgeAutomation"),
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
import com.pulumi.azurenative.databoxedge.CloudEdgeManagementRole;
import com.pulumi.azurenative.databoxedge.CloudEdgeManagementRoleArgs;
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
        var cloudEdgeManagementRole = new CloudEdgeManagementRole("cloudEdgeManagementRole", CloudEdgeManagementRoleArgs.builder()        
            .deviceName("testedgedevice")
            .name("IoTRole1")
            .resourceGroupName("GroupForEdgeAutomation")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cloudEdgeManagementRole = new azure_native.databoxedge.CloudEdgeManagementRole("cloudEdgeManagementRole", {
    deviceName: "testedgedevice",
    name: "IoTRole1",
    resourceGroupName: "GroupForEdgeAutomation",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cloud_edge_management_role = azure_native.databoxedge.CloudEdgeManagementRole("cloudEdgeManagementRole",
    device_name="testedgedevice",
    name="IoTRole1",
    resource_group_name="GroupForEdgeAutomation")

```

```yaml
resources:
  cloudEdgeManagementRole:
    type: azure-native:databoxedge:CloudEdgeManagementRole
    properties:
      deviceName: testedgedevice
      name: IoTRole1
      resourceGroupName: GroupForEdgeAutomation

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:databoxedge:CloudEdgeManagementRole IoTRole1 /subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/roles/IoTRole1 
```
