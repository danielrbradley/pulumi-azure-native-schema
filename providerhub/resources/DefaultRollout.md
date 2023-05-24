Default rollout definition.
API Version: 2020-11-20.
Previous API Version: 2020-11-20. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### DefaultRollouts_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var defaultRollout = new AzureNative.ProviderHub.DefaultRollout("defaultRollout", new()
    {
        Properties = new AzureNative.ProviderHub.Inputs.DefaultRolloutPropertiesArgs
        {
            Specification = new AzureNative.ProviderHub.Inputs.DefaultRolloutPropertiesSpecificationArgs
            {
                Canary = new AzureNative.ProviderHub.Inputs.DefaultRolloutSpecificationCanaryArgs
                {
                    SkipRegions = new[]
                    {
                        "eastus2euap",
                    },
                },
                RestOfTheWorldGroupTwo = new AzureNative.ProviderHub.Inputs.DefaultRolloutSpecificationRestOfTheWorldGroupTwoArgs
                {
                    WaitDuration = "PT4H",
                },
            },
        },
        ProviderNamespace = "Microsoft.Contoso",
        RolloutName = "2020week10",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.providerhub.DefaultRollout;
import com.pulumi.azurenative.providerhub.DefaultRolloutArgs;
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
        var defaultRollout = new DefaultRollout("defaultRollout", DefaultRolloutArgs.builder()        
            .properties(Map.of("specification", Map.ofEntries(
                Map.entry("canary", Map.of("skipRegions", "eastus2euap")),
                Map.entry("restOfTheWorldGroupTwo", Map.of("waitDuration", "PT4H"))
            )))
            .providerNamespace("Microsoft.Contoso")
            .rolloutName("2020week10")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const defaultRollout = new azure_native.providerhub.DefaultRollout("defaultRollout", {
    properties: {
        specification: {
            canary: {
                skipRegions: ["eastus2euap"],
            },
            restOfTheWorldGroupTwo: {
                waitDuration: "PT4H",
            },
        },
    },
    providerNamespace: "Microsoft.Contoso",
    rolloutName: "2020week10",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

default_rollout = azure_native.providerhub.DefaultRollout("defaultRollout",
    properties=azure_native.providerhub.DefaultRolloutResponsePropertiesArgs(
        specification={
            "canary": azure_native.providerhub.DefaultRolloutSpecificationCanaryArgs(
                skip_regions=["eastus2euap"],
            ),
            "restOfTheWorldGroupTwo": azure_native.providerhub.DefaultRolloutSpecificationRestOfTheWorldGroupTwoArgs(
                wait_duration="PT4H",
            ),
        },
    ),
    provider_namespace="Microsoft.Contoso",
    rollout_name="2020week10")

```

```yaml
resources:
  defaultRollout:
    type: azure-native:providerhub:DefaultRollout
    properties:
      properties:
        specification:
          canary:
            skipRegions:
              - eastus2euap
          restOfTheWorldGroupTwo:
            waitDuration: PT4H
      providerNamespace: Microsoft.Contoso
      rolloutName: 2020week10

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:providerhub:DefaultRollout Microsoft.Contoso/2020week10 /subscriptions/ab7a8701-f7ef-471a-a2f4-d0ebbf494f77providers/Microsoft.ProviderHub/providerRegistrations/Microsoft.Contoso/defaultRollouts/2020week10 
```
