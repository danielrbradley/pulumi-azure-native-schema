Information about a domain.
API Version: 2022-09-01.
Previous API Version: 2020-10-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create App Service Domain
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var domain = new AzureNative.DomainRegistration.Domain("domain", new()
    {
        AuthCode = "exampleAuthCode",
        AutoRenew = true,
        Consent = new AzureNative.DomainRegistration.Inputs.DomainPurchaseConsentArgs
        {
            AgreedAt = "2021-09-10T19:30:53Z",
            AgreedBy = "192.0.2.1",
            AgreementKeys = new[]
            {
                "agreementKey1",
            },
        },
        ContactAdmin = new AzureNative.DomainRegistration.Inputs.ContactArgs
        {
            AddressMailing = new AzureNative.DomainRegistration.Inputs.AddressArgs
            {
                Address1 = "3400 State St",
                City = "Chicago",
                Country = "United States",
                PostalCode = "67098",
                State = "IL",
            },
            Email = "admin@email.com",
            Fax = "1-245-534-2242",
            JobTitle = "Admin",
            NameFirst = "John",
            NameLast = "Doe",
            NameMiddle = "",
            Organization = "Microsoft Inc.",
            Phone = "1-245-534-2242",
        },
        ContactBilling = new AzureNative.DomainRegistration.Inputs.ContactArgs
        {
            AddressMailing = new AzureNative.DomainRegistration.Inputs.AddressArgs
            {
                Address1 = "3400 State St",
                City = "Chicago",
                Country = "United States",
                PostalCode = "67098",
                State = "IL",
            },
            Email = "billing@email.com",
            Fax = "1-245-534-2242",
            JobTitle = "Billing",
            NameFirst = "John",
            NameLast = "Doe",
            NameMiddle = "",
            Organization = "Microsoft Inc.",
            Phone = "1-245-534-2242",
        },
        ContactRegistrant = new AzureNative.DomainRegistration.Inputs.ContactArgs
        {
            AddressMailing = new AzureNative.DomainRegistration.Inputs.AddressArgs
            {
                Address1 = "3400 State St",
                City = "Chicago",
                Country = "United States",
                PostalCode = "67098",
                State = "IL",
            },
            Email = "registrant@email.com",
            Fax = "1-245-534-2242",
            JobTitle = "Registrant",
            NameFirst = "John",
            NameLast = "Doe",
            NameMiddle = "",
            Organization = "Microsoft Inc.",
            Phone = "1-245-534-2242",
        },
        ContactTech = new AzureNative.DomainRegistration.Inputs.ContactArgs
        {
            AddressMailing = new AzureNative.DomainRegistration.Inputs.AddressArgs
            {
                Address1 = "3400 State St",
                City = "Chicago",
                Country = "United States",
                PostalCode = "67098",
                State = "IL",
            },
            Email = "tech@email.com",
            Fax = "1-245-534-2242",
            JobTitle = "Tech",
            NameFirst = "John",
            NameLast = "Doe",
            NameMiddle = "",
            Organization = "Microsoft Inc.",
            Phone = "1-245-534-2242",
        },
        DnsType = AzureNative.DomainRegistration.DnsType.DefaultDomainRegistrarDns,
        DomainName = "example.com",
        Location = "global",
        Privacy = false,
        ResourceGroupName = "testrg123",
        Tags = null,
    });

});


```

```go
package main

