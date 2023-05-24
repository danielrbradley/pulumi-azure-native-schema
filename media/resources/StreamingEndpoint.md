The streaming endpoint.
API Version: 2022-11-01.
Previous API Version: 2020-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a streaming endpoint
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var streamingEndpoint = new AzureNative.Media.StreamingEndpoint("streamingEndpoint", new()
    {
        AccessControl = new AzureNative.Media.Inputs.StreamingEndpointAccessControlArgs
        {
            Akamai = new AzureNative.Media.Inputs.AkamaiAccessControlArgs
            {
                AkamaiSignatureHeaderAuthenticationKeyList = new[]
                {
                    new AzureNative.Media.Inputs.AkamaiSignatureHeaderAuthenticationKeyArgs
                    {
                        Base64Key = "dGVzdGlkMQ==",
                        Expiration = "2029-12-31T16:00:00-08:00",
                        Identifier = "id1",
                    },
                    new AzureNative.Media.Inputs.AkamaiSignatureHeaderAuthenticationKeyArgs
                    {
                        Base64Key = "dGVzdGlkMQ==",
                        Expiration = "2030-12-31T16:00:00-08:00",
                        Identifier = "id2",
                    },
                },
            },
            Ip = new AzureNative.Media.Inputs.IPAccessControlArgs
            {
                Allow = new[]
                {
                    new AzureNative.Media.Inputs.IPRangeArgs
                    {
                        Address = "192.168.1.1",
                        Name = "AllowedIp",
                    },
                },
            },
        },
        AccountName = "slitestmedia10",
        AvailabilitySetName = "availableset",
        CdnEnabled = false,
        Description = "test event 1",
        Location = "West US",
        ResourceGroupName = "mediaresources",
        ScaleUnits = 1,
        StreamingEndpointName = "myStreamingEndpoint1",
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
import com.pulumi.azurenative.media.StreamingEndpoint;
import com.pulumi.azurenative.media.StreamingEndpointArgs;
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
        var streamingEndpoint = new StreamingEndpoint("streamingEndpoint", StreamingEndpointArgs.builder()        
            .accessControl(Map.ofEntries(
                Map.entry("akamai", Map.of("akamaiSignatureHeaderAuthenticationKeyList",                 
                    Map.ofEntries(
                        Map.entry("base64Key", "dGVzdGlkMQ=="),
                        Map.entry("expiration", "2029-12-31T16:00:00-08:00"),
                        Map.entry("identifier", "id1")
                    ),
                    Map.ofEntries(
                        Map.entry("base64Key", "dGVzdGlkMQ=="),
                        Map.entry("expiration", "2030-12-31T16:00:00-08:00"),
                        Map.entry("identifier", "id2")
                    ))),
                Map.entry("ip", Map.of("allow", Map.ofEntries(
                    Map.entry("address", "192.168.1.1"),
                    Map.entry("name", "AllowedIp")
                )))
            ))
            .accountName("slitestmedia10")
            .availabilitySetName("availableset")
            .cdnEnabled(false)
            .description("test event 1")
            .location("West US")
            .resourceGroupName("mediaresources")
            .scaleUnits(1)
            .streamingEndpointName("myStreamingEndpoint1")
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

const streamingEndpoint = new azure_native.media.StreamingEndpoint("streamingEndpoint", {
    accessControl: {
        akamai: {
            akamaiSignatureHeaderAuthenticationKeyList: [
                {
                    base64Key: "dGVzdGlkMQ==",
                    expiration: "2029-12-31T16:00:00-08:00",
                    identifier: "id1",
                },
                {
                    base64Key: "dGVzdGlkMQ==",
                    expiration: "2030-12-31T16:00:00-08:00",
                    identifier: "id2",
                },
            ],
        },
        ip: {
            allow: [{
                address: "192.168.1.1",
                name: "AllowedIp",
            }],
        },
    },
    accountName: "slitestmedia10",
    availabilitySetName: "availableset",
    cdnEnabled: false,
    description: "test event 1",
    location: "West US",
    resourceGroupName: "mediaresources",
    scaleUnits: 1,
    streamingEndpointName: "myStreamingEndpoint1",
    tags: {
        tag1: "value1",
        tag2: "value2",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

streaming_endpoint = azure_native.media.StreamingEndpoint("streamingEndpoint",
    access_control=azure_native.media.StreamingEndpointAccessControlResponseArgs(
        akamai={
            "akamaiSignatureHeaderAuthenticationKeyList": [
                azure_native.media.AkamaiSignatureHeaderAuthenticationKeyArgs(
                    base64_key="dGVzdGlkMQ==",
                    expiration="2029-12-31T16:00:00-08:00",
                    identifier="id1",
                ),
                azure_native.media.AkamaiSignatureHeaderAuthenticationKeyArgs(
                    base64_key="dGVzdGlkMQ==",
                    expiration="2030-12-31T16:00:00-08:00",
                    identifier="id2",
                ),
            ],
        },
        ip={
            "allow": [azure_native.media.IPRangeArgs(
                address="192.168.1.1",
                name="AllowedIp",
            )],
        },
    ),
    account_name="slitestmedia10",
    availability_set_name="availableset",
    cdn_enabled=False,
    description="test event 1",
    location="West US",
    resource_group_name="mediaresources",
    scale_units=1,
    streaming_endpoint_name="myStreamingEndpoint1",
    tags={
        "tag1": "value1",
        "tag2": "value2",
    })

```

```yaml
resources:
  streamingEndpoint:
    type: azure-native:media:StreamingEndpoint
    properties:
      accessControl:
        akamai:
          akamaiSignatureHeaderAuthenticationKeyList:
            - base64Key: dGVzdGlkMQ==
              expiration: 2029-12-31T16:00:00-08:00
              identifier: id1
            - base64Key: dGVzdGlkMQ==
              expiration: 2030-12-31T16:00:00-08:00
              identifier: id2
        ip:
          allow:
            - address: 192.168.1.1
              name: AllowedIp
      accountName: slitestmedia10
      availabilitySetName: availableset
      cdnEnabled: false
      description: test event 1
      location: West US
      resourceGroupName: mediaresources
      scaleUnits: 1
      streamingEndpointName: myStreamingEndpoint1
      tags:
        tag1: value1
        tag2: value2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:media:StreamingEndpoint myStreamingEndpoint1 /subscriptions/0a6ec948-5a62-437d-b9df-934dc7c1b722/resourceGroups/mediaresources/providers/Microsoft.Media/mediaservices/slitestmedia10/streamingendpoints/myStreamingEndpoint1 
```
