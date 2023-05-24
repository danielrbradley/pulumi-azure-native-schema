A Cache instance. Follows Azure Resource Manager standards: https://github.com/Azure/azure-resource-manager-rpc/blob/master/v1.0/resource-api-reference.md
API Version: 2023-01-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Caches_CreateOrUpdate_ldap_only
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cache = new AzureNative.StorageCache.Cache("cache", new()
    {
        CacheName = "sc1",
        CacheSizeGB = 3072,
        DirectoryServicesSettings = new AzureNative.StorageCache.Inputs.CacheDirectorySettingsArgs
        {
            UsernameDownload = new AzureNative.StorageCache.Inputs.CacheUsernameDownloadSettingsArgs
            {
                Credentials = new AzureNative.StorageCache.Inputs.CacheUsernameDownloadSettingsCredentialsArgs
                {
                    BindDn = "cn=ldapadmin,dc=contosoad,dc=contoso,dc=local",
                    BindPassword = "<bindPassword>",
                },
                ExtendedGroups = true,
                LdapBaseDN = "dc=contosoad,dc=contoso,dc=local",
                LdapServer = "192.0.2.12",
                UsernameSource = "LDAP",
            },
        },
        EncryptionSettings = new AzureNative.StorageCache.Inputs.CacheEncryptionSettingsArgs
        {
            KeyEncryptionKey = new AzureNative.StorageCache.Inputs.KeyVaultKeyReferenceArgs
            {
                KeyUrl = "https://keyvault-cmk.vault.azure.net/keys/key2048/test",
                SourceVault = new AzureNative.StorageCache.Inputs.KeyVaultKeyReferenceSourceVaultArgs
                {
                    Id = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/scgroup/providers/Microsoft.KeyVault/vaults/keyvault-cmk",
                },
            },
        },
        Location = "westus",
        ResourceGroupName = "scgroup",
        SecuritySettings = new AzureNative.StorageCache.Inputs.CacheSecuritySettingsArgs
        {
            AccessPolicies = new[]
            {
                new AzureNative.StorageCache.Inputs.NfsAccessPolicyArgs
                {
                    AccessRules = new[]
                    {
                        new AzureNative.StorageCache.Inputs.NfsAccessRuleArgs
                        {
                            Access = "rw",
                            RootSquash = false,
                            Scope = "default",
                            SubmountAccess = true,
                            Suid = false,
                        },
                    },
                    Name = "default",
                },
            },
        },
        Sku = new AzureNative.StorageCache.Inputs.CacheSkuArgs
        {
            Name = "Standard_2G",
        },
        Subnet = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/scgroup/providers/Microsoft.Network/virtualNetworks/scvnet/subnets/sub1",
        Tags = 
        {
            { "Dept", "Contoso" },
        },
        UpgradeSettings = new AzureNative.StorageCache.Inputs.CacheUpgradeSettingsArgs
        {
            ScheduledTime = "2022-04-26T18:25:43.511Z",
            UpgradeScheduleEnabled = true,
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.storagecache.Cache;
import com.pulumi.azurenative.storagecache.CacheArgs;
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
        var cache = new Cache("cache", CacheArgs.builder()        
            .cacheName("sc1")
            .cacheSizeGB(3072)
            .directoryServicesSettings(Map.of("usernameDownload", Map.ofEntries(
                Map.entry("credentials", Map.ofEntries(
                    Map.entry("bindDn", "cn=ldapadmin,dc=contosoad,dc=contoso,dc=local"),
                    Map.entry("bindPassword", "<bindPassword>")
                )),
                Map.entry("extendedGroups", true),
                Map.entry("ldapBaseDN", "dc=contosoad,dc=contoso,dc=local"),
                Map.entry("ldapServer", "192.0.2.12"),
                Map.entry("usernameSource", "LDAP")
            )))
            .encryptionSettings(Map.of("keyEncryptionKey", Map.ofEntries(
                Map.entry("keyUrl", "https://keyvault-cmk.vault.azure.net/keys/key2048/test"),
                Map.entry("sourceVault", Map.of("id", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/scgroup/providers/Microsoft.KeyVault/vaults/keyvault-cmk"))
            )))
            .location("westus")
            .resourceGroupName("scgroup")
            .securitySettings(Map.of("accessPolicies", Map.ofEntries(
                Map.entry("accessRules", Map.ofEntries(
                    Map.entry("access", "rw"),
                    Map.entry("rootSquash", false),
                    Map.entry("scope", "default"),
                    Map.entry("submountAccess", true),
                    Map.entry("suid", false)
                )),
                Map.entry("name", "default")
            )))
            .sku(Map.of("name", "Standard_2G"))
            .subnet("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/scgroup/providers/Microsoft.Network/virtualNetworks/scvnet/subnets/sub1")
            .tags(Map.of("Dept", "Contoso"))
            .upgradeSettings(Map.ofEntries(
                Map.entry("scheduledTime", "2022-04-26T18:25:43.511Z"),
                Map.entry("upgradeScheduleEnabled", true)
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cache = new azure_native.storagecache.Cache("cache", {
    cacheName: "sc1",
    cacheSizeGB: 3072,
    directoryServicesSettings: {
        usernameDownload: {
            credentials: {
                bindDn: "cn=ldapadmin,dc=contosoad,dc=contoso,dc=local",
                bindPassword: "<bindPassword>",
            },
            extendedGroups: true,
            ldapBaseDN: "dc=contosoad,dc=contoso,dc=local",
            ldapServer: "192.0.2.12",
            usernameSource: "LDAP",
        },
    },
    encryptionSettings: {
        keyEncryptionKey: {
            keyUrl: "https://keyvault-cmk.vault.azure.net/keys/key2048/test",
            sourceVault: {
                id: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/scgroup/providers/Microsoft.KeyVault/vaults/keyvault-cmk",
            },
        },
    },
    location: "westus",
    resourceGroupName: "scgroup",
    securitySettings: {
        accessPolicies: [{
            accessRules: [{
                access: "rw",
                rootSquash: false,
                scope: "default",
                submountAccess: true,
                suid: false,
            }],
            name: "default",
        }],
    },
    sku: {
        name: "Standard_2G",
    },
    subnet: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/scgroup/providers/Microsoft.Network/virtualNetworks/scvnet/subnets/sub1",
    tags: {
        Dept: "Contoso",
    },
    upgradeSettings: {
        scheduledTime: "2022-04-26T18:25:43.511Z",
        upgradeScheduleEnabled: true,
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cache = azure_native.storagecache.Cache("cache",
    cache_name="sc1",
    cache_size_gb=3072,
    directory_services_settings=azure_native.storagecache.CacheDirectorySettingsResponseArgs(
        username_download={
            "credentials": azure_native.storagecache.CacheUsernameDownloadSettingsCredentialsArgs(
                bind_dn="cn=ldapadmin,dc=contosoad,dc=contoso,dc=local",
                bind_password="<bindPassword>",
            ),
            "extendedGroups": True,
            "ldapBaseDN": "dc=contosoad,dc=contoso,dc=local",
            "ldapServer": "192.0.2.12",
            "usernameSource": "LDAP",
        },
    ),
    encryption_settings=azure_native.storagecache.CacheEncryptionSettingsResponseArgs(
        key_encryption_key={
            "keyUrl": "https://keyvault-cmk.vault.azure.net/keys/key2048/test",
            "sourceVault": azure_native.storagecache.KeyVaultKeyReferenceSourceVaultArgs(
                id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/scgroup/providers/Microsoft.KeyVault/vaults/keyvault-cmk",
            ),
        },
    ),
    location="westus",
    resource_group_name="scgroup",
    security_settings=azure_native.storagecache.CacheSecuritySettingsResponseArgs(
        access_policies=[{
            "accessRules": [azure_native.storagecache.NfsAccessRuleArgs(
                access="rw",
                root_squash=False,
                scope="default",
                submount_access=True,
                suid=False,
            )],
            "name": "default",
        }],
    ),
    sku=azure_native.storagecache.CacheSkuArgs(
        name="Standard_2G",
    ),
    subnet="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/scgroup/providers/Microsoft.Network/virtualNetworks/scvnet/subnets/sub1",
    tags={
        "Dept": "Contoso",
    },
    upgrade_settings=azure_native.storagecache.CacheUpgradeSettingsArgs(
        scheduled_time="2022-04-26T18:25:43.511Z",
        upgrade_schedule_enabled=True,
    ))

```

```yaml
resources:
  cache:
    type: azure-native:storagecache:Cache
    properties:
      cacheName: sc1
      cacheSizeGB: 3072
      directoryServicesSettings:
        usernameDownload:
          credentials:
            bindDn: cn=ldapadmin,dc=contosoad,dc=contoso,dc=local
            bindPassword: <bindPassword>
          extendedGroups: true
          ldapBaseDN: dc=contosoad,dc=contoso,dc=local
          ldapServer: 192.0.2.12
          usernameSource: LDAP
      encryptionSettings:
        keyEncryptionKey:
          keyUrl: https://keyvault-cmk.vault.azure.net/keys/key2048/test
          sourceVault:
            id: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/scgroup/providers/Microsoft.KeyVault/vaults/keyvault-cmk
      location: westus
      resourceGroupName: scgroup
      securitySettings:
        accessPolicies:
          - accessRules:
              - access: rw
                rootSquash: false
                scope: default
                submountAccess: true
                suid: false
            name: default
      sku:
        name: Standard_2G
      subnet: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/scgroup/providers/Microsoft.Network/virtualNetworks/scvnet/subnets/sub1
      tags:
        Dept: Contoso
      upgradeSettings:
        scheduledTime: 2022-04-26T18:25:43.511Z
        upgradeScheduleEnabled: true

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storagecache:Cache sc1 /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/scgroup/providers/Microsoft.StorageCache/caches/sc1 
```
