
API Version: 2020-11-20.
Previous API Version: 2020-11-20. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Skus_CreateOrUpdateNestedResourceTypeSecond
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var skusNestedResourceTypeSecond = new AzureNative.ProviderHub.SkusNestedResourceTypeSecond("skusNestedResourceTypeSecond", new()
    {
        NestedResourceTypeFirst = "nestedResourceTypeFirst",
        NestedResourceTypeSecond = "nestedResourceTypeSecond",
        Properties = new AzureNative.ProviderHub.Inputs.SkuResourcePropertiesArgs
        {
            SkuSettings = new[]
            {
                new AzureNative.ProviderHub.Inputs.SkuSettingArgs
                {
                    Kind = "Standard",
                    Name = "freeSku",
                    Tier = "Tier1",
                },
                new AzureNative.ProviderHub.Inputs.SkuSettingArgs
                {
                    Costs = new[]
                    {
                        new AzureNative.ProviderHub.Inputs.SkuCostArgs
                        {
                            MeterId = "xxx",
                        },
                    },
                    Kind = "Premium",
                    Name = "premiumSku",
                    Tier = "Tier2",
                },
            },
        },
        ProviderNamespace = "Microsoft.Contoso",
        ResourceType = "testResourceType",
        Sku = "testSku",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.providerhub.SkusNestedResourceTypeSecond;
import com.pulumi.azurenative.providerhub.SkusNestedResourceTypeSecondArgs;
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
        var skusNestedResourceTypeSecond = new SkusNestedResourceTypeSecond("skusNestedResourceTypeSecond", SkusNestedResourceTypeSecondArgs.builder()        
            .nestedResourceTypeFirst("nestedResourceTypeFirst")
            .nestedResourceTypeSecond("nestedResourceTypeSecond")
            .properties(Map.of("skuSettings",             
                Map.ofEntries(
                    Map.entry("kind", "Standard"),
                    Map.entry("name", "freeSku"),
                    Map.entry("tier", "Tier1")
                ),
                Map.ofEntries(
                    Map.entry("costs", Map.of("meterId", "xxx")),
                    Map.entry("kind", "Premium"),
                    Map.entry("name", "premiumSku"),
                    Map.entry("tier", "Tier2")
                )))
            .providerNamespace("Microsoft.Contoso")
            .resourceType("testResourceType")
            .sku("testSku")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const skusNestedResourceTypeSecond = new azure_native.providerhub.SkusNestedResourceTypeSecond("skusNestedResourceTypeSecond", {
    nestedResourceTypeFirst: "nestedResourceTypeFirst",
    nestedResourceTypeSecond: "nestedResourceTypeSecond",
    properties: {
        skuSettings: [
            {
                kind: "Standard",
                name: "freeSku",
                tier: "Tier1",
            },
            {
                costs: [{
                    meterId: "xxx",
                }],
                kind: "Premium",
                name: "premiumSku",
                tier: "Tier2",
            },
        ],
    },
    providerNamespace: "Microsoft.Contoso",
    resourceType: "testResourceType",
    sku: "testSku",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

skus_nested_resource_type_second = azure_native.providerhub.SkusNestedResourceTypeSecond("skusNestedResourceTypeSecond",
    nested_resource_type_first="nestedResourceTypeFirst",
    nested_resource_type_second="nestedResourceTypeSecond",
    properties=azure_native.providerhub.SkuResourceResponsePropertiesArgs(
        sku_settings=[
            azure_native.providerhub.SkuSettingArgs(
                kind="Standard",
                name="freeSku",
                tier="Tier1",
            ),
            {
                "costs": [azure_native.providerhub.SkuCostArgs(
                    meter_id="xxx",
                )],
                "kind": "Premium",
                "name": "premiumSku",
                "tier": "Tier2",
            },
        ],
    ),
    provider_namespace="Microsoft.Contoso",
    resource_type="testResourceType",
    sku="testSku")

```

```yaml
resources:
  skusNestedResourceTypeSecond:
    type: azure-native:providerhub:SkusNestedResourceTypeSecond
    properties:
      nestedResourceTypeFirst: nestedResourceTypeFirst
      nestedResourceTypeSecond: nestedResourceTypeSecond
      properties:
        skuSettings:
          - kind: Standard
            name: freeSku
            tier: Tier1
          - costs:
              - meterId: xxx
            kind: Premium
            name: premiumSku
            tier: Tier2
      providerNamespace: Microsoft.Contoso
      resourceType: testResourceType
      sku: testSku

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:providerhub:SkusNestedResourceTypeSecond Microsoft.Contoso/ /subscriptions/ab7a8701-f7ef-471a-a2f4-d0ebbf494f77providers/Microsoft.ProviderHub/providerRegistrations/Microsoft.Contoso/ 
```
