Policy Contract details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateApiOperationPolicy
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var apiOperationPolicy = new AzureNative.ApiManagement.ApiOperationPolicy("apiOperationPolicy", new()
    {
        ApiId = "5600b57e7e8880006a040001",
        Format = "xml",
        OperationId = "5600b57e7e8880006a080001",
        PolicyId = "policy",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        Value = "<policies> <inbound /> <backend>    <forward-request />  </backend>  <outbound /></policies>",
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
		_, err := apimanagement.NewApiOperationPolicy(ctx, "apiOperationPolicy", &apimanagement.ApiOperationPolicyArgs{
			ApiId:             pulumi.String("5600b57e7e8880006a040001"),
			Format:            pulumi.String("xml"),
			OperationId:       pulumi.String("5600b57e7e8880006a080001"),
			PolicyId:          pulumi.String("policy"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			Value:             pulumi.String("<policies> <inbound /> <backend>    <forward-request />  </backend>  <outbound /></policies>"),
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
import com.pulumi.azurenative.apimanagement.ApiOperationPolicy;
import com.pulumi.azurenative.apimanagement.ApiOperationPolicyArgs;
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
        var apiOperationPolicy = new ApiOperationPolicy("apiOperationPolicy", ApiOperationPolicyArgs.builder()        
            .apiId("5600b57e7e8880006a040001")
            .format("xml")
            .operationId("5600b57e7e8880006a080001")
            .policyId("policy")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .value("<policies> <inbound /> <backend>    <forward-request />  </backend>  <outbound /></policies>")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const apiOperationPolicy = new azure_native.apimanagement.ApiOperationPolicy("apiOperationPolicy", {
    apiId: "5600b57e7e8880006a040001",
    format: "xml",
    operationId: "5600b57e7e8880006a080001",
    policyId: "policy",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    value: "<policies> <inbound /> <backend>    <forward-request />  </backend>  <outbound /></policies>",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api_operation_policy = azure_native.apimanagement.ApiOperationPolicy("apiOperationPolicy",
    api_id="5600b57e7e8880006a040001",
    format="xml",
    operation_id="5600b57e7e8880006a080001",
    policy_id="policy",
    resource_group_name="rg1",
    service_name="apimService1",
    value="<policies> <inbound /> <backend>    <forward-request />  </backend>  <outbound /></policies>")

```

```yaml
resources:
  apiOperationPolicy:
    type: azure-native:apimanagement:ApiOperationPolicy
    properties:
      apiId: 5600b57e7e8880006a040001
      format: xml
      operationId: 5600b57e7e8880006a080001
      policyId: policy
      resourceGroupName: rg1
      serviceName: apimService1
      value: <policies> <inbound /> <backend>    <forward-request />  </backend>  <outbound /></policies>

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:ApiOperationPolicy policy /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apis/5600b57e7e8880006a040001/operations/5600b57e7e8880006a080001/policies/policy 
```
