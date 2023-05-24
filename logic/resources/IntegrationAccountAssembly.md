The assembly definition.
API Version: 2019-05-01.
Previous API Version: 2019-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update an account assembly
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var integrationAccountAssembly = new AzureNative.Logic.IntegrationAccountAssembly("integrationAccountAssembly", new()
    {
        AssemblyArtifactName = "testAssembly",
        IntegrationAccountName = "testIntegrationAccount",
        Location = "westus",
        Properties = new AzureNative.Logic.Inputs.AssemblyPropertiesArgs
        {
            AssemblyName = "System.IdentityModel.Tokens.Jwt",
            Content = "Base64 encoded Assembly Content",
            Metadata = null,
        },
        ResourceGroupName = "testResourceGroup",
    });

});


```

```go
package main

import (
	logic "github.com/pulumi/pulumi-azure-native-sdk/logic"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := logic.NewIntegrationAccountAssembly(ctx, "integrationAccountAssembly", &logic.IntegrationAccountAssemblyArgs{
			AssemblyArtifactName:   pulumi.String("testAssembly"),
			IntegrationAccountName: pulumi.String("testIntegrationAccount"),
			Location:               pulumi.String("westus"),
			Properties: &logic.AssemblyPropertiesArgs{
				AssemblyName: pulumi.String("System.IdentityModel.Tokens.Jwt"),
				Content:      pulumi.Any("Base64 encoded Assembly Content"),
				Metadata:     nil,
			},
			ResourceGroupName: pulumi.String("testResourceGroup"),
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
import com.pulumi.azurenative.logic.IntegrationAccountAssembly;
import com.pulumi.azurenative.logic.IntegrationAccountAssemblyArgs;
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
        var integrationAccountAssembly = new IntegrationAccountAssembly("integrationAccountAssembly", IntegrationAccountAssemblyArgs.builder()        
            .assemblyArtifactName("testAssembly")
            .integrationAccountName("testIntegrationAccount")
            .location("westus")
            .properties(Map.ofEntries(
                Map.entry("assemblyName", "System.IdentityModel.Tokens.Jwt"),
                Map.entry("content", "Base64 encoded Assembly Content"),
                Map.entry("metadata", )
            ))
            .resourceGroupName("testResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const integrationAccountAssembly = new azure_native.logic.IntegrationAccountAssembly("integrationAccountAssembly", {
    assemblyArtifactName: "testAssembly",
    integrationAccountName: "testIntegrationAccount",
    location: "westus",
    properties: {
        assemblyName: "System.IdentityModel.Tokens.Jwt",
        content: "Base64 encoded Assembly Content",
        metadata: {},
    },
    resourceGroupName: "testResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

integration_account_assembly = azure_native.logic.IntegrationAccountAssembly("integrationAccountAssembly",
    assembly_artifact_name="testAssembly",
    integration_account_name="testIntegrationAccount",
    location="westus",
    properties=azure_native.logic.AssemblyPropertiesArgs(
        assembly_name="System.IdentityModel.Tokens.Jwt",
        content="Base64 encoded Assembly Content",
        metadata={},
    ),
    resource_group_name="testResourceGroup")

```

```yaml
resources:
  integrationAccountAssembly:
    type: azure-native:logic:IntegrationAccountAssembly
    properties:
      assemblyArtifactName: testAssembly
      integrationAccountName: testIntegrationAccount
      location: westus
      properties:
        assemblyName: System.IdentityModel.Tokens.Jwt
        content: Base64 encoded Assembly Content
        metadata: {}
      resourceGroupName: testResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:logic:IntegrationAccountAssembly testAssembly /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testResourceGroup/providers/Microsoft.Logic/integrationAccounts/testIntegrationAccount/assemblies/testAssembly 
```
