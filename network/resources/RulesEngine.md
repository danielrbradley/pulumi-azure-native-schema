A rules engine configuration containing a list of rules that will run to modify the runtime behavior of the request and response.
API Version: 2021-06-01.
Previous API Version: 2020-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a specific Rules Engine Configuration
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var rulesEngine = new AzureNative.Network.RulesEngine("rulesEngine", new()
    {
        FrontDoorName = "frontDoor1",
        ResourceGroupName = "rg1",
        Rules = new[]
        {
            new AzureNative.Network.Inputs.RulesEngineRuleArgs
            {
                Action = new AzureNative.Network.Inputs.RulesEngineActionArgs
                {
                    RouteConfigurationOverride = new AzureNative.Network.Inputs.RedirectConfigurationArgs
                    {
                        CustomFragment = "fragment",
                        CustomHost = "www.bing.com",
                        CustomPath = "/api",
                        CustomQueryString = "a=b",
                        OdataType = "#Microsoft.Azure.FrontDoor.Models.FrontdoorRedirectConfiguration",
                        RedirectProtocol = "HttpsOnly",
                        RedirectType = "Moved",
                    },
                },
                MatchConditions = new[]
                {
                    new AzureNative.Network.Inputs.RulesEngineMatchConditionArgs
                    {
                        RulesEngineMatchValue = new[]
                        {
                            "CH",
                        },
                        RulesEngineMatchVariable = "RemoteAddr",
                        RulesEngineOperator = "GeoMatch",
                    },
                },
                MatchProcessingBehavior = "Stop",
                Name = "Rule1",
                Priority = 1,
            },
            new AzureNative.Network.Inputs.RulesEngineRuleArgs
            {
                Action = new AzureNative.Network.Inputs.RulesEngineActionArgs
                {
                    ResponseHeaderActions = new[]
                    {
                        new AzureNative.Network.Inputs.HeaderActionArgs
                        {
                            HeaderActionType = "Overwrite",
                            HeaderName = "Cache-Control",
                            Value = "public, max-age=31536000",
                        },
                    },
                },
                MatchConditions = new[]
                {
                    new AzureNative.Network.Inputs.RulesEngineMatchConditionArgs
                    {
                        RulesEngineMatchValue = new[]
                        {
                            "jpg",
                        },
                        RulesEngineMatchVariable = "RequestFilenameExtension",
                        RulesEngineOperator = "Equal",
                        Transforms = new[]
                        {
                            "Lowercase",
                        },
                    },
                },
                Name = "Rule2",
                Priority = 2,
            },
            new AzureNative.Network.Inputs.RulesEngineRuleArgs
            {
                Action = new AzureNative.Network.Inputs.RulesEngineActionArgs
                {
                    RouteConfigurationOverride = new AzureNative.Network.Inputs.ForwardingConfigurationArgs
                    {
                        BackendPool = new AzureNative.Network.Inputs.SubResourceArgs
                        {
                            Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/backendPools/backendPool1",
                        },
                        CacheConfiguration = new AzureNative.Network.Inputs.CacheConfigurationArgs
                        {
                            CacheDuration = "P1DT12H20M30S",
                            DynamicCompression = "Disabled",
                            QueryParameterStripDirective = "StripOnly",
                            QueryParameters = "a=b,p=q",
                        },
                        ForwardingProtocol = "HttpsOnly",
                        OdataType = "#Microsoft.Azure.FrontDoor.Models.FrontdoorForwardingConfiguration",
                    },
                },
                MatchConditions = new[]
                {
                    new AzureNative.Network.Inputs.RulesEngineMatchConditionArgs
                    {
                        NegateCondition = false,
                        RulesEngineMatchValue = new[]
                        {
                            "allowoverride",
                        },
                        RulesEngineMatchVariable = "RequestHeader",
                        RulesEngineOperator = "Equal",
                        Selector = "Rules-Engine-Route-Forward",
                        Transforms = new[]
                        {
                            "Lowercase",
                        },
                    },
                },
                Name = "Rule3",
                Priority = 3,
            },
        },
        RulesEngineName = "rulesEngine1",
    });

});


```

```go
package main

