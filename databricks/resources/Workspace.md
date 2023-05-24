Information about workspace.
API Version: 2023-02-01.
Previous API Version: 2018-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a workspace which is ready for Customer-Managed Key (CMK) encryption
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var workspace = new AzureNative.Databricks.Workspace("workspace", new()
    {
        Location = "westus",
        ManagedResourceGroupId = "/subscriptions/subid/resourceGroups/myManagedRG",
        Parameters = new AzureNative.Databricks.Inputs.WorkspaceCustomParametersArgs
        {
            PrepareEncryption = new AzureNative.Databricks.Inputs.WorkspaceCustomBooleanParameterArgs
            {
                Value = true,
            },
        },
        ResourceGroupName = "rg",
        WorkspaceName = "myWorkspace",
    });

});


```

```go
package main

import (
	databricks "github.com/pulumi/pulumi-azure-native-sdk/databricks"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := databricks.NewWorkspace(ctx, "workspace", &databricks.WorkspaceArgs{
			Location:               pulumi.String("westus"),
			ManagedResourceGroupId: pulumi.String("/subscriptions/subid/resourceGroups/myManagedRG"),
			Parameters: databricks.WorkspaceCustomParametersResponse{
				PrepareEncryption: &databricks.WorkspaceCustomBooleanParameterArgs{
					Value: pulumi.Bool(true),
				},
			},
			ResourceGroupName: pulumi.String("rg"),
			WorkspaceName:     pulumi.String("myWorkspace"),
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
import com.pulumi.azurenative.databricks.Workspace;
import com.pulumi.azurenative.databricks.WorkspaceArgs;
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
        var workspace = new Workspace("workspace", WorkspaceArgs.builder()        
            .location("westus")
            .managedResourceGroupId("/subscriptions/subid/resourceGroups/myManagedRG")
            .parameters(Map.of("prepareEncryption", Map.of("value", true)))
            .resourceGroupName("rg")
            .workspaceName("myWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const workspace = new azure_native.databricks.Workspace("workspace", {
    location: "westus",
    managedResourceGroupId: "/subscriptions/subid/resourceGroups/myManagedRG",
    parameters: {
        prepareEncryption: {
            value: true,
        },
    },
    resourceGroupName: "rg",
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

workspace = azure_native.databricks.Workspace("workspace",
    location="westus",
    managed_resource_group_id="/subscriptions/subid/resourceGroups/myManagedRG",
    parameters=azure_native.databricks.WorkspaceCustomParametersResponseArgs(
        prepare_encryption=azure_native.databricks.WorkspaceCustomBooleanParameterArgs(
            value=True,
        ),
    ),
    resource_group_name="rg",
    workspace_name="myWorkspace")

```

```yaml
resources:
  workspace:
    type: azure-native:databricks:Workspace
    properties:
      location: westus
      managedResourceGroupId: /subscriptions/subid/resourceGroups/myManagedRG
      parameters:
        prepareEncryption:
          value: true
      resourceGroupName: rg
      workspaceName: myWorkspace

```

{{% /example %}}
{{% example %}}
### Create a workspace with Customer-Managed Key (CMK) encryption for Managed Disks
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var workspace = new AzureNative.Databricks.Workspace("workspace", new()
    {
        Encryption = new AzureNative.Databricks.Inputs.WorkspacePropertiesEncryptionArgs
        {
            Entities = new AzureNative.Databricks.Inputs.EncryptionEntitiesDefinitionArgs
            {
                ManagedDisk = new AzureNative.Databricks.Inputs.ManagedDiskEncryptionArgs
                {
                    KeySource = "Microsoft.Keyvault",
                    KeyVaultProperties = new AzureNative.Databricks.Inputs.ManagedDiskEncryptionKeyVaultPropertiesArgs
                    {
                        KeyName = "test-cmk-key",
                        KeyVaultUri = "https://test-vault-name.vault.azure.net/",
                        KeyVersion = "00000000000000000000000000000000",
                    },
                    RotationToLatestKeyVersionEnabled = true,
                },
            },
        },
        Location = "westus",
        ManagedResourceGroupId = "/subscriptions/subid/resourceGroups/myManagedRG",
        ResourceGroupName = "rg",
        WorkspaceName = "myWorkspace",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.databricks.Workspace;
import com.pulumi.azurenative.databricks.WorkspaceArgs;
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
        var workspace = new Workspace("workspace", WorkspaceArgs.builder()        
            .encryption(Map.of("entities", Map.of("managedDisk", Map.ofEntries(
                Map.entry("keySource", "Microsoft.Keyvault"),
                Map.entry("keyVaultProperties", Map.ofEntries(
                    Map.entry("keyName", "test-cmk-key"),
                    Map.entry("keyVaultUri", "https://test-vault-name.vault.azure.net/"),
                    Map.entry("keyVersion", "00000000000000000000000000000000")
                )),
                Map.entry("rotationToLatestKeyVersionEnabled", true)
            ))))
            .location("westus")
            .managedResourceGroupId("/subscriptions/subid/resourceGroups/myManagedRG")
            .resourceGroupName("rg")
            .workspaceName("myWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const workspace = new azure_native.databricks.Workspace("workspace", {
    encryption: {
        entities: {
            managedDisk: {
                keySource: "Microsoft.Keyvault",
                keyVaultProperties: {
                    keyName: "test-cmk-key",
                    keyVaultUri: "https://test-vault-name.vault.azure.net/",
                    keyVersion: "00000000000000000000000000000000",
                },
                rotationToLatestKeyVersionEnabled: true,
            },
        },
    },
    location: "westus",
    managedResourceGroupId: "/subscriptions/subid/resourceGroups/myManagedRG",
    resourceGroupName: "rg",
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

workspace = azure_native.databricks.Workspace("workspace",
    encryption=azure_native.databricks.WorkspacePropertiesResponseEncryptionArgs(
        entities={
            "managedDisk": {
                "keySource": "Microsoft.Keyvault",
                "keyVaultProperties": azure_native.databricks.ManagedDiskEncryptionKeyVaultPropertiesArgs(
                    key_name="test-cmk-key",
                    key_vault_uri="https://test-vault-name.vault.azure.net/",
                    key_version="00000000000000000000000000000000",
                ),
                "rotationToLatestKeyVersionEnabled": True,
            },
        },
    ),
    location="westus",
    managed_resource_group_id="/subscriptions/subid/resourceGroups/myManagedRG",
    resource_group_name="rg",
    workspace_name="myWorkspace")

```

```yaml
resources:
  workspace:
    type: azure-native:databricks:Workspace
    properties:
      encryption:
        entities:
          managedDisk:
            keySource: Microsoft.Keyvault
            keyVaultProperties:
              keyName: test-cmk-key
              keyVaultUri: https://test-vault-name.vault.azure.net/
              keyVersion: '00000000000000000000000000000000'
            rotationToLatestKeyVersionEnabled: true
      location: westus
      managedResourceGroupId: /subscriptions/subid/resourceGroups/myManagedRG
      resourceGroupName: rg
      workspaceName: myWorkspace

```

{{% /example %}}
{{% example %}}
### Create or update workspace
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var workspace = new AzureNative.Databricks.Workspace("workspace", new()
    {
        Location = "westus",
        ManagedResourceGroupId = "/subscriptions/subid/resourceGroups/myManagedRG",
        ResourceGroupName = "rg",
        WorkspaceName = "myWorkspace",
    });

});


```

```go
package main

import (
	databricks "github.com/pulumi/pulumi-azure-native-sdk/databricks"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := databricks.NewWorkspace(ctx, "workspace", &databricks.WorkspaceArgs{
			Location:               pulumi.String("westus"),
			ManagedResourceGroupId: pulumi.String("/subscriptions/subid/resourceGroups/myManagedRG"),
			ResourceGroupName:      pulumi.String("rg"),
			WorkspaceName:          pulumi.String("myWorkspace"),
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
import com.pulumi.azurenative.databricks.Workspace;
import com.pulumi.azurenative.databricks.WorkspaceArgs;
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
        var workspace = new Workspace("workspace", WorkspaceArgs.builder()        
            .location("westus")
            .managedResourceGroupId("/subscriptions/subid/resourceGroups/myManagedRG")
            .resourceGroupName("rg")
            .workspaceName("myWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const workspace = new azure_native.databricks.Workspace("workspace", {
    location: "westus",
    managedResourceGroupId: "/subscriptions/subid/resourceGroups/myManagedRG",
    resourceGroupName: "rg",
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

workspace = azure_native.databricks.Workspace("workspace",
    location="westus",
    managed_resource_group_id="/subscriptions/subid/resourceGroups/myManagedRG",
    resource_group_name="rg",
    workspace_name="myWorkspace")

```

```yaml
resources:
  workspace:
    type: azure-native:databricks:Workspace
    properties:
      location: westus
      managedResourceGroupId: /subscriptions/subid/resourceGroups/myManagedRG
      resourceGroupName: rg
      workspaceName: myWorkspace

```

{{% /example %}}
{{% example %}}
### Create or update workspace with custom parameters
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var workspace = new AzureNative.Databricks.Workspace("workspace", new()
    {
        Location = "westus",
        ManagedResourceGroupId = "/subscriptions/subid/resourceGroups/myManagedRG",
        Parameters = new AzureNative.Databricks.Inputs.WorkspaceCustomParametersArgs
        {
            CustomPrivateSubnetName = new AzureNative.Databricks.Inputs.WorkspaceCustomStringParameterArgs
            {
                Value = "myPrivateSubnet",
            },
            CustomPublicSubnetName = new AzureNative.Databricks.Inputs.WorkspaceCustomStringParameterArgs
            {
                Value = "myPublicSubnet",
            },
            CustomVirtualNetworkId = new AzureNative.Databricks.Inputs.WorkspaceCustomStringParameterArgs
            {
                Value = "/subscriptions/subid/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/myNetwork",
            },
        },
        ResourceGroupName = "rg",
        WorkspaceName = "myWorkspace",
    });

});


```

```go
package main

import (
	databricks "github.com/pulumi/pulumi-azure-native-sdk/databricks"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := databricks.NewWorkspace(ctx, "workspace", &databricks.WorkspaceArgs{
			Location:               pulumi.String("westus"),
			ManagedResourceGroupId: pulumi.String("/subscriptions/subid/resourceGroups/myManagedRG"),
			Parameters: databricks.WorkspaceCustomParametersResponse{
				CustomPrivateSubnetName: &databricks.WorkspaceCustomStringParameterArgs{
					Value: pulumi.String("myPrivateSubnet"),
				},
				CustomPublicSubnetName: &databricks.WorkspaceCustomStringParameterArgs{
					Value: pulumi.String("myPublicSubnet"),
				},
				CustomVirtualNetworkId: &databricks.WorkspaceCustomStringParameterArgs{
					Value: pulumi.String("/subscriptions/subid/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/myNetwork"),
				},
			},
			ResourceGroupName: pulumi.String("rg"),
			WorkspaceName:     pulumi.String("myWorkspace"),
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
import com.pulumi.azurenative.databricks.Workspace;
import com.pulumi.azurenative.databricks.WorkspaceArgs;
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
        var workspace = new Workspace("workspace", WorkspaceArgs.builder()        
            .location("westus")
            .managedResourceGroupId("/subscriptions/subid/resourceGroups/myManagedRG")
            .parameters(Map.ofEntries(
                Map.entry("customPrivateSubnetName", Map.of("value", "myPrivateSubnet")),
                Map.entry("customPublicSubnetName", Map.of("value", "myPublicSubnet")),
                Map.entry("customVirtualNetworkId", Map.of("value", "/subscriptions/subid/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/myNetwork"))
            ))
            .resourceGroupName("rg")
            .workspaceName("myWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const workspace = new azure_native.databricks.Workspace("workspace", {
    location: "westus",
    managedResourceGroupId: "/subscriptions/subid/resourceGroups/myManagedRG",
    parameters: {
        customPrivateSubnetName: {
            value: "myPrivateSubnet",
        },
        customPublicSubnetName: {
            value: "myPublicSubnet",
        },
        customVirtualNetworkId: {
            value: "/subscriptions/subid/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/myNetwork",
        },
    },
    resourceGroupName: "rg",
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

workspace = azure_native.databricks.Workspace("workspace",
    location="westus",
    managed_resource_group_id="/subscriptions/subid/resourceGroups/myManagedRG",
    parameters=azure_native.databricks.WorkspaceCustomParametersResponseArgs(
        custom_private_subnet_name=azure_native.databricks.WorkspaceCustomStringParameterArgs(
            value="myPrivateSubnet",
        ),
        custom_public_subnet_name=azure_native.databricks.WorkspaceCustomStringParameterArgs(
            value="myPublicSubnet",
        ),
        custom_virtual_network_id=azure_native.databricks.WorkspaceCustomStringParameterArgs(
            value="/subscriptions/subid/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/myNetwork",
        ),
    ),
    resource_group_name="rg",
    workspace_name="myWorkspace")

```

```yaml
resources:
  workspace:
    type: azure-native:databricks:Workspace
    properties:
      location: westus
      managedResourceGroupId: /subscriptions/subid/resourceGroups/myManagedRG
      parameters:
        customPrivateSubnetName:
          value: myPrivateSubnet
        customPublicSubnetName:
          value: myPublicSubnet
        customVirtualNetworkId:
          value: /subscriptions/subid/resourceGroups/rg/providers/Microsoft.Network/virtualNetworks/myNetwork
      resourceGroupName: rg
      workspaceName: myWorkspace

```

{{% /example %}}
{{% example %}}
### Enable Customer-Managed Key (CMK) encryption on a workspace which is prepared for encryption
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var workspace = new AzureNative.Databricks.Workspace("workspace", new()
    {
        Location = "westus",
        ManagedResourceGroupId = "/subscriptions/subid/resourceGroups/myManagedRG",
        Parameters = new AzureNative.Databricks.Inputs.WorkspaceCustomParametersArgs
        {
            Encryption = new AzureNative.Databricks.Inputs.WorkspaceEncryptionParameterArgs
            {
                Value = new AzureNative.Databricks.Inputs.EncryptionArgs
                {
                    KeyName = "myKeyName",
                    KeySource = "Microsoft.Keyvault",
                    KeyVaultUri = "https://myKeyVault.vault.azure.net/",
                    KeyVersion = "00000000000000000000000000000000",
                },
            },
            PrepareEncryption = new AzureNative.Databricks.Inputs.WorkspaceCustomBooleanParameterArgs
            {
                Value = true,
            },
        },
        ResourceGroupName = "rg",
        WorkspaceName = "myWorkspace",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.databricks.Workspace;
import com.pulumi.azurenative.databricks.WorkspaceArgs;
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
        var workspace = new Workspace("workspace", WorkspaceArgs.builder()        
            .location("westus")
            .managedResourceGroupId("/subscriptions/subid/resourceGroups/myManagedRG")
            .parameters(Map.ofEntries(
                Map.entry("encryption", Map.of("value", Map.ofEntries(
                    Map.entry("keyName", "myKeyName"),
                    Map.entry("keySource", "Microsoft.Keyvault"),
                    Map.entry("keyVaultUri", "https://myKeyVault.vault.azure.net/"),
                    Map.entry("keyVersion", "00000000000000000000000000000000")
                ))),
                Map.entry("prepareEncryption", Map.of("value", true))
            ))
            .resourceGroupName("rg")
            .workspaceName("myWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const workspace = new azure_native.databricks.Workspace("workspace", {
    location: "westus",
    managedResourceGroupId: "/subscriptions/subid/resourceGroups/myManagedRG",
    parameters: {
        encryption: {
            value: {
                keyName: "myKeyName",
                keySource: "Microsoft.Keyvault",
                keyVaultUri: "https://myKeyVault.vault.azure.net/",
                keyVersion: "00000000000000000000000000000000",
            },
        },
        prepareEncryption: {
            value: true,
        },
    },
    resourceGroupName: "rg",
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

workspace = azure_native.databricks.Workspace("workspace",
    location="westus",
    managed_resource_group_id="/subscriptions/subid/resourceGroups/myManagedRG",
    parameters=azure_native.databricks.WorkspaceCustomParametersResponseArgs(
        encryption={
            "value": azure_native.databricks.EncryptionArgs(
                key_name="myKeyName",
                key_source="Microsoft.Keyvault",
                key_vault_uri="https://myKeyVault.vault.azure.net/",
                key_version="00000000000000000000000000000000",
            ),
        },
        prepare_encryption=azure_native.databricks.WorkspaceCustomBooleanParameterArgs(
            value=True,
        ),
    ),
    resource_group_name="rg",
    workspace_name="myWorkspace")

```

```yaml
resources:
  workspace:
    type: azure-native:databricks:Workspace
    properties:
      location: westus
      managedResourceGroupId: /subscriptions/subid/resourceGroups/myManagedRG
      parameters:
        encryption:
          value:
            keyName: myKeyName
            keySource: Microsoft.Keyvault
            keyVaultUri: https://myKeyVault.vault.azure.net/
            keyVersion: '00000000000000000000000000000000'
        prepareEncryption:
          value: true
      resourceGroupName: rg
      workspaceName: myWorkspace

```

{{% /example %}}
{{% example %}}
### Revert Customer-Managed Key (CMK) encryption to Microsoft Managed Keys encryption on a workspace
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var workspace = new AzureNative.Databricks.Workspace("workspace", new()
    {
        Location = "westus",
        ManagedResourceGroupId = "/subscriptions/subid/resourceGroups/myManagedRG",
        Parameters = new AzureNative.Databricks.Inputs.WorkspaceCustomParametersArgs
        {
            Encryption = new AzureNative.Databricks.Inputs.WorkspaceEncryptionParameterArgs
            {
                Value = new AzureNative.Databricks.Inputs.EncryptionArgs
                {
                    KeySource = "Default",
                },
            },
        },
        ResourceGroupName = "rg",
        WorkspaceName = "myWorkspace",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.databricks.Workspace;
import com.pulumi.azurenative.databricks.WorkspaceArgs;
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
        var workspace = new Workspace("workspace", WorkspaceArgs.builder()        
            .location("westus")
            .managedResourceGroupId("/subscriptions/subid/resourceGroups/myManagedRG")
            .parameters(Map.of("encryption", Map.of("value", Map.of("keySource", "Default"))))
            .resourceGroupName("rg")
            .workspaceName("myWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const workspace = new azure_native.databricks.Workspace("workspace", {
    location: "westus",
    managedResourceGroupId: "/subscriptions/subid/resourceGroups/myManagedRG",
    parameters: {
        encryption: {
            value: {
                keySource: "Default",
            },
        },
    },
    resourceGroupName: "rg",
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

workspace = azure_native.databricks.Workspace("workspace",
    location="westus",
    managed_resource_group_id="/subscriptions/subid/resourceGroups/myManagedRG",
    parameters=azure_native.databricks.WorkspaceCustomParametersResponseArgs(
        encryption={
            "value": azure_native.databricks.EncryptionArgs(
                key_source="Default",
            ),
        },
    ),
    resource_group_name="rg",
    workspace_name="myWorkspace")

```

```yaml
resources:
  workspace:
    type: azure-native:databricks:Workspace
    properties:
      location: westus
      managedResourceGroupId: /subscriptions/subid/resourceGroups/myManagedRG
      parameters:
        encryption:
          value:
            keySource: Default
      resourceGroupName: rg
      workspaceName: myWorkspace

```

{{% /example %}}
{{% example %}}
### Update a workspace with Customer-Managed Key (CMK) encryption for Managed Disks
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var workspace = new AzureNative.Databricks.Workspace("workspace", new()
    {
        Encryption = new AzureNative.Databricks.Inputs.WorkspacePropertiesEncryptionArgs
        {
            Entities = new AzureNative.Databricks.Inputs.EncryptionEntitiesDefinitionArgs
            {
                ManagedDisk = new AzureNative.Databricks.Inputs.ManagedDiskEncryptionArgs
                {
                    KeySource = "Microsoft.Keyvault",
                    KeyVaultProperties = new AzureNative.Databricks.Inputs.ManagedDiskEncryptionKeyVaultPropertiesArgs
                    {
                        KeyName = "test-cmk-key",
                        KeyVaultUri = "https://test-vault-name.vault.azure.net/",
                        KeyVersion = "00000000000000000000000000000000",
                    },
                    RotationToLatestKeyVersionEnabled = true,
                },
            },
        },
        Location = "westus",
        ManagedResourceGroupId = "/subscriptions/subid/resourceGroups/myManagedRG",
        ResourceGroupName = "rg",
        Tags = 
        {
            { "mytag1", "myvalue1" },
        },
        WorkspaceName = "myWorkspace",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.databricks.Workspace;
import com.pulumi.azurenative.databricks.WorkspaceArgs;
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
        var workspace = new Workspace("workspace", WorkspaceArgs.builder()        
            .encryption(Map.of("entities", Map.of("managedDisk", Map.ofEntries(
                Map.entry("keySource", "Microsoft.Keyvault"),
                Map.entry("keyVaultProperties", Map.ofEntries(
                    Map.entry("keyName", "test-cmk-key"),
                    Map.entry("keyVaultUri", "https://test-vault-name.vault.azure.net/"),
                    Map.entry("keyVersion", "00000000000000000000000000000000")
                )),
                Map.entry("rotationToLatestKeyVersionEnabled", true)
            ))))
            .location("westus")
            .managedResourceGroupId("/subscriptions/subid/resourceGroups/myManagedRG")
            .resourceGroupName("rg")
            .tags(Map.of("mytag1", "myvalue1"))
            .workspaceName("myWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const workspace = new azure_native.databricks.Workspace("workspace", {
    encryption: {
        entities: {
            managedDisk: {
                keySource: "Microsoft.Keyvault",
                keyVaultProperties: {
                    keyName: "test-cmk-key",
                    keyVaultUri: "https://test-vault-name.vault.azure.net/",
                    keyVersion: "00000000000000000000000000000000",
                },
                rotationToLatestKeyVersionEnabled: true,
            },
        },
    },
    location: "westus",
    managedResourceGroupId: "/subscriptions/subid/resourceGroups/myManagedRG",
    resourceGroupName: "rg",
    tags: {
        mytag1: "myvalue1",
    },
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

workspace = azure_native.databricks.Workspace("workspace",
    encryption=azure_native.databricks.WorkspacePropertiesResponseEncryptionArgs(
        entities={
            "managedDisk": {
                "keySource": "Microsoft.Keyvault",
                "keyVaultProperties": azure_native.databricks.ManagedDiskEncryptionKeyVaultPropertiesArgs(
                    key_name="test-cmk-key",
                    key_vault_uri="https://test-vault-name.vault.azure.net/",
                    key_version="00000000000000000000000000000000",
                ),
                "rotationToLatestKeyVersionEnabled": True,
            },
        },
    ),
    location="westus",
    managed_resource_group_id="/subscriptions/subid/resourceGroups/myManagedRG",
    resource_group_name="rg",
    tags={
        "mytag1": "myvalue1",
    },
    workspace_name="myWorkspace")

```

```yaml
resources:
  workspace:
    type: azure-native:databricks:Workspace
    properties:
      encryption:
        entities:
          managedDisk:
            keySource: Microsoft.Keyvault
            keyVaultProperties:
              keyName: test-cmk-key
              keyVaultUri: https://test-vault-name.vault.azure.net/
              keyVersion: '00000000000000000000000000000000'
            rotationToLatestKeyVersionEnabled: true
      location: westus
      managedResourceGroupId: /subscriptions/subid/resourceGroups/myManagedRG
      resourceGroupName: rg
      tags:
        mytag1: myvalue1
      workspaceName: myWorkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:databricks:Workspace myWorkspace /subscriptions/subid/resourceGroups/rg/providers/Microsoft.Databricks/workspaces/myWorkspace 
```
