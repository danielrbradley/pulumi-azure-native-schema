Confidential Ledger. Contains the properties of Confidential Ledger Resource.
API Version: 2022-05-13.
Previous API Version: 2020-12-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ConfidentialLedgerCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var ledger = new AzureNative.ConfidentialLedger.Ledger("ledger", new()
    {
        LedgerName = "DummyLedgerName",
        Location = "EastUS",
        Properties = new AzureNative.ConfidentialLedger.Inputs.LedgerPropertiesArgs
        {
            AadBasedSecurityPrincipals = new[]
            {
                new AzureNative.ConfidentialLedger.Inputs.AADBasedSecurityPrincipalArgs
                {
                    LedgerRoleName = "Administrator",
                    PrincipalId = "34621747-6fc8-4771-a2eb-72f31c461f2e",
                    TenantId = "bce123b9-2b7b-4975-8360-5ca0b9b1cd08",
                },
            },
            CertBasedSecurityPrincipals = new[]
            {
                new AzureNative.ConfidentialLedger.Inputs.CertBasedSecurityPrincipalArgs
                {
                    Cert = "-----BEGIN CERTIFICATE-----MIIBsjCCATigAwIBAgIUZWIbyG79TniQLd2UxJuU74tqrKcwCgYIKoZIzj0EAwMwEDEOMAwGA1UEAwwFdXNlcjAwHhcNMjEwMzE2MTgwNjExWhcNMjIwMzE2MTgwNjExWjAQMQ4wDAYDVQQDDAV1c2VyMDB2MBAGByqGSM49AgEGBSuBBAAiA2IABBiWSo/j8EFit7aUMm5lF+lUmCu+IgfnpFD+7QMgLKtxRJ3aGSqgS/GpqcYVGddnODtSarNE/HyGKUFUolLPQ5ybHcouUk0kyfA7XMeSoUA4lBz63Wha8wmXo+NdBRo39qNTMFEwHQYDVR0OBBYEFPtuhrwgGjDFHeUUT4nGsXaZn69KMB8GA1UdIwQYMBaAFPtuhrwgGjDFHeUUT4nGsXaZn69KMA8GA1UdEwEB/wQFMAMBAf8wCgYIKoZIzj0EAwMDaAAwZQIxAOnozm2CyqRwSSQLls5r+mUHRGRyXHXwYtM4Dcst/VEZdmS9fqvHRCHbjUlO/+HNfgIwMWZ4FmsjD3wnPxONOm9YdVn/PRD7SsPRPbOjwBiE4EBGaHDsLjYAGDSGi7NJnSkA-----END CERTIFICATE-----",
                    LedgerRoleName = "Reader",
                },
            },
            LedgerType = "Public",
        },
        ResourceGroupName = "DummyResourceGroupName",
        Tags = 
        {
            { "additionalProps1", "additional properties" },
        },
    });

});


```

```go
package main

