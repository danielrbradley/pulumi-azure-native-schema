External OAuth authorization server settings.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateAuthorizationServer
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var authorizationServer = new AzureNative.ApiManagement.AuthorizationServer("authorizationServer", new()
    {
        AuthorizationEndpoint = "https://www.contoso.com/oauth2/auth",
        AuthorizationMethods = new[]
        {
            AzureNative.ApiManagement.AuthorizationMethod.GET,
        },
        Authsid = "newauthServer",
        BearerTokenSendingMethods = new[]
        {
            "authorizationHeader",
        },
        ClientId = "1",
        ClientRegistrationEndpoint = "https://www.contoso.com/apps",
        ClientSecret = "2",
        DefaultScope = "read write",
        Description = "test server",
        DisplayName = "test2",
        GrantTypes = new[]
        {
            "authorizationCode",
            "implicit",
        },
        ResourceGroupName = "rg1",
        ResourceOwnerPassword = "pwd",
        ResourceOwnerUsername = "un",
        ServiceName = "apimService1",
        SupportState = true,
        TokenEndpoint = "https://www.contoso.com/oauth2/token",
        UseInApiDocumentation = true,
        UseInTestConsole = false,
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
		_, err := apimanagement.NewAuthorizationServer(ctx, "authorizationServer", &apimanagement.AuthorizationServerArgs{
			AuthorizationEndpoint: pulumi.String("https://www.contoso.com/oauth2/auth"),
			AuthorizationMethods: []apimanagement.AuthorizationMethod{
				apimanagement.AuthorizationMethodGET,
			},
			Authsid: pulumi.String("newauthServer"),
			BearerTokenSendingMethods: pulumi.StringArray{
				pulumi.String("authorizationHeader"),
			},
			ClientId:                   pulumi.String("1"),
			ClientRegistrationEndpoint: pulumi.String("https://www.contoso.com/apps"),
			ClientSecret:               pulumi.String("2"),
			DefaultScope:               pulumi.String("read write"),
			Description:                pulumi.String("test server"),
			DisplayName:                pulumi.String("test2"),
			GrantTypes: pulumi.StringArray{
				pulumi.String("authorizationCode"),
				pulumi.String("implicit"),
			},
			ResourceGroupName:     pulumi.String("rg1"),
			ResourceOwnerPassword: pulumi.String("pwd"),
			ResourceOwnerUsername: pulumi.String("un"),
			ServiceName:           pulumi.String("apimService1"),
			SupportState:          pulumi.Bool(true),
			TokenEndpoint:         pulumi.String("https://www.contoso.com/oauth2/token"),
			UseInApiDocumentation: pulumi.Bool(true),
			UseInTestConsole:      pulumi.Bool(false),
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
import com.pulumi.azurenative.apimanagement.AuthorizationServer;
import com.pulumi.azurenative.apimanagement.AuthorizationServerArgs;
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
        var authorizationServer = new AuthorizationServer("authorizationServer", AuthorizationServerArgs.builder()        
            .authorizationEndpoint("https://www.contoso.com/oauth2/auth")
            .authorizationMethods("GET")
            .authsid("newauthServer")
            .bearerTokenSendingMethods("authorizationHeader")
            .clientId("1")
            .clientRegistrationEndpoint("https://www.contoso.com/apps")
            .clientSecret("2")
            .defaultScope("read write")
            .description("test server")
            .displayName("test2")
            .grantTypes(            
                "authorizationCode",
                "implicit")
            .resourceGroupName("rg1")
            .resourceOwnerPassword("pwd")
            .resourceOwnerUsername("un")
            .serviceName("apimService1")
            .supportState(true)
            .tokenEndpoint("https://www.contoso.com/oauth2/token")
            .useInApiDocumentation(true)
            .useInTestConsole(false)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const authorizationServer = new azure_native.apimanagement.AuthorizationServer("authorizationServer", {
    authorizationEndpoint: "https://www.contoso.com/oauth2/auth",
    authorizationMethods: [azure_native.apimanagement.AuthorizationMethod.GET],
    authsid: "newauthServer",
    bearerTokenSendingMethods: ["authorizationHeader"],
    clientId: "1",
    clientRegistrationEndpoint: "https://www.contoso.com/apps",
    clientSecret: "2",
    defaultScope: "read write",
    description: "test server",
    displayName: "test2",
    grantTypes: [
        "authorizationCode",
        "implicit",
    ],
    resourceGroupName: "rg1",
    resourceOwnerPassword: "pwd",
    resourceOwnerUsername: "un",
    serviceName: "apimService1",
    supportState: true,
    tokenEndpoint: "https://www.contoso.com/oauth2/token",
    useInApiDocumentation: true,
    useInTestConsole: false,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

authorization_server = azure_native.apimanagement.AuthorizationServer("authorizationServer",
    authorization_endpoint="https://www.contoso.com/oauth2/auth",
    authorization_methods=[azure_native.apimanagement.AuthorizationMethod.GET],
    authsid="newauthServer",
    bearer_token_sending_methods=["authorizationHeader"],
    client_id="1",
    client_registration_endpoint="https://www.contoso.com/apps",
    client_secret="2",
    default_scope="read write",
    description="test server",
    display_name="test2",
    grant_types=[
        "authorizationCode",
        "implicit",
    ],
    resource_group_name="rg1",
    resource_owner_password="pwd",
    resource_owner_username="un",
    service_name="apimService1",
    support_state=True,
    token_endpoint="https://www.contoso.com/oauth2/token",
    use_in_api_documentation=True,
    use_in_test_console=False)

```

```yaml
resources:
  authorizationServer:
    type: azure-native:apimanagement:AuthorizationServer
    properties:
      authorizationEndpoint: https://www.contoso.com/oauth2/auth
      authorizationMethods:
        - GET
      authsid: newauthServer
      bearerTokenSendingMethods:
        - authorizationHeader
      clientId: '1'
      clientRegistrationEndpoint: https://www.contoso.com/apps
      clientSecret: '2'
      defaultScope: read write
      description: test server
      displayName: test2
      grantTypes:
        - authorizationCode
        - implicit
      resourceGroupName: rg1
      resourceOwnerPassword: pwd
      resourceOwnerUsername: un
      serviceName: apimService1
      supportState: true
      tokenEndpoint: https://www.contoso.com/oauth2/token
      useInApiDocumentation: true
      useInTestConsole: false

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:AuthorizationServer newauthServer /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/authorizationServers/newauthServer 
```
