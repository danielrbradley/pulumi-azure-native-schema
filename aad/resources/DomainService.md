Domain service.
API Version: 2022-12-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Domain Service
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var domainService = new AzureNative.Aad.DomainService("domainService", new()
    {
        DomainName = "TestDomainService.com",
        DomainSecuritySettings = new AzureNative.Aad.Inputs.DomainSecuritySettingsArgs
        {
            NtlmV1 = "Enabled",
            SyncNtlmPasswords = "Enabled",
            TlsV1 = "Disabled",
        },
        DomainServiceName = "TestDomainService.com",
        FilteredSync = "Enabled",
        LdapsSettings = new AzureNative.Aad.Inputs.LdapsSettingsArgs
        {
            ExternalAccess = "Enabled",
            Ldaps = "Enabled",
            PfxCertificate = "MIIDPDCCAiSgAwIBAgIQQUI9P6tq2p9OFIJa7DLNvTANBgkqhkiG9w0BAQsFADAgMR4w...",
            PfxCertificatePassword = "<pfxCertificatePassword>",
        },
        NotificationSettings = new AzureNative.Aad.Inputs.NotificationSettingsArgs
        {
            AdditionalRecipients = new[]
            {
                "jicha@microsoft.com",
                "caalmont@microsoft.com",
            },
            NotifyDcAdmins = "Enabled",
            NotifyGlobalAdmins = "Enabled",
        },
        ReplicaSets = new[]
        {
            new AzureNative.Aad.Inputs.ReplicaSetArgs
            {
                Location = "West US",
                SubnetId = "/subscriptions/1639790a-76a2-4ac4-98d9-8562f5dfcb4d/resourceGroups/TestNetworkResourceGroup/providers/Microsoft.Network/virtualNetworks/TestVnetWUS/subnets/TestSubnetWUS",
            },
        },
        ResourceGroupName = "TestResourceGroup",
    });

});


```

```go
package main

