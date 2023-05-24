Friendly domain name mapping to the endpoint hostname that the customer provides for branding purposes, e.g. www.contoso.com.
API Version: 2021-06-01.
Previous API Version: 2020-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### AFDCustomDomains_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var afdCustomDomain = new AzureNative.Cdn.AFDCustomDomain("afdCustomDomain", new()
    {
        AzureDnsZone = new AzureNative.Cdn.Inputs.ResourceReferenceArgs
        {
            Id = "",
        },
        CustomDomainName = "domain1",
        HostName = "www.someDomain.net",
        ProfileName = "profile1",
        ResourceGroupName = "RG",
        TlsSettings = new AzureNative.Cdn.Inputs.AFDDomainHttpsParametersArgs
        {
            CertificateType = "ManagedCertificate",
            MinimumTlsVersion = AzureNative.Cdn.AfdMinimumTlsVersion.TLS12,
        },
    });

});


```

```go
package main

import (
	cdn "github.com/pulumi/pulumi-azure-native-sdk/cdn"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := cdn.NewAFDCustomDomain(ctx, "afdCustomDomain", &cdn.AFDCustomDomainArgs{
			AzureDnsZone: &cdn.ResourceReferenceArgs{
				Id: pulumi.String(""),
			},
			CustomDomainName:  pulumi.String("domain1"),
			HostName:          pulumi.String("www.someDomain.net"),
			ProfileName:       pulumi.String("profile1"),
			ResourceGroupName: pulumi.String("RG"),
			TlsSettings: &cdn.AFDDomainHttpsParametersArgs{
				CertificateType:   pulumi.String("ManagedCertificate"),
				MinimumTlsVersion: cdn.AfdMinimumTlsVersionTLS12,
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
import com.pulumi.azurenative.cdn.AFDCustomDomain;
import com.pulumi.azurenative.cdn.AFDCustomDomainArgs;
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
        var afdCustomDomain = new AFDCustomDomain("afdCustomDomain", AFDCustomDomainArgs.builder()        
            .azureDnsZone(Map.of("id", ""))
            .customDomainName("domain1")
            .hostName("www.someDomain.net")
            .profileName("profile1")
            .resourceGroupName("RG")
            .tlsSettings(Map.ofEntries(
                Map.entry("certificateType", "ManagedCertificate"),
                Map.entry("minimumTlsVersion", "TLS12")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const afdCustomDomain = new azure_native.cdn.AFDCustomDomain("afdCustomDomain", {
    azureDnsZone: {
        id: "",
    },
    customDomainName: "domain1",
    hostName: "www.someDomain.net",
    profileName: "profile1",
    resourceGroupName: "RG",
    tlsSettings: {
        certificateType: "ManagedCertificate",
        minimumTlsVersion: azure_native.cdn.AfdMinimumTlsVersion.TLS12,
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

afd_custom_domain = azure_native.cdn.AFDCustomDomain("afdCustomDomain",
    azure_dns_zone=azure_native.cdn.ResourceReferenceArgs(
        id="",
    ),
    custom_domain_name="domain1",
    host_name="www.someDomain.net",
    profile_name="profile1",
    resource_group_name="RG",
    tls_settings=azure_native.cdn.AFDDomainHttpsParametersArgs(
        certificate_type="ManagedCertificate",
        minimum_tls_version=azure_native.cdn.AfdMinimumTlsVersion.TLS12,
    ))

```

```yaml
resources:
  afdCustomDomain:
    type: azure-native:cdn:AFDCustomDomain
    properties:
      azureDnsZone:
        id:
      customDomainName: domain1
      hostName: www.someDomain.net
      profileName: profile1
      resourceGroupName: RG
      tlsSettings:
        certificateType: ManagedCertificate
        minimumTlsVersion: TLS12

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:cdn:AFDCustomDomain domain1 /subscriptions/subid/resourcegroups/RG/providers/Microsoft.Cdn/profiles/profile1/customdomains/domain1 
```
