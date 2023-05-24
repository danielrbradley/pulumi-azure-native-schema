Represents a container on the  Data Box Edge/Gateway device.
API Version: 2022-03-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ContainerPut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var container = new AzureNative.DataBoxEdge.Container("container", new()
    {
        ContainerName = "blobcontainer1",
        DataFormat = "BlockBlob",
        DeviceName = "testedgedevice",
        ResourceGroupName = "GroupForEdgeAutomation",
        StorageAccountName = "storageaccount1",
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
		_, err := databoxedge.NewContainer(ctx, "container", &databoxedge.ContainerArgs{
			ContainerName:      pulumi.String("blobcontainer1"),
			DataFormat:         pulumi.String("BlockBlob"),
			DeviceName:         pulumi.String("testedgedevice"),
			ResourceGroupName:  pulumi.String("GroupForEdgeAutomation"),
			StorageAccountName: pulumi.String("storageaccount1"),
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
import com.pulumi.azurenative.databoxedge.Container;
import com.pulumi.azurenative.databoxedge.ContainerArgs;
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
        var container = new Container("container", ContainerArgs.builder()        
            .containerName("blobcontainer1")
            .dataFormat("BlockBlob")
            .deviceName("testedgedevice")
            .resourceGroupName("GroupForEdgeAutomation")
            .storageAccountName("storageaccount1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const container = new azure_native.databoxedge.Container("container", {
    containerName: "blobcontainer1",
    dataFormat: "BlockBlob",
    deviceName: "testedgedevice",
    resourceGroupName: "GroupForEdgeAutomation",
    storageAccountName: "storageaccount1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

container = azure_native.databoxedge.Container("container",
    container_name="blobcontainer1",
    data_format="BlockBlob",
    device_name="testedgedevice",
    resource_group_name="GroupForEdgeAutomation",
    storage_account_name="storageaccount1")

```

```yaml
resources:
  container:
    type: azure-native:databoxedge:Container
    properties:
      containerName: blobcontainer1
      dataFormat: BlockBlob
      deviceName: testedgedevice
      resourceGroupName: GroupForEdgeAutomation
      storageAccountName: storageaccount1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:databoxedge:Container blobcontainer-5e155efe /subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForDataBoxEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/storageAccounts/storageaccount1/containers/blobcontainer1 
```
