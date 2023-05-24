Organization resource.
API Version: 2021-12-01.
Previous API Version: 2020-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Organization_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var organization = new AzureNative.Confluent.Organization("organization", new()
    {
        Location = "West US",
        OfferDetail = new AzureNative.Confluent.Inputs.OfferDetailArgs
        {
            Id = "string",
            PlanId = "string",
            PlanName = "string",
            PublisherId = "string",
            TermUnit = "string",
        },
        OrganizationName = "myOrganization",
        ResourceGroupName = "myResourceGroup",
        Tags = 
        {
            { "Environment", "Dev" },
        },
        UserDetail = new AzureNative.Confluent.Inputs.UserDetailArgs
        {
            EmailAddress = "contoso@microsoft.com",
            FirstName = "string",
            LastName = "string",
        },
    });

});


```

```go
package main

import (
	confluent "github.com/pulumi/pulumi-azure-native-sdk/confluent"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := confluent.NewOrganization(ctx, "organization", &confluent.OrganizationArgs{
			Location: pulumi.String("West US"),
			OfferDetail: &confluent.OfferDetailArgs{
				Id:          pulumi.String("string"),
				PlanId:      pulumi.String("string"),
				PlanName:    pulumi.String("string"),
				PublisherId: pulumi.String("string"),
				TermUnit:    pulumi.String("string"),
			},
			OrganizationName:  pulumi.String("myOrganization"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			Tags: pulumi.StringMap{
				"Environment": pulumi.String("Dev"),
			},
			UserDetail: &confluent.UserDetailArgs{
				EmailAddress: pulumi.String("contoso@microsoft.com"),
				FirstName:    pulumi.String("string"),
				LastName:     pulumi.String("string"),
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
import com.pulumi.azurenative.confluent.Organization;
import com.pulumi.azurenative.confluent.OrganizationArgs;
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
        var organization = new Organization("organization", OrganizationArgs.builder()        
            .location("West US")
            .offerDetail(Map.ofEntries(
                Map.entry("id", "string"),
                Map.entry("planId", "string"),
                Map.entry("planName", "string"),
                Map.entry("publisherId", "string"),
                Map.entry("termUnit", "string")
            ))
            .organizationName("myOrganization")
            .resourceGroupName("myResourceGroup")
            .tags(Map.of("Environment", "Dev"))
            .userDetail(Map.ofEntries(
                Map.entry("emailAddress", "contoso@microsoft.com"),
                Map.entry("firstName", "string"),
                Map.entry("lastName", "string")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const organization = new azure_native.confluent.Organization("organization", {
    location: "West US",
    offerDetail: {
        id: "string",
        planId: "string",
        planName: "string",
        publisherId: "string",
        termUnit: "string",
    },
    organizationName: "myOrganization",
    resourceGroupName: "myResourceGroup",
    tags: {
        Environment: "Dev",
    },
    userDetail: {
        emailAddress: "contoso@microsoft.com",
        firstName: "string",
        lastName: "string",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

organization = azure_native.confluent.Organization("organization",
    location="West US",
    offer_detail=azure_native.confluent.OfferDetailArgs(
        id="string",
        plan_id="string",
        plan_name="string",
        publisher_id="string",
        term_unit="string",
    ),
    organization_name="myOrganization",
    resource_group_name="myResourceGroup",
    tags={
        "Environment": "Dev",
    },
    user_detail=azure_native.confluent.UserDetailArgs(
        email_address="contoso@microsoft.com",
        first_name="string",
        last_name="string",
    ))

```

```yaml
resources:
  organization:
    type: azure-native:confluent:Organization
    properties:
      location: West US
      offerDetail:
        id: string
        planId: string
        planName: string
        publisherId: string
        termUnit: string
      organizationName: myOrganization
      resourceGroupName: myResourceGroup
      tags:
        Environment: Dev
      userDetail:
        emailAddress: contoso@microsoft.com
        firstName: string
        lastName: string

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:confluent:Organization myOrganization /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Confluent/organizations/myOrganization 
```
