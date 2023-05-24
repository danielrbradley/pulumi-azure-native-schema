A secret.
API Version: 2018-09-15.
Previous API Version: 2018-09-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Secrets_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var secret = new AzureNative.DevTestLab.Secret("secret", new()
    {
        LabName = "{labName}",
        Name = "{secretName}",
        ResourceGroupName = "resourceGroupName",
        UserName = "{userName}",
        Value = "{secret}",
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
		_, err := devtestlab.NewSecret(ctx, "secret", &devtestlab.SecretArgs{
			LabName:           pulumi.String("{labName}"),
			Name:              pulumi.String("{secretName}"),
			ResourceGroupName: pulumi.String("resourceGroupName"),
			UserName:          pulumi.String("{userName}"),
			Value:             pulumi.String("{secret}"),
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
import com.pulumi.azurenative.devtestlab.Secret;
import com.pulumi.azurenative.devtestlab.SecretArgs;
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
        var secret = new Secret("secret", SecretArgs.builder()        
            .labName("{labName}")
            .name("{secretName}")
            .resourceGroupName("resourceGroupName")
            .userName("{userName}")
            .value("{secret}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const secret = new azure_native.devtestlab.Secret("secret", {
    labName: "{labName}",
    name: "{secretName}",
    resourceGroupName: "resourceGroupName",
    userName: "{userName}",
    value: "{secret}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

secret = azure_native.devtestlab.Secret("secret",
    lab_name="{labName}",
    name="{secretName}",
    resource_group_name="resourceGroupName",
    user_name="{userName}",
    value="{secret}")

```

```yaml
resources:
  secret:
    type: azure-native:devtestlab:Secret
    properties:
      labName: '{labName}'
      name: '{secretName}'
      resourceGroupName: resourceGroupName
      userName: '{userName}'
      value: '{secret}'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devtestlab:Secret {secretName} /subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/users/{userName}/secrets/{secretName} 
```
