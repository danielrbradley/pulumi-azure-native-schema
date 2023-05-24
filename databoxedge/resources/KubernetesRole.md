The limited preview of Kubernetes Cluster Management from the Azure supports:
1. Using a simple turn-key option in Azure Portal, deploy a Kubernetes cluster on your Azure Stack Edge device. 
2. Configure Kubernetes cluster running on your device with Arc enabled Kubernetes with a click of a button in the Azure Portal. 
 Azure Arc enables organizations to view, manage, and govern their on-premises Kubernetes clusters using the Azure Portal, command line tools, and APIs.
3. Easily configure Persistent Volumes using SMB and NFS shares for storing container data. 
 For more information, refer to the document here: https://databoxupdatepackages.blob.core.windows.net/documentation/Microsoft-Azure-Stack-Edge-K8-Cloud-Management-20210323.pdf 
 Or Demo: https://databoxupdatepackages.blob.core.windows.net/documentation/Microsoft-Azure-Stack-Edge-K8S-Cloud-Management-20210323.mp4
 By using this feature, you agree to the preview legal terms. See the https://azure.microsoft.com/en-us/support/legal/preview-supplemental-terms/
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
    var kubernetesRole = new AzureNative.DataBoxEdge.KubernetesRole("kubernetesRole", new()
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
		_, err := databoxedge.NewKubernetesRole(ctx, "kubernetesRole", &databoxedge.KubernetesRoleArgs{
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
import com.pulumi.azurenative.databoxedge.KubernetesRole;
import com.pulumi.azurenative.databoxedge.KubernetesRoleArgs;
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
        var kubernetesRole = new KubernetesRole("kubernetesRole", KubernetesRoleArgs.builder()        
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

const kubernetesRole = new azure_native.databoxedge.KubernetesRole("kubernetesRole", {
    deviceName: "testedgedevice",
    name: "IoTRole1",
    resourceGroupName: "GroupForEdgeAutomation",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

kubernetes_role = azure_native.databoxedge.KubernetesRole("kubernetesRole",
    device_name="testedgedevice",
    name="IoTRole1",
    resource_group_name="GroupForEdgeAutomation")

```

```yaml
resources:
  kubernetesRole:
    type: azure-native:databoxedge:KubernetesRole
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
$ pulumi import azure-native:databoxedge:KubernetesRole IoTRole1 /subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/roles/IoTRole1 
```