import (
	confidentialledger "github.com/pulumi/pulumi-azure-native-sdk/confidentialledger"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := confidentialledger.NewLedger(ctx, "ledger", &confidentialledger.LedgerArgs{
			LedgerName: pulumi.String("DummyLedgerName"),
			Location:   pulumi.String("EastUS"),
			Properties: confidentialledger.LedgerPropertiesResponse{
				AadBasedSecurityPrincipals: confidentialledger.AADBasedSecurityPrincipalArray{
					&confidentialledger.AADBasedSecurityPrincipalArgs{
						LedgerRoleName: pulumi.String("Administrator"),
						PrincipalId:    pulumi.String("34621747-6fc8-4771-a2eb-72f31c461f2e"),
						TenantId:       pulumi.String("bce123b9-2b7b-4975-8360-5ca0b9b1cd08"),
					},
				},
				CertBasedSecurityPrincipals: confidentialledger.CertBasedSecurityPrincipalArray{
					&confidentialledger.CertBasedSecurityPrincipalArgs{
						Cert:           pulumi.String("-----BEGIN CERTIFICATE-----MIIBsjCCATigAwIBAgIUZWIbyG79TniQLd2UxJuU74tqrKcwCgYIKoZIzj0EAwMwEDEOMAwGA1UEAwwFdXNlcjAwHhcNMjEwMzE2MTgwNjExWhcNMjIwMzE2MTgwNjExWjAQMQ4wDAYDVQQDDAV1c2VyMDB2MBAGByqGSM49AgEGBSuBBAAiA2IABBiWSo/j8EFit7aUMm5lF+lUmCu+IgfnpFD+7QMgLKtxRJ3aGSqgS/GpqcYVGddnODtSarNE/HyGKUFUolLPQ5ybHcouUk0kyfA7XMeSoUA4lBz63Wha8wmXo+NdBRo39qNTMFEwHQYDVR0OBBYEFPtuhrwgGjDFHeUUT4nGsXaZn69KMB8GA1UdIwQYMBaAFPtuhrwgGjDFHeUUT4nGsXaZn69KMA8GA1UdEwEB/wQFMAMBAf8wCgYIKoZIzj0EAwMDaAAwZQIxAOnozm2CyqRwSSQLls5r+mUHRGRyXHXwYtM4Dcst/VEZdmS9fqvHRCHbjUlO/+HNfgIwMWZ4FmsjD3wnPxONOm9YdVn/PRD7SsPRPbOjwBiE4EBGaHDsLjYAGDSGi7NJnSkA-----END CERTIFICATE-----"),
						LedgerRoleName: pulumi.String("Reader"),
					},
				},
				LedgerType: pulumi.String("Public"),
			},
			ResourceGroupName: pulumi.String("DummyResourceGroupName"),
			Tags: pulumi.StringMap{
				"additionalProps1": pulumi.String("additional properties"),
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
import com.pulumi.azurenative.confidentialledger.Ledger;
import com.pulumi.azurenative.confidentialledger.LedgerArgs;
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
        var ledger = new Ledger("ledger", LedgerArgs.builder()        
            .ledgerName("DummyLedgerName")
            .location("EastUS")
            .properties(Map.ofEntries(
                Map.entry("aadBasedSecurityPrincipals", Map.ofEntries(
                    Map.entry("ledgerRoleName", "Administrator"),
                    Map.entry("principalId", "34621747-6fc8-4771-a2eb-72f31c461f2e"),
                    Map.entry("tenantId", "bce123b9-2b7b-4975-8360-5ca0b9b1cd08")
                )),
                Map.entry("certBasedSecurityPrincipals", Map.ofEntries(
                    Map.entry("cert", "-----BEGIN CERTIFICATE-----MIIBsjCCATigAwIBAgIUZWIbyG79TniQLd2UxJuU74tqrKcwCgYIKoZIzj0EAwMwEDEOMAwGA1UEAwwFdXNlcjAwHhcNMjEwMzE2MTgwNjExWhcNMjIwMzE2MTgwNjExWjAQMQ4wDAYDVQQDDAV1c2VyMDB2MBAGByqGSM49AgEGBSuBBAAiA2IABBiWSo/j8EFit7aUMm5lF+lUmCu+IgfnpFD+7QMgLKtxRJ3aGSqgS/GpqcYVGddnODtSarNE/HyGKUFUolLPQ5ybHcouUk0kyfA7XMeSoUA4lBz63Wha8wmXo+NdBRo39qNTMFEwHQYDVR0OBBYEFPtuhrwgGjDFHeUUT4nGsXaZn69KMB8GA1UdIwQYMBaAFPtuhrwgGjDFHeUUT4nGsXaZn69KMA8GA1UdEwEB/wQFMAMBAf8wCgYIKoZIzj0EAwMDaAAwZQIxAOnozm2CyqRwSSQLls5r+mUHRGRyXHXwYtM4Dcst/VEZdmS9fqvHRCHbjUlO/+HNfgIwMWZ4FmsjD3wnPxONOm9YdVn/PRD7SsPRPbOjwBiE4EBGaHDsLjYAGDSGi7NJnSkA-----END CERTIFICATE-----"),
                    Map.entry("ledgerRoleName", "Reader")
                )),
                Map.entry("ledgerType", "Public")
            ))
            .resourceGroupName("DummyResourceGroupName")
            .tags(Map.of("additionalProps1", "additional properties"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const ledger = new azure_native.confidentialledger.Ledger("ledger", {
    ledgerName: "DummyLedgerName",
    location: "EastUS",
    properties: {
        aadBasedSecurityPrincipals: [{
            ledgerRoleName: "Administrator",
            principalId: "34621747-6fc8-4771-a2eb-72f31c461f2e",
            tenantId: "bce123b9-2b7b-4975-8360-5ca0b9b1cd08",
        }],
        certBasedSecurityPrincipals: [{
            cert: "-----BEGIN CERTIFICATE-----MIIBsjCCATigAwIBAgIUZWIbyG79TniQLd2UxJuU74tqrKcwCgYIKoZIzj0EAwMwEDEOMAwGA1UEAwwFdXNlcjAwHhcNMjEwMzE2MTgwNjExWhcNMjIwMzE2MTgwNjExWjAQMQ4wDAYDVQQDDAV1c2VyMDB2MBAGByqGSM49AgEGBSuBBAAiA2IABBiWSo/j8EFit7aUMm5lF+lUmCu+IgfnpFD+7QMgLKtxRJ3aGSqgS/GpqcYVGddnODtSarNE/HyGKUFUolLPQ5ybHcouUk0kyfA7XMeSoUA4lBz63Wha8wmXo+NdBRo39qNTMFEwHQYDVR0OBBYEFPtuhrwgGjDFHeUUT4nGsXaZn69KMB8GA1UdIwQYMBaAFPtuhrwgGjDFHeUUT4nGsXaZn69KMA8GA1UdEwEB/wQFMAMBAf8wCgYIKoZIzj0EAwMDaAAwZQIxAOnozm2CyqRwSSQLls5r+mUHRGRyXHXwYtM4Dcst/VEZdmS9fqvHRCHbjUlO/+HNfgIwMWZ4FmsjD3wnPxONOm9YdVn/PRD7SsPRPbOjwBiE4EBGaHDsLjYAGDSGi7NJnSkA-----END CERTIFICATE-----",
            ledgerRoleName: "Reader",
        }],
        ledgerType: "Public",
    },
    resourceGroupName: "DummyResourceGroupName",
    tags: {
        additionalProps1: "additional properties",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

ledger = azure_native.confidentialledger.Ledger("ledger",
    ledger_name="DummyLedgerName",
    location="EastUS",
    properties=azure_native.confidentialledger.LedgerPropertiesResponseArgs(
        aad_based_security_principals=[azure_native.confidentialledger.AADBasedSecurityPrincipalArgs(
            ledger_role_name="Administrator",
            principal_id="34621747-6fc8-4771-a2eb-72f31c461f2e",
            tenant_id="bce123b9-2b7b-4975-8360-5ca0b9b1cd08",
        )],
        cert_based_security_principals=[azure_native.confidentialledger.CertBasedSecurityPrincipalArgs(
            cert="-----BEGIN CERTIFICATE-----MIIBsjCCATigAwIBAgIUZWIbyG79TniQLd2UxJuU74tqrKcwCgYIKoZIzj0EAwMwEDEOMAwGA1UEAwwFdXNlcjAwHhcNMjEwMzE2MTgwNjExWhcNMjIwMzE2MTgwNjExWjAQMQ4wDAYDVQQDDAV1c2VyMDB2MBAGByqGSM49AgEGBSuBBAAiA2IABBiWSo/j8EFit7aUMm5lF+lUmCu+IgfnpFD+7QMgLKtxRJ3aGSqgS/GpqcYVGddnODtSarNE/HyGKUFUolLPQ5ybHcouUk0kyfA7XMeSoUA4lBz63Wha8wmXo+NdBRo39qNTMFEwHQYDVR0OBBYEFPtuhrwgGjDFHeUUT4nGsXaZn69KMB8GA1UdIwQYMBaAFPtuhrwgGjDFHeUUT4nGsXaZn69KMA8GA1UdEwEB/wQFMAMBAf8wCgYIKoZIzj0EAwMDaAAwZQIxAOnozm2CyqRwSSQLls5r+mUHRGRyXHXwYtM4Dcst/VEZdmS9fqvHRCHbjUlO/+HNfgIwMWZ4FmsjD3wnPxONOm9YdVn/PRD7SsPRPbOjwBiE4EBGaHDsLjYAGDSGi7NJnSkA-----END CERTIFICATE-----",
            ledger_role_name="Reader",
        )],
        ledger_type="Public",
    ),
    resource_group_name="DummyResourceGroupName",
    tags={
        "additionalProps1": "additional properties",
    })

```

```yaml
resources:
  ledger:
    type: azure-native:confidentialledger:Ledger
    properties:
      ledgerName: DummyLedgerName
      location: EastUS
      properties:
        aadBasedSecurityPrincipals:
          - ledgerRoleName: Administrator
            principalId: 34621747-6fc8-4771-a2eb-72f31c461f2e
            tenantId: bce123b9-2b7b-4975-8360-5ca0b9b1cd08
        certBasedSecurityPrincipals:
          - cert: '-----BEGIN CERTIFICATE-----MIIBsjCCATigAwIBAgIUZWIbyG79TniQLd2UxJuU74tqrKcwCgYIKoZIzj0EAwMwEDEOMAwGA1UEAwwFdXNlcjAwHhcNMjEwMzE2MTgwNjExWhcNMjIwMzE2MTgwNjExWjAQMQ4wDAYDVQQDDAV1c2VyMDB2MBAGByqGSM49AgEGBSuBBAAiA2IABBiWSo/j8EFit7aUMm5lF+lUmCu+IgfnpFD+7QMgLKtxRJ3aGSqgS/GpqcYVGddnODtSarNE/HyGKUFUolLPQ5ybHcouUk0kyfA7XMeSoUA4lBz63Wha8wmXo+NdBRo39qNTMFEwHQYDVR0OBBYEFPtuhrwgGjDFHeUUT4nGsXaZn69KMB8GA1UdIwQYMBaAFPtuhrwgGjDFHeUUT4nGsXaZn69KMA8GA1UdEwEB/wQFMAMBAf8wCgYIKoZIzj0EAwMDaAAwZQIxAOnozm2CyqRwSSQLls5r+mUHRGRyXHXwYtM4Dcst/VEZdmS9fqvHRCHbjUlO/+HNfgIwMWZ4FmsjD3wnPxONOm9YdVn/PRD7SsPRPbOjwBiE4EBGaHDsLjYAGDSGi7NJnSkA-----END CERTIFICATE-----'
            ledgerRoleName: Reader
        ledgerType: Public
      resourceGroupName: DummyResourceGroupName
      tags:
        additionalProps1: additional properties

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:confidentialledger:Ledger DummyLedgerName /subscriptions/00000000-0000-0000-0000-000000000001/providers/Microsoft.ConfidentialLedger/ledgers/DummyLedgerName 
```
