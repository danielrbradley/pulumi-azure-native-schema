Origin group comprising of origins is used for load balancing to origins when the content cannot be served from CDN.
API Version: 2021-06-01.
Previous API Version: 2020-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### OriginGroups_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var originGroup = new AzureNative.Cdn.OriginGroup("originGroup", new()
    {
        EndpointName = "endpoint1",
        HealthProbeSettings = new AzureNative.Cdn.Inputs.HealthProbeParametersArgs
        {
            ProbeIntervalInSeconds = 120,
            ProbePath = "/health.aspx",
            ProbeProtocol = AzureNative.Cdn.ProbeProtocol.Http,
            ProbeRequestType = AzureNative.Cdn.HealthProbeRequestType.GET,
        },
        OriginGroupName = "origingroup1",
        Origins = new[]
        {
            new AzureNative.Cdn.Inputs.ResourceReferenceArgs
            {
                Id = "/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/endpoints/endpoint1/origins/origin1",
            },
        },
        ProfileName = "profile1",
        ResourceGroupName = "RG",
        ResponseBasedOriginErrorDetectionSettings = new AzureNative.Cdn.Inputs.ResponseBasedOriginErrorDetectionParametersArgs
        {
            ResponseBasedDetectedErrorTypes = AzureNative.Cdn.ResponseBasedDetectedErrorTypes.TcpErrorsOnly,
            ResponseBasedFailoverThresholdPercentage = 10,
        },
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
		_, err := cdn.NewOriginGroup(ctx, "originGroup", &cdn.OriginGroupArgs{
			EndpointName: pulumi.String("endpoint1"),
			HealthProbeSettings: &cdn.HealthProbeParametersArgs{
				ProbeIntervalInSeconds: pulumi.Int(120),
				ProbePath:              pulumi.String("/health.aspx"),
				ProbeProtocol:          cdn.ProbeProtocolHttp,
				ProbeRequestType:       cdn.HealthProbeRequestTypeGET,
			},
			OriginGroupName: pulumi.String("origingroup1"),
			Origins: []cdn.ResourceReferenceArgs{
				{
					Id: pulumi.String("/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/endpoints/endpoint1/origins/origin1"),
				},
			},
			ProfileName:       pulumi.String("profile1"),
			ResourceGroupName: pulumi.String("RG"),
			ResponseBasedOriginErrorDetectionSettings: &cdn.ResponseBasedOriginErrorDetectionParametersArgs{
				ResponseBasedDetectedErrorTypes:          cdn.ResponseBasedDetectedErrorTypesTcpErrorsOnly,
				ResponseBasedFailoverThresholdPercentage: pulumi.Int(10),
			},
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
import com.pulumi.azurenative.cdn.OriginGroup;
import com.pulumi.azurenative.cdn.OriginGroupArgs;
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
        var originGroup = new OriginGroup("originGroup", OriginGroupArgs.builder()        
            .endpointName("endpoint1")
            .healthProbeSettings(Map.ofEntries(
                Map.entry("probeIntervalInSeconds", 120),
                Map.entry("probePath", "/health.aspx"),
                Map.entry("probeProtocol", "Http"),
                Map.entry("probeRequestType", "GET")
            ))
            .originGroupName("origingroup1")
            .origins(Map.of("id", "/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/endpoints/endpoint1/origins/origin1"))
            .profileName("profile1")
            .resourceGroupName("RG")
            .responseBasedOriginErrorDetectionSettings(Map.ofEntries(
                Map.entry("responseBasedDetectedErrorTypes", "TcpErrorsOnly"),
                Map.entry("responseBasedFailoverThresholdPercentage", 10)
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const originGroup = new azure_native.cdn.OriginGroup("originGroup", {
    endpointName: "endpoint1",
    healthProbeSettings: {
        probeIntervalInSeconds: 120,
        probePath: "/health.aspx",
        probeProtocol: azure_native.cdn.ProbeProtocol.Http,
        probeRequestType: azure_native.cdn.HealthProbeRequestType.GET,
    },
    originGroupName: "origingroup1",
    origins: [{
        id: "/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/endpoints/endpoint1/origins/origin1",
    }],
    profileName: "profile1",
    resourceGroupName: "RG",
    responseBasedOriginErrorDetectionSettings: {
        responseBasedDetectedErrorTypes: azure_native.cdn.ResponseBasedDetectedErrorTypes.TcpErrorsOnly,
        responseBasedFailoverThresholdPercentage: 10,
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

origin_group = azure_native.cdn.OriginGroup("originGroup",
    endpoint_name="endpoint1",
    health_probe_settings=azure_native.cdn.HealthProbeParametersArgs(
        probe_interval_in_seconds=120,
        probe_path="/health.aspx",
        probe_protocol=azure_native.cdn.ProbeProtocol.HTTP,
        probe_request_type=azure_native.cdn.HealthProbeRequestType.GET,
    ),
    origin_group_name="origingroup1",
    origins=[azure_native.cdn.ResourceReferenceArgs(
        id="/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/endpoints/endpoint1/origins/origin1",
    )],
    profile_name="profile1",
    resource_group_name="RG",
    response_based_origin_error_detection_settings=azure_native.cdn.ResponseBasedOriginErrorDetectionParametersArgs(
        response_based_detected_error_types=azure_native.cdn.ResponseBasedDetectedErrorTypes.TCP_ERRORS_ONLY,
        response_based_failover_threshold_percentage=10,
    ))

```

```yaml
resources:
  originGroup:
    type: azure-native:cdn:OriginGroup
    properties:
      endpointName: endpoint1
      healthProbeSettings:
        probeIntervalInSeconds: 120
        probePath: /health.aspx
        probeProtocol: Http
        probeRequestType: GET
      originGroupName: origingroup1
      origins:
        - id: /subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/endpoints/endpoint1/origins/origin1
      profileName: profile1
      resourceGroupName: RG
      responseBasedOriginErrorDetectionSettings:
        responseBasedDetectedErrorTypes: TcpErrorsOnly
        responseBasedFailoverThresholdPercentage: 10

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:cdn:OriginGroup origingroup1 /subscriptions/subid/resourcegroups/RG/providers/Microsoft.Cdn/profiles/profile1/endpoints/endpoint1/originGroups/originGroup1 
```
