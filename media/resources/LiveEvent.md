The live event.
API Version: 2022-11-01.
Previous API Version: 2020-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a LiveEvent
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var liveEvent = new AzureNative.Media.LiveEvent("liveEvent", new()
    {
        AccountName = "slitestmedia10",
        Description = "test event 1",
        Input = new AzureNative.Media.Inputs.LiveEventInputArgs
        {
            AccessControl = new AzureNative.Media.Inputs.LiveEventInputAccessControlArgs
            {
                Ip = new AzureNative.Media.Inputs.IPAccessControlArgs
                {
                    Allow = new[]
                    {
                        new AzureNative.Media.Inputs.IPRangeArgs
                        {
                            Address = "0.0.0.0",
                            Name = "AllowAll",
                            SubnetPrefixLength = 0,
                        },
                    },
                },
            },
            KeyFrameIntervalDuration = "PT6S",
            StreamingProtocol = "RTMP",
        },
        LiveEventName = "myLiveEvent1",
        Location = "West US",
        Preview = new AzureNative.Media.Inputs.LiveEventPreviewArgs
        {
            AccessControl = new AzureNative.Media.Inputs.LiveEventPreviewAccessControlArgs
            {
                Ip = new AzureNative.Media.Inputs.IPAccessControlArgs
                {
                    Allow = new[]
                    {
                        new AzureNative.Media.Inputs.IPRangeArgs
                        {
                            Address = "0.0.0.0",
                            Name = "AllowAll",
                            SubnetPrefixLength = 0,
                        },
                    },
                },
            },
        },
        ResourceGroupName = "mediaresources",
        Tags = 
        {
            { "tag1", "value1" },
            { "tag2", "value2" },
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.media.LiveEvent;
import com.pulumi.azurenative.media.LiveEventArgs;
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
        var liveEvent = new LiveEvent("liveEvent", LiveEventArgs.builder()        
            .accountName("slitestmedia10")
            .description("test event 1")
            .input(Map.ofEntries(
                Map.entry("accessControl", Map.of("ip", Map.of("allow", Map.ofEntries(
                    Map.entry("address", "0.0.0.0"),
                    Map.entry("name", "AllowAll"),
                    Map.entry("subnetPrefixLength", 0)
                )))),
                Map.entry("keyFrameIntervalDuration", "PT6S"),
                Map.entry("streamingProtocol", "RTMP")
            ))
            .liveEventName("myLiveEvent1")
            .location("West US")
            .preview(Map.of("accessControl", Map.of("ip", Map.of("allow", Map.ofEntries(
                Map.entry("address", "0.0.0.0"),
                Map.entry("name", "AllowAll"),
                Map.entry("subnetPrefixLength", 0)
            )))))
            .resourceGroupName("mediaresources")
            .tags(Map.ofEntries(
                Map.entry("tag1", "value1"),
                Map.entry("tag2", "value2")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const liveEvent = new azure_native.media.LiveEvent("liveEvent", {
    accountName: "slitestmedia10",
    description: "test event 1",
    input: {
        accessControl: {
            ip: {
                allow: [{
                    address: "0.0.0.0",
                    name: "AllowAll",
                    subnetPrefixLength: 0,
                }],
            },
        },
        keyFrameIntervalDuration: "PT6S",
        streamingProtocol: "RTMP",
    },
    liveEventName: "myLiveEvent1",
    location: "West US",
    preview: {
        accessControl: {
            ip: {
                allow: [{
                    address: "0.0.0.0",
                    name: "AllowAll",
                    subnetPrefixLength: 0,
                }],
            },
        },
    },
    resourceGroupName: "mediaresources",
    tags: {
        tag1: "value1",
        tag2: "value2",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

live_event = azure_native.media.LiveEvent("liveEvent",
    account_name="slitestmedia10",
    description="test event 1",
    input=azure_native.media.LiveEventInputResponseArgs(
        access_control={
            "ip": {
                "allow": [azure_native.media.IPRangeArgs(
                    address="0.0.0.0",
                    name="AllowAll",
                    subnet_prefix_length=0,
                )],
            },
        },
        key_frame_interval_duration="PT6S",
        streaming_protocol="RTMP",
    ),
    live_event_name="myLiveEvent1",
    location="West US",
    preview=azure_native.media.LiveEventPreviewResponseArgs(
        access_control={
            "ip": {
                "allow": [azure_native.media.IPRangeArgs(
                    address="0.0.0.0",
                    name="AllowAll",
                    subnet_prefix_length=0,
                )],
            },
        },
    ),
    resource_group_name="mediaresources",
    tags={
        "tag1": "value1",
        "tag2": "value2",
    })

```

```yaml
resources:
  liveEvent:
    type: azure-native:media:LiveEvent
    properties:
      accountName: slitestmedia10
      description: test event 1
      input:
        accessControl:
          ip:
            allow:
              - address: 0.0.0.0
                name: AllowAll
                subnetPrefixLength: 0
        keyFrameIntervalDuration: PT6S
        streamingProtocol: RTMP
      liveEventName: myLiveEvent1
      location: West US
      preview:
        accessControl:
          ip:
            allow:
              - address: 0.0.0.0
                name: AllowAll
                subnetPrefixLength: 0
      resourceGroupName: mediaresources
      tags:
        tag1: value1
        tag2: value2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:media:LiveEvent myLiveEvent1 /subscriptions/0a6ec948-5a62-437d-b9df-934dc7c1b722/resourceGroups/mediaresources/providers/Microsoft.Media/mediaservices/slitestmedia10/liveevents/myLiveEvent1 
```
