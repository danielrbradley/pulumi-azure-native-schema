The service resource.
API Version: 2023-02-01-preview.
Previous API Version: 2020-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Put a service with maximum parameters
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var service = new AzureNative.ServiceFabric.Service("service", new()
    {
        ApplicationName = "myApp",
        ClusterName = "myCluster",
        Location = "eastus",
        Properties = new AzureNative.ServiceFabric.Inputs.StatelessServicePropertiesArgs
        {
            CorrelationScheme = new[]
            {
                new AzureNative.ServiceFabric.Inputs.ServiceCorrelationArgs
                {
                    Scheme = "AlignedAffinity",
                    ServiceName = "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/resRg/providers/Microsoft.ServiceFabric/managedclusters/myCluster/applications/myApp/services/myService1",
                },
            },
            DefaultMoveCost = "Medium",
            InstanceCount = 5,
            MinInstanceCount = 3,
            MinInstancePercentage = 30,
            PartitionDescription = new AzureNative.ServiceFabric.Inputs.SingletonPartitionSchemeArgs
            {
                PartitionScheme = "Singleton",
            },
            PlacementConstraints = "NodeType==frontend",
            ScalingPolicies = new[]
            {
                new AzureNative.ServiceFabric.Inputs.ScalingPolicyArgs
                {
                    ScalingMechanism = new AzureNative.ServiceFabric.Inputs.PartitionInstanceCountScaleMechanismArgs
                    {
                        Kind = "ScalePartitionInstanceCount",
                        MaxInstanceCount = 9,
                        MinInstanceCount = 3,
                        ScaleIncrement = 2,
                    },
                    ScalingTrigger = new AzureNative.ServiceFabric.Inputs.AveragePartitionLoadScalingTriggerArgs
                    {
                        Kind = "AveragePartitionLoadTrigger",
                        LowerLoadThreshold = 2,
                        MetricName = "metricName",
                        ScaleInterval = "00:01:00",
                        UpperLoadThreshold = 8,
                    },
                },
            },
            ServiceDnsName = "myservicednsname.myApp",
            ServiceKind = "Stateless",
            ServiceLoadMetrics = new[]
            {
                new AzureNative.ServiceFabric.Inputs.ServiceLoadMetricArgs
                {
                    DefaultLoad = 3,
                    Name = "metric1",
                    Weight = "Low",
                },
            },
            ServicePackageActivationMode = "SharedProcess",
            ServicePlacementPolicies = new[]
            {
                new AzureNative.ServiceFabric.Inputs.ServicePlacementNonPartiallyPlaceServicePolicyArgs
                {
                    Type = "NonPartiallyPlaceService",
                },
            },
            ServiceTypeName = "myServiceType",
        },
        ResourceGroupName = "resRg",
        ServiceName = "myService",
        Tags = 
        {
            { "a", "b" },
        },
    });

});


```

```go
package main

