Single item in List or Get Migration Config operation
API Version: 2021-11-01.
Previous API Version: 2017-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### MigrationConfigurationsStartMigration
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var migrationConfig = new AzureNative.ServiceBus.MigrationConfig("migrationConfig", new()
    {
        ConfigName = "$default",
        NamespaceName = "sdk-Namespace-41",
        PostMigrationName = "sdk-PostMigration-5919",
        ResourceGroupName = "ResourceGroup",
        TargetNamespace = "/subscriptions/SubscriptionId/resourceGroups/ResourceGroup/providers/Microsoft.ServiceBus/namespaces/sdk-Namespace-4028",
    });

});


```

```go
package main

import (
	servicebus "github.com/pulumi/pulumi-azure-native-sdk/servicebus"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := servicebus.NewMigrationConfig(ctx, "migrationConfig", &servicebus.MigrationConfigArgs{
			ConfigName:        pulumi.String("$default"),
			NamespaceName:     pulumi.String("sdk-Namespace-41"),
			PostMigrationName: pulumi.String("sdk-PostMigration-5919"),
			ResourceGroupName: pulumi.String("ResourceGroup"),
			TargetNamespace:   pulumi.String("/subscriptions/SubscriptionId/resourceGroups/ResourceGroup/providers/Microsoft.ServiceBus/namespaces/sdk-Namespace-4028"),
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
import com.pulumi.azurenative.servicebus.MigrationConfig;
import com.pulumi.azurenative.servicebus.MigrationConfigArgs;
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
        var migrationConfig = new MigrationConfig("migrationConfig", MigrationConfigArgs.builder()        
            .configName("$default")
            .namespaceName("sdk-Namespace-41")
            .postMigrationName("sdk-PostMigration-5919")
            .resourceGroupName("ResourceGroup")
            .targetNamespace("/subscriptions/SubscriptionId/resourceGroups/ResourceGroup/providers/Microsoft.ServiceBus/namespaces/sdk-Namespace-4028")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const migrationConfig = new azure_native.servicebus.MigrationConfig("migrationConfig", {
    configName: "$default",
    namespaceName: "sdk-Namespace-41",
    postMigrationName: "sdk-PostMigration-5919",
    resourceGroupName: "ResourceGroup",
    targetNamespace: "/subscriptions/SubscriptionId/resourceGroups/ResourceGroup/providers/Microsoft.ServiceBus/namespaces/sdk-Namespace-4028",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

migration_config = azure_native.servicebus.MigrationConfig("migrationConfig",
    config_name="$default",
    namespace_name="sdk-Namespace-41",
    post_migration_name="sdk-PostMigration-5919",
    resource_group_name="ResourceGroup",
    target_namespace="/subscriptions/SubscriptionId/resourceGroups/ResourceGroup/providers/Microsoft.ServiceBus/namespaces/sdk-Namespace-4028")

```

```yaml
resources:
  migrationConfig:
    type: azure-native:servicebus:MigrationConfig
    properties:
      configName: $default
      namespaceName: sdk-Namespace-41
      postMigrationName: sdk-PostMigration-5919
      resourceGroupName: ResourceGroup
      targetNamespace: /subscriptions/SubscriptionId/resourceGroups/ResourceGroup/providers/Microsoft.ServiceBus/namespaces/sdk-Namespace-4028

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:servicebus:MigrationConfig sdk-Namespace-41 /subscriptions/SubscriptionId/resourceGroups/ResourceGroup/providers/Microsoft.ServiceBus/namespaces/sdk-Namespace-41/migrationConfigs/$default 
```
