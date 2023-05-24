The status of the Canonical support plan.
API Version: 2018-03-01.
Previous API Version: 2018-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### SupportPlanTypes_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var supportPlanType = new AzureNative.Addons.SupportPlanType("supportPlanType", new()
    {
        PlanTypeName = "Standard",
        ProviderName = "Canonical",
    });

});


```

```go
package main

import (
	addons "github.com/pulumi/pulumi-azure-native-sdk/addons"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := addons.NewSupportPlanType(ctx, "supportPlanType", &addons.SupportPlanTypeArgs{
			PlanTypeName: pulumi.String("Standard"),
			ProviderName: pulumi.String("Canonical"),
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
import com.pulumi.azurenative.addons.SupportPlanType;
import com.pulumi.azurenative.addons.SupportPlanTypeArgs;
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
        var supportPlanType = new SupportPlanType("supportPlanType", SupportPlanTypeArgs.builder()        
            .planTypeName("Standard")
            .providerName("Canonical")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const supportPlanType = new azure_native.addons.SupportPlanType("supportPlanType", {
    planTypeName: "Standard",
    providerName: "Canonical",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

support_plan_type = azure_native.addons.SupportPlanType("supportPlanType",
    plan_type_name="Standard",
    provider_name="Canonical")

```

```yaml
resources:
  supportPlanType:
    type: azure-native:addons:SupportPlanType
    properties:
      planTypeName: Standard
      providerName: Canonical

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:addons:SupportPlanType Standard subscriptions/d18d258f-bdba-4de1-8b51-e79d6c181d5e/providers/Microsoft.Addons/supportProviders/canonical/supportPlanTypes/Standard 
```
