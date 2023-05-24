CDN endpoint is the entity within a CDN profile containing configuration information such as origin, protocol, content caching and delivery behavior. The CDN endpoint uses the URL format <endpointname>.azureedge.net.
API Version: 2021-06-01.
Previous API Version: 2020-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Endpoints_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var endpoint = new AzureNative.Cdn.Endpoint("endpoint", new()
    {
        ContentTypesToCompress = new[]
        {
            "text/html",
            "application/octet-stream",
        },
        DefaultOriginGroup = new AzureNative.Cdn.Inputs.ResourceReferenceArgs
        {
            Id = "/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/endpoints/endpoint1/originGroups/originGroup1",
        },
        DeliveryPolicy = new AzureNative.Cdn.Inputs.EndpointPropertiesUpdateParametersDeliveryPolicyArgs
        {
            Description = "Test description for a policy.",
            Rules = new[]
            {
                new AzureNative.Cdn.Inputs.DeliveryRuleArgs
                {
                    Actions = 
                    {
                        new AzureNative.Cdn.Inputs.DeliveryRuleCacheExpirationActionArgs
                        {
                            Name = "CacheExpiration",
                            Parameters = new AzureNative.Cdn.Inputs.CacheExpirationActionParametersArgs
                            {
                                CacheBehavior = "Override",
                                CacheDuration = "10:10:09",
                                CacheType = "All",
                                TypeName = "DeliveryRuleCacheExpirationActionParameters",
                            },
                        },
                        new AzureNative.Cdn.Inputs.DeliveryRuleResponseHeaderActionArgs
                        {
                            Name = "ModifyResponseHeader",
                            Parameters = new AzureNative.Cdn.Inputs.HeaderActionParametersArgs
                            {
                                HeaderAction = "Overwrite",
                                HeaderName = "Access-Control-Allow-Origin",
                                TypeName = "DeliveryRuleHeaderActionParameters",
                                Value = "*",
                            },
                        },
                        new AzureNative.Cdn.Inputs.DeliveryRuleRequestHeaderActionArgs
                        {
                            Name = "ModifyRequestHeader",
                            Parameters = new AzureNative.Cdn.Inputs.HeaderActionParametersArgs
                            {
                                HeaderAction = "Overwrite",
                                HeaderName = "Accept-Encoding",
                                TypeName = "DeliveryRuleHeaderActionParameters",
                                Value = "gzip",
                            },
                        },
                    },
                    Conditions = new[]
                    {
                        new AzureNative.Cdn.Inputs.DeliveryRuleRemoteAddressConditionArgs
                        {
                            Name = "RemoteAddress",
                            Parameters = new AzureNative.Cdn.Inputs.RemoteAddressMatchConditionParametersArgs
                            {
                                MatchValues = new[]
                                {
                                    "192.168.1.0/24",
                                    "10.0.0.0/24",
                                },
                                NegateCondition = true,
                                Operator = "IPMatch",
                                TypeName = "DeliveryRuleRemoteAddressConditionParameters",
                            },
                        },
                    },
                    Name = "rule1",
                    Order = 1,
                },
            },
        },
        EndpointName = "endpoint1",
        IsCompressionEnabled = true,
        IsHttpAllowed = true,
        IsHttpsAllowed = true,
        Location = "WestUs",
        OriginGroups = new[]
        {
            new AzureNative.Cdn.Inputs.DeepCreatedOriginGroupArgs
            {
                HealthProbeSettings = new AzureNative.Cdn.Inputs.HealthProbeParametersArgs
                {
                    ProbeIntervalInSeconds = 120,
                    ProbePath = "/health.aspx",
                    ProbeProtocol = AzureNative.Cdn.ProbeProtocol.Http,
                    ProbeRequestType = AzureNative.Cdn.HealthProbeRequestType.GET,
                },
                Name = "originGroup1",
                Origins = new[]
                {
                    new AzureNative.Cdn.Inputs.ResourceReferenceArgs
                    {
                        Id = "/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/endpoints/endpoint1/origins/origin1",
                    },
                    new AzureNative.Cdn.Inputs.ResourceReferenceArgs
                    {
                        Id = "/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/endpoints/endpoint1/origins/origin2",
                    },
                },
                ResponseBasedOriginErrorDetectionSettings = new AzureNative.Cdn.Inputs.ResponseBasedOriginErrorDetectionParametersArgs
                {
                    ResponseBasedDetectedErrorTypes = AzureNative.Cdn.ResponseBasedDetectedErrorTypes.TcpErrorsOnly,
                    ResponseBasedFailoverThresholdPercentage = 10,
                },
            },
        },
        OriginHostHeader = "www.bing.com",
        OriginPath = "/photos",
        Origins = new[]
        {
            new AzureNative.Cdn.Inputs.DeepCreatedOriginArgs
            {
                Enabled = true,
                HostName = "www.someDomain1.net",
                HttpPort = 80,
                HttpsPort = 443,
                Name = "origin1",
                OriginHostHeader = "www.someDomain1.net",
                Priority = 1,
                Weight = 50,
            },
            new AzureNative.Cdn.Inputs.DeepCreatedOriginArgs
            {
                Enabled = true,
                HostName = "www.someDomain2.net",
                HttpPort = 80,
                HttpsPort = 443,
                Name = "origin2",
                OriginHostHeader = "www.someDomain2.net",
                Priority = 2,
                Weight = 50,
            },
        },
        ProfileName = "profile1",
        QueryStringCachingBehavior = AzureNative.Cdn.QueryStringCachingBehavior.BypassCaching,
        ResourceGroupName = "RG",
        Tags = 
        {
            { "key1", "value1" },
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
		_, err := cdn.NewEndpoint(ctx, "endpoint", &cdn.EndpointArgs{
			ContentTypesToCompress: pulumi.StringArray{
				pulumi.String("text/html"),
				pulumi.String("application/octet-stream"),
			},
			DefaultOriginGroup: &cdn.ResourceReferenceArgs{
				Id: pulumi.String("/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/endpoints/endpoint1/originGroups/originGroup1"),
			},
			DeliveryPolicy: cdn.EndpointPropertiesUpdateParametersResponseDeliveryPolicy{
				Description: pulumi.String("Test description for a policy."),
				Rules: []cdn.DeliveryRuleArgs{
					{
						Actions: pulumi.AnyArray{
							{
								Name: "CacheExpiration",
								Parameters: {
									CacheBehavior: "Override",
									CacheDuration: "10:10:09",
									CacheType:     "All",
									TypeName:      "DeliveryRuleCacheExpirationActionParameters",
								},
							},
							{
								Name: "ModifyResponseHeader",
								Parameters: {
									HeaderAction: "Overwrite",
									HeaderName:   "Access-Control-Allow-Origin",
									TypeName:     "DeliveryRuleHeaderActionParameters",
									Value:        "*",
								},
							},
							{
								Name: "ModifyRequestHeader",
								Parameters: {
									HeaderAction: "Overwrite",
									HeaderName:   "Accept-Encoding",
									TypeName:     "DeliveryRuleHeaderActionParameters",
									Value:        "gzip",
								},
							},
						},
						Conditions: pulumi.AnyArray{
							{
								Name: "RemoteAddress",
								Parameters: {
									MatchValues: []string{
										"192.168.1.0/24",
										"10.0.0.0/24",
									},
									NegateCondition: true,
									Operator:        "IPMatch",
									TypeName:        "DeliveryRuleRemoteAddressConditionParameters",
								},
							},
						},
						Name:  pulumi.String("rule1"),
						Order: pulumi.Int(1),
					},
				},
			},
			EndpointName:         pulumi.String("endpoint1"),
			IsCompressionEnabled: pulumi.Bool(true),
			IsHttpAllowed:        pulumi.Bool(true),
			IsHttpsAllowed:       pulumi.Bool(true),
			Location:             pulumi.String("WestUs"),
			OriginGroups: []cdn.DeepCreatedOriginGroupArgs{
				{
					HealthProbeSettings: {
						ProbeIntervalInSeconds: pulumi.Int(120),
						ProbePath:              pulumi.String("/health.aspx"),
						ProbeProtocol:          cdn.ProbeProtocolHttp,
						ProbeRequestType:       cdn.HealthProbeRequestTypeGET,
					},
					Name: pulumi.String("originGroup1"),
					Origins: cdn.ResourceReferenceArray{
						{
							Id: pulumi.String("/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/endpoints/endpoint1/origins/origin1"),
						},
						{
							Id: pulumi.String("/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/endpoints/endpoint1/origins/origin2"),
						},
					},
					ResponseBasedOriginErrorDetectionSettings: {
						ResponseBasedDetectedErrorTypes:          cdn.ResponseBasedDetectedErrorTypesTcpErrorsOnly,
						ResponseBasedFailoverThresholdPercentage: pulumi.Int(10),
					},
				},
			},
			OriginHostHeader: pulumi.String("www.bing.com"),
			OriginPath:       pulumi.String("/photos"),
			Origins: []cdn.DeepCreatedOriginArgs{
				{
					Enabled:          pulumi.Bool(true),
					HostName:         pulumi.String("www.someDomain1.net"),
					HttpPort:         pulumi.Int(80),
					HttpsPort:        pulumi.Int(443),
					Name:             pulumi.String("origin1"),
					OriginHostHeader: pulumi.String("www.someDomain1.net"),
					Priority:         pulumi.Int(1),
					Weight:           pulumi.Int(50),
				},
				{
					Enabled:          pulumi.Bool(true),
					HostName:         pulumi.String("www.someDomain2.net"),
					HttpPort:         pulumi.Int(80),
					HttpsPort:        pulumi.Int(443),
					Name:             pulumi.String("origin2"),
					OriginHostHeader: pulumi.String("www.someDomain2.net"),
					Priority:         pulumi.Int(2),
					Weight:           pulumi.Int(50),
				},
			},
			ProfileName:                pulumi.String("profile1"),
			QueryStringCachingBehavior: cdn.QueryStringCachingBehaviorBypassCaching,
			ResourceGroupName:          pulumi.String("RG"),
			Tags: pulumi.StringMap{
				"key1": pulumi.String("value1"),
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
import com.pulumi.azurenative.cdn.Endpoint;
import com.pulumi.azurenative.cdn.EndpointArgs;
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
        var endpoint = new Endpoint("endpoint", EndpointArgs.builder()        
            .contentTypesToCompress(            
                "text/html",
                "application/octet-stream")
            .defaultOriginGroup(Map.of("id", "/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/endpoints/endpoint1/originGroups/originGroup1"))
            .deliveryPolicy(Map.ofEntries(
                Map.entry("description", "Test description for a policy."),
                Map.entry("rules", Map.ofEntries(
                    Map.entry("actions",                     
                        Map.ofEntries(
                            Map.entry("name", "CacheExpiration"),
                            Map.entry("parameters", Map.ofEntries(
                                Map.entry("cacheBehavior", "Override"),
                                Map.entry("cacheDuration", "10:10:09"),
                                Map.entry("cacheType", "All"),
                                Map.entry("typeName", "DeliveryRuleCacheExpirationActionParameters")
                            ))
                        ),
                        Map.ofEntries(
                            Map.entry("name", "ModifyResponseHeader"),
                            Map.entry("parameters", Map.ofEntries(
                                Map.entry("headerAction", "Overwrite"),
                                Map.entry("headerName", "Access-Control-Allow-Origin"),
                                Map.entry("typeName", "DeliveryRuleHeaderActionParameters"),
                                Map.entry("value", "*")
                            ))
                        ),
                        Map.ofEntries(
                            Map.entry("name", "ModifyRequestHeader"),
                            Map.entry("parameters", Map.ofEntries(
                                Map.entry("headerAction", "Overwrite"),
                                Map.entry("headerName", "Accept-Encoding"),
                                Map.entry("typeName", "DeliveryRuleHeaderActionParameters"),
                                Map.entry("value", "gzip")
                            ))
                        )),
                    Map.entry("conditions", Map.ofEntries(
                        Map.entry("name", "RemoteAddress"),
                        Map.entry("parameters", Map.ofEntries(
                            Map.entry("matchValues",                             
                                "192.168.1.0/24",
                                "10.0.0.0/24"),
                            Map.entry("negateCondition", true),
                            Map.entry("operator", "IPMatch"),
                            Map.entry("typeName", "DeliveryRuleRemoteAddressConditionParameters")
                        ))
                    )),
                    Map.entry("name", "rule1"),
                    Map.entry("order", 1)
                ))
            ))
            .endpointName("endpoint1")
            .isCompressionEnabled(true)
            .isHttpAllowed(true)
            .isHttpsAllowed(true)
            .location("WestUs")
            .originGroups(Map.ofEntries(
                Map.entry("healthProbeSettings", Map.ofEntries(
                    Map.entry("probeIntervalInSeconds", 120),
                    Map.entry("probePath", "/health.aspx"),
                    Map.entry("probeProtocol", "Http"),
                    Map.entry("probeRequestType", "GET")
                )),
                Map.entry("name", "originGroup1"),
                Map.entry("origins",                 
                    Map.of("id", "/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/endpoints/endpoint1/origins/origin1"),
                    Map.of("id", "/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/endpoints/endpoint1/origins/origin2")),
                Map.entry("responseBasedOriginErrorDetectionSettings", Map.ofEntries(
                    Map.entry("responseBasedDetectedErrorTypes", "TcpErrorsOnly"),
                    Map.entry("responseBasedFailoverThresholdPercentage", 10)
                ))
            ))
            .originHostHeader("www.bing.com")
            .originPath("/photos")
            .origins(            
                Map.ofEntries(
                    Map.entry("enabled", true),
                    Map.entry("hostName", "www.someDomain1.net"),
                    Map.entry("httpPort", 80),
                    Map.entry("httpsPort", 443),
                    Map.entry("name", "origin1"),
                    Map.entry("originHostHeader", "www.someDomain1.net"),
                    Map.entry("priority", 1),
                    Map.entry("weight", 50)
                ),
                Map.ofEntries(
                    Map.entry("enabled", true),
                    Map.entry("hostName", "www.someDomain2.net"),
                    Map.entry("httpPort", 80),
                    Map.entry("httpsPort", 443),
                    Map.entry("name", "origin2"),
                    Map.entry("originHostHeader", "www.someDomain2.net"),
                    Map.entry("priority", 2),
                    Map.entry("weight", 50)
                ))
            .profileName("profile1")
            .queryStringCachingBehavior("BypassCaching")
            .resourceGroupName("RG")
            .tags(Map.of("key1", "value1"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const endpoint = new azure_native.cdn.Endpoint("endpoint", {
    contentTypesToCompress: [
        "text/html",
        "application/octet-stream",
    ],
    defaultOriginGroup: {
        id: "/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/endpoints/endpoint1/originGroups/originGroup1",
    },
    deliveryPolicy: {
        description: "Test description for a policy.",
        rules: [{
            actions: [
                {
                    name: "CacheExpiration",
                    parameters: {
                        cacheBehavior: "Override",
                        cacheDuration: "10:10:09",
                        cacheType: "All",
                        typeName: "DeliveryRuleCacheExpirationActionParameters",
                    },
                },
                {
                    name: "ModifyResponseHeader",
                    parameters: {
                        headerAction: "Overwrite",
                        headerName: "Access-Control-Allow-Origin",
                        typeName: "DeliveryRuleHeaderActionParameters",
                        value: "*",
                    },
                },
                {
                    name: "ModifyRequestHeader",
                    parameters: {
                        headerAction: "Overwrite",
                        headerName: "Accept-Encoding",
                        typeName: "DeliveryRuleHeaderActionParameters",
                        value: "gzip",
                    },
                },
            ],
            conditions: [{
                name: "RemoteAddress",
                parameters: {
                    matchValues: [
                        "192.168.1.0/24",
                        "10.0.0.0/24",
                    ],
                    negateCondition: true,
                    operator: "IPMatch",
                    typeName: "DeliveryRuleRemoteAddressConditionParameters",
                },
            }],
            name: "rule1",
            order: 1,
        }],
    },
    endpointName: "endpoint1",
    isCompressionEnabled: true,
    isHttpAllowed: true,
    isHttpsAllowed: true,
    location: "WestUs",
    originGroups: [{
        healthProbeSettings: {
            probeIntervalInSeconds: 120,
            probePath: "/health.aspx",
            probeProtocol: azure_native.cdn.ProbeProtocol.Http,
            probeRequestType: azure_native.cdn.HealthProbeRequestType.GET,
        },
        name: "originGroup1",
        origins: [
            {
                id: "/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/endpoints/endpoint1/origins/origin1",
            },
            {
                id: "/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/endpoints/endpoint1/origins/origin2",
            },
        ],
        responseBasedOriginErrorDetectionSettings: {
            responseBasedDetectedErrorTypes: azure_native.cdn.ResponseBasedDetectedErrorTypes.TcpErrorsOnly,
            responseBasedFailoverThresholdPercentage: 10,
        },
    }],
    originHostHeader: "www.bing.com",
    originPath: "/photos",
    origins: [
        {
            enabled: true,
            hostName: "www.someDomain1.net",
            httpPort: 80,
            httpsPort: 443,
            name: "origin1",
            originHostHeader: "www.someDomain1.net",
            priority: 1,
            weight: 50,
        },
        {
            enabled: true,
            hostName: "www.someDomain2.net",
            httpPort: 80,
            httpsPort: 443,
            name: "origin2",
            originHostHeader: "www.someDomain2.net",
            priority: 2,
            weight: 50,
        },
    ],
    profileName: "profile1",
    queryStringCachingBehavior: azure_native.cdn.QueryStringCachingBehavior.BypassCaching,
    resourceGroupName: "RG",
    tags: {
        key1: "value1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

endpoint = azure_native.cdn.Endpoint("endpoint",
    content_types_to_compress=[
        "text/html",
        "application/octet-stream",
    ],
    default_origin_group=azure_native.cdn.ResourceReferenceArgs(
        id="/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/endpoints/endpoint1/originGroups/originGroup1",
    ),
    delivery_policy=azure_native.cdn.EndpointPropertiesUpdateParametersResponseDeliveryPolicyArgs(
        description="Test description for a policy.",
        rules=[{
            "actions": [
                azure_native.cdn.DeliveryRuleCacheExpirationActionArgs(
                    name="CacheExpiration",
                    parameters=azure_native.cdn.CacheExpirationActionParametersArgs(
                        cache_behavior="Override",
                        cache_duration="10:10:09",
                        cache_type="All",
                        type_name="DeliveryRuleCacheExpirationActionParameters",
                    ),
                ),
                azure_native.cdn.DeliveryRuleResponseHeaderActionArgs(
                    name="ModifyResponseHeader",
                    parameters=azure_native.cdn.HeaderActionParametersArgs(
                        header_action="Overwrite",
                        header_name="Access-Control-Allow-Origin",
                        type_name="DeliveryRuleHeaderActionParameters",
                        value="*",
                    ),
                ),
                azure_native.cdn.DeliveryRuleRequestHeaderActionArgs(
                    name="ModifyRequestHeader",
                    parameters=azure_native.cdn.HeaderActionParametersArgs(
                        header_action="Overwrite",
                        header_name="Accept-Encoding",
                        type_name="DeliveryRuleHeaderActionParameters",
                        value="gzip",
                    ),
                ),
            ],
            "conditions": [azure_native.cdn.DeliveryRuleRemoteAddressConditionArgs(
                name="RemoteAddress",
                parameters=azure_native.cdn.RemoteAddressMatchConditionParametersArgs(
                    match_values=[
                        "192.168.1.0/24",
                        "10.0.0.0/24",
                    ],
                    negate_condition=True,
                    operator="IPMatch",
                    type_name="DeliveryRuleRemoteAddressConditionParameters",
                ),
            )],
            "name": "rule1",
            "order": 1,
        }],
    ),
    endpoint_name="endpoint1",
    is_compression_enabled=True,
    is_http_allowed=True,
    is_https_allowed=True,
    location="WestUs",
    origin_groups=[{
        "healthProbeSettings": azure_native.cdn.HealthProbeParametersArgs(
            probe_interval_in_seconds=120,
            probe_path="/health.aspx",
            probe_protocol=azure_native.cdn.ProbeProtocol.HTTP,
            probe_request_type=azure_native.cdn.HealthProbeRequestType.GET,
        ),
        "name": "originGroup1",
        "origins": [
            azure_native.cdn.ResourceReferenceArgs(
                id="/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/endpoints/endpoint1/origins/origin1",
            ),
            azure_native.cdn.ResourceReferenceArgs(
                id="/subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/endpoints/endpoint1/origins/origin2",
            ),
        ],
        "responseBasedOriginErrorDetectionSettings": azure_native.cdn.ResponseBasedOriginErrorDetectionParametersArgs(
            response_based_detected_error_types=azure_native.cdn.ResponseBasedDetectedErrorTypes.TCP_ERRORS_ONLY,
            response_based_failover_threshold_percentage=10,
        ),
    }],
    origin_host_header="www.bing.com",
    origin_path="/photos",
    origins=[
        azure_native.cdn.DeepCreatedOriginArgs(
            enabled=True,
            host_name="www.someDomain1.net",
            http_port=80,
            https_port=443,
            name="origin1",
            origin_host_header="www.someDomain1.net",
            priority=1,
            weight=50,
        ),
        azure_native.cdn.DeepCreatedOriginArgs(
            enabled=True,
            host_name="www.someDomain2.net",
            http_port=80,
            https_port=443,
            name="origin2",
            origin_host_header="www.someDomain2.net",
            priority=2,
            weight=50,
        ),
    ],
    profile_name="profile1",
    query_string_caching_behavior=azure_native.cdn.QueryStringCachingBehavior.BYPASS_CACHING,
    resource_group_name="RG",
    tags={
        "key1": "value1",
    })

```

```yaml
resources:
  endpoint:
    type: azure-native:cdn:Endpoint
    properties:
      contentTypesToCompress:
        - text/html
        - application/octet-stream
      defaultOriginGroup:
        id: /subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/endpoints/endpoint1/originGroups/originGroup1
      deliveryPolicy:
        description: Test description for a policy.
        rules:
          - actions:
              - name: CacheExpiration
                parameters:
                  cacheBehavior: Override
                  cacheDuration: 10:10:09
                  cacheType: All
                  typeName: DeliveryRuleCacheExpirationActionParameters
              - name: ModifyResponseHeader
                parameters:
                  headerAction: Overwrite
                  headerName: Access-Control-Allow-Origin
                  typeName: DeliveryRuleHeaderActionParameters
                  value: '*'
              - name: ModifyRequestHeader
                parameters:
                  headerAction: Overwrite
                  headerName: Accept-Encoding
                  typeName: DeliveryRuleHeaderActionParameters
                  value: gzip
            conditions:
              - name: RemoteAddress
                parameters:
                  matchValues:
                    - 192.168.1.0/24
                    - 10.0.0.0/24
                  negateCondition: true
                  operator: IPMatch
                  typeName: DeliveryRuleRemoteAddressConditionParameters
            name: rule1
            order: 1
      endpointName: endpoint1
      isCompressionEnabled: true
      isHttpAllowed: true
      isHttpsAllowed: true
      location: WestUs
      originGroups:
        - healthProbeSettings:
            probeIntervalInSeconds: 120
            probePath: /health.aspx
            probeProtocol: Http
            probeRequestType: GET
          name: originGroup1
          origins:
            - id: /subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/endpoints/endpoint1/origins/origin1
            - id: /subscriptions/subid/resourceGroups/RG/providers/Microsoft.Cdn/profiles/profile1/endpoints/endpoint1/origins/origin2
          responseBasedOriginErrorDetectionSettings:
            responseBasedDetectedErrorTypes: TcpErrorsOnly
            responseBasedFailoverThresholdPercentage: 10
      originHostHeader: www.bing.com
      originPath: /photos
      origins:
        - enabled: true
          hostName: www.someDomain1.net
          httpPort: 80
          httpsPort: 443
          name: origin1
          originHostHeader: www.someDomain1.net
          priority: 1
          weight: 50
        - enabled: true
          hostName: www.someDomain2.net
          httpPort: 80
          httpsPort: 443
          name: origin2
          originHostHeader: www.someDomain2.net
          priority: 2
          weight: 50
      profileName: profile1
      queryStringCachingBehavior: BypassCaching
      resourceGroupName: RG
      tags:
        key1: value1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:cdn:Endpoint endpoint4899 /subscriptions/subid/resourcegroups/RG/providers/Microsoft.Cdn/profiles/profile1/endpoints/endpoint1 
```
