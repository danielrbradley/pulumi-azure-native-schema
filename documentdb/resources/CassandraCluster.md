Representation of a managed Cassandra cluster.
API Version: 2022-11-15.
Previous API Version: 2021-03-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CosmosDBManagedCassandraClusterCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cassandraCluster = new AzureNative.DocumentDB.CassandraCluster("cassandraCluster", new()
    {
        ClusterName = "cassandra-prod",
        Location = "West US",
        Properties = new AzureNative.DocumentDB.Inputs.ClusterResourcePropertiesArgs
        {
            AuthenticationMethod = "Cassandra",
            CassandraVersion = "3.11",
            ClientCertificates = new[]
            {
                new AzureNative.DocumentDB.Inputs.CertificateArgs
                {
                    Pem = @"-----BEGIN CERTIFICATE-----
...Base64 encoded certificate...
-----END CERTIFICATE-----",
                },
            },
            ClusterNameOverride = "ClusterNameIllegalForAzureResource",
            DelegatedManagementSubnetId = "/subscriptions/536e130b-d7d6-4ac7-98a5-de20d69588d2/resourceGroups/customer-vnet-rg/providers/Microsoft.Network/virtualNetworks/customer-vnet/subnets/management",
            ExternalGossipCertificates = new[]
            {
                new AzureNative.DocumentDB.Inputs.CertificateArgs
                {
                    Pem = @"-----BEGIN CERTIFICATE-----
...Base64 encoded certificate...
-----END CERTIFICATE-----",
                },
            },
            ExternalSeedNodes = new[]
            {
                new AzureNative.DocumentDB.Inputs.SeedNodeArgs
                {
                    IpAddress = "10.52.221.2",
                },
                new AzureNative.DocumentDB.Inputs.SeedNodeArgs
                {
                    IpAddress = "10.52.221.3",
                },
                new AzureNative.DocumentDB.Inputs.SeedNodeArgs
                {
                    IpAddress = "10.52.221.4",
                },
            },
            HoursBetweenBackups = 24,
            InitialCassandraAdminPassword = "mypassword",
        },
        ResourceGroupName = "cassandra-prod-rg",
        Tags = null,
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
		_, err := documentdb.NewCassandraCluster(ctx, "cassandraCluster", &documentdb.CassandraClusterArgs{
			ClusterName: pulumi.String("cassandra-prod"),
			Location:    pulumi.String("West US"),
			Properties: documentdb.ClusterResourceResponseProperties{
				AuthenticationMethod: pulumi.String("Cassandra"),
				CassandraVersion:     pulumi.String("3.11"),
				ClientCertificates: documentdb.CertificateArray{
					&documentdb.CertificateArgs{
						Pem: pulumi.String("-----BEGIN CERTIFICATE-----\n...Base64 encoded certificate...\n-----END CERTIFICATE-----"),
					},
				},
				ClusterNameOverride:         pulumi.String("ClusterNameIllegalForAzureResource"),
				DelegatedManagementSubnetId: pulumi.String("/subscriptions/536e130b-d7d6-4ac7-98a5-de20d69588d2/resourceGroups/customer-vnet-rg/providers/Microsoft.Network/virtualNetworks/customer-vnet/subnets/management"),
				ExternalGossipCertificates: documentdb.CertificateArray{
					&documentdb.CertificateArgs{
						Pem: pulumi.String("-----BEGIN CERTIFICATE-----\n...Base64 encoded certificate...\n-----END CERTIFICATE-----"),
					},
				},
				ExternalSeedNodes: documentdb.SeedNodeArray{
					&documentdb.SeedNodeArgs{
						IpAddress: pulumi.String("10.52.221.2"),
					},
					&documentdb.SeedNodeArgs{
						IpAddress: pulumi.String("10.52.221.3"),
					},
					&documentdb.SeedNodeArgs{
						IpAddress: pulumi.String("10.52.221.4"),
					},
				},
				HoursBetweenBackups:           pulumi.Int(24),
				InitialCassandraAdminPassword: pulumi.String("mypassword"),
			},
			ResourceGroupName: pulumi.String("cassandra-prod-rg"),
			Tags:              nil,
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
import com.pulumi.azurenative.documentdb.CassandraCluster;
import com.pulumi.azurenative.documentdb.CassandraClusterArgs;
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
        var cassandraCluster = new CassandraCluster("cassandraCluster", CassandraClusterArgs.builder()        
            .clusterName("cassandra-prod")
            .location("West US")
            .properties(Map.ofEntries(
                Map.entry("authenticationMethod", "Cassandra"),
                Map.entry("cassandraVersion", "3.11"),
                Map.entry("clientCertificates", Map.of("pem", """
-----BEGIN CERTIFICATE-----
...Base64 encoded certificate...
-----END CERTIFICATE-----                """)),
                Map.entry("clusterNameOverride", "ClusterNameIllegalForAzureResource"),
                Map.entry("delegatedManagementSubnetId", "/subscriptions/536e130b-d7d6-4ac7-98a5-de20d69588d2/resourceGroups/customer-vnet-rg/providers/Microsoft.Network/virtualNetworks/customer-vnet/subnets/management"),
                Map.entry("externalGossipCertificates", Map.of("pem", """
-----BEGIN CERTIFICATE-----
...Base64 encoded certificate...
-----END CERTIFICATE-----                """)),
                Map.entry("externalSeedNodes",                 
                    Map.of("ipAddress", "10.52.221.2"),
                    Map.of("ipAddress", "10.52.221.3"),
                    Map.of("ipAddress", "10.52.221.4")),
                Map.entry("hoursBetweenBackups", 24),
                Map.entry("initialCassandraAdminPassword", "mypassword")
            ))
            .resourceGroupName("cassandra-prod-rg")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cassandraCluster = new azure_native.documentdb.CassandraCluster("cassandraCluster", {
    clusterName: "cassandra-prod",
    location: "West US",
    properties: {
        authenticationMethod: "Cassandra",
        cassandraVersion: "3.11",
        clientCertificates: [{
            pem: `-----BEGIN CERTIFICATE-----
...Base64 encoded certificate...
-----END CERTIFICATE-----`,
        }],
        clusterNameOverride: "ClusterNameIllegalForAzureResource",
        delegatedManagementSubnetId: "/subscriptions/536e130b-d7d6-4ac7-98a5-de20d69588d2/resourceGroups/customer-vnet-rg/providers/Microsoft.Network/virtualNetworks/customer-vnet/subnets/management",
        externalGossipCertificates: [{
            pem: `-----BEGIN CERTIFICATE-----
...Base64 encoded certificate...
-----END CERTIFICATE-----`,
        }],
        externalSeedNodes: [
            {
                ipAddress: "10.52.221.2",
            },
            {
                ipAddress: "10.52.221.3",
            },
            {
                ipAddress: "10.52.221.4",
            },
        ],
        hoursBetweenBackups: 24,
        initialCassandraAdminPassword: "mypassword",
    },
    resourceGroupName: "cassandra-prod-rg",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cassandra_cluster = azure_native.documentdb.CassandraCluster("cassandraCluster",
    cluster_name="cassandra-prod",
    location="West US",
    properties=azure_native.documentdb.ClusterResourceResponsePropertiesArgs(
        authentication_method="Cassandra",
        cassandra_version="3.11",
        client_certificates=[azure_native.documentdb.CertificateArgs(
            pem="""-----BEGIN CERTIFICATE-----
...Base64 encoded certificate...
-----END CERTIFICATE-----""",
        )],
        cluster_name_override="ClusterNameIllegalForAzureResource",
        delegated_management_subnet_id="/subscriptions/536e130b-d7d6-4ac7-98a5-de20d69588d2/resourceGroups/customer-vnet-rg/providers/Microsoft.Network/virtualNetworks/customer-vnet/subnets/management",
        external_gossip_certificates=[azure_native.documentdb.CertificateArgs(
            pem="""-----BEGIN CERTIFICATE-----
...Base64 encoded certificate...
-----END CERTIFICATE-----""",
        )],
        external_seed_nodes=[
            azure_native.documentdb.SeedNodeArgs(
                ip_address="10.52.221.2",
            ),
            azure_native.documentdb.SeedNodeArgs(
                ip_address="10.52.221.3",
            ),
            azure_native.documentdb.SeedNodeArgs(
                ip_address="10.52.221.4",
            ),
        ],
        hours_between_backups=24,
        initial_cassandra_admin_password="mypassword",
    ),
    resource_group_name="cassandra-prod-rg",
    tags={})

```

```yaml
resources:
  cassandraCluster:
    type: azure-native:documentdb:CassandraCluster
    properties:
      clusterName: cassandra-prod
      location: West US
      properties:
        authenticationMethod: Cassandra
        cassandraVersion: '3.11'
        clientCertificates:
          - pem: |-
              -----BEGIN CERTIFICATE-----
              ...Base64 encoded certificate...
              -----END CERTIFICATE-----
        clusterNameOverride: ClusterNameIllegalForAzureResource
        delegatedManagementSubnetId: /subscriptions/536e130b-d7d6-4ac7-98a5-de20d69588d2/resourceGroups/customer-vnet-rg/providers/Microsoft.Network/virtualNetworks/customer-vnet/subnets/management
        externalGossipCertificates:
          - pem: |-
              -----BEGIN CERTIFICATE-----
              ...Base64 encoded certificate...
              -----END CERTIFICATE-----
        externalSeedNodes:
          - ipAddress: 10.52.221.2
          - ipAddress: 10.52.221.3
          - ipAddress: 10.52.221.4
        hoursBetweenBackups: 24
        initialCassandraAdminPassword: mypassword
      resourceGroupName: cassandra-prod-rg
      tags: {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:documentdb:CassandraCluster cassandra-prod /subscriptions/subid/resourceGroups/cassandra-prod-rg/providers/Microsoft.DocumentDB/cassandraClusters/cassandra-prod 
```
