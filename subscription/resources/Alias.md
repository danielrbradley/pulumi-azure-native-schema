Subscription Information with the alias.
API Version: 2021-10-01.
Previous API Version: 2020-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateAlias
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var @alias = new AzureNative.Subscription.Alias("alias", new()
    {
        AliasName = "aliasForNewSub",
        Properties = new AzureNative.Subscription.Inputs.PutAliasRequestPropertiesArgs
        {
            AdditionalProperties = new AzureNative.Subscription.Inputs.PutAliasRequestAdditionalPropertiesArgs
            {
                SubscriptionOwnerId = "f09b39eb-c496-482c-9ab9-afd799572f4c",
                SubscriptionTenantId = "66f6e4d6-07dc-4aea-94ea-e12d3026a3c8",
                Tags = 
                {
                    { "tag1", "Messi" },
                    { "tag2", "Ronaldo" },
                    { "tag3", "Lebron" },
                },
            },
            BillingScope = "/billingAccounts/af6231a7-7f8d-4fcc-a993-dd8466108d07:c663dac6-a9a5-405a-8938-cd903e12ab5b_2019_05_31/billingProfiles/QWDQ-QWHI-AUW-SJDO-DJH/invoiceSections/FEUF-EUHE-ISJ-SKDW-DJH",
            DisplayName = "Test Subscription",
            Workload = "Production",
        },
    });

});


```

```go
package main

import (
	subscription "github.com/pulumi/pulumi-azure-native-sdk/subscription"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := subscription.NewAlias(ctx, "alias", &subscription.AliasArgs{
			AliasName: pulumi.String("aliasForNewSub"),
			Properties: subscription.SubscriptionAliasResponsePropertiesResponse{
				AdditionalProperties: &subscription.PutAliasRequestAdditionalPropertiesArgs{
					SubscriptionOwnerId:  pulumi.String("f09b39eb-c496-482c-9ab9-afd799572f4c"),
					SubscriptionTenantId: pulumi.String("66f6e4d6-07dc-4aea-94ea-e12d3026a3c8"),
					Tags: pulumi.StringMap{
						"tag1": pulumi.String("Messi"),
						"tag2": pulumi.String("Ronaldo"),
						"tag3": pulumi.String("Lebron"),
					},
				},
				BillingScope: pulumi.String("/billingAccounts/af6231a7-7f8d-4fcc-a993-dd8466108d07:c663dac6-a9a5-405a-8938-cd903e12ab5b_2019_05_31/billingProfiles/QWDQ-QWHI-AUW-SJDO-DJH/invoiceSections/FEUF-EUHE-ISJ-SKDW-DJH"),
				DisplayName:  pulumi.String("Test Subscription"),
				Workload:     pulumi.String("Production"),
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
import com.pulumi.azurenative.subscription.Alias;
import com.pulumi.azurenative.subscription.AliasArgs;
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
        var alias = new Alias("alias", AliasArgs.builder()        
            .aliasName("aliasForNewSub")
            .properties(Map.ofEntries(
                Map.entry("additionalProperties", Map.ofEntries(
                    Map.entry("subscriptionOwnerId", "f09b39eb-c496-482c-9ab9-afd799572f4c"),
                    Map.entry("subscriptionTenantId", "66f6e4d6-07dc-4aea-94ea-e12d3026a3c8"),
                    Map.entry("tags", Map.ofEntries(
                        Map.entry("tag1", "Messi"),
                        Map.entry("tag2", "Ronaldo"),
                        Map.entry("tag3", "Lebron")
                    ))
                )),
                Map.entry("billingScope", "/billingAccounts/af6231a7-7f8d-4fcc-a993-dd8466108d07:c663dac6-a9a5-405a-8938-cd903e12ab5b_2019_05_31/billingProfiles/QWDQ-QWHI-AUW-SJDO-DJH/invoiceSections/FEUF-EUHE-ISJ-SKDW-DJH"),
                Map.entry("displayName", "Test Subscription"),
                Map.entry("workload", "Production")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const alias = new azure_native.subscription.Alias("alias", {
    aliasName: "aliasForNewSub",
    properties: {
        additionalProperties: {
            subscriptionOwnerId: "f09b39eb-c496-482c-9ab9-afd799572f4c",
            subscriptionTenantId: "66f6e4d6-07dc-4aea-94ea-e12d3026a3c8",
            tags: {
                tag1: "Messi",
                tag2: "Ronaldo",
                tag3: "Lebron",
            },
        },
        billingScope: "/billingAccounts/af6231a7-7f8d-4fcc-a993-dd8466108d07:c663dac6-a9a5-405a-8938-cd903e12ab5b_2019_05_31/billingProfiles/QWDQ-QWHI-AUW-SJDO-DJH/invoiceSections/FEUF-EUHE-ISJ-SKDW-DJH",
        displayName: "Test Subscription",
        workload: "Production",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

alias = azure_native.subscription.Alias("alias",
    alias_name="aliasForNewSub",
    properties=azure_native.subscription.SubscriptionAliasResponsePropertiesResponseArgs(
        additional_properties=azure_native.subscription.PutAliasRequestAdditionalPropertiesArgs(
            subscription_owner_id="f09b39eb-c496-482c-9ab9-afd799572f4c",
            subscription_tenant_id="66f6e4d6-07dc-4aea-94ea-e12d3026a3c8",
            tags={
                "tag1": "Messi",
                "tag2": "Ronaldo",
                "tag3": "Lebron",
            },
        ),
        billing_scope="/billingAccounts/af6231a7-7f8d-4fcc-a993-dd8466108d07:c663dac6-a9a5-405a-8938-cd903e12ab5b_2019_05_31/billingProfiles/QWDQ-QWHI-AUW-SJDO-DJH/invoiceSections/FEUF-EUHE-ISJ-SKDW-DJH",
        display_name="Test Subscription",
        workload="Production",
    ))

```

```yaml
resources:
  alias:
    type: azure-native:subscription:Alias
    properties:
      aliasName: aliasForNewSub
      properties:
        additionalProperties:
          subscriptionOwnerId: f09b39eb-c496-482c-9ab9-afd799572f4c
          subscriptionTenantId: 66f6e4d6-07dc-4aea-94ea-e12d3026a3c8
          tags:
            tag1: Messi
            tag2: Ronaldo
            tag3: Lebron
        billingScope: /billingAccounts/af6231a7-7f8d-4fcc-a993-dd8466108d07:c663dac6-a9a5-405a-8938-cd903e12ab5b_2019_05_31/billingProfiles/QWDQ-QWHI-AUW-SJDO-DJH/invoiceSections/FEUF-EUHE-ISJ-SKDW-DJH
        displayName: Test Subscription
        workload: Production

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:subscription:Alias string string 
```
