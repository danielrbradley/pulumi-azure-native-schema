An event source that receives its data from an Azure EventHub.
API Version: 2020-05-15.
Previous API Version: 2020-05-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateEventHubEventSource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var eventHubEventSource = new AzureNative.TimeSeriesInsights.EventHubEventSource("eventHubEventSource", new()
    {
        ConsumerGroupName = "cgn",
        EnvironmentName = "env1",
        EventHubName = "ehn",
        EventSourceName = "es1",
        EventSourceResourceId = "somePathInArm",
        KeyName = "managementKey",
        Kind = "Microsoft.EventHub",
        Location = "West US",
        ResourceGroupName = "rg1",
        ServiceBusNamespace = "sbn",
        SharedAccessKey = "someSecretvalue",
        TimestampPropertyName = "someTimestampProperty",
        Type = "EarliestAvailable",
    });

});


```

```go
package main

import (
	timeseriesinsights "github.com/pulumi/pulumi-azure-native-sdk/timeseriesinsights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := timeseriesinsights.NewEventHubEventSource(ctx, "eventHubEventSource", &timeseriesinsights.EventHubEventSourceArgs{
			ConsumerGroupName:     pulumi.String("cgn"),
			EnvironmentName:       pulumi.String("env1"),
			EventHubName:          pulumi.String("ehn"),
			EventSourceName:       pulumi.String("es1"),
			EventSourceResourceId: pulumi.String("somePathInArm"),
			KeyName:               pulumi.String("managementKey"),
			Kind:                  pulumi.String("Microsoft.EventHub"),
			Location:              pulumi.String("West US"),
			ResourceGroupName:     pulumi.String("rg1"),
			ServiceBusNamespace:   pulumi.String("sbn"),
			SharedAccessKey:       pulumi.String("someSecretvalue"),
			TimestampPropertyName: pulumi.String("someTimestampProperty"),
			Type:                  pulumi.String("EarliestAvailable"),
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
import com.pulumi.azurenative.timeseriesinsights.EventHubEventSource;
import com.pulumi.azurenative.timeseriesinsights.EventHubEventSourceArgs;
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
        var eventHubEventSource = new EventHubEventSource("eventHubEventSource", EventHubEventSourceArgs.builder()        
            .consumerGroupName("cgn")
            .environmentName("env1")
            .eventHubName("ehn")
            .eventSourceName("es1")
            .eventSourceResourceId("somePathInArm")
            .keyName("managementKey")
            .kind("Microsoft.EventHub")
            .location("West US")
            .resourceGroupName("rg1")
            .serviceBusNamespace("sbn")
            .sharedAccessKey("someSecretvalue")
            .timestampPropertyName("someTimestampProperty")
            .type("EarliestAvailable")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const eventHubEventSource = new azure_native.timeseriesinsights.EventHubEventSource("eventHubEventSource", {
    consumerGroupName: "cgn",
    environmentName: "env1",
    eventHubName: "ehn",
    eventSourceName: "es1",
    eventSourceResourceId: "somePathInArm",
    keyName: "managementKey",
    kind: "Microsoft.EventHub",
    location: "West US",
    resourceGroupName: "rg1",
    serviceBusNamespace: "sbn",
    sharedAccessKey: "someSecretvalue",
    timestampPropertyName: "someTimestampProperty",
    type: "EarliestAvailable",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

event_hub_event_source = azure_native.timeseriesinsights.EventHubEventSource("eventHubEventSource",
    consumer_group_name="cgn",
    environment_name="env1",
    event_hub_name="ehn",
    event_source_name="es1",
    event_source_resource_id="somePathInArm",
    key_name="managementKey",
    kind="Microsoft.EventHub",
    location="West US",
    resource_group_name="rg1",
    service_bus_namespace="sbn",
    shared_access_key="someSecretvalue",
    timestamp_property_name="someTimestampProperty",
    type="EarliestAvailable")

```

```yaml
resources:
  eventHubEventSource:
    type: azure-native:timeseriesinsights:EventHubEventSource
    properties:
      consumerGroupName: cgn
      environmentName: env1
      eventHubName: ehn
      eventSourceName: es1
      eventSourceResourceId: somePathInArm
      keyName: managementKey
      kind: Microsoft.EventHub
      location: West US
      resourceGroupName: rg1
      serviceBusNamespace: sbn
      sharedAccessKey: someSecretvalue
      timestampPropertyName: someTimestampProperty
      type: EarliestAvailable

```

{{% /example %}}
{{% example %}}
### EventSourcesCreateEventHubWithCustomEnquedTime
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var eventHubEventSource = new AzureNative.TimeSeriesInsights.EventHubEventSource("eventHubEventSource", new()
    {
        ConsumerGroupName = "cgn",
        EnvironmentName = "env1",
        EventHubName = "ehn",
        EventSourceName = "es1",
        EventSourceResourceId = "somePathInArm",
        KeyName = "managementKey",
        Kind = "Microsoft.EventHub",
        Location = "West US",
        ResourceGroupName = "rg1",
        ServiceBusNamespace = "sbn",
        SharedAccessKey = "someSecretvalue",
        Time = "2017-04-01T19:20:33.2288820Z",
        TimestampPropertyName = "someTimestampProperty",
        Type = "CustomEnqueuedTime",
    });

});


```

```go
package main

import (
	timeseriesinsights "github.com/pulumi/pulumi-azure-native-sdk/timeseriesinsights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := timeseriesinsights.NewEventHubEventSource(ctx, "eventHubEventSource", &timeseriesinsights.EventHubEventSourceArgs{
			ConsumerGroupName:     pulumi.String("cgn"),
			EnvironmentName:       pulumi.String("env1"),
			EventHubName:          pulumi.String("ehn"),
			EventSourceName:       pulumi.String("es1"),
			EventSourceResourceId: pulumi.String("somePathInArm"),
			KeyName:               pulumi.String("managementKey"),
			Kind:                  pulumi.String("Microsoft.EventHub"),
			Location:              pulumi.String("West US"),
			ResourceGroupName:     pulumi.String("rg1"),
			ServiceBusNamespace:   pulumi.String("sbn"),
			SharedAccessKey:       pulumi.String("someSecretvalue"),
			Time:                  pulumi.String("2017-04-01T19:20:33.2288820Z"),
			TimestampPropertyName: pulumi.String("someTimestampProperty"),
			Type:                  pulumi.String("CustomEnqueuedTime"),
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
import com.pulumi.azurenative.timeseriesinsights.EventHubEventSource;
import com.pulumi.azurenative.timeseriesinsights.EventHubEventSourceArgs;
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
        var eventHubEventSource = new EventHubEventSource("eventHubEventSource", EventHubEventSourceArgs.builder()        
            .consumerGroupName("cgn")
            .environmentName("env1")
            .eventHubName("ehn")
            .eventSourceName("es1")
            .eventSourceResourceId("somePathInArm")
            .keyName("managementKey")
            .kind("Microsoft.EventHub")
            .location("West US")
            .resourceGroupName("rg1")
            .serviceBusNamespace("sbn")
            .sharedAccessKey("someSecretvalue")
            .time("2017-04-01T19:20:33.2288820Z")
            .timestampPropertyName("someTimestampProperty")
            .type("CustomEnqueuedTime")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const eventHubEventSource = new azure_native.timeseriesinsights.EventHubEventSource("eventHubEventSource", {
    consumerGroupName: "cgn",
    environmentName: "env1",
    eventHubName: "ehn",
    eventSourceName: "es1",
    eventSourceResourceId: "somePathInArm",
    keyName: "managementKey",
    kind: "Microsoft.EventHub",
    location: "West US",
    resourceGroupName: "rg1",
    serviceBusNamespace: "sbn",
    sharedAccessKey: "someSecretvalue",
    time: "2017-04-01T19:20:33.2288820Z",
    timestampPropertyName: "someTimestampProperty",
    type: "CustomEnqueuedTime",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

event_hub_event_source = azure_native.timeseriesinsights.EventHubEventSource("eventHubEventSource",
    consumer_group_name="cgn",
    environment_name="env1",
    event_hub_name="ehn",
    event_source_name="es1",
    event_source_resource_id="somePathInArm",
    key_name="managementKey",
    kind="Microsoft.EventHub",
    location="West US",
    resource_group_name="rg1",
    service_bus_namespace="sbn",
    shared_access_key="someSecretvalue",
    time="2017-04-01T19:20:33.2288820Z",
    timestamp_property_name="someTimestampProperty",
    type="CustomEnqueuedTime")

```

```yaml
resources:
  eventHubEventSource:
    type: azure-native:timeseriesinsights:EventHubEventSource
    properties:
      consumerGroupName: cgn
      environmentName: env1
      eventHubName: ehn
      eventSourceName: es1
      eventSourceResourceId: somePathInArm
      keyName: managementKey
      kind: Microsoft.EventHub
      location: West US
      resourceGroupName: rg1
      serviceBusNamespace: sbn
      sharedAccessKey: someSecretvalue
      time: 2017-04-01T19:20:33.2288820Z
      timestampPropertyName: someTimestampProperty
      type: CustomEnqueuedTime

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:timeseriesinsights:EventHubEventSource es1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.TimeSeriesInsights/Environments/env1/eventSources/es1 
```
