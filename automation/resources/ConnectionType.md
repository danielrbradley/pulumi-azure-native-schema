Definition of the connection type.
API Version: 2022-08-08.
Previous API Version: 2019-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update connection type
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var connectionType = new AzureNative.Automation.ConnectionType("connectionType", new()
    {
        AutomationAccountName = "myAutomationAccount22",
        ConnectionTypeName = "myCT",
        FieldDefinitions = 
        {
            { "myBoolField", new AzureNative.Automation.Inputs.FieldDefinitionArgs
            {
                IsEncrypted = false,
                IsOptional = false,
                Type = "bool",
            } },
            { "myStringField", new AzureNative.Automation.Inputs.FieldDefinitionArgs
            {
                IsEncrypted = false,
                IsOptional = false,
                Type = "string",
            } },
            { "myStringFieldEncrypted", new AzureNative.Automation.Inputs.FieldDefinitionArgs
            {
                IsEncrypted = true,
                IsOptional = false,
                Type = "string",
            } },
        },
        IsGlobal = false,
        Name = "myCT",
        ResourceGroupName = "rg",
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
		_, err := automation.NewConnectionType(ctx, "connectionType", &automation.ConnectionTypeArgs{
			AutomationAccountName: pulumi.String("myAutomationAccount22"),
			ConnectionTypeName:    pulumi.String("myCT"),
			FieldDefinitions: automation.FieldDefinitionMap{
				"myBoolField": &automation.FieldDefinitionArgs{
					IsEncrypted: pulumi.Bool(false),
					IsOptional:  pulumi.Bool(false),
					Type:        pulumi.String("bool"),
				},
				"myStringField": &automation.FieldDefinitionArgs{
					IsEncrypted: pulumi.Bool(false),
					IsOptional:  pulumi.Bool(false),
					Type:        pulumi.String("string"),
				},
				"myStringFieldEncrypted": &automation.FieldDefinitionArgs{
					IsEncrypted: pulumi.Bool(true),
					IsOptional:  pulumi.Bool(false),
					Type:        pulumi.String("string"),
				},
			},
			IsGlobal:          pulumi.Bool(false),
			Name:              pulumi.String("myCT"),
			ResourceGroupName: pulumi.String("rg"),
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
import com.pulumi.azurenative.automation.ConnectionType;
import com.pulumi.azurenative.automation.ConnectionTypeArgs;
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
        var connectionType = new ConnectionType("connectionType", ConnectionTypeArgs.builder()        
            .automationAccountName("myAutomationAccount22")
            .connectionTypeName("myCT")
            .fieldDefinitions(Map.ofEntries(
                Map.entry("myBoolField", Map.ofEntries(
                    Map.entry("isEncrypted", false),
                    Map.entry("isOptional", false),
                    Map.entry("type", "bool")
                )),
                Map.entry("myStringField", Map.ofEntries(
                    Map.entry("isEncrypted", false),
                    Map.entry("isOptional", false),
                    Map.entry("type", "string")
                )),
                Map.entry("myStringFieldEncrypted", Map.ofEntries(
                    Map.entry("isEncrypted", true),
                    Map.entry("isOptional", false),
                    Map.entry("type", "string")
                ))
            ))
            .isGlobal(false)
            .name("myCT")
            .resourceGroupName("rg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const connectionType = new azure_native.automation.ConnectionType("connectionType", {
    automationAccountName: "myAutomationAccount22",
    connectionTypeName: "myCT",
    fieldDefinitions: {
        myBoolField: {
            isEncrypted: false,
            isOptional: false,
            type: "bool",
        },
        myStringField: {
            isEncrypted: false,
            isOptional: false,
            type: "string",
        },
        myStringFieldEncrypted: {
            isEncrypted: true,
            isOptional: false,
            type: "string",
        },
    },
    isGlobal: false,
    name: "myCT",
    resourceGroupName: "rg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

connection_type = azure_native.automation.ConnectionType("connectionType",
    automation_account_name="myAutomationAccount22",
    connection_type_name="myCT",
    field_definitions={
        "myBoolField": azure_native.automation.FieldDefinitionArgs(
            is_encrypted=False,
            is_optional=False,
            type="bool",
        ),
        "myStringField": azure_native.automation.FieldDefinitionArgs(
            is_encrypted=False,
            is_optional=False,
            type="string",
        ),
        "myStringFieldEncrypted": azure_native.automation.FieldDefinitionArgs(
            is_encrypted=True,
            is_optional=False,
            type="string",
        ),
    },
    is_global=False,
    name="myCT",
    resource_group_name="rg")

```

```yaml
resources:
  connectionType:
    type: azure-native:automation:ConnectionType
    properties:
      automationAccountName: myAutomationAccount22
      connectionTypeName: myCT
      fieldDefinitions:
        myBoolField:
          isEncrypted: false
          isOptional: false
          type: bool
        myStringField:
          isEncrypted: false
          isOptional: false
          type: string
        myStringFieldEncrypted:
          isEncrypted: true
          isOptional: false
          type: string
      isGlobal: false
      name: myCT
      resourceGroupName: rg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:automation:ConnectionType myCT /subscriptions/subid/resourceGroups/rg/providers/Microsoft.Automation/automationAccounts/myAutomationAccount22/connectionTypes/myCT 
```
