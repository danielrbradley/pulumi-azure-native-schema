GraphQL API Resolver details.
API Version: 2022-08-01.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateGraphQLApiResolver
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var graphQLApiResolver = new AzureNative.ApiManagement.GraphQLApiResolver("graphQLApiResolver", new()
    {
        ApiId = "someAPI",
        Description = "A GraphQL Resolver example",
        DisplayName = "Query Users",
        Path = "Query/users",
        ResolverId = "newResolver",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
    });

});


```

```go
package main

import (
	apimanagement "github.com/pulumi/pulumi-azure-native-sdk/apimanagement"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := apimanagement.NewGraphQLApiResolver(ctx, "graphQLApiResolver", &apimanagement.GraphQLApiResolverArgs{
			ApiId:             pulumi.String("someAPI"),
			Description:       pulumi.String("A GraphQL Resolver example"),
			DisplayName:       pulumi.String("Query Users"),
			Path:              pulumi.String("Query/users"),
			ResolverId:        pulumi.String("newResolver"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
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
import com.pulumi.azurenative.apimanagement.GraphQLApiResolver;
import com.pulumi.azurenative.apimanagement.GraphQLApiResolverArgs;
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
        var graphQLApiResolver = new GraphQLApiResolver("graphQLApiResolver", GraphQLApiResolverArgs.builder()        
            .apiId("someAPI")
            .description("A GraphQL Resolver example")
            .displayName("Query Users")
            .path("Query/users")
            .resolverId("newResolver")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const graphQLApiResolver = new azure_native.apimanagement.GraphQLApiResolver("graphQLApiResolver", {
    apiId: "someAPI",
    description: "A GraphQL Resolver example",
    displayName: "Query Users",
    path: "Query/users",
    resolverId: "newResolver",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

graph_ql_api_resolver = azure_native.apimanagement.GraphQLApiResolver("graphQLApiResolver",
    api_id="someAPI",
    description="A GraphQL Resolver example",
    display_name="Query Users",
    path="Query/users",
    resolver_id="newResolver",
    resource_group_name="rg1",
    service_name="apimService1")

```

```yaml
resources:
  graphQLApiResolver:
    type: azure-native:apimanagement:GraphQLApiResolver
    properties:
      apiId: someAPI
      description: A GraphQL Resolver example
      displayName: Query Users
      path: Query/users
      resolverId: newResolver
      resourceGroupName: rg1
      serviceName: apimService1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:GraphQLApiResolver newResolver /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apis/someAPI/resolvers/newResolver 
```
