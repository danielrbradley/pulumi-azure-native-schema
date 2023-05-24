Defines an Network Experiment Profile and lists of Experiments
API Version: 2019-11-01.
Previous API Version: 2019-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates an NetworkExperiment Profile in a Resource Group
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var networkExperimentProfile = new AzureNative.Network.NetworkExperimentProfile("networkExperimentProfile", new()
    {
        EnabledState = "Enabled",
        Location = "WestUs",
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
		_, err := network.NewNetworkExperimentProfile(ctx, "networkExperimentProfile", &network.NetworkExperimentProfileArgs{
			EnabledState:      pulumi.String("Enabled"),
			Location:          pulumi.String("WestUs"),
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
import com.pulumi.azurenative.network.NetworkExperimentProfile;
import com.pulumi.azurenative.network.NetworkExperimentProfileArgs;
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
        var networkExperimentProfile = new NetworkExperimentProfile("networkExperimentProfile", NetworkExperimentProfileArgs.builder()        
            .enabledState("Enabled")
            .location("WestUs")
            .profileName("MyProfile")
            .resourceGroupName("MyResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const networkExperimentProfile = new azure_native.network.NetworkExperimentProfile("networkExperimentProfile", {
    enabledState: "Enabled",
    location: "WestUs",
    profileName: "MyProfile",
    resourceGroupName: "MyResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

network_experiment_profile = azure_native.network.NetworkExperimentProfile("networkExperimentProfile",
    enabled_state="Enabled",
    location="WestUs",
    profile_name="MyProfile",
    resource_group_name="MyResourceGroup")

```

```yaml
resources:
  networkExperimentProfile:
    type: azure-native:network:NetworkExperimentProfile
    properties:
      enabledState: Enabled
      location: WestUs
      profileName: MyProfile
      resourceGroupName: MyResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:NetworkExperimentProfile MyProfile /subscriptions/subid/resourceGroups/MyResourceGroup/providers/Microsoft.Network/NetworkExperimentProfiles/MyProfile 
```
