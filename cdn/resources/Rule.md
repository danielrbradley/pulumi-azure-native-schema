Friendly Rules name mapping to the any Rules or secret related information.
API Version: 2021-06-01.
Previous API Version: 2020-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Rules_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var rule = new AzureNative.Cdn.Rule("rule", new()
    {
        Actions = new[]
        {
            new AzureNative.Cdn.Inputs.DeliveryRuleResponseHeaderActionArgs
            {
                Name = "ModifyResponseHeader",
                Parameters = new AzureNative.Cdn.Inputs.HeaderActionParametersArgs
                {
                    HeaderAction = "Overwrite",
                    HeaderName = "X-CDN",
                    TypeName = "DeliveryRuleHeaderActionParameters",
                    Value = "MSFT",
                },
            },
        },
        Conditions = new[]
        {
            new AzureNative.Cdn.Inputs.DeliveryRuleRequestMethodConditionArgs
            {
                Name = "RequestMethod",
                Parameters = new AzureNative.Cdn.Inputs.RequestMethodMatchConditionParametersArgs
                {
                    MatchValues = new[]
                    {
                        "GET",
                    },
                    NegateCondition = false,
                    Operator = "Equal",
                    TypeName = "DeliveryRuleRequestMethodConditionParameters",
                },
            },
        },
        Order = 1,
        ProfileName = "profile1",
        ResourceGroupName = "RG",
        RuleName = "rule1",
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
		_, err := cdn.NewRule(ctx, "rule", &cdn.RuleArgs{
			Actions: pulumi.AnyArray{
				cdn.DeliveryRuleResponseHeaderAction{
					Name: "ModifyResponseHeader",
					Parameters: cdn.HeaderActionParameters{
						HeaderAction: "Overwrite",
						HeaderName:   "X-CDN",
						TypeName:     "DeliveryRuleHeaderActionParameters",
						Value:        "MSFT",
					},
				},
			},
			Conditions: pulumi.AnyArray{
				cdn.DeliveryRuleRequestMethodCondition{
					Name: "RequestMethod",
					Parameters: cdn.RequestMethodMatchConditionParameters{
						MatchValues: []string{
							"GET",
						},
						NegateCondition: false,
						Operator:        "Equal",
						TypeName:        "DeliveryRuleRequestMethodConditionParameters",
					},
				},
			},
			Order:             pulumi.Int(1),
			ProfileName:       pulumi.String("profile1"),
			ResourceGroupName: pulumi.String("RG"),
			RuleName:          pulumi.String("rule1"),
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
import com.pulumi.azurenative.cdn.Rule;
import com.pulumi.azurenative.cdn.RuleArgs;
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
        var rule = new Rule("rule", RuleArgs.builder()        
            .actions(Map.ofEntries(
                Map.entry("name", "ModifyResponseHeader"),
                Map.entry("parameters", Map.ofEntries(
                    Map.entry("headerAction", "Overwrite"),
                    Map.entry("headerName", "X-CDN"),
                    Map.entry("typeName", "DeliveryRuleHeaderActionParameters"),
                    Map.entry("value", "MSFT")
                ))
            ))
            .conditions(Map.ofEntries(
                Map.entry("name", "RequestMethod"),
                Map.entry("parameters", Map.ofEntries(
                    Map.entry("matchValues", "GET"),
                    Map.entry("negateCondition", false),
                    Map.entry("operator", "Equal"),
                    Map.entry("typeName", "DeliveryRuleRequestMethodConditionParameters")
                ))
            ))
            .order(1)
            .profileName("profile1")
            .resourceGroupName("RG")
            .ruleName("rule1")
            .ruleSetName("ruleSet1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const rule = new azure_native.cdn.Rule("rule", {
    actions: [{
        name: "ModifyResponseHeader",
        parameters: {
            headerAction: "Overwrite",
            headerName: "X-CDN",
            typeName: "DeliveryRuleHeaderActionParameters",
            value: "MSFT",
        },
    }],
    conditions: [{
        name: "RequestMethod",
        parameters: {
            matchValues: ["GET"],
            negateCondition: false,
            operator: "Equal",
            typeName: "DeliveryRuleRequestMethodConditionParameters",
        },
    }],
    order: 1,
    profileName: "profile1",
    resourceGroupName: "RG",
    ruleName: "rule1",
    ruleSetName: "ruleSet1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

rule = azure_native.cdn.Rule("rule",
    actions=[azure_native.cdn.DeliveryRuleResponseHeaderActionArgs(
        name="ModifyResponseHeader",
        parameters=azure_native.cdn.HeaderActionParametersArgs(
            header_action="Overwrite",
            header_name="X-CDN",
            type_name="DeliveryRuleHeaderActionParameters",
            value="MSFT",
        ),
    )],
    conditions=[azure_native.cdn.DeliveryRuleRequestMethodConditionArgs(
        name="RequestMethod",
        parameters=azure_native.cdn.RequestMethodMatchConditionParametersArgs(
            match_values=["GET"],
            negate_condition=False,
            operator="Equal",
            type_name="DeliveryRuleRequestMethodConditionParameters",
        ),
    )],
    order=1,
    profile_name="profile1",
    resource_group_name="RG",
    rule_name="rule1",
    rule_set_name="ruleSet1")

```

```yaml
resources:
  rule:
    type: azure-native:cdn:Rule
    properties:
      actions:
        - name: ModifyResponseHeader
          parameters:
            headerAction: Overwrite
            headerName: X-CDN
            typeName: DeliveryRuleHeaderActionParameters
            value: MSFT
      conditions:
        - name: RequestMethod
          parameters:
            matchValues:
              - GET
            negateCondition: false
            operator: Equal
            typeName: DeliveryRuleRequestMethodConditionParameters
      order: 1
      profileName: profile1
      resourceGroupName: RG
      ruleName: rule1
      ruleSetName: ruleSet1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:cdn:Rule rule1 /subscriptions/subid/resourcegroups/RG/providers/Microsoft.Cdn/profiles/profile1/rulesets/ruleSet1/rules/rule1 
```
