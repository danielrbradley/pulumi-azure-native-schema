Policy Contract details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateApiPolicy
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var apiPolicy = new AzureNative.ApiManagement.ApiPolicy("apiPolicy", new()
    {
        ApiId = "5600b57e7e8880006a040001",
        Format = "xml",
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
		_, err := apimanagement.NewApiPolicy(ctx, "apiPolicy", &apimanagement.ApiPolicyArgs{
			ApiId:             pulumi.String("5600b57e7e8880006a040001"),
			Format:            pulumi.String("xml"),
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
import com.pulumi.azurenative.apimanagement.ApiPolicy;
import com.pulumi.azurenative.apimanagement.ApiPolicyArgs;
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
        var apiPolicy = new ApiPolicy("apiPolicy", ApiPolicyArgs.builder()        
            .apiId("5600b57e7e8880006a040001")
            .format("xml")
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

const apiPolicy = new azure_native.apimanagement.ApiPolicy("apiPolicy", {
    apiId: "5600b57e7e8880006a040001",
    format: "xml",
    policyId: "policy",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    value: "<policies> <inbound /> <backend>    <forward-request />  </backend>  <outbound /></policies>",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api_policy = azure_native.apimanagement.ApiPolicy("apiPolicy",
    api_id="5600b57e7e8880006a040001",
    format="xml",
    policy_id="policy",
    resource_group_name="rg1",
    service_name="apimService1",
    value="<policies> <inbound /> <backend>    <forward-request />  </backend>  <outbound /></policies>")

```

```yaml
resources:
  apiPolicy:
    type: azure-native:apimanagement:ApiPolicy
    properties:
      apiId: 5600b57e7e8880006a040001
      format: xml
      policyId: policy
      resourceGroupName: rg1
      serviceName: apimService1
      value: <policies> <inbound /> <backend>    <forward-request />  </backend>  <outbound /></policies>

```

{{% /example %}}
{{% example %}}
### ApiManagementCreateApiPolicyNonXmlEncoded
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var apiPolicy = new AzureNative.ApiManagement.ApiPolicy("apiPolicy", new()
    {
        ApiId = "5600b57e7e8880006a040001",
        Format = "rawxml",
        PolicyId = "policy",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        Value = @"<policies>
     <inbound>
     <base />
  <set-header name=""newvalue"" exists-action=""override"">
   <value>""@(context.Request.Headers.FirstOrDefault(h => h.Ke==""Via""))"" </value>
    </set-header>
  </inbound>
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
		_, err := apimanagement.NewApiPolicy(ctx, "apiPolicy", &apimanagement.ApiPolicyArgs{
			ApiId:             pulumi.String("5600b57e7e8880006a040001"),
			Format:            pulumi.String("rawxml"),
			PolicyId:          pulumi.String("policy"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			Value:             pulumi.String("<policies>\n     <inbound>\n     <base />\n  <set-header name=\"newvalue\" exists-action=\"override\">\n   <value>\"@(context.Request.Headers.FirstOrDefault(h => h.Ke==\"Via\"))\" </value>\n    </set-header>\n  </inbound>\n      </policies>"),
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
import com.pulumi.azurenative.apimanagement.ApiPolicy;
import com.pulumi.azurenative.apimanagement.ApiPolicyArgs;
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
        var apiPolicy = new ApiPolicy("apiPolicy", ApiPolicyArgs.builder()        
            .apiId("5600b57e7e8880006a040001")
            .format("rawxml")
            .policyId("policy")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .value("""
<policies>
     <inbound>
     <base />
  <set-header name="newvalue" exists-action="override">
   <value>"@(context.Request.Headers.FirstOrDefault(h => h.Ke=="Via"))" </value>
    </set-header>
  </inbound>
      </policies>            """)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const apiPolicy = new azure_native.apimanagement.ApiPolicy("apiPolicy", {
    apiId: "5600b57e7e8880006a040001",
    format: "rawxml",
    policyId: "policy",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    value: `<policies>
     <inbound>
     <base />
  <set-header name="newvalue" exists-action="override">
   <value>"@(context.Request.Headers.FirstOrDefault(h => h.Ke=="Via"))" </value>
    </set-header>
  </inbound>
      </policies>`,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api_policy = azure_native.apimanagement.ApiPolicy("apiPolicy",
    api_id="5600b57e7e8880006a040001",
    format="rawxml",
    policy_id="policy",
    resource_group_name="rg1",
    service_name="apimService1",
    value="""<policies>
     <inbound>
     <base />
  <set-header name="newvalue" exists-action="override">
   <value>"@(context.Request.Headers.FirstOrDefault(h => h.Ke=="Via"))" </value>
    </set-header>
  </inbound>
      </policies>""")

```

```yaml
resources:
  apiPolicy:
    type: azure-native:apimanagement:ApiPolicy
    properties:
      apiId: 5600b57e7e8880006a040001
      format: rawxml
      policyId: policy
      resourceGroupName: rg1
      serviceName: apimService1
      value: "<policies>\r\n     <inbound>\r\n     <base />\r\n  <set-header name=\"newvalue\" exists-action=\"override\">\r\n   <value>\"@(context.Request.Headers.FirstOrDefault(h => h.Ke==\"Via\"))\" </value>\r\n    </set-header>\r\n  </inbound>\r\n      </policies>"

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:ApiPolicy policy /subscriptions/4c1a3bc6-89f9-46fe-a175-5d8984b25095/resourcegroups/Api-DF-West-US/providers/Microsoft.ApiManagement/service/samirmsiservice2/apis/echo-api/operations/create-resource/policies/policy 
```
