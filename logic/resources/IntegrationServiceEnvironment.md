The integration service environment.
API Version: 2019-05-01.
Previous API Version: 2019-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update an integration service environment
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var integrationServiceEnvironment = new AzureNative.Logic.IntegrationServiceEnvironment("integrationServiceEnvironment", new()
    {
        IntegrationServiceEnvironmentName = "testIntegrationServiceEnvironment",
        Location = "brazilsouth",
        Properties = new AzureNative.Logic.Inputs.IntegrationServiceEnvironmentPropertiesArgs
        {
            EncryptionConfiguration = new AzureNative.Logic.Inputs.IntegrationServiceEnvironmenEncryptionConfigurationArgs
            {
                EncryptionKeyReference = new AzureNative.Logic.Inputs.IntegrationServiceEnvironmenEncryptionKeyReferenceArgs
                {
                    KeyName = "testKeyName",
                    KeyVault = new AzureNative.Logic.Inputs.ResourceReferenceArgs
                    {
                        Id = "/subscriptions/f34b22a3-2202-4fb1-b040-1332bd928c84/resourceGroups/testResourceGroup/providers/Microsoft.KeyVault/vaults/testKeyVault",
                    },
                    KeyVersion = "13b261d30b984753869902d7f47f4d55",
                },
            },
            NetworkConfiguration = new AzureNative.Logic.Inputs.NetworkConfigurationArgs
            {
                AccessEndpoint = new AzureNative.Logic.Inputs.IntegrationServiceEnvironmentAccessEndpointArgs
                {
                    Type = "Internal",
                },
                Subnets = new[]
                {
                    new AzureNative.Logic.Inputs.ResourceReferenceArgs
                    {
                        Id = "/subscriptions/f34b22a3-2202-4fb1-b040-1332bd928c84/resourceGroups/testResourceGroup/providers/Microsoft.Network/virtualNetworks/testVNET/subnets/s1",
                    },
                    new AzureNative.Logic.Inputs.ResourceReferenceArgs
                    {
                        Id = "/subscriptions/f34b22a3-2202-4fb1-b040-1332bd928c84/resourceGroups/testResourceGroup/providers/Microsoft.Network/virtualNetworks/testVNET/subnets/s2",
                    },
                    new AzureNative.Logic.Inputs.ResourceReferenceArgs
                    {
                        Id = "/subscriptions/f34b22a3-2202-4fb1-b040-1332bd928c84/resourceGroups/testResourceGroup/providers/Microsoft.Network/virtualNetworks/testVNET/subnets/s3",
                    },
                    new AzureNative.Logic.Inputs.ResourceReferenceArgs
                    {
                        Id = "/subscriptions/f34b22a3-2202-4fb1-b040-1332bd928c84/resourceGroups/testResourceGroup/providers/Microsoft.Network/virtualNetworks/testVNET/subnets/s4",
                    },
                },
            },
        },
        ResourceGroup = "testResourceGroup",
        Sku = new AzureNative.Logic.Inputs.IntegrationServiceEnvironmentSkuArgs
        {
            Capacity = 2,
            Name = "Premium",
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.logic.IntegrationServiceEnvironment;
import com.pulumi.azurenative.logic.IntegrationServiceEnvironmentArgs;
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
        var integrationServiceEnvironment = new IntegrationServiceEnvironment("integrationServiceEnvironment", IntegrationServiceEnvironmentArgs.builder()        
            .integrationServiceEnvironmentName("testIntegrationServiceEnvironment")
            .location("brazilsouth")
            .properties(Map.ofEntries(
                Map.entry("encryptionConfiguration", Map.of("encryptionKeyReference", Map.ofEntries(
                    Map.entry("keyName", "testKeyName"),
                    Map.entry("keyVault", Map.of("id", "/subscriptions/f34b22a3-2202-4fb1-b040-1332bd928c84/resourceGroups/testResourceGroup/providers/Microsoft.KeyVault/vaults/testKeyVault")),
                    Map.entry("keyVersion", "13b261d30b984753869902d7f47f4d55")
                ))),
                Map.entry("networkConfiguration", Map.ofEntries(
                    Map.entry("accessEndpoint", Map.of("type", "Internal")),
                    Map.entry("subnets",                     
                        Map.of("id", "/subscriptions/f34b22a3-2202-4fb1-b040-1332bd928c84/resourceGroups/testResourceGroup/providers/Microsoft.Network/virtualNetworks/testVNET/subnets/s1"),
                        Map.of("id", "/subscriptions/f34b22a3-2202-4fb1-b040-1332bd928c84/resourceGroups/testResourceGroup/providers/Microsoft.Network/virtualNetworks/testVNET/subnets/s2"),
                        Map.of("id", "/subscriptions/f34b22a3-2202-4fb1-b040-1332bd928c84/resourceGroups/testResourceGroup/providers/Microsoft.Network/virtualNetworks/testVNET/subnets/s3"),
                        Map.of("id", "/subscriptions/f34b22a3-2202-4fb1-b040-1332bd928c84/resourceGroups/testResourceGroup/providers/Microsoft.Network/virtualNetworks/testVNET/subnets/s4"))
                ))
            ))
            .resourceGroup("testResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 2),
                Map.entry("name", "Premium")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const integrationServiceEnvironment = new azure_native.logic.IntegrationServiceEnvironment("integrationServiceEnvironment", {
    integrationServiceEnvironmentName: "testIntegrationServiceEnvironment",
    location: "brazilsouth",
    properties: {
        encryptionConfiguration: {
            encryptionKeyReference: {
                keyName: "testKeyName",
                keyVault: {
                    id: "/subscriptions/f34b22a3-2202-4fb1-b040-1332bd928c84/resourceGroups/testResourceGroup/providers/Microsoft.KeyVault/vaults/testKeyVault",
                },
                keyVersion: "13b261d30b984753869902d7f47f4d55",
            },
        },
        networkConfiguration: {
            accessEndpoint: {
                type: "Internal",
            },
            subnets: [
                {
                    id: "/subscriptions/f34b22a3-2202-4fb1-b040-1332bd928c84/resourceGroups/testResourceGroup/providers/Microsoft.Network/virtualNetworks/testVNET/subnets/s1",
                },
                {
                    id: "/subscriptions/f34b22a3-2202-4fb1-b040-1332bd928c84/resourceGroups/testResourceGroup/providers/Microsoft.Network/virtualNetworks/testVNET/subnets/s2",
                },
                {
                    id: "/subscriptions/f34b22a3-2202-4fb1-b040-1332bd928c84/resourceGroups/testResourceGroup/providers/Microsoft.Network/virtualNetworks/testVNET/subnets/s3",
                },
                {
                    id: "/subscriptions/f34b22a3-2202-4fb1-b040-1332bd928c84/resourceGroups/testResourceGroup/providers/Microsoft.Network/virtualNetworks/testVNET/subnets/s4",
                },
            ],
        },
    },
    resourceGroup: "testResourceGroup",
    sku: {
        capacity: 2,
        name: "Premium",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

integration_service_environment = azure_native.logic.IntegrationServiceEnvironment("integrationServiceEnvironment",
    integration_service_environment_name="testIntegrationServiceEnvironment",
    location="brazilsouth",
    properties=azure_native.logic.IntegrationServiceEnvironmentPropertiesResponseArgs(
        encryption_configuration={
            "encryptionKeyReference": {
                "keyName": "testKeyName",
                "keyVault": azure_native.logic.ResourceReferenceArgs(
                    id="/subscriptions/f34b22a3-2202-4fb1-b040-1332bd928c84/resourceGroups/testResourceGroup/providers/Microsoft.KeyVault/vaults/testKeyVault",
                ),
                "keyVersion": "13b261d30b984753869902d7f47f4d55",
            },
        },
        network_configuration={
            "accessEndpoint": azure_native.logic.IntegrationServiceEnvironmentAccessEndpointArgs(
                type="Internal",
            ),
            "subnets": [
                azure_native.logic.ResourceReferenceArgs(
                    id="/subscriptions/f34b22a3-2202-4fb1-b040-1332bd928c84/resourceGroups/testResourceGroup/providers/Microsoft.Network/virtualNetworks/testVNET/subnets/s1",
                ),
                azure_native.logic.ResourceReferenceArgs(
                    id="/subscriptions/f34b22a3-2202-4fb1-b040-1332bd928c84/resourceGroups/testResourceGroup/providers/Microsoft.Network/virtualNetworks/testVNET/subnets/s2",
                ),
                azure_native.logic.ResourceReferenceArgs(
                    id="/subscriptions/f34b22a3-2202-4fb1-b040-1332bd928c84/resourceGroups/testResourceGroup/providers/Microsoft.Network/virtualNetworks/testVNET/subnets/s3",
                ),
                azure_native.logic.ResourceReferenceArgs(
                    id="/subscriptions/f34b22a3-2202-4fb1-b040-1332bd928c84/resourceGroups/testResourceGroup/providers/Microsoft.Network/virtualNetworks/testVNET/subnets/s4",
                ),
            ],
        },
    ),
    resource_group="testResourceGroup",
    sku=azure_native.logic.IntegrationServiceEnvironmentSkuArgs(
        capacity=2,
        name="Premium",
    ))

```

```yaml
resources:
  integrationServiceEnvironment:
    type: azure-native:logic:IntegrationServiceEnvironment
    properties:
      integrationServiceEnvironmentName: testIntegrationServiceEnvironment
      location: brazilsouth
      properties:
        encryptionConfiguration:
          encryptionKeyReference:
            keyName: testKeyName
            keyVault:
              id: /subscriptions/f34b22a3-2202-4fb1-b040-1332bd928c84/resourceGroups/testResourceGroup/providers/Microsoft.KeyVault/vaults/testKeyVault
            keyVersion: 13b261d30b984753869902d7f47f4d55
        networkConfiguration:
          accessEndpoint:
            type: Internal
          subnets:
            - id: /subscriptions/f34b22a3-2202-4fb1-b040-1332bd928c84/resourceGroups/testResourceGroup/providers/Microsoft.Network/virtualNetworks/testVNET/subnets/s1
            - id: /subscriptions/f34b22a3-2202-4fb1-b040-1332bd928c84/resourceGroups/testResourceGroup/providers/Microsoft.Network/virtualNetworks/testVNET/subnets/s2
            - id: /subscriptions/f34b22a3-2202-4fb1-b040-1332bd928c84/resourceGroups/testResourceGroup/providers/Microsoft.Network/virtualNetworks/testVNET/subnets/s3
            - id: /subscriptions/f34b22a3-2202-4fb1-b040-1332bd928c84/resourceGroups/testResourceGroup/providers/Microsoft.Network/virtualNetworks/testVNET/subnets/s4
      resourceGroup: testResourceGroup
      sku:
        capacity: 2
        name: Premium

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:logic:IntegrationServiceEnvironment testIntegrationServiceEnvironment /subscriptions/f34b22a3-2202-4fb1-b040-1332bd928c84/resourceGroups/testResourceGroup/providers/Microsoft.Logic/integrationServiceEnvironments/testIntegrationServiceEnvironment 
```
