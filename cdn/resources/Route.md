Friendly Routes name mapping to the any Routes or secret related information.
API Version: 2021-06-01.
Previous API Version: 2020-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Routes_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var route = new AzureNative.Cdn.Route("route", new()
    {
        CacheConfiguration = new AzureNative.Cdn.Inputs.AfdRouteCacheConfigurationArgs
        {
            CompressionSettings = new AzureNative.Cdn.Inputs.CompressionSettingsArgs
            {
                ContentTypesToCompress = new[]
                {
                    "text/html",
                    "application/octet-stream",
                },
                IsCompressionEnabled = true,
            },
            QueryParameters = "querystring=test",
            QueryStringCachingBehavior = "IgnoreSpecifiedQueryStrings",
        },
        CustomDomains = new[]
        {
            new AzureNative.Cdn.Inputs.ActivatedResourceReferenceArgs
            {
                Id = "/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/customDomains/domain1",
            },
        },
        EnabledState = "Enabled",
        EndpointName = "endpoint1",
        ForwardingProtocol = "MatchRequest",
        HttpsRedirect = "Enabled",
        LinkToDefaultDomain = "Enabled",
        OriginGroup = new AzureNative.Cdn.Inputs.ResourceReferenceArgs
        {
            Id = "/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/originGroups/originGroup1",
        },
        PatternsToMatch = new[]
        {
            "/*",
        },
        ProfileName = "profile1",
        ResourceGroupName = "RG",
        RouteName = "route1",
        RuleSets = new[]
        {
            new AzureNative.Cdn.Inputs.ResourceReferenceArgs
            {
                Id = "/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/ruleSets/ruleSet1",
            },
        },
        SupportedProtocols = new[]
        {
            "Https",
            "Http",
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
		_, err := cdn.NewRoute(ctx, "route", &cdn.RouteArgs{
			CacheConfiguration: cdn.AfdRouteCacheConfigurationResponse{
				CompressionSettings: &cdn.CompressionSettingsArgs{
					ContentTypesToCompress: pulumi.StringArray{
						pulumi.String("text/html"),
						pulumi.String("application/octet-stream"),
					},
					IsCompressionEnabled: pulumi.Bool(true),
				},
				QueryParameters:            pulumi.String("querystring=test"),
				QueryStringCachingBehavior: pulumi.String("IgnoreSpecifiedQueryStrings"),
			},
			CustomDomains: []cdn.ActivatedResourceReferenceArgs{
				{
					Id: pulumi.String("/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/customDomains/domain1"),
				},
			},
			EnabledState:        pulumi.String("Enabled"),
			EndpointName:        pulumi.String("endpoint1"),
			ForwardingProtocol:  pulumi.String("MatchRequest"),
			HttpsRedirect:       pulumi.String("Enabled"),
			LinkToDefaultDomain: pulumi.String("Enabled"),
			OriginGroup: &cdn.ResourceReferenceArgs{
				Id: pulumi.String("/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/originGroups/originGroup1"),
			},
			PatternsToMatch: pulumi.StringArray{
				pulumi.String("/*"),
			},
			ProfileName:       pulumi.String("profile1"),
			ResourceGroupName: pulumi.String("RG"),
			RouteName:         pulumi.String("route1"),
			RuleSets: []cdn.ResourceReferenceArgs{
				{
					Id: pulumi.String("/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/ruleSets/ruleSet1"),
				},
			},
			SupportedProtocols: pulumi.StringArray{
				pulumi.String("Https"),
				pulumi.String("Http"),
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
import com.pulumi.azurenative.cdn.Route;
import com.pulumi.azurenative.cdn.RouteArgs;
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
        var route = new Route("route", RouteArgs.builder()        
            .cacheConfiguration(Map.ofEntries(
                Map.entry("compressionSettings", Map.ofEntries(
                    Map.entry("contentTypesToCompress",                     
                        "text/html",
                        "application/octet-stream"),
                    Map.entry("isCompressionEnabled", true)
                )),
                Map.entry("queryParameters", "querystring=test"),
                Map.entry("queryStringCachingBehavior", "IgnoreSpecifiedQueryStrings")
            ))
            .customDomains(Map.of("id", "/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/customDomains/domain1"))
            .enabledState("Enabled")
            .endpointName("endpoint1")
            .forwardingProtocol("MatchRequest")
            .httpsRedirect("Enabled")
            .linkToDefaultDomain("Enabled")
            .originGroup(Map.of("id", "/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/originGroups/originGroup1"))
            .patternsToMatch("/*")
            .profileName("profile1")
            .resourceGroupName("RG")
            .routeName("route1")
            .ruleSets(Map.of("id", "/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/ruleSets/ruleSet1"))
            .supportedProtocols(            
                "Https",
                "Http")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const route = new azure_native.cdn.Route("route", {
    cacheConfiguration: {
        compressionSettings: {
            contentTypesToCompress: [
                "text/html",
                "application/octet-stream",
            ],
            isCompressionEnabled: true,
        },
        queryParameters: "querystring=test",
        queryStringCachingBehavior: "IgnoreSpecifiedQueryStrings",
    },
    customDomains: [{
        id: "/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/customDomains/domain1",
    }],
    enabledState: "Enabled",
    endpointName: "endpoint1",
    forwardingProtocol: "MatchRequest",
    httpsRedirect: "Enabled",
    linkToDefaultDomain: "Enabled",
    originGroup: {
        id: "/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/originGroups/originGroup1",
    },
    patternsToMatch: ["/*"],
    profileName: "profile1",
    resourceGroupName: "RG",
    routeName: "route1",
    ruleSets: [{
        id: "/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/ruleSets/ruleSet1",
    }],
    supportedProtocols: [
        "Https",
        "Http",
    ],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

route = azure_native.cdn.Route("route",
    cache_configuration=azure_native.cdn.AfdRouteCacheConfigurationResponseArgs(
        compression_settings=azure_native.cdn.CompressionSettingsArgs(
            content_types_to_compress=[
                "text/html",
                "application/octet-stream",
            ],
            is_compression_enabled=True,
        ),
        query_parameters="querystring=test",
        query_string_caching_behavior="IgnoreSpecifiedQueryStrings",
    ),
    custom_domains=[azure_native.cdn.ActivatedResourceReferenceArgs(
        id="/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/customDomains/domain1",
    )],
    enabled_state="Enabled",
    endpoint_name="endpoint1",
    forwarding_protocol="MatchRequest",
    https_redirect="Enabled",
    link_to_default_domain="Enabled",
    origin_group=azure_native.cdn.ResourceReferenceArgs(
        id="/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/originGroups/originGroup1",
    ),
    patterns_to_match=["/*"],
    profile_name="profile1",
    resource_group_name="RG",
    route_name="route1",
    rule_sets=[azure_native.cdn.ResourceReferenceArgs(
        id="/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/ruleSets/ruleSet1",
    )],
    supported_protocols=[
        "Https",
        "Http",
    ])

```

```yaml
resources:
  route:
    type: azure-native:cdn:Route
    properties:
      cacheConfiguration:
        compressionSettings:
          contentTypesToCompress:
            - text/html
            - application/octet-stream
          isCompressionEnabled: true
        queryParameters: querystring=test
        queryStringCachingBehavior: IgnoreSpecifiedQueryStrings
      customDomains:
        - id: /subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/customDomains/domain1
      enabledState: Enabled
      endpointName: endpoint1
      forwardingProtocol: MatchRequest
      httpsRedirect: Enabled
      linkToDefaultDomain: Enabled
      originGroup:
        id: /subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/originGroups/originGroup1
      patternsToMatch:
        - /*
      profileName: profile1
      resourceGroupName: RG
      routeName: route1
      ruleSets:
        - id: /subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/ruleSets/ruleSet1
      supportedProtocols:
        - Https
        - Http

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:cdn:Route route1 /subscriptions/subid/resourcegroups/RG/providers/Microsoft.Cdn/profiles/profile1/afdendpoints/endpoint1/routes/route1 
```
