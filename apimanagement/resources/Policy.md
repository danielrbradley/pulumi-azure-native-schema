Policy Contract details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreatePolicy
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var policy = new AzureNative.ApiManagement.Policy("policy", new()
    {
        Format = "xml",
        PolicyId = "policy",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        Value = @"<policies>
  <inbound />
  <backend>
    <forward-request />
  </backend>
  <outbound />
</policies>",
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
		_, err := apimanagement.NewPolicy(ctx, "policy", &apimanagement.PolicyArgs{
			Format:            pulumi.String("xml"),
			PolicyId:          pulumi.String("policy"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			Value:             pulumi.String("<policies>\n  <inbound />\n  <backend>\n    <forward-request />\n  </backend>\n  <outbound />\n</policies>"),
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
import com.pulumi.azurenative.apimanagement.Policy;
import com.pulumi.azurenative.apimanagement.PolicyArgs;
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
        var policy = new Policy("policy", PolicyArgs.builder()        
            .format("xml")
            .policyId("policy")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .value("""
<policies>
  <inbound />
  <backend>
    <forward-request />
  </backend>
  <outbound />
</policies>            """)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const policy = new azure_native.apimanagement.Policy("policy", {
    format: "xml",
    policyId: "policy",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    value: `<policies>
  <inbound />
  <backend>
    <forward-request />
  </backend>
  <outbound />
</policies>`,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

policy = azure_native.apimanagement.Policy("policy",
    format="xml",
    policy_id="policy",
    resource_group_name="rg1",
    service_name="apimService1",
    value="""<policies>
  <inbound />
  <backend>
    <forward-request />
  </backend>
  <outbound />
</policies>""")

```

```yaml
resources:
  policy:
    type: azure-native:apimanagement:Policy
    properties:
      format: xml
      policyId: policy
      resourceGroupName: rg1
      serviceName: apimService1
      value: "<policies>\r\n  <inbound />\r\n  <backend>\r\n    <forward-request />\r\n  </backend>\r\n  <outbound />\r\n</policies>"

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:Policy policy /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/policies/policy 
```
