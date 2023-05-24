Resource information with extended details.
API Version: 2023-02-01.
Previous API Version: 2019-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a new vault or update an existing vault
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var vault = new AzureNative.KeyVault.Vault("vault", new()
    {
        Location = "westus",
        Properties = new AzureNative.KeyVault.Inputs.VaultPropertiesArgs
        {
            AccessPolicies = new[]
            {
                new AzureNative.KeyVault.Inputs.AccessPolicyEntryArgs
                {
                    ObjectId = "00000000-0000-0000-0000-000000000000",
                    Permissions = new AzureNative.KeyVault.Inputs.PermissionsArgs
                    {
                        Certificates = new[]
                        {
                            "get",
                            "list",
                            "delete",
                            "create",
                            "import",
                            "update",
                            "managecontacts",
                            "getissuers",
                            "listissuers",
                            "setissuers",
                            "deleteissuers",
                            "manageissuers",
                            "recover",
                            "purge",
                        },
                        Keys = new[]
                        {
                            "encrypt",
                            "decrypt",
                            "wrapKey",
                            "unwrapKey",
                            "sign",
                            "verify",
                            "get",
                            "list",
                            "create",
                            "update",
                            "import",
                            "delete",
                            "backup",
                            "restore",
                            "recover",
                            "purge",
                        },
                        Secrets = new[]
                        {
                            "get",
                            "list",
                            "set",
                            "delete",
                            "backup",
                            "restore",
                            "recover",
                            "purge",
                        },
                    },
                    TenantId = "00000000-0000-0000-0000-000000000000",
                },
            },
            EnabledForDeployment = true,
            EnabledForDiskEncryption = true,
            EnabledForTemplateDeployment = true,
            PublicNetworkAccess = "Enabled",
            Sku = new AzureNative.KeyVault.Inputs.SkuArgs
            {
                Family = "A",
                Name = AzureNative.KeyVault.SkuName.Standard,
            },
            TenantId = "00000000-0000-0000-0000-000000000000",
        },
        ResourceGroupName = "sample-resource-group",
        VaultName = "sample-vault",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.keyvault.Vault;
import com.pulumi.azurenative.keyvault.VaultArgs;
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
        var vault = new Vault("vault", VaultArgs.builder()        
            .location("westus")
            .properties(Map.ofEntries(
                Map.entry("accessPolicies", Map.ofEntries(
                    Map.entry("objectId", "00000000-0000-0000-0000-000000000000"),
                    Map.entry("permissions", Map.ofEntries(
                        Map.entry("certificates",                         
                            "get",
                            "list",
                            "delete",
                            "create",
                            "import",
                            "update",
                            "managecontacts",
                            "getissuers",
                            "listissuers",
                            "setissuers",
                            "deleteissuers",
                            "manageissuers",
                            "recover",
                            "purge"),
                        Map.entry("keys",                         
                            "encrypt",
                            "decrypt",
                            "wrapKey",
                            "unwrapKey",
                            "sign",
                            "verify",
                            "get",
                            "list",
                            "create",
                            "update",
                            "import",
                            "delete",
                            "backup",
                            "restore",
                            "recover",
                            "purge"),
                        Map.entry("secrets",                         
                            "get",
                            "list",
                            "set",
                            "delete",
                            "backup",
                            "restore",
                            "recover",
                            "purge")
                    )),
                    Map.entry("tenantId", "00000000-0000-0000-0000-000000000000")
                )),
                Map.entry("enabledForDeployment", true),
                Map.entry("enabledForDiskEncryption", true),
                Map.entry("enabledForTemplateDeployment", true),
                Map.entry("publicNetworkAccess", "Enabled"),
                Map.entry("sku", Map.ofEntries(
                    Map.entry("family", "A"),
                    Map.entry("name", "standard")
                )),
                Map.entry("tenantId", "00000000-0000-0000-0000-000000000000")
            ))
            .resourceGroupName("sample-resource-group")
            .vaultName("sample-vault")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const vault = new azure_native.keyvault.Vault("vault", {
    location: "westus",
    properties: {
        accessPolicies: [{
            objectId: "00000000-0000-0000-0000-000000000000",
            permissions: {
                certificates: [
                    "get",
                    "list",
                    "delete",
                    "create",
                    "import",
                    "update",
                    "managecontacts",
                    "getissuers",
                    "listissuers",
                    "setissuers",
                    "deleteissuers",
                    "manageissuers",
                    "recover",
                    "purge",
                ],
                keys: [
                    "encrypt",
                    "decrypt",
                    "wrapKey",
                    "unwrapKey",
                    "sign",
                    "verify",
                    "get",
                    "list",
                    "create",
                    "update",
                    "import",
                    "delete",
                    "backup",
                    "restore",
                    "recover",
                    "purge",
                ],
                secrets: [
                    "get",
                    "list",
                    "set",
                    "delete",
                    "backup",
                    "restore",
                    "recover",
                    "purge",
                ],
            },
            tenantId: "00000000-0000-0000-0000-000000000000",
        }],
        enabledForDeployment: true,
        enabledForDiskEncryption: true,
        enabledForTemplateDeployment: true,
        publicNetworkAccess: "Enabled",
        sku: {
            family: "A",
            name: azure_native.keyvault.SkuName.Standard,
        },
        tenantId: "00000000-0000-0000-0000-000000000000",
    },
    resourceGroupName: "sample-resource-group",
    vaultName: "sample-vault",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

vault = azure_native.keyvault.Vault("vault",
    location="westus",
    properties=azure_native.keyvault.VaultPropertiesResponseArgs(
        access_policies=[{
            "objectId": "00000000-0000-0000-0000-000000000000",
            "permissions": azure_native.keyvault.PermissionsArgs(
                certificates=[
                    "get",
                    "list",
                    "delete",
                    "create",
                    "import",
                    "update",
                    "managecontacts",
                    "getissuers",
                    "listissuers",
                    "setissuers",
                    "deleteissuers",
                    "manageissuers",
                    "recover",
                    "purge",
                ],
                keys=[
                    "encrypt",
                    "decrypt",
                    "wrapKey",
                    "unwrapKey",
                    "sign",
                    "verify",
                    "get",
                    "list",
                    "create",
                    "update",
                    "import",
                    "delete",
                    "backup",
                    "restore",
                    "recover",
                    "purge",
                ],
                secrets=[
                    "get",
                    "list",
                    "set",
                    "delete",
                    "backup",
                    "restore",
                    "recover",
                    "purge",
                ],
            ),
            "tenantId": "00000000-0000-0000-0000-000000000000",
        }],
        enabled_for_deployment=True,
        enabled_for_disk_encryption=True,
        enabled_for_template_deployment=True,
        public_network_access="Enabled",
        sku=azure_native.keyvault.SkuArgs(
            family="A",
            name=azure_native.keyvault.SkuName.STANDARD,
        ),
        tenant_id="00000000-0000-0000-0000-000000000000",
    ),
    resource_group_name="sample-resource-group",
    vault_name="sample-vault")

```

```yaml
resources:
  vault:
    type: azure-native:keyvault:Vault
    properties:
      location: westus
      properties:
        accessPolicies:
          - objectId: 00000000-0000-0000-0000-000000000000
            permissions:
              certificates:
                - get
                - list
                - delete
                - create
                - import
                - update
                - managecontacts
                - getissuers
                - listissuers
                - setissuers
                - deleteissuers
                - manageissuers
                - recover
                - purge
              keys:
                - encrypt
                - decrypt
                - wrapKey
                - unwrapKey
                - sign
                - verify
                - get
                - list
                - create
                - update
                - import
                - delete
                - backup
                - restore
                - recover
                - purge
              secrets:
                - get
                - list
                - set
                - delete
                - backup
                - restore
                - recover
                - purge
            tenantId: 00000000-0000-0000-0000-000000000000
        enabledForDeployment: true
        enabledForDiskEncryption: true
        enabledForTemplateDeployment: true
        publicNetworkAccess: Enabled
        sku:
          family: A
          name: standard
        tenantId: 00000000-0000-0000-0000-000000000000
      resourceGroupName: sample-resource-group
      vaultName: sample-vault

```

{{% /example %}}
{{% example %}}
### Create or update a vault with network acls
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var vault = new AzureNative.KeyVault.Vault("vault", new()
    {
        Location = "westus",
        Properties = new AzureNative.KeyVault.Inputs.VaultPropertiesArgs
        {
            EnabledForDeployment = true,
            EnabledForDiskEncryption = true,
            EnabledForTemplateDeployment = true,
            NetworkAcls = new AzureNative.KeyVault.Inputs.NetworkRuleSetArgs
            {
                Bypass = "AzureServices",
                DefaultAction = "Deny",
                IpRules = new[]
                {
                    new AzureNative.KeyVault.Inputs.IPRuleArgs
                    {
                        Value = "124.56.78.91",
                    },
                    new AzureNative.KeyVault.Inputs.IPRuleArgs
                    {
                        Value = "'10.91.4.0/24'",
                    },
                },
                VirtualNetworkRules = new[]
                {
                    new AzureNative.KeyVault.Inputs.VirtualNetworkRuleArgs
                    {
                        Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/subnet1",
                    },
                },
            },
            Sku = new AzureNative.KeyVault.Inputs.SkuArgs
            {
                Family = "A",
                Name = AzureNative.KeyVault.SkuName.Standard,
            },
            TenantId = "00000000-0000-0000-0000-000000000000",
        },
        ResourceGroupName = "sample-resource-group",
        VaultName = "sample-vault",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.keyvault.Vault;
import com.pulumi.azurenative.keyvault.VaultArgs;
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
        var vault = new Vault("vault", VaultArgs.builder()        
            .location("westus")
            .properties(Map.ofEntries(
                Map.entry("enabledForDeployment", true),
                Map.entry("enabledForDiskEncryption", true),
                Map.entry("enabledForTemplateDeployment", true),
                Map.entry("networkAcls", Map.ofEntries(
                    Map.entry("bypass", "AzureServices"),
                    Map.entry("defaultAction", "Deny"),
                    Map.entry("ipRules",                     
                        Map.of("value", "124.56.78.91"),
                        Map.of("value", "'10.91.4.0/24'")),
                    Map.entry("virtualNetworkRules", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/subnet1"))
                )),
                Map.entry("sku", Map.ofEntries(
                    Map.entry("family", "A"),
                    Map.entry("name", "standard")
                )),
                Map.entry("tenantId", "00000000-0000-0000-0000-000000000000")
            ))
            .resourceGroupName("sample-resource-group")
            .vaultName("sample-vault")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const vault = new azure_native.keyvault.Vault("vault", {
    location: "westus",
    properties: {
        enabledForDeployment: true,
        enabledForDiskEncryption: true,
        enabledForTemplateDeployment: true,
        networkAcls: {
            bypass: "AzureServices",
            defaultAction: "Deny",
            ipRules: [
                {
                    value: "124.56.78.91",
                },
                {
                    value: "'10.91.4.0/24'",
                },
            ],
            virtualNetworkRules: [{
                id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/subnet1",
            }],
        },
        sku: {
            family: "A",
            name: azure_native.keyvault.SkuName.Standard,
        },
        tenantId: "00000000-0000-0000-0000-000000000000",
    },
    resourceGroupName: "sample-resource-group",
    vaultName: "sample-vault",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

vault = azure_native.keyvault.Vault("vault",
    location="westus",
    properties=azure_native.keyvault.VaultPropertiesResponseArgs(
        enabled_for_deployment=True,
        enabled_for_disk_encryption=True,
        enabled_for_template_deployment=True,
        network_acls={
            "bypass": "AzureServices",
            "defaultAction": "Deny",
            "ipRules": [
                azure_native.keyvault.IPRuleArgs(
                    value="124.56.78.91",
                ),
                azure_native.keyvault.IPRuleArgs(
                    value="'10.91.4.0/24'",
                ),
            ],
            "virtualNetworkRules": [azure_native.keyvault.VirtualNetworkRuleArgs(
                id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/subnet1",
            )],
        },
        sku=azure_native.keyvault.SkuArgs(
            family="A",
            name=azure_native.keyvault.SkuName.STANDARD,
        ),
        tenant_id="00000000-0000-0000-0000-000000000000",
    ),
    resource_group_name="sample-resource-group",
    vault_name="sample-vault")

```

```yaml
resources:
  vault:
    type: azure-native:keyvault:Vault
    properties:
      location: westus
      properties:
        enabledForDeployment: true
        enabledForDiskEncryption: true
        enabledForTemplateDeployment: true
        networkAcls:
          bypass: AzureServices
          defaultAction: Deny
          ipRules:
            - value: 124.56.78.91
            - value: '''10.91.4.0/24'''
          virtualNetworkRules:
            - id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/subnet1
        sku:
          family: A
          name: standard
        tenantId: 00000000-0000-0000-0000-000000000000
      resourceGroupName: sample-resource-group
      vaultName: sample-vault

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:keyvault:Vault sample-vault /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/sample-resource-group/providers/Microsoft.KeyVault/vaults/sample-vault 
```
