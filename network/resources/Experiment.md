Defines the properties of an Experiment
API Version: 2019-11-01.
Previous API Version: 2019-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates an Experiment
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var experiment = new AzureNative.Network.Experiment("experiment", new()
    {
        Description = "this is my first experiment!",
        EnabledState = "Enabled",
        EndpointA = new AzureNative.Network.Inputs.ExperimentEndpointArgs
        {
            Endpoint = "endpointA.net",
            Name = "endpoint A",
        },
        EndpointB = new AzureNative.Network.Inputs.ExperimentEndpointArgs
        {
            Endpoint = "endpointB.net",
            Name = "endpoint B",
        },
        ExperimentName = "MyExperiment",
        ProfileName = "MyProfile",
        ResourceGroupName = "MyResourceGroup",
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
		_, err := network.NewExperiment(ctx, "experiment", &network.ExperimentArgs{
			Description:  pulumi.String("this is my first experiment!"),
			EnabledState: pulumi.String("Enabled"),
			EndpointA: &network.ExperimentEndpointArgs{
				Endpoint: pulumi.String("endpointA.net"),
				Name:     pulumi.String("endpoint A"),
			},
			EndpointB: &network.ExperimentEndpointArgs{
				Endpoint: pulumi.String("endpointB.net"),
				Name:     pulumi.String("endpoint B"),
			},
			ExperimentName:    pulumi.String("MyExperiment"),
			ProfileName:       pulumi.String("MyProfile"),
			ResourceGroupName: pulumi.String("MyResourceGroup"),
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
import com.pulumi.azurenative.network.Experiment;
import com.pulumi.azurenative.network.ExperimentArgs;
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
        var experiment = new Experiment("experiment", ExperimentArgs.builder()        
            .description("this is my first experiment!")
            .enabledState("Enabled")
            .endpointA(Map.ofEntries(
                Map.entry("endpoint", "endpointA.net"),
                Map.entry("name", "endpoint A")
            ))
            .endpointB(Map.ofEntries(
                Map.entry("endpoint", "endpointB.net"),
                Map.entry("name", "endpoint B")
            ))
            .experimentName("MyExperiment")
            .profileName("MyProfile")
            .resourceGroupName("MyResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const experiment = new azure_native.network.Experiment("experiment", {
    description: "this is my first experiment!",
    enabledState: "Enabled",
    endpointA: {
        endpoint: "endpointA.net",
        name: "endpoint A",
    },
    endpointB: {
        endpoint: "endpointB.net",
        name: "endpoint B",
    },
    experimentName: "MyExperiment",
    profileName: "MyProfile",
    resourceGroupName: "MyResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

experiment = azure_native.network.Experiment("experiment",
    description="this is my first experiment!",
    enabled_state="Enabled",
    endpoint_a=azure_native.network.ExperimentEndpointArgs(
        endpoint="endpointA.net",
        name="endpoint A",
    ),
    endpoint_b=azure_native.network.ExperimentEndpointArgs(
        endpoint="endpointB.net",
        name="endpoint B",
    ),
    experiment_name="MyExperiment",
    profile_name="MyProfile",
    resource_group_name="MyResourceGroup")

```

```yaml
resources:
  experiment:
    type: azure-native:network:Experiment
    properties:
      description: this is my first experiment!
      enabledState: Enabled
      endpointA:
        endpoint: endpointA.net
        name: endpoint A
      endpointB:
        endpoint: endpointB.net
        name: endpoint B
      experimentName: MyExperiment
      profileName: MyProfile
      resourceGroupName: MyResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:Experiment MyExperiment /subscriptions/subid/resourceGroups/MyResourceGroup/providers/Microsoft.Network/NetworkExperimentProfiles/MyProfile/Experiments/MyExperiment 
```
