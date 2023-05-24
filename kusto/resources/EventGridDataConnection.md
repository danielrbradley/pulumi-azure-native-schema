Class representing an Event Grid data connection.
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
    var eventGridDataConnection = new AzureNative.Kusto.EventGridDataConnection("eventGridDataConnection", new()
    {
        ClusterName = "kustoCluster",
        DataConnectionName = "dataConnectionTest",
        DatabaseName = "KustoDatabase1",
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
		_, err := kusto.NewEventGridDataConnection(ctx, "eventGridDataConnection", &kusto.EventGridDataConnectionArgs{
			ClusterName:        pulumi.String("kustoCluster"),
			DataConnectionName: pulumi.String("dataConnectionTest"),
			DatabaseName:       pulumi.String("KustoDatabase1"),
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
import com.pulumi.azurenative.kusto.EventGridDataConnection;
import com.pulumi.azurenative.kusto.EventGridDataConnectionArgs;
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
        var eventGridDataConnection = new EventGridDataConnection("eventGridDataConnection", EventGridDataConnectionArgs.builder()        
            .clusterName("kustoCluster")
            .dataConnectionName("dataConnectionTest")
            .databaseName("KustoDatabase1")
            .resourceGroupName("kustorptest")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const eventGridDataConnection = new azure_native.kusto.EventGridDataConnection("eventGridDataConnection", {
    clusterName: "kustoCluster",
    dataConnectionName: "dataConnectionTest",
    databaseName: "KustoDatabase1",
    resourceGroupName: "kustorptest",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

event_grid_data_connection = azure_native.kusto.EventGridDataConnection("eventGridDataConnection",
    cluster_name="kustoCluster",
    data_connection_name="dataConnectionTest",
    database_name="KustoDatabase1",
    resource_group_name="kustorptest")

```

```yaml
resources:
  eventGridDataConnection:
    type: azure-native:kusto:EventGridDataConnection
    properties:
      clusterName: kustoCluster
      dataConnectionName: dataConnectionTest
      databaseName: KustoDatabase1
      resourceGroupName: kustorptest

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
    var eventGridDataConnection = new AzureNative.Kusto.EventGridDataConnection("eventGridDataConnection", new()
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
		_, err := kusto.NewEventGridDataConnection(ctx, "eventGridDataConnection", &kusto.EventGridDataConnectionArgs{
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
import com.pulumi.azurenative.kusto.EventGridDataConnection;
import com.pulumi.azurenative.kusto.EventGridDataConnectionArgs;
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
        var eventGridDataConnection = new EventGridDataConnection("eventGridDataConnection", EventGridDataConnectionArgs.builder()        
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

const eventGridDataConnection = new azure_native.kusto.EventGridDataConnection("eventGridDataConnection", {
    clusterName: "kustoCluster",
    dataConnectionName: "dataConnectionTest",
    databaseName: "KustoDatabase8",
    resourceGroupName: "kustorptest",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

event_grid_data_connection = azure_native.kusto.EventGridDataConnection("eventGridDataConnection",
    cluster_name="kustoCluster",
    data_connection_name="dataConnectionTest",
    database_name="KustoDatabase8",
    resource_group_name="kustorptest")

```

```yaml
resources:
  eventGridDataConnection:
    type: azure-native:kusto:EventGridDataConnection
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
    var eventGridDataConnection = new AzureNative.Kusto.EventGridDataConnection("eventGridDataConnection", new()
    {
        BlobStorageEventType = "Microsoft.Storage.BlobCreated",
        ClusterName = "kustoCluster",
        ConsumerGroup = "$Default",
        DataConnectionName = "dataConnectionTest",
        DataFormat = "JSON",
        DatabaseName = "KustoDatabase8",
        DatabaseRouting = "Single",
        EventGridResourceId = "/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Storage/storageAccounts/teststorageaccount/providers/Microsoft.EventGrid/eventSubscriptions/eventSubscriptionTest",
        EventHubResourceId = "/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.EventHub/namespaces/eventhubTestns1/eventhubs/eventhubTest2",
        IgnoreFirstRecord = false,
        Kind = "EventGrid",
        Location = "westus",
        ManagedIdentityResourceId = "/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.ManagedIdentity/userAssignedIdentities/managedidentityTest1",
        MappingRuleName = "TestMapping",
        ResourceGroupName = "kustorptest",
        StorageAccountResourceId = "/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Storage/storageAccounts/teststorageaccount",
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
		_, err := kusto.NewEventGridDataConnection(ctx, "eventGridDataConnection", &kusto.EventGridDataConnectionArgs{
			BlobStorageEventType:      pulumi.String("Microsoft.Storage.BlobCreated"),
			ClusterName:               pulumi.String("kustoCluster"),
			ConsumerGroup:             pulumi.String("$Default"),
			DataConnectionName:        pulumi.String("dataConnectionTest"),
			DataFormat:                pulumi.String("JSON"),
			DatabaseName:              pulumi.String("KustoDatabase8"),
			DatabaseRouting:           pulumi.String("Single"),
			EventGridResourceId:       pulumi.String("/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Storage/storageAccounts/teststorageaccount/providers/Microsoft.EventGrid/eventSubscriptions/eventSubscriptionTest"),
			EventHubResourceId:        pulumi.String("/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.EventHub/namespaces/eventhubTestns1/eventhubs/eventhubTest2"),
			IgnoreFirstRecord:         pulumi.Bool(false),
			Kind:                      pulumi.String("EventGrid"),
			Location:                  pulumi.String("westus"),
			ManagedIdentityResourceId: pulumi.String("/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.ManagedIdentity/userAssignedIdentities/managedidentityTest1"),
			MappingRuleName:           pulumi.String("TestMapping"),
			ResourceGroupName:         pulumi.String("kustorptest"),
			StorageAccountResourceId:  pulumi.String("/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Storage/storageAccounts/teststorageaccount"),
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
import com.pulumi.azurenative.kusto.EventGridDataConnection;
import com.pulumi.azurenative.kusto.EventGridDataConnectionArgs;
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
        var eventGridDataConnection = new EventGridDataConnection("eventGridDataConnection", EventGridDataConnectionArgs.builder()        
            .blobStorageEventType("Microsoft.Storage.BlobCreated")
            .clusterName("kustoCluster")
            .consumerGroup("$Default")
            .dataConnectionName("dataConnectionTest")
            .dataFormat("JSON")
            .databaseName("KustoDatabase8")
            .databaseRouting("Single")
            .eventGridResourceId("/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Storage/storageAccounts/teststorageaccount/providers/Microsoft.EventGrid/eventSubscriptions/eventSubscriptionTest")
            .eventHubResourceId("/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.EventHub/namespaces/eventhubTestns1/eventhubs/eventhubTest2")
            .ignoreFirstRecord(false)
            .kind("EventGrid")
            .location("westus")
            .managedIdentityResourceId("/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.ManagedIdentity/userAssignedIdentities/managedidentityTest1")
            .mappingRuleName("TestMapping")
            .resourceGroupName("kustorptest")
            .storageAccountResourceId("/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Storage/storageAccounts/teststorageaccount")
            .tableName("TestTable")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const eventGridDataConnection = new azure_native.kusto.EventGridDataConnection("eventGridDataConnection", {
    blobStorageEventType: "Microsoft.Storage.BlobCreated",
    clusterName: "kustoCluster",
    consumerGroup: "$Default",
    dataConnectionName: "dataConnectionTest",
    dataFormat: "JSON",
    databaseName: "KustoDatabase8",
    databaseRouting: "Single",
    eventGridResourceId: "/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Storage/storageAccounts/teststorageaccount/providers/Microsoft.EventGrid/eventSubscriptions/eventSubscriptionTest",
    eventHubResourceId: "/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.EventHub/namespaces/eventhubTestns1/eventhubs/eventhubTest2",
    ignoreFirstRecord: false,
    kind: "EventGrid",
    location: "westus",
    managedIdentityResourceId: "/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.ManagedIdentity/userAssignedIdentities/managedidentityTest1",
    mappingRuleName: "TestMapping",
    resourceGroupName: "kustorptest",
    storageAccountResourceId: "/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Storage/storageAccounts/teststorageaccount",
    tableName: "TestTable",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

event_grid_data_connection = azure_native.kusto.EventGridDataConnection("eventGridDataConnection",
    blob_storage_event_type="Microsoft.Storage.BlobCreated",
    cluster_name="kustoCluster",
    consumer_group="$Default",
    data_connection_name="dataConnectionTest",
    data_format="JSON",
    database_name="KustoDatabase8",
    database_routing="Single",
    event_grid_resource_id="/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Storage/storageAccounts/teststorageaccount/providers/Microsoft.EventGrid/eventSubscriptions/eventSubscriptionTest",
    event_hub_resource_id="/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.EventHub/namespaces/eventhubTestns1/eventhubs/eventhubTest2",
    ignore_first_record=False,
    kind="EventGrid",
    location="westus",
    managed_identity_resource_id="/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.ManagedIdentity/userAssignedIdentities/managedidentityTest1",
    mapping_rule_name="TestMapping",
    resource_group_name="kustorptest",
    storage_account_resource_id="/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Storage/storageAccounts/teststorageaccount",
    table_name="TestTable")

```

```yaml
resources:
  eventGridDataConnection:
    type: azure-native:kusto:EventGridDataConnection
    properties:
      blobStorageEventType: Microsoft.Storage.BlobCreated
      clusterName: kustoCluster
      consumerGroup: $Default
      dataConnectionName: dataConnectionTest
      dataFormat: JSON
      databaseName: KustoDatabase8
      databaseRouting: Single
      eventGridResourceId: /subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Storage/storageAccounts/teststorageaccount/providers/Microsoft.EventGrid/eventSubscriptions/eventSubscriptionTest
      eventHubResourceId: /subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.EventHub/namespaces/eventhubTestns1/eventhubs/eventhubTest2
      ignoreFirstRecord: false
      kind: EventGrid
      location: westus
      managedIdentityResourceId: /subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.ManagedIdentity/userAssignedIdentities/managedidentityTest1
      mappingRuleName: TestMapping
      resourceGroupName: kustorptest
      storageAccountResourceId: /subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Storage/storageAccounts/teststorageaccount
      tableName: TestTable

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:kusto:EventGridDataConnection kustoCluster/KustoDatabase8/dataConnectionTest /subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Kusto/Clusters/kustoCluster/Databases/KustoDatabase8/DataConnections/KustoDataConnection9 
```
