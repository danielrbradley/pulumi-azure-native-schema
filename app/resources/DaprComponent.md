Dapr Component.
API Version: 2022-10-01.
Previous API Version: 2022-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update dapr component with secret store component
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var daprComponent = new AzureNative.App.DaprComponent("daprComponent", new()
    {
        ComponentName = "reddog",
        ComponentType = "state.azure.cosmosdb",
        EnvironmentName = "myenvironment",
        IgnoreErrors = false,
        InitTimeout = "50s",
        Metadata = new[]
        {
            new AzureNative.App.Inputs.DaprMetadataArgs
            {
                Name = "url",
                Value = "<COSMOS-URL>",
            },
            new AzureNative.App.Inputs.DaprMetadataArgs
            {
                Name = "database",
                Value = "itemsDB",
            },
            new AzureNative.App.Inputs.DaprMetadataArgs
            {
                Name = "collection",
                Value = "items",
            },
            new AzureNative.App.Inputs.DaprMetadataArgs
            {
                Name = "masterkey",
                SecretRef = "masterkey",
            },
        },
        ResourceGroupName = "examplerg",
        Scopes = new[]
        {
            "container-app-1",
            "container-app-2",
        },
        SecretStoreComponent = "my-secret-store",
        Version = "v1",
    });

});


```

```go
package main