import (
	servicefabric "github.com/pulumi/pulumi-azure-native-sdk/servicefabric"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := servicefabric.NewService(ctx, "service", &servicefabric.ServiceArgs{
			ApplicationName: pulumi.String("myApp"),
			ClusterName:     pulumi.String("myCluster"),
			Location:        pulumi.String("eastus"),
			Properties: servicefabric.StatelessServiceProperties{
				CorrelationScheme: []servicefabric.ServiceCorrelation{
					{
						Scheme:      "AlignedAffinity",
						ServiceName: "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/resRg/providers/Microsoft.ServiceFabric/managedclusters/myCluster/applications/myApp/services/myService1",
					},
				},
				DefaultMoveCost:       "Medium",
				InstanceCount:         5,
				MinInstanceCount:      3,
				MinInstancePercentage: 30,
				PartitionDescription: servicefabric.SingletonPartitionScheme{
					PartitionScheme: "Singleton",
				},
				PlacementConstraints: "NodeType==frontend",
				ScalingPolicies: []servicefabric.ScalingPolicy{
					{
						ScalingMechanism: {
							Kind:             "ScalePartitionInstanceCount",
							MaxInstanceCount: 9,
							MinInstanceCount: 3,
							ScaleIncrement:   2,
						},
						ScalingTrigger: {
							Kind:               "AveragePartitionLoadTrigger",
							LowerLoadThreshold: 2,
							MetricName:         "metricName",
							ScaleInterval:      "00:01:00",
							UpperLoadThreshold: 8,
						},
					},
				},
				ServiceDnsName: "myservicednsname.myApp",
				ServiceKind:    "Stateless",
				ServiceLoadMetrics: []servicefabric.ServiceLoadMetric{
					{
						DefaultLoad: 3,
						Name:        "metric1",
						Weight:      "Low",
					},
				},
				ServicePackageActivationMode: "SharedProcess",
				ServicePlacementPolicies: []interface{}{
					servicefabric.ServicePlacementNonPartiallyPlaceServicePolicy{
						Type: "NonPartiallyPlaceService",
					},
				},
				ServiceTypeName: "myServiceType",
			},
			ResourceGroupName: pulumi.String("resRg"),
			ServiceName:       pulumi.String("myService"),
			Tags: pulumi.StringMap{
				"a": pulumi.String("b"),
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
import com.pulumi.azurenative.servicefabric.Service;
import com.pulumi.azurenative.servicefabric.ServiceArgs;
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
        var service = new Service("service", ServiceArgs.builder()        
            .applicationName("myApp")
            .clusterName("myCluster")
            .location("eastus")
            .properties(Map.ofEntries(
                Map.entry("correlationScheme", Map.ofEntries(
                    Map.entry("scheme", "AlignedAffinity"),
                    Map.entry("serviceName", "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/resRg/providers/Microsoft.ServiceFabric/managedclusters/myCluster/applications/myApp/services/myService1")
                )),
                Map.entry("defaultMoveCost", "Medium"),
                Map.entry("instanceCount", 5),
                Map.entry("minInstanceCount", 3),
                Map.entry("minInstancePercentage", 30),
                Map.entry("partitionDescription", Map.of("partitionScheme", "Singleton")),
                Map.entry("placementConstraints", "NodeType==frontend"),
                Map.entry("scalingPolicies", Map.ofEntries(
                    Map.entry("scalingMechanism", Map.ofEntries(
                        Map.entry("kind", "ScalePartitionInstanceCount"),
                        Map.entry("maxInstanceCount", 9),
                        Map.entry("minInstanceCount", 3),
                        Map.entry("scaleIncrement", 2)
                    )),
                    Map.entry("scalingTrigger", Map.ofEntries(
                        Map.entry("kind", "AveragePartitionLoadTrigger"),
                        Map.entry("lowerLoadThreshold", 2),
                        Map.entry("metricName", "metricName"),
                        Map.entry("scaleInterval", "00:01:00"),
                        Map.entry("upperLoadThreshold", 8)
                    ))
                )),
                Map.entry("serviceDnsName", "myservicednsname.myApp"),
                Map.entry("serviceKind", "Stateless"),
                Map.entry("serviceLoadMetrics", Map.ofEntries(
                    Map.entry("defaultLoad", 3),
                    Map.entry("name", "metric1"),
                    Map.entry("weight", "Low")
                )),
                Map.entry("servicePackageActivationMode", "SharedProcess"),
                Map.entry("servicePlacementPolicies", Map.of("type", "NonPartiallyPlaceService")),
                Map.entry("serviceTypeName", "myServiceType")
            ))
            .resourceGroupName("resRg")
            .serviceName("myService")
            .tags(Map.of("a", "b"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const service = new azure_native.servicefabric.Service("service", {
    applicationName: "myApp",
    clusterName: "myCluster",
    location: "eastus",
    properties: {
        correlationScheme: [{
            scheme: "AlignedAffinity",
            serviceName: "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/resRg/providers/Microsoft.ServiceFabric/managedclusters/myCluster/applications/myApp/services/myService1",
        }],
        defaultMoveCost: "Medium",
        instanceCount: 5,
        minInstanceCount: 3,
        minInstancePercentage: 30,
        partitionDescription: {
            partitionScheme: "Singleton",
        },
        placementConstraints: "NodeType==frontend",
        scalingPolicies: [{
            scalingMechanism: {
                kind: "ScalePartitionInstanceCount",
                maxInstanceCount: 9,
                minInstanceCount: 3,
                scaleIncrement: 2,
            },
            scalingTrigger: {
                kind: "AveragePartitionLoadTrigger",
                lowerLoadThreshold: 2,
                metricName: "metricName",
                scaleInterval: "00:01:00",
                upperLoadThreshold: 8,
            },
        }],
        serviceDnsName: "myservicednsname.myApp",
        serviceKind: "Stateless",
        serviceLoadMetrics: [{
            defaultLoad: 3,
            name: "metric1",
            weight: "Low",
        }],
        servicePackageActivationMode: "SharedProcess",
        servicePlacementPolicies: [{
            type: "NonPartiallyPlaceService",
        }],
        serviceTypeName: "myServiceType",
    },
    resourceGroupName: "resRg",
    serviceName: "myService",
    tags: {
        a: "b",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service = azure_native.servicefabric.Service("service",
    application_name="myApp",
    cluster_name="myCluster",
    location="eastus",
    properties=azure_native.servicefabric.StatelessServicePropertiesArgs(
        correlation_scheme=[azure_native.servicefabric.ServiceCorrelationArgs(
            scheme="AlignedAffinity",
            service_name="/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/resRg/providers/Microsoft.ServiceFabric/managedclusters/myCluster/applications/myApp/services/myService1",
        )],
        default_move_cost="Medium",
        instance_count=5,
        min_instance_count=3,
        min_instance_percentage=30,
        partition_description=azure_native.servicefabric.SingletonPartitionSchemeArgs(
            partition_scheme="Singleton",
        ),
        placement_constraints="NodeType==frontend",
        scaling_policies=[azure_native.servicefabric.ScalingPolicyArgs(
            scaling_mechanism=azure_native.servicefabric.PartitionInstanceCountScaleMechanismArgs(
                kind="ScalePartitionInstanceCount",
                max_instance_count=9,
                min_instance_count=3,
                scale_increment=2,
            ),
            scaling_trigger=azure_native.servicefabric.AveragePartitionLoadScalingTriggerArgs(
                kind="AveragePartitionLoadTrigger",
                lower_load_threshold=2,
                metric_name="metricName",
                scale_interval="00:01:00",
                upper_load_threshold=8,
            ),
        )],
        service_dns_name="myservicednsname.myApp",
        service_kind="Stateless",
        service_load_metrics=[azure_native.servicefabric.ServiceLoadMetricArgs(
            default_load=3,
            name="metric1",
            weight="Low",
        )],
        service_package_activation_mode="SharedProcess",
        service_placement_policies=[azure_native.servicefabric.ServicePlacementNonPartiallyPlaceServicePolicyArgs(
            type="NonPartiallyPlaceService",
        )],
        service_type_name="myServiceType",
    ),
    resource_group_name="resRg",
    service_name="myService",
    tags={
        "a": "b",
    })

```

```yaml
resources:
  service:
    type: azure-native:servicefabric:Service
    properties:
      applicationName: myApp
      clusterName: myCluster
      location: eastus
      properties:
        correlationScheme:
          - scheme: AlignedAffinity
            serviceName: /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/resRg/providers/Microsoft.ServiceFabric/managedclusters/myCluster/applications/myApp/services/myService1
        defaultMoveCost: Medium
        instanceCount: 5
        minInstanceCount: 3
        minInstancePercentage: 30
        partitionDescription:
          partitionScheme: Singleton
        placementConstraints: NodeType==frontend
        scalingPolicies:
          - scalingMechanism:
              kind: ScalePartitionInstanceCount
              maxInstanceCount: 9
              minInstanceCount: 3
              scaleIncrement: 2
            scalingTrigger:
              kind: AveragePartitionLoadTrigger
              lowerLoadThreshold: 2
              metricName: metricName
              scaleInterval: 00:01:00
              upperLoadThreshold: 8
        serviceDnsName: myservicednsname.myApp
        serviceKind: Stateless
        serviceLoadMetrics:
          - defaultLoad: 3
            name: metric1
            weight: Low
        servicePackageActivationMode: SharedProcess
        servicePlacementPolicies:
          - type: NonPartiallyPlaceService
        serviceTypeName: myServiceType
      resourceGroupName: resRg
      serviceName: myService
      tags:
        a: b

```

{{% /example %}}
{{% example %}}
### Put a service with minimum parameters
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var service = new AzureNative.ServiceFabric.Service("service", new()
    {
        ApplicationName = "myApp",
        ClusterName = "myCluster",
        Location = "eastus",
        Properties = new AzureNative.ServiceFabric.Inputs.StatelessServicePropertiesArgs
        {
            InstanceCount = 1,
            PartitionDescription = new AzureNative.ServiceFabric.Inputs.SingletonPartitionSchemeArgs
            {
                PartitionScheme = "Singleton",
            },
            ServiceKind = "Stateless",
            ServiceTypeName = "myServiceType",
        },
        ResourceGroupName = "resRg",
        ServiceName = "myService",
    });

});


```

```go
package main

import (
	servicefabric "github.com/pulumi/pulumi-azure-native-sdk/servicefabric"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := servicefabric.NewService(ctx, "service", &servicefabric.ServiceArgs{
			ApplicationName: pulumi.String("myApp"),
			ClusterName:     pulumi.String("myCluster"),
			Location:        pulumi.String("eastus"),
			Properties: servicefabric.StatelessServiceProperties{
				InstanceCount: 1,
				PartitionDescription: servicefabric.SingletonPartitionScheme{
					PartitionScheme: "Singleton",
				},
				ServiceKind:     "Stateless",
				ServiceTypeName: "myServiceType",
			},
			ResourceGroupName: pulumi.String("resRg"),
			ServiceName:       pulumi.String("myService"),
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
import com.pulumi.azurenative.servicefabric.Service;
import com.pulumi.azurenative.servicefabric.ServiceArgs;
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
        var service = new Service("service", ServiceArgs.builder()        
            .applicationName("myApp")
            .clusterName("myCluster")
            .location("eastus")
            .properties(Map.ofEntries(
                Map.entry("instanceCount", 1),
                Map.entry("partitionDescription", Map.of("partitionScheme", "Singleton")),
                Map.entry("serviceKind", "Stateless"),
                Map.entry("serviceTypeName", "myServiceType")
            ))
            .resourceGroupName("resRg")
            .serviceName("myService")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const service = new azure_native.servicefabric.Service("service", {
    applicationName: "myApp",
    clusterName: "myCluster",
    location: "eastus",
    properties: {
        instanceCount: 1,
        partitionDescription: {
            partitionScheme: "Singleton",
        },
        serviceKind: "Stateless",
        serviceTypeName: "myServiceType",
    },
    resourceGroupName: "resRg",
    serviceName: "myService",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service = azure_native.servicefabric.Service("service",
    application_name="myApp",
    cluster_name="myCluster",
    location="eastus",
    properties=azure_native.servicefabric.StatelessServicePropertiesArgs(
        instance_count=1,
        partition_description=azure_native.servicefabric.SingletonPartitionSchemeArgs(
            partition_scheme="Singleton",
        ),
        service_kind="Stateless",
        service_type_name="myServiceType",
    ),
    resource_group_name="resRg",
    service_name="myService")

```

```yaml
resources:
  service:
    type: azure-native:servicefabric:Service
    properties:
      applicationName: myApp
      clusterName: myCluster
      location: eastus
      properties:
        instanceCount: 1
        partitionDescription:
          partitionScheme: Singleton
        serviceKind: Stateless
        serviceTypeName: myServiceType
      resourceGroupName: resRg
      serviceName: myService

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:servicefabric:Service myService /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/resRg/providers/Microsoft.ServiceFabric/managedclusters/myCluster/applications/myApp/services/myService 
```
