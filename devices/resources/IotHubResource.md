The description of the IoT hub.
API Version: 2021-07-02.
Previous API Version: 2020-08-31. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### IotHubResource_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var iotHubResource = new AzureNative.Devices.IotHubResource("iotHubResource", new()
    {
        Location = "centraluseuap",
        Properties = new AzureNative.Devices.Inputs.IotHubPropertiesArgs
        {
            CloudToDevice = new AzureNative.Devices.Inputs.CloudToDevicePropertiesArgs
            {
                DefaultTtlAsIso8601 = "PT1H",
                Feedback = new AzureNative.Devices.Inputs.FeedbackPropertiesArgs
                {
                    LockDurationAsIso8601 = "PT1M",
                    MaxDeliveryCount = 10,
                    TtlAsIso8601 = "PT1H",
                },
                MaxDeliveryCount = 10,
            },
            EnableDataResidency = false,
            EnableFileUploadNotifications = false,
            EventHubEndpoints = 
            {
                { "events", new AzureNative.Devices.Inputs.EventHubPropertiesArgs
                {
                    PartitionCount = 2,
                    RetentionTimeInDays = 1,
                } },
            },
            Features = "None",
            IpFilterRules = new[] {},
            MessagingEndpoints = 
            {
                { "fileNotifications", new AzureNative.Devices.Inputs.MessagingEndpointPropertiesArgs
                {
                    LockDurationAsIso8601 = "PT1M",
                    MaxDeliveryCount = 10,
                    TtlAsIso8601 = "PT1H",
                } },
            },
            MinTlsVersion = "1.2",
            NetworkRuleSets = new AzureNative.Devices.Inputs.NetworkRuleSetPropertiesArgs
            {
                ApplyToBuiltInEventHubEndpoint = true,
                DefaultAction = "Deny",
                IpRules = new[]
                {
                    new AzureNative.Devices.Inputs.NetworkRuleSetIpRuleArgs
                    {
                        Action = "Allow",
                        FilterName = "rule1",
                        IpMask = "131.117.159.53",
                    },
                    new AzureNative.Devices.Inputs.NetworkRuleSetIpRuleArgs
                    {
                        Action = "Allow",
                        FilterName = "rule2",
                        IpMask = "157.55.59.128/25",
                    },
                },
            },
            Routing = new AzureNative.Devices.Inputs.RoutingPropertiesArgs
            {
                Endpoints = new AzureNative.Devices.Inputs.RoutingEndpointsArgs
                {
                    EventHubs = new[] {},
                    ServiceBusQueues = new[] {},
                    ServiceBusTopics = new[] {},
                    StorageContainers = new[] {},
                },
                FallbackRoute = new AzureNative.Devices.Inputs.FallbackRoutePropertiesArgs
                {
                    Condition = "true",
                    EndpointNames = new[]
                    {
                        "events",
                    },
                    IsEnabled = true,
                    Name = "$fallback",
                    Source = "DeviceMessages",
                },
                Routes = new[] {},
            },
            StorageEndpoints = 
            {
                { "$default", new AzureNative.Devices.Inputs.StorageEndpointPropertiesArgs
                {
                    ConnectionString = "",
                    ContainerName = "",
                    SasTtlAsIso8601 = "PT1H",
                } },
            },
        },
        ResourceGroupName = "myResourceGroup",
        ResourceName = "testHub",
        Sku = new AzureNative.Devices.Inputs.IotHubSkuInfoArgs
        {
            Capacity = 1,
            Name = "S1",
        },
        Tags = null,
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.devices.IotHubResource;
import com.pulumi.azurenative.devices.IotHubResourceArgs;
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
        var iotHubResource = new IotHubResource("iotHubResource", IotHubResourceArgs.builder()        
            .location("centraluseuap")
            .properties(Map.ofEntries(
                Map.entry("cloudToDevice", Map.ofEntries(
                    Map.entry("defaultTtlAsIso8601", "PT1H"),
                    Map.entry("feedback", Map.ofEntries(
                        Map.entry("lockDurationAsIso8601", "PT1M"),
                        Map.entry("maxDeliveryCount", 10),
                        Map.entry("ttlAsIso8601", "PT1H")
                    )),
                    Map.entry("maxDeliveryCount", 10)
                )),
                Map.entry("enableDataResidency", false),
                Map.entry("enableFileUploadNotifications", false),
                Map.entry("eventHubEndpoints", Map.of("events", Map.ofEntries(
                    Map.entry("partitionCount", 2),
                    Map.entry("retentionTimeInDays", 1)
                ))),
                Map.entry("features", "None"),
                Map.entry("ipFilterRules", ),
                Map.entry("messagingEndpoints", Map.of("fileNotifications", Map.ofEntries(
                    Map.entry("lockDurationAsIso8601", "PT1M"),
                    Map.entry("maxDeliveryCount", 10),
                    Map.entry("ttlAsIso8601", "PT1H")
                ))),
                Map.entry("minTlsVersion", "1.2"),
                Map.entry("networkRuleSets", Map.ofEntries(
                    Map.entry("applyToBuiltInEventHubEndpoint", true),
                    Map.entry("defaultAction", "Deny"),
                    Map.entry("ipRules",                     
                        Map.ofEntries(
                            Map.entry("action", "Allow"),
                            Map.entry("filterName", "rule1"),
                            Map.entry("ipMask", "131.117.159.53")
                        ),
                        Map.ofEntries(
                            Map.entry("action", "Allow"),
                            Map.entry("filterName", "rule2"),
                            Map.entry("ipMask", "157.55.59.128/25")
                        ))
                )),
                Map.entry("routing", Map.ofEntries(
                    Map.entry("endpoints", Map.ofEntries(
                        Map.entry("eventHubs", ),
                        Map.entry("serviceBusQueues", ),
                        Map.entry("serviceBusTopics", ),
                        Map.entry("storageContainers", )
                    )),
                    Map.entry("fallbackRoute", Map.ofEntries(
                        Map.entry("condition", "true"),
                        Map.entry("endpointNames", "events"),
                        Map.entry("isEnabled", true),
                        Map.entry("name", "$fallback"),
                        Map.entry("source", "DeviceMessages")
                    )),
                    Map.entry("routes", )
                )),
                Map.entry("storageEndpoints", Map.of("$default", Map.ofEntries(
                    Map.entry("connectionString", ""),
                    Map.entry("containerName", ""),
                    Map.entry("sasTtlAsIso8601", "PT1H")
                )))
            ))
            .resourceGroupName("myResourceGroup")
            .resourceName("testHub")
            .sku(Map.ofEntries(
                Map.entry("capacity", 1),
                Map.entry("name", "S1")
            ))
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const iotHubResource = new azure_native.devices.IotHubResource("iotHubResource", {
    location: "centraluseuap",
    properties: {
        cloudToDevice: {
            defaultTtlAsIso8601: "PT1H",
            feedback: {
                lockDurationAsIso8601: "PT1M",
                maxDeliveryCount: 10,
                ttlAsIso8601: "PT1H",
            },
            maxDeliveryCount: 10,
        },
        enableDataResidency: false,
        enableFileUploadNotifications: false,
        eventHubEndpoints: {
            events: {
                partitionCount: 2,
                retentionTimeInDays: 1,
            },
        },
        features: "None",
        ipFilterRules: [],
        messagingEndpoints: {
            fileNotifications: {
                lockDurationAsIso8601: "PT1M",
                maxDeliveryCount: 10,
                ttlAsIso8601: "PT1H",
            },
        },
        minTlsVersion: "1.2",
        networkRuleSets: {
            applyToBuiltInEventHubEndpoint: true,
            defaultAction: "Deny",
            ipRules: [
                {
                    action: "Allow",
                    filterName: "rule1",
                    ipMask: "131.117.159.53",
                },
                {
                    action: "Allow",
                    filterName: "rule2",
                    ipMask: "157.55.59.128/25",
                },
            ],
        },
        routing: {
            endpoints: {
                eventHubs: [],
                serviceBusQueues: [],
                serviceBusTopics: [],
                storageContainers: [],
            },
            fallbackRoute: {
                condition: "true",
                endpointNames: ["events"],
                isEnabled: true,
                name: "$fallback",
                source: "DeviceMessages",
            },
            routes: [],
        },
        storageEndpoints: {
            $default: {
                connectionString: "",
                containerName: "",
                sasTtlAsIso8601: "PT1H",
            },
        },
    },
    resourceGroupName: "myResourceGroup",
    resourceName: "testHub",
    sku: {
        capacity: 1,
        name: "S1",
    },
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

iot_hub_resource = azure_native.devices.IotHubResource("iotHubResource",
    location="centraluseuap",
    properties=azure_native.devices.IotHubPropertiesResponseArgs(
        cloud_to_device={
            "defaultTtlAsIso8601": "PT1H",
            "feedback": azure_native.devices.FeedbackPropertiesArgs(
                lock_duration_as_iso8601="PT1M",
                max_delivery_count=10,
                ttl_as_iso8601="PT1H",
            ),
            "maxDeliveryCount": 10,
        },
        enable_data_residency=False,
        enable_file_upload_notifications=False,
        event_hub_endpoints={
            "events": azure_native.devices.EventHubPropertiesArgs(
                partition_count=2,
                retention_time_in_days=1,
            ),
        },
        features="None",
        ip_filter_rules=[],
        messaging_endpoints={
            "fileNotifications": azure_native.devices.MessagingEndpointPropertiesArgs(
                lock_duration_as_iso8601="PT1M",
                max_delivery_count=10,
                ttl_as_iso8601="PT1H",
            ),
        },
        min_tls_version="1.2",
        network_rule_sets={
            "applyToBuiltInEventHubEndpoint": True,
            "defaultAction": "Deny",
            "ipRules": [
                azure_native.devices.NetworkRuleSetIpRuleArgs(
                    action="Allow",
                    filter_name="rule1",
                    ip_mask="131.117.159.53",
                ),
                azure_native.devices.NetworkRuleSetIpRuleArgs(
                    action="Allow",
                    filter_name="rule2",
                    ip_mask="157.55.59.128/25",
                ),
            ],
        },
        routing={
            "endpoints": {
                "eventHubs": [],
                "serviceBusQueues": [],
                "serviceBusTopics": [],
                "storageContainers": [],
            },
            "fallbackRoute": azure_native.devices.FallbackRoutePropertiesArgs(
                condition="true",
                endpoint_names=["events"],
                is_enabled=True,
                name="$fallback",
                source="DeviceMessages",
            ),
            "routes": [],
        },
        storage_endpoints={
            "$default": azure_native.devices.StorageEndpointPropertiesArgs(
                connection_string="",
                container_name="",
                sas_ttl_as_iso8601="PT1H",
            ),
        },
    ),
    resource_group_name="myResourceGroup",
    resource_name_="testHub",
    sku=azure_native.devices.IotHubSkuInfoArgs(
        capacity=1,
        name="S1",
    ),
    tags={})

```

```yaml
resources:
  iotHubResource:
    type: azure-native:devices:IotHubResource
    properties:
      location: centraluseuap
      properties:
        cloudToDevice:
          defaultTtlAsIso8601: PT1H
          feedback:
            lockDurationAsIso8601: PT1M
            maxDeliveryCount: 10
            ttlAsIso8601: PT1H
          maxDeliveryCount: 10
        enableDataResidency: false
        enableFileUploadNotifications: false
        eventHubEndpoints:
          events:
            partitionCount: 2
            retentionTimeInDays: 1
        features: None
        ipFilterRules: []
        messagingEndpoints:
          fileNotifications:
            lockDurationAsIso8601: PT1M
            maxDeliveryCount: 10
            ttlAsIso8601: PT1H
        minTlsVersion: '1.2'
        networkRuleSets:
          applyToBuiltInEventHubEndpoint: true
          defaultAction: Deny
          ipRules:
            - action: Allow
              filterName: rule1
              ipMask: 131.117.159.53
            - action: Allow
              filterName: rule2
              ipMask: 157.55.59.128/25
        routing:
          endpoints:
            eventHubs: []
            serviceBusQueues: []
            serviceBusTopics: []
            storageContainers: []
          fallbackRoute:
            condition: 'true'
            endpointNames:
              - events
            isEnabled: true
            name: $fallback
            source: DeviceMessages
          routes: []
        storageEndpoints:
          $default:
            connectionString:
            containerName:
            sasTtlAsIso8601: PT1H
      resourceGroupName: myResourceGroup
      resourceName: testHub
      sku:
        capacity: 1
        name: S1
      tags: {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devices:IotHubResource testHub /subscriptions/ae24ff83-d2ca-4fc8-9717-05dae4bba489/resourceGroups/myResourceGroup/providers/Microsoft.Devices/IotHubs/testHub 
```
