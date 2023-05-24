Policy fragment contract details.
API Version: 2022-08-01.
Previous API Version: 2021-12-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

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
    var policyFragment = new AzureNative.ApiManagement.PolicyFragment("policyFragment", new()
    {
        Description = "A policy fragment example",
        Format = "xml",
        Id = "policyFragment1",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        Value = "<fragment><json-to-xml apply=\"always\" consider-accept-header=\"false\" /></fragment>",
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
		_, err := apimanagement.NewPolicyFragment(ctx, "policyFragment", &apimanagement.PolicyFragmentArgs{
			Description:       pulumi.String("A policy fragment example"),
			Format:            pulumi.String("xml"),
			Id:                pulumi.String("policyFragment1"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			Value:             pulumi.String("<fragment><json-to-xml apply=\"always\" consider-accept-header=\"false\" /></fragment>"),
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
import com.pulumi.azurenative.apimanagement.PolicyFragment;
import com.pulumi.azurenative.apimanagement.PolicyFragmentArgs;
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
        var policyFragment = new PolicyFragment("policyFragment", PolicyFragmentArgs.builder()        
            .description("A policy fragment example")
            .format("xml")
            .id("policyFragment1")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .value("<fragment><json-to-xml apply=\"always\" consider-accept-header=\"false\" /></fragment>")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const policyFragment = new azure_native.apimanagement.PolicyFragment("policyFragment", {
    description: "A policy fragment example",
    format: "xml",
    id: "policyFragment1",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    value: "<fragment><json-to-xml apply=\"always\" consider-accept-header=\"false\" /></fragment>",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

policy_fragment = azure_native.apimanagement.PolicyFragment("policyFragment",
    description="A policy fragment example",
    format="xml",
    id="policyFragment1",
    resource_group_name="rg1",
    service_name="apimService1",
    value="<fragment><json-to-xml apply=\"always\" consider-accept-header=\"false\" /></fragment>")

```

```yaml
resources:
  policyFragment:
    type: azure-native:apimanagement:PolicyFragment
    properties:
      description: A policy fragment example
      format: xml
      id: policyFragment1
      resourceGroupName: rg1
      serviceName: apimService1
      value: <fragment><json-to-xml apply="always" consider-accept-header="false" /></fragment>

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:PolicyFragment policyFragment1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/policyFragments/policyFragment1 
```
