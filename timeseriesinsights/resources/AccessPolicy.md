An access policy is used to grant users and applications access to the environment. Roles are assigned to service principals in Azure Active Directory. These roles define the actions the principal can perform through the Time Series Insights data plane APIs.
API Version: 2020-05-15.
Previous API Version: 2020-05-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### AccessPoliciesCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var accessPolicy = new AzureNative.TimeSeriesInsights.AccessPolicy("accessPolicy", new()
    {
        AccessPolicyName = "ap1",
        Description = "some description",
        EnvironmentName = "env1",
        PrincipalObjectId = "aGuid",
        ResourceGroupName = "rg1",
        Roles = new[]
        {
            "Reader",
        },
    });

});


```

```go
package main

import (
	timeseriesinsights "github.com/pulumi/pulumi-azure-native-sdk/timeseriesinsights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := timeseriesinsights.NewAccessPolicy(ctx, "accessPolicy", &timeseriesinsights.AccessPolicyArgs{
			AccessPolicyName:  pulumi.String("ap1"),
			Description:       pulumi.String("some description"),
			EnvironmentName:   pulumi.String("env1"),
			PrincipalObjectId: pulumi.String("aGuid"),
			ResourceGroupName: pulumi.String("rg1"),
			Roles: pulumi.StringArray{
				pulumi.String("Reader"),
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
import com.pulumi.azurenative.timeseriesinsights.AccessPolicy;
import com.pulumi.azurenative.timeseriesinsights.AccessPolicyArgs;
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
        var accessPolicy = new AccessPolicy("accessPolicy", AccessPolicyArgs.builder()        
            .accessPolicyName("ap1")
            .description("some description")
            .environmentName("env1")
            .principalObjectId("aGuid")
            .resourceGroupName("rg1")
            .roles("Reader")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const accessPolicy = new azure_native.timeseriesinsights.AccessPolicy("accessPolicy", {
    accessPolicyName: "ap1",
    description: "some description",
    environmentName: "env1",
    principalObjectId: "aGuid",
    resourceGroupName: "rg1",
    roles: ["Reader"],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

access_policy = azure_native.timeseriesinsights.AccessPolicy("accessPolicy",
    access_policy_name="ap1",
    description="some description",
    environment_name="env1",
    principal_object_id="aGuid",
    resource_group_name="rg1",
    roles=["Reader"])

```

```yaml
resources:
  accessPolicy:
    type: azure-native:timeseriesinsights:AccessPolicy
    properties:
      accessPolicyName: ap1
      description: some description
      environmentName: env1
      principalObjectId: aGuid
      resourceGroupName: rg1
      roles:
        - Reader

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:timeseriesinsights:AccessPolicy ap1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.TimeSeriesInsights/Environments/env1/accessPolicies/ap1 
```
