NetApp account resource
API Version: 2022-09-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Accounts_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var account = new AzureNative.NetApp.Account("account", new()
    {
        AccountName = "account1",
        Location = "eastus",
        ResourceGroupName = "myRG",
    });

});


```

```go
package main

import (
	netapp "github.com/pulumi/pulumi-azure-native-sdk/netapp"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := netapp.NewAccount(ctx, "account", &netapp.AccountArgs{
			AccountName:       pulumi.String("account1"),
			Location:          pulumi.String("eastus"),
			ResourceGroupName: pulumi.String("myRG"),
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
import com.pulumi.azurenative.netapp.Account;
import com.pulumi.azurenative.netapp.AccountArgs;
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
        var account = new Account("account", AccountArgs.builder()        
            .accountName("account1")
            .location("eastus")
            .resourceGroupName("myRG")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const account = new azure_native.netapp.Account("account", {
    accountName: "account1",
    location: "eastus",
    resourceGroupName: "myRG",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

account = azure_native.netapp.Account("account",
    account_name="account1",
    location="eastus",
    resource_group_name="myRG")

```

```yaml
resources:
  account:
    type: azure-native:netapp:Account
    properties:
      accountName: account1
      location: eastus
      resourceGroupName: myRG

```

{{% /example %}}
{{% example %}}
### Accounts_CreateOrUpdateWithActiveDirectory
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var account = new AzureNative.NetApp.Account("account", new()
    {
        AccountName = "account1",
        ActiveDirectories = new[]
        {
            new AzureNative.NetApp.Inputs.ActiveDirectoryArgs
            {
                AesEncryption = true,
                Dns = "10.10.10.3, 10.10.10.4",
                Domain = "10.10.10.3",
                LdapOverTLS = false,
                LdapSigning = false,
                OrganizationalUnit = "OU=Engineering",
                Password = "ad_password",
                Site = "SiteName",
                SmbServerName = "SMBServer",
                Username = "ad_user_name",
            },
        },
        Location = "eastus",
        ResourceGroupName = "myRG",
    });

});


```

```go
package main

import (
	netapp "github.com/pulumi/pulumi-azure-native-sdk/netapp"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := netapp.NewAccount(ctx, "account", &netapp.AccountArgs{
			AccountName: pulumi.String("account1"),
			ActiveDirectories: []netapp.ActiveDirectoryArgs{
				{
					AesEncryption:      pulumi.Bool(true),
					Dns:                pulumi.String("10.10.10.3, 10.10.10.4"),
					Domain:             pulumi.String("10.10.10.3"),
					LdapOverTLS:        pulumi.Bool(false),
					LdapSigning:        pulumi.Bool(false),
					OrganizationalUnit: pulumi.String("OU=Engineering"),
					Password:           pulumi.String("ad_password"),
					Site:               pulumi.String("SiteName"),
					SmbServerName:      pulumi.String("SMBServer"),
					Username:           pulumi.String("ad_user_name"),
				},
			},
			Location:          pulumi.String("eastus"),
			ResourceGroupName: pulumi.String("myRG"),
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
import com.pulumi.azurenative.netapp.Account;
import com.pulumi.azurenative.netapp.AccountArgs;
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
        var account = new Account("account", AccountArgs.builder()        
            .accountName("account1")
            .activeDirectories(Map.ofEntries(
                Map.entry("aesEncryption", true),
                Map.entry("dns", "10.10.10.3, 10.10.10.4"),
                Map.entry("domain", "10.10.10.3"),
                Map.entry("ldapOverTLS", false),
                Map.entry("ldapSigning", false),
                Map.entry("organizationalUnit", "OU=Engineering"),
                Map.entry("password", "ad_password"),
                Map.entry("site", "SiteName"),
                Map.entry("smbServerName", "SMBServer"),
                Map.entry("username", "ad_user_name")
            ))
            .location("eastus")
            .resourceGroupName("myRG")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const account = new azure_native.netapp.Account("account", {
    accountName: "account1",
    activeDirectories: [{
        aesEncryption: true,
        dns: "10.10.10.3, 10.10.10.4",
        domain: "10.10.10.3",
        ldapOverTLS: false,
        ldapSigning: false,
        organizationalUnit: "OU=Engineering",
        password: "ad_password",
        site: "SiteName",
        smbServerName: "SMBServer",
        username: "ad_user_name",
    }],
    location: "eastus",
    resourceGroupName: "myRG",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

account = azure_native.netapp.Account("account",
    account_name="account1",
    active_directories=[azure_native.netapp.ActiveDirectoryArgs(
        aes_encryption=True,
        dns="10.10.10.3, 10.10.10.4",
        domain="10.10.10.3",
        ldap_over_tls=False,
        ldap_signing=False,
        organizational_unit="OU=Engineering",
        password="ad_password",
        site="SiteName",
        smb_server_name="SMBServer",
        username="ad_user_name",
    )],
    location="eastus",
    resource_group_name="myRG")

```

```yaml
resources:
  account:
    type: azure-native:netapp:Account
    properties:
      accountName: account1
      activeDirectories:
        - aesEncryption: true
          dns: 10.10.10.3, 10.10.10.4
          domain: 10.10.10.3
          ldapOverTLS: false
          ldapSigning: false
          organizationalUnit: OU=Engineering
          password: ad_password
          site: SiteName
          smbServerName: SMBServer
          username: ad_user_name
      location: eastus
      resourceGroupName: myRG

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:netapp:Account account1 /subscriptions/D633CC2E-722B-4AE1-B636-BBD9E4C60ED9/resourceGroups/myRG/providers/Microsoft.NetApp/netAppAccounts/account1 
```
