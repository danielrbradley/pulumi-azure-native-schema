Custom Locations definition.
API Version: 2021-08-15.
Previous API Version: 2021-03-15-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create/Update Custom Location
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var customLocation = new AzureNative.ExtendedLocation.CustomLocation("customLocation", new()
    {
        Authentication = new AzureNative.ExtendedLocation.Inputs.CustomLocationPropertiesAuthenticationArgs
        {
            Type = "KubeConfig",
            Value = "<base64 KubeConfig>",
        },
        ClusterExtensionIds = new[]
        {
            "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Kubernetes/connectedCluster/someCluster/Microsoft.KubernetesConfiguration/clusterExtensions/fooExtension",
        },
        DisplayName = "customLocationLocation01",
        HostResourceId = "/subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/testresourcegroup/providers/Microsoft.ContainerService/managedClusters/cluster01",
        Identity = new AzureNative.ExtendedLocation.Inputs.IdentityArgs
        {
            Type = "SystemAssigned",
        },
        Location = "West US",
        Namespace = "namespace01",
        ResourceGroupName = "testresourcegroup",
        ResourceName = "customLocation01",
    });

});


```

```go
package main

import (
	extendedlocation "github.com/pulumi/pulumi-azure-native-sdk/extendedlocation"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := extendedlocation.NewCustomLocation(ctx, "customLocation", &extendedlocation.CustomLocationArgs{
			Authentication: &extendedlocation.CustomLocationPropertiesAuthenticationArgs{
				Type:  pulumi.String("KubeConfig"),
				Value: pulumi.String("<base64 KubeConfig>"),
			},
			ClusterExtensionIds: pulumi.StringArray{
				pulumi.String("/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Kubernetes/connectedCluster/someCluster/Microsoft.KubernetesConfiguration/clusterExtensions/fooExtension"),
			},
			DisplayName:    pulumi.String("customLocationLocation01"),
			HostResourceId: pulumi.String("/subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/testresourcegroup/providers/Microsoft.ContainerService/managedClusters/cluster01"),
			Identity: &extendedlocation.IdentityArgs{
				Type: pulumi.String("SystemAssigned"),
			},
			Location:          pulumi.String("West US"),
			Namespace:         pulumi.String("namespace01"),
			ResourceGroupName: pulumi.String("testresourcegroup"),
			ResourceName:      pulumi.String("customLocation01"),
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
import com.pulumi.azurenative.extendedlocation.CustomLocation;
import com.pulumi.azurenative.extendedlocation.CustomLocationArgs;
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
        var customLocation = new CustomLocation("customLocation", CustomLocationArgs.builder()        
            .authentication(Map.ofEntries(
                Map.entry("type", "KubeConfig"),
                Map.entry("value", "<base64 KubeConfig>")
            ))
            .clusterExtensionIds("/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Kubernetes/connectedCluster/someCluster/Microsoft.KubernetesConfiguration/clusterExtensions/fooExtension")
            .displayName("customLocationLocation01")
            .hostResourceId("/subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/testresourcegroup/providers/Microsoft.ContainerService/managedClusters/cluster01")
            .identity(Map.of("type", "SystemAssigned"))
            .location("West US")
            .namespace("namespace01")
            .resourceGroupName("testresourcegroup")
            .resourceName("customLocation01")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const customLocation = new azure_native.extendedlocation.CustomLocation("customLocation", {
    authentication: {
        type: "KubeConfig",
        value: "<base64 KubeConfig>",
    },
    clusterExtensionIds: ["/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Kubernetes/connectedCluster/someCluster/Microsoft.KubernetesConfiguration/clusterExtensions/fooExtension"],
    displayName: "customLocationLocation01",
    hostResourceId: "/subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/testresourcegroup/providers/Microsoft.ContainerService/managedClusters/cluster01",
    identity: {
        type: "SystemAssigned",
    },
    location: "West US",
    namespace: "namespace01",
    resourceGroupName: "testresourcegroup",
    resourceName: "customLocation01",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

custom_location = azure_native.extendedlocation.CustomLocation("customLocation",
    authentication=azure_native.extendedlocation.CustomLocationPropertiesAuthenticationArgs(
        type="KubeConfig",
        value="<base64 KubeConfig>",
    ),
    cluster_extension_ids=["/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Kubernetes/connectedCluster/someCluster/Microsoft.KubernetesConfiguration/clusterExtensions/fooExtension"],
    display_name="customLocationLocation01",
    host_resource_id="/subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/testresourcegroup/providers/Microsoft.ContainerService/managedClusters/cluster01",
    identity=azure_native.extendedlocation.IdentityArgs(
        type="SystemAssigned",
    ),
    location="West US",
    namespace="namespace01",
    resource_group_name="testresourcegroup",
    resource_name_="customLocation01")

```

```yaml
resources:
  customLocation:
    type: azure-native:extendedlocation:CustomLocation
    properties:
      authentication:
        type: KubeConfig
        value: <base64 KubeConfig>
      clusterExtensionIds:
        - /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Kubernetes/connectedCluster/someCluster/Microsoft.KubernetesConfiguration/clusterExtensions/fooExtension
      displayName: customLocationLocation01
      hostResourceId: /subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/testresourcegroup/providers/Microsoft.ContainerService/managedClusters/cluster01
      identity:
        type: SystemAssigned
      location: West US
      namespace: namespace01
      resourceGroupName: testresourcegroup
      resourceName: customLocation01

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:extendedlocation:CustomLocation customLocation01 /subscriptions/11111111-2222-3333-4444-555555555555/resourceGroups/testrg/providers/Microsoft.ExtendedLocation/customLocations/customLocation01 
```