import (
	network "github.com/pulumi/pulumi-azure-native-sdk/network"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := network.NewRulesEngine(ctx, "rulesEngine", &network.RulesEngineArgs{
			FrontDoorName:     pulumi.String("frontDoor1"),
			ResourceGroupName: pulumi.String("rg1"),
			Rules: []network.RulesEngineRuleArgs{
				{
					Action: {
						RouteConfigurationOverride: {
							CustomFragment:    "fragment",
							CustomHost:        "www.bing.com",
							CustomPath:        "/api",
							CustomQueryString: "a=b",
							OdataType:         "#Microsoft.Azure.FrontDoor.Models.FrontdoorRedirectConfiguration",
							RedirectProtocol:  "HttpsOnly",
							RedirectType:      "Moved",
						},
					},
					MatchConditions: network.RulesEngineMatchConditionArray{
						{
							RulesEngineMatchValue: pulumi.StringArray{
								pulumi.String("CH"),
							},
							RulesEngineMatchVariable: pulumi.String("RemoteAddr"),
							RulesEngineOperator:      pulumi.String("GeoMatch"),
						},
					},
					MatchProcessingBehavior: pulumi.String("Stop"),
					Name:                    pulumi.String("Rule1"),
					Priority:                pulumi.Int(1),
				},
				{
					Action: {
						ResponseHeaderActions: network.HeaderActionArray{
							{
								HeaderActionType: pulumi.String("Overwrite"),
								HeaderName:       pulumi.String("Cache-Control"),
								Value:            pulumi.String("public, max-age=31536000"),
							},
						},
					},
					MatchConditions: network.RulesEngineMatchConditionArray{
						{
							RulesEngineMatchValue: pulumi.StringArray{
								pulumi.String("jpg"),
							},
							RulesEngineMatchVariable: pulumi.String("RequestFilenameExtension"),
							RulesEngineOperator:      pulumi.String("Equal"),
							Transforms: pulumi.StringArray{
								pulumi.String("Lowercase"),
							},
						},
					},
					Name:     pulumi.String("Rule2"),
					Priority: pulumi.Int(2),
				},
				{
					Action: {
						RouteConfigurationOverride: {
							BackendPool: {
								Id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/backendPools/backendPool1",
							},
							CacheConfiguration: {
								CacheDuration:                "P1DT12H20M30S",
								DynamicCompression:           "Disabled",
								QueryParameterStripDirective: "StripOnly",
								QueryParameters:              "a=b,p=q",
							},
							ForwardingProtocol: "HttpsOnly",
							OdataType:          "#Microsoft.Azure.FrontDoor.Models.FrontdoorForwardingConfiguration",
						},
					},
					MatchConditions: network.RulesEngineMatchConditionArray{
						{
							NegateCondition: pulumi.Bool(false),
							RulesEngineMatchValue: pulumi.StringArray{
								pulumi.String("allowoverride"),
							},
							RulesEngineMatchVariable: pulumi.String("RequestHeader"),
							RulesEngineOperator:      pulumi.String("Equal"),
							Selector:                 pulumi.String("Rules-Engine-Route-Forward"),
							Transforms: pulumi.StringArray{
								pulumi.String("Lowercase"),
							},
						},
					},
					Name:     pulumi.String("Rule3"),
					Priority: pulumi.Int(3),
				},
			},
			RulesEngineName: pulumi.String("rulesEngine1"),
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
import com.pulumi.azurenative.network.RulesEngine;
import com.pulumi.azurenative.network.RulesEngineArgs;
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
        var rulesEngine = new RulesEngine("rulesEngine", RulesEngineArgs.builder()        
            .frontDoorName("frontDoor1")
            .resourceGroupName("rg1")
            .rules(            
                Map.ofEntries(
                    Map.entry("action", Map.of("routeConfigurationOverride", Map.ofEntries(
                        Map.entry("customFragment", "fragment"),
                        Map.entry("customHost", "www.bing.com"),
                        Map.entry("customPath", "/api"),
                        Map.entry("customQueryString", "a=b"),
                        Map.entry("odataType", "#Microsoft.Azure.FrontDoor.Models.FrontdoorRedirectConfiguration"),
                        Map.entry("redirectProtocol", "HttpsOnly"),
                        Map.entry("redirectType", "Moved")
                    ))),
                    Map.entry("matchConditions", Map.ofEntries(
                        Map.entry("rulesEngineMatchValue", "CH"),
                        Map.entry("rulesEngineMatchVariable", "RemoteAddr"),
                        Map.entry("rulesEngineOperator", "GeoMatch")
                    )),
                    Map.entry("matchProcessingBehavior", "Stop"),
                    Map.entry("name", "Rule1"),
                    Map.entry("priority", 1)
                ),
                Map.ofEntries(
                    Map.entry("action", Map.of("responseHeaderActions", Map.ofEntries(
                        Map.entry("headerActionType", "Overwrite"),
                        Map.entry("headerName", "Cache-Control"),
                        Map.entry("value", "public, max-age=31536000")
                    ))),
                    Map.entry("matchConditions", Map.ofEntries(
                        Map.entry("rulesEngineMatchValue", "jpg"),
                        Map.entry("rulesEngineMatchVariable", "RequestFilenameExtension"),
                        Map.entry("rulesEngineOperator", "Equal"),
                        Map.entry("transforms", "Lowercase")
                    )),
                    Map.entry("name", "Rule2"),
                    Map.entry("priority", 2)
                ),
                Map.ofEntries(
                    Map.entry("action", Map.of("routeConfigurationOverride", Map.ofEntries(
                        Map.entry("backendPool", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/backendPools/backendPool1")),
                        Map.entry("cacheConfiguration", Map.ofEntries(
                            Map.entry("cacheDuration", "P1DT12H20M30S"),
                            Map.entry("dynamicCompression", "Disabled"),
                            Map.entry("queryParameterStripDirective", "StripOnly"),
                            Map.entry("queryParameters", "a=b,p=q")
                        )),
                        Map.entry("forwardingProtocol", "HttpsOnly"),
                        Map.entry("odataType", "#Microsoft.Azure.FrontDoor.Models.FrontdoorForwardingConfiguration")
                    ))),
                    Map.entry("matchConditions", Map.ofEntries(
                        Map.entry("negateCondition", false),
                        Map.entry("rulesEngineMatchValue", "allowoverride"),
                        Map.entry("rulesEngineMatchVariable", "RequestHeader"),
                        Map.entry("rulesEngineOperator", "Equal"),
                        Map.entry("selector", "Rules-Engine-Route-Forward"),
                        Map.entry("transforms", "Lowercase")
                    )),
                    Map.entry("name", "Rule3"),
                    Map.entry("priority", 3)
                ))
            .rulesEngineName("rulesEngine1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const rulesEngine = new azure_native.network.RulesEngine("rulesEngine", {
    frontDoorName: "frontDoor1",
    resourceGroupName: "rg1",
    rules: [
        {
            action: {
                routeConfigurationOverride: {
                    customFragment: "fragment",
                    customHost: "www.bing.com",
                    customPath: "/api",
                    customQueryString: "a=b",
                    odataType: "#Microsoft.Azure.FrontDoor.Models.FrontdoorRedirectConfiguration",
                    redirectProtocol: "HttpsOnly",
                    redirectType: "Moved",
                },
            },
            matchConditions: [{
                rulesEngineMatchValue: ["CH"],
                rulesEngineMatchVariable: "RemoteAddr",
                rulesEngineOperator: "GeoMatch",
            }],
            matchProcessingBehavior: "Stop",
            name: "Rule1",
            priority: 1,
        },
        {
            action: {
                responseHeaderActions: [{
                    headerActionType: "Overwrite",
                    headerName: "Cache-Control",
                    value: "public, max-age=31536000",
                }],
            },
            matchConditions: [{
                rulesEngineMatchValue: ["jpg"],
                rulesEngineMatchVariable: "RequestFilenameExtension",
                rulesEngineOperator: "Equal",
                transforms: ["Lowercase"],
            }],
            name: "Rule2",
            priority: 2,
        },
        {
            action: {
                routeConfigurationOverride: {
                    backendPool: {
                        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/backendPools/backendPool1",
                    },
                    cacheConfiguration: {
                        cacheDuration: "P1DT12H20M30S",
                        dynamicCompression: "Disabled",
                        queryParameterStripDirective: "StripOnly",
                        queryParameters: "a=b,p=q",
                    },
                    forwardingProtocol: "HttpsOnly",
                    odataType: "#Microsoft.Azure.FrontDoor.Models.FrontdoorForwardingConfiguration",
                },
            },
            matchConditions: [{
                negateCondition: false,
                rulesEngineMatchValue: ["allowoverride"],
                rulesEngineMatchVariable: "RequestHeader",
                rulesEngineOperator: "Equal",
                selector: "Rules-Engine-Route-Forward",
                transforms: ["Lowercase"],
            }],
            name: "Rule3",
            priority: 3,
        },
    ],
    rulesEngineName: "rulesEngine1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

rules_engine = azure_native.network.RulesEngine("rulesEngine",
    front_door_name="frontDoor1",
    resource_group_name="rg1",
    rules=[
        {
            "action": azure_native.network.RulesEngineActionArgs(
                route_configuration_override=azure_native.network.RedirectConfigurationArgs(
                    custom_fragment="fragment",
                    custom_host="www.bing.com",
                    custom_path="/api",
                    custom_query_string="a=b",
                    odata_type="#Microsoft.Azure.FrontDoor.Models.FrontdoorRedirectConfiguration",
                    redirect_protocol="HttpsOnly",
                    redirect_type="Moved",
                ),
            ),
            "matchConditions": [azure_native.network.RulesEngineMatchConditionArgs(
                rules_engine_match_value=["CH"],
                rules_engine_match_variable="RemoteAddr",
                rules_engine_operator="GeoMatch",
            )],
            "matchProcessingBehavior": "Stop",
            "name": "Rule1",
            "priority": 1,
        },
        {
            "action": {
                "responseHeaderActions": [azure_native.network.HeaderActionArgs(
                    header_action_type="Overwrite",
                    header_name="Cache-Control",
                    value="public, max-age=31536000",
                )],
            },
            "matchConditions": [azure_native.network.RulesEngineMatchConditionArgs(
                rules_engine_match_value=["jpg"],
                rules_engine_match_variable="RequestFilenameExtension",
                rules_engine_operator="Equal",
                transforms=["Lowercase"],
            )],
            "name": "Rule2",
            "priority": 2,
        },
        {
            "action": azure_native.network.RulesEngineActionArgs(
                route_configuration_override=azure_native.network.ForwardingConfigurationArgs(
                    backend_pool=azure_native.network.SubResourceArgs(
                        id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/backendPools/backendPool1",
                    ),
                    cache_configuration=azure_native.network.CacheConfigurationArgs(
                        cache_duration="P1DT12H20M30S",
                        dynamic_compression="Disabled",
                        query_parameter_strip_directive="StripOnly",
                        query_parameters="a=b,p=q",
                    ),
                    forwarding_protocol="HttpsOnly",
                    odata_type="#Microsoft.Azure.FrontDoor.Models.FrontdoorForwardingConfiguration",
                ),
            ),
            "matchConditions": [azure_native.network.RulesEngineMatchConditionArgs(
                negate_condition=False,
                rules_engine_match_value=["allowoverride"],
                rules_engine_match_variable="RequestHeader",
                rules_engine_operator="Equal",
                selector="Rules-Engine-Route-Forward",
                transforms=["Lowercase"],
            )],
            "name": "Rule3",
            "priority": 3,
        },
    ],
    rules_engine_name="rulesEngine1")

```

```yaml
resources:
  rulesEngine:
    type: azure-native:network:RulesEngine
    properties:
      frontDoorName: frontDoor1
      resourceGroupName: rg1
      rules:
        - action:
            routeConfigurationOverride:
              customFragment: fragment
              customHost: www.bing.com
              customPath: /api
              customQueryString: a=b
              odataType: '#Microsoft.Azure.FrontDoor.Models.FrontdoorRedirectConfiguration'
              redirectProtocol: HttpsOnly
              redirectType: Moved
          matchConditions:
            - rulesEngineMatchValue:
                - CH
              rulesEngineMatchVariable: RemoteAddr
              rulesEngineOperator: GeoMatch
          matchProcessingBehavior: Stop
          name: Rule1
          priority: 1
        - action:
            responseHeaderActions:
              - headerActionType: Overwrite
                headerName: Cache-Control
                value: public, max-age=31536000
          matchConditions:
            - rulesEngineMatchValue:
                - jpg
              rulesEngineMatchVariable: RequestFilenameExtension
              rulesEngineOperator: Equal
              transforms:
                - Lowercase
          name: Rule2
          priority: 2
        - action:
            routeConfigurationOverride:
              backendPool:
                id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/backendPools/backendPool1
              cacheConfiguration:
                cacheDuration: P1DT12H20M30S
                dynamicCompression: Disabled
                queryParameterStripDirective: StripOnly
                queryParameters: a=b,p=q
              forwardingProtocol: HttpsOnly
              odataType: '#Microsoft.Azure.FrontDoor.Models.FrontdoorForwardingConfiguration'
          matchConditions:
            - negateCondition: false
              rulesEngineMatchValue:
                - allowoverride
              rulesEngineMatchVariable: RequestHeader
              rulesEngineOperator: Equal
              selector: Rules-Engine-Route-Forward
              transforms:
                - Lowercase
          name: Rule3
          priority: 3
      rulesEngineName: rulesEngine1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:RulesEngine rulesEngine1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/rulesEngines/rulesEngine1 
```
