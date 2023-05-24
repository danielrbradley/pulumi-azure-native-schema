A server DNS alias.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create server DNS alias
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var serverDnsAlias = new AzureNative.Sql.ServerDnsAlias("serverDnsAlias", new()
    {
        DnsAliasName = "dns-alias-name-1",
        ResourceGroupName = "Default",
        ServerName = "dns-alias-server",
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
		_, err := sql.NewServerDnsAlias(ctx, "serverDnsAlias", &sql.ServerDnsAliasArgs{
			DnsAliasName:      pulumi.String("dns-alias-name-1"),
			ResourceGroupName: pulumi.String("Default"),
			ServerName:        pulumi.String("dns-alias-server"),
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
import com.pulumi.azurenative.sql.ServerDnsAlias;
import com.pulumi.azurenative.sql.ServerDnsAliasArgs;
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
        var serverDnsAlias = new ServerDnsAlias("serverDnsAlias", ServerDnsAliasArgs.builder()        
            .dnsAliasName("dns-alias-name-1")
            .resourceGroupName("Default")
            .serverName("dns-alias-server")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const serverDnsAlias = new azure_native.sql.ServerDnsAlias("serverDnsAlias", {
    dnsAliasName: "dns-alias-name-1",
    resourceGroupName: "Default",
    serverName: "dns-alias-server",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

server_dns_alias = azure_native.sql.ServerDnsAlias("serverDnsAlias",
    dns_alias_name="dns-alias-name-1",
    resource_group_name="Default",
    server_name="dns-alias-server")

```

```yaml
resources:
  serverDnsAlias:
    type: azure-native:sql:ServerDnsAlias
    properties:
      dnsAliasName: dns-alias-name-1
      resourceGroupName: Default
      serverName: dns-alias-server

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:ServerDnsAlias dns-alias-name-1 /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/servers/dns-alias-server/dnsAliases/dns-alias-name-1 
```
