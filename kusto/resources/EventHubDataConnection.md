Class representing an event hub data connection.
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
    var eventHubDataConnection = new AzureNative.Kusto.EventHubDataConnection("eventHubDataConnection", new()
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
		_, err := kusto.NewEventHubDataConnection(ctx, "eventHubDataConnection", &kusto.EventHubDataConnectionArgs{
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
import com.pulumi.azurenative.kusto.EventHubDataConnection;
import com.pulumi.azurenative.kusto.EventHubDataConnectionArgs;
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
        var eventHubDataConnection = new EventHubDataConnection("eventHubDataConnection", EventHubDataConnectionArgs.builder()        
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

const eventHubDataConnection = new azure_native.kusto.EventHubDataConnection("eventHubDataConnection", {
    clusterName: "kustoCluster",
    dataConnectionName: "dataConnectionTest",
    databaseName: "KustoDatabase1",
    resourceGroupName: "kustorptest",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

event_hub_data_connection = azure_native.kusto.EventHubDataConnection("eventHubDataConnection",
    cluster_name="kustoCluster",
    data_connection_name="dataConnectionTest",
    database_name="KustoDatabase1",
    resource_group_name="kustorptest")

```

```yaml
resources:
  eventHubDataConnection:
    type: azure-native:kusto:EventHubDataConnection
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
    var eventHubDataConnection = new AzureNative.Kusto.EventHubDataConnection("eventHubDataConnection", new()
    {
        ClusterName = "kustoCluster",
        ConsumerGroup = "testConsumerGroup1",
        DataConnectionName = "dataConnectionTest",
        DatabaseName = "KustoDatabase8",
        EventHubResourceId = "/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.EventHub/namespaces/eventhubTestns1/eventhubs/eventhubTest1",
        Kind = "EventHub",
        Location = "westus",
        ManagedIdentityResourceId = "/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.ManagedIdentity/userAssignedIdentities/managedidentityTest1",
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
		_, err := kusto.NewEventHubDataConnection(ctx, "eventHubDataConnection", &kusto.EventHubDataConnectionArgs{
			ClusterName:               pulumi.String("kustoCluster"),
			ConsumerGroup:             pulumi.String("testConsumerGroup1"),
			DataConnectionName:        pulumi.String("dataConnectionTest"),
			DatabaseName:              pulumi.String("KustoDatabase8"),
			EventHubResourceId:        pulumi.String("/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.EventHub/namespaces/eventhubTestns1/eventhubs/eventhubTest1"),
			Kind:                      pulumi.String("EventHub"),
			Location:                  pulumi.String("westus"),
			ManagedIdentityResourceId: pulumi.String("/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.ManagedIdentity/userAssignedIdentities/managedidentityTest1"),
			ResourceGroupName:         pulumi.String("kustorptest"),
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
import com.pulumi.azurenative.kusto.EventHubDataConnection;
import com.pulumi.azurenative.kusto.EventHubDataConnectionArgs;
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
        var eventHubDataConnection = new EventHubDataConnection("eventHubDataConnection", EventHubDataConnectionArgs.builder()        
            .clusterName("kustoCluster")
            .consumerGroup("testConsumerGroup1")
            .dataConnectionName("dataConnectionTest")
            .databaseName("KustoDatabase8")
            .eventHubResourceId("/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.EventHub/namespaces/eventhubTestns1/eventhubs/eventhubTest1")
            .kind("EventHub")
            .location("westus")
            .managedIdentityResourceId("/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.ManagedIdentity/userAssignedIdentities/managedidentityTest1")
            .resourceGroupName("kustorptest")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const eventHubDataConnection = new azure_native.kusto.EventHubDataConnection("eventHubDataConnection", {
    clusterName: "kustoCluster",
    consumerGroup: "testConsumerGroup1",
    dataConnectionName: "dataConnectionTest",
    databaseName: "KustoDatabase8",
    eventHubResourceId: "/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.EventHub/namespaces/eventhubTestns1/eventhubs/eventhubTest1",
    kind: "EventHub",
    location: "westus",
    managedIdentityResourceId: "/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.ManagedIdentity/userAssignedIdentities/managedidentityTest1",
    resourceGroupName: "kustorptest",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

event_hub_data_connection = azure_native.kusto.EventHubDataConnection("eventHubDataConnection",
    cluster_name="kustoCluster",
    consumer_group="testConsumerGroup1",
    data_connection_name="dataConnectionTest",
    database_name="KustoDatabase8",
    event_hub_resource_id="/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.EventHub/namespaces/eventhubTestns1/eventhubs/eventhubTest1",
    kind="EventHub",
    location="westus",
    managed_identity_resource_id="/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.ManagedIdentity/userAssignedIdentities/managedidentityTest1",
    resource_group_name="kustorptest")

```

```yaml
resources:
  eventHubDataConnection:
    type: azure-native:kusto:EventHubDataConnection
    properties:
      clusterName: kustoCluster
      consumerGroup: testConsumerGroup1
      dataConnectionName: dataConnectionTest
      databaseName: KustoDatabase8
      eventHubResourceId: /subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.EventHub/namespaces/eventhubTestns1/eventhubs/eventhubTest1
      kind: EventHub
      location: westus
      managedIdentityResourceId: /subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.ManagedIdentity/userAssignedIdentities/managedidentityTest1
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
    var eventHubDataConnection = new AzureNative.Kusto.EventHubDataConnection("eventHubDataConnection", new()
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
		_, err := kusto.NewEventHubDataConnection(ctx, "eventHubDataConnection", &kusto.EventHubDataConnectionArgs{
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
import com.pulumi.azurenative.kusto.EventHubDataConnection;
import com.pulumi.azurenative.kusto.EventHubDataConnectionArgs;
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
        var eventHubDataConnection = new EventHubDataConnection("eventHubDataConnection", EventHubDataConnectionArgs.builder()        
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

const eventHubDataConnection = new azure_native.kusto.EventHubDataConnection("eventHubDataConnection", {
    clusterName: "kustoCluster",
    dataConnectionName: "dataConnectionTest",
    databaseName: "KustoDatabase8",
    resourceGroupName: "kustorptest",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

event_hub_data_connection = azure_native.kusto.EventHubDataConnection("eventHubDataConnection",
    cluster_name="kustoCluster",
    data_connection_name="dataConnectionTest",
    database_name="KustoDatabase8",
    resource_group_name="kustorptest")

```

```yaml
resources:
  eventHubDataConnection:
    type: azure-native:kusto:EventHubDataConnection
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
$ pulumi import azure-native:kusto:EventHubDataConnection kustoCluster/KustoDatabase8/dataConnectionTest /subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Kusto/Clusters/kustoCluster/Databases/KustoDatabase8/DataConnections/KustoDataConnection9 
```
