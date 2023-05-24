The RoutePolicy resource definition.
API Version: 2023-02-01-preview.
Previous API Version: 2023-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### RoutePolicies_Create_MaximumSet_Gen
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var routePolicy = new AzureNative.ManagedNetworkFabric.RoutePolicy("routePolicy", new()
    {
        Annotation = "example routepolicy",
        Conditions = new[]
        {
            new AzureNative.ManagedNetworkFabric.Inputs.RoutePolicyPropertiesConditionsArgs
            {
                Action = new AzureNative.ManagedNetworkFabric.Inputs.RoutePolicyPropertiesActionArgs
                {
                    Action = "allow",
                    Set = new AzureNative.ManagedNetworkFabric.Inputs.RoutePolicyPropertiesSetArgs
                    {
                        Set = new AzureNative.ManagedNetworkFabric.Inputs.RoutePolicyPropertiesSetSetArgs
                        {
                            IpCommunityListIds = new[]
                            {
                                "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/ipCommunityLists/ipCommunityListName",
                            },
                            IpExtendedCommunityListIds = new[]
                            {
                                "",
                            },
                        },
                    },
                },
                Annotation = "",
                Match = new AzureNative.ManagedNetworkFabric.Inputs.RoutePolicyPropertiesMatchArgs
                {
                    AccessControlListIds = new[]
                    {
                        "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/accessControlLists/accessControlListName",
                    },
                    IpCommunityListIds = new[]
                    {
                        "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/ipCommunityLists/ipCommunityListName",
                    },
                    IpExtendedCommunityListIds = new[]
                    {
                        "",
                    },
                },
                SequenceNumber = 7,
            },
        },
        Description = "RPexample",
        Location = "EastUS",
        ResourceGroupName = "rgRoutePolicies",
        RoutePolicyName = "example RoutePolicy",
        Tags = 
        {
            { "key8254", "" },
        },
    });

});


```

```go
package main

import (
	managednetworkfabric "github.com/pulumi/pulumi-azure-native-sdk/managednetworkfabric"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := managednetworkfabric.NewRoutePolicy(ctx, "routePolicy", &managednetworkfabric.RoutePolicyArgs{
			Annotation: pulumi.String("example routepolicy"),
			Conditions: []managednetworkfabric.RoutePolicyPropertiesConditionsArgs{
				{
					Action: {
						Action: pulumi.String("allow"),
						Set: {
							Set: {
								IpCommunityListIds: pulumi.StringArray{
									pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/ipCommunityLists/ipCommunityListName"),
								},
								IpExtendedCommunityListIds: pulumi.StringArray{
									pulumi.String(""),
								},
							},
						},
					},
					Annotation: pulumi.String(""),
					Match: {
						AccessControlListIds: pulumi.StringArray{
							pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/accessControlLists/accessControlListName"),
						},
						IpCommunityListIds: pulumi.StringArray{
							pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/ipCommunityLists/ipCommunityListName"),
						},
						IpExtendedCommunityListIds: pulumi.StringArray{
							pulumi.String(""),
						},
					},
					SequenceNumber: pulumi.Int(7),
				},
			},
			Description:       pulumi.String("RPexample"),
			Location:          pulumi.String("EastUS"),
			ResourceGroupName: pulumi.String("rgRoutePolicies"),
			RoutePolicyName:   pulumi.String("example RoutePolicy"),
			Tags: pulumi.StringMap{
				"key8254": pulumi.String(""),
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
import com.pulumi.azurenative.managednetworkfabric.RoutePolicy;
import com.pulumi.azurenative.managednetworkfabric.RoutePolicyArgs;
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
        var routePolicy = new RoutePolicy("routePolicy", RoutePolicyArgs.builder()        
            .annotation("example routepolicy")
            .conditions(Map.ofEntries(
                Map.entry("action", Map.ofEntries(
                    Map.entry("action", "allow"),
                    Map.entry("set", Map.of("set", Map.ofEntries(
                        Map.entry("ipCommunityListIds", "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/ipCommunityLists/ipCommunityListName"),
                        Map.entry("ipExtendedCommunityListIds", "")
                    )))
                )),
                Map.entry("annotation", ""),
                Map.entry("match", Map.ofEntries(
                    Map.entry("accessControlListIds", "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/accessControlLists/accessControlListName"),
                    Map.entry("ipCommunityListIds", "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/ipCommunityLists/ipCommunityListName"),
                    Map.entry("ipExtendedCommunityListIds", "")
                )),
                Map.entry("sequenceNumber", 7)
            ))
            .description("RPexample")
            .location("EastUS")
            .resourceGroupName("rgRoutePolicies")
            .routePolicyName("example RoutePolicy")
            .tags(Map.of("key8254", ""))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const routePolicy = new azure_native.managednetworkfabric.RoutePolicy("routePolicy", {
    annotation: "example routepolicy",
    conditions: [{
        action: {
            action: "allow",
            set: {
                set: {
                    ipCommunityListIds: ["/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/ipCommunityLists/ipCommunityListName"],
                    ipExtendedCommunityListIds: [""],
                },
            },
        },
        annotation: "",
        match: {
            accessControlListIds: ["/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/accessControlLists/accessControlListName"],
            ipCommunityListIds: ["/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/ipCommunityLists/ipCommunityListName"],
            ipExtendedCommunityListIds: [""],
        },
        sequenceNumber: 7,
    }],
    description: "RPexample",
    location: "EastUS",
    resourceGroupName: "rgRoutePolicies",
    routePolicyName: "example RoutePolicy",
    tags: {
        key8254: "",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

route_policy = azure_native.managednetworkfabric.RoutePolicy("routePolicy",
    annotation="example routepolicy",
    conditions=[{
        "action": {
            "action": "allow",
            "set": {
                "set": azure_native.managednetworkfabric.RoutePolicyPropertiesSetSetArgs(
                    ip_community_list_ids=["/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/ipCommunityLists/ipCommunityListName"],
                    ip_extended_community_list_ids=[""],
                ),
            },
        },
        "annotation": "",
        "match": azure_native.managednetworkfabric.RoutePolicyPropertiesMatchArgs(
            access_control_list_ids=["/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/accessControlLists/accessControlListName"],
            ip_community_list_ids=["/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/ipCommunityLists/ipCommunityListName"],
            ip_extended_community_list_ids=[""],
        ),
        "sequenceNumber": 7,
    }],
    description="RPexample",
    location="EastUS",
    resource_group_name="rgRoutePolicies",
    route_policy_name="example RoutePolicy",
    tags={
        "key8254": "",
    })

```

```yaml
resources:
  routePolicy:
    type: azure-native:managednetworkfabric:RoutePolicy
    properties:
      annotation: example routepolicy
      conditions:
        - action:
            action: allow
            set:
              set:
                ipCommunityListIds:
                  - /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/ipCommunityLists/ipCommunityListName
                ipExtendedCommunityListIds:
                  -
          annotation:
          match:
            accessControlListIds:
              - /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/accessControlLists/accessControlListName
            ipCommunityListIds:
              - /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/ipCommunityLists/ipCommunityListName
            ipExtendedCommunityListIds:
              -
          sequenceNumber: 7
      description: RPexample
      location: EastUS
      resourceGroupName: rgRoutePolicies
      routePolicyName: example RoutePolicy
      tags:
        key8254:

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:managednetworkfabric:RoutePolicy routePolicyName /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName 
```
