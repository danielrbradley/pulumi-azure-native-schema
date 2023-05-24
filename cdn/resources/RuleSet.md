Friendly RuleSet name mapping to the any RuleSet or secret related information.
API Version: 2021-06-01.
Previous API Version: 2020-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### RuleSets_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var ruleSet = new AzureNative.Cdn.RuleSet("ruleSet", new()
    {
        ProfileName = "profile1",
        ResourceGroupName = "RG",
        RuleSetName = "ruleSet1",
    });

});


```

```go
package main

import (
	cdn "github.com/pulumi/pulumi-azure-native-sdk/cdn"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := cdn.NewRuleSet(ctx, "ruleSet", &cdn.RuleSetArgs{
			ProfileName:       pulumi.String("profile1"),
			ResourceGroupName: pulumi.String("RG"),
			RuleSetName:       pulumi.String("ruleSet1"),
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
import com.pulumi.azurenative.cdn.RuleSet;
import com.pulumi.azurenative.cdn.RuleSetArgs;
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
        var ruleSet = new RuleSet("ruleSet", RuleSetArgs.builder()        
            .profileName("profile1")
            .resourceGroupName("RG")
            .ruleSetName("ruleSet1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const ruleSet = new azure_native.cdn.RuleSet("ruleSet", {
    profileName: "profile1",
    resourceGroupName: "RG",
    ruleSetName: "ruleSet1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

rule_set = azure_native.cdn.RuleSet("ruleSet",
    profile_name="profile1",
    resource_group_name="RG",
    rule_set_name="ruleSet1")

```

```yaml
resources:
  ruleSet:
    type: azure-native:cdn:RuleSet
    properties:
      profileName: profile1
      resourceGroupName: RG
      ruleSetName: ruleSet1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:cdn:RuleSet ruleSet1 /subscriptions/subid/resourcegroups/RG/providers/Microsoft.Cdn/profiles/profile1/rulesets/ruleSet1 
```
