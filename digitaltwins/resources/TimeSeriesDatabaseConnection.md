Describes a time series database connection resource.
API Version: 2023-01-31.
Previous API Version: 2021-06-30-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or replace a time series database connection for a DigitalTwins instance with user assigned identity.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var timeSeriesDatabaseConnection = new AzureNative.DigitalTwins.TimeSeriesDatabaseConnection("timeSeriesDatabaseConnection", new()
    {
        Properties = new AzureNative.DigitalTwins.Inputs.AzureDataExplorerConnectionPropertiesArgs
        {
            AdxDatabaseName = "myDatabase",
            AdxEndpointUri = "https://mycluster.kusto.windows.net",
            AdxResourceId = "/subscriptions/c493073e-2460-45ba-a403-f3e0df1e9feg/resourceGroups/testrg/providers/Microsoft.Kusto/clusters/mycluster",
            AdxTableName = "myTable",
            ConnectionType = "AzureDataExplorer",
            EventHubEndpointUri = "sb://myeh.servicebus.windows.net/",
            EventHubEntityPath = "myeh",
            EventHubNamespaceResourceId = "/subscriptions/c493073e-2460-45ba-a403-f3e0df1e9feg/resourceGroups/testrg/providers/Microsoft.EventHub/namespaces/myeh",
            Identity = new AzureNative.DigitalTwins.Inputs.ManagedIdentityReferenceArgs
            {
                Type = "UserAssigned",
                UserAssignedIdentity = "/subscriptions/50016170-c839-41ba-a724-51e9df440b9e/resourceGroups/testrg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/testidentity",
            },
        },
        ResourceGroupName = "resRg",
        ResourceName = "myDigitalTwinsService",
        TimeSeriesDatabaseConnectionName = "myConnection",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.digitaltwins.TimeSeriesDatabaseConnection;
import com.pulumi.azurenative.digitaltwins.TimeSeriesDatabaseConnectionArgs;
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
        var timeSeriesDatabaseConnection = new TimeSeriesDatabaseConnection("timeSeriesDatabaseConnection", TimeSeriesDatabaseConnectionArgs.builder()        
            .properties(Map.ofEntries(
                Map.entry("adxDatabaseName", "myDatabase"),
                Map.entry("adxEndpointUri", "https://mycluster.kusto.windows.net"),
                Map.entry("adxResourceId", "/subscriptions/c493073e-2460-45ba-a403-f3e0df1e9feg/resourceGroups/testrg/providers/Microsoft.Kusto/clusters/mycluster"),
                Map.entry("adxTableName", "myTable"),
                Map.entry("connectionType", "AzureDataExplorer"),
                Map.entry("eventHubEndpointUri", "sb://myeh.servicebus.windows.net/"),
                Map.entry("eventHubEntityPath", "myeh"),
                Map.entry("eventHubNamespaceResourceId", "/subscriptions/c493073e-2460-45ba-a403-f3e0df1e9feg/resourceGroups/testrg/providers/Microsoft.EventHub/namespaces/myeh"),
                Map.entry("identity", Map.ofEntries(
                    Map.entry("type", "UserAssigned"),
                    Map.entry("userAssignedIdentity", "/subscriptions/50016170-c839-41ba-a724-51e9df440b9e/resourceGroups/testrg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/testidentity")
                ))
            ))
            .resourceGroupName("resRg")
            .resourceName("myDigitalTwinsService")
            .timeSeriesDatabaseConnectionName("myConnection")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const timeSeriesDatabaseConnection = new azure_native.digitaltwins.TimeSeriesDatabaseConnection("timeSeriesDatabaseConnection", {
    properties: {
        adxDatabaseName: "myDatabase",
        adxEndpointUri: "https://mycluster.kusto.windows.net",
        adxResourceId: "/subscriptions/c493073e-2460-45ba-a403-f3e0df1e9feg/resourceGroups/testrg/providers/Microsoft.Kusto/clusters/mycluster",
        adxTableName: "myTable",
        connectionType: "AzureDataExplorer",
        eventHubEndpointUri: "sb://myeh.servicebus.windows.net/",
        eventHubEntityPath: "myeh",
        eventHubNamespaceResourceId: "/subscriptions/c493073e-2460-45ba-a403-f3e0df1e9feg/resourceGroups/testrg/providers/Microsoft.EventHub/namespaces/myeh",
        identity: {
            type: "UserAssigned",
            userAssignedIdentity: "/subscriptions/50016170-c839-41ba-a724-51e9df440b9e/resourceGroups/testrg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/testidentity",
        },
    },
    resourceGroupName: "resRg",
    resourceName: "myDigitalTwinsService",
    timeSeriesDatabaseConnectionName: "myConnection",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

time_series_database_connection = azure_native.digitaltwins.TimeSeriesDatabaseConnection("timeSeriesDatabaseConnection",
    properties=azure_native.digitaltwins.AzureDataExplorerConnectionPropertiesResponseArgs(
        adx_database_name="myDatabase",
        adx_endpoint_uri="https://mycluster.kusto.windows.net",
        adx_resource_id="/subscriptions/c493073e-2460-45ba-a403-f3e0df1e9feg/resourceGroups/testrg/providers/Microsoft.Kusto/clusters/mycluster",
        adx_table_name="myTable",
        connection_type="AzureDataExplorer",
        event_hub_endpoint_uri="sb://myeh.servicebus.windows.net/",
        event_hub_entity_path="myeh",
        event_hub_namespace_resource_id="/subscriptions/c493073e-2460-45ba-a403-f3e0df1e9feg/resourceGroups/testrg/providers/Microsoft.EventHub/namespaces/myeh",
        identity=azure_native.digitaltwins.ManagedIdentityReferenceArgs(
            type="UserAssigned",
            user_assigned_identity="/subscriptions/50016170-c839-41ba-a724-51e9df440b9e/resourceGroups/testrg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/testidentity",
        ),
    ),
    resource_group_name="resRg",
    resource_name_="myDigitalTwinsService",
    time_series_database_connection_name="myConnection")

```

```yaml
resources:
  timeSeriesDatabaseConnection:
    type: azure-native:digitaltwins:TimeSeriesDatabaseConnection
    properties:
      properties:
        adxDatabaseName: myDatabase
        adxEndpointUri: https://mycluster.kusto.windows.net
        adxResourceId: /subscriptions/c493073e-2460-45ba-a403-f3e0df1e9feg/resourceGroups/testrg/providers/Microsoft.Kusto/clusters/mycluster
        adxTableName: myTable
        connectionType: AzureDataExplorer
        eventHubEndpointUri: sb://myeh.servicebus.windows.net/
        eventHubEntityPath: myeh
        eventHubNamespaceResourceId: /subscriptions/c493073e-2460-45ba-a403-f3e0df1e9feg/resourceGroups/testrg/providers/Microsoft.EventHub/namespaces/myeh
        identity:
          type: UserAssigned
          userAssignedIdentity: /subscriptions/50016170-c839-41ba-a724-51e9df440b9e/resourceGroups/testrg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/testidentity
      resourceGroupName: resRg
      resourceName: myDigitalTwinsService
      timeSeriesDatabaseConnectionName: myConnection

```

{{% /example %}}
{{% example %}}
### Create or replace a time series database connection for a DigitalTwins instance.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var timeSeriesDatabaseConnection = new AzureNative.DigitalTwins.TimeSeriesDatabaseConnection("timeSeriesDatabaseConnection", new()
    {
        Properties = new AzureNative.DigitalTwins.Inputs.AzureDataExplorerConnectionPropertiesArgs
        {
            AdxDatabaseName = "myDatabase",
            AdxEndpointUri = "https://mycluster.kusto.windows.net",
            AdxRelationshipLifecycleEventsTableName = "myRelationshipLifecycleEventsTable",
            AdxResourceId = "/subscriptions/c493073e-2460-45ba-a403-f3e0df1e9feg/resourceGroups/testrg/providers/Microsoft.Kusto/clusters/mycluster",
            AdxTableName = "myPropertyUpdatesTable",
            AdxTwinLifecycleEventsTableName = "myTwinLifecycleEventsTable",
            ConnectionType = "AzureDataExplorer",
            EventHubEndpointUri = "sb://myeh.servicebus.windows.net/",
            EventHubEntityPath = "myeh",
            EventHubNamespaceResourceId = "/subscriptions/c493073e-2460-45ba-a403-f3e0df1e9feg/resourceGroups/testrg/providers/Microsoft.EventHub/namespaces/myeh",
            RecordPropertyAndItemRemovals = "true",
        },
        ResourceGroupName = "resRg",
        ResourceName = "myDigitalTwinsService",
        TimeSeriesDatabaseConnectionName = "myConnection",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.digitaltwins.TimeSeriesDatabaseConnection;
import com.pulumi.azurenative.digitaltwins.TimeSeriesDatabaseConnectionArgs;
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
        var timeSeriesDatabaseConnection = new TimeSeriesDatabaseConnection("timeSeriesDatabaseConnection", TimeSeriesDatabaseConnectionArgs.builder()        
            .properties(Map.ofEntries(
                Map.entry("adxDatabaseName", "myDatabase"),
                Map.entry("adxEndpointUri", "https://mycluster.kusto.windows.net"),
                Map.entry("adxRelationshipLifecycleEventsTableName", "myRelationshipLifecycleEventsTable"),
                Map.entry("adxResourceId", "/subscriptions/c493073e-2460-45ba-a403-f3e0df1e9feg/resourceGroups/testrg/providers/Microsoft.Kusto/clusters/mycluster"),
                Map.entry("adxTableName", "myPropertyUpdatesTable"),
                Map.entry("adxTwinLifecycleEventsTableName", "myTwinLifecycleEventsTable"),
                Map.entry("connectionType", "AzureDataExplorer"),
                Map.entry("eventHubEndpointUri", "sb://myeh.servicebus.windows.net/"),
                Map.entry("eventHubEntityPath", "myeh"),
                Map.entry("eventHubNamespaceResourceId", "/subscriptions/c493073e-2460-45ba-a403-f3e0df1e9feg/resourceGroups/testrg/providers/Microsoft.EventHub/namespaces/myeh"),
                Map.entry("recordPropertyAndItemRemovals", "true")
            ))
            .resourceGroupName("resRg")
            .resourceName("myDigitalTwinsService")
            .timeSeriesDatabaseConnectionName("myConnection")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const timeSeriesDatabaseConnection = new azure_native.digitaltwins.TimeSeriesDatabaseConnection("timeSeriesDatabaseConnection", {
    properties: {
        adxDatabaseName: "myDatabase",
        adxEndpointUri: "https://mycluster.kusto.windows.net",
        adxRelationshipLifecycleEventsTableName: "myRelationshipLifecycleEventsTable",
        adxResourceId: "/subscriptions/c493073e-2460-45ba-a403-f3e0df1e9feg/resourceGroups/testrg/providers/Microsoft.Kusto/clusters/mycluster",
        adxTableName: "myPropertyUpdatesTable",
        adxTwinLifecycleEventsTableName: "myTwinLifecycleEventsTable",
        connectionType: "AzureDataExplorer",
        eventHubEndpointUri: "sb://myeh.servicebus.windows.net/",
        eventHubEntityPath: "myeh",
        eventHubNamespaceResourceId: "/subscriptions/c493073e-2460-45ba-a403-f3e0df1e9feg/resourceGroups/testrg/providers/Microsoft.EventHub/namespaces/myeh",
        recordPropertyAndItemRemovals: "true",
    },
    resourceGroupName: "resRg",
    resourceName: "myDigitalTwinsService",
    timeSeriesDatabaseConnectionName: "myConnection",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

time_series_database_connection = azure_native.digitaltwins.TimeSeriesDatabaseConnection("timeSeriesDatabaseConnection",
    properties=azure_native.digitaltwins.AzureDataExplorerConnectionPropertiesResponseArgs(
        adx_database_name="myDatabase",
        adx_endpoint_uri="https://mycluster.kusto.windows.net",
        adx_relationship_lifecycle_events_table_name="myRelationshipLifecycleEventsTable",
        adx_resource_id="/subscriptions/c493073e-2460-45ba-a403-f3e0df1e9feg/resourceGroups/testrg/providers/Microsoft.Kusto/clusters/mycluster",
        adx_table_name="myPropertyUpdatesTable",
        adx_twin_lifecycle_events_table_name="myTwinLifecycleEventsTable",
        connection_type="AzureDataExplorer",
        event_hub_endpoint_uri="sb://myeh.servicebus.windows.net/",
        event_hub_entity_path="myeh",
        event_hub_namespace_resource_id="/subscriptions/c493073e-2460-45ba-a403-f3e0df1e9feg/resourceGroups/testrg/providers/Microsoft.EventHub/namespaces/myeh",
        record_property_and_item_removals="true",
    ),
    resource_group_name="resRg",
    resource_name_="myDigitalTwinsService",
    time_series_database_connection_name="myConnection")

```

```yaml
resources:
  timeSeriesDatabaseConnection:
    type: azure-native:digitaltwins:TimeSeriesDatabaseConnection
    properties:
      properties:
        adxDatabaseName: myDatabase
        adxEndpointUri: https://mycluster.kusto.windows.net
        adxRelationshipLifecycleEventsTableName: myRelationshipLifecycleEventsTable
        adxResourceId: /subscriptions/c493073e-2460-45ba-a403-f3e0df1e9feg/resourceGroups/testrg/providers/Microsoft.Kusto/clusters/mycluster
        adxTableName: myPropertyUpdatesTable
        adxTwinLifecycleEventsTableName: myTwinLifecycleEventsTable
        connectionType: AzureDataExplorer
        eventHubEndpointUri: sb://myeh.servicebus.windows.net/
        eventHubEntityPath: myeh
        eventHubNamespaceResourceId: /subscriptions/c493073e-2460-45ba-a403-f3e0df1e9feg/resourceGroups/testrg/providers/Microsoft.EventHub/namespaces/myeh
        recordPropertyAndItemRemovals: 'true'
      resourceGroupName: resRg
      resourceName: myDigitalTwinsService
      timeSeriesDatabaseConnectionName: myConnection

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:digitaltwins:TimeSeriesDatabaseConnection myConnection /subscriptions/50016170-c839-41ba-a724-51e9df440b9e/resourcegroups/resRg/providers/Microsoft.DigitalTwins/digitalTwinsInstances/myDigitalTwinsService/timeSeriesDatabaseConnections/myConnection 
```
