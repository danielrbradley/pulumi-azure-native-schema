A managed server DNS alias.
API Version: 2021-11-01.
Previous API Version: 2021-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create managed server DNS alias
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedServerDnsAlias = new AzureNative.Sql.ManagedServerDnsAlias("managedServerDnsAlias", new()
    {
        DnsAliasName = "dns-alias-mi",
        ManagedInstanceName = "dns-mi",
        ResourceGroupName = "Default",
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
		_, err := sql.NewManagedServerDnsAlias(ctx, "managedServerDnsAlias", &sql.ManagedServerDnsAliasArgs{
			DnsAliasName:        pulumi.String("dns-alias-mi"),
			ManagedInstanceName: pulumi.String("dns-mi"),
			ResourceGroupName:   pulumi.String("Default"),
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
import com.pulumi.azurenative.sql.ManagedServerDnsAlias;
import com.pulumi.azurenative.sql.ManagedServerDnsAliasArgs;
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
        var managedServerDnsAlias = new ManagedServerDnsAlias("managedServerDnsAlias", ManagedServerDnsAliasArgs.builder()        
            .dnsAliasName("dns-alias-mi")
            .managedInstanceName("dns-mi")
            .resourceGroupName("Default")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedServerDnsAlias = new azure_native.sql.ManagedServerDnsAlias("managedServerDnsAlias", {
    dnsAliasName: "dns-alias-mi",
    managedInstanceName: "dns-mi",
    resourceGroupName: "Default",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_server_dns_alias = azure_native.sql.ManagedServerDnsAlias("managedServerDnsAlias",
    dns_alias_name="dns-alias-mi",
    managed_instance_name="dns-mi",
    resource_group_name="Default")

```

```yaml
resources:
  managedServerDnsAlias:
    type: azure-native:sql:ManagedServerDnsAlias
    properties:
      dnsAliasName: dns-alias-mi
      managedInstanceName: dns-mi
      resourceGroupName: Default

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:ManagedServerDnsAlias dns-alias-mi /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/managedInstances/dns-mi/dnsAliases/dns-alias-mi 
```
