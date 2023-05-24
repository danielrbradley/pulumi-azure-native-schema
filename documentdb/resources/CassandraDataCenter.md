A managed Cassandra data center.
API Version: 2022-11-15.
Previous API Version: 2021-03-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CosmosDBManagedCassandraDataCenterCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cassandraDataCenter = new AzureNative.DocumentDB.CassandraDataCenter("cassandraDataCenter", new()
    {
        ClusterName = "cassandra-prod",
        DataCenterName = "dc1",
        Properties = new AzureNative.DocumentDB.Inputs.DataCenterResourcePropertiesArgs
        {
            Base64EncodedCassandraYamlFragment = "Y29tcGFjdGlvbl90aHJvdWdocHV0X21iX3Blcl9zZWM6IDMyCmNvbXBhY3Rpb25fbGFyZ2VfcGFydGl0aW9uX3dhcm5pbmdfdGhyZXNob2xkX21iOiAxMDA=",
            DataCenterLocation = "West US 2",
            DelegatedSubnetId = "/subscriptions/536e130b-d7d6-4ac7-98a5-de20d69588d2/resourceGroups/customer-vnet-rg/providers/Microsoft.Network/virtualNetworks/customer-vnet/subnets/dc1-subnet",
            NodeCount = 9,
        },
        ResourceGroupName = "cassandra-prod-rg",
    });

});


```

```go
package main

import (
	documentdb "github.com/pulumi/pulumi-azure-native-sdk/documentdb"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := documentdb.NewCassandraDataCenter(ctx, "cassandraDataCenter", &documentdb.CassandraDataCenterArgs{
			ClusterName:    pulumi.String("cassandra-prod"),
			DataCenterName: pulumi.String("dc1"),
			Properties: &documentdb.DataCenterResourcePropertiesArgs{
				Base64EncodedCassandraYamlFragment: pulumi.String("Y29tcGFjdGlvbl90aHJvdWdocHV0X21iX3Blcl9zZWM6IDMyCmNvbXBhY3Rpb25fbGFyZ2VfcGFydGl0aW9uX3dhcm5pbmdfdGhyZXNob2xkX21iOiAxMDA="),
				DataCenterLocation:                 pulumi.String("West US 2"),
				DelegatedSubnetId:                  pulumi.String("/subscriptions/536e130b-d7d6-4ac7-98a5-de20d69588d2/resourceGroups/customer-vnet-rg/providers/Microsoft.Network/virtualNetworks/customer-vnet/subnets/dc1-subnet"),
				NodeCount:                          pulumi.Int(9),
			},
			ResourceGroupName: pulumi.String("cassandra-prod-rg"),
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
import com.pulumi.azurenative.documentdb.CassandraDataCenter;
import com.pulumi.azurenative.documentdb.CassandraDataCenterArgs;
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
        var cassandraDataCenter = new CassandraDataCenter("cassandraDataCenter", CassandraDataCenterArgs.builder()        
            .clusterName("cassandra-prod")
            .dataCenterName("dc1")
            .properties(Map.ofEntries(
                Map.entry("base64EncodedCassandraYamlFragment", "Y29tcGFjdGlvbl90aHJvdWdocHV0X21iX3Blcl9zZWM6IDMyCmNvbXBhY3Rpb25fbGFyZ2VfcGFydGl0aW9uX3dhcm5pbmdfdGhyZXNob2xkX21iOiAxMDA="),
                Map.entry("dataCenterLocation", "West US 2"),
                Map.entry("delegatedSubnetId", "/subscriptions/536e130b-d7d6-4ac7-98a5-de20d69588d2/resourceGroups/customer-vnet-rg/providers/Microsoft.Network/virtualNetworks/customer-vnet/subnets/dc1-subnet"),
                Map.entry("nodeCount", 9)
            ))
            .resourceGroupName("cassandra-prod-rg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cassandraDataCenter = new azure_native.documentdb.CassandraDataCenter("cassandraDataCenter", {
    clusterName: "cassandra-prod",
    dataCenterName: "dc1",
    properties: {
        base64EncodedCassandraYamlFragment: "Y29tcGFjdGlvbl90aHJvdWdocHV0X21iX3Blcl9zZWM6IDMyCmNvbXBhY3Rpb25fbGFyZ2VfcGFydGl0aW9uX3dhcm5pbmdfdGhyZXNob2xkX21iOiAxMDA=",
        dataCenterLocation: "West US 2",
        delegatedSubnetId: "/subscriptions/536e130b-d7d6-4ac7-98a5-de20d69588d2/resourceGroups/customer-vnet-rg/providers/Microsoft.Network/virtualNetworks/customer-vnet/subnets/dc1-subnet",
        nodeCount: 9,
    },
    resourceGroupName: "cassandra-prod-rg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cassandra_data_center = azure_native.documentdb.CassandraDataCenter("cassandraDataCenter",
    cluster_name="cassandra-prod",
    data_center_name="dc1",
    properties=azure_native.documentdb.DataCenterResourcePropertiesArgs(
        base64_encoded_cassandra_yaml_fragment="Y29tcGFjdGlvbl90aHJvdWdocHV0X21iX3Blcl9zZWM6IDMyCmNvbXBhY3Rpb25fbGFyZ2VfcGFydGl0aW9uX3dhcm5pbmdfdGhyZXNob2xkX21iOiAxMDA=",
        data_center_location="West US 2",
        delegated_subnet_id="/subscriptions/536e130b-d7d6-4ac7-98a5-de20d69588d2/resourceGroups/customer-vnet-rg/providers/Microsoft.Network/virtualNetworks/customer-vnet/subnets/dc1-subnet",
        node_count=9,
    ),
    resource_group_name="cassandra-prod-rg")

```

```yaml
resources:
  cassandraDataCenter:
    type: azure-native:documentdb:CassandraDataCenter
    properties:
      clusterName: cassandra-prod
      dataCenterName: dc1
      properties:
        base64EncodedCassandraYamlFragment: Y29tcGFjdGlvbl90aHJvdWdocHV0X21iX3Blcl9zZWM6IDMyCmNvbXBhY3Rpb25fbGFyZ2VfcGFydGl0aW9uX3dhcm5pbmdfdGhyZXNob2xkX21iOiAxMDA=
        dataCenterLocation: West US 2
        delegatedSubnetId: /subscriptions/536e130b-d7d6-4ac7-98a5-de20d69588d2/resourceGroups/customer-vnet-rg/providers/Microsoft.Network/virtualNetworks/customer-vnet/subnets/dc1-subnet
        nodeCount: 9
      resourceGroupName: cassandra-prod-rg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:documentdb:CassandraDataCenter dc1 /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/cassandra-prod-rg/providers/Microsoft.DocumentDB/cassandraClusters/cassandra-prod/dataCenters/dc1 
```
