
API Version: 2019-10-01.
Previous API Version: 2019-10-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ImportCollectors_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var importCollector = new AzureNative.Migrate.ImportCollector("importCollector", new()
    {
        ImportCollectorName = "importCollector2952",
        ProjectName = "rajoshCCY9671project",
        ResourceGroupName = "markusavstestrg",
    });

});


```

```go
package main

import (
	migrate "github.com/pulumi/pulumi-azure-native-sdk/migrate"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := migrate.NewImportCollector(ctx, "importCollector", &migrate.ImportCollectorArgs{
			ImportCollectorName: pulumi.String("importCollector2952"),
			ProjectName:         pulumi.String("rajoshCCY9671project"),
			ResourceGroupName:   pulumi.String("markusavstestrg"),
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
import com.pulumi.azurenative.migrate.ImportCollector;
import com.pulumi.azurenative.migrate.ImportCollectorArgs;
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
        var importCollector = new ImportCollector("importCollector", ImportCollectorArgs.builder()        
            .importCollectorName("importCollector2952")
            .projectName("rajoshCCY9671project")
            .resourceGroupName("markusavstestrg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const importCollector = new azure_native.migrate.ImportCollector("importCollector", {
    importCollectorName: "importCollector2952",
    projectName: "rajoshCCY9671project",
    resourceGroupName: "markusavstestrg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

import_collector = azure_native.migrate.ImportCollector("importCollector",
    import_collector_name="importCollector2952",
    project_name="rajoshCCY9671project",
    resource_group_name="markusavstestrg")

```

```yaml
resources:
  importCollector:
    type: azure-native:migrate:ImportCollector
    properties:
      importCollectorName: importCollector2952
      projectName: rajoshCCY9671project
      resourceGroupName: markusavstestrg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:migrate:ImportCollector importCollector2952 /subscriptions/31be0ff4-c932-4cb3-8efc-efa411d79280/resourceGroups/markusavstestrg/providers/Microsoft.Migrate/assessmentprojects/rajoshCCY9671project/importcollectors/importCollector2952 
```
