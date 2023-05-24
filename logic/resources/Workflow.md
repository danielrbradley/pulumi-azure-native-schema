The workflow type.
API Version: 2019-05-01.
Previous API Version: 2019-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a workflow
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var workflow = new AzureNative.Logic.Workflow("workflow", new()
    {
        Definition = 
        {
            { "$schema", "https://schema.management.azure.com/providers/Microsoft.Logic/schemas/2016-06-01/workflowdefinition.json#" },
            { "actions", 
            {
                { "Find_pet_by_ID", 
                {
                    { "inputs", 
                    {
                        { "host", 
                        {
                            { "connection", 
                            {
                                { "name", "@parameters('$connections')['test-custom-connector']['connectionId']" },
                            } },
                        } },
                        { "method", "get" },
                        { "path", "/pet/@{encodeURIComponent('1')}" },
                    } },
                    { "runAfter", null },
                    { "type", "ApiConnection" },
                } },
            } },
            { "contentVersion", "1.0.0.0" },
            { "outputs", null },
            { "parameters", 
            {
                { "$connections", 
                {
                    { "defaultValue", null },
                    { "type", "Object" },
                } },
            } },
            { "triggers", 
            {
                { "manual", 
                {
                    { "inputs", 
                    {
                        { "schema", null },
                    } },
                    { "kind", "Http" },
                    { "type", "Request" },
                } },
            } },
        },
        IntegrationAccount = new AzureNative.Logic.Inputs.ResourceReferenceArgs
        {
            Id = "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/test-resource-group/providers/Microsoft.Logic/integrationAccounts/test-integration-account",
        },
        Location = "brazilsouth",
        Parameters = 
        {
            { "$connections", new AzureNative.Logic.Inputs.WorkflowParameterArgs
            {
                Value = 
                {
                    { "test-custom-connector", 
                    {
                        { "connectionId", "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/test-resource-group/providers/Microsoft.Web/connections/test-custom-connector" },
                        { "connectionName", "test-custom-connector" },
                        { "id", "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/providers/Microsoft.Web/locations/brazilsouth/managedApis/test-custom-connector" },
                    } },
                },
            } },
        },
        ResourceGroupName = "test-resource-group",
        Tags = null,
        WorkflowName = "test-workflow",
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
		_, err := logic.NewWorkflow(ctx, "workflow", &logic.WorkflowArgs{
			Definition: pulumi.Any{
				Schema: "https://schema.management.azure.com/providers/Microsoft.Logic/schemas/2016-06-01/workflowdefinition.json#",
				Actions: map[string]interface{}{
					"Find_pet_by_ID": map[string]interface{}{
						"inputs": map[string]interface{}{
							"host": map[string]interface{}{
								"connection": map[string]interface{}{
									"name": "@parameters('$connections')['test-custom-connector']['connectionId']",
								},
							},
							"method": "get",
							"path":   "/pet/@{encodeURIComponent('1')}",
						},
						"runAfter": nil,
						"type":     "ApiConnection",
					},
				},
				ContentVersion: "1.0.0.0",
				Outputs:        nil,
				Parameters: map[string]interface{}{
					"$connections": map[string]interface{}{
						"defaultValue": nil,
						"type":         "Object",
					},
				},
				Triggers: map[string]interface{}{
					"manual": map[string]interface{}{
						"inputs": map[string]interface{}{
							"schema": nil,
						},
						"kind": "Http",
						"type": "Request",
					},
				},
			},
			IntegrationAccount: &logic.ResourceReferenceArgs{
				Id: pulumi.String("/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/test-resource-group/providers/Microsoft.Logic/integrationAccounts/test-integration-account"),
			},
			Location: pulumi.String("brazilsouth"),
			Parameters: logic.WorkflowParameterMap{
				"$connections": &logic.WorkflowParameterArgs{
					Value: pulumi.Any{
						TestCustomConnector: map[string]interface{}{
							"connectionId":   "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/test-resource-group/providers/Microsoft.Web/connections/test-custom-connector",
							"connectionName": "test-custom-connector",
							"id":             "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/providers/Microsoft.Web/locations/brazilsouth/managedApis/test-custom-connector",
						},
					},
				},
			},
			ResourceGroupName: pulumi.String("test-resource-group"),
			Tags:              nil,
			WorkflowName:      pulumi.String("test-workflow"),
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
import com.pulumi.azurenative.logic.Workflow;
import com.pulumi.azurenative.logic.WorkflowArgs;
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
        var workflow = new Workflow("workflow", WorkflowArgs.builder()        
            .definition(Map.ofEntries(
                Map.entry("$schema", "https://schema.management.azure.com/providers/Microsoft.Logic/schemas/2016-06-01/workflowdefinition.json#"),
                Map.entry("actions", Map.of("Find_pet_by_ID", Map.ofEntries(
                    Map.entry("inputs", Map.ofEntries(
                        Map.entry("host", Map.of("connection", Map.of("name", "@parameters('$connections')['test-custom-connector']['connectionId']"))),
                        Map.entry("method", "get"),
                        Map.entry("path", "/pet/@{encodeURIComponent('1')}")
                    )),
                    Map.entry("runAfter", ),
                    Map.entry("type", "ApiConnection")
                ))),
                Map.entry("contentVersion", "1.0.0.0"),
                Map.entry("outputs", ),
                Map.entry("parameters", Map.of("$connections", Map.ofEntries(
                    Map.entry("defaultValue", ),
                    Map.entry("type", "Object")
                ))),
                Map.entry("triggers", Map.of("manual", Map.ofEntries(
                    Map.entry("inputs", Map.of("schema", )),
                    Map.entry("kind", "Http"),
                    Map.entry("type", "Request")
                )))
            ))
            .integrationAccount(Map.of("id", "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/test-resource-group/providers/Microsoft.Logic/integrationAccounts/test-integration-account"))
            .location("brazilsouth")
            .parameters(Map.of("$connections", Map.of("value", Map.of("test-custom-connector", Map.ofEntries(
                Map.entry("connectionId", "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/test-resource-group/providers/Microsoft.Web/connections/test-custom-connector"),
                Map.entry("connectionName", "test-custom-connector"),
                Map.entry("id", "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/providers/Microsoft.Web/locations/brazilsouth/managedApis/test-custom-connector")
            )))))
            .resourceGroupName("test-resource-group")
            .tags()
            .workflowName("test-workflow")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const workflow = new azure_native.logic.Workflow("workflow", {
    definition: {
        $schema: "https://schema.management.azure.com/providers/Microsoft.Logic/schemas/2016-06-01/workflowdefinition.json#",
        actions: {
            Find_pet_by_ID: {
                inputs: {
                    host: {
                        connection: {
                            name: "@parameters('$connections')['test-custom-connector']['connectionId']",
                        },
                    },
                    method: "get",
                    path: "/pet/@{encodeURIComponent('1')}",
                },
                runAfter: {},
                type: "ApiConnection",
            },
        },
        contentVersion: "1.0.0.0",
        outputs: {},
        parameters: {
            $connections: {
                defaultValue: {},
                type: "Object",
            },
        },
        triggers: {
            manual: {
                inputs: {
                    schema: {},
                },
                kind: "Http",
                type: "Request",
            },
        },
    },
    integrationAccount: {
        id: "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/test-resource-group/providers/Microsoft.Logic/integrationAccounts/test-integration-account",
    },
    location: "brazilsouth",
    parameters: {
        $connections: {
            value: {
                "test-custom-connector": {
                    connectionId: "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/test-resource-group/providers/Microsoft.Web/connections/test-custom-connector",
                    connectionName: "test-custom-connector",
                    id: "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/providers/Microsoft.Web/locations/brazilsouth/managedApis/test-custom-connector",
                },
            },
        },
    },
    resourceGroupName: "test-resource-group",
    tags: {},
    workflowName: "test-workflow",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

workflow = azure_native.logic.Workflow("workflow",
    definition={
        "$schema": "https://schema.management.azure.com/providers/Microsoft.Logic/schemas/2016-06-01/workflowdefinition.json#",
        "actions": {
            "Find_pet_by_ID": {
                "inputs": {
                    "host": {
                        "connection": {
                            "name": "@parameters('$connections')['test-custom-connector']['connectionId']",
                        },
                    },
                    "method": "get",
                    "path": "/pet/@{encodeURIComponent('1')}",
                },
                "runAfter": {},
                "type": "ApiConnection",
            },
        },
        "contentVersion": "1.0.0.0",
        "outputs": {},
        "parameters": {
            "$connections": {
                "defaultValue": {},
                "type": "Object",
            },
        },
        "triggers": {
            "manual": {
                "inputs": {
                    "schema": {},
                },
                "kind": "Http",
                "type": "Request",
            },
        },
    },
    integration_account=azure_native.logic.ResourceReferenceArgs(
        id="/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/test-resource-group/providers/Microsoft.Logic/integrationAccounts/test-integration-account",
    ),
    location="brazilsouth",
    parameters={
        "$connections": azure_native.logic.WorkflowParameterArgs(
            value={
                "test-custom-connector": {
                    "connectionId": "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/test-resource-group/providers/Microsoft.Web/connections/test-custom-connector",
                    "connectionName": "test-custom-connector",
                    "id": "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/providers/Microsoft.Web/locations/brazilsouth/managedApis/test-custom-connector",
                },
            },
        ),
    },
    resource_group_name="test-resource-group",
    tags={},
    workflow_name="test-workflow")

```

```yaml
resources:
  workflow:
    type: azure-native:logic:Workflow
    properties:
      definition:
        $schema: https://schema.management.azure.com/providers/Microsoft.Logic/schemas/2016-06-01/workflowdefinition.json#
        actions:
          Find_pet_by_ID:
            inputs:
              host:
                connection:
                  name: '@parameters(''$connections'')[''test-custom-connector''][''connectionId'']'
              method: get
              path: /pet/@{encodeURIComponent('1')}
            runAfter: {}
            type: ApiConnection
        contentVersion: 1.0.0.0
        outputs: {}
        parameters:
          $connections:
            defaultValue: {}
            type: Object
        triggers:
          manual:
            inputs:
              schema: {}
            kind: Http
            type: Request
      integrationAccount:
        id: /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/test-resource-group/providers/Microsoft.Logic/integrationAccounts/test-integration-account
      location: brazilsouth
      parameters:
        $connections:
          value:
            test-custom-connector:
              connectionId: /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/test-resource-group/providers/Microsoft.Web/connections/test-custom-connector
              connectionName: test-custom-connector
              id: /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/providers/Microsoft.Web/locations/brazilsouth/managedApis/test-custom-connector
      resourceGroupName: test-resource-group
      tags: {}
      workflowName: test-workflow

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:logic:Workflow myresource1 /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Logic/workflows/{workflowName} 
```
