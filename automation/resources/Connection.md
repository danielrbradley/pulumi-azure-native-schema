Definition of the connection.
API Version: 2022-08-08.
Previous API Version: 2019-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update connection
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var connection = new AzureNative.Automation.Connection("connection", new()
    {
        AutomationAccountName = "myAutomationAccount28",
        ConnectionName = "mysConnection",
        ConnectionType = new AzureNative.Automation.Inputs.ConnectionTypeAssociationPropertyArgs
        {
            Name = "Azure",
        },
        Description = "my description goes here",
        FieldDefinitionValues = 
        {
            { "AutomationCertificateName", "mysCertificateName" },
            { "SubscriptionID", "subid" },
        },
        Name = "mysConnection",
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
		_, err := automation.NewConnection(ctx, "connection", &automation.ConnectionArgs{
			AutomationAccountName: pulumi.String("myAutomationAccount28"),
			ConnectionName:        pulumi.String("mysConnection"),
			ConnectionType: &automation.ConnectionTypeAssociationPropertyArgs{
				Name: pulumi.String("Azure"),
			},
			Description: pulumi.String("my description goes here"),
			FieldDefinitionValues: pulumi.StringMap{
				"AutomationCertificateName": pulumi.String("mysCertificateName"),
				"SubscriptionID":            pulumi.String("subid"),
			},
			Name:              pulumi.String("mysConnection"),
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
import com.pulumi.azurenative.automation.Connection;
import com.pulumi.azurenative.automation.ConnectionArgs;
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
        var connection = new Connection("connection", ConnectionArgs.builder()        
            .automationAccountName("myAutomationAccount28")
            .connectionName("mysConnection")
            .connectionType(Map.of("name", "Azure"))
            .description("my description goes here")
            .fieldDefinitionValues(Map.ofEntries(
                Map.entry("AutomationCertificateName", "mysCertificateName"),
                Map.entry("SubscriptionID", "subid")
            ))
            .name("mysConnection")
            .resourceGroupName("rg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const connection = new azure_native.automation.Connection("connection", {
    automationAccountName: "myAutomationAccount28",
    connectionName: "mysConnection",
    connectionType: {
        name: "Azure",
    },
    description: "my description goes here",
    fieldDefinitionValues: {
        AutomationCertificateName: "mysCertificateName",
        SubscriptionID: "subid",
    },
    name: "mysConnection",
    resourceGroupName: "rg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

connection = azure_native.automation.Connection("connection",
    automation_account_name="myAutomationAccount28",
    connection_name="mysConnection",
    connection_type=azure_native.automation.ConnectionTypeAssociationPropertyArgs(
        name="Azure",
    ),
    description="my description goes here",
    field_definition_values={
        "AutomationCertificateName": "mysCertificateName",
        "SubscriptionID": "subid",
    },
    name="mysConnection",
    resource_group_name="rg")

```

```yaml
resources:
  connection:
    type: azure-native:automation:Connection
    properties:
      automationAccountName: myAutomationAccount28
      connectionName: mysConnection
      connectionType:
        name: Azure
      description: my description goes here
      fieldDefinitionValues:
        AutomationCertificateName: mysCertificateName
        SubscriptionID: subid
      name: mysConnection
      resourceGroupName: rg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:automation:Connection mysConnection /subscriptions/subid/resourceGroups/rg/providers/Microsoft.Automation/automationAccounts/myAutomationAccount28/connections/mysConnection 
```
