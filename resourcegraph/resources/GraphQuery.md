Graph Query entity definition.
API Version: 2020-04-01-preview.
Previous API Version: 2018-09-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Graph Query
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var graphQuery = new AzureNative.ResourceGraph.GraphQuery("graphQuery", new()
    {
        Description = "Docker VMs in PROD",
        Query = "where isnotnull(tags['Prod']) and properties.extensions[0].Name == 'docker'",
        ResourceGroupName = "my-resource-group",
        ResourceName = "MyDockerVMs",
        Tags = null,
    });

});


```

```go
package main

import (
	resourcegraph "github.com/pulumi/pulumi-azure-native-sdk/resourcegraph"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := resourcegraph.NewGraphQuery(ctx, "graphQuery", &resourcegraph.GraphQueryArgs{
			Description:       pulumi.String("Docker VMs in PROD"),
			Query:             pulumi.String("where isnotnull(tags['Prod']) and properties.extensions[0].Name == 'docker'"),
			ResourceGroupName: pulumi.String("my-resource-group"),
			ResourceName:      pulumi.String("MyDockerVMs"),
			Tags:              nil,
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
import com.pulumi.azurenative.resourcegraph.GraphQuery;
import com.pulumi.azurenative.resourcegraph.GraphQueryArgs;
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
        var graphQuery = new GraphQuery("graphQuery", GraphQueryArgs.builder()        
            .description("Docker VMs in PROD")
            .query("where isnotnull(tags['Prod']) and properties.extensions[0].Name == 'docker'")
            .resourceGroupName("my-resource-group")
            .resourceName("MyDockerVMs")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const graphQuery = new azure_native.resourcegraph.GraphQuery("graphQuery", {
    description: "Docker VMs in PROD",
    query: "where isnotnull(tags['Prod']) and properties.extensions[0].Name == 'docker'",
    resourceGroupName: "my-resource-group",
    resourceName: "MyDockerVMs",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

graph_query = azure_native.resourcegraph.GraphQuery("graphQuery",
    description="Docker VMs in PROD",
    query="where isnotnull(tags['Prod']) and properties.extensions[0].Name == 'docker'",
    resource_group_name="my-resource-group",
    resource_name_="MyDockerVMs",
    tags={})

```

```yaml
resources:
  graphQuery:
    type: azure-native:resourcegraph:GraphQuery
    properties:
      description: Docker VMs in PROD
      query: where isnotnull(tags['Prod']) and properties.extensions[0].Name == 'docker'
      resourceGroupName: my-resource-group
      resourceName: MyDockerVMs
      tags: {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:resourcegraph:GraphQuery MyDockerVMs  /subscriptions/024e2271-06fa-46b6-9079-f1ed3c7b070e/resources/my-resource-group/providers/Microsoft.ResourceGraph/queries/MyDockerVMs 
```
