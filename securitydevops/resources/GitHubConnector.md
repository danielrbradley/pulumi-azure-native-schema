Represents an ARM resource for /subscriptions/xxx/resourceGroups/xxx/providers/Microsoft.SecurityDevOps/gitHubConnectors.
API Version: 2022-09-01-preview.
Previous API Version: 2022-09-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### GitHubConnector_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var gitHubConnector = new AzureNative.SecurityDevOps.GitHubConnector("gitHubConnector", new()
    {
        GitHubConnectorName = "testconnector",
        Location = "West US",
        Properties = new AzureNative.SecurityDevOps.Inputs.GitHubConnectorPropertiesArgs
        {
            Code = "00000000000000000000",
        },
        ResourceGroupName = "westusrg",
    });

});


```

```go
package main

import (
	securitydevops "github.com/pulumi/pulumi-azure-native-sdk/securitydevops"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := securitydevops.NewGitHubConnector(ctx, "gitHubConnector", &securitydevops.GitHubConnectorArgs{
			GitHubConnectorName: pulumi.String("testconnector"),
			Location:            pulumi.String("West US"),
			Properties: &securitydevops.GitHubConnectorPropertiesArgs{
				Code: pulumi.String("00000000000000000000"),
			},
			ResourceGroupName: pulumi.String("westusrg"),
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
import com.pulumi.azurenative.securitydevops.GitHubConnector;
import com.pulumi.azurenative.securitydevops.GitHubConnectorArgs;
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
        var gitHubConnector = new GitHubConnector("gitHubConnector", GitHubConnectorArgs.builder()        
            .gitHubConnectorName("testconnector")
            .location("West US")
            .properties(Map.of("code", "00000000000000000000"))
            .resourceGroupName("westusrg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const gitHubConnector = new azure_native.securitydevops.GitHubConnector("gitHubConnector", {
    gitHubConnectorName: "testconnector",
    location: "West US",
    properties: {
        code: "00000000000000000000",
    },
    resourceGroupName: "westusrg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

git_hub_connector = azure_native.securitydevops.GitHubConnector("gitHubConnector",
    git_hub_connector_name="testconnector",
    location="West US",
    properties=azure_native.securitydevops.GitHubConnectorPropertiesArgs(
        code="00000000000000000000",
    ),
    resource_group_name="westusrg")

```

```yaml
resources:
  gitHubConnector:
    type: azure-native:securitydevops:GitHubConnector
    properties:
      gitHubConnectorName: testconnector
      location: West US
      properties:
        code: '00000000000000000000'
      resourceGroupName: westusrg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:securitydevops:GitHubConnector testconnector /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/westusrg/providers/Microsoft.SecurityDevOps/gitHubConnectors/testconnector 
```
