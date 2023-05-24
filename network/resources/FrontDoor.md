Front Door represents a collection of backend endpoints to route traffic to along with rules that specify how traffic is sent there.
API Version: 2021-06-01.
Previous API Version: 2020-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update specific Front Door
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var frontDoor = new AzureNative.Network.FrontDoor("frontDoor", new()
    {
        BackendPools = new[]
        {
            new AzureNative.Network.Inputs.BackendPoolArgs
            {
                Backends = new[]
                {
                    new AzureNative.Network.Inputs.BackendArgs
                    {
                        Address = "w3.contoso.com",
                        HttpPort = 80,
                        HttpsPort = 443,
                        Priority = 2,
                        Weight = 1,
                    },
                    new AzureNative.Network.Inputs.BackendArgs
                    {
                        Address = "contoso.com.website-us-west-2.othercloud.net",
                        HttpPort = 80,
                        HttpsPort = 443,
                        Priority = 1,
                        PrivateLinkApprovalMessage = "Please approve the connection request for this Private Link",
                        PrivateLinkLocation = "eastus",
                        PrivateLinkResourceId = "/subscriptions/subid/resourcegroups/rg1/providers/Microsoft.Network/privateLinkServices/pls1",
                        Weight = 2,
                    },
                    new AzureNative.Network.Inputs.BackendArgs
                    {
                        Address = "10.0.1.5",
                        HttpPort = 80,
                        HttpsPort = 443,
                        Priority = 1,
                        PrivateLinkAlias = "APPSERVER.d84e61f0-0870-4d24-9746-7438fa0019d1.westus2.azure.privatelinkservice",
                        PrivateLinkApprovalMessage = "Please approve this request to connect to the Private Link",
                        Weight = 1,
                    },
                },
                HealthProbeSettings = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/healthProbeSettings/healthProbeSettings1",
                },
                LoadBalancingSettings = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/loadBalancingSettings/loadBalancingSettings1",
                },
                Name = "backendPool1",
            },
        },
        BackendPoolsSettings = new AzureNative.Network.Inputs.BackendPoolsSettingsArgs
        {
            EnforceCertificateNameCheck = "Enabled",
            SendRecvTimeoutSeconds = 60,
        },
        EnabledState = "Enabled",
        FrontDoorName = "frontDoor1",
        FrontendEndpoints = new[]
        {
            new AzureNative.Network.Inputs.FrontendEndpointArgs
            {
                HostName = "www.contoso.com",
                Name = "frontendEndpoint1",
                SessionAffinityEnabledState = "Enabled",
                SessionAffinityTtlSeconds = 60,
                WebApplicationFirewallPolicyLink = new AzureNative.Network.Inputs.FrontendEndpointUpdateParametersWebApplicationFirewallPolicyLinkArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoorWebApplicationFirewallPolicies/policy1",
                },
            },
            new AzureNative.Network.Inputs.FrontendEndpointArgs
            {
                HostName = "frontDoor1.azurefd.net",
                Name = "default",
            },
        },
        HealthProbeSettings = new[]
        {
            new AzureNative.Network.Inputs.HealthProbeSettingsModelArgs
            {
                EnabledState = "Enabled",
                HealthProbeMethod = "HEAD",
                IntervalInSeconds = 120,
                Name = "healthProbeSettings1",
                Path = "/",
                Protocol = "Http",
            },
        },
        LoadBalancingSettings = new[]
        {
            new AzureNative.Network.Inputs.LoadBalancingSettingsModelArgs
            {
                Name = "loadBalancingSettings1",
                SampleSize = 4,
                SuccessfulSamplesRequired = 2,
            },
        },
        Location = "westus",
        ResourceGroupName = "rg1",
        RoutingRules = new[]
        {
            new AzureNative.Network.Inputs.RoutingRuleArgs
            {
                AcceptedProtocols = new[]
                {
                    "Http",
                },
                EnabledState = "Enabled",
                FrontendEndpoints = new[]
                {
                    new AzureNative.Network.Inputs.SubResourceArgs
                    {
                        Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/frontendEndpoints/frontendEndpoint1",
                    },
                    new AzureNative.Network.Inputs.SubResourceArgs
                    {
                        Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/frontendEndpoints/default",
                    },
                },
                Name = "routingRule1",
                PatternsToMatch = new[]
                {
                    "/*",
                },
                RouteConfiguration = new AzureNative.Network.Inputs.ForwardingConfigurationArgs
                {
                    BackendPool = new AzureNative.Network.Inputs.SubResourceArgs
                    {
                        Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/backendPools/backendPool1",
                    },
                    OdataType = "#Microsoft.Azure.FrontDoor.Models.FrontdoorForwardingConfiguration",
                },
                RulesEngine = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/rulesEngines/rulesEngine1",
                },
                WebApplicationFirewallPolicyLink = new AzureNative.Network.Inputs.RoutingRuleUpdateParametersWebApplicationFirewallPolicyLinkArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoorWebApplicationFirewallPolicies/policy1",
                },
            },
        },
        Tags = 
        {
            { "tag1", "value1" },
            { "tag2", "value2" },
        },
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
		_, err := network.NewFrontDoor(ctx, "frontDoor", &network.FrontDoorArgs{
			BackendPools: []network.BackendPoolArgs{
				{
					Backends: network.BackendArray{
						{
							Address:   pulumi.String("w3.contoso.com"),
							HttpPort:  pulumi.Int(80),
							HttpsPort: pulumi.Int(443),
							Priority:  pulumi.Int(2),
							Weight:    pulumi.Int(1),
						},
						{
							Address:                    pulumi.String("contoso.com.website-us-west-2.othercloud.net"),
							HttpPort:                   pulumi.Int(80),
							HttpsPort:                  pulumi.Int(443),
							Priority:                   pulumi.Int(1),
							PrivateLinkApprovalMessage: pulumi.String("Please approve the connection request for this Private Link"),
							PrivateLinkLocation:        pulumi.String("eastus"),
							PrivateLinkResourceId:      pulumi.String("/subscriptions/subid/resourcegroups/rg1/providers/Microsoft.Network/privateLinkServices/pls1"),
							Weight:                     pulumi.Int(2),
						},
						{
							Address:                    pulumi.String("10.0.1.5"),
							HttpPort:                   pulumi.Int(80),
							HttpsPort:                  pulumi.Int(443),
							Priority:                   pulumi.Int(1),
							PrivateLinkAlias:           pulumi.String("APPSERVER.d84e61f0-0870-4d24-9746-7438fa0019d1.westus2.azure.privatelinkservice"),
							PrivateLinkApprovalMessage: pulumi.String("Please approve this request to connect to the Private Link"),
							Weight:                     pulumi.Int(1),
						},
					},
					HealthProbeSettings: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/healthProbeSettings/healthProbeSettings1"),
					},
					LoadBalancingSettings: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/loadBalancingSettings/loadBalancingSettings1"),
					},
					Name: pulumi.String("backendPool1"),
				},
			},
			BackendPoolsSettings: &network.BackendPoolsSettingsArgs{
				EnforceCertificateNameCheck: pulumi.String("Enabled"),
				SendRecvTimeoutSeconds:      pulumi.Int(60),
			},
			EnabledState:  pulumi.String("Enabled"),
			FrontDoorName: pulumi.String("frontDoor1"),
			FrontendEndpoints: []network.FrontendEndpointArgs{
				{
					HostName:                    pulumi.String("www.contoso.com"),
					Name:                        pulumi.String("frontendEndpoint1"),
					SessionAffinityEnabledState: pulumi.String("Enabled"),
					SessionAffinityTtlSeconds:   pulumi.Int(60),
					WebApplicationFirewallPolicyLink: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoorWebApplicationFirewallPolicies/policy1"),
					},
				},
				{
					HostName: pulumi.String("frontDoor1.azurefd.net"),
					Name:     pulumi.String("default"),
				},
			},
			HealthProbeSettings: []network.HealthProbeSettingsModelArgs{
				{
					EnabledState:      pulumi.String("Enabled"),
					HealthProbeMethod: pulumi.String("HEAD"),
					IntervalInSeconds: pulumi.Int(120),
					Name:              pulumi.String("healthProbeSettings1"),
					Path:              pulumi.String("/"),
					Protocol:          pulumi.String("Http"),
				},
			},
			LoadBalancingSettings: []network.LoadBalancingSettingsModelArgs{
				{
					Name:                      pulumi.String("loadBalancingSettings1"),
					SampleSize:                pulumi.Int(4),
					SuccessfulSamplesRequired: pulumi.Int(2),
				},
			},
			Location:          pulumi.String("westus"),
			ResourceGroupName: pulumi.String("rg1"),
			RoutingRules: []network.RoutingRuleArgs{
				{
					AcceptedProtocols: pulumi.StringArray{
						pulumi.String("Http"),
					},
					EnabledState: pulumi.String("Enabled"),
					FrontendEndpoints: network.SubResourceArray{
						{
							Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/frontendEndpoints/frontendEndpoint1"),
						},
						{
							Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/frontendEndpoints/default"),
						},
					},
					Name: pulumi.String("routingRule1"),
					PatternsToMatch: pulumi.StringArray{
						pulumi.String("/*"),
					},
					RouteConfiguration: {
						BackendPool: {
							Id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/backendPools/backendPool1",
						},
						OdataType: "#Microsoft.Azure.FrontDoor.Models.FrontdoorForwardingConfiguration",
					},
					RulesEngine: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/rulesEngines/rulesEngine1"),
					},
					WebApplicationFirewallPolicyLink: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoorWebApplicationFirewallPolicies/policy1"),
					},
				},
			},
			Tags: pulumi.StringMap{
				"tag1": pulumi.String("value1"),
				"tag2": pulumi.String("value2"),
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
import com.pulumi.azurenative.network.FrontDoor;
import com.pulumi.azurenative.network.FrontDoorArgs;
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
        var frontDoor = new FrontDoor("frontDoor", FrontDoorArgs.builder()        
            .backendPools(Map.ofEntries(
                Map.entry("backends",                 
                    Map.ofEntries(
                        Map.entry("address", "w3.contoso.com"),
                        Map.entry("httpPort", 80),
                        Map.entry("httpsPort", 443),
                        Map.entry("priority", 2),
                        Map.entry("weight", 1)
                    ),
                    Map.ofEntries(
                        Map.entry("address", "contoso.com.website-us-west-2.othercloud.net"),
                        Map.entry("httpPort", 80),
                        Map.entry("httpsPort", 443),
                        Map.entry("priority", 1),
                        Map.entry("privateLinkApprovalMessage", "Please approve the connection request for this Private Link"),
                        Map.entry("privateLinkLocation", "eastus"),
                        Map.entry("privateLinkResourceId", "/subscriptions/subid/resourcegroups/rg1/providers/Microsoft.Network/privateLinkServices/pls1"),
                        Map.entry("weight", 2)
                    ),
                    Map.ofEntries(
                        Map.entry("address", "10.0.1.5"),
                        Map.entry("httpPort", 80),
                        Map.entry("httpsPort", 443),
                        Map.entry("priority", 1),
                        Map.entry("privateLinkAlias", "APPSERVER.d84e61f0-0870-4d24-9746-7438fa0019d1.westus2.azure.privatelinkservice"),
                        Map.entry("privateLinkApprovalMessage", "Please approve this request to connect to the Private Link"),
                        Map.entry("weight", 1)
                    )),
                Map.entry("healthProbeSettings", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/healthProbeSettings/healthProbeSettings1")),
                Map.entry("loadBalancingSettings", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/loadBalancingSettings/loadBalancingSettings1")),
                Map.entry("name", "backendPool1")
            ))
            .backendPoolsSettings(Map.ofEntries(
                Map.entry("enforceCertificateNameCheck", "Enabled"),
                Map.entry("sendRecvTimeoutSeconds", 60)
            ))
            .enabledState("Enabled")
            .frontDoorName("frontDoor1")
            .frontendEndpoints(            
                Map.ofEntries(
                    Map.entry("hostName", "www.contoso.com"),
                    Map.entry("name", "frontendEndpoint1"),
                    Map.entry("sessionAffinityEnabledState", "Enabled"),
                    Map.entry("sessionAffinityTtlSeconds", 60),
                    Map.entry("webApplicationFirewallPolicyLink", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoorWebApplicationFirewallPolicies/policy1"))
                ),
                Map.ofEntries(
                    Map.entry("hostName", "frontDoor1.azurefd.net"),
                    Map.entry("name", "default")
                ))
            .healthProbeSettings(Map.ofEntries(
                Map.entry("enabledState", "Enabled"),
                Map.entry("healthProbeMethod", "HEAD"),
                Map.entry("intervalInSeconds", 120),
                Map.entry("name", "healthProbeSettings1"),
                Map.entry("path", "/"),
                Map.entry("protocol", "Http")
            ))
            .loadBalancingSettings(Map.ofEntries(
                Map.entry("name", "loadBalancingSettings1"),
                Map.entry("sampleSize", 4),
                Map.entry("successfulSamplesRequired", 2)
            ))
            .location("westus")
            .resourceGroupName("rg1")
            .routingRules(Map.ofEntries(
                Map.entry("acceptedProtocols", "Http"),
                Map.entry("enabledState", "Enabled"),
                Map.entry("frontendEndpoints",                 
                    Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/frontendEndpoints/frontendEndpoint1"),
                    Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/frontendEndpoints/default")),
                Map.entry("name", "routingRule1"),
                Map.entry("patternsToMatch", "/*"),
                Map.entry("routeConfiguration", Map.ofEntries(
                    Map.entry("backendPool", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/backendPools/backendPool1")),
                    Map.entry("odataType", "#Microsoft.Azure.FrontDoor.Models.FrontdoorForwardingConfiguration")
                )),
                Map.entry("rulesEngine", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/rulesEngines/rulesEngine1")),
                Map.entry("webApplicationFirewallPolicyLink", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoorWebApplicationFirewallPolicies/policy1"))
            ))
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

const frontDoor = new azure_native.network.FrontDoor("frontDoor", {
    backendPools: [{
        backends: [
            {
                address: "w3.contoso.com",
                httpPort: 80,
                httpsPort: 443,
                priority: 2,
                weight: 1,
            },
            {
                address: "contoso.com.website-us-west-2.othercloud.net",
                httpPort: 80,
                httpsPort: 443,
                priority: 1,
                privateLinkApprovalMessage: "Please approve the connection request for this Private Link",
                privateLinkLocation: "eastus",
                privateLinkResourceId: "/subscriptions/subid/resourcegroups/rg1/providers/Microsoft.Network/privateLinkServices/pls1",
                weight: 2,
            },
            {
                address: "10.0.1.5",
                httpPort: 80,
                httpsPort: 443,
                priority: 1,
                privateLinkAlias: "APPSERVER.d84e61f0-0870-4d24-9746-7438fa0019d1.westus2.azure.privatelinkservice",
                privateLinkApprovalMessage: "Please approve this request to connect to the Private Link",
                weight: 1,
            },
        ],
        healthProbeSettings: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/healthProbeSettings/healthProbeSettings1",
        },
        loadBalancingSettings: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/loadBalancingSettings/loadBalancingSettings1",
        },
        name: "backendPool1",
    }],
    backendPoolsSettings: {
        enforceCertificateNameCheck: "Enabled",
        sendRecvTimeoutSeconds: 60,
    },
    enabledState: "Enabled",
    frontDoorName: "frontDoor1",
    frontendEndpoints: [
        {
            hostName: "www.contoso.com",
            name: "frontendEndpoint1",
            sessionAffinityEnabledState: "Enabled",
            sessionAffinityTtlSeconds: 60,
            webApplicationFirewallPolicyLink: {
                id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoorWebApplicationFirewallPolicies/policy1",
            },
        },
        {
            hostName: "frontDoor1.azurefd.net",
            name: "default",
        },
    ],
    healthProbeSettings: [{
        enabledState: "Enabled",
        healthProbeMethod: "HEAD",
        intervalInSeconds: 120,
        name: "healthProbeSettings1",
        path: "/",
        protocol: "Http",
    }],
    loadBalancingSettings: [{
        name: "loadBalancingSettings1",
        sampleSize: 4,
        successfulSamplesRequired: 2,
    }],
    location: "westus",
    resourceGroupName: "rg1",
    routingRules: [{
        acceptedProtocols: ["Http"],
        enabledState: "Enabled",
        frontendEndpoints: [
            {
                id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/frontendEndpoints/frontendEndpoint1",
            },
            {
                id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/frontendEndpoints/default",
            },
        ],
        name: "routingRule1",
        patternsToMatch: ["/*"],
        routeConfiguration: {
            backendPool: {
                id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/backendPools/backendPool1",
            },
            odataType: "#Microsoft.Azure.FrontDoor.Models.FrontdoorForwardingConfiguration",
        },
        rulesEngine: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/rulesEngines/rulesEngine1",
        },
        webApplicationFirewallPolicyLink: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoorWebApplicationFirewallPolicies/policy1",
        },
    }],
    tags: {
        tag1: "value1",
        tag2: "value2",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

front_door = azure_native.network.FrontDoor("frontDoor",
    backend_pools=[{
        "backends": [
            azure_native.network.BackendArgs(
                address="w3.contoso.com",
                http_port=80,
                https_port=443,
                priority=2,
                weight=1,
            ),
            azure_native.network.BackendArgs(
                address="contoso.com.website-us-west-2.othercloud.net",
                http_port=80,
                https_port=443,
                priority=1,
                private_link_approval_message="Please approve the connection request for this Private Link",
                private_link_location="eastus",
                private_link_resource_id="/subscriptions/subid/resourcegroups/rg1/providers/Microsoft.Network/privateLinkServices/pls1",
                weight=2,
            ),
            azure_native.network.BackendArgs(
                address="10.0.1.5",
                http_port=80,
                https_port=443,
                priority=1,
                private_link_alias="APPSERVER.d84e61f0-0870-4d24-9746-7438fa0019d1.westus2.azure.privatelinkservice",
                private_link_approval_message="Please approve this request to connect to the Private Link",
                weight=1,
            ),
        ],
        "healthProbeSettings": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/healthProbeSettings/healthProbeSettings1",
        ),
        "loadBalancingSettings": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/loadBalancingSettings/loadBalancingSettings1",
        ),
        "name": "backendPool1",
    }],
    backend_pools_settings=azure_native.network.BackendPoolsSettingsArgs(
        enforce_certificate_name_check="Enabled",
        send_recv_timeout_seconds=60,
    ),
    enabled_state="Enabled",
    front_door_name="frontDoor1",
    frontend_endpoints=[
        {
            "hostName": "www.contoso.com",
            "name": "frontendEndpoint1",
            "sessionAffinityEnabledState": "Enabled",
            "sessionAffinityTtlSeconds": 60,
            "webApplicationFirewallPolicyLink": azure_native.network.FrontendEndpointUpdateParametersWebApplicationFirewallPolicyLinkArgs(
                id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoorWebApplicationFirewallPolicies/policy1",
            ),
        },
        azure_native.network.FrontendEndpointArgs(
            host_name="frontDoor1.azurefd.net",
            name="default",
        ),
    ],
    health_probe_settings=[azure_native.network.HealthProbeSettingsModelArgs(
        enabled_state="Enabled",
        health_probe_method="HEAD",
        interval_in_seconds=120,
        name="healthProbeSettings1",
        path="/",
        protocol="Http",
    )],
    load_balancing_settings=[azure_native.network.LoadBalancingSettingsModelArgs(
        name="loadBalancingSettings1",
        sample_size=4,
        successful_samples_required=2,
    )],
    location="westus",
    resource_group_name="rg1",
    routing_rules=[{
        "acceptedProtocols": ["Http"],
        "enabledState": "Enabled",
        "frontendEndpoints": [
            azure_native.network.SubResourceArgs(
                id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/frontendEndpoints/frontendEndpoint1",
            ),
            azure_native.network.SubResourceArgs(
                id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/frontendEndpoints/default",
            ),
        ],
        "name": "routingRule1",
        "patternsToMatch": ["/*"],
        "routeConfiguration": azure_native.network.ForwardingConfigurationArgs(
            backend_pool=azure_native.network.SubResourceArgs(
                id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/backendPools/backendPool1",
            ),
            odata_type="#Microsoft.Azure.FrontDoor.Models.FrontdoorForwardingConfiguration",
        ),
        "rulesEngine": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/rulesEngines/rulesEngine1",
        ),
        "webApplicationFirewallPolicyLink": azure_native.network.RoutingRuleUpdateParametersWebApplicationFirewallPolicyLinkArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoorWebApplicationFirewallPolicies/policy1",
        ),
    }],
    tags={
        "tag1": "value1",
        "tag2": "value2",
    })

```

```yaml
resources:
  frontDoor:
    type: azure-native:network:FrontDoor
    properties:
      backendPools:
        - backends:
            - address: w3.contoso.com
              httpPort: 80
              httpsPort: 443
              priority: 2
              weight: 1
            - address: contoso.com.website-us-west-2.othercloud.net
              httpPort: 80
              httpsPort: 443
              priority: 1
              privateLinkApprovalMessage: Please approve the connection request for this Private Link
              privateLinkLocation: eastus
              privateLinkResourceId: /subscriptions/subid/resourcegroups/rg1/providers/Microsoft.Network/privateLinkServices/pls1
              weight: 2
            - address: 10.0.1.5
              httpPort: 80
              httpsPort: 443
              priority: 1
              privateLinkAlias: APPSERVER.d84e61f0-0870-4d24-9746-7438fa0019d1.westus2.azure.privatelinkservice
              privateLinkApprovalMessage: Please approve this request to connect to the Private Link
              weight: 1
          healthProbeSettings:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/healthProbeSettings/healthProbeSettings1
          loadBalancingSettings:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/loadBalancingSettings/loadBalancingSettings1
          name: backendPool1
      backendPoolsSettings:
        enforceCertificateNameCheck: Enabled
        sendRecvTimeoutSeconds: 60
      enabledState: Enabled
      frontDoorName: frontDoor1
      frontendEndpoints:
        - hostName: www.contoso.com
          name: frontendEndpoint1
          sessionAffinityEnabledState: Enabled
          sessionAffinityTtlSeconds: 60
          webApplicationFirewallPolicyLink:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoorWebApplicationFirewallPolicies/policy1
        - hostName: frontDoor1.azurefd.net
          name: default
      healthProbeSettings:
        - enabledState: Enabled
          healthProbeMethod: HEAD
          intervalInSeconds: 120
          name: healthProbeSettings1
          path: /
          protocol: Http
      loadBalancingSettings:
        - name: loadBalancingSettings1
          sampleSize: 4
          successfulSamplesRequired: 2
      location: westus
      resourceGroupName: rg1
      routingRules:
        - acceptedProtocols:
            - Http
          enabledState: Enabled
          frontendEndpoints:
            - id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/frontendEndpoints/frontendEndpoint1
            - id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/frontendEndpoints/default
          name: routingRule1
          patternsToMatch:
            - /*
          routeConfiguration:
            backendPool:
              id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/backendPools/backendPool1
            odataType: '#Microsoft.Azure.FrontDoor.Models.FrontdoorForwardingConfiguration'
          rulesEngine:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1/rulesEngines/rulesEngine1
          webApplicationFirewallPolicyLink:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoorWebApplicationFirewallPolicies/policy1
      tags:
        tag1: value1
        tag2: value2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:FrontDoor frontDoor1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/frontDoors/frontDoor1 
```
