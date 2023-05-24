ProfessionalService REST API resource definition.
API Version: 2023-07-01-preview.
Previous API Version: 2023-07-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create subscription level ProfessionalService resource (indefinite term)
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var professionalServiceSubscriptionLevel = new AzureNative.ProfessionalService.ProfessionalServiceSubscriptionLevel("professionalServiceSubscriptionLevel", new()
    {
        Location = "global",
        Name = "MyContosoPS",
        Properties = new AzureNative.ProfessionalService.Inputs.ProfessionalServiceCreationPropertiesArgs
        {
            OfferId = "testprofservice",
            PublisherId = "microsoft-contoso",
            QuoteId = "quoteabc",
            SkuId = "ff051f4f-a6d9-4cbc-8d9a-2a41bd468abc",
        },
        ResourceGroupName = "my-ps-rg",
        ResourceName = "MyContosoPS",
    });

});


```

```go
package main

import (
	professionalservice "github.com/pulumi/pulumi-azure-native-sdk/professionalservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := professionalservice.NewProfessionalServiceSubscriptionLevel(ctx, "professionalServiceSubscriptionLevel", &professionalservice.ProfessionalServiceSubscriptionLevelArgs{
			Location: pulumi.String("global"),
			Name:     pulumi.String("MyContosoPS"),
			Properties: &professionalservice.ProfessionalServiceCreationPropertiesArgs{
				OfferId:     pulumi.String("testprofservice"),
				PublisherId: pulumi.String("microsoft-contoso"),
				QuoteId:     pulumi.String("quoteabc"),
				SkuId:       pulumi.String("ff051f4f-a6d9-4cbc-8d9a-2a41bd468abc"),
			},
			ResourceGroupName: pulumi.String("my-ps-rg"),
			ResourceName:      pulumi.String("MyContosoPS"),
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
import com.pulumi.azurenative.professionalservice.ProfessionalServiceSubscriptionLevel;
import com.pulumi.azurenative.professionalservice.ProfessionalServiceSubscriptionLevelArgs;
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
        var professionalServiceSubscriptionLevel = new ProfessionalServiceSubscriptionLevel("professionalServiceSubscriptionLevel", ProfessionalServiceSubscriptionLevelArgs.builder()        
            .location("global")
            .name("MyContosoPS")
            .properties(Map.ofEntries(
                Map.entry("offerId", "testprofservice"),
                Map.entry("publisherId", "microsoft-contoso"),
                Map.entry("quoteId", "quoteabc"),
                Map.entry("skuId", "ff051f4f-a6d9-4cbc-8d9a-2a41bd468abc")
            ))
            .resourceGroupName("my-ps-rg")
            .resourceName("MyContosoPS")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const professionalServiceSubscriptionLevel = new azure_native.professionalservice.ProfessionalServiceSubscriptionLevel("professionalServiceSubscriptionLevel", {
    location: "global",
    name: "MyContosoPS",
    properties: {
        offerId: "testprofservice",
        publisherId: "microsoft-contoso",
        quoteId: "quoteabc",
        skuId: "ff051f4f-a6d9-4cbc-8d9a-2a41bd468abc",
    },
    resourceGroupName: "my-ps-rg",
    resourceName: "MyContosoPS",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

professional_service_subscription_level = azure_native.professionalservice.ProfessionalServiceSubscriptionLevel("professionalServiceSubscriptionLevel",
    location="global",
    name="MyContosoPS",
    properties=azure_native.professionalservice.ProfessionalServiceCreationPropertiesArgs(
        offer_id="testprofservice",
        publisher_id="microsoft-contoso",
        quote_id="quoteabc",
        sku_id="ff051f4f-a6d9-4cbc-8d9a-2a41bd468abc",
    ),
    resource_group_name="my-ps-rg",
    resource_name_="MyContosoPS")

```

```yaml
resources:
  professionalServiceSubscriptionLevel:
    type: azure-native:professionalservice:ProfessionalServiceSubscriptionLevel
    properties:
      location: global
      name: MyContosoPS
      properties:
        offerId: testprofservice
        publisherId: microsoft-contoso
        quoteId: quoteabc
        skuId: ff051f4f-a6d9-4cbc-8d9a-2a41bd468abc
      resourceGroupName: my-ps-rg
      resourceName: MyContosoPS

```

{{% /example %}}
{{% example %}}
### Create subscription level ProfessionalService resource (with term)
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var professionalServiceSubscriptionLevel = new AzureNative.ProfessionalService.ProfessionalServiceSubscriptionLevel("professionalServiceSubscriptionLevel", new()
    {
        Location = "global",
        Name = "MyContosoPS",
        Properties = new AzureNative.ProfessionalService.Inputs.ProfessionalServiceCreationPropertiesArgs
        {
            BillingPeriod = "P1Y",
            OfferId = "testprofservice",
            PublisherId = "microsoft-contoso",
            QuoteId = "quoteabc",
            SkuId = "ff051f4f-a6d9-4cbc-8d9a-2a41bd468abc",
            TermUnit = "P3Y",
        },
        ResourceGroupName = "my-ps-rg",
        ResourceName = "MyContosoPS",
    });

});


```

```go
package main

import (
	professionalservice "github.com/pulumi/pulumi-azure-native-sdk/professionalservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := professionalservice.NewProfessionalServiceSubscriptionLevel(ctx, "professionalServiceSubscriptionLevel", &professionalservice.ProfessionalServiceSubscriptionLevelArgs{
			Location: pulumi.String("global"),
			Name:     pulumi.String("MyContosoPS"),
			Properties: &professionalservice.ProfessionalServiceCreationPropertiesArgs{
				BillingPeriod: pulumi.String("P1Y"),
				OfferId:       pulumi.String("testprofservice"),
				PublisherId:   pulumi.String("microsoft-contoso"),
				QuoteId:       pulumi.String("quoteabc"),
				SkuId:         pulumi.String("ff051f4f-a6d9-4cbc-8d9a-2a41bd468abc"),
				TermUnit:      pulumi.String("P3Y"),
			},
			ResourceGroupName: pulumi.String("my-ps-rg"),
			ResourceName:      pulumi.String("MyContosoPS"),
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
import com.pulumi.azurenative.professionalservice.ProfessionalServiceSubscriptionLevel;
import com.pulumi.azurenative.professionalservice.ProfessionalServiceSubscriptionLevelArgs;
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
        var professionalServiceSubscriptionLevel = new ProfessionalServiceSubscriptionLevel("professionalServiceSubscriptionLevel", ProfessionalServiceSubscriptionLevelArgs.builder()        
            .location("global")
            .name("MyContosoPS")
            .properties(Map.ofEntries(
                Map.entry("billingPeriod", "P1Y"),
                Map.entry("offerId", "testprofservice"),
                Map.entry("publisherId", "microsoft-contoso"),
                Map.entry("quoteId", "quoteabc"),
                Map.entry("skuId", "ff051f4f-a6d9-4cbc-8d9a-2a41bd468abc"),
                Map.entry("termUnit", "P3Y")
            ))
            .resourceGroupName("my-ps-rg")
            .resourceName("MyContosoPS")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const professionalServiceSubscriptionLevel = new azure_native.professionalservice.ProfessionalServiceSubscriptionLevel("professionalServiceSubscriptionLevel", {
    location: "global",
    name: "MyContosoPS",
    properties: {
        billingPeriod: "P1Y",
        offerId: "testprofservice",
        publisherId: "microsoft-contoso",
        quoteId: "quoteabc",
        skuId: "ff051f4f-a6d9-4cbc-8d9a-2a41bd468abc",
        termUnit: "P3Y",
    },
    resourceGroupName: "my-ps-rg",
    resourceName: "MyContosoPS",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

professional_service_subscription_level = azure_native.professionalservice.ProfessionalServiceSubscriptionLevel("professionalServiceSubscriptionLevel",
    location="global",
    name="MyContosoPS",
    properties=azure_native.professionalservice.ProfessionalServiceCreationPropertiesArgs(
        billing_period="P1Y",
        offer_id="testprofservice",
        publisher_id="microsoft-contoso",
        quote_id="quoteabc",
        sku_id="ff051f4f-a6d9-4cbc-8d9a-2a41bd468abc",
        term_unit="P3Y",
    ),
    resource_group_name="my-ps-rg",
    resource_name_="MyContosoPS")

```

```yaml
resources:
  professionalServiceSubscriptionLevel:
    type: azure-native:professionalservice:ProfessionalServiceSubscriptionLevel
    properties:
      location: global
      name: MyContosoPS
      properties:
        billingPeriod: P1Y
        offerId: testprofservice
        publisherId: microsoft-contoso
        quoteId: quoteabc
        skuId: ff051f4f-a6d9-4cbc-8d9a-2a41bd468abc
        termUnit: P3Y
      resourceGroupName: my-ps-rg
      resourceName: MyContosoPS

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:professionalservice:ProfessionalServiceSubscriptionLevel MyContosoPS /subscriptions/c825645b-e31b-9cf4-1cee-2aba9e58bc7c/resourceGroups/my-ps-rg/providers/Microsoft.ProfessionalService/resources/MyContosoPS 
```
