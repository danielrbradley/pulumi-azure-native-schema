EnterpriseKnowledgeGraph resource definition
API Version: 2018-12-03.
Previous API Version: 2018-12-03. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create EnterpriseKnowledgeGraph
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var enterpriseKnowledgeGraph = new AzureNative.EnterpriseKnowledgeGraph.EnterpriseKnowledgeGraph("enterpriseKnowledgeGraph", new()
    {
        Location = "West US",
        Properties = null,
        ResourceGroupName = "OneResourceGroupName",
        ResourceName = "sampleekgname",
        Tags = 
        {
            { "tag1", "value1" },
            { "tag2", "value2" },
        },
    });

});


```

```go
package main

import (
	enterpriseknowledgegraph "github.com/pulumi/pulumi-azure-native-sdk/enterpriseknowledgegraph"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := enterpriseknowledgegraph.NewEnterpriseKnowledgeGraph(ctx, "enterpriseKnowledgeGraph", &enterpriseknowledgegraph.EnterpriseKnowledgeGraphArgs{
			Location:          pulumi.String("West US"),
			Properties:        nil,
			ResourceGroupName: pulumi.String("OneResourceGroupName"),
			ResourceName:      pulumi.String("sampleekgname"),
			Tags: pulumi.StringMap{
				"tag1": pulumi.String("value1"),
				"tag2": pulumi.String("value2"),
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
import com.pulumi.azurenative.enterpriseknowledgegraph.EnterpriseKnowledgeGraph;
import com.pulumi.azurenative.enterpriseknowledgegraph.EnterpriseKnowledgeGraphArgs;
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
        var enterpriseKnowledgeGraph = new EnterpriseKnowledgeGraph("enterpriseKnowledgeGraph", EnterpriseKnowledgeGraphArgs.builder()        
            .location("West US")
            .properties()
            .resourceGroupName("OneResourceGroupName")
            .resourceName("sampleekgname")
            .tags(Map.ofEntries(
                Map.entry("tag1", "value1"),
                Map.entry("tag2", "value2")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const enterpriseKnowledgeGraph = new azure_native.enterpriseknowledgegraph.EnterpriseKnowledgeGraph("enterpriseKnowledgeGraph", {
    location: "West US",
    properties: {},
    resourceGroupName: "OneResourceGroupName",
    resourceName: "sampleekgname",
    tags: {
        tag1: "value1",
        tag2: "value2",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

enterprise_knowledge_graph = azure_native.enterpriseknowledgegraph.EnterpriseKnowledgeGraph("enterpriseKnowledgeGraph",
    location="West US",
    properties=azure_native.enterpriseknowledgegraph.EnterpriseKnowledgeGraphPropertiesArgs(),
    resource_group_name="OneResourceGroupName",
    resource_name_="sampleekgname",
    tags={
        "tag1": "value1",
        "tag2": "value2",
    })

```

```yaml
resources:
  enterpriseKnowledgeGraph:
    type: azure-native:enterpriseknowledgegraph:EnterpriseKnowledgeGraph
    properties:
      location: West US
      properties: {}
      resourceGroupName: OneResourceGroupName
      resourceName: sampleekgname
      tags:
        tag1: value1
        tag2: value2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:enterpriseknowledgegraph:EnterpriseKnowledgeGraph samplename someid 
```
