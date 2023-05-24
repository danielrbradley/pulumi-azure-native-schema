Partner configuration information
API Version: 2022-06-15.
Previous API Version: 2021-10-15-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PartnerConfigurations_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var partnerConfiguration = new AzureNative.EventGrid.PartnerConfiguration("partnerConfiguration", new()
    {
        PartnerAuthorization = new AzureNative.EventGrid.Inputs.PartnerAuthorizationArgs
        {
            AuthorizedPartnersList = new[]
            {
                new AzureNative.EventGrid.Inputs.PartnerArgs
                {
                    AuthorizationExpirationTimeInUtc = "2022-01-28T01:20:55.142Z",
                    PartnerName = "Contoso.Finance",
                    PartnerRegistrationImmutableId = "941892bc-f5d0-4d1c-8fb5-477570fc2b71",
                },
                new AzureNative.EventGrid.Inputs.PartnerArgs
                {
                    AuthorizationExpirationTimeInUtc = "2022-02-20T01:00:00.142Z",
                    PartnerName = "fabrikam.HR",
                    PartnerRegistrationImmutableId = "5362bdb6-ce3e-4d0d-9a5b-3eb92c8aab38",
                },
            },
            DefaultMaximumExpirationTimeInDays = 10,
        },
        ResourceGroupName = "examplerg",
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
		_, err := eventgrid.NewPartnerConfiguration(ctx, "partnerConfiguration", &eventgrid.PartnerConfigurationArgs{
			PartnerAuthorization: eventgrid.PartnerAuthorizationResponse{
				AuthorizedPartnersList: eventgrid.PartnerArray{
					&eventgrid.PartnerArgs{
						AuthorizationExpirationTimeInUtc: pulumi.String("2022-01-28T01:20:55.142Z"),
						PartnerName:                      pulumi.String("Contoso.Finance"),
						PartnerRegistrationImmutableId:   pulumi.String("941892bc-f5d0-4d1c-8fb5-477570fc2b71"),
					},
					&eventgrid.PartnerArgs{
						AuthorizationExpirationTimeInUtc: pulumi.String("2022-02-20T01:00:00.142Z"),
						PartnerName:                      pulumi.String("fabrikam.HR"),
						PartnerRegistrationImmutableId:   pulumi.String("5362bdb6-ce3e-4d0d-9a5b-3eb92c8aab38"),
					},
				},
				DefaultMaximumExpirationTimeInDays: pulumi.Int(10),
			},
			ResourceGroupName: pulumi.String("examplerg"),
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
import com.pulumi.azurenative.eventgrid.PartnerConfiguration;
import com.pulumi.azurenative.eventgrid.PartnerConfigurationArgs;
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
        var partnerConfiguration = new PartnerConfiguration("partnerConfiguration", PartnerConfigurationArgs.builder()        
            .partnerAuthorization(Map.ofEntries(
                Map.entry("authorizedPartnersList",                 
                    Map.ofEntries(
                        Map.entry("authorizationExpirationTimeInUtc", "2022-01-28T01:20:55.142Z"),
                        Map.entry("partnerName", "Contoso.Finance"),
                        Map.entry("partnerRegistrationImmutableId", "941892bc-f5d0-4d1c-8fb5-477570fc2b71")
                    ),
                    Map.ofEntries(
                        Map.entry("authorizationExpirationTimeInUtc", "2022-02-20T01:00:00.142Z"),
                        Map.entry("partnerName", "fabrikam.HR"),
                        Map.entry("partnerRegistrationImmutableId", "5362bdb6-ce3e-4d0d-9a5b-3eb92c8aab38")
                    )),
                Map.entry("defaultMaximumExpirationTimeInDays", 10)
            ))
            .resourceGroupName("examplerg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const partnerConfiguration = new azure_native.eventgrid.PartnerConfiguration("partnerConfiguration", {
    partnerAuthorization: {
        authorizedPartnersList: [
            {
                authorizationExpirationTimeInUtc: "2022-01-28T01:20:55.142Z",
                partnerName: "Contoso.Finance",
                partnerRegistrationImmutableId: "941892bc-f5d0-4d1c-8fb5-477570fc2b71",
            },
            {
                authorizationExpirationTimeInUtc: "2022-02-20T01:00:00.142Z",
                partnerName: "fabrikam.HR",
                partnerRegistrationImmutableId: "5362bdb6-ce3e-4d0d-9a5b-3eb92c8aab38",
            },
        ],
        defaultMaximumExpirationTimeInDays: 10,
    },
    resourceGroupName: "examplerg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

partner_configuration = azure_native.eventgrid.PartnerConfiguration("partnerConfiguration",
    partner_authorization=azure_native.eventgrid.PartnerAuthorizationResponseArgs(
        authorized_partners_list=[
            azure_native.eventgrid.PartnerArgs(
                authorization_expiration_time_in_utc="2022-01-28T01:20:55.142Z",
                partner_name="Contoso.Finance",
                partner_registration_immutable_id="941892bc-f5d0-4d1c-8fb5-477570fc2b71",
            ),
            azure_native.eventgrid.PartnerArgs(
                authorization_expiration_time_in_utc="2022-02-20T01:00:00.142Z",
                partner_name="fabrikam.HR",
                partner_registration_immutable_id="5362bdb6-ce3e-4d0d-9a5b-3eb92c8aab38",
            ),
        ],
        default_maximum_expiration_time_in_days=10,
    ),
    resource_group_name="examplerg")

```

```yaml
resources:
  partnerConfiguration:
    type: azure-native:eventgrid:PartnerConfiguration
    properties:
      partnerAuthorization:
        authorizedPartnersList:
          - authorizationExpirationTimeInUtc: 2022-01-28T01:20:55.142Z
            partnerName: Contoso.Finance
            partnerRegistrationImmutableId: 941892bc-f5d0-4d1c-8fb5-477570fc2b71
          - authorizationExpirationTimeInUtc: 2022-02-20T01:00:00.142Z
            partnerName: fabrikam.HR
            partnerRegistrationImmutableId: 5362bdb6-ce3e-4d0d-9a5b-3eb92c8aab38
        defaultMaximumExpirationTimeInDays: 10
      resourceGroupName: examplerg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:eventgrid:PartnerConfiguration default /subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/partnerConfigurations/default 
```
