Tenant configuration.
API Version: 2020-09-01-preview.
Previous API Version: 2020-09-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update Tenant configuration
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var tenantConfiguration = new AzureNative.Portal.TenantConfiguration("tenantConfiguration", new()
    {
        ConfigurationName = "default",
        EnforcePrivateMarkdownStorage = true,
    });

});


```

```go
package main

import (
	portal "github.com/pulumi/pulumi-azure-native-sdk/portal"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := portal.NewTenantConfiguration(ctx, "tenantConfiguration", &portal.TenantConfigurationArgs{
			ConfigurationName:             pulumi.String("default"),
			EnforcePrivateMarkdownStorage: pulumi.Bool(true),
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
import com.pulumi.azurenative.portal.TenantConfiguration;
import com.pulumi.azurenative.portal.TenantConfigurationArgs;
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
        var tenantConfiguration = new TenantConfiguration("tenantConfiguration", TenantConfigurationArgs.builder()        
            .configurationName("default")
            .enforcePrivateMarkdownStorage(true)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const tenantConfiguration = new azure_native.portal.TenantConfiguration("tenantConfiguration", {
    configurationName: "default",
    enforcePrivateMarkdownStorage: true,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

tenant_configuration = azure_native.portal.TenantConfiguration("tenantConfiguration",
    configuration_name="default",
    enforce_private_markdown_storage=True)

```

```yaml
resources:
  tenantConfiguration:
    type: azure-native:portal:TenantConfiguration
    properties:
      configurationName: default
      enforcePrivateMarkdownStorage: true

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:portal:TenantConfiguration default /providers/Microsoft.Portal/tenantConfigurations/default 
```
