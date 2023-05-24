A hub setting
API Version: 2023-02-01.
Previous API Version: 2021-10-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### WebPubSubHubs_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var webPubSubHub = new AzureNative.WebPubSub.WebPubSubHub("webPubSubHub", new()
    {
        HubName = "exampleHub",
        Properties = new AzureNative.WebPubSub.Inputs.WebPubSubHubPropertiesArgs
        {
            AnonymousConnectPolicy = "allow",
            EventHandlers = new[]
            {
                new AzureNative.WebPubSub.Inputs.EventHandlerArgs
                {
                    Auth = new AzureNative.WebPubSub.Inputs.UpstreamAuthSettingsArgs
                    {
                        ManagedIdentity = new AzureNative.WebPubSub.Inputs.ManagedIdentitySettingsArgs
                        {
                            Resource = "abc",
                        },
                        Type = "ManagedIdentity",
                    },
                    SystemEvents = new[]
                    {
                        "connect",
                        "connected",
                    },
                    UrlTemplate = "http://host.com",
                    UserEventPattern = "*",
                },
            },
            EventListeners = new[]
            {
                new AzureNative.WebPubSub.Inputs.EventListenerArgs
                {
                    Endpoint = 
                    {
                        { "eventHubName", "eventHubName1" },
                        { "fullyQualifiedNamespace", "example.servicebus.windows.net" },
                        { "type", "EventHub" },
                    },
                    Filter = 
                    {
                        { "systemEvents", new[]
                        {
                            "connected",
                            "disconnected",
                        } },
                        { "type", "EventName" },
                        { "userEventPattern", "*" },
                    },
                },
            },
        },
        ResourceGroupName = "myResourceGroup",
        ResourceName = "myWebPubSubService",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.webpubsub.WebPubSubHub;
import com.pulumi.azurenative.webpubsub.WebPubSubHubArgs;
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
        var webPubSubHub = new WebPubSubHub("webPubSubHub", WebPubSubHubArgs.builder()        
            .hubName("exampleHub")
            .properties(Map.ofEntries(
                Map.entry("anonymousConnectPolicy", "allow"),
                Map.entry("eventHandlers", Map.ofEntries(
                    Map.entry("auth", Map.ofEntries(
                        Map.entry("managedIdentity", Map.of("resource", "abc")),
                        Map.entry("type", "ManagedIdentity")
                    )),
                    Map.entry("systemEvents",                     
                        "connect",
                        "connected"),
                    Map.entry("urlTemplate", "http://host.com"),
                    Map.entry("userEventPattern", "*")
                )),
                Map.entry("eventListeners", Map.ofEntries(
                    Map.entry("endpoint", Map.ofEntries(
                        Map.entry("eventHubName", "eventHubName1"),
                        Map.entry("fullyQualifiedNamespace", "example.servicebus.windows.net"),
                        Map.entry("type", "EventHub")
                    )),
                    Map.entry("filter", Map.ofEntries(
                        Map.entry("systemEvents",                         
                            "connected",
                            "disconnected"),
                        Map.entry("type", "EventName"),
                        Map.entry("userEventPattern", "*")
                    ))
                ))
            ))
            .resourceGroupName("myResourceGroup")
            .resourceName("myWebPubSubService")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const webPubSubHub = new azure_native.webpubsub.WebPubSubHub("webPubSubHub", {
    hubName: "exampleHub",
    properties: {
        anonymousConnectPolicy: "allow",
        eventHandlers: [{
            auth: {
                managedIdentity: {
                    resource: "abc",
                },
                type: "ManagedIdentity",
            },
            systemEvents: [
                "connect",
                "connected",
            ],
            urlTemplate: "http://host.com",
            userEventPattern: "*",
        }],
        eventListeners: [{
            endpoint: {
                eventHubName: "eventHubName1",
                fullyQualifiedNamespace: "example.servicebus.windows.net",
                type: "EventHub",
            },
            filter: {
                systemEvents: [
                    "connected",
                    "disconnected",
                ],
                type: "EventName",
                userEventPattern: "*",
            },
        }],
    },
    resourceGroupName: "myResourceGroup",
    resourceName: "myWebPubSubService",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

web_pub_sub_hub = azure_native.webpubsub.WebPubSubHub("webPubSubHub",
    hub_name="exampleHub",
    properties=azure_native.webpubsub.WebPubSubHubPropertiesResponseArgs(
        anonymous_connect_policy="allow",
        event_handlers=[{
            "auth": {
                "managedIdentity": azure_native.webpubsub.ManagedIdentitySettingsArgs(
                    resource="abc",
                ),
                "type": "ManagedIdentity",
            },
            "systemEvents": [
                "connect",
                "connected",
            ],
            "urlTemplate": "http://host.com",
            "userEventPattern": "*",
        }],
        event_listeners=[{
            "endpoint": azure_native.webpubsub.EventHubEndpointResponseArgs(
                event_hub_name="eventHubName1",
                fully_qualified_namespace="example.servicebus.windows.net",
                type="EventHub",
            ),
            "filter": azure_native.webpubsub.EventNameFilterResponseArgs(
                system_events=[
                    "connected",
                    "disconnected",
                ],
                type="EventName",
                user_event_pattern="*",
            ),
        }],
    ),
    resource_group_name="myResourceGroup",
    resource_name_="myWebPubSubService")

```

```yaml
resources:
  webPubSubHub:
    type: azure-native:webpubsub:WebPubSubHub
    properties:
      hubName: exampleHub
      properties:
        anonymousConnectPolicy: allow
        eventHandlers:
          - auth:
              managedIdentity:
                resource: abc
              type: ManagedIdentity
            systemEvents:
              - connect
              - connected
            urlTemplate: http://host.com
            userEventPattern: '*'
        eventListeners:
          - endpoint:
              eventHubName: eventHubName1
              fullyQualifiedNamespace: example.servicebus.windows.net
              type: EventHub
            filter:
              systemEvents:
                - connected
                - disconnected
              type: EventName
              userEventPattern: '*'
      resourceGroupName: myResourceGroup
      resourceName: myWebPubSubService

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:webpubsub:WebPubSubHub exampleHub /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.SignalRService/WebPubSub/myWebPubSubService/hubs/exampleHub 
```
