Upon creation, the additional services that are provided by the platform will be allocated and
represented in the status of this resource. All resources associated with this cloud services network will be part
of the same layer 2 (L2) isolation domain. At least one service network must be created but may be reused across many
virtual machines and/or Hybrid AKS clusters.
API Version: 2022-12-12-preview.
Previous API Version: 2022-12-12-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update cloud services network
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cloudServicesNetwork = new AzureNative.NetworkCloud.CloudServicesNetwork("cloudServicesNetwork", new()
    {
        AdditionalEgressEndpoints = new[]
        {
            new AzureNative.NetworkCloud.Inputs.EgressEndpointArgs
            {
                Category = "azure-resource-management",
                Endpoints = new[]
                {
                    new AzureNative.NetworkCloud.Inputs.EndpointDependencyArgs
                    {
                        DomainName = "https://storageaccountex.blob.core.windows.net",
                        Port = 443,
                    },
                },
            },
        },
        CloudServicesNetworkName = "cloudServicesNetworkName",
        EnableDefaultEgressEndpoints = "False",
        ExtendedLocation = new AzureNative.NetworkCloud.Inputs.ExtendedLocationArgs
        {
            Name = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName",
            Type = "CustomLocation",
        },
        Location = "location",
        ResourceGroupName = "resourceGroupName",
        Tags = 
        {
            { "key1", "myvalue1" },
            { "key2", "myvalue2" },
        },
    });

});


```

```go
package main

import (
	networkcloud "github.com/pulumi/pulumi-azure-native-sdk/networkcloud"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := networkcloud.NewCloudServicesNetwork(ctx, "cloudServicesNetwork", &networkcloud.CloudServicesNetworkArgs{
			AdditionalEgressEndpoints: []networkcloud.EgressEndpointArgs{
				{
					Category: pulumi.String("azure-resource-management"),
					Endpoints: networkcloud.EndpointDependencyArray{
						{
							DomainName: pulumi.String("https://storageaccountex.blob.core.windows.net"),
							Port:       pulumi.Float64(443),
						},
					},
				},
			},
			CloudServicesNetworkName:     pulumi.String("cloudServicesNetworkName"),
			EnableDefaultEgressEndpoints: pulumi.String("False"),
			ExtendedLocation: &networkcloud.ExtendedLocationArgs{
				Name: pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName"),
				Type: pulumi.String("CustomLocation"),
			},
			Location:          pulumi.String("location"),
			ResourceGroupName: pulumi.String("resourceGroupName"),
			Tags: pulumi.StringMap{
				"key1": pulumi.String("myvalue1"),
				"key2": pulumi.String("myvalue2"),
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
import com.pulumi.azurenative.networkcloud.CloudServicesNetwork;
import com.pulumi.azurenative.networkcloud.CloudServicesNetworkArgs;
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
        var cloudServicesNetwork = new CloudServicesNetwork("cloudServicesNetwork", CloudServicesNetworkArgs.builder()        
            .additionalEgressEndpoints(Map.ofEntries(
                Map.entry("category", "azure-resource-management"),
                Map.entry("endpoints", Map.ofEntries(
                    Map.entry("domainName", "https://storageaccountex.blob.core.windows.net"),
                    Map.entry("port", 443)
                ))
            ))
            .cloudServicesNetworkName("cloudServicesNetworkName")
            .enableDefaultEgressEndpoints("False")
            .extendedLocation(Map.ofEntries(
                Map.entry("name", "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName"),
                Map.entry("type", "CustomLocation")
            ))
            .location("location")
            .resourceGroupName("resourceGroupName")
            .tags(Map.ofEntries(
                Map.entry("key1", "myvalue1"),
                Map.entry("key2", "myvalue2")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cloudServicesNetwork = new azure_native.networkcloud.CloudServicesNetwork("cloudServicesNetwork", {
    additionalEgressEndpoints: [{
        category: "azure-resource-management",
        endpoints: [{
            domainName: "https://storageaccountex.blob.core.windows.net",
            port: 443,
        }],
    }],
    cloudServicesNetworkName: "cloudServicesNetworkName",
    enableDefaultEgressEndpoints: "False",
    extendedLocation: {
        name: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName",
        type: "CustomLocation",
    },
    location: "location",
    resourceGroupName: "resourceGroupName",
    tags: {
        key1: "myvalue1",
        key2: "myvalue2",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cloud_services_network = azure_native.networkcloud.CloudServicesNetwork("cloudServicesNetwork",
    additional_egress_endpoints=[{
        "category": "azure-resource-management",
        "endpoints": [azure_native.networkcloud.EndpointDependencyArgs(
            domain_name="https://storageaccountex.blob.core.windows.net",
            port=443,
        )],
    }],
    cloud_services_network_name="cloudServicesNetworkName",
    enable_default_egress_endpoints="False",
    extended_location=azure_native.networkcloud.ExtendedLocationArgs(
        name="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName",
        type="CustomLocation",
    ),
    location="location",
    resource_group_name="resourceGroupName",
    tags={
        "key1": "myvalue1",
        "key2": "myvalue2",
    })

```

```yaml
resources:
  cloudServicesNetwork:
    type: azure-native:networkcloud:CloudServicesNetwork
    properties:
      additionalEgressEndpoints:
        - category: azure-resource-management
          endpoints:
            - domainName: https://storageaccountex.blob.core.windows.net
              port: 443
      cloudServicesNetworkName: cloudServicesNetworkName
      enableDefaultEgressEndpoints: False
      extendedLocation:
        name: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName
        type: CustomLocation
      location: location
      resourceGroupName: resourceGroupName
      tags:
        key1: myvalue1
        key2: myvalue2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:networkcloud:CloudServicesNetwork cloudServicesNetworkName /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/cloudServicesNetworks/cloudServicesNetworkName 
```
