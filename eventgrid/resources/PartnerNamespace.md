EventGrid Partner Namespace.
API Version: 2022-06-15.
Previous API Version: 2021-06-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PartnerNamespaces_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var partnerNamespace = new AzureNative.EventGrid.PartnerNamespace("partnerNamespace", new()
    {
        Location = "westus",
        PartnerNamespaceName = "examplePartnerNamespaceName1",
        PartnerRegistrationFullyQualifiedId = "/subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/partnerRegistrations/ContosoCorpAccount1",
        ResourceGroupName = "examplerg",
        Tags = 
        {
            { "tag1", "value1" },
            { "tag2", "value2" },
        },
    });

});


```

```go
package main

import (
	eventgrid "github.com/pulumi/pulumi-azure-native-sdk/eventgrid"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := eventgrid.NewPartnerNamespace(ctx, "partnerNamespace", &eventgrid.PartnerNamespaceArgs{
			Location:                            pulumi.String("westus"),
			PartnerNamespaceName:                pulumi.String("examplePartnerNamespaceName1"),
			PartnerRegistrationFullyQualifiedId: pulumi.String("/subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/partnerRegistrations/ContosoCorpAccount1"),
			ResourceGroupName:                   pulumi.String("examplerg"),
			Tags: pulumi.StringMap{
				"tag1": pulumi.String("value1"),
				"tag2": pulumi.String("value2"),
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
import com.pulumi.azurenative.eventgrid.PartnerNamespace;
import com.pulumi.azurenative.eventgrid.PartnerNamespaceArgs;
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
        var partnerNamespace = new PartnerNamespace("partnerNamespace", PartnerNamespaceArgs.builder()        
            .location("westus")
            .partnerNamespaceName("examplePartnerNamespaceName1")
            .partnerRegistrationFullyQualifiedId("/subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/partnerRegistrations/ContosoCorpAccount1")
            .resourceGroupName("examplerg")
            .tags(Map.ofEntries(
                Map.entry("tag1", "value1"),
                Map.entry("tag2", "value2")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const partnerNamespace = new azure_native.eventgrid.PartnerNamespace("partnerNamespace", {
    location: "westus",
    partnerNamespaceName: "examplePartnerNamespaceName1",
    partnerRegistrationFullyQualifiedId: "/subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/partnerRegistrations/ContosoCorpAccount1",
    resourceGroupName: "examplerg",
    tags: {
        tag1: "value1",
        tag2: "value2",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

partner_namespace = azure_native.eventgrid.PartnerNamespace("partnerNamespace",
    location="westus",
    partner_namespace_name="examplePartnerNamespaceName1",
    partner_registration_fully_qualified_id="/subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/partnerRegistrations/ContosoCorpAccount1",
    resource_group_name="examplerg",
    tags={
        "tag1": "value1",
        "tag2": "value2",
    })

```

```yaml
resources:
  partnerNamespace:
    type: azure-native:eventgrid:PartnerNamespace
    properties:
      location: westus
      partnerNamespaceName: examplePartnerNamespaceName1
      partnerRegistrationFullyQualifiedId: /subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/partnerRegistrations/ContosoCorpAccount1
      resourceGroupName: examplerg
      tags:
        tag1: value1
        tag2: value2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:eventgrid:PartnerNamespace examplePartnerNamespaceName1 /subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/partnerNamespaces/examplePartnerNamespaceName1 
```