import (
	aad "github.com/pulumi/pulumi-azure-native-sdk/aad"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := aad.NewDomainService(ctx, "domainService", &aad.DomainServiceArgs{
			DomainName: pulumi.String("TestDomainService.com"),
			DomainSecuritySettings: &aad.DomainSecuritySettingsArgs{
				NtlmV1:            pulumi.String("Enabled"),
				SyncNtlmPasswords: pulumi.String("Enabled"),
				TlsV1:             pulumi.String("Disabled"),
			},
			DomainServiceName: pulumi.String("TestDomainService.com"),
			FilteredSync:      pulumi.String("Enabled"),
			LdapsSettings: &aad.LdapsSettingsArgs{
				ExternalAccess:         pulumi.String("Enabled"),
				Ldaps:                  pulumi.String("Enabled"),
				PfxCertificate:         pulumi.String("MIIDPDCCAiSgAwIBAgIQQUI9P6tq2p9OFIJa7DLNvTANBgkqhkiG9w0BAQsFADAgMR4w..."),
				PfxCertificatePassword: pulumi.String("<pfxCertificatePassword>"),
			},
			NotificationSettings: &aad.NotificationSettingsArgs{
				AdditionalRecipients: pulumi.StringArray{
					pulumi.String("jicha@microsoft.com"),
					pulumi.String("caalmont@microsoft.com"),
				},
				NotifyDcAdmins:     pulumi.String("Enabled"),
				NotifyGlobalAdmins: pulumi.String("Enabled"),
			},
			ReplicaSets: []aad.ReplicaSetArgs{
				{
					Location: pulumi.String("West US"),
					SubnetId: pulumi.String("/subscriptions/1639790a-76a2-4ac4-98d9-8562f5dfcb4d/resourceGroups/TestNetworkResourceGroup/providers/Microsoft.Network/virtualNetworks/TestVnetWUS/subnets/TestSubnetWUS"),
				},
			},
			ResourceGroupName: pulumi.String("TestResourceGroup"),
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
import com.pulumi.azurenative.aad.DomainService;
import com.pulumi.azurenative.aad.DomainServiceArgs;
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
        var domainService = new DomainService("domainService", DomainServiceArgs.builder()        
            .domainName("TestDomainService.com")
            .domainSecuritySettings(Map.ofEntries(
                Map.entry("ntlmV1", "Enabled"),
                Map.entry("syncNtlmPasswords", "Enabled"),
                Map.entry("tlsV1", "Disabled")
            ))
            .domainServiceName("TestDomainService.com")
            .filteredSync("Enabled")
            .ldapsSettings(Map.ofEntries(
                Map.entry("externalAccess", "Enabled"),
                Map.entry("ldaps", "Enabled"),
                Map.entry("pfxCertificate", "MIIDPDCCAiSgAwIBAgIQQUI9P6tq2p9OFIJa7DLNvTANBgkqhkiG9w0BAQsFADAgMR4w..."),
                Map.entry("pfxCertificatePassword", "<pfxCertificatePassword>")
            ))
            .notificationSettings(Map.ofEntries(
                Map.entry("additionalRecipients",                 
                    "jicha@microsoft.com",
                    "caalmont@microsoft.com"),
                Map.entry("notifyDcAdmins", "Enabled"),
                Map.entry("notifyGlobalAdmins", "Enabled")
            ))
            .replicaSets(Map.ofEntries(
                Map.entry("location", "West US"),
                Map.entry("subnetId", "/subscriptions/1639790a-76a2-4ac4-98d9-8562f5dfcb4d/resourceGroups/TestNetworkResourceGroup/providers/Microsoft.Network/virtualNetworks/TestVnetWUS/subnets/TestSubnetWUS")
            ))
            .resourceGroupName("TestResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const domainService = new azure_native.aad.DomainService("domainService", {
    domainName: "TestDomainService.com",
    domainSecuritySettings: {
        ntlmV1: "Enabled",
        syncNtlmPasswords: "Enabled",
        tlsV1: "Disabled",
    },
    domainServiceName: "TestDomainService.com",
    filteredSync: "Enabled",
    ldapsSettings: {
        externalAccess: "Enabled",
        ldaps: "Enabled",
        pfxCertificate: "MIIDPDCCAiSgAwIBAgIQQUI9P6tq2p9OFIJa7DLNvTANBgkqhkiG9w0BAQsFADAgMR4w...",
        pfxCertificatePassword: "<pfxCertificatePassword>",
    },
    notificationSettings: {
        additionalRecipients: [
            "jicha@microsoft.com",
            "caalmont@microsoft.com",
        ],
        notifyDcAdmins: "Enabled",
        notifyGlobalAdmins: "Enabled",
    },
    replicaSets: [{
        location: "West US",
        subnetId: "/subscriptions/1639790a-76a2-4ac4-98d9-8562f5dfcb4d/resourceGroups/TestNetworkResourceGroup/providers/Microsoft.Network/virtualNetworks/TestVnetWUS/subnets/TestSubnetWUS",
    }],
    resourceGroupName: "TestResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

domain_service = azure_native.aad.DomainService("domainService",
    domain_name="TestDomainService.com",
    domain_security_settings=azure_native.aad.DomainSecuritySettingsArgs(
        ntlm_v1="Enabled",
        sync_ntlm_passwords="Enabled",
        tls_v1="Disabled",
    ),
    domain_service_name="TestDomainService.com",
    filtered_sync="Enabled",
    ldaps_settings=azure_native.aad.LdapsSettingsArgs(
        external_access="Enabled",
        ldaps="Enabled",
        pfx_certificate="MIIDPDCCAiSgAwIBAgIQQUI9P6tq2p9OFIJa7DLNvTANBgkqhkiG9w0BAQsFADAgMR4w...",
        pfx_certificate_password="<pfxCertificatePassword>",
    ),
    notification_settings=azure_native.aad.NotificationSettingsArgs(
        additional_recipients=[
            "jicha@microsoft.com",
            "caalmont@microsoft.com",
        ],
        notify_dc_admins="Enabled",
        notify_global_admins="Enabled",
    ),
    replica_sets=[azure_native.aad.ReplicaSetArgs(
        location="West US",
        subnet_id="/subscriptions/1639790a-76a2-4ac4-98d9-8562f5dfcb4d/resourceGroups/TestNetworkResourceGroup/providers/Microsoft.Network/virtualNetworks/TestVnetWUS/subnets/TestSubnetWUS",
    )],
    resource_group_name="TestResourceGroup")

```

```yaml
resources:
  domainService:
    type: azure-native:aad:DomainService
    properties:
      domainName: TestDomainService.com
      domainSecuritySettings:
        ntlmV1: Enabled
        syncNtlmPasswords: Enabled
        tlsV1: Disabled
      domainServiceName: TestDomainService.com
      filteredSync: Enabled
      ldapsSettings:
        externalAccess: Enabled
        ldaps: Enabled
        pfxCertificate: MIIDPDCCAiSgAwIBAgIQQUI9P6tq2p9OFIJa7DLNvTANBgkqhkiG9w0BAQsFADAgMR4w...
        pfxCertificatePassword: <pfxCertificatePassword>
      notificationSettings:
        additionalRecipients:
          - jicha@microsoft.com
          - caalmont@microsoft.com
        notifyDcAdmins: Enabled
        notifyGlobalAdmins: Enabled
      replicaSets:
        - location: West US
          subnetId: /subscriptions/1639790a-76a2-4ac4-98d9-8562f5dfcb4d/resourceGroups/TestNetworkResourceGroup/providers/Microsoft.Network/virtualNetworks/TestVnetWUS/subnets/TestSubnetWUS
      resourceGroupName: TestResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:aad:DomainService TestDomainService.com /subscriptions/1639790a-76a2-4ac4-98d9-8562f5dfcb4d/resourceGroups/TestResourceGroup/providers/Microsoft.AAD/DomainServices/TestDomainService.com 
```
