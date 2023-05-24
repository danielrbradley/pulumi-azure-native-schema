Fabric definition.
API Version: 2023-02-01.
Previous API Version: 2018-07-10. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates an Azure Site Recovery fabric.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var replicationFabric = new AzureNative.RecoveryServices.ReplicationFabric("replicationFabric", new()
    {
        FabricName = "cloud1",
        Properties = new AzureNative.RecoveryServices.Inputs.FabricCreationInputPropertiesArgs
        {
            CustomDetails = 
            {
                { "instanceType", "FabricSpecificCreationInput" },
            },
        },
        ResourceGroupName = "resourceGroupPS1",
        ResourceName = "vault1",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.recoveryservices.ReplicationFabric;
import com.pulumi.azurenative.recoveryservices.ReplicationFabricArgs;
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
        var replicationFabric = new ReplicationFabric("replicationFabric", ReplicationFabricArgs.builder()        
            .fabricName("cloud1")
            .properties(Map.of("customDetails", Map.of("instanceType", "FabricSpecificCreationInput")))
            .resourceGroupName("resourceGroupPS1")
            .resourceName("vault1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const replicationFabric = new azure_native.recoveryservices.ReplicationFabric("replicationFabric", {
    fabricName: "cloud1",
    properties: {
        customDetails: {
            instanceType: "FabricSpecificCreationInput",
        },
    },
    resourceGroupName: "resourceGroupPS1",
    resourceName: "vault1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

replication_fabric = azure_native.recoveryservices.ReplicationFabric("replicationFabric",
    fabric_name="cloud1",
    properties=azure_native.recoveryservices.FabricPropertiesResponseArgs(
        custom_details={
            "instanceType": "FabricSpecificCreationInput",
        },
    ),
    resource_group_name="resourceGroupPS1",
    resource_name_="vault1")

```

```yaml
resources:
  replicationFabric:
    type: azure-native:recoveryservices:ReplicationFabric
    properties:
      fabricName: cloud1
      properties:
        customDetails:
          instanceType: FabricSpecificCreationInput
      resourceGroupName: resourceGroupPS1
      resourceName: vault1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:recoveryservices:ReplicationFabric cloud1 /Subscriptions/c183865e-6077-46f2-a3b1-deb0f4f4650a/resourceGroups/resourceGroupPS1/providers/Microsoft.RecoveryServices/vaults/vault1/replicationFabrics/cloud1 
```
