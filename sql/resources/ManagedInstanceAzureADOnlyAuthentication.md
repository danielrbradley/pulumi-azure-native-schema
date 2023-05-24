Azure Active Directory only authentication.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates or updates Azure Active Directory only authentication object.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedInstanceAzureADOnlyAuthentication = new AzureNative.Sql.ManagedInstanceAzureADOnlyAuthentication("managedInstanceAzureADOnlyAuthentication", new()
    {
        AuthenticationName = "Default",
        AzureADOnlyAuthentication = false,
        ManagedInstanceName = "managedInstance",
        ResourceGroupName = "Default-SQL-SouthEastAsia",
    });

});


```

```go
package main

import (
	sql "github.com/pulumi/pulumi-azure-native-sdk/sql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := sql.NewManagedInstanceAzureADOnlyAuthentication(ctx, "managedInstanceAzureADOnlyAuthentication", &sql.ManagedInstanceAzureADOnlyAuthenticationArgs{
			AuthenticationName:        pulumi.String("Default"),
			AzureADOnlyAuthentication: pulumi.Bool(false),
			ManagedInstanceName:       pulumi.String("managedInstance"),
			ResourceGroupName:         pulumi.String("Default-SQL-SouthEastAsia"),
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
import com.pulumi.azurenative.sql.ManagedInstanceAzureADOnlyAuthentication;
import com.pulumi.azurenative.sql.ManagedInstanceAzureADOnlyAuthenticationArgs;
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
        var managedInstanceAzureADOnlyAuthentication = new ManagedInstanceAzureADOnlyAuthentication("managedInstanceAzureADOnlyAuthentication", ManagedInstanceAzureADOnlyAuthenticationArgs.builder()        
            .authenticationName("Default")
            .azureADOnlyAuthentication(false)
            .managedInstanceName("managedInstance")
            .resourceGroupName("Default-SQL-SouthEastAsia")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedInstanceAzureADOnlyAuthentication = new azure_native.sql.ManagedInstanceAzureADOnlyAuthentication("managedInstanceAzureADOnlyAuthentication", {
    authenticationName: "Default",
    azureADOnlyAuthentication: false,
    managedInstanceName: "managedInstance",
    resourceGroupName: "Default-SQL-SouthEastAsia",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_instance_azure_ad_only_authentication = azure_native.sql.ManagedInstanceAzureADOnlyAuthentication("managedInstanceAzureADOnlyAuthentication",
    authentication_name="Default",
    azure_ad_only_authentication=False,
    managed_instance_name="managedInstance",
    resource_group_name="Default-SQL-SouthEastAsia")

```

```yaml
resources:
  managedInstanceAzureADOnlyAuthentication:
    type: azure-native:sql:ManagedInstanceAzureADOnlyAuthentication
    properties:
      authenticationName: Default
      azureADOnlyAuthentication: false
      managedInstanceName: managedInstance
      resourceGroupName: Default-SQL-SouthEastAsia

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:ManagedInstanceAzureADOnlyAuthentication Default /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/azureADOnlyAuthentications/providers/Microsoft.Sql/managedInstances/managedInstance/azureadonlyauthentications/default 
```
