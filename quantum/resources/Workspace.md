The resource proxy definition object for quantum workspace.
API Version: 2022-01-10-preview.
Previous API Version: 2019-11-04-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### QuantumWorkspacesPut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var workspace = new AzureNative.Quantum.Workspace("workspace", new()
    {
        Location = "West US",
        Providers = new[]
        {
            new AzureNative.Quantum.Inputs.ProviderArgs
            {
                ProviderId = "Honeywell",
                ProviderSku = "Basic",
            },
            new AzureNative.Quantum.Inputs.ProviderArgs
            {
                ProviderId = "IonQ",
                ProviderSku = "Basic",
            },
            new AzureNative.Quantum.Inputs.ProviderArgs
            {
                ProviderId = "OneQBit",
                ProviderSku = "Basic",
            },
        },
        ResourceGroupName = "quantumResourcegroup",
        StorageAccount = "/subscriptions/1C4B2828-7D49-494F-933D-061373BE28C2/resourceGroups/quantumResourcegroup/providers/Microsoft.Storage/storageAccounts/testStorageAccount",
        WorkspaceName = "quantumworkspace1",
    });

});


```

```go
package main

import (
	quantum "github.com/pulumi/pulumi-azure-native-sdk/quantum"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := quantum.NewWorkspace(ctx, "workspace", &quantum.WorkspaceArgs{
			Location: pulumi.String("West US"),
			Providers: []quantum.ProviderArgs{
				{
					ProviderId:  pulumi.String("Honeywell"),
					ProviderSku: pulumi.String("Basic"),
				},
				{
					ProviderId:  pulumi.String("IonQ"),
					ProviderSku: pulumi.String("Basic"),
				},
				{
					ProviderId:  pulumi.String("OneQBit"),
					ProviderSku: pulumi.String("Basic"),
				},
			},
			ResourceGroupName: pulumi.String("quantumResourcegroup"),
			StorageAccount:    pulumi.String("/subscriptions/1C4B2828-7D49-494F-933D-061373BE28C2/resourceGroups/quantumResourcegroup/providers/Microsoft.Storage/storageAccounts/testStorageAccount"),
			WorkspaceName:     pulumi.String("quantumworkspace1"),
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
import com.pulumi.azurenative.quantum.Workspace;
import com.pulumi.azurenative.quantum.WorkspaceArgs;
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
            .location("West US")
            .providers(            
                Map.ofEntries(
                    Map.entry("providerId", "Honeywell"),
                    Map.entry("providerSku", "Basic")
                ),
                Map.ofEntries(
                    Map.entry("providerId", "IonQ"),
                    Map.entry("providerSku", "Basic")
                ),
                Map.ofEntries(
                    Map.entry("providerId", "OneQBit"),
                    Map.entry("providerSku", "Basic")
                ))
            .resourceGroupName("quantumResourcegroup")
            .storageAccount("/subscriptions/1C4B2828-7D49-494F-933D-061373BE28C2/resourceGroups/quantumResourcegroup/providers/Microsoft.Storage/storageAccounts/testStorageAccount")
            .workspaceName("quantumworkspace1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const workspace = new azure_native.quantum.Workspace("workspace", {
    location: "West US",
    providers: [
        {
            providerId: "Honeywell",
            providerSku: "Basic",
        },
        {
            providerId: "IonQ",
            providerSku: "Basic",
        },
        {
            providerId: "OneQBit",
            providerSku: "Basic",
        },
    ],
    resourceGroupName: "quantumResourcegroup",
    storageAccount: "/subscriptions/1C4B2828-7D49-494F-933D-061373BE28C2/resourceGroups/quantumResourcegroup/providers/Microsoft.Storage/storageAccounts/testStorageAccount",
    workspaceName: "quantumworkspace1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

workspace = azure_native.quantum.Workspace("workspace",
    location="West US",
    providers=[
        azure_native.quantum.ProviderArgs(
            provider_id="Honeywell",
            provider_sku="Basic",
        ),
        azure_native.quantum.ProviderArgs(
            provider_id="IonQ",
            provider_sku="Basic",
        ),
        azure_native.quantum.ProviderArgs(
            provider_id="OneQBit",
            provider_sku="Basic",
        ),
    ],
    resource_group_name="quantumResourcegroup",
    storage_account="/subscriptions/1C4B2828-7D49-494F-933D-061373BE28C2/resourceGroups/quantumResourcegroup/providers/Microsoft.Storage/storageAccounts/testStorageAccount",
    workspace_name="quantumworkspace1")

```

```yaml
resources:
  workspace:
    type: azure-native:quantum:Workspace
    properties:
      location: West US
      providers:
        - providerId: Honeywell
          providerSku: Basic
        - providerId: IonQ
          providerSku: Basic
        - providerId: OneQBit
          providerSku: Basic
      resourceGroupName: quantumResourcegroup
      storageAccount: /subscriptions/1C4B2828-7D49-494F-933D-061373BE28C2/resourceGroups/quantumResourcegroup/providers/Microsoft.Storage/storageAccounts/testStorageAccount
      workspaceName: quantumworkspace1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:quantum:Workspace quantumworkspace1 /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/quantumResourcegroup/providers/Microsoft.Quantum/Workspaces/quantumworkspace1 
```
