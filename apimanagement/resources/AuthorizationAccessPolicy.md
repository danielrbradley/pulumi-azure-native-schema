Authorization access policy contract.
API Version: 2022-08-01.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateAuthorizationAccessPolicy
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var authorizationAccessPolicy = new AzureNative.ApiManagement.AuthorizationAccessPolicy("authorizationAccessPolicy", new()
    {
        AuthorizationAccessPolicyId = "fe0bed83-631f-4149-bd0b-0464b1bc7cab",
        AuthorizationId = "authz1",
        AuthorizationProviderId = "aadwithauthcode",
        ObjectId = "fe0bed83-631f-4149-bd0b-0464b1bc7cab",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        TenantId = "13932a0d-5c63-4d37-901d-1df9c97722ff",
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
		_, err := apimanagement.NewAuthorizationAccessPolicy(ctx, "authorizationAccessPolicy", &apimanagement.AuthorizationAccessPolicyArgs{
			AuthorizationAccessPolicyId: pulumi.String("fe0bed83-631f-4149-bd0b-0464b1bc7cab"),
			AuthorizationId:             pulumi.String("authz1"),
			AuthorizationProviderId:     pulumi.String("aadwithauthcode"),
			ObjectId:                    pulumi.String("fe0bed83-631f-4149-bd0b-0464b1bc7cab"),
			ResourceGroupName:           pulumi.String("rg1"),
			ServiceName:                 pulumi.String("apimService1"),
			TenantId:                    pulumi.String("13932a0d-5c63-4d37-901d-1df9c97722ff"),
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
import com.pulumi.azurenative.apimanagement.AuthorizationAccessPolicy;
import com.pulumi.azurenative.apimanagement.AuthorizationAccessPolicyArgs;
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
        var authorizationAccessPolicy = new AuthorizationAccessPolicy("authorizationAccessPolicy", AuthorizationAccessPolicyArgs.builder()        
            .authorizationAccessPolicyId("fe0bed83-631f-4149-bd0b-0464b1bc7cab")
            .authorizationId("authz1")
            .authorizationProviderId("aadwithauthcode")
            .objectId("fe0bed83-631f-4149-bd0b-0464b1bc7cab")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .tenantId("13932a0d-5c63-4d37-901d-1df9c97722ff")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const authorizationAccessPolicy = new azure_native.apimanagement.AuthorizationAccessPolicy("authorizationAccessPolicy", {
    authorizationAccessPolicyId: "fe0bed83-631f-4149-bd0b-0464b1bc7cab",
    authorizationId: "authz1",
    authorizationProviderId: "aadwithauthcode",
    objectId: "fe0bed83-631f-4149-bd0b-0464b1bc7cab",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    tenantId: "13932a0d-5c63-4d37-901d-1df9c97722ff",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

authorization_access_policy = azure_native.apimanagement.AuthorizationAccessPolicy("authorizationAccessPolicy",
    authorization_access_policy_id="fe0bed83-631f-4149-bd0b-0464b1bc7cab",
    authorization_id="authz1",
    authorization_provider_id="aadwithauthcode",
    object_id="fe0bed83-631f-4149-bd0b-0464b1bc7cab",
    resource_group_name="rg1",
    service_name="apimService1",
    tenant_id="13932a0d-5c63-4d37-901d-1df9c97722ff")

```

```yaml
resources:
  authorizationAccessPolicy:
    type: azure-native:apimanagement:AuthorizationAccessPolicy
    properties:
      authorizationAccessPolicyId: fe0bed83-631f-4149-bd0b-0464b1bc7cab
      authorizationId: authz1
      authorizationProviderId: aadwithauthcode
      objectId: fe0bed83-631f-4149-bd0b-0464b1bc7cab
      resourceGroupName: rg1
      serviceName: apimService1
      tenantId: 13932a0d-5c63-4d37-901d-1df9c97722ff

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:AuthorizationAccessPolicy fe0bed83-631f-4149-bd0b-0464b1bc7cab /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/authorizationProviders/aadwithauthcode/authorizations/authz1/accessPolicies 
```
