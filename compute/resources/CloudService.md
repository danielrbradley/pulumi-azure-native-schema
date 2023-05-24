Describes the cloud service.
API Version: 2022-09-04.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create New Cloud Service with Multiple Roles
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cloudService = new AzureNative.Compute.CloudService("cloudService", new()
    {
        CloudServiceName = "{cs-name}",
        Location = "westus",
        Properties = new AzureNative.Compute.Inputs.CloudServicePropertiesArgs
        {
            Configuration = "{ServiceConfiguration}",
            NetworkProfile = new AzureNative.Compute.Inputs.CloudServiceNetworkProfileArgs
            {
                LoadBalancerConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.LoadBalancerConfigurationArgs
                    {
                        Name = "contosolb",
                        Properties = new AzureNative.Compute.Inputs.LoadBalancerConfigurationPropertiesArgs
                        {
                            FrontendIpConfigurations = new[]
                            {
                                new AzureNative.Compute.Inputs.LoadBalancerFrontendIpConfigurationArgs
                                {
                                    Name = "contosofe",
                                    Properties = new AzureNative.Compute.Inputs.LoadBalancerFrontendIpConfigurationPropertiesArgs
                                    {
                                        PublicIPAddress = new AzureNative.Compute.Inputs.SubResourceArgs
                                        {
                                            Id = "/subscriptions/{subscription-id}/resourceGroups/ConstosoRG/providers/Microsoft.Network/publicIPAddresses/contosopublicip",
                                        },
                                    },
                                },
                            },
                        },
                    },
                },
            },
            PackageUrl = "{PackageUrl}",
            RoleProfile = new AzureNative.Compute.Inputs.CloudServiceRoleProfileArgs
            {
                Roles = new[]
                {
                    new AzureNative.Compute.Inputs.CloudServiceRoleProfilePropertiesArgs
                    {
                        Name = "ContosoFrontend",
                        Sku = new AzureNative.Compute.Inputs.CloudServiceRoleSkuArgs
                        {
                            Capacity = 1,
                            Name = "Standard_D1_v2",
                            Tier = "Standard",
                        },
                    },
                    new AzureNative.Compute.Inputs.CloudServiceRoleProfilePropertiesArgs
                    {
                        Name = "ContosoBackend",
                        Sku = new AzureNative.Compute.Inputs.CloudServiceRoleSkuArgs
                        {
                            Capacity = 1,
                            Name = "Standard_D1_v2",
                            Tier = "Standard",
                        },
                    },
                },
            },
            UpgradeMode = "Auto",
        },
        ResourceGroupName = "ConstosoRG",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.CloudService;
import com.pulumi.azurenative.compute.CloudServiceArgs;
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
        var cloudService = new CloudService("cloudService", CloudServiceArgs.builder()        
            .cloudServiceName("{cs-name}")
            .location("westus")
            .properties(Map.ofEntries(
                Map.entry("configuration", "{ServiceConfiguration}"),
                Map.entry("networkProfile", Map.of("loadBalancerConfigurations", Map.ofEntries(
                    Map.entry("name", "contosolb"),
                    Map.entry("properties", Map.of("frontendIpConfigurations", Map.ofEntries(
                        Map.entry("name", "contosofe"),
                        Map.entry("properties", Map.of("publicIPAddress", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/ConstosoRG/providers/Microsoft.Network/publicIPAddresses/contosopublicip")))
                    )))
                ))),
                Map.entry("packageUrl", "{PackageUrl}"),
                Map.entry("roleProfile", Map.of("roles",                 
                    Map.ofEntries(
                        Map.entry("name", "ContosoFrontend"),
                        Map.entry("sku", Map.ofEntries(
                            Map.entry("capacity", 1),
                            Map.entry("name", "Standard_D1_v2"),
                            Map.entry("tier", "Standard")
                        ))
                    ),
                    Map.ofEntries(
                        Map.entry("name", "ContosoBackend"),
                        Map.entry("sku", Map.ofEntries(
                            Map.entry("capacity", 1),
                            Map.entry("name", "Standard_D1_v2"),
                            Map.entry("tier", "Standard")
                        ))
                    ))),
                Map.entry("upgradeMode", "Auto")
            ))
            .resourceGroupName("ConstosoRG")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cloudService = new azure_native.compute.CloudService("cloudService", {
    cloudServiceName: "{cs-name}",
    location: "westus",
    properties: {
        configuration: "{ServiceConfiguration}",
        networkProfile: {
            loadBalancerConfigurations: [{
                name: "contosolb",
                properties: {
                    frontendIpConfigurations: [{
                        name: "contosofe",
                        properties: {
                            publicIPAddress: {
                                id: "/subscriptions/{subscription-id}/resourceGroups/ConstosoRG/providers/Microsoft.Network/publicIPAddresses/contosopublicip",
                            },
                        },
                    }],
                },
            }],
        },
        packageUrl: "{PackageUrl}",
        roleProfile: {
            roles: [
                {
                    name: "ContosoFrontend",
                    sku: {
                        capacity: 1,
                        name: "Standard_D1_v2",
                        tier: "Standard",
                    },
                },
                {
                    name: "ContosoBackend",
                    sku: {
                        capacity: 1,
                        name: "Standard_D1_v2",
                        tier: "Standard",
                    },
                },
            ],
        },
        upgradeMode: "Auto",
    },
    resourceGroupName: "ConstosoRG",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cloud_service = azure_native.compute.CloudService("cloudService",
    cloud_service_name="{cs-name}",
    location="westus",
    properties=azure_native.compute.CloudServicePropertiesResponseArgs(
        configuration="{ServiceConfiguration}",
        network_profile={
            "loadBalancerConfigurations": [{
                "name": "contosolb",
                "properties": {
                    "frontendIpConfigurations": [{
                        "name": "contosofe",
                        "properties": {
                            "publicIPAddress": azure_native.compute.SubResourceArgs(
                                id="/subscriptions/{subscription-id}/resourceGroups/ConstosoRG/providers/Microsoft.Network/publicIPAddresses/contosopublicip",
                            ),
                        },
                    }],
                },
            }],
        },
        package_url="{PackageUrl}",
        role_profile={
            "roles": [
                {
                    "name": "ContosoFrontend",
                    "sku": azure_native.compute.CloudServiceRoleSkuArgs(
                        capacity=1,
                        name="Standard_D1_v2",
                        tier="Standard",
                    ),
                },
                {
                    "name": "ContosoBackend",
                    "sku": azure_native.compute.CloudServiceRoleSkuArgs(
                        capacity=1,
                        name="Standard_D1_v2",
                        tier="Standard",
                    ),
                },
            ],
        },
        upgrade_mode="Auto",
    ),
    resource_group_name="ConstosoRG")

```

```yaml
resources:
  cloudService:
    type: azure-native:compute:CloudService
    properties:
      cloudServiceName: '{cs-name}'
      location: westus
      properties:
        configuration: '{ServiceConfiguration}'
        networkProfile:
          loadBalancerConfigurations:
            - name: contosolb
              properties:
                frontendIpConfigurations:
                  - name: contosofe
                    properties:
                      publicIPAddress:
                        id: /subscriptions/{subscription-id}/resourceGroups/ConstosoRG/providers/Microsoft.Network/publicIPAddresses/contosopublicip
        packageUrl: '{PackageUrl}'
        roleProfile:
          roles:
            - name: ContosoFrontend
              sku:
                capacity: 1
                name: Standard_D1_v2
                tier: Standard
            - name: ContosoBackend
              sku:
                capacity: 1
                name: Standard_D1_v2
                tier: Standard
        upgradeMode: Auto
      resourceGroupName: ConstosoRG

```

{{% /example %}}
{{% example %}}
### Create New Cloud Service with Multiple Roles in a specific availability zone
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cloudService = new AzureNative.Compute.CloudService("cloudService", new()
    {
        CloudServiceName = "{cs-name}",
        Location = "westus",
        Properties = new AzureNative.Compute.Inputs.CloudServicePropertiesArgs
        {
            Configuration = "{ServiceConfiguration}",
            NetworkProfile = new AzureNative.Compute.Inputs.CloudServiceNetworkProfileArgs
            {
                LoadBalancerConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.LoadBalancerConfigurationArgs
                    {
                        Name = "contosolb",
                        Properties = new AzureNative.Compute.Inputs.LoadBalancerConfigurationPropertiesArgs
                        {
                            FrontendIpConfigurations = new[]
                            {
                                new AzureNative.Compute.Inputs.LoadBalancerFrontendIpConfigurationArgs
                                {
                                    Name = "contosofe",
                                    Properties = new AzureNative.Compute.Inputs.LoadBalancerFrontendIpConfigurationPropertiesArgs
                                    {
                                        PublicIPAddress = new AzureNative.Compute.Inputs.SubResourceArgs
                                        {
                                            Id = "/subscriptions/{subscription-id}/resourceGroups/ConstosoRG/providers/Microsoft.Network/publicIPAddresses/contosopublicip",
                                        },
                                    },
                                },
                            },
                        },
                    },
                },
            },
            PackageUrl = "{PackageUrl}",
            RoleProfile = new AzureNative.Compute.Inputs.CloudServiceRoleProfileArgs
            {
                Roles = new[]
                {
                    new AzureNative.Compute.Inputs.CloudServiceRoleProfilePropertiesArgs
                    {
                        Name = "ContosoFrontend",
                        Sku = new AzureNative.Compute.Inputs.CloudServiceRoleSkuArgs
                        {
                            Capacity = 1,
                            Name = "Standard_D1_v2",
                            Tier = "Standard",
                        },
                    },
                    new AzureNative.Compute.Inputs.CloudServiceRoleProfilePropertiesArgs
                    {
                        Name = "ContosoBackend",
                        Sku = new AzureNative.Compute.Inputs.CloudServiceRoleSkuArgs
                        {
                            Capacity = 1,
                            Name = "Standard_D1_v2",
                            Tier = "Standard",
                        },
                    },
                },
            },
            UpgradeMode = "Auto",
        },
        ResourceGroupName = "ConstosoRG",
        Zones = new[]
        {
            "1",
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.CloudService;
import com.pulumi.azurenative.compute.CloudServiceArgs;
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
        var cloudService = new CloudService("cloudService", CloudServiceArgs.builder()        
            .cloudServiceName("{cs-name}")
            .location("westus")
            .properties(Map.ofEntries(
                Map.entry("configuration", "{ServiceConfiguration}"),
                Map.entry("networkProfile", Map.of("loadBalancerConfigurations", Map.ofEntries(
                    Map.entry("name", "contosolb"),
                    Map.entry("properties", Map.of("frontendIpConfigurations", Map.ofEntries(
                        Map.entry("name", "contosofe"),
                        Map.entry("properties", Map.of("publicIPAddress", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/ConstosoRG/providers/Microsoft.Network/publicIPAddresses/contosopublicip")))
                    )))
                ))),
                Map.entry("packageUrl", "{PackageUrl}"),
                Map.entry("roleProfile", Map.of("roles",                 
                    Map.ofEntries(
                        Map.entry("name", "ContosoFrontend"),
                        Map.entry("sku", Map.ofEntries(
                            Map.entry("capacity", 1),
                            Map.entry("name", "Standard_D1_v2"),
                            Map.entry("tier", "Standard")
                        ))
                    ),
                    Map.ofEntries(
                        Map.entry("name", "ContosoBackend"),
                        Map.entry("sku", Map.ofEntries(
                            Map.entry("capacity", 1),
                            Map.entry("name", "Standard_D1_v2"),
                            Map.entry("tier", "Standard")
                        ))
                    ))),
                Map.entry("upgradeMode", "Auto")
            ))
            .resourceGroupName("ConstosoRG")
            .zones("1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cloudService = new azure_native.compute.CloudService("cloudService", {
    cloudServiceName: "{cs-name}",
    location: "westus",
    properties: {
        configuration: "{ServiceConfiguration}",
        networkProfile: {
            loadBalancerConfigurations: [{
                name: "contosolb",
                properties: {
                    frontendIpConfigurations: [{
                        name: "contosofe",
                        properties: {
                            publicIPAddress: {
                                id: "/subscriptions/{subscription-id}/resourceGroups/ConstosoRG/providers/Microsoft.Network/publicIPAddresses/contosopublicip",
                            },
                        },
                    }],
                },
            }],
        },
        packageUrl: "{PackageUrl}",
        roleProfile: {
            roles: [
                {
                    name: "ContosoFrontend",
                    sku: {
                        capacity: 1,
                        name: "Standard_D1_v2",
                        tier: "Standard",
                    },
                },
                {
                    name: "ContosoBackend",
                    sku: {
                        capacity: 1,
                        name: "Standard_D1_v2",
                        tier: "Standard",
                    },
                },
            ],
        },
        upgradeMode: "Auto",
    },
    resourceGroupName: "ConstosoRG",
    zones: ["1"],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cloud_service = azure_native.compute.CloudService("cloudService",
    cloud_service_name="{cs-name}",
    location="westus",
    properties=azure_native.compute.CloudServicePropertiesResponseArgs(
        configuration="{ServiceConfiguration}",
        network_profile={
            "loadBalancerConfigurations": [{
                "name": "contosolb",
                "properties": {
                    "frontendIpConfigurations": [{
                        "name": "contosofe",
                        "properties": {
                            "publicIPAddress": azure_native.compute.SubResourceArgs(
                                id="/subscriptions/{subscription-id}/resourceGroups/ConstosoRG/providers/Microsoft.Network/publicIPAddresses/contosopublicip",
                            ),
                        },
                    }],
                },
            }],
        },
        package_url="{PackageUrl}",
        role_profile={
            "roles": [
                {
                    "name": "ContosoFrontend",
                    "sku": azure_native.compute.CloudServiceRoleSkuArgs(
                        capacity=1,
                        name="Standard_D1_v2",
                        tier="Standard",
                    ),
                },
                {
                    "name": "ContosoBackend",
                    "sku": azure_native.compute.CloudServiceRoleSkuArgs(
                        capacity=1,
                        name="Standard_D1_v2",
                        tier="Standard",
                    ),
                },
            ],
        },
        upgrade_mode="Auto",
    ),
    resource_group_name="ConstosoRG",
    zones=["1"])

```

```yaml
resources:
  cloudService:
    type: azure-native:compute:CloudService
    properties:
      cloudServiceName: '{cs-name}'
      location: westus
      properties:
        configuration: '{ServiceConfiguration}'
        networkProfile:
          loadBalancerConfigurations:
            - name: contosolb
              properties:
                frontendIpConfigurations:
                  - name: contosofe
                    properties:
                      publicIPAddress:
                        id: /subscriptions/{subscription-id}/resourceGroups/ConstosoRG/providers/Microsoft.Network/publicIPAddresses/contosopublicip
        packageUrl: '{PackageUrl}'
        roleProfile:
          roles:
            - name: ContosoFrontend
              sku:
                capacity: 1
                name: Standard_D1_v2
                tier: Standard
            - name: ContosoBackend
              sku:
                capacity: 1
                name: Standard_D1_v2
                tier: Standard
        upgradeMode: Auto
      resourceGroupName: ConstosoRG
      zones:
        - '1'

```

{{% /example %}}
{{% example %}}
### Create New Cloud Service with Single Role
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cloudService = new AzureNative.Compute.CloudService("cloudService", new()
    {
        CloudServiceName = "{cs-name}",
        Location = "westus",
        Properties = new AzureNative.Compute.Inputs.CloudServicePropertiesArgs
        {
            Configuration = "{ServiceConfiguration}",
            NetworkProfile = new AzureNative.Compute.Inputs.CloudServiceNetworkProfileArgs
            {
                LoadBalancerConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.LoadBalancerConfigurationArgs
                    {
                        Name = "myLoadBalancer",
                        Properties = new AzureNative.Compute.Inputs.LoadBalancerConfigurationPropertiesArgs
                        {
                            FrontendIpConfigurations = new[]
                            {
                                new AzureNative.Compute.Inputs.LoadBalancerFrontendIpConfigurationArgs
                                {
                                    Name = "myfe",
                                    Properties = new AzureNative.Compute.Inputs.LoadBalancerFrontendIpConfigurationPropertiesArgs
                                    {
                                        PublicIPAddress = new AzureNative.Compute.Inputs.SubResourceArgs
                                        {
                                            Id = "/subscriptions/{subscription-id}/resourceGroups/ConstosoRG/providers/Microsoft.Network/publicIPAddresses/myPublicIP",
                                        },
                                    },
                                },
                            },
                        },
                    },
                },
            },
            PackageUrl = "{PackageUrl}",
            RoleProfile = new AzureNative.Compute.Inputs.CloudServiceRoleProfileArgs
            {
                Roles = new[]
                {
                    new AzureNative.Compute.Inputs.CloudServiceRoleProfilePropertiesArgs
                    {
                        Name = "ContosoFrontend",
                        Sku = new AzureNative.Compute.Inputs.CloudServiceRoleSkuArgs
                        {
                            Capacity = 1,
                            Name = "Standard_D1_v2",
                            Tier = "Standard",
                        },
                    },
                },
            },
            UpgradeMode = "Auto",
        },
        ResourceGroupName = "ConstosoRG",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.CloudService;
import com.pulumi.azurenative.compute.CloudServiceArgs;
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
        var cloudService = new CloudService("cloudService", CloudServiceArgs.builder()        
            .cloudServiceName("{cs-name}")
            .location("westus")
            .properties(Map.ofEntries(
                Map.entry("configuration", "{ServiceConfiguration}"),
                Map.entry("networkProfile", Map.of("loadBalancerConfigurations", Map.ofEntries(
                    Map.entry("name", "myLoadBalancer"),
                    Map.entry("properties", Map.of("frontendIpConfigurations", Map.ofEntries(
                        Map.entry("name", "myfe"),
                        Map.entry("properties", Map.of("publicIPAddress", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/ConstosoRG/providers/Microsoft.Network/publicIPAddresses/myPublicIP")))
                    )))
                ))),
                Map.entry("packageUrl", "{PackageUrl}"),
                Map.entry("roleProfile", Map.of("roles", Map.ofEntries(
                    Map.entry("name", "ContosoFrontend"),
                    Map.entry("sku", Map.ofEntries(
                        Map.entry("capacity", 1),
                        Map.entry("name", "Standard_D1_v2"),
                        Map.entry("tier", "Standard")
                    ))
                ))),
                Map.entry("upgradeMode", "Auto")
            ))
            .resourceGroupName("ConstosoRG")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cloudService = new azure_native.compute.CloudService("cloudService", {
    cloudServiceName: "{cs-name}",
    location: "westus",
    properties: {
        configuration: "{ServiceConfiguration}",
        networkProfile: {
            loadBalancerConfigurations: [{
                name: "myLoadBalancer",
                properties: {
                    frontendIpConfigurations: [{
                        name: "myfe",
                        properties: {
                            publicIPAddress: {
                                id: "/subscriptions/{subscription-id}/resourceGroups/ConstosoRG/providers/Microsoft.Network/publicIPAddresses/myPublicIP",
                            },
                        },
                    }],
                },
            }],
        },
        packageUrl: "{PackageUrl}",
        roleProfile: {
            roles: [{
                name: "ContosoFrontend",
                sku: {
                    capacity: 1,
                    name: "Standard_D1_v2",
                    tier: "Standard",
                },
            }],
        },
        upgradeMode: "Auto",
    },
    resourceGroupName: "ConstosoRG",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cloud_service = azure_native.compute.CloudService("cloudService",
    cloud_service_name="{cs-name}",
    location="westus",
    properties=azure_native.compute.CloudServicePropertiesResponseArgs(
        configuration="{ServiceConfiguration}",
        network_profile={
            "loadBalancerConfigurations": [{
                "name": "myLoadBalancer",
                "properties": {
                    "frontendIpConfigurations": [{
                        "name": "myfe",
                        "properties": {
                            "publicIPAddress": azure_native.compute.SubResourceArgs(
                                id="/subscriptions/{subscription-id}/resourceGroups/ConstosoRG/providers/Microsoft.Network/publicIPAddresses/myPublicIP",
                            ),
                        },
                    }],
                },
            }],
        },
        package_url="{PackageUrl}",
        role_profile={
            "roles": [{
                "name": "ContosoFrontend",
                "sku": azure_native.compute.CloudServiceRoleSkuArgs(
                    capacity=1,
                    name="Standard_D1_v2",
                    tier="Standard",
                ),
            }],
        },
        upgrade_mode="Auto",
    ),
    resource_group_name="ConstosoRG")

```

```yaml
resources:
  cloudService:
    type: azure-native:compute:CloudService
    properties:
      cloudServiceName: '{cs-name}'
      location: westus
      properties:
        configuration: '{ServiceConfiguration}'
        networkProfile:
          loadBalancerConfigurations:
            - name: myLoadBalancer
              properties:
                frontendIpConfigurations:
                  - name: myfe
                    properties:
                      publicIPAddress:
                        id: /subscriptions/{subscription-id}/resourceGroups/ConstosoRG/providers/Microsoft.Network/publicIPAddresses/myPublicIP
        packageUrl: '{PackageUrl}'
        roleProfile:
          roles:
            - name: ContosoFrontend
              sku:
                capacity: 1
                name: Standard_D1_v2
                tier: Standard
        upgradeMode: Auto
      resourceGroupName: ConstosoRG

```

{{% /example %}}
{{% example %}}
### Create New Cloud Service with Single Role and Certificate from Key Vault
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cloudService = new AzureNative.Compute.CloudService("cloudService", new()
    {
        CloudServiceName = "{cs-name}",
        Location = "westus",
        Properties = new AzureNative.Compute.Inputs.CloudServicePropertiesArgs
        {
            Configuration = "{ServiceConfiguration}",
            NetworkProfile = new AzureNative.Compute.Inputs.CloudServiceNetworkProfileArgs
            {
                LoadBalancerConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.LoadBalancerConfigurationArgs
                    {
                        Name = "contosolb",
                        Properties = new AzureNative.Compute.Inputs.LoadBalancerConfigurationPropertiesArgs
                        {
                            FrontendIpConfigurations = new[]
                            {
                                new AzureNative.Compute.Inputs.LoadBalancerFrontendIpConfigurationArgs
                                {
                                    Name = "contosofe",
                                    Properties = new AzureNative.Compute.Inputs.LoadBalancerFrontendIpConfigurationPropertiesArgs
                                    {
                                        PublicIPAddress = new AzureNative.Compute.Inputs.SubResourceArgs
                                        {
                                            Id = "/subscriptions/{subscription-id}/resourceGroups/ConstosoRG/providers/Microsoft.Network/publicIPAddresses/contosopublicip",
                                        },
                                    },
                                },
                            },
                        },
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.CloudServiceOsProfileArgs
            {
                Secrets = new[]
                {
                    new AzureNative.Compute.Inputs.CloudServiceVaultSecretGroupArgs
                    {
                        SourceVault = new AzureNative.Compute.Inputs.SubResourceArgs
                        {
                            Id = "/subscriptions/{subscription-id}/resourceGroups/ConstosoRG/providers/Microsoft.KeyVault/vaults/{keyvault-name}",
                        },
                        VaultCertificates = new[]
                        {
                            new AzureNative.Compute.Inputs.CloudServiceVaultCertificateArgs
                            {
                                CertificateUrl = "https://{keyvault-name}.vault.azure.net:443/secrets/ContosoCertificate/{secret-id}",
                            },
                        },
                    },
                },
            },
            PackageUrl = "{PackageUrl}",
            RoleProfile = new AzureNative.Compute.Inputs.CloudServiceRoleProfileArgs
            {
                Roles = new[]
                {
                    new AzureNative.Compute.Inputs.CloudServiceRoleProfilePropertiesArgs
                    {
                        Name = "ContosoFrontend",
                        Sku = new AzureNative.Compute.Inputs.CloudServiceRoleSkuArgs
                        {
                            Capacity = 1,
                            Name = "Standard_D1_v2",
                            Tier = "Standard",
                        },
                    },
                },
            },
            UpgradeMode = "Auto",
        },
        ResourceGroupName = "ConstosoRG",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.CloudService;
import com.pulumi.azurenative.compute.CloudServiceArgs;
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
        var cloudService = new CloudService("cloudService", CloudServiceArgs.builder()        
            .cloudServiceName("{cs-name}")
            .location("westus")
            .properties(Map.ofEntries(
                Map.entry("configuration", "{ServiceConfiguration}"),
                Map.entry("networkProfile", Map.of("loadBalancerConfigurations", Map.ofEntries(
                    Map.entry("name", "contosolb"),
                    Map.entry("properties", Map.of("frontendIpConfigurations", Map.ofEntries(
                        Map.entry("name", "contosofe"),
                        Map.entry("properties", Map.of("publicIPAddress", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/ConstosoRG/providers/Microsoft.Network/publicIPAddresses/contosopublicip")))
                    )))
                ))),
                Map.entry("osProfile", Map.of("secrets", Map.ofEntries(
                    Map.entry("sourceVault", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/ConstosoRG/providers/Microsoft.KeyVault/vaults/{keyvault-name}")),
                    Map.entry("vaultCertificates", Map.of("certificateUrl", "https://{keyvault-name}.vault.azure.net:443/secrets/ContosoCertificate/{secret-id}"))
                ))),
                Map.entry("packageUrl", "{PackageUrl}"),
                Map.entry("roleProfile", Map.of("roles", Map.ofEntries(
                    Map.entry("name", "ContosoFrontend"),
                    Map.entry("sku", Map.ofEntries(
                        Map.entry("capacity", 1),
                        Map.entry("name", "Standard_D1_v2"),
                        Map.entry("tier", "Standard")
                    ))
                ))),
                Map.entry("upgradeMode", "Auto")
            ))
            .resourceGroupName("ConstosoRG")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cloudService = new azure_native.compute.CloudService("cloudService", {
    cloudServiceName: "{cs-name}",
    location: "westus",
    properties: {
        configuration: "{ServiceConfiguration}",
        networkProfile: {
            loadBalancerConfigurations: [{
                name: "contosolb",
                properties: {
                    frontendIpConfigurations: [{
                        name: "contosofe",
                        properties: {
                            publicIPAddress: {
                                id: "/subscriptions/{subscription-id}/resourceGroups/ConstosoRG/providers/Microsoft.Network/publicIPAddresses/contosopublicip",
                            },
                        },
                    }],
                },
            }],
        },
        osProfile: {
            secrets: [{
                sourceVault: {
                    id: "/subscriptions/{subscription-id}/resourceGroups/ConstosoRG/providers/Microsoft.KeyVault/vaults/{keyvault-name}",
                },
                vaultCertificates: [{
                    certificateUrl: "https://{keyvault-name}.vault.azure.net:443/secrets/ContosoCertificate/{secret-id}",
                }],
            }],
        },
        packageUrl: "{PackageUrl}",
        roleProfile: {
            roles: [{
                name: "ContosoFrontend",
                sku: {
                    capacity: 1,
                    name: "Standard_D1_v2",
                    tier: "Standard",
                },
            }],
        },
        upgradeMode: "Auto",
    },
    resourceGroupName: "ConstosoRG",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cloud_service = azure_native.compute.CloudService("cloudService",
    cloud_service_name="{cs-name}",
    location="westus",
    properties=azure_native.compute.CloudServicePropertiesResponseArgs(
        configuration="{ServiceConfiguration}",
        network_profile={
            "loadBalancerConfigurations": [{
                "name": "contosolb",
                "properties": {
                    "frontendIpConfigurations": [{
                        "name": "contosofe",
                        "properties": {
                            "publicIPAddress": azure_native.compute.SubResourceArgs(
                                id="/subscriptions/{subscription-id}/resourceGroups/ConstosoRG/providers/Microsoft.Network/publicIPAddresses/contosopublicip",
                            ),
                        },
                    }],
                },
            }],
        },
        os_profile={
            "secrets": [{
                "sourceVault": azure_native.compute.SubResourceArgs(
                    id="/subscriptions/{subscription-id}/resourceGroups/ConstosoRG/providers/Microsoft.KeyVault/vaults/{keyvault-name}",
                ),
                "vaultCertificates": [azure_native.compute.CloudServiceVaultCertificateArgs(
                    certificate_url="https://{keyvault-name}.vault.azure.net:443/secrets/ContosoCertificate/{secret-id}",
                )],
            }],
        },
        package_url="{PackageUrl}",
        role_profile={
            "roles": [{
                "name": "ContosoFrontend",
                "sku": azure_native.compute.CloudServiceRoleSkuArgs(
                    capacity=1,
                    name="Standard_D1_v2",
                    tier="Standard",
                ),
            }],
        },
        upgrade_mode="Auto",
    ),
    resource_group_name="ConstosoRG")

```

```yaml
resources:
  cloudService:
    type: azure-native:compute:CloudService
    properties:
      cloudServiceName: '{cs-name}'
      location: westus
      properties:
        configuration: '{ServiceConfiguration}'
        networkProfile:
          loadBalancerConfigurations:
            - name: contosolb
              properties:
                frontendIpConfigurations:
                  - name: contosofe
                    properties:
                      publicIPAddress:
                        id: /subscriptions/{subscription-id}/resourceGroups/ConstosoRG/providers/Microsoft.Network/publicIPAddresses/contosopublicip
        osProfile:
          secrets:
            - sourceVault:
                id: /subscriptions/{subscription-id}/resourceGroups/ConstosoRG/providers/Microsoft.KeyVault/vaults/{keyvault-name}
              vaultCertificates:
                - certificateUrl: https://{keyvault-name}.vault.azure.net:443/secrets/ContosoCertificate/{secret-id}
        packageUrl: '{PackageUrl}'
        roleProfile:
          roles:
            - name: ContosoFrontend
              sku:
                capacity: 1
                name: Standard_D1_v2
                tier: Standard
        upgradeMode: Auto
      resourceGroupName: ConstosoRG

```

{{% /example %}}
{{% example %}}
### Create New Cloud Service with Single Role and RDP Extension
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cloudService = new AzureNative.Compute.CloudService("cloudService", new()
    {
        CloudServiceName = "{cs-name}",
        Location = "westus",
        Properties = new AzureNative.Compute.Inputs.CloudServicePropertiesArgs
        {
            Configuration = "{ServiceConfiguration}",
            ExtensionProfile = new AzureNative.Compute.Inputs.CloudServiceExtensionProfileArgs
            {
                Extensions = new[]
                {
                    new AzureNative.Compute.Inputs.ExtensionArgs
                    {
                        Name = "RDPExtension",
                        Properties = new AzureNative.Compute.Inputs.CloudServiceExtensionPropertiesArgs
                        {
                            AutoUpgradeMinorVersion = false,
                            ProtectedSettings = "<PrivateConfig><Password>{password}</Password></PrivateConfig>",
                            Publisher = "Microsoft.Windows.Azure.Extensions",
                            Settings = "<PublicConfig><UserName>UserAzure</UserName><Expiration>10/22/2021 15:05:45</Expiration></PublicConfig>",
                            Type = "RDP",
                            TypeHandlerVersion = "1.2",
                        },
                    },
                },
            },
            NetworkProfile = new AzureNative.Compute.Inputs.CloudServiceNetworkProfileArgs
            {
                LoadBalancerConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.LoadBalancerConfigurationArgs
                    {
                        Name = "contosolb",
                        Properties = new AzureNative.Compute.Inputs.LoadBalancerConfigurationPropertiesArgs
                        {
                            FrontendIpConfigurations = new[]
                            {
                                new AzureNative.Compute.Inputs.LoadBalancerFrontendIpConfigurationArgs
                                {
                                    Name = "contosofe",
                                    Properties = new AzureNative.Compute.Inputs.LoadBalancerFrontendIpConfigurationPropertiesArgs
                                    {
                                        PublicIPAddress = new AzureNative.Compute.Inputs.SubResourceArgs
                                        {
                                            Id = "/subscriptions/{subscription-id}/resourceGroups/ConstosoRG/providers/Microsoft.Network/publicIPAddresses/contosopublicip",
                                        },
                                    },
                                },
                            },
                        },
                    },
                },
            },
            PackageUrl = "{PackageUrl}",
            RoleProfile = new AzureNative.Compute.Inputs.CloudServiceRoleProfileArgs
            {
                Roles = new[]
                {
                    new AzureNative.Compute.Inputs.CloudServiceRoleProfilePropertiesArgs
                    {
                        Name = "ContosoFrontend",
                        Sku = new AzureNative.Compute.Inputs.CloudServiceRoleSkuArgs
                        {
                            Capacity = 1,
                            Name = "Standard_D1_v2",
                            Tier = "Standard",
                        },
                    },
                },
            },
            UpgradeMode = "Auto",
        },
        ResourceGroupName = "ConstosoRG",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.CloudService;
import com.pulumi.azurenative.compute.CloudServiceArgs;
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
        var cloudService = new CloudService("cloudService", CloudServiceArgs.builder()        
            .cloudServiceName("{cs-name}")
            .location("westus")
            .properties(Map.ofEntries(
                Map.entry("configuration", "{ServiceConfiguration}"),
                Map.entry("extensionProfile", Map.of("extensions", Map.ofEntries(
                    Map.entry("name", "RDPExtension"),
                    Map.entry("properties", Map.ofEntries(
                        Map.entry("autoUpgradeMinorVersion", false),
                        Map.entry("protectedSettings", "<PrivateConfig><Password>{password}</Password></PrivateConfig>"),
                        Map.entry("publisher", "Microsoft.Windows.Azure.Extensions"),
                        Map.entry("settings", "<PublicConfig><UserName>UserAzure</UserName><Expiration>10/22/2021 15:05:45</Expiration></PublicConfig>"),
                        Map.entry("type", "RDP"),
                        Map.entry("typeHandlerVersion", "1.2")
                    ))
                ))),
                Map.entry("networkProfile", Map.of("loadBalancerConfigurations", Map.ofEntries(
                    Map.entry("name", "contosolb"),
                    Map.entry("properties", Map.of("frontendIpConfigurations", Map.ofEntries(
                        Map.entry("name", "contosofe"),
                        Map.entry("properties", Map.of("publicIPAddress", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/ConstosoRG/providers/Microsoft.Network/publicIPAddresses/contosopublicip")))
                    )))
                ))),
                Map.entry("packageUrl", "{PackageUrl}"),
                Map.entry("roleProfile", Map.of("roles", Map.ofEntries(
                    Map.entry("name", "ContosoFrontend"),
                    Map.entry("sku", Map.ofEntries(
                        Map.entry("capacity", 1),
                        Map.entry("name", "Standard_D1_v2"),
                        Map.entry("tier", "Standard")
                    ))
                ))),
                Map.entry("upgradeMode", "Auto")
            ))
            .resourceGroupName("ConstosoRG")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cloudService = new azure_native.compute.CloudService("cloudService", {
    cloudServiceName: "{cs-name}",
    location: "westus",
    properties: {
        configuration: "{ServiceConfiguration}",
        extensionProfile: {
            extensions: [{
                name: "RDPExtension",
                properties: {
                    autoUpgradeMinorVersion: false,
                    protectedSettings: "<PrivateConfig><Password>{password}</Password></PrivateConfig>",
                    publisher: "Microsoft.Windows.Azure.Extensions",
                    settings: "<PublicConfig><UserName>UserAzure</UserName><Expiration>10/22/2021 15:05:45</Expiration></PublicConfig>",
                    type: "RDP",
                    typeHandlerVersion: "1.2",
                },
            }],
        },
        networkProfile: {
            loadBalancerConfigurations: [{
                name: "contosolb",
                properties: {
                    frontendIpConfigurations: [{
                        name: "contosofe",
                        properties: {
                            publicIPAddress: {
                                id: "/subscriptions/{subscription-id}/resourceGroups/ConstosoRG/providers/Microsoft.Network/publicIPAddresses/contosopublicip",
                            },
                        },
                    }],
                },
            }],
        },
        packageUrl: "{PackageUrl}",
        roleProfile: {
            roles: [{
                name: "ContosoFrontend",
                sku: {
                    capacity: 1,
                    name: "Standard_D1_v2",
                    tier: "Standard",
                },
            }],
        },
        upgradeMode: "Auto",
    },
    resourceGroupName: "ConstosoRG",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cloud_service = azure_native.compute.CloudService("cloudService",
    cloud_service_name="{cs-name}",
    location="westus",
    properties=azure_native.compute.CloudServicePropertiesResponseArgs(
        configuration="{ServiceConfiguration}",
        extension_profile={
            "extensions": [{
                "name": "RDPExtension",
                "properties": azure_native.compute.CloudServiceExtensionPropertiesArgs(
                    auto_upgrade_minor_version=False,
                    protected_settings="<PrivateConfig><Password>{password}</Password></PrivateConfig>",
                    publisher="Microsoft.Windows.Azure.Extensions",
                    settings="<PublicConfig><UserName>UserAzure</UserName><Expiration>10/22/2021 15:05:45</Expiration></PublicConfig>",
                    type="RDP",
                    type_handler_version="1.2",
                ),
            }],
        },
        network_profile={
            "loadBalancerConfigurations": [{
                "name": "contosolb",
                "properties": {
                    "frontendIpConfigurations": [{
                        "name": "contosofe",
                        "properties": {
                            "publicIPAddress": azure_native.compute.SubResourceArgs(
                                id="/subscriptions/{subscription-id}/resourceGroups/ConstosoRG/providers/Microsoft.Network/publicIPAddresses/contosopublicip",
                            ),
                        },
                    }],
                },
            }],
        },
        package_url="{PackageUrl}",
        role_profile={
            "roles": [{
                "name": "ContosoFrontend",
                "sku": azure_native.compute.CloudServiceRoleSkuArgs(
                    capacity=1,
                    name="Standard_D1_v2",
                    tier="Standard",
                ),
            }],
        },
        upgrade_mode="Auto",
    ),
    resource_group_name="ConstosoRG")

```

```yaml
resources:
  cloudService:
    type: azure-native:compute:CloudService
    properties:
      cloudServiceName: '{cs-name}'
      location: westus
      properties:
        configuration: '{ServiceConfiguration}'
        extensionProfile:
          extensions:
            - name: RDPExtension
              properties:
                autoUpgradeMinorVersion: false
                protectedSettings: <PrivateConfig><Password>{password}</Password></PrivateConfig>
                publisher: Microsoft.Windows.Azure.Extensions
                settings: <PublicConfig><UserName>UserAzure</UserName><Expiration>10/22/2021 15:05:45</Expiration></PublicConfig>
                type: RDP
                typeHandlerVersion: '1.2'
        networkProfile:
          loadBalancerConfigurations:
            - name: contosolb
              properties:
                frontendIpConfigurations:
                  - name: contosofe
                    properties:
                      publicIPAddress:
                        id: /subscriptions/{subscription-id}/resourceGroups/ConstosoRG/providers/Microsoft.Network/publicIPAddresses/contosopublicip
        packageUrl: '{PackageUrl}'
        roleProfile:
          roles:
            - name: ContosoFrontend
              sku:
                capacity: 1
                name: Standard_D1_v2
                tier: Standard
        upgradeMode: Auto
      resourceGroupName: ConstosoRG

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:compute:CloudService {cs-name} /subscriptions/{subscription-id}/resourceGroups/ConstosoRG/providers/Microsoft.Compute/cloudServices/{cs-name} 
```
