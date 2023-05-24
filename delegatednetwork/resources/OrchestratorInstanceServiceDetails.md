Represents an instance of a orchestrator.
API Version: 2021-03-15.
Previous API Version: 2021-03-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create orchestrator instance
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var orchestratorInstanceServiceDetails = new AzureNative.DelegatedNetwork.OrchestratorInstanceServiceDetails("orchestratorInstanceServiceDetails", new()
    {
        ApiServerEndpoint = "https://testk8s.cloudapp.net",
        ClusterRootCA = "ddsadsad344mfdsfdl",
        ControllerDetails = new AzureNative.DelegatedNetwork.Inputs.ControllerDetailsArgs
        {
            Id = "/subscriptions/613192d7-503f-477a-9cfe-4efc3ee2bd60/resourceGroups/TestRG/providers/Microsoft.DelegatedNetwork/controller/testcontroller",
        },
        Identity = new AzureNative.DelegatedNetwork.Inputs.OrchestratorIdentityArgs
        {
            Type = AzureNative.DelegatedNetwork.ResourceIdentityType.SystemAssigned,
        },
        Kind = "Kubernetes",
        Location = "West US",
        OrchestratorAppId = "546192d7-503f-477a-9cfe-4efc3ee2b6e1",
        OrchestratorTenantId = "da6192d7-503f-477a-9cfe-4efc3ee2b6c3",
        PrivateLinkResourceId = "/subscriptions/613192d7-503f-477a-9cfe-4efc3ee2bd60/resourceGroups/TestRG/providers/Microsoft.Network/privateLinkServices/plresource1",
        ResourceGroupName = "TestRG",
        ResourceName = "testk8s1",
    });

});


```

```go
package main

