The integration account partner.
API Version: 2019-05-01.
Previous API Version: 2019-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a partner
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var integrationAccountPartner = new AzureNative.Logic.IntegrationAccountPartner("integrationAccountPartner", new()
    {
        Content = new AzureNative.Logic.Inputs.PartnerContentArgs
        {
            B2b = new AzureNative.Logic.Inputs.B2BPartnerContentArgs
            {
                BusinessIdentities = new[]
                {
                    new AzureNative.Logic.Inputs.BusinessIdentityArgs
                    {
                        Qualifier = "AA",
                        Value = "ZZ",
                    },
                },
            },
        },
        IntegrationAccountName = "testIntegrationAccount",
        Location = "westus",
        Metadata = null,
        PartnerName = "testPartner",
        PartnerType = "B2B",
        ResourceGroupName = "testResourceGroup",
        Tags = null,
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.logic.IntegrationAccountPartner;
import com.pulumi.azurenative.logic.IntegrationAccountPartnerArgs;
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
        var integrationAccountPartner = new IntegrationAccountPartner("integrationAccountPartner", IntegrationAccountPartnerArgs.builder()        
            .content(Map.of("b2b", Map.of("businessIdentities", Map.ofEntries(
                Map.entry("qualifier", "AA"),
                Map.entry("value", "ZZ")
            ))))
            .integrationAccountName("testIntegrationAccount")
            .location("westus")
            .metadata()
            .partnerName("testPartner")
            .partnerType("B2B")
            .resourceGroupName("testResourceGroup")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const integrationAccountPartner = new azure_native.logic.IntegrationAccountPartner("integrationAccountPartner", {
    content: {
        b2b: {
            businessIdentities: [{
                qualifier: "AA",
                value: "ZZ",
            }],
        },
    },
    integrationAccountName: "testIntegrationAccount",
    location: "westus",
    metadata: {},
    partnerName: "testPartner",
    partnerType: "B2B",
    resourceGroupName: "testResourceGroup",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

integration_account_partner = azure_native.logic.IntegrationAccountPartner("integrationAccountPartner",
    content=azure_native.logic.PartnerContentResponseArgs(
        b2b={
            "businessIdentities": [azure_native.logic.BusinessIdentityArgs(
                qualifier="AA",
                value="ZZ",
            )],
        },
    ),
    integration_account_name="testIntegrationAccount",
    location="westus",
    metadata={},
    partner_name="testPartner",
    partner_type="B2B",
    resource_group_name="testResourceGroup",
    tags={})

```

```yaml
resources:
  integrationAccountPartner:
    type: azure-native:logic:IntegrationAccountPartner
    properties:
      content:
        b2b:
          businessIdentities:
            - qualifier: AA
              value: ZZ
      integrationAccountName: testIntegrationAccount
      location: westus
      metadata: {}
      partnerName: testPartner
      partnerType: B2B
      resourceGroupName: testResourceGroup
      tags: {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:logic:IntegrationAccountPartner testPartner /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/flowrg/providers/Microsoft.Logic/integrationAccounts/testIntegrationAccount/partners/testPartner 
```
