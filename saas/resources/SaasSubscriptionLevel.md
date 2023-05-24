SaaS REST API resource definition.
API Version: 2018-03-01-beta.
Previous API Version: 2018-03-01-beta. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create subscription level SaaS resource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var saasSubscriptionLevel = new AzureNative.SaaS.SaasSubscriptionLevel("saasSubscriptionLevel", new()
    {
        Location = "global",
        Name = "MyContosoSubscription",
        Properties = new AzureNative.SaaS.Inputs.SaasCreationPropertiesArgs
        {
            OfferId = "contosoOffer",
            PaymentChannelMetadata = 
            {
                { "AzureSubscriptionId", "155af98a-3205-47e7-883b-a2ab9db9f88d" },
            },
            PaymentChannelType = "SubscriptionDelegated",
            PublisherId = "microsoft-contoso",
            SaasResourceName = "MyContosoSubscription",
            SkuId = "free",
            TermId = "hjdtn7tfnxcy",
        },
        ResourceGroupName = "my-saas-rg",
        ResourceName = "MyContosoSubscription",
    });

});


```

```go
package main

import (
	saas "github.com/pulumi/pulumi-azure-native-sdk/saas"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := saas.NewSaasSubscriptionLevel(ctx, "saasSubscriptionLevel", &saas.SaasSubscriptionLevelArgs{
			Location: pulumi.String("global"),
			Name:     pulumi.String("MyContosoSubscription"),
			Properties: &saas.SaasCreationPropertiesArgs{
				OfferId: pulumi.String("contosoOffer"),
				PaymentChannelMetadata: pulumi.StringMap{
					"AzureSubscriptionId": pulumi.String("155af98a-3205-47e7-883b-a2ab9db9f88d"),
				},
				PaymentChannelType: pulumi.String("SubscriptionDelegated"),
				PublisherId:        pulumi.String("microsoft-contoso"),
				SaasResourceName:   pulumi.String("MyContosoSubscription"),
				SkuId:              pulumi.String("free"),
				TermId:             pulumi.String("hjdtn7tfnxcy"),
			},
			ResourceGroupName: pulumi.String("my-saas-rg"),
			ResourceName:      pulumi.String("MyContosoSubscription"),
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
import com.pulumi.azurenative.saas.SaasSubscriptionLevel;
import com.pulumi.azurenative.saas.SaasSubscriptionLevelArgs;
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
        var saasSubscriptionLevel = new SaasSubscriptionLevel("saasSubscriptionLevel", SaasSubscriptionLevelArgs.builder()        
            .location("global")
            .name("MyContosoSubscription")
            .properties(Map.ofEntries(
                Map.entry("offerId", "contosoOffer"),
                Map.entry("paymentChannelMetadata", Map.of("AzureSubscriptionId", "155af98a-3205-47e7-883b-a2ab9db9f88d")),
                Map.entry("paymentChannelType", "SubscriptionDelegated"),
                Map.entry("publisherId", "microsoft-contoso"),
                Map.entry("saasResourceName", "MyContosoSubscription"),
                Map.entry("skuId", "free"),
                Map.entry("termId", "hjdtn7tfnxcy")
            ))
            .resourceGroupName("my-saas-rg")
            .resourceName("MyContosoSubscription")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const saasSubscriptionLevel = new azure_native.saas.SaasSubscriptionLevel("saasSubscriptionLevel", {
    location: "global",
    name: "MyContosoSubscription",
    properties: {
        offerId: "contosoOffer",
        paymentChannelMetadata: {
            AzureSubscriptionId: "155af98a-3205-47e7-883b-a2ab9db9f88d",
        },
        paymentChannelType: "SubscriptionDelegated",
        publisherId: "microsoft-contoso",
        saasResourceName: "MyContosoSubscription",
        skuId: "free",
        termId: "hjdtn7tfnxcy",
    },
    resourceGroupName: "my-saas-rg",
    resourceName: "MyContosoSubscription",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

saas_subscription_level = azure_native.saas.SaasSubscriptionLevel("saasSubscriptionLevel",
    location="global",
    name="MyContosoSubscription",
    properties=azure_native.saas.SaasCreationPropertiesArgs(
        offer_id="contosoOffer",
        payment_channel_metadata={
            "AzureSubscriptionId": "155af98a-3205-47e7-883b-a2ab9db9f88d",
        },
        payment_channel_type="SubscriptionDelegated",
        publisher_id="microsoft-contoso",
        saas_resource_name="MyContosoSubscription",
        sku_id="free",
        term_id="hjdtn7tfnxcy",
    ),
    resource_group_name="my-saas-rg",
    resource_name_="MyContosoSubscription")

```

```yaml
resources:
  saasSubscriptionLevel:
    type: azure-native:saas:SaasSubscriptionLevel
    properties:
      location: global
      name: MyContosoSubscription
      properties:
        offerId: contosoOffer
        paymentChannelMetadata:
          AzureSubscriptionId: 155af98a-3205-47e7-883b-a2ab9db9f88d
        paymentChannelType: SubscriptionDelegated
        publisherId: microsoft-contoso
        saasResourceName: MyContosoSubscription
        skuId: free
        termId: hjdtn7tfnxcy
      resourceGroupName: my-saas-rg
      resourceName: MyContosoSubscription

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:saas:SaasSubscriptionLevel MyContosoSubscription /subscriptions/c825645b-e31b-9cf4-1cee-2aba9e58bc7c/resourceGroups/my-saas-rg/providers/Microsoft.SaaS/resources/MyContosoSubscription 
```
