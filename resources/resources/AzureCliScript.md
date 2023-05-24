Object model for the Azure CLI script.
API Version: 2020-10-01.
Previous API Version: 2020-10-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### DeploymentScriptsCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var azureCliScript = new AzureNative.Resources.AzureCliScript("azureCliScript", new()
    {
        ResourceGroupName = "script-rg",
        ScriptName = "MyDeploymentScript",
    });

});


```

```go
package main

import (
	resources "github.com/pulumi/pulumi-azure-native-sdk/resources"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := resources.NewAzureCliScript(ctx, "azureCliScript", &resources.AzureCliScriptArgs{
			ResourceGroupName: pulumi.String("script-rg"),
			ScriptName:        pulumi.String("MyDeploymentScript"),
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
import com.pulumi.azurenative.resources.AzureCliScript;
import com.pulumi.azurenative.resources.AzureCliScriptArgs;
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
        var azureCliScript = new AzureCliScript("azureCliScript", AzureCliScriptArgs.builder()        
            .resourceGroupName("script-rg")
            .scriptName("MyDeploymentScript")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const azureCliScript = new azure_native.resources.AzureCliScript("azureCliScript", {
    resourceGroupName: "script-rg",
    scriptName: "MyDeploymentScript",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

azure_cli_script = azure_native.resources.AzureCliScript("azureCliScript",
    resource_group_name="script-rg",
    script_name="MyDeploymentScript")

```

```yaml
resources:
  azureCliScript:
    type: azure-native:resources:AzureCliScript
    properties:
      resourceGroupName: script-rg
      scriptName: MyDeploymentScript

```

{{% /example %}}
{{% example %}}
### DeploymentScriptsCreateNoUserManagedIdentity
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var azureCliScript = new AzureNative.Resources.AzureCliScript("azureCliScript", new()
    {
        ResourceGroupName = "script-rg",
        ScriptName = "MyDeploymentScript",
    });

});


```

```go
package main

import (
	resources "github.com/pulumi/pulumi-azure-native-sdk/resources"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := resources.NewAzureCliScript(ctx, "azureCliScript", &resources.AzureCliScriptArgs{
			ResourceGroupName: pulumi.String("script-rg"),
			ScriptName:        pulumi.String("MyDeploymentScript"),
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
import com.pulumi.azurenative.resources.AzureCliScript;
import com.pulumi.azurenative.resources.AzureCliScriptArgs;
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
        var azureCliScript = new AzureCliScript("azureCliScript", AzureCliScriptArgs.builder()        
            .resourceGroupName("script-rg")
            .scriptName("MyDeploymentScript")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const azureCliScript = new azure_native.resources.AzureCliScript("azureCliScript", {
    resourceGroupName: "script-rg",
    scriptName: "MyDeploymentScript",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

azure_cli_script = azure_native.resources.AzureCliScript("azureCliScript",
    resource_group_name="script-rg",
    script_name="MyDeploymentScript")

```

```yaml
resources:
  azureCliScript:
    type: azure-native:resources:AzureCliScript
    properties:
      resourceGroupName: script-rg
      scriptName: MyDeploymentScript

```

{{% /example %}}
{{% example %}}
### DeploymentScriptsCreate_MinCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var azureCliScript = new AzureNative.Resources.AzureCliScript("azureCliScript", new()
    {
        ResourceGroupName = "script-rg",
        ScriptName = "MyDeploymentScript",
    });

});


```

```go
package main

import (
	resources "github.com/pulumi/pulumi-azure-native-sdk/resources"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := resources.NewAzureCliScript(ctx, "azureCliScript", &resources.AzureCliScriptArgs{
			ResourceGroupName: pulumi.String("script-rg"),
			ScriptName:        pulumi.String("MyDeploymentScript"),
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
import com.pulumi.azurenative.resources.AzureCliScript;
import com.pulumi.azurenative.resources.AzureCliScriptArgs;
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
        var azureCliScript = new AzureCliScript("azureCliScript", AzureCliScriptArgs.builder()        
            .resourceGroupName("script-rg")
            .scriptName("MyDeploymentScript")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const azureCliScript = new azure_native.resources.AzureCliScript("azureCliScript", {
    resourceGroupName: "script-rg",
    scriptName: "MyDeploymentScript",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

azure_cli_script = azure_native.resources.AzureCliScript("azureCliScript",
    resource_group_name="script-rg",
    script_name="MyDeploymentScript")

```

```yaml
resources:
  azureCliScript:
    type: azure-native:resources:AzureCliScript
    properties:
      resourceGroupName: script-rg
      scriptName: MyDeploymentScript

```

{{% /example %}}
{{% example %}}
### DeploymentScriptsCreate_UsingCustomACIName
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var azureCliScript = new AzureNative.Resources.AzureCliScript("azureCliScript", new()
    {
        ResourceGroupName = "script-rg",
        ScriptName = "MyDeploymentScript",
    });

});


```

```go
package main

import (
	resources "github.com/pulumi/pulumi-azure-native-sdk/resources"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := resources.NewAzureCliScript(ctx, "azureCliScript", &resources.AzureCliScriptArgs{
			ResourceGroupName: pulumi.String("script-rg"),
			ScriptName:        pulumi.String("MyDeploymentScript"),
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
import com.pulumi.azurenative.resources.AzureCliScript;
import com.pulumi.azurenative.resources.AzureCliScriptArgs;
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
        var azureCliScript = new AzureCliScript("azureCliScript", AzureCliScriptArgs.builder()        
            .resourceGroupName("script-rg")
            .scriptName("MyDeploymentScript")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const azureCliScript = new azure_native.resources.AzureCliScript("azureCliScript", {
    resourceGroupName: "script-rg",
    scriptName: "MyDeploymentScript",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

azure_cli_script = azure_native.resources.AzureCliScript("azureCliScript",
    resource_group_name="script-rg",
    script_name="MyDeploymentScript")

```

```yaml
resources:
  azureCliScript:
    type: azure-native:resources:AzureCliScript
    properties:
      resourceGroupName: script-rg
      scriptName: MyDeploymentScript

```

{{% /example %}}
{{% example %}}
### DeploymentScriptsCreate_UsingExistingStorageAccount
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var azureCliScript = new AzureNative.Resources.AzureCliScript("azureCliScript", new()
    {
        ResourceGroupName = "script-rg",
        ScriptName = "MyDeploymentScript",
    });

});


```

```go
package main

import (
	resources "github.com/pulumi/pulumi-azure-native-sdk/resources"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := resources.NewAzureCliScript(ctx, "azureCliScript", &resources.AzureCliScriptArgs{
			ResourceGroupName: pulumi.String("script-rg"),
			ScriptName:        pulumi.String("MyDeploymentScript"),
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
import com.pulumi.azurenative.resources.AzureCliScript;
import com.pulumi.azurenative.resources.AzureCliScriptArgs;
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
        var azureCliScript = new AzureCliScript("azureCliScript", AzureCliScriptArgs.builder()        
            .resourceGroupName("script-rg")
            .scriptName("MyDeploymentScript")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const azureCliScript = new azure_native.resources.AzureCliScript("azureCliScript", {
    resourceGroupName: "script-rg",
    scriptName: "MyDeploymentScript",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

azure_cli_script = azure_native.resources.AzureCliScript("azureCliScript",
    resource_group_name="script-rg",
    script_name="MyDeploymentScript")

```

```yaml
resources:
  azureCliScript:
    type: azure-native:resources:AzureCliScript
    properties:
      resourceGroupName: script-rg
      scriptName: MyDeploymentScript

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:resources:AzureCliScript myresource1 /subscriptions/{subscriptionId}/resourcegroups/{resourceGroupName}/providers/Microsoft.Resources/deploymentScripts/{scriptName} 
```
