Policy Contract details.
API Version: 2022-08-01.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateGraphQLApiResolverPolicy
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var graphQLApiResolverPolicy = new AzureNative.ApiManagement.GraphQLApiResolverPolicy("graphQLApiResolverPolicy", new()
    {
        ApiId = "5600b57e7e8880006a040001",
        Format = "xml",
        PolicyId = "policy",
        ResolverId = "5600b57e7e8880006a080001",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        Value = "<http-data-source><http-request><set-method>GET</set-method><set-backend-service base-url=\"https://some.service.com\" /><set-url>/api/users</set-url></http-request></http-data-source>",
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
		_, err := apimanagement.NewGraphQLApiResolverPolicy(ctx, "graphQLApiResolverPolicy", &apimanagement.GraphQLApiResolverPolicyArgs{
			ApiId:             pulumi.String("5600b57e7e8880006a040001"),
			Format:            pulumi.String("xml"),
			PolicyId:          pulumi.String("policy"),
			ResolverId:        pulumi.String("5600b57e7e8880006a080001"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			Value:             pulumi.String("<http-data-source><http-request><set-method>GET</set-method><set-backend-service base-url=\"https://some.service.com\" /><set-url>/api/users</set-url></http-request></http-data-source>"),
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
import com.pulumi.azurenative.apimanagement.GraphQLApiResolverPolicy;
import com.pulumi.azurenative.apimanagement.GraphQLApiResolverPolicyArgs;
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
        var graphQLApiResolverPolicy = new GraphQLApiResolverPolicy("graphQLApiResolverPolicy", GraphQLApiResolverPolicyArgs.builder()        
            .apiId("5600b57e7e8880006a040001")
            .format("xml")
            .policyId("policy")
            .resolverId("5600b57e7e8880006a080001")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .value("<http-data-source><http-request><set-method>GET</set-method><set-backend-service base-url=\"https://some.service.com\" /><set-url>/api/users</set-url></http-request></http-data-source>")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const graphQLApiResolverPolicy = new azure_native.apimanagement.GraphQLApiResolverPolicy("graphQLApiResolverPolicy", {
    apiId: "5600b57e7e8880006a040001",
    format: "xml",
    policyId: "policy",
    resolverId: "5600b57e7e8880006a080001",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    value: "<http-data-source><http-request><set-method>GET</set-method><set-backend-service base-url=\"https://some.service.com\" /><set-url>/api/users</set-url></http-request></http-data-source>",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

graph_ql_api_resolver_policy = azure_native.apimanagement.GraphQLApiResolverPolicy("graphQLApiResolverPolicy",
    api_id="5600b57e7e8880006a040001",
    format="xml",
    policy_id="policy",
    resolver_id="5600b57e7e8880006a080001",
    resource_group_name="rg1",
    service_name="apimService1",
    value="<http-data-source><http-request><set-method>GET</set-method><set-backend-service base-url=\"https://some.service.com\" /><set-url>/api/users</set-url></http-request></http-data-source>")

```

```yaml
resources:
  graphQLApiResolverPolicy:
    type: azure-native:apimanagement:GraphQLApiResolverPolicy
    properties:
      apiId: 5600b57e7e8880006a040001
      format: xml
      policyId: policy
      resolverId: 5600b57e7e8880006a080001
      resourceGroupName: rg1
      serviceName: apimService1
      value: <http-data-source><http-request><set-method>GET</set-method><set-backend-service base-url="https://some.service.com" /><set-url>/api/users</set-url></http-request></http-data-source>

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:GraphQLApiResolverPolicy policy /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apis/5600b57e7e8880006a040001/resolvers/5600b57e7e8880006a080001/policies/policy 
```
