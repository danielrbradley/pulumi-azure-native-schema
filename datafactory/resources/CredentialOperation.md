Credential resource type.
API Version: 2018-06-01.
Previous API Version: 2018-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Credentials_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var credentialOperation = new AzureNative.DataFactory.CredentialOperation("credentialOperation", new()
    {
        CredentialName = "exampleCredential",
        FactoryName = "exampleFactoryName",
        Properties = new AzureNative.DataFactory.Inputs.ManagedIdentityCredentialArgs
        {
            ResourceId = "/subscriptions/12345678-1234-1234-1234-12345678abc/resourcegroups/exampleResourceGroup/providers/Microsoft.ManagedIdentity/userAssignedIdentities/exampleUami",
            Type = "ManagedIdentity",
        },
        ResourceGroupName = "exampleResourceGroup",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.datafactory.CredentialOperation;
import com.pulumi.azurenative.datafactory.CredentialOperationArgs;
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
        var credentialOperation = new CredentialOperation("credentialOperation", CredentialOperationArgs.builder()        
            .credentialName("exampleCredential")
            .factoryName("exampleFactoryName")
            .properties(Map.ofEntries(
                Map.entry("resourceId", "/subscriptions/12345678-1234-1234-1234-12345678abc/resourcegroups/exampleResourceGroup/providers/Microsoft.ManagedIdentity/userAssignedIdentities/exampleUami"),
                Map.entry("type", "ManagedIdentity")
            ))
            .resourceGroupName("exampleResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const credentialOperation = new azure_native.datafactory.CredentialOperation("credentialOperation", {
    credentialName: "exampleCredential",
    factoryName: "exampleFactoryName",
    properties: {
        resourceId: "/subscriptions/12345678-1234-1234-1234-12345678abc/resourcegroups/exampleResourceGroup/providers/Microsoft.ManagedIdentity/userAssignedIdentities/exampleUami",
        type: "ManagedIdentity",
    },
    resourceGroupName: "exampleResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

credential_operation = azure_native.datafactory.CredentialOperation("credentialOperation",
    credential_name="exampleCredential",
    factory_name="exampleFactoryName",
    properties=azure_native.datafactory.ManagedIdentityCredentialResponseArgs(
        resource_id="/subscriptions/12345678-1234-1234-1234-12345678abc/resourcegroups/exampleResourceGroup/providers/Microsoft.ManagedIdentity/userAssignedIdentities/exampleUami",
        type="ManagedIdentity",
    ),
    resource_group_name="exampleResourceGroup")

```

```yaml
resources:
  credentialOperation:
    type: azure-native:datafactory:CredentialOperation
    properties:
      credentialName: exampleCredential
      factoryName: exampleFactoryName
      properties:
        resourceId: /subscriptions/12345678-1234-1234-1234-12345678abc/resourcegroups/exampleResourceGroup/providers/Microsoft.ManagedIdentity/userAssignedIdentities/exampleUami
        type: ManagedIdentity
      resourceGroupName: exampleResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:datafactory:CredentialOperation exampleCredential /subscriptions/12345678-1234-1234-1234-12345678abc/resourceGroups/exampleResourceGroup/providers/Microsoft.DataFactory/factories/exampleFactoryName/credentials/exampleCredential 
```
