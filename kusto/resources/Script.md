Class representing a database script.
API Version: 2022-12-29.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### KustoScriptsCreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var script = new AzureNative.Kusto.Script("script", new()
    {
        ClusterName = "kustoCluster",
        ContinueOnErrors = true,
        DatabaseName = "KustoDatabase8",
        ForceUpdateTag = "2bcf3c21-ffd1-4444-b9dd-e52e00ee53fe",
        ResourceGroupName = "kustorptest",
        ScriptName = "kustoScript",
        ScriptUrl = "https://mysa.blob.core.windows.net/container/script.txt",
        ScriptUrlSasToken = "?sv=2019-02-02&st=2019-04-29T22%3A18%3A26Z&se=2019-04-30T02%3A23%3A26Z&sr=b&sp=rw&sip=168.1.5.60-168.1.5.70&spr=https&sig=********************************",
    });

});


```

```go
package main

import (
	kusto "github.com/pulumi/pulumi-azure-native-sdk/kusto"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := kusto.NewScript(ctx, "script", &kusto.ScriptArgs{
			ClusterName:       pulumi.String("kustoCluster"),
			ContinueOnErrors:  pulumi.Bool(true),
			DatabaseName:      pulumi.String("KustoDatabase8"),
			ForceUpdateTag:    pulumi.String("2bcf3c21-ffd1-4444-b9dd-e52e00ee53fe"),
			ResourceGroupName: pulumi.String("kustorptest"),
			ScriptName:        pulumi.String("kustoScript"),
			ScriptUrl:         pulumi.String("https://mysa.blob.core.windows.net/container/script.txt"),
			ScriptUrlSasToken: pulumi.String("?sv=2019-02-02&st=2019-04-29T22%3A18%3A26Z&se=2019-04-30T02%3A23%3A26Z&sr=b&sp=rw&sip=168.1.5.60-168.1.5.70&spr=https&sig=********************************"),
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
import com.pulumi.azurenative.kusto.Script;
import com.pulumi.azurenative.kusto.ScriptArgs;
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
        var script = new Script("script", ScriptArgs.builder()        
            .clusterName("kustoCluster")
            .continueOnErrors(true)
            .databaseName("KustoDatabase8")
            .forceUpdateTag("2bcf3c21-ffd1-4444-b9dd-e52e00ee53fe")
            .resourceGroupName("kustorptest")
            .scriptName("kustoScript")
            .scriptUrl("https://mysa.blob.core.windows.net/container/script.txt")
            .scriptUrlSasToken("?sv=2019-02-02&st=2019-04-29T22%3A18%3A26Z&se=2019-04-30T02%3A23%3A26Z&sr=b&sp=rw&sip=168.1.5.60-168.1.5.70&spr=https&sig=********************************")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const script = new azure_native.kusto.Script("script", {
    clusterName: "kustoCluster",
    continueOnErrors: true,
    databaseName: "KustoDatabase8",
    forceUpdateTag: "2bcf3c21-ffd1-4444-b9dd-e52e00ee53fe",
    resourceGroupName: "kustorptest",
    scriptName: "kustoScript",
    scriptUrl: "https://mysa.blob.core.windows.net/container/script.txt",
    scriptUrlSasToken: "?sv=2019-02-02&st=2019-04-29T22%3A18%3A26Z&se=2019-04-30T02%3A23%3A26Z&sr=b&sp=rw&sip=168.1.5.60-168.1.5.70&spr=https&sig=********************************",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

script = azure_native.kusto.Script("script",
    cluster_name="kustoCluster",
    continue_on_errors=True,
    database_name="KustoDatabase8",
    force_update_tag="2bcf3c21-ffd1-4444-b9dd-e52e00ee53fe",
    resource_group_name="kustorptest",
    script_name="kustoScript",
    script_url="https://mysa.blob.core.windows.net/container/script.txt",
    script_url_sas_token="?sv=2019-02-02&st=2019-04-29T22%3A18%3A26Z&se=2019-04-30T02%3A23%3A26Z&sr=b&sp=rw&sip=168.1.5.60-168.1.5.70&spr=https&sig=********************************")

```

```yaml
resources:
  script:
    type: azure-native:kusto:Script
    properties:
      clusterName: kustoCluster
      continueOnErrors: true
      databaseName: KustoDatabase8
      forceUpdateTag: 2bcf3c21-ffd1-4444-b9dd-e52e00ee53fe
      resourceGroupName: kustorptest
      scriptName: kustoScript
      scriptUrl: https://mysa.blob.core.windows.net/container/script.txt
      scriptUrlSasToken: ?sv=2019-02-02&st=2019-04-29T22%3A18%3A26Z&se=2019-04-30T02%3A23%3A26Z&sr=b&sp=rw&sip=168.1.5.60-168.1.5.70&spr=https&sig=********************************

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:kusto:Script kustoCluster/KustoDatabase8/kustoScript /subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Kusto/Clusters/kustoCluster/Databases/KustoDatabase8/Scripts/kustoScript 
```
