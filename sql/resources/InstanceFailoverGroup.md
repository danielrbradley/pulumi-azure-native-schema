An instance failover group.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create failover group
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var instanceFailoverGroup = new AzureNative.Sql.InstanceFailoverGroup("instanceFailoverGroup", new()
    {
        FailoverGroupName = "failover-group-test-3",
        LocationName = "Japan East",
        ManagedInstancePairs = new[]
        {
            new AzureNative.Sql.Inputs.ManagedInstancePairInfoArgs
            {
                PartnerManagedInstanceId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/managedInstances/failover-group-secondary-mngdInstance",
                PrimaryManagedInstanceId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/managedInstances/failover-group-primary-mngdInstance",
            },
        },
        PartnerRegions = new[]
        {
            new AzureNative.Sql.Inputs.PartnerRegionInfoArgs
            {
                Location = "Japan West",
            },
        },
        ReadOnlyEndpoint = new AzureNative.Sql.Inputs.InstanceFailoverGroupReadOnlyEndpointArgs
        {
            FailoverPolicy = "Disabled",
        },
        ReadWriteEndpoint = new AzureNative.Sql.Inputs.InstanceFailoverGroupReadWriteEndpointArgs
        {
            FailoverPolicy = "Automatic",
            FailoverWithDataLossGracePeriodMinutes = 480,
        },
        ResourceGroupName = "Default",
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
		_, err := sql.NewInstanceFailoverGroup(ctx, "instanceFailoverGroup", &sql.InstanceFailoverGroupArgs{
			FailoverGroupName: pulumi.String("failover-group-test-3"),
			LocationName:      pulumi.String("Japan East"),
			ManagedInstancePairs: []sql.ManagedInstancePairInfoArgs{
				{
					PartnerManagedInstanceId: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/managedInstances/failover-group-secondary-mngdInstance"),
					PrimaryManagedInstanceId: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/managedInstances/failover-group-primary-mngdInstance"),
				},
			},
			PartnerRegions: []sql.PartnerRegionInfoArgs{
				{
					Location: pulumi.String("Japan West"),
				},
			},
			ReadOnlyEndpoint: &sql.InstanceFailoverGroupReadOnlyEndpointArgs{
				FailoverPolicy: pulumi.String("Disabled"),
			},
			ReadWriteEndpoint: &sql.InstanceFailoverGroupReadWriteEndpointArgs{
				FailoverPolicy:                         pulumi.String("Automatic"),
				FailoverWithDataLossGracePeriodMinutes: pulumi.Int(480),
			},
			ResourceGroupName: pulumi.String("Default"),
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
import com.pulumi.azurenative.sql.InstanceFailoverGroup;
import com.pulumi.azurenative.sql.InstanceFailoverGroupArgs;
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
        var instanceFailoverGroup = new InstanceFailoverGroup("instanceFailoverGroup", InstanceFailoverGroupArgs.builder()        
            .failoverGroupName("failover-group-test-3")
            .locationName("Japan East")
            .managedInstancePairs(Map.ofEntries(
                Map.entry("partnerManagedInstanceId", "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/managedInstances/failover-group-secondary-mngdInstance"),
                Map.entry("primaryManagedInstanceId", "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/managedInstances/failover-group-primary-mngdInstance")
            ))
            .partnerRegions(Map.of("location", "Japan West"))
            .readOnlyEndpoint(Map.of("failoverPolicy", "Disabled"))
            .readWriteEndpoint(Map.ofEntries(
                Map.entry("failoverPolicy", "Automatic"),
                Map.entry("failoverWithDataLossGracePeriodMinutes", 480)
            ))
            .resourceGroupName("Default")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const instanceFailoverGroup = new azure_native.sql.InstanceFailoverGroup("instanceFailoverGroup", {
    failoverGroupName: "failover-group-test-3",
    locationName: "Japan East",
    managedInstancePairs: [{
        partnerManagedInstanceId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/managedInstances/failover-group-secondary-mngdInstance",
        primaryManagedInstanceId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/managedInstances/failover-group-primary-mngdInstance",
    }],
    partnerRegions: [{
        location: "Japan West",
    }],
    readOnlyEndpoint: {
        failoverPolicy: "Disabled",
    },
    readWriteEndpoint: {
        failoverPolicy: "Automatic",
        failoverWithDataLossGracePeriodMinutes: 480,
    },
    resourceGroupName: "Default",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

instance_failover_group = azure_native.sql.InstanceFailoverGroup("instanceFailoverGroup",
    failover_group_name="failover-group-test-3",
    location_name="Japan East",
    managed_instance_pairs=[azure_native.sql.ManagedInstancePairInfoArgs(
        partner_managed_instance_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/managedInstances/failover-group-secondary-mngdInstance",
        primary_managed_instance_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/managedInstances/failover-group-primary-mngdInstance",
    )],
    partner_regions=[azure_native.sql.PartnerRegionInfoArgs(
        location="Japan West",
    )],
    read_only_endpoint=azure_native.sql.InstanceFailoverGroupReadOnlyEndpointArgs(
        failover_policy="Disabled",
    ),
    read_write_endpoint=azure_native.sql.InstanceFailoverGroupReadWriteEndpointArgs(
        failover_policy="Automatic",
        failover_with_data_loss_grace_period_minutes=480,
    ),
    resource_group_name="Default")

```

```yaml
resources:
  instanceFailoverGroup:
    type: azure-native:sql:InstanceFailoverGroup
    properties:
      failoverGroupName: failover-group-test-3
      locationName: Japan East
      managedInstancePairs:
        - partnerManagedInstanceId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/managedInstances/failover-group-secondary-mngdInstance
          primaryManagedInstanceId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/managedInstances/failover-group-primary-mngdInstance
      partnerRegions:
        - location: Japan West
      readOnlyEndpoint:
        failoverPolicy: Disabled
      readWriteEndpoint:
        failoverPolicy: Automatic
        failoverWithDataLossGracePeriodMinutes: 480
      resourceGroupName: Default

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:InstanceFailoverGroup failover-group-test-3 /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/locations/JapanEast/instanceFailoverGroups/failover-group-test-3 
```
