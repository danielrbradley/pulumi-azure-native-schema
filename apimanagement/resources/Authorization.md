Authorization contract.
API Version: 2022-08-01.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateAuthorizationAADAuthCode
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var authorization = new AzureNative.ApiManagement.Authorization("authorization", new()
    {
        AuthorizationId = "authz2",
        AuthorizationProviderId = "aadwithauthcode",
        AuthorizationType = "OAuth2",
        OAuth2GrantType = "AuthorizationCode",
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
		_, err := apimanagement.NewAuthorization(ctx, "authorization", &apimanagement.AuthorizationArgs{
			AuthorizationId:         pulumi.String("authz2"),
			AuthorizationProviderId: pulumi.String("aadwithauthcode"),
			AuthorizationType:       pulumi.String("OAuth2"),
			OAuth2GrantType:         pulumi.String("AuthorizationCode"),
			ResourceGroupName:       pulumi.String("rg1"),
			ServiceName:             pulumi.String("apimService1"),
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
import com.pulumi.azurenative.apimanagement.Authorization;
import com.pulumi.azurenative.apimanagement.AuthorizationArgs;
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
        var authorization = new Authorization("authorization", AuthorizationArgs.builder()        
            .authorizationId("authz2")
            .authorizationProviderId("aadwithauthcode")
            .authorizationType("OAuth2")
            .oAuth2GrantType("AuthorizationCode")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const authorization = new azure_native.apimanagement.Authorization("authorization", {
    authorizationId: "authz2",
    authorizationProviderId: "aadwithauthcode",
    authorizationType: "OAuth2",
    oAuth2GrantType: "AuthorizationCode",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

authorization = azure_native.apimanagement.Authorization("authorization",
    authorization_id="authz2",
    authorization_provider_id="aadwithauthcode",
    authorization_type="OAuth2",
    o_auth2_grant_type="AuthorizationCode",
    resource_group_name="rg1",
    service_name="apimService1")

```

```yaml
resources:
  authorization:
    type: azure-native:apimanagement:Authorization
    properties:
      authorizationId: authz2
      authorizationProviderId: aadwithauthcode
      authorizationType: OAuth2
      oAuth2GrantType: AuthorizationCode
      resourceGroupName: rg1
      serviceName: apimService1

```

{{% /example %}}
{{% example %}}
### ApiManagementCreateAuthorizationAADClientCred
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var authorization = new AzureNative.ApiManagement.Authorization("authorization", new()
    {
        AuthorizationId = "authz1",
        AuthorizationProviderId = "aadwithclientcred",
        AuthorizationType = "OAuth2",
        OAuth2GrantType = "AuthorizationCode",
        Parameters = 
        {
            { "clientId", "53790925-fdd3-4b80-bc7a-4c3aaf25801d" },
            { "clientSecret", "FcJkQ3iPSaKAQRA7Ft8Q~fZ1X5vKmqzUAfJagcJ8" },
        },
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
		_, err := apimanagement.NewAuthorization(ctx, "authorization", &apimanagement.AuthorizationArgs{
			AuthorizationId:         pulumi.String("authz1"),
			AuthorizationProviderId: pulumi.String("aadwithclientcred"),
			AuthorizationType:       pulumi.String("OAuth2"),
			OAuth2GrantType:         pulumi.String("AuthorizationCode"),
			Parameters: pulumi.StringMap{
				"clientId":     pulumi.String("53790925-fdd3-4b80-bc7a-4c3aaf25801d"),
				"clientSecret": pulumi.String("FcJkQ3iPSaKAQRA7Ft8Q~fZ1X5vKmqzUAfJagcJ8"),
			},
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
import com.pulumi.azurenative.apimanagement.Authorization;
import com.pulumi.azurenative.apimanagement.AuthorizationArgs;
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
        var authorization = new Authorization("authorization", AuthorizationArgs.builder()        
            .authorizationId("authz1")
            .authorizationProviderId("aadwithclientcred")
            .authorizationType("OAuth2")
            .oAuth2GrantType("AuthorizationCode")
            .parameters(Map.ofEntries(
                Map.entry("clientId", "53790925-fdd3-4b80-bc7a-4c3aaf25801d"),
                Map.entry("clientSecret", "FcJkQ3iPSaKAQRA7Ft8Q~fZ1X5vKmqzUAfJagcJ8")
            ))
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const authorization = new azure_native.apimanagement.Authorization("authorization", {
    authorizationId: "authz1",
    authorizationProviderId: "aadwithclientcred",
    authorizationType: "OAuth2",
    oAuth2GrantType: "AuthorizationCode",
    parameters: {
        clientId: "53790925-fdd3-4b80-bc7a-4c3aaf25801d",
        clientSecret: "FcJkQ3iPSaKAQRA7Ft8Q~fZ1X5vKmqzUAfJagcJ8",
    },
    resourceGroupName: "rg1",
    serviceName: "apimService1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

authorization = azure_native.apimanagement.Authorization("authorization",
    authorization_id="authz1",
    authorization_provider_id="aadwithclientcred",
    authorization_type="OAuth2",
    o_auth2_grant_type="AuthorizationCode",
    parameters={
        "clientId": "53790925-fdd3-4b80-bc7a-4c3aaf25801d",
        "clientSecret": "FcJkQ3iPSaKAQRA7Ft8Q~fZ1X5vKmqzUAfJagcJ8",
    },
    resource_group_name="rg1",
    service_name="apimService1")

```

```yaml
resources:
  authorization:
    type: azure-native:apimanagement:Authorization
    properties:
      authorizationId: authz1
      authorizationProviderId: aadwithclientcred
      authorizationType: OAuth2
      oAuth2GrantType: AuthorizationCode
      parameters:
        clientId: 53790925-fdd3-4b80-bc7a-4c3aaf25801d
        clientSecret: FcJkQ3iPSaKAQRA7Ft8Q~fZ1X5vKmqzUAfJagcJ8
      resourceGroupName: rg1
      serviceName: apimService1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:Authorization authz1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/authorizationProviders/aadwithclientcred/authorizations/authz1 
```
