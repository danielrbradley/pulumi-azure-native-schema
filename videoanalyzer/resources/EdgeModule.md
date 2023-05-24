The representation of an edge module.
API Version: 2021-11-01-preview.
Previous API Version: 2021-05-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Registers an edge module.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var edgeModule = new AzureNative.VideoAnalyzer.EdgeModule("edgeModule", new()
    {
        AccountName = "testaccount2",
        EdgeModuleName = "edgeModule1",
        ResourceGroupName = "testrg",
    });

});


```

```go
package main

import (
	videoanalyzer "github.com/pulumi/pulumi-azure-native-sdk/videoanalyzer"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := videoanalyzer.NewEdgeModule(ctx, "edgeModule", &videoanalyzer.EdgeModuleArgs{
			AccountName:       pulumi.String("testaccount2"),
			EdgeModuleName:    pulumi.String("edgeModule1"),
			ResourceGroupName: pulumi.String("testrg"),
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
import com.pulumi.azurenative.videoanalyzer.EdgeModule;
import com.pulumi.azurenative.videoanalyzer.EdgeModuleArgs;
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
        var edgeModule = new EdgeModule("edgeModule", EdgeModuleArgs.builder()        
            .accountName("testaccount2")
            .edgeModuleName("edgeModule1")
            .resourceGroupName("testrg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const edgeModule = new azure_native.videoanalyzer.EdgeModule("edgeModule", {
    accountName: "testaccount2",
    edgeModuleName: "edgeModule1",
    resourceGroupName: "testrg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

edge_module = azure_native.videoanalyzer.EdgeModule("edgeModule",
    account_name="testaccount2",
    edge_module_name="edgeModule1",
    resource_group_name="testrg")

```

```yaml
resources:
  edgeModule:
    type: azure-native:videoanalyzer:EdgeModule
    properties:
      accountName: testaccount2
      edgeModuleName: edgeModule1
      resourceGroupName: testrg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:videoanalyzer:EdgeModule edgeModule1 /subscriptions/591e76c3-3e97-44db-879c-3e2b12961b62/resourceGroups/testrg/providers/Microsoft.Media/videoAnalyzers/testaccount2/edgeModules/edgeModule1 
```
