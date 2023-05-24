Class representing a CosmosDb data connection.
API Version: 2022-12-29.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### KustoDataConnectionsCosmosDbCreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cosmosDbDataConnection = new AzureNative.Kusto.CosmosDbDataConnection("cosmosDbDataConnection", new()
    {
        ClusterName = "kustoCluster",
        CosmosDbAccountResourceId = "/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.DocumentDb/databaseAccounts/cosmosDbAccountTest1",
        CosmosDbContainer = "cosmosDbContainerTest",
        CosmosDbDatabase = "cosmosDbDatabaseTest",
        DataConnectionName = "dataConnectionTest",
        DatabaseName = "KustoDatabase1",
        Kind = "CosmosDb",
        Location = "westus",
        ManagedIdentityResourceId = "/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.ManagedIdentity/userAssignedIdentities/managedidentityTest1",
        MappingRuleName = "TestMapping",
        ResourceGroupName = "kustorptest",
        RetrievalStartDate = "2022-07-29T12:00:00.6554616Z",
        TableName = "TestTable",
    });

});


```

```go
package main

import (
	kusto "github.com/pulumi/pulumi-azure-native-sdk/kusto"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := kusto.NewCosmosDbDataConnection(ctx, "cosmosDbDataConnection", &kusto.CosmosDbDataConnectionArgs{
			ClusterName:               pulumi.String("kustoCluster"),
			CosmosDbAccountResourceId: pulumi.String("/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.DocumentDb/databaseAccounts/cosmosDbAccountTest1"),
			CosmosDbContainer:         pulumi.String("cosmosDbContainerTest"),
			CosmosDbDatabase:          pulumi.String("cosmosDbDatabaseTest"),
			DataConnectionName:        pulumi.String("dataConnectionTest"),
			DatabaseName:              pulumi.String("KustoDatabase1"),
			Kind:                      pulumi.String("CosmosDb"),
			Location:                  pulumi.String("westus"),
			ManagedIdentityResourceId: pulumi.String("/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.ManagedIdentity/userAssignedIdentities/managedidentityTest1"),
			MappingRuleName:           pulumi.String("TestMapping"),
			ResourceGroupName:         pulumi.String("kustorptest"),
			RetrievalStartDate:        pulumi.String("2022-07-29T12:00:00.6554616Z"),
			TableName:                 pulumi.String("TestTable"),
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
import com.pulumi.azurenative.kusto.CosmosDbDataConnection;
import com.pulumi.azurenative.kusto.CosmosDbDataConnectionArgs;
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
        var cosmosDbDataConnection = new CosmosDbDataConnection("cosmosDbDataConnection", CosmosDbDataConnectionArgs.builder()        
            .clusterName("kustoCluster")
            .cosmosDbAccountResourceId("/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.DocumentDb/databaseAccounts/cosmosDbAccountTest1")
            .cosmosDbContainer("cosmosDbContainerTest")
            .cosmosDbDatabase("cosmosDbDatabaseTest")
            .dataConnectionName("dataConnectionTest")
            .databaseName("KustoDatabase1")
            .kind("CosmosDb")
            .location("westus")
            .managedIdentityResourceId("/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.ManagedIdentity/userAssignedIdentities/managedidentityTest1")
            .mappingRuleName("TestMapping")
            .resourceGroupName("kustorptest")
            .retrievalStartDate("2022-07-29T12:00:00.6554616Z")
            .tableName("TestTable")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cosmosDbDataConnection = new azure_native.kusto.CosmosDbDataConnection("cosmosDbDataConnection", {
    clusterName: "kustoCluster",
    cosmosDbAccountResourceId: "/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.DocumentDb/databaseAccounts/cosmosDbAccountTest1",
    cosmosDbContainer: "cosmosDbContainerTest",
    cosmosDbDatabase: "cosmosDbDatabaseTest",
    dataConnectionName: "dataConnectionTest",
    databaseName: "KustoDatabase1",
    kind: "CosmosDb",
    location: "westus",
    managedIdentityResourceId: "/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.ManagedIdentity/userAssignedIdentities/managedidentityTest1",
    mappingRuleName: "TestMapping",
    resourceGroupName: "kustorptest",
    retrievalStartDate: "2022-07-29T12:00:00.6554616Z",
    tableName: "TestTable",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cosmos_db_data_connection = azure_native.kusto.CosmosDbDataConnection("cosmosDbDataConnection",
    cluster_name="kustoCluster",
    cosmos_db_account_resource_id="/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.DocumentDb/databaseAccounts/cosmosDbAccountTest1",
    cosmos_db_container="cosmosDbContainerTest",
    cosmos_db_database="cosmosDbDatabaseTest",
    data_connection_name="dataConnectionTest",
    database_name="KustoDatabase1",
    kind="CosmosDb",
    location="westus",
    managed_identity_resource_id="/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.ManagedIdentity/userAssignedIdentities/managedidentityTest1",
    mapping_rule_name="TestMapping",
    resource_group_name="kustorptest",
    retrieval_start_date="2022-07-29T12:00:00.6554616Z",
    table_name="TestTable")

```

```yaml
resources:
  cosmosDbDataConnection:
    type: azure-native:kusto:CosmosDbDataConnection
    properties:
      clusterName: kustoCluster
      cosmosDbAccountResourceId: /subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.DocumentDb/databaseAccounts/cosmosDbAccountTest1
      cosmosDbContainer: cosmosDbContainerTest
      cosmosDbDatabase: cosmosDbDatabaseTest
      dataConnectionName: dataConnectionTest
      databaseName: KustoDatabase1
      kind: CosmosDb
      location: westus
      managedIdentityResourceId: /subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.ManagedIdentity/userAssignedIdentities/managedidentityTest1
      mappingRuleName: TestMapping
      resourceGroupName: kustorptest
      retrievalStartDate: 2022-07-29T12:00:00.6554616Z
      tableName: TestTable

```

{{% /example %}}
{{% example %}}
### KustoDataConnectionsCreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cosmosDbDataConnection = new AzureNative.Kusto.CosmosDbDataConnection("cosmosDbDataConnection", new()
    {
        ClusterName = "kustoCluster",
        DataConnectionName = "dataConnectionTest",
        DatabaseName = "KustoDatabase8",
        ResourceGroupName = "kustorptest",
    });

});


```

```go
package main

import (
	kusto "github.com/pulumi/pulumi-azure-native-sdk/kusto"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := kusto.NewCosmosDbDataConnection(ctx, "cosmosDbDataConnection", &kusto.CosmosDbDataConnectionArgs{
			ClusterName:        pulumi.String("kustoCluster"),
			DataConnectionName: pulumi.String("dataConnectionTest"),
			DatabaseName:       pulumi.String("KustoDatabase8"),
			ResourceGroupName:  pulumi.String("kustorptest"),
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
import com.pulumi.azurenative.kusto.CosmosDbDataConnection;
import com.pulumi.azurenative.kusto.CosmosDbDataConnectionArgs;
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
        var cosmosDbDataConnection = new CosmosDbDataConnection("cosmosDbDataConnection", CosmosDbDataConnectionArgs.builder()        
            .clusterName("kustoCluster")
            .dataConnectionName("dataConnectionTest")
            .databaseName("KustoDatabase8")
            .resourceGroupName("kustorptest")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cosmosDbDataConnection = new azure_native.kusto.CosmosDbDataConnection("cosmosDbDataConnection", {
    clusterName: "kustoCluster",
    dataConnectionName: "dataConnectionTest",
    databaseName: "KustoDatabase8",
    resourceGroupName: "kustorptest",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cosmos_db_data_connection = azure_native.kusto.CosmosDbDataConnection("cosmosDbDataConnection",
    cluster_name="kustoCluster",
    data_connection_name="dataConnectionTest",
    database_name="KustoDatabase8",
    resource_group_name="kustorptest")

```

```yaml
resources:
  cosmosDbDataConnection:
    type: azure-native:kusto:CosmosDbDataConnection
    properties:
      clusterName: kustoCluster
      dataConnectionName: dataConnectionTest
      databaseName: KustoDatabase8
      resourceGroupName: kustorptest

```

{{% /example %}}
{{% example %}}
### KustoDataConnectionsEventGridCreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cosmosDbDataConnection = new AzureNative.Kusto.CosmosDbDataConnection("cosmosDbDataConnection", new()
    {
        ClusterName = "kustoCluster",
        DataConnectionName = "dataConnectionTest",
        DatabaseName = "KustoDatabase8",
        ResourceGroupName = "kustorptest",
    });

});


```

```go
package main

import (
	kusto "github.com/pulumi/pulumi-azure-native-sdk/kusto"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := kusto.NewCosmosDbDataConnection(ctx, "cosmosDbDataConnection", &kusto.CosmosDbDataConnectionArgs{
			ClusterName:        pulumi.String("kustoCluster"),
			DataConnectionName: pulumi.String("dataConnectionTest"),
			DatabaseName:       pulumi.String("KustoDatabase8"),
			ResourceGroupName:  pulumi.String("kustorptest"),
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
import com.pulumi.azurenative.kusto.CosmosDbDataConnection;
import com.pulumi.azurenative.kusto.CosmosDbDataConnectionArgs;
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
        var cosmosDbDataConnection = new CosmosDbDataConnection("cosmosDbDataConnection", CosmosDbDataConnectionArgs.builder()        
            .clusterName("kustoCluster")
            .dataConnectionName("dataConnectionTest")
            .databaseName("KustoDatabase8")
            .resourceGroupName("kustorptest")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cosmosDbDataConnection = new azure_native.kusto.CosmosDbDataConnection("cosmosDbDataConnection", {
    clusterName: "kustoCluster",
    dataConnectionName: "dataConnectionTest",
    databaseName: "KustoDatabase8",
    resourceGroupName: "kustorptest",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cosmos_db_data_connection = azure_native.kusto.CosmosDbDataConnection("cosmosDbDataConnection",
    cluster_name="kustoCluster",
    data_connection_name="dataConnectionTest",
    database_name="KustoDatabase8",
    resource_group_name="kustorptest")

```

```yaml
resources:
  cosmosDbDataConnection:
    type: azure-native:kusto:CosmosDbDataConnection
    properties:
      clusterName: kustoCluster
      dataConnectionName: dataConnectionTest
      databaseName: KustoDatabase8
      resourceGroupName: kustorptest

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:kusto:CosmosDbDataConnection kustoCluster/KustoDatabase8/dataConnectionTest /subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Kusto/Clusters/kustoCluster/Databases/KustoDatabase8/DataConnections/KustoDataConnection9 
```
