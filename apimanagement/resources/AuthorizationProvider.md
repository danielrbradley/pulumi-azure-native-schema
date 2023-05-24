Authorization Provider contract.
API Version: 2022-08-01.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateAuthorizationProviderAADAuthCode
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var authorizationProvider = new AzureNative.ApiManagement.AuthorizationProvider("authorizationProvider", new()
    {
        AuthorizationProviderId = "aadwithauthcode",
        DisplayName = "aadwithauthcode",
        IdentityProvider = "aad",
        Oauth2 = new AzureNative.ApiManagement.Inputs.AuthorizationProviderOAuth2SettingsArgs
        {
            GrantTypes = new AzureNative.ApiManagement.Inputs.AuthorizationProviderOAuth2GrantTypesArgs
            {
                AuthorizationCode = 
                {
                    { "clientId", "59790825-fdd3-4b10-bc7a-4c3aaf25801d" },
                    { "clientSecret", "Q3iPSaKQ~fZFcJk5vKmqzUAfJagcJ8" },
                    { "resourceUri", "https://graph.microsoft.com" },
                    { "scopes", "User.Read.All Group.Read.All" },
                },
            },
            RedirectUrl = "https://authorization-manager.consent.azure-apim.net/redirect/apim/apimService1",
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
		_, err := apimanagement.NewAuthorizationProvider(ctx, "authorizationProvider", &apimanagement.AuthorizationProviderArgs{
			AuthorizationProviderId: pulumi.String("aadwithauthcode"),
			DisplayName:             pulumi.String("aadwithauthcode"),
			IdentityProvider:        pulumi.String("aad"),
			Oauth2: apimanagement.AuthorizationProviderOAuth2SettingsResponse{
				GrantTypes: &apimanagement.AuthorizationProviderOAuth2GrantTypesArgs{
					AuthorizationCode: pulumi.StringMap{
						"clientId":     pulumi.String("59790825-fdd3-4b10-bc7a-4c3aaf25801d"),
						"clientSecret": pulumi.String("Q3iPSaKQ~fZFcJk5vKmqzUAfJagcJ8"),
						"resourceUri":  pulumi.String("https://graph.microsoft.com"),
						"scopes":       pulumi.String("User.Read.All Group.Read.All"),
					},
				},
				RedirectUrl: pulumi.String("https://authorization-manager.consent.azure-apim.net/redirect/apim/apimService1"),
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
import com.pulumi.azurenative.apimanagement.AuthorizationProvider;
import com.pulumi.azurenative.apimanagement.AuthorizationProviderArgs;
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
        var authorizationProvider = new AuthorizationProvider("authorizationProvider", AuthorizationProviderArgs.builder()        
            .authorizationProviderId("aadwithauthcode")
            .displayName("aadwithauthcode")
            .identityProvider("aad")
            .oauth2(Map.ofEntries(
                Map.entry("grantTypes", Map.of("authorizationCode", Map.ofEntries(
                    Map.entry("clientId", "59790825-fdd3-4b10-bc7a-4c3aaf25801d"),
                    Map.entry("clientSecret", "Q3iPSaKQ~fZFcJk5vKmqzUAfJagcJ8"),
                    Map.entry("resourceUri", "https://graph.microsoft.com"),
                    Map.entry("scopes", "User.Read.All Group.Read.All")
                ))),
                Map.entry("redirectUrl", "https://authorization-manager.consent.azure-apim.net/redirect/apim/apimService1")
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

const authorizationProvider = new azure_native.apimanagement.AuthorizationProvider("authorizationProvider", {
    authorizationProviderId: "aadwithauthcode",
    displayName: "aadwithauthcode",
    identityProvider: "aad",
    oauth2: {
        grantTypes: {
            authorizationCode: {
                clientId: "59790825-fdd3-4b10-bc7a-4c3aaf25801d",
                clientSecret: "Q3iPSaKQ~fZFcJk5vKmqzUAfJagcJ8",
                resourceUri: "https://graph.microsoft.com",
                scopes: "User.Read.All Group.Read.All",
            },
        },
        redirectUrl: "https://authorization-manager.consent.azure-apim.net/redirect/apim/apimService1",
    },
    resourceGroupName: "rg1",
    serviceName: "apimService1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

authorization_provider = azure_native.apimanagement.AuthorizationProvider("authorizationProvider",
    authorization_provider_id="aadwithauthcode",
    display_name="aadwithauthcode",
    identity_provider="aad",
    oauth2=azure_native.apimanagement.AuthorizationProviderOAuth2SettingsResponseArgs(
        grant_types=azure_native.apimanagement.AuthorizationProviderOAuth2GrantTypesArgs(
            authorization_code={
                "clientId": "59790825-fdd3-4b10-bc7a-4c3aaf25801d",
                "clientSecret": "Q3iPSaKQ~fZFcJk5vKmqzUAfJagcJ8",
                "resourceUri": "https://graph.microsoft.com",
                "scopes": "User.Read.All Group.Read.All",
            },
        ),
        redirect_url="https://authorization-manager.consent.azure-apim.net/redirect/apim/apimService1",
    ),
    resource_group_name="rg1",
    service_name="apimService1")

```

```yaml
resources:
  authorizationProvider:
    type: azure-native:apimanagement:AuthorizationProvider
    properties:
      authorizationProviderId: aadwithauthcode
      displayName: aadwithauthcode
      identityProvider: aad
      oauth2:
        grantTypes:
          authorizationCode:
            clientId: 59790825-fdd3-4b10-bc7a-4c3aaf25801d
            clientSecret: Q3iPSaKQ~fZFcJk5vKmqzUAfJagcJ8
            resourceUri: https://graph.microsoft.com
            scopes: User.Read.All Group.Read.All
        redirectUrl: https://authorization-manager.consent.azure-apim.net/redirect/apim/apimService1
      resourceGroupName: rg1
      serviceName: apimService1

```

{{% /example %}}
{{% example %}}
### ApiManagementCreateAuthorizationProviderAADClientCred
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var authorizationProvider = new AzureNative.ApiManagement.AuthorizationProvider("authorizationProvider", new()
    {
        AuthorizationProviderId = "aadwithclientcred",
        DisplayName = "aadwithclientcred",
        IdentityProvider = "aad",
        Oauth2 = new AzureNative.ApiManagement.Inputs.AuthorizationProviderOAuth2SettingsArgs
        {
            GrantTypes = new AzureNative.ApiManagement.Inputs.AuthorizationProviderOAuth2GrantTypesArgs
            {
                AuthorizationCode = 
                {
                    { "resourceUri", "https://graph.microsoft.com" },
                    { "scopes", "User.Read.All Group.Read.All" },
                },
            },
            RedirectUrl = "https://authorization-manager.consent.azure-apim.net/redirect/apim/apimService1",
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
		_, err := apimanagement.NewAuthorizationProvider(ctx, "authorizationProvider", &apimanagement.AuthorizationProviderArgs{
			AuthorizationProviderId: pulumi.String("aadwithclientcred"),
			DisplayName:             pulumi.String("aadwithclientcred"),
			IdentityProvider:        pulumi.String("aad"),
			Oauth2: apimanagement.AuthorizationProviderOAuth2SettingsResponse{
				GrantTypes: &apimanagement.AuthorizationProviderOAuth2GrantTypesArgs{
					AuthorizationCode: pulumi.StringMap{
						"resourceUri": pulumi.String("https://graph.microsoft.com"),
						"scopes":      pulumi.String("User.Read.All Group.Read.All"),
					},
				},
				RedirectUrl: pulumi.String("https://authorization-manager.consent.azure-apim.net/redirect/apim/apimService1"),
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
import com.pulumi.azurenative.apimanagement.AuthorizationProvider;
import com.pulumi.azurenative.apimanagement.AuthorizationProviderArgs;
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
        var authorizationProvider = new AuthorizationProvider("authorizationProvider", AuthorizationProviderArgs.builder()        
            .authorizationProviderId("aadwithclientcred")
            .displayName("aadwithclientcred")
            .identityProvider("aad")
            .oauth2(Map.ofEntries(
                Map.entry("grantTypes", Map.of("authorizationCode", Map.ofEntries(
                    Map.entry("resourceUri", "https://graph.microsoft.com"),
                    Map.entry("scopes", "User.Read.All Group.Read.All")
                ))),
                Map.entry("redirectUrl", "https://authorization-manager.consent.azure-apim.net/redirect/apim/apimService1")
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

const authorizationProvider = new azure_native.apimanagement.AuthorizationProvider("authorizationProvider", {
    authorizationProviderId: "aadwithclientcred",
    displayName: "aadwithclientcred",
    identityProvider: "aad",
    oauth2: {
        grantTypes: {
            authorizationCode: {
                resourceUri: "https://graph.microsoft.com",
                scopes: "User.Read.All Group.Read.All",
            },
        },
        redirectUrl: "https://authorization-manager.consent.azure-apim.net/redirect/apim/apimService1",
    },
    resourceGroupName: "rg1",
    serviceName: "apimService1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

authorization_provider = azure_native.apimanagement.AuthorizationProvider("authorizationProvider",
    authorization_provider_id="aadwithclientcred",
    display_name="aadwithclientcred",
    identity_provider="aad",
    oauth2=azure_native.apimanagement.AuthorizationProviderOAuth2SettingsResponseArgs(
        grant_types=azure_native.apimanagement.AuthorizationProviderOAuth2GrantTypesArgs(
            authorization_code={
                "resourceUri": "https://graph.microsoft.com",
                "scopes": "User.Read.All Group.Read.All",
            },
        ),
        redirect_url="https://authorization-manager.consent.azure-apim.net/redirect/apim/apimService1",
    ),
    resource_group_name="rg1",
    service_name="apimService1")

```

```yaml
resources:
  authorizationProvider:
    type: azure-native:apimanagement:AuthorizationProvider
    properties:
      authorizationProviderId: aadwithclientcred
      displayName: aadwithclientcred
      identityProvider: aad
      oauth2:
        grantTypes:
          authorizationCode:
            resourceUri: https://graph.microsoft.com
            scopes: User.Read.All Group.Read.All
        redirectUrl: https://authorization-manager.consent.azure-apim.net/redirect/apim/apimService1
      resourceGroupName: rg1
      serviceName: apimService1

```

{{% /example %}}
{{% example %}}
### ApiManagementCreateAuthorizationProviderOOBGoogle
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var authorizationProvider = new AzureNative.ApiManagement.AuthorizationProvider("authorizationProvider", new()
    {
        AuthorizationProviderId = "google",
        DisplayName = "google",
        IdentityProvider = "google",
        Oauth2 = new AzureNative.ApiManagement.Inputs.AuthorizationProviderOAuth2SettingsArgs
        {
            GrantTypes = new AzureNative.ApiManagement.Inputs.AuthorizationProviderOAuth2GrantTypesArgs
            {
                AuthorizationCode = 
                {
                    { "clientId", "508791967882-5qv6o2i99a75un7329vlegtk78kr766h.apps.googleusercontent.com" },
                    { "clientSecret", "qDN0VyVFjU1OsOyT5Kz8ce" },
                    { "scopes", "openid https://www.googleapis.com/auth/userinfo.profile https://www.googleapis.com/auth/userinfo.email" },
                },
            },
            RedirectUrl = "https://authorization-manager.consent.azure-apim.net/redirect/apim/apimService1",
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
		_, err := apimanagement.NewAuthorizationProvider(ctx, "authorizationProvider", &apimanagement.AuthorizationProviderArgs{
			AuthorizationProviderId: pulumi.String("google"),
			DisplayName:             pulumi.String("google"),
			IdentityProvider:        pulumi.String("google"),
			Oauth2: apimanagement.AuthorizationProviderOAuth2SettingsResponse{
				GrantTypes: &apimanagement.AuthorizationProviderOAuth2GrantTypesArgs{
					AuthorizationCode: pulumi.StringMap{
						"clientId":     pulumi.String("508791967882-5qv6o2i99a75un7329vlegtk78kr766h.apps.googleusercontent.com"),
						"clientSecret": pulumi.String("qDN0VyVFjU1OsOyT5Kz8ce"),
						"scopes":       pulumi.String("openid https://www.googleapis.com/auth/userinfo.profile https://www.googleapis.com/auth/userinfo.email"),
					},
				},
				RedirectUrl: pulumi.String("https://authorization-manager.consent.azure-apim.net/redirect/apim/apimService1"),
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
import com.pulumi.azurenative.apimanagement.AuthorizationProvider;
import com.pulumi.azurenative.apimanagement.AuthorizationProviderArgs;
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
        var authorizationProvider = new AuthorizationProvider("authorizationProvider", AuthorizationProviderArgs.builder()        
            .authorizationProviderId("google")
            .displayName("google")
            .identityProvider("google")
            .oauth2(Map.ofEntries(
                Map.entry("grantTypes", Map.of("authorizationCode", Map.ofEntries(
                    Map.entry("clientId", "508791967882-5qv6o2i99a75un7329vlegtk78kr766h.apps.googleusercontent.com"),
                    Map.entry("clientSecret", "qDN0VyVFjU1OsOyT5Kz8ce"),
                    Map.entry("scopes", "openid https://www.googleapis.com/auth/userinfo.profile https://www.googleapis.com/auth/userinfo.email")
                ))),
                Map.entry("redirectUrl", "https://authorization-manager.consent.azure-apim.net/redirect/apim/apimService1")
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

const authorizationProvider = new azure_native.apimanagement.AuthorizationProvider("authorizationProvider", {
    authorizationProviderId: "google",
    displayName: "google",
    identityProvider: "google",
    oauth2: {
        grantTypes: {
            authorizationCode: {
                clientId: "508791967882-5qv6o2i99a75un7329vlegtk78kr766h.apps.googleusercontent.com",
                clientSecret: "qDN0VyVFjU1OsOyT5Kz8ce",
                scopes: "openid https://www.googleapis.com/auth/userinfo.profile https://www.googleapis.com/auth/userinfo.email",
            },
        },
        redirectUrl: "https://authorization-manager.consent.azure-apim.net/redirect/apim/apimService1",
    },
    resourceGroupName: "rg1",
    serviceName: "apimService1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

authorization_provider = azure_native.apimanagement.AuthorizationProvider("authorizationProvider",
    authorization_provider_id="google",
    display_name="google",
    identity_provider="google",
    oauth2=azure_native.apimanagement.AuthorizationProviderOAuth2SettingsResponseArgs(
        grant_types=azure_native.apimanagement.AuthorizationProviderOAuth2GrantTypesArgs(
            authorization_code={
                "clientId": "508791967882-5qv6o2i99a75un7329vlegtk78kr766h.apps.googleusercontent.com",
                "clientSecret": "qDN0VyVFjU1OsOyT5Kz8ce",
                "scopes": "openid https://www.googleapis.com/auth/userinfo.profile https://www.googleapis.com/auth/userinfo.email",
            },
        ),
        redirect_url="https://authorization-manager.consent.azure-apim.net/redirect/apim/apimService1",
    ),
    resource_group_name="rg1",
    service_name="apimService1")

```

```yaml
resources:
  authorizationProvider:
    type: azure-native:apimanagement:AuthorizationProvider
    properties:
      authorizationProviderId: google
      displayName: google
      identityProvider: google
      oauth2:
        grantTypes:
          authorizationCode:
            clientId: 508791967882-5qv6o2i99a75un7329vlegtk78kr766h.apps.googleusercontent.com
            clientSecret: qDN0VyVFjU1OsOyT5Kz8ce
            scopes: openid https://www.googleapis.com/auth/userinfo.profile https://www.googleapis.com/auth/userinfo.email
        redirectUrl: https://authorization-manager.consent.azure-apim.net/redirect/apim/apimService1
      resourceGroupName: rg1
      serviceName: apimService1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:AuthorizationProvider google /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/authorizationProviders/google 
```