import (
	app "github.com/pulumi/pulumi-azure-native-sdk/app"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := app.NewDaprComponent(ctx, "daprComponent", &app.DaprComponentArgs{
			ComponentName:   pulumi.String("reddog"),
			ComponentType:   pulumi.String("state.azure.cosmosdb"),
			EnvironmentName: pulumi.String("myenvironment"),
			IgnoreErrors:    pulumi.Bool(false),
			InitTimeout:     pulumi.String("50s"),
			Metadata: []app.DaprMetadataArgs{
				{
					Name:  pulumi.String("url"),
					Value: pulumi.String("<COSMOS-URL>"),
				},
				{
					Name:  pulumi.String("database"),
					Value: pulumi.String("itemsDB"),
				},
				{
					Name:  pulumi.String("collection"),
					Value: pulumi.String("items"),
				},
				{
					Name:      pulumi.String("masterkey"),
					SecretRef: pulumi.String("masterkey"),
				},
			},
			ResourceGroupName: pulumi.String("examplerg"),
			Scopes: pulumi.StringArray{
				pulumi.String("container-app-1"),
				pulumi.String("container-app-2"),
			},
			SecretStoreComponent: pulumi.String("my-secret-store"),
			Version:              pulumi.String("v1"),
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
import com.pulumi.azurenative.app.DaprComponent;
import com.pulumi.azurenative.app.DaprComponentArgs;
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
        var daprComponent = new DaprComponent("daprComponent", DaprComponentArgs.builder()        
            .componentName("reddog")
            .componentType("state.azure.cosmosdb")
            .environmentName("myenvironment")
            .ignoreErrors(false)
            .initTimeout("50s")
            .metadata(            
                Map.ofEntries(
                    Map.entry("name", "url"),
                    Map.entry("value", "<COSMOS-URL>")
                ),
                Map.ofEntries(
                    Map.entry("name", "database"),
                    Map.entry("value", "itemsDB")
                ),
                Map.ofEntries(
                    Map.entry("name", "collection"),
                    Map.entry("value", "items")
                ),
                Map.ofEntries(
                    Map.entry("name", "masterkey"),
                    Map.entry("secretRef", "masterkey")
                ))
            .resourceGroupName("examplerg")
            .scopes(            
                "container-app-1",
                "container-app-2")
            .secretStoreComponent("my-secret-store")
            .version("v1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const daprComponent = new azure_native.app.DaprComponent("daprComponent", {
    componentName: "reddog",
    componentType: "state.azure.cosmosdb",
    environmentName: "myenvironment",
    ignoreErrors: false,
    initTimeout: "50s",
    metadata: [
        {
            name: "url",
            value: "<COSMOS-URL>",
        },
        {
            name: "database",
            value: "itemsDB",
        },
        {
            name: "collection",
            value: "items",
        },
        {
            name: "masterkey",
            secretRef: "masterkey",
        },
    ],
    resourceGroupName: "examplerg",
    scopes: [
        "container-app-1",
        "container-app-2",
    ],
    secretStoreComponent: "my-secret-store",
    version: "v1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

dapr_component = azure_native.app.DaprComponent("daprComponent",
    component_name="reddog",
    component_type="state.azure.cosmosdb",
    environment_name="myenvironment",
    ignore_errors=False,
    init_timeout="50s",
    metadata=[
        azure_native.app.DaprMetadataArgs(
            name="url",
            value="<COSMOS-URL>",
        ),
        azure_native.app.DaprMetadataArgs(
            name="database",
            value="itemsDB",
        ),
        azure_native.app.DaprMetadataArgs(
            name="collection",
            value="items",
        ),
        azure_native.app.DaprMetadataArgs(
            name="masterkey",
            secret_ref="masterkey",
        ),
    ],
    resource_group_name="examplerg",
    scopes=[
        "container-app-1",
        "container-app-2",
    ],
    secret_store_component="my-secret-store",
    version="v1")

```

```yaml
resources:
  daprComponent:
    type: azure-native:app:DaprComponent
    properties:
      componentName: reddog
      componentType: state.azure.cosmosdb
      environmentName: myenvironment
      ignoreErrors: false
      initTimeout: 50s
      metadata:
        - name: url
          value: <COSMOS-URL>
        - name: database
          value: itemsDB
        - name: collection
          value: items
        - name: masterkey
          secretRef: masterkey
      resourceGroupName: examplerg
      scopes:
        - container-app-1
        - container-app-2
      secretStoreComponent: my-secret-store
      version: v1

```

{{% /example %}}
{{% example %}}
### Create or update dapr component with secrets
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var daprComponent = new AzureNative.App.DaprComponent("daprComponent", new()
    {
        ComponentName = "reddog",
        ComponentType = "state.azure.cosmosdb",
        EnvironmentName = "myenvironment",
        IgnoreErrors = false,
        InitTimeout = "50s",
        Metadata = new[]
        {
            new AzureNative.App.Inputs.DaprMetadataArgs
            {
                Name = "url",
                Value = "<COSMOS-URL>",
            },
            new AzureNative.App.Inputs.DaprMetadataArgs
            {
                Name = "database",
                Value = "itemsDB",
            },
            new AzureNative.App.Inputs.DaprMetadataArgs
            {
                Name = "collection",
                Value = "items",
            },
            new AzureNative.App.Inputs.DaprMetadataArgs
            {
                Name = "masterkey",
                SecretRef = "masterkey",
            },
        },
        ResourceGroupName = "examplerg",
        Scopes = new[]
        {
            "container-app-1",
            "container-app-2",
        },
        Secrets = new[]
        {
            new AzureNative.App.Inputs.SecretArgs
            {
                Name = "masterkey",
                Value = "keyvalue",
            },
        },
        Version = "v1",
    });

});


```

```go
package main

import (
	app "github.com/pulumi/pulumi-azure-native-sdk/app"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := app.NewDaprComponent(ctx, "daprComponent", &app.DaprComponentArgs{
			ComponentName:   pulumi.String("reddog"),
			ComponentType:   pulumi.String("state.azure.cosmosdb"),
			EnvironmentName: pulumi.String("myenvironment"),
			IgnoreErrors:    pulumi.Bool(false),
			InitTimeout:     pulumi.String("50s"),
			Metadata: []app.DaprMetadataArgs{
				{
					Name:  pulumi.String("url"),
					Value: pulumi.String("<COSMOS-URL>"),
				},
				{
					Name:  pulumi.String("database"),
					Value: pulumi.String("itemsDB"),
				},
				{
					Name:  pulumi.String("collection"),
					Value: pulumi.String("items"),
				},
				{
					Name:      pulumi.String("masterkey"),
					SecretRef: pulumi.String("masterkey"),
				},
			},
			ResourceGroupName: pulumi.String("examplerg"),
			Scopes: pulumi.StringArray{
				pulumi.String("container-app-1"),
				pulumi.String("container-app-2"),
			},
			Secrets: []app.SecretArgs{
				{
					Name:  pulumi.String("masterkey"),
					Value: pulumi.String("keyvalue"),
				},
			},
			Version: pulumi.String("v1"),
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
import com.pulumi.azurenative.app.DaprComponent;
import com.pulumi.azurenative.app.DaprComponentArgs;
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
        var daprComponent = new DaprComponent("daprComponent", DaprComponentArgs.builder()        
            .componentName("reddog")
            .componentType("state.azure.cosmosdb")
            .environmentName("myenvironment")
            .ignoreErrors(false)
            .initTimeout("50s")
            .metadata(            
                Map.ofEntries(
                    Map.entry("name", "url"),
                    Map.entry("value", "<COSMOS-URL>")
                ),
                Map.ofEntries(
                    Map.entry("name", "database"),
                    Map.entry("value", "itemsDB")
                ),
                Map.ofEntries(
                    Map.entry("name", "collection"),
                    Map.entry("value", "items")
                ),
                Map.ofEntries(
                    Map.entry("name", "masterkey"),
                    Map.entry("secretRef", "masterkey")
                ))
            .resourceGroupName("examplerg")
            .scopes(            
                "container-app-1",
                "container-app-2")
            .secrets(Map.ofEntries(
                Map.entry("name", "masterkey"),
                Map.entry("value", "keyvalue")
            ))
            .version("v1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const daprComponent = new azure_native.app.DaprComponent("daprComponent", {
    componentName: "reddog",
    componentType: "state.azure.cosmosdb",
    environmentName: "myenvironment",
    ignoreErrors: false,
    initTimeout: "50s",
    metadata: [
        {
            name: "url",
            value: "<COSMOS-URL>",
        },
        {
            name: "database",
            value: "itemsDB",
        },
        {
            name: "collection",
            value: "items",
        },
        {
            name: "masterkey",
            secretRef: "masterkey",
        },
    ],
    resourceGroupName: "examplerg",
    scopes: [
        "container-app-1",
        "container-app-2",
    ],
    secrets: [{
        name: "masterkey",
        value: "keyvalue",
    }],
    version: "v1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

dapr_component = azure_native.app.DaprComponent("daprComponent",
    component_name="reddog",
    component_type="state.azure.cosmosdb",
    environment_name="myenvironment",
    ignore_errors=False,
    init_timeout="50s",
    metadata=[
        azure_native.app.DaprMetadataArgs(
            name="url",
            value="<COSMOS-URL>",
        ),
        azure_native.app.DaprMetadataArgs(
            name="database",
            value="itemsDB",
        ),
        azure_native.app.DaprMetadataArgs(
            name="collection",
            value="items",
        ),
        azure_native.app.DaprMetadataArgs(
            name="masterkey",
            secret_ref="masterkey",
        ),
    ],
    resource_group_name="examplerg",
    scopes=[
        "container-app-1",
        "container-app-2",
    ],
    secrets=[azure_native.app.SecretArgs(
        name="masterkey",
        value="keyvalue",
    )],
    version="v1")

```

```yaml
resources:
  daprComponent:
    type: azure-native:app:DaprComponent
    properties:
      componentName: reddog
      componentType: state.azure.cosmosdb
      environmentName: myenvironment
      ignoreErrors: false
      initTimeout: 50s
      metadata:
        - name: url
          value: <COSMOS-URL>
        - name: database
          value: itemsDB
        - name: collection
          value: items
        - name: masterkey
          secretRef: masterkey
      resourceGroupName: examplerg
      scopes:
        - container-app-1
        - container-app-2
      secrets:
        - name: masterkey
          value: keyvalue
      version: v1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:app:DaprComponent reddog /subscriptions/8efdecc5-919e-44eb-b179-915dca89ebf9/resourceGroups/examplerg/providers/Microsoft.App/managedEnvironments/jlaw-demo1/daprcomponents/reddog 
```