import (
	domainregistration "github.com/pulumi/pulumi-azure-native-sdk/domainregistration"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := domainregistration.NewDomain(ctx, "domain", &domainregistration.DomainArgs{
			AuthCode:  pulumi.String("exampleAuthCode"),
			AutoRenew: pulumi.Bool(true),
			Consent: &domainregistration.DomainPurchaseConsentArgs{
				AgreedAt: pulumi.String("2021-09-10T19:30:53Z"),
				AgreedBy: pulumi.String("192.0.2.1"),
				AgreementKeys: pulumi.StringArray{
					pulumi.String("agreementKey1"),
				},
			},
			ContactAdmin: &domainregistration.ContactArgs{
				AddressMailing: &domainregistration.AddressArgs{
					Address1:   pulumi.String("3400 State St"),
					City:       pulumi.String("Chicago"),
					Country:    pulumi.String("United States"),
					PostalCode: pulumi.String("67098"),
					State:      pulumi.String("IL"),
				},
				Email:        pulumi.String("admin@email.com"),
				Fax:          pulumi.String("1-245-534-2242"),
				JobTitle:     pulumi.String("Admin"),
				NameFirst:    pulumi.String("John"),
				NameLast:     pulumi.String("Doe"),
				NameMiddle:   pulumi.String(""),
				Organization: pulumi.String("Microsoft Inc."),
				Phone:        pulumi.String("1-245-534-2242"),
			},
			ContactBilling: &domainregistration.ContactArgs{
				AddressMailing: &domainregistration.AddressArgs{
					Address1:   pulumi.String("3400 State St"),
					City:       pulumi.String("Chicago"),
					Country:    pulumi.String("United States"),
					PostalCode: pulumi.String("67098"),
					State:      pulumi.String("IL"),
				},
				Email:        pulumi.String("billing@email.com"),
				Fax:          pulumi.String("1-245-534-2242"),
				JobTitle:     pulumi.String("Billing"),
				NameFirst:    pulumi.String("John"),
				NameLast:     pulumi.String("Doe"),
				NameMiddle:   pulumi.String(""),
				Organization: pulumi.String("Microsoft Inc."),
				Phone:        pulumi.String("1-245-534-2242"),
			},
			ContactRegistrant: &domainregistration.ContactArgs{
				AddressMailing: &domainregistration.AddressArgs{
					Address1:   pulumi.String("3400 State St"),
					City:       pulumi.String("Chicago"),
					Country:    pulumi.String("United States"),
					PostalCode: pulumi.String("67098"),
					State:      pulumi.String("IL"),
				},
				Email:        pulumi.String("registrant@email.com"),
				Fax:          pulumi.String("1-245-534-2242"),
				JobTitle:     pulumi.String("Registrant"),
				NameFirst:    pulumi.String("John"),
				NameLast:     pulumi.String("Doe"),
				NameMiddle:   pulumi.String(""),
				Organization: pulumi.String("Microsoft Inc."),
				Phone:        pulumi.String("1-245-534-2242"),
			},
			ContactTech: &domainregistration.ContactArgs{
				AddressMailing: &domainregistration.AddressArgs{
					Address1:   pulumi.String("3400 State St"),
					City:       pulumi.String("Chicago"),
					Country:    pulumi.String("United States"),
					PostalCode: pulumi.String("67098"),
					State:      pulumi.String("IL"),
				},
				Email:        pulumi.String("tech@email.com"),
				Fax:          pulumi.String("1-245-534-2242"),
				JobTitle:     pulumi.String("Tech"),
				NameFirst:    pulumi.String("John"),
				NameLast:     pulumi.String("Doe"),
				NameMiddle:   pulumi.String(""),
				Organization: pulumi.String("Microsoft Inc."),
				Phone:        pulumi.String("1-245-534-2242"),
			},
			DnsType:           domainregistration.DnsTypeDefaultDomainRegistrarDns,
			DomainName:        pulumi.String("example.com"),
			Location:          pulumi.String("global"),
			Privacy:           pulumi.Bool(false),
			ResourceGroupName: pulumi.String("testrg123"),
			Tags:              nil,
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
import com.pulumi.azurenative.domainregistration.Domain;
import com.pulumi.azurenative.domainregistration.DomainArgs;
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
        var domain = new Domain("domain", DomainArgs.builder()        
            .authCode("exampleAuthCode")
            .autoRenew(true)
            .consent(Map.ofEntries(
                Map.entry("agreedAt", "2021-09-10T19:30:53Z"),
                Map.entry("agreedBy", "192.0.2.1"),
                Map.entry("agreementKeys", "agreementKey1")
            ))
            .contactAdmin(Map.ofEntries(
                Map.entry("addressMailing", Map.ofEntries(
                    Map.entry("address1", "3400 State St"),
                    Map.entry("city", "Chicago"),
                    Map.entry("country", "United States"),
                    Map.entry("postalCode", "67098"),
                    Map.entry("state", "IL")
                )),
                Map.entry("email", "admin@email.com"),
                Map.entry("fax", "1-245-534-2242"),
                Map.entry("jobTitle", "Admin"),
                Map.entry("nameFirst", "John"),
                Map.entry("nameLast", "Doe"),
                Map.entry("nameMiddle", ""),
                Map.entry("organization", "Microsoft Inc."),
                Map.entry("phone", "1-245-534-2242")
            ))
            .contactBilling(Map.ofEntries(
                Map.entry("addressMailing", Map.ofEntries(
                    Map.entry("address1", "3400 State St"),
                    Map.entry("city", "Chicago"),
                    Map.entry("country", "United States"),
                    Map.entry("postalCode", "67098"),
                    Map.entry("state", "IL")
                )),
                Map.entry("email", "billing@email.com"),
                Map.entry("fax", "1-245-534-2242"),
                Map.entry("jobTitle", "Billing"),
                Map.entry("nameFirst", "John"),
                Map.entry("nameLast", "Doe"),
                Map.entry("nameMiddle", ""),
                Map.entry("organization", "Microsoft Inc."),
                Map.entry("phone", "1-245-534-2242")
            ))
            .contactRegistrant(Map.ofEntries(
                Map.entry("addressMailing", Map.ofEntries(
                    Map.entry("address1", "3400 State St"),
                    Map.entry("city", "Chicago"),
                    Map.entry("country", "United States"),
                    Map.entry("postalCode", "67098"),
                    Map.entry("state", "IL")
                )),
                Map.entry("email", "registrant@email.com"),
                Map.entry("fax", "1-245-534-2242"),
                Map.entry("jobTitle", "Registrant"),
                Map.entry("nameFirst", "John"),
                Map.entry("nameLast", "Doe"),
                Map.entry("nameMiddle", ""),
                Map.entry("organization", "Microsoft Inc."),
                Map.entry("phone", "1-245-534-2242")
            ))
            .contactTech(Map.ofEntries(
                Map.entry("addressMailing", Map.ofEntries(
                    Map.entry("address1", "3400 State St"),
                    Map.entry("city", "Chicago"),
                    Map.entry("country", "United States"),
                    Map.entry("postalCode", "67098"),
                    Map.entry("state", "IL")
                )),
                Map.entry("email", "tech@email.com"),
                Map.entry("fax", "1-245-534-2242"),
                Map.entry("jobTitle", "Tech"),
                Map.entry("nameFirst", "John"),
                Map.entry("nameLast", "Doe"),
                Map.entry("nameMiddle", ""),
                Map.entry("organization", "Microsoft Inc."),
                Map.entry("phone", "1-245-534-2242")
            ))
            .dnsType("DefaultDomainRegistrarDns")
            .domainName("example.com")
            .location("global")
            .privacy(false)
            .resourceGroupName("testrg123")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const domain = new azure_native.domainregistration.Domain("domain", {
    authCode: "exampleAuthCode",
    autoRenew: true,
    consent: {
        agreedAt: "2021-09-10T19:30:53Z",
        agreedBy: "192.0.2.1",
        agreementKeys: ["agreementKey1"],
    },
    contactAdmin: {
        addressMailing: {
            address1: "3400 State St",
            city: "Chicago",
            country: "United States",
            postalCode: "67098",
            state: "IL",
        },
        email: "admin@email.com",
        fax: "1-245-534-2242",
        jobTitle: "Admin",
        nameFirst: "John",
        nameLast: "Doe",
        nameMiddle: "",
        organization: "Microsoft Inc.",
        phone: "1-245-534-2242",
    },
    contactBilling: {
        addressMailing: {
            address1: "3400 State St",
            city: "Chicago",
            country: "United States",
            postalCode: "67098",
            state: "IL",
        },
        email: "billing@email.com",
        fax: "1-245-534-2242",
        jobTitle: "Billing",
        nameFirst: "John",
        nameLast: "Doe",
        nameMiddle: "",
        organization: "Microsoft Inc.",
        phone: "1-245-534-2242",
    },
    contactRegistrant: {
        addressMailing: {
            address1: "3400 State St",
            city: "Chicago",
            country: "United States",
            postalCode: "67098",
            state: "IL",
        },
        email: "registrant@email.com",
        fax: "1-245-534-2242",
        jobTitle: "Registrant",
        nameFirst: "John",
        nameLast: "Doe",
        nameMiddle: "",
        organization: "Microsoft Inc.",
        phone: "1-245-534-2242",
    },
    contactTech: {
        addressMailing: {
            address1: "3400 State St",
            city: "Chicago",
            country: "United States",
            postalCode: "67098",
            state: "IL",
        },
        email: "tech@email.com",
        fax: "1-245-534-2242",
        jobTitle: "Tech",
        nameFirst: "John",
        nameLast: "Doe",
        nameMiddle: "",
        organization: "Microsoft Inc.",
        phone: "1-245-534-2242",
    },
    dnsType: azure_native.domainregistration.DnsType.DefaultDomainRegistrarDns,
    domainName: "example.com",
    location: "global",
    privacy: false,
    resourceGroupName: "testrg123",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

domain = azure_native.domainregistration.Domain("domain",
    auth_code="exampleAuthCode",
    auto_renew=True,
    consent=azure_native.domainregistration.DomainPurchaseConsentArgs(
        agreed_at="2021-09-10T19:30:53Z",
        agreed_by="192.0.2.1",
        agreement_keys=["agreementKey1"],
    ),
    contact_admin=azure_native.domainregistration.ContactArgs(
        address_mailing=azure_native.domainregistration.AddressArgs(
            address1="3400 State St",
            city="Chicago",
            country="United States",
            postal_code="67098",
            state="IL",
        ),
        email="admin@email.com",
        fax="1-245-534-2242",
        job_title="Admin",
        name_first="John",
        name_last="Doe",
        name_middle="",
        organization="Microsoft Inc.",
        phone="1-245-534-2242",
    ),
    contact_billing=azure_native.domainregistration.ContactArgs(
        address_mailing=azure_native.domainregistration.AddressArgs(
            address1="3400 State St",
            city="Chicago",
            country="United States",
            postal_code="67098",
            state="IL",
        ),
        email="billing@email.com",
        fax="1-245-534-2242",
        job_title="Billing",
        name_first="John",
        name_last="Doe",
        name_middle="",
        organization="Microsoft Inc.",
        phone="1-245-534-2242",
    ),
    contact_registrant=azure_native.domainregistration.ContactArgs(
        address_mailing=azure_native.domainregistration.AddressArgs(
            address1="3400 State St",
            city="Chicago",
            country="United States",
            postal_code="67098",
            state="IL",
        ),
        email="registrant@email.com",
        fax="1-245-534-2242",
        job_title="Registrant",
        name_first="John",
        name_last="Doe",
        name_middle="",
        organization="Microsoft Inc.",
        phone="1-245-534-2242",
    ),
    contact_tech=azure_native.domainregistration.ContactArgs(
        address_mailing=azure_native.domainregistration.AddressArgs(
            address1="3400 State St",
            city="Chicago",
            country="United States",
            postal_code="67098",
            state="IL",
        ),
        email="tech@email.com",
        fax="1-245-534-2242",
        job_title="Tech",
        name_first="John",
        name_last="Doe",
        name_middle="",
        organization="Microsoft Inc.",
        phone="1-245-534-2242",
    ),
    dns_type=azure_native.domainregistration.DnsType.DEFAULT_DOMAIN_REGISTRAR_DNS,
    domain_name="example.com",
    location="global",
    privacy=False,
    resource_group_name="testrg123",
    tags={})

```

```yaml
resources:
  domain:
    type: azure-native:domainregistration:Domain
    properties:
      authCode: exampleAuthCode
      autoRenew: true
      consent:
        agreedAt: 2021-09-10T19:30:53Z
        agreedBy: 192.0.2.1
        agreementKeys:
          - agreementKey1
      contactAdmin:
        addressMailing:
          address1: 3400 State St
          city: Chicago
          country: United States
          postalCode: '67098'
          state: IL
        email: admin@email.com
        fax: 1-245-534-2242
        jobTitle: Admin
        nameFirst: John
        nameLast: Doe
        nameMiddle:
        organization: Microsoft Inc.
        phone: 1-245-534-2242
      contactBilling:
        addressMailing:
          address1: 3400 State St
          city: Chicago
          country: United States
          postalCode: '67098'
          state: IL
        email: billing@email.com
        fax: 1-245-534-2242
        jobTitle: Billing
        nameFirst: John
        nameLast: Doe
        nameMiddle:
        organization: Microsoft Inc.
        phone: 1-245-534-2242
      contactRegistrant:
        addressMailing:
          address1: 3400 State St
          city: Chicago
          country: United States
          postalCode: '67098'
          state: IL
        email: registrant@email.com
        fax: 1-245-534-2242
        jobTitle: Registrant
        nameFirst: John
        nameLast: Doe
        nameMiddle:
        organization: Microsoft Inc.
        phone: 1-245-534-2242
      contactTech:
        addressMailing:
          address1: 3400 State St
          city: Chicago
          country: United States
          postalCode: '67098'
          state: IL
        email: tech@email.com
        fax: 1-245-534-2242
        jobTitle: Tech
        nameFirst: John
        nameLast: Doe
        nameMiddle:
        organization: Microsoft Inc.
        phone: 1-245-534-2242
      dnsType: DefaultDomainRegistrarDns
      domainName: example.com
      location: global
      privacy: false
      resourceGroupName: testrg123
      tags: {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:domainregistration:Domain example.com /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.DomainRegistration/domains/example.com 
```
