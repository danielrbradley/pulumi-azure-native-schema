Definition of the credential.
API Version: 2022-08-08.
Previous API Version: 2019-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a credential
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var credential = new AzureNative.Automation.Credential("credential", new()
    {
        AutomationAccountName = "myAutomationAccount18",
        CredentialName = "myCredential",
        Description = "my description goes here",
        Name = "myCredential",
        Password = "<password>",
        ResourceGroupName = "rg",
        UserName = "mylingaiah",
    });

});


```

```go
package main

import (
	automation "github.com/pulumi/pulumi-azure-native-sdk/automation"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := automation.NewCredential(ctx, "credential", &automation.CredentialArgs{
			AutomationAccountName: pulumi.String("myAutomationAccount18"),
			CredentialName:        pulumi.String("myCredential"),
			Description:           pulumi.String("my description goes here"),
			Name:                  pulumi.String("myCredential"),
			Password:              pulumi.String("<password>"),
			ResourceGroupName:     pulumi.String("rg"),
			UserName:              pulumi.String("mylingaiah"),
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
import com.pulumi.azurenative.automation.Credential;
import com.pulumi.azurenative.automation.CredentialArgs;
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
        var credential = new Credential("credential", CredentialArgs.builder()        
            .automationAccountName("myAutomationAccount18")
            .credentialName("myCredential")
            .description("my description goes here")
            .name("myCredential")
            .password("<password>")
            .resourceGroupName("rg")
            .userName("mylingaiah")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const credential = new azure_native.automation.Credential("credential", {
    automationAccountName: "myAutomationAccount18",
    credentialName: "myCredential",
    description: "my description goes here",
    name: "myCredential",
    password: "<password>",
    resourceGroupName: "rg",
    userName: "mylingaiah",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

credential = azure_native.automation.Credential("credential",
    automation_account_name="myAutomationAccount18",
    credential_name="myCredential",
    description="my description goes here",
    name="myCredential",
    password="<password>",
    resource_group_name="rg",
    user_name="mylingaiah")

```

```yaml
resources:
  credential:
    type: azure-native:automation:Credential
    properties:
      automationAccountName: myAutomationAccount18
      credentialName: myCredential
      description: my description goes here
      name: myCredential
      password: <password>
      resourceGroupName: rg
      userName: mylingaiah

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:automation:Credential myCredential /subscriptions/subid/resourceGroups/rg/providers/Microsoft.Automation/automationAccounts/myAutomationAccount18/credentials/myCredential 
```
