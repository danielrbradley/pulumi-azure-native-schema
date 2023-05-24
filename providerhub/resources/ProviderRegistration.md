
API Version: 2020-11-20.
Previous API Version: 2020-11-20. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ProviderRegistrations_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var providerRegistration = new AzureNative.ProviderHub.ProviderRegistration("providerRegistration", new()
    {
        Properties = new AzureNative.ProviderHub.Inputs.ProviderRegistrationPropertiesArgs
        {
            Capabilities = new[]
            {
                new AzureNative.ProviderHub.Inputs.ResourceProviderCapabilitiesArgs
                {
                    Effect = "Allow",
                    QuotaId = "CSP_2015-05-01",
                },
                new AzureNative.ProviderHub.Inputs.ResourceProviderCapabilitiesArgs
                {
                    Effect = "Allow",
                    QuotaId = "CSP_MG_2017-12-01",
                },
            },
            Management = new AzureNative.ProviderHub.Inputs.ResourceProviderManifestPropertiesManagementArgs
            {
                IncidentContactEmail = "helpme@contoso.com",
                IncidentRoutingService = "Contoso Resource Provider",
                IncidentRoutingTeam = "Contoso Triage",
            },
            ProviderType = "Internal",
            ProviderVersion = "2.0",
        },
        ProviderNamespace = "Microsoft.Contoso",
    });

});


```

```go
package main

import (
	providerhub "github.com/pulumi/pulumi-azure-native-sdk/providerhub"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := providerhub.NewProviderRegistration(ctx, "providerRegistration", &providerhub.ProviderRegistrationArgs{
			Properties: providerhub.ProviderRegistrationResponseProperties{
				Capabilities: providerhub.ResourceProviderCapabilitiesArray{
					&providerhub.ResourceProviderCapabilitiesArgs{
						Effect:  pulumi.String("Allow"),
						QuotaId: pulumi.String("CSP_2015-05-01"),
					},
					&providerhub.ResourceProviderCapabilitiesArgs{
						Effect:  pulumi.String("Allow"),
						QuotaId: pulumi.String("CSP_MG_2017-12-01"),
					},
				},
				Management: &providerhub.ResourceProviderManifestPropertiesManagementArgs{
					IncidentContactEmail:   pulumi.String("helpme@contoso.com"),
					IncidentRoutingService: pulumi.String("Contoso Resource Provider"),
					IncidentRoutingTeam:    pulumi.String("Contoso Triage"),
				},
				ProviderType:    pulumi.String("Internal"),
				ProviderVersion: pulumi.String("2.0"),
			},
			ProviderNamespace: pulumi.String("Microsoft.Contoso"),
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
import com.pulumi.azurenative.providerhub.ProviderRegistration;
import com.pulumi.azurenative.providerhub.ProviderRegistrationArgs;
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
        var providerRegistration = new ProviderRegistration("providerRegistration", ProviderRegistrationArgs.builder()        
            .properties(Map.ofEntries(
                Map.entry("capabilities",                 
                    Map.ofEntries(
                        Map.entry("effect", "Allow"),
                        Map.entry("quotaId", "CSP_2015-05-01")
                    ),
                    Map.ofEntries(
                        Map.entry("effect", "Allow"),
                        Map.entry("quotaId", "CSP_MG_2017-12-01")
                    )),
                Map.entry("management", Map.ofEntries(
                    Map.entry("incidentContactEmail", "helpme@contoso.com"),
                    Map.entry("incidentRoutingService", "Contoso Resource Provider"),
                    Map.entry("incidentRoutingTeam", "Contoso Triage")
                )),
                Map.entry("providerType", "Internal"),
                Map.entry("providerVersion", "2.0")
            ))
            .providerNamespace("Microsoft.Contoso")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const providerRegistration = new azure_native.providerhub.ProviderRegistration("providerRegistration", {
    properties: {
        capabilities: [
            {
                effect: "Allow",
                quotaId: "CSP_2015-05-01",
            },
            {
                effect: "Allow",
                quotaId: "CSP_MG_2017-12-01",
            },
        ],
        management: {
            incidentContactEmail: "helpme@contoso.com",
            incidentRoutingService: "Contoso Resource Provider",
            incidentRoutingTeam: "Contoso Triage",
        },
        providerType: "Internal",
        providerVersion: "2.0",
    },
    providerNamespace: "Microsoft.Contoso",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

provider_registration = azure_native.providerhub.ProviderRegistration("providerRegistration",
    properties=azure_native.providerhub.ProviderRegistrationResponsePropertiesArgs(
        capabilities=[
            azure_native.providerhub.ResourceProviderCapabilitiesArgs(
                effect="Allow",
                quota_id="CSP_2015-05-01",
            ),
            azure_native.providerhub.ResourceProviderCapabilitiesArgs(
                effect="Allow",
                quota_id="CSP_MG_2017-12-01",
            ),
        ],
        management=azure_native.providerhub.ResourceProviderManifestPropertiesManagementArgs(
            incident_contact_email="helpme@contoso.com",
            incident_routing_service="Contoso Resource Provider",
            incident_routing_team="Contoso Triage",
        ),
        provider_type="Internal",
        provider_version="2.0",
    ),
    provider_namespace="Microsoft.Contoso")

```

```yaml
resources:
  providerRegistration:
    type: azure-native:providerhub:ProviderRegistration
    properties:
      properties:
        capabilities:
          - effect: Allow
            quotaId: CSP_2015-05-01
          - effect: Allow
            quotaId: CSP_MG_2017-12-01
        management:
          incidentContactEmail: helpme@contoso.com
          incidentRoutingService: Contoso Resource Provider
          incidentRoutingTeam: Contoso Triage
        providerType: Internal
        providerVersion: '2.0'
      providerNamespace: Microsoft.Contoso

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:providerhub:ProviderRegistration myresource1 /subscriptions/{subscriptionId}/providers/Microsoft.ProviderHub/providerRegistrations/{providerNamespace} 
```
