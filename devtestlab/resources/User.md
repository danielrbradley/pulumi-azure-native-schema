Profile of a lab user.
API Version: 2018-09-15.
Previous API Version: 2018-09-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Users_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var user = new AzureNative.DevTestLab.User("user", new()
    {
        Identity = new AzureNative.DevTestLab.Inputs.UserIdentityArgs
        {
            AppId = "{appId}",
            ObjectId = "{objectId}",
            PrincipalId = "{principalId}",
            PrincipalName = "{principalName}",
            TenantId = "{tenantId}",
        },
        LabName = "{devtestlabName}",
        Location = "{location}",
        Name = "{userName}",
        ResourceGroupName = "resourceGroupName",
        SecretStore = new AzureNative.DevTestLab.Inputs.UserSecretStoreArgs
        {
            KeyVaultId = "{keyVaultId}",
            KeyVaultUri = "{keyVaultUri}",
        },
        Tags = 
        {
            { "tagName1", "tagValue1" },
        },
    });

});


```

```go
package main

import (
	devtestlab "github.com/pulumi/pulumi-azure-native-sdk/devtestlab"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := devtestlab.NewUser(ctx, "user", &devtestlab.UserArgs{
			Identity: &devtestlab.UserIdentityArgs{
				AppId:         pulumi.String("{appId}"),
				ObjectId:      pulumi.String("{objectId}"),
				PrincipalId:   pulumi.String("{principalId}"),
				PrincipalName: pulumi.String("{principalName}"),
				TenantId:      pulumi.String("{tenantId}"),
			},
			LabName:           pulumi.String("{devtestlabName}"),
			Location:          pulumi.String("{location}"),
			Name:              pulumi.String("{userName}"),
			ResourceGroupName: pulumi.String("resourceGroupName"),
			SecretStore: &devtestlab.UserSecretStoreArgs{
				KeyVaultId:  pulumi.String("{keyVaultId}"),
				KeyVaultUri: pulumi.String("{keyVaultUri}"),
			},
			Tags: pulumi.StringMap{
				"tagName1": pulumi.String("tagValue1"),
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
import com.pulumi.azurenative.devtestlab.User;
import com.pulumi.azurenative.devtestlab.UserArgs;
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
        var user = new User("user", UserArgs.builder()        
            .identity(Map.ofEntries(
                Map.entry("appId", "{appId}"),
                Map.entry("objectId", "{objectId}"),
                Map.entry("principalId", "{principalId}"),
                Map.entry("principalName", "{principalName}"),
                Map.entry("tenantId", "{tenantId}")
            ))
            .labName("{devtestlabName}")
            .location("{location}")
            .name("{userName}")
            .resourceGroupName("resourceGroupName")
            .secretStore(Map.ofEntries(
                Map.entry("keyVaultId", "{keyVaultId}"),
                Map.entry("keyVaultUri", "{keyVaultUri}")
            ))
            .tags(Map.of("tagName1", "tagValue1"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const user = new azure_native.devtestlab.User("user", {
    identity: {
        appId: "{appId}",
        objectId: "{objectId}",
        principalId: "{principalId}",
        principalName: "{principalName}",
        tenantId: "{tenantId}",
    },
    labName: "{devtestlabName}",
    location: "{location}",
    name: "{userName}",
    resourceGroupName: "resourceGroupName",
    secretStore: {
        keyVaultId: "{keyVaultId}",
        keyVaultUri: "{keyVaultUri}",
    },
    tags: {
        tagName1: "tagValue1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

user = azure_native.devtestlab.User("user",
    identity=azure_native.devtestlab.UserIdentityArgs(
        app_id="{appId}",
        object_id="{objectId}",
        principal_id="{principalId}",
        principal_name="{principalName}",
        tenant_id="{tenantId}",
    ),
    lab_name="{devtestlabName}",
    location="{location}",
    name="{userName}",
    resource_group_name="resourceGroupName",
    secret_store=azure_native.devtestlab.UserSecretStoreArgs(
        key_vault_id="{keyVaultId}",
        key_vault_uri="{keyVaultUri}",
    ),
    tags={
        "tagName1": "tagValue1",
    })

```

```yaml
resources:
  user:
    type: azure-native:devtestlab:User
    properties:
      identity:
        appId: '{appId}'
        objectId: '{objectId}'
        principalId: '{principalId}'
        principalName: '{principalName}'
        tenantId: '{tenantId}'
      labName: '{devtestlabName}'
      location: '{location}'
      name: '{userName}'
      resourceGroupName: resourceGroupName
      secretStore:
        keyVaultId: '{keyVaultId}'
        keyVaultUri: '{keyVaultUri}'
      tags:
        tagName1: tagValue1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devtestlab:User myresource1 /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.DevTestLab/labs/{labName}/users/{name} 
```
