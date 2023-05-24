Collector policy resource.
API Version: 2022-11-01.
Previous API Version: 2022-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a collection policy
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var collectorPolicy = new AzureNative.NetworkFunction.CollectorPolicy("collectorPolicy", new()
    {
        AzureTrafficCollectorName = "atc",
        CollectorPolicyName = "cp1",
        EmissionPolicies = new[]
        {
            new AzureNative.NetworkFunction.Inputs.EmissionPoliciesPropertiesFormatArgs
            {
                EmissionDestinations = new[]
                {
                    new AzureNative.NetworkFunction.Inputs.EmissionPolicyDestinationArgs
                    {
                        DestinationType = "AzureMonitor",
                    },
                },
                EmissionType = "IPFIX",
            },
        },
        IngestionPolicy = new AzureNative.NetworkFunction.Inputs.IngestionPolicyPropertiesFormatArgs
        {
            IngestionSources = new[]
            {
                new AzureNative.NetworkFunction.Inputs.IngestionSourcesPropertiesFormatArgs
                {
                    ResourceId = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/expressRouteCircuits/circuitName",
                    SourceType = "Resource",
                },
            },
            IngestionType = "IPFIX",
        },
        Location = "West US",
        ResourceGroupName = "rg1",
    });

});


```

```go
package main

import (
	networkfunction "github.com/pulumi/pulumi-azure-native-sdk/networkfunction"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := networkfunction.NewCollectorPolicy(ctx, "collectorPolicy", &networkfunction.CollectorPolicyArgs{
			AzureTrafficCollectorName: pulumi.String("atc"),
			CollectorPolicyName:       pulumi.String("cp1"),
			EmissionPolicies: []networkfunction.EmissionPoliciesPropertiesFormatArgs{
				{
					EmissionDestinations: networkfunction.EmissionPolicyDestinationArray{
						{
							DestinationType: pulumi.String("AzureMonitor"),
						},
					},
					EmissionType: pulumi.String("IPFIX"),
				},
			},
			IngestionPolicy: networkfunction.IngestionPolicyPropertiesFormatResponse{
				IngestionSources: networkfunction.IngestionSourcesPropertiesFormatArray{
					&networkfunction.IngestionSourcesPropertiesFormatArgs{
						ResourceId: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/expressRouteCircuits/circuitName"),
						SourceType: pulumi.String("Resource"),
					},
				},
				IngestionType: pulumi.String("IPFIX"),
			},
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("rg1"),
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
import com.pulumi.azurenative.networkfunction.CollectorPolicy;
import com.pulumi.azurenative.networkfunction.CollectorPolicyArgs;
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
        var collectorPolicy = new CollectorPolicy("collectorPolicy", CollectorPolicyArgs.builder()        
            .azureTrafficCollectorName("atc")
            .collectorPolicyName("cp1")
            .emissionPolicies(Map.ofEntries(
                Map.entry("emissionDestinations", Map.of("destinationType", "AzureMonitor")),
                Map.entry("emissionType", "IPFIX")
            ))
            .ingestionPolicy(Map.ofEntries(
                Map.entry("ingestionSources", Map.ofEntries(
                    Map.entry("resourceId", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/expressRouteCircuits/circuitName"),
                    Map.entry("sourceType", "Resource")
                )),
                Map.entry("ingestionType", "IPFIX")
            ))
            .location("West US")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const collectorPolicy = new azure_native.networkfunction.CollectorPolicy("collectorPolicy", {
    azureTrafficCollectorName: "atc",
    collectorPolicyName: "cp1",
    emissionPolicies: [{
        emissionDestinations: [{
            destinationType: "AzureMonitor",
        }],
        emissionType: "IPFIX",
    }],
    ingestionPolicy: {
        ingestionSources: [{
            resourceId: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/expressRouteCircuits/circuitName",
            sourceType: "Resource",
        }],
        ingestionType: "IPFIX",
    },
    location: "West US",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

collector_policy = azure_native.networkfunction.CollectorPolicy("collectorPolicy",
    azure_traffic_collector_name="atc",
    collector_policy_name="cp1",
    emission_policies=[{
        "emissionDestinations": [azure_native.networkfunction.EmissionPolicyDestinationArgs(
            destination_type="AzureMonitor",
        )],
        "emissionType": "IPFIX",
    }],
    ingestion_policy=azure_native.networkfunction.IngestionPolicyPropertiesFormatResponseArgs(
        ingestion_sources=[azure_native.networkfunction.IngestionSourcesPropertiesFormatArgs(
            resource_id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/expressRouteCircuits/circuitName",
            source_type="Resource",
        )],
        ingestion_type="IPFIX",
    ),
    location="West US",
    resource_group_name="rg1")

```

```yaml
resources:
  collectorPolicy:
    type: azure-native:networkfunction:CollectorPolicy
    properties:
      azureTrafficCollectorName: atc
      collectorPolicyName: cp1
      emissionPolicies:
        - emissionDestinations:
            - destinationType: AzureMonitor
          emissionType: IPFIX
      ingestionPolicy:
        ingestionSources:
          - resourceId: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/expressRouteCircuits/circuitName
            sourceType: Resource
        ingestionType: IPFIX
      location: West US
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:networkfunction:CollectorPolicy cp1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.NetworkFunction/AzureTrafficCollector/atc/collectorPolicies/cp1 
```
