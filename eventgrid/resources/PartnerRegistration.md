Information about a partner registration.
API Version: 2022-06-15.
Previous API Version: 2021-06-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PartnerRegistrations_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var partnerRegistration = new AzureNative.EventGrid.PartnerRegistration("partnerRegistration", new()
    {
        Location = "global",
        PartnerRegistrationName = "examplePartnerRegistrationName1",
        ResourceGroupName = "examplerg",
        Tags = 
        {
            { "key1", "value1" },
            { "key2", "Value2" },
            { "key3", "Value3" },
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
		_, err := eventgrid.NewPartnerRegistration(ctx, "partnerRegistration", &eventgrid.PartnerRegistrationArgs{
			Location:                pulumi.String("global"),
			PartnerRegistrationName: pulumi.String("examplePartnerRegistrationName1"),
			ResourceGroupName:       pulumi.String("examplerg"),
			Tags: pulumi.StringMap{
				"key1": pulumi.String("value1"),
				"key2": pulumi.String("Value2"),
				"key3": pulumi.String("Value3"),
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
import com.pulumi.azurenative.eventgrid.PartnerRegistration;
import com.pulumi.azurenative.eventgrid.PartnerRegistrationArgs;
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
        var partnerRegistration = new PartnerRegistration("partnerRegistration", PartnerRegistrationArgs.builder()        
            .location("global")
            .partnerRegistrationName("examplePartnerRegistrationName1")
            .resourceGroupName("examplerg")
            .tags(Map.ofEntries(
                Map.entry("key1", "value1"),
                Map.entry("key2", "Value2"),
                Map.entry("key3", "Value3")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const partnerRegistration = new azure_native.eventgrid.PartnerRegistration("partnerRegistration", {
    location: "global",
    partnerRegistrationName: "examplePartnerRegistrationName1",
    resourceGroupName: "examplerg",
    tags: {
        key1: "value1",
        key2: "Value2",
        key3: "Value3",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

partner_registration = azure_native.eventgrid.PartnerRegistration("partnerRegistration",
    location="global",
    partner_registration_name="examplePartnerRegistrationName1",
    resource_group_name="examplerg",
    tags={
        "key1": "value1",
        "key2": "Value2",
        "key3": "Value3",
    })

```

```yaml
resources:
  partnerRegistration:
    type: azure-native:eventgrid:PartnerRegistration
    properties:
      location: global
      partnerRegistrationName: examplePartnerRegistrationName1
      resourceGroupName: examplerg
      tags:
        key1: value1
        key2: Value2
        key3: Value3

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:eventgrid:PartnerRegistration examplePartnerRegistrationName1 /subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/partnerRegistrations/examplePartnerRegistrationName1 
```
