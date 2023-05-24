Site REST Resource.
API Version: 2020-07-07.
Previous API Version: 2020-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Hyper-V site
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var hyperVSite = new AzureNative.OffAzure.HyperVSite("hyperVSite", new()
    {
        Location = "eastus",
        Properties = new AzureNative.OffAzure.Inputs.SitePropertiesArgs
        {
            ServicePrincipalIdentityDetails = new AzureNative.OffAzure.Inputs.SiteSpnPropertiesArgs
            {
                AadAuthority = "https://login.windows.net/72f988bf-86f1-41af-91ab-2d7cd011db47",
                ApplicationId = "e9f013df-2a2a-4871-b766-e79867f30348",
                Audience = "https://72f988bf-86f1-41af-91ab-2d7cd011db47/MaheshSite17ac9agentauthaadapp",
                ObjectId = "2cd492bc-7ef3-4ee0-b301-59a88108b47b",
                TenantId = "72f988bf-86f1-41af-91ab-2d7cd011db47",
            },
        },
        ResourceGroupName = "pajindTest",
        SiteName = "appliance1e39site",
    });

});


```

```go
package main

import (
	offazure "github.com/pulumi/pulumi-azure-native-sdk/offazure"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := offazure.NewHyperVSite(ctx, "hyperVSite", &offazure.HyperVSiteArgs{
			Location: pulumi.String("eastus"),
			Properties: offazure.SitePropertiesResponse{
				ServicePrincipalIdentityDetails: &offazure.SiteSpnPropertiesArgs{
					AadAuthority:  pulumi.String("https://login.windows.net/72f988bf-86f1-41af-91ab-2d7cd011db47"),
					ApplicationId: pulumi.String("e9f013df-2a2a-4871-b766-e79867f30348"),
					Audience:      pulumi.String("https://72f988bf-86f1-41af-91ab-2d7cd011db47/MaheshSite17ac9agentauthaadapp"),
					ObjectId:      pulumi.String("2cd492bc-7ef3-4ee0-b301-59a88108b47b"),
					TenantId:      pulumi.String("72f988bf-86f1-41af-91ab-2d7cd011db47"),
				},
			},
			ResourceGroupName: pulumi.String("pajindTest"),
			SiteName:          pulumi.String("appliance1e39site"),
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
import com.pulumi.azurenative.offazure.HyperVSite;
import com.pulumi.azurenative.offazure.HyperVSiteArgs;
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
        var hyperVSite = new HyperVSite("hyperVSite", HyperVSiteArgs.builder()        
            .location("eastus")
            .properties(Map.of("servicePrincipalIdentityDetails", Map.ofEntries(
                Map.entry("aadAuthority", "https://login.windows.net/72f988bf-86f1-41af-91ab-2d7cd011db47"),
                Map.entry("applicationId", "e9f013df-2a2a-4871-b766-e79867f30348"),
                Map.entry("audience", "https://72f988bf-86f1-41af-91ab-2d7cd011db47/MaheshSite17ac9agentauthaadapp"),
                Map.entry("objectId", "2cd492bc-7ef3-4ee0-b301-59a88108b47b"),
                Map.entry("tenantId", "72f988bf-86f1-41af-91ab-2d7cd011db47")
            )))
            .resourceGroupName("pajindTest")
            .siteName("appliance1e39site")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const hyperVSite = new azure_native.offazure.HyperVSite("hyperVSite", {
    location: "eastus",
    properties: {
        servicePrincipalIdentityDetails: {
            aadAuthority: "https://login.windows.net/72f988bf-86f1-41af-91ab-2d7cd011db47",
            applicationId: "e9f013df-2a2a-4871-b766-e79867f30348",
            audience: "https://72f988bf-86f1-41af-91ab-2d7cd011db47/MaheshSite17ac9agentauthaadapp",
            objectId: "2cd492bc-7ef3-4ee0-b301-59a88108b47b",
            tenantId: "72f988bf-86f1-41af-91ab-2d7cd011db47",
        },
    },
    resourceGroupName: "pajindTest",
    siteName: "appliance1e39site",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

hyper_v_site = azure_native.offazure.HyperVSite("hyperVSite",
    location="eastus",
    properties=azure_native.offazure.SitePropertiesResponseArgs(
        service_principal_identity_details=azure_native.offazure.SiteSpnPropertiesArgs(
            aad_authority="https://login.windows.net/72f988bf-86f1-41af-91ab-2d7cd011db47",
            application_id="e9f013df-2a2a-4871-b766-e79867f30348",
            audience="https://72f988bf-86f1-41af-91ab-2d7cd011db47/MaheshSite17ac9agentauthaadapp",
            object_id="2cd492bc-7ef3-4ee0-b301-59a88108b47b",
            tenant_id="72f988bf-86f1-41af-91ab-2d7cd011db47",
        ),
    ),
    resource_group_name="pajindTest",
    site_name="appliance1e39site")

```

```yaml
resources:
  hyperVSite:
    type: azure-native:offazure:HyperVSite
    properties:
      location: eastus
      properties:
        servicePrincipalIdentityDetails:
          aadAuthority: https://login.windows.net/72f988bf-86f1-41af-91ab-2d7cd011db47
          applicationId: e9f013df-2a2a-4871-b766-e79867f30348
          audience: https://72f988bf-86f1-41af-91ab-2d7cd011db47/MaheshSite17ac9agentauthaadapp
          objectId: 2cd492bc-7ef3-4ee0-b301-59a88108b47b
          tenantId: 72f988bf-86f1-41af-91ab-2d7cd011db47
      resourceGroupName: pajindTest
      siteName: appliance1e39site

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:offazure:HyperVSite appliance1e39site /subscriptions/4bd2aa0f-2bd2-4d67-91a8-5a4533d58600/resourceGroups/pajindTest/providers/Microsoft.OffAzure/HyperVSites/appliance1e39site 
```
