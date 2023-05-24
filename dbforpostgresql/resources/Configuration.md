Represents a Configuration.
API Version: 2022-12-01.
Previous API Version: 2017-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Update a user configuration
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var configuration = new AzureNative.DBforPostgreSQL.Configuration("configuration", new()
    {
        ConfigurationName = "event_scheduler",
        ResourceGroupName = "testrg",
        ServerName = "testserver",
        Source = "user-override",
        Value = "on",
    });

});


```

```go
package main

import (
	dbforpostgresql "github.com/pulumi/pulumi-azure-native-sdk/dbforpostgresql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := dbforpostgresql.NewConfiguration(ctx, "configuration", &dbforpostgresql.ConfigurationArgs{
			ConfigurationName: pulumi.String("event_scheduler"),
			ResourceGroupName: pulumi.String("testrg"),
			ServerName:        pulumi.String("testserver"),
			Source:            pulumi.String("user-override"),
			Value:             pulumi.String("on"),
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
import com.pulumi.azurenative.dbforpostgresql.Configuration;
import com.pulumi.azurenative.dbforpostgresql.ConfigurationArgs;
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
        var configuration = new Configuration("configuration", ConfigurationArgs.builder()        
            .configurationName("event_scheduler")
            .resourceGroupName("testrg")
            .serverName("testserver")
            .source("user-override")
            .value("on")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const configuration = new azure_native.dbforpostgresql.Configuration("configuration", {
    configurationName: "event_scheduler",
    resourceGroupName: "testrg",
    serverName: "testserver",
    source: "user-override",
    value: "on",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

configuration = azure_native.dbforpostgresql.Configuration("configuration",
    configuration_name="event_scheduler",
    resource_group_name="testrg",
    server_name="testserver",
    source="user-override",
    value="on")

```

```yaml
resources:
  configuration:
    type: azure-native:dbforpostgresql:Configuration
    properties:
      configurationName: event_scheduler
      resourceGroupName: testrg
      serverName: testserver
      source: user-override
      value: on

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:dbforpostgresql:Configuration event_scheduler /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.DBforPostgreSQL/flexibleServers/testserver/configurations/event_scheduler 
```
