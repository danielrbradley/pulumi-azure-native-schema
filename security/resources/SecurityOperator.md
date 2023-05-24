Security operator under a given subscription and pricing
API Version: 2023-01-01-preview.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a security operator on the given scope
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var securityOperator = new AzureNative.Security.SecurityOperator("securityOperator", new()
    {
        PricingName = "CloudPosture",
        SecurityOperatorName = "DefenderCSPMSecurityOperator",
    });

});


```

```go
package main

import (
	security "github.com/pulumi/pulumi-azure-native-sdk/security"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := security.NewSecurityOperator(ctx, "securityOperator", &security.SecurityOperatorArgs{
			PricingName:          pulumi.String("CloudPosture"),
			SecurityOperatorName: pulumi.String("DefenderCSPMSecurityOperator"),
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
import com.pulumi.azurenative.security.SecurityOperator;
import com.pulumi.azurenative.security.SecurityOperatorArgs;
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
        var securityOperator = new SecurityOperator("securityOperator", SecurityOperatorArgs.builder()        
            .pricingName("CloudPosture")
            .securityOperatorName("DefenderCSPMSecurityOperator")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const securityOperator = new azure_native.security.SecurityOperator("securityOperator", {
    pricingName: "CloudPosture",
    securityOperatorName: "DefenderCSPMSecurityOperator",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

security_operator = azure_native.security.SecurityOperator("securityOperator",
    pricing_name="CloudPosture",
    security_operator_name="DefenderCSPMSecurityOperator")

```

```yaml
resources:
  securityOperator:
    type: azure-native:security:SecurityOperator
    properties:
      pricingName: CloudPosture
      securityOperatorName: DefenderCSPMSecurityOperator

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:security:SecurityOperator DefenderCSPMSecurityOperator /subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/providers/Microsoft.Security/pricings/CloudPosture/securityOperators/DefenderCSPMSecurityOperator 
```
