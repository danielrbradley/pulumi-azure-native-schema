A notebook workspace resource
API Version: 2022-11-15.
Previous API Version: 2021-03-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CosmosDBNotebookWorkspaceCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var notebookWorkspace = new AzureNative.DocumentDB.NotebookWorkspace("notebookWorkspace", new()
    {
        AccountName = "ddb1",
        NotebookWorkspaceName = "default",
        ResourceGroupName = "rg1",
    });

});


```

```go
package main

import (
	documentdb "github.com/pulumi/pulumi-azure-native-sdk/documentdb"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := documentdb.NewNotebookWorkspace(ctx, "notebookWorkspace", &documentdb.NotebookWorkspaceArgs{
			AccountName:           pulumi.String("ddb1"),
			NotebookWorkspaceName: pulumi.String("default"),
			ResourceGroupName:     pulumi.String("rg1"),
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
import com.pulumi.azurenative.documentdb.NotebookWorkspace;
import com.pulumi.azurenative.documentdb.NotebookWorkspaceArgs;
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
        var notebookWorkspace = new NotebookWorkspace("notebookWorkspace", NotebookWorkspaceArgs.builder()        
            .accountName("ddb1")
            .notebookWorkspaceName("default")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const notebookWorkspace = new azure_native.documentdb.NotebookWorkspace("notebookWorkspace", {
    accountName: "ddb1",
    notebookWorkspaceName: "default",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

notebook_workspace = azure_native.documentdb.NotebookWorkspace("notebookWorkspace",
    account_name="ddb1",
    notebook_workspace_name="default",
    resource_group_name="rg1")

```

```yaml
resources:
  notebookWorkspace:
    type: azure-native:documentdb:NotebookWorkspace
    properties:
      accountName: ddb1
      notebookWorkspaceName: default
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:documentdb:NotebookWorkspace default /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.DocumentDB/databaseAccounts/ddb1/notebookWorkspaces/default 
```
