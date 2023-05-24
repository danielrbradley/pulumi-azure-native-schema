Distributed availability group between box and Sql Managed Instance.
API Version: 2021-11-01.
Previous API Version: 2021-05-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a distributed availability group.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var distributedAvailabilityGroup = new AzureNative.Sql.DistributedAvailabilityGroup("distributedAvailabilityGroup", new()
    {
        DistributedAvailabilityGroupName = "dag",
        ManagedInstanceName = "testcl",
        PrimaryAvailabilityGroupName = "BoxLocalAg1",
        ResourceGroupName = "testrg",
        SecondaryAvailabilityGroupName = "testcl",
        SourceEndpoint = "TCP://SERVER:7022",
        TargetDatabase = "testdb",
    });

});


```

```go
package main

import (
	sql "github.com/pulumi/pulumi-azure-native-sdk/sql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := sql.NewDistributedAvailabilityGroup(ctx, "distributedAvailabilityGroup", &sql.DistributedAvailabilityGroupArgs{
			DistributedAvailabilityGroupName: pulumi.String("dag"),
			ManagedInstanceName:              pulumi.String("testcl"),
			PrimaryAvailabilityGroupName:     pulumi.String("BoxLocalAg1"),
			ResourceGroupName:                pulumi.String("testrg"),
			SecondaryAvailabilityGroupName:   pulumi.String("testcl"),
			SourceEndpoint:                   pulumi.String("TCP://SERVER:7022"),
			TargetDatabase:                   pulumi.String("testdb"),
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
import com.pulumi.azurenative.sql.DistributedAvailabilityGroup;
import com.pulumi.azurenative.sql.DistributedAvailabilityGroupArgs;
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
        var distributedAvailabilityGroup = new DistributedAvailabilityGroup("distributedAvailabilityGroup", DistributedAvailabilityGroupArgs.builder()        
            .distributedAvailabilityGroupName("dag")
            .managedInstanceName("testcl")
            .primaryAvailabilityGroupName("BoxLocalAg1")
            .resourceGroupName("testrg")
            .secondaryAvailabilityGroupName("testcl")
            .sourceEndpoint("TCP://SERVER:7022")
            .targetDatabase("testdb")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const distributedAvailabilityGroup = new azure_native.sql.DistributedAvailabilityGroup("distributedAvailabilityGroup", {
    distributedAvailabilityGroupName: "dag",
    managedInstanceName: "testcl",
    primaryAvailabilityGroupName: "BoxLocalAg1",
    resourceGroupName: "testrg",
    secondaryAvailabilityGroupName: "testcl",
    sourceEndpoint: "TCP://SERVER:7022",
    targetDatabase: "testdb",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

distributed_availability_group = azure_native.sql.DistributedAvailabilityGroup("distributedAvailabilityGroup",
    distributed_availability_group_name="dag",
    managed_instance_name="testcl",
    primary_availability_group_name="BoxLocalAg1",
    resource_group_name="testrg",
    secondary_availability_group_name="testcl",
    source_endpoint="TCP://SERVER:7022",
    target_database="testdb")

```

```yaml
resources:
  distributedAvailabilityGroup:
    type: azure-native:sql:DistributedAvailabilityGroup
    properties:
      distributedAvailabilityGroupName: dag
      managedInstanceName: testcl
      primaryAvailabilityGroupName: BoxLocalAg1
      resourceGroupName: testrg
      secondaryAvailabilityGroupName: testcl
      sourceEndpoint: TCP://SERVER:7022
      targetDatabase: testdb

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:DistributedAvailabilityGroup dag /subscriptions/f2669dff-5f08-45dd-b857-b2a60b72cdc9/resourceGroups/testrg/providers/Microsoft.Sql/managedInstances/testcl/distributedAvailabilityGroups/dag 
```