import (
	delegatednetwork "github.com/pulumi/pulumi-azure-native-sdk/delegatednetwork"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := delegatednetwork.NewOrchestratorInstanceServiceDetails(ctx, "orchestratorInstanceServiceDetails", &delegatednetwork.OrchestratorInstanceServiceDetailsArgs{
			ApiServerEndpoint: pulumi.String("https://testk8s.cloudapp.net"),
			ClusterRootCA:     pulumi.String("ddsadsad344mfdsfdl"),
			ControllerDetails: &delegatednetwork.ControllerDetailsTypeArgs{
				Id: pulumi.String("/subscriptions/613192d7-503f-477a-9cfe-4efc3ee2bd60/resourceGroups/TestRG/providers/Microsoft.DelegatedNetwork/controller/testcontroller"),
			},
			Identity: &delegatednetwork.OrchestratorIdentityArgs{
				Type: delegatednetwork.ResourceIdentityTypeSystemAssigned,
			},
			Kind:                  pulumi.String("Kubernetes"),
			Location:              pulumi.String("West US"),
			OrchestratorAppId:     pulumi.String("546192d7-503f-477a-9cfe-4efc3ee2b6e1"),
			OrchestratorTenantId:  pulumi.String("da6192d7-503f-477a-9cfe-4efc3ee2b6c3"),
			PrivateLinkResourceId: pulumi.String("/subscriptions/613192d7-503f-477a-9cfe-4efc3ee2bd60/resourceGroups/TestRG/providers/Microsoft.Network/privateLinkServices/plresource1"),
			ResourceGroupName:     pulumi.String("TestRG"),
			ResourceName:          pulumi.String("testk8s1"),
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
import com.pulumi.azurenative.delegatednetwork.OrchestratorInstanceServiceDetails;
import com.pulumi.azurenative.delegatednetwork.OrchestratorInstanceServiceDetailsArgs;
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
        var orchestratorInstanceServiceDetails = new OrchestratorInstanceServiceDetails("orchestratorInstanceServiceDetails", OrchestratorInstanceServiceDetailsArgs.builder()        
            .apiServerEndpoint("https://testk8s.cloudapp.net")
            .clusterRootCA("ddsadsad344mfdsfdl")
            .controllerDetails(Map.of("id", "/subscriptions/613192d7-503f-477a-9cfe-4efc3ee2bd60/resourceGroups/TestRG/providers/Microsoft.DelegatedNetwork/controller/testcontroller"))
            .identity(Map.of("type", "SystemAssigned"))
            .kind("Kubernetes")
            .location("West US")
            .orchestratorAppId("546192d7-503f-477a-9cfe-4efc3ee2b6e1")
            .orchestratorTenantId("da6192d7-503f-477a-9cfe-4efc3ee2b6c3")
            .privateLinkResourceId("/subscriptions/613192d7-503f-477a-9cfe-4efc3ee2bd60/resourceGroups/TestRG/providers/Microsoft.Network/privateLinkServices/plresource1")
            .resourceGroupName("TestRG")
            .resourceName("testk8s1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const orchestratorInstanceServiceDetails = new azure_native.delegatednetwork.OrchestratorInstanceServiceDetails("orchestratorInstanceServiceDetails", {
    apiServerEndpoint: "https://testk8s.cloudapp.net",
    clusterRootCA: "ddsadsad344mfdsfdl",
    controllerDetails: {
        id: "/subscriptions/613192d7-503f-477a-9cfe-4efc3ee2bd60/resourceGroups/TestRG/providers/Microsoft.DelegatedNetwork/controller/testcontroller",
    },
    identity: {
        type: azure_native.delegatednetwork.ResourceIdentityType.SystemAssigned,
    },
    kind: "Kubernetes",
    location: "West US",
    orchestratorAppId: "546192d7-503f-477a-9cfe-4efc3ee2b6e1",
    orchestratorTenantId: "da6192d7-503f-477a-9cfe-4efc3ee2b6c3",
    privateLinkResourceId: "/subscriptions/613192d7-503f-477a-9cfe-4efc3ee2bd60/resourceGroups/TestRG/providers/Microsoft.Network/privateLinkServices/plresource1",
    resourceGroupName: "TestRG",
    resourceName: "testk8s1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

orchestrator_instance_service_details = azure_native.delegatednetwork.OrchestratorInstanceServiceDetails("orchestratorInstanceServiceDetails",
    api_server_endpoint="https://testk8s.cloudapp.net",
    cluster_root_ca="ddsadsad344mfdsfdl",
    controller_details=azure_native.delegatednetwork.ControllerDetailsArgs(
        id="/subscriptions/613192d7-503f-477a-9cfe-4efc3ee2bd60/resourceGroups/TestRG/providers/Microsoft.DelegatedNetwork/controller/testcontroller",
    ),
    identity=azure_native.delegatednetwork.OrchestratorIdentityArgs(
        type=azure_native.delegatednetwork.ResourceIdentityType.SYSTEM_ASSIGNED,
    ),
    kind="Kubernetes",
    location="West US",
    orchestrator_app_id="546192d7-503f-477a-9cfe-4efc3ee2b6e1",
    orchestrator_tenant_id="da6192d7-503f-477a-9cfe-4efc3ee2b6c3",
    private_link_resource_id="/subscriptions/613192d7-503f-477a-9cfe-4efc3ee2bd60/resourceGroups/TestRG/providers/Microsoft.Network/privateLinkServices/plresource1",
    resource_group_name="TestRG",
    resource_name_="testk8s1")

```

```yaml
resources:
  orchestratorInstanceServiceDetails:
    type: azure-native:delegatednetwork:OrchestratorInstanceServiceDetails
    properties:
      apiServerEndpoint: https://testk8s.cloudapp.net
      clusterRootCA: ddsadsad344mfdsfdl
      controllerDetails:
        id: /subscriptions/613192d7-503f-477a-9cfe-4efc3ee2bd60/resourceGroups/TestRG/providers/Microsoft.DelegatedNetwork/controller/testcontroller
      identity:
        type: SystemAssigned
      kind: Kubernetes
      location: West US
      orchestratorAppId: 546192d7-503f-477a-9cfe-4efc3ee2b6e1
      orchestratorTenantId: da6192d7-503f-477a-9cfe-4efc3ee2b6c3
      privateLinkResourceId: /subscriptions/613192d7-503f-477a-9cfe-4efc3ee2bd60/resourceGroups/TestRG/providers/Microsoft.Network/privateLinkServices/plresource1
      resourceGroupName: TestRG
      resourceName: testk8s1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:delegatednetwork:OrchestratorInstanceServiceDetails testk8s1 /subscriptions/613192d7-503f-477a-9cfe-4efc3ee2bd60/resourceGroups/TestRG/providers/Microsoft.DelegatedNetwork/orchestrators/testk8s1 
```
