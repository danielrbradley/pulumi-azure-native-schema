AFDOrigin group comprising of origins is used for load balancing to origins when the content cannot be served from CDN.
API Version: 2021-06-01.
Previous API Version: 2020-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### AFDOriginGroups_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var afdOriginGroup = new AzureNative.Cdn.AFDOriginGroup("afdOriginGroup", new()
    {
        HealthProbeSettings = new AzureNative.Cdn.Inputs.HealthProbeParametersArgs
        {
            ProbeIntervalInSeconds = 10,
            ProbePath = "/path2",
            ProbeProtocol = AzureNative.Cdn.ProbeProtocol.NotSet,
            ProbeRequestType = AzureNative.Cdn.HealthProbeRequestType.NotSet,
        },
        LoadBalancingSettings = new AzureNative.Cdn.Inputs.LoadBalancingSettingsParametersArgs
        {
            AdditionalLatencyInMilliseconds = 1000,
            SampleSize = 3,
            SuccessfulSamplesRequired = 3,
        },
        OriginGroupName = "origingroup1",
        ProfileName = "profile1",
        ResourceGroupName = "RG",
        TrafficRestorationTimeToHealedOrNewEndpointsInMinutes = 5,
    });

});


```

```go
package main

import (
	cdn "github.com/pulumi/pulumi-azure-native-sdk/cdn"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := cdn.NewAFDOriginGroup(ctx, "afdOriginGroup", &cdn.AFDOriginGroupArgs{
			HealthProbeSettings: &cdn.HealthProbeParametersArgs{
				ProbeIntervalInSeconds: pulumi.Int(10),
				ProbePath:              pulumi.String("/path2"),
				ProbeProtocol:          cdn.ProbeProtocolNotSet,
				ProbeRequestType:       cdn.HealthProbeRequestTypeNotSet,
			},
			LoadBalancingSettings: &cdn.LoadBalancingSettingsParametersArgs{
				AdditionalLatencyInMilliseconds: pulumi.Int(1000),
				SampleSize:                      pulumi.Int(3),
				SuccessfulSamplesRequired:       pulumi.Int(3),
			},
			OriginGroupName:   pulumi.String("origingroup1"),
			ProfileName:       pulumi.String("profile1"),
			ResourceGroupName: pulumi.String("RG"),
			TrafficRestorationTimeToHealedOrNewEndpointsInMinutes: pulumi.Int(5),
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
import com.pulumi.azurenative.cdn.AFDOriginGroup;
import com.pulumi.azurenative.cdn.AFDOriginGroupArgs;
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
        var afdOriginGroup = new AFDOriginGroup("afdOriginGroup", AFDOriginGroupArgs.builder()        
            .healthProbeSettings(Map.ofEntries(
                Map.entry("probeIntervalInSeconds", 10),
                Map.entry("probePath", "/path2"),
                Map.entry("probeProtocol", "NotSet"),
                Map.entry("probeRequestType", "NotSet")
            ))
            .loadBalancingSettings(Map.ofEntries(
                Map.entry("additionalLatencyInMilliseconds", 1000),
                Map.entry("sampleSize", 3),
                Map.entry("successfulSamplesRequired", 3)
            ))
            .originGroupName("origingroup1")
            .profileName("profile1")
            .resourceGroupName("RG")
            .trafficRestorationTimeToHealedOrNewEndpointsInMinutes(5)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const afdOriginGroup = new azure_native.cdn.AFDOriginGroup("afdOriginGroup", {
    healthProbeSettings: {
        probeIntervalInSeconds: 10,
        probePath: "/path2",
        probeProtocol: azure_native.cdn.ProbeProtocol.NotSet,
        probeRequestType: azure_native.cdn.HealthProbeRequestType.NotSet,
    },
    loadBalancingSettings: {
        additionalLatencyInMilliseconds: 1000,
        sampleSize: 3,
        successfulSamplesRequired: 3,
    },
    originGroupName: "origingroup1",
    profileName: "profile1",
    resourceGroupName: "RG",
    trafficRestorationTimeToHealedOrNewEndpointsInMinutes: 5,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

afd_origin_group = azure_native.cdn.AFDOriginGroup("afdOriginGroup",
    health_probe_settings=azure_native.cdn.HealthProbeParametersArgs(
        probe_interval_in_seconds=10,
        probe_path="/path2",
        probe_protocol=azure_native.cdn.ProbeProtocol.NOT_SET,
        probe_request_type=azure_native.cdn.HealthProbeRequestType.NOT_SET,
    ),
    load_balancing_settings=azure_native.cdn.LoadBalancingSettingsParametersArgs(
        additional_latency_in_milliseconds=1000,
        sample_size=3,
        successful_samples_required=3,
    ),
    origin_group_name="origingroup1",
    profile_name="profile1",
    resource_group_name="RG",
    traffic_restoration_time_to_healed_or_new_endpoints_in_minutes=5)

```

```yaml
resources:
  afdOriginGroup:
    type: azure-native:cdn:AFDOriginGroup
    properties:
      healthProbeSettings:
        probeIntervalInSeconds: 10
        probePath: /path2
        probeProtocol: NotSet
        probeRequestType: NotSet
      loadBalancingSettings:
        additionalLatencyInMilliseconds: 1000
        sampleSize: 3
        successfulSamplesRequired: 3
      originGroupName: origingroup1
      profileName: profile1
      resourceGroupName: RG
      trafficRestorationTimeToHealedOrNewEndpointsInMinutes: 5

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:cdn:AFDOriginGroup origingroup1 /subscriptions/subid/resourcegroups/RG/providers/Microsoft.Cdn/profiles/profile1/origingroups/origingroup1 
```
