The replica resource.
API Version: 2023-03-01.

{{% examples %}}
## Example Usage
{{% example %}}
### Replicas_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var replica = new AzureNative.AppConfiguration.Replica("replica", new()
    {
        ConfigStoreName = "contoso",
        Location = "eastus",
        ReplicaName = "myReplicaEus",
        ResourceGroupName = "myResourceGroup",
    });

});


```

```go
package main

import (
	appconfiguration "github.com/pulumi/pulumi-azure-native-sdk/appconfiguration"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := appconfiguration.NewReplica(ctx, "replica", &appconfiguration.ReplicaArgs{
			ConfigStoreName:   pulumi.String("contoso"),
			Location:          pulumi.String("eastus"),
			ReplicaName:       pulumi.String("myReplicaEus"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.appconfiguration.Replica;
import com.pulumi.azurenative.appconfiguration.ReplicaArgs;
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
        var replica = new Replica("replica", ReplicaArgs.builder()        
            .configStoreName("contoso")
            .location("eastus")
            .replicaName("myReplicaEus")
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const replica = new azure_native.appconfiguration.Replica("replica", {
    configStoreName: "contoso",
    location: "eastus",
    replicaName: "myReplicaEus",
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

replica = azure_native.appconfiguration.Replica("replica",
    config_store_name="contoso",
    location="eastus",
    replica_name="myReplicaEus",
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  replica:
    type: azure-native:appconfiguration:Replica
    properties:
      configStoreName: contoso
      location: eastus
      replicaName: myReplicaEus
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:appconfiguration:Replica myReplicaEus /subscriptions/c80fb759-c965-4c6a-9110-9b2b2d038882/resourceGroups/myResourceGroup/providers/Microsoft.AppConfiguration/configurationStores/contoso/replicas/myReplicaEus 
```
