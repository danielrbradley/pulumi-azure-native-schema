A SQL server registration.
API Version: 2019-07-24-preview.
Previous API Version: 2019-07-24-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates or updates a SQL Server registration.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sqlServerRegistration = new AzureNative.AzureData.SqlServerRegistration("sqlServerRegistration", new()
    {
        Location = "northeurope",
        ResourceGroupName = "testrg",
        SqlServerRegistrationName = "testsqlregistration",
        Tags = 
        {
            { "mytag", "myval" },
        },
    });

});


```

```go
package main

import (
	azuredata "github.com/pulumi/pulumi-azure-native-sdk/azuredata"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := azuredata.NewSqlServerRegistration(ctx, "sqlServerRegistration", &azuredata.SqlServerRegistrationArgs{
			Location:                  pulumi.String("northeurope"),
			ResourceGroupName:         pulumi.String("testrg"),
			SqlServerRegistrationName: pulumi.String("testsqlregistration"),
			Tags: pulumi.StringMap{
				"mytag": pulumi.String("myval"),
			},
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
import com.pulumi.azurenative.azuredata.SqlServerRegistration;
import com.pulumi.azurenative.azuredata.SqlServerRegistrationArgs;
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
        var sqlServerRegistration = new SqlServerRegistration("sqlServerRegistration", SqlServerRegistrationArgs.builder()        
            .location("northeurope")
            .resourceGroupName("testrg")
            .sqlServerRegistrationName("testsqlregistration")
            .tags(Map.of("mytag", "myval"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sqlServerRegistration = new azure_native.azuredata.SqlServerRegistration("sqlServerRegistration", {
    location: "northeurope",
    resourceGroupName: "testrg",
    sqlServerRegistrationName: "testsqlregistration",
    tags: {
        mytag: "myval",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sql_server_registration = azure_native.azuredata.SqlServerRegistration("sqlServerRegistration",
    location="northeurope",
    resource_group_name="testrg",
    sql_server_registration_name="testsqlregistration",
    tags={
        "mytag": "myval",
    })

```

```yaml
resources:
  sqlServerRegistration:
    type: azure-native:azuredata:SqlServerRegistration
    properties:
      location: northeurope
      resourceGroupName: testrg
      sqlServerRegistrationName: testsqlregistration
      tags:
        mytag: myval

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:azuredata:SqlServerRegistration testsqlregistration /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.AzureData/SqlServerRegistrations/testsqlregistration 
```
