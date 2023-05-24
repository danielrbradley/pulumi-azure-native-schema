Response on GET of a hybrid use benefit
API Version: 2019-12-01.
Previous API Version: 2019-06-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### HybridUseBenefit
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var hybridUseBenefit = new AzureNative.SoftwarePlan.HybridUseBenefit("hybridUseBenefit", new()
    {
        PlanId = "94f46eda-45f8-493a-8425-251921463a89",
        Scope = "subscriptions/{sub-id}/resourceGroups/{rg-name}/providers/Microsoft.Compute/HostGroups/{host-group-name}/hosts/{host-name}",
        Sku = new AzureNative.SoftwarePlan.Inputs.SkuArgs
        {
            Name = "SQL_Server_Perpetual",
        },
    });

});


```

```go
package main

import (
	softwareplan "github.com/pulumi/pulumi-azure-native-sdk/softwareplan"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := softwareplan.NewHybridUseBenefit(ctx, "hybridUseBenefit", &softwareplan.HybridUseBenefitArgs{
			PlanId: pulumi.String("94f46eda-45f8-493a-8425-251921463a89"),
			Scope:  pulumi.String("subscriptions/{sub-id}/resourceGroups/{rg-name}/providers/Microsoft.Compute/HostGroups/{host-group-name}/hosts/{host-name}"),
			Sku: &softwareplan.SkuArgs{
				Name: pulumi.String("SQL_Server_Perpetual"),
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
import com.pulumi.azurenative.softwareplan.HybridUseBenefit;
import com.pulumi.azurenative.softwareplan.HybridUseBenefitArgs;
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
        var hybridUseBenefit = new HybridUseBenefit("hybridUseBenefit", HybridUseBenefitArgs.builder()        
            .planId("94f46eda-45f8-493a-8425-251921463a89")
            .scope("subscriptions/{sub-id}/resourceGroups/{rg-name}/providers/Microsoft.Compute/HostGroups/{host-group-name}/hosts/{host-name}")
            .sku(Map.of("name", "SQL_Server_Perpetual"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const hybridUseBenefit = new azure_native.softwareplan.HybridUseBenefit("hybridUseBenefit", {
    planId: "94f46eda-45f8-493a-8425-251921463a89",
    scope: "subscriptions/{sub-id}/resourceGroups/{rg-name}/providers/Microsoft.Compute/HostGroups/{host-group-name}/hosts/{host-name}",
    sku: {
        name: "SQL_Server_Perpetual",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

hybrid_use_benefit = azure_native.softwareplan.HybridUseBenefit("hybridUseBenefit",
    plan_id="94f46eda-45f8-493a-8425-251921463a89",
    scope="subscriptions/{sub-id}/resourceGroups/{rg-name}/providers/Microsoft.Compute/HostGroups/{host-group-name}/hosts/{host-name}",
    sku=azure_native.softwareplan.SkuArgs(
        name="SQL_Server_Perpetual",
    ))

```

```yaml
resources:
  hybridUseBenefit:
    type: azure-native:softwareplan:HybridUseBenefit
    properties:
      planId: 94f46eda-45f8-493a-8425-251921463a89
      scope: subscriptions/{sub-id}/resourceGroups/{rg-name}/providers/Microsoft.Compute/HostGroups/{host-group-name}/hosts/{host-name}
      sku:
        name: SQL_Server_Perpetual

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:softwareplan:HybridUseBenefit SQL_{hostGroupName}_{hostName} /subscriptions/{sub-id}/resourceGroups/{rg-name}/providers/Microsoft.Compute/HostGroups/{host-group-name}/hosts/{host-name}/providers/Microsoft.SoftwarePlan/hybridUseBenefits/SQL_{hostGroupName}_{hostName} 
```
