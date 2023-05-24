Definition of the variable.
API Version: 2022-08-08.
Previous API Version: 2019-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a variable
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var variable = new AzureNative.Automation.Variable("variable", new()
    {
        AutomationAccountName = "sampleAccount9",
        Description = "my description",
        IsEncrypted = false,
        Name = "sampleVariable",
        ResourceGroupName = "rg",
        Value = "\"ComputerName.domain.com\"",
        VariableName = "sampleVariable",
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
		_, err := automation.NewVariable(ctx, "variable", &automation.VariableArgs{
			AutomationAccountName: pulumi.String("sampleAccount9"),
			Description:           pulumi.String("my description"),
			IsEncrypted:           pulumi.Bool(false),
			Name:                  pulumi.String("sampleVariable"),
			ResourceGroupName:     pulumi.String("rg"),
			Value:                 pulumi.String("\"ComputerName.domain.com\""),
			VariableName:          pulumi.String("sampleVariable"),
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
import com.pulumi.azurenative.automation.Variable;
import com.pulumi.azurenative.automation.VariableArgs;
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
        var variable = new Variable("variable", VariableArgs.builder()        
            .automationAccountName("sampleAccount9")
            .description("my description")
            .isEncrypted(false)
            .name("sampleVariable")
            .resourceGroupName("rg")
            .value("\"ComputerName.domain.com\"")
            .variableName("sampleVariable")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const variable = new azure_native.automation.Variable("variable", {
    automationAccountName: "sampleAccount9",
    description: "my description",
    isEncrypted: false,
    name: "sampleVariable",
    resourceGroupName: "rg",
    value: "\"ComputerName.domain.com\"",
    variableName: "sampleVariable",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

variable = azure_native.automation.Variable("variable",
    automation_account_name="sampleAccount9",
    description="my description",
    is_encrypted=False,
    name="sampleVariable",
    resource_group_name="rg",
    value="\"ComputerName.domain.com\"",
    variable_name="sampleVariable")

```

```yaml
resources:
  variable:
    type: azure-native:automation:Variable
    properties:
      automationAccountName: sampleAccount9
      description: my description
      isEncrypted: false
      name: sampleVariable
      resourceGroupName: rg
      value: '"ComputerName.domain.com"'
      variableName: sampleVariable

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:automation:Variable sampleVariable /subscriptions/subid/resourceGroups/rg/providers/Microsoft.Automation/automationAccounts/sampleAccount9/variables/sampleVariable 
```
