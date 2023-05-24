API details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateApi
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var api = new AzureNative.ApiManagement.Api("api", new()
    {
        ApiId = "tempgroup",
        AuthenticationSettings = new AzureNative.ApiManagement.Inputs.AuthenticationSettingsContractArgs
        {
            OAuth2 = new AzureNative.ApiManagement.Inputs.OAuth2AuthenticationSettingsContractArgs
            {
                AuthorizationServerId = "authorizationServerId2283",
                Scope = "oauth2scope2580",
            },
        },
        Description = "apidescription5200",
        DisplayName = "apiname1463",
        Path = "newapiPath",
        Protocols = new[]
        {
            "https",
            "http",
        },
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        ServiceUrl = "http://newechoapi.cloudapp.net/api",
        SubscriptionKeyParameterNames = new AzureNative.ApiManagement.Inputs.SubscriptionKeyParameterNamesContractArgs
        {
            Header = "header4520",
            Query = "query3037",
        },
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
		_, err := apimanagement.NewApi(ctx, "api", &apimanagement.ApiArgs{
			ApiId: pulumi.String("tempgroup"),
			AuthenticationSettings: apimanagement.AuthenticationSettingsContractResponse{
				OAuth2: &apimanagement.OAuth2AuthenticationSettingsContractArgs{
					AuthorizationServerId: pulumi.String("authorizationServerId2283"),
					Scope:                 pulumi.String("oauth2scope2580"),
				},
			},
			Description: pulumi.String("apidescription5200"),
			DisplayName: pulumi.String("apiname1463"),
			Path:        pulumi.String("newapiPath"),
			Protocols: pulumi.StringArray{
				pulumi.String("https"),
				pulumi.String("http"),
			},
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			ServiceUrl:        pulumi.String("http://newechoapi.cloudapp.net/api"),
			SubscriptionKeyParameterNames: &apimanagement.SubscriptionKeyParameterNamesContractArgs{
				Header: pulumi.String("header4520"),
				Query:  pulumi.String("query3037"),
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
import com.pulumi.azurenative.apimanagement.Api;
import com.pulumi.azurenative.apimanagement.ApiArgs;
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
        var api = new Api("api", ApiArgs.builder()        
            .apiId("tempgroup")
            .authenticationSettings(Map.of("oAuth2", Map.ofEntries(
                Map.entry("authorizationServerId", "authorizationServerId2283"),
                Map.entry("scope", "oauth2scope2580")
            )))
            .description("apidescription5200")
            .displayName("apiname1463")
            .path("newapiPath")
            .protocols(            
                "https",
                "http")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .serviceUrl("http://newechoapi.cloudapp.net/api")
            .subscriptionKeyParameterNames(Map.ofEntries(
                Map.entry("header", "header4520"),
                Map.entry("query", "query3037")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const api = new azure_native.apimanagement.Api("api", {
    apiId: "tempgroup",
    authenticationSettings: {
        oAuth2: {
            authorizationServerId: "authorizationServerId2283",
            scope: "oauth2scope2580",
        },
    },
    description: "apidescription5200",
    displayName: "apiname1463",
    path: "newapiPath",
    protocols: [
        "https",
        "http",
    ],
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    serviceUrl: "http://newechoapi.cloudapp.net/api",
    subscriptionKeyParameterNames: {
        header: "header4520",
        query: "query3037",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api = azure_native.apimanagement.Api("api",
    api_id="tempgroup",
    authentication_settings=azure_native.apimanagement.AuthenticationSettingsContractResponseArgs(
        o_auth2=azure_native.apimanagement.OAuth2AuthenticationSettingsContractArgs(
            authorization_server_id="authorizationServerId2283",
            scope="oauth2scope2580",
        ),
    ),
    description="apidescription5200",
    display_name="apiname1463",
    path="newapiPath",
    protocols=[
        "https",
        "http",
    ],
    resource_group_name="rg1",
    service_name="apimService1",
    service_url="http://newechoapi.cloudapp.net/api",
    subscription_key_parameter_names=azure_native.apimanagement.SubscriptionKeyParameterNamesContractArgs(
        header="header4520",
        query="query3037",
    ))

```

```yaml
resources:
  api:
    type: azure-native:apimanagement:Api
    properties:
      apiId: tempgroup
      authenticationSettings:
        oAuth2:
          authorizationServerId: authorizationServerId2283
          scope: oauth2scope2580
      description: apidescription5200
      displayName: apiname1463
      path: newapiPath
      protocols:
        - https
        - http
      resourceGroupName: rg1
      serviceName: apimService1
      serviceUrl: http://newechoapi.cloudapp.net/api
      subscriptionKeyParameterNames:
        header: header4520
        query: query3037

```

{{% /example %}}
{{% example %}}
### ApiManagementCreateApiClone
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var api = new AzureNative.ApiManagement.Api("api", new()
    {
        ApiId = "echo-api2",
        Description = "Copy of Existing Echo Api including Operations.",
        DisplayName = "Echo API2",
        IsCurrent = true,
        Path = "echo2",
        Protocols = new[]
        {
            "http",
            "https",
        },
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        ServiceUrl = "http://echoapi.cloudapp.net/api",
        SourceApiId = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apis/58a4aeac497000007d040001",
        SubscriptionRequired = true,
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
		_, err := apimanagement.NewApi(ctx, "api", &apimanagement.ApiArgs{
			ApiId:       pulumi.String("echo-api2"),
			Description: pulumi.String("Copy of Existing Echo Api including Operations."),
			DisplayName: pulumi.String("Echo API2"),
			IsCurrent:   pulumi.Bool(true),
			Path:        pulumi.String("echo2"),
			Protocols: pulumi.StringArray{
				pulumi.String("http"),
				pulumi.String("https"),
			},
			ResourceGroupName:    pulumi.String("rg1"),
			ServiceName:          pulumi.String("apimService1"),
			ServiceUrl:           pulumi.String("http://echoapi.cloudapp.net/api"),
			SourceApiId:          pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apis/58a4aeac497000007d040001"),
			SubscriptionRequired: pulumi.Bool(true),
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
import com.pulumi.azurenative.apimanagement.Api;
import com.pulumi.azurenative.apimanagement.ApiArgs;
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
        var api = new Api("api", ApiArgs.builder()        
            .apiId("echo-api2")
            .description("Copy of Existing Echo Api including Operations.")
            .displayName("Echo API2")
            .isCurrent(true)
            .path("echo2")
            .protocols(            
                "http",
                "https")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .serviceUrl("http://echoapi.cloudapp.net/api")
            .sourceApiId("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apis/58a4aeac497000007d040001")
            .subscriptionRequired(true)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const api = new azure_native.apimanagement.Api("api", {
    apiId: "echo-api2",
    description: "Copy of Existing Echo Api including Operations.",
    displayName: "Echo API2",
    isCurrent: true,
    path: "echo2",
    protocols: [
        "http",
        "https",
    ],
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    serviceUrl: "http://echoapi.cloudapp.net/api",
    sourceApiId: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apis/58a4aeac497000007d040001",
    subscriptionRequired: true,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api = azure_native.apimanagement.Api("api",
    api_id="echo-api2",
    description="Copy of Existing Echo Api including Operations.",
    display_name="Echo API2",
    is_current=True,
    path="echo2",
    protocols=[
        "http",
        "https",
    ],
    resource_group_name="rg1",
    service_name="apimService1",
    service_url="http://echoapi.cloudapp.net/api",
    source_api_id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apis/58a4aeac497000007d040001",
    subscription_required=True)

```

```yaml
resources:
  api:
    type: azure-native:apimanagement:Api
    properties:
      apiId: echo-api2
      description: Copy of Existing Echo Api including Operations.
      displayName: Echo API2
      isCurrent: true
      path: echo2
      protocols:
        - http
        - https
      resourceGroupName: rg1
      serviceName: apimService1
      serviceUrl: http://echoapi.cloudapp.net/api
      sourceApiId: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apis/58a4aeac497000007d040001
      subscriptionRequired: true

```

{{% /example %}}
{{% example %}}
### ApiManagementCreateApiNewVersionUsingExistingApi
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var api = new AzureNative.ApiManagement.Api("api", new()
    {
        ApiId = "echoapiv3",
        ApiVersion = "v4",
        ApiVersionSetId = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apiVersionSets/aa9c59e6-c0cd-4258-9356-9ca7d2f0b458",
        Description = "Create Echo API into a new Version using Existing Version Set and Copy all Operations.",
        DisplayName = "Echo API2",
        IsCurrent = true,
        Path = "echo2",
        Protocols = new[]
        {
            "http",
            "https",
        },
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        ServiceUrl = "http://echoapi.cloudapp.net/api",
        SourceApiId = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apis/echoPath",
        SubscriptionRequired = true,
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
		_, err := apimanagement.NewApi(ctx, "api", &apimanagement.ApiArgs{
			ApiId:           pulumi.String("echoapiv3"),
			ApiVersion:      pulumi.String("v4"),
			ApiVersionSetId: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apiVersionSets/aa9c59e6-c0cd-4258-9356-9ca7d2f0b458"),
			Description:     pulumi.String("Create Echo API into a new Version using Existing Version Set and Copy all Operations."),
			DisplayName:     pulumi.String("Echo API2"),
			IsCurrent:       pulumi.Bool(true),
			Path:            pulumi.String("echo2"),
			Protocols: pulumi.StringArray{
				pulumi.String("http"),
				pulumi.String("https"),
			},
			ResourceGroupName:    pulumi.String("rg1"),
			ServiceName:          pulumi.String("apimService1"),
			ServiceUrl:           pulumi.String("http://echoapi.cloudapp.net/api"),
			SourceApiId:          pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apis/echoPath"),
			SubscriptionRequired: pulumi.Bool(true),
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
import com.pulumi.azurenative.apimanagement.Api;
import com.pulumi.azurenative.apimanagement.ApiArgs;
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
        var api = new Api("api", ApiArgs.builder()        
            .apiId("echoapiv3")
            .apiVersion("v4")
            .apiVersionSetId("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apiVersionSets/aa9c59e6-c0cd-4258-9356-9ca7d2f0b458")
            .description("Create Echo API into a new Version using Existing Version Set and Copy all Operations.")
            .displayName("Echo API2")
            .isCurrent(true)
            .path("echo2")
            .protocols(            
                "http",
                "https")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .serviceUrl("http://echoapi.cloudapp.net/api")
            .sourceApiId("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apis/echoPath")
            .subscriptionRequired(true)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const api = new azure_native.apimanagement.Api("api", {
    apiId: "echoapiv3",
    apiVersion: "v4",
    apiVersionSetId: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apiVersionSets/aa9c59e6-c0cd-4258-9356-9ca7d2f0b458",
    description: "Create Echo API into a new Version using Existing Version Set and Copy all Operations.",
    displayName: "Echo API2",
    isCurrent: true,
    path: "echo2",
    protocols: [
        "http",
        "https",
    ],
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    serviceUrl: "http://echoapi.cloudapp.net/api",
    sourceApiId: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apis/echoPath",
    subscriptionRequired: true,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api = azure_native.apimanagement.Api("api",
    api_id="echoapiv3",
    api_version="v4",
    api_version_set_id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apiVersionSets/aa9c59e6-c0cd-4258-9356-9ca7d2f0b458",
    description="Create Echo API into a new Version using Existing Version Set and Copy all Operations.",
    display_name="Echo API2",
    is_current=True,
    path="echo2",
    protocols=[
        "http",
        "https",
    ],
    resource_group_name="rg1",
    service_name="apimService1",
    service_url="http://echoapi.cloudapp.net/api",
    source_api_id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apis/echoPath",
    subscription_required=True)

```

```yaml
resources:
  api:
    type: azure-native:apimanagement:Api
    properties:
      apiId: echoapiv3
      apiVersion: v4
      apiVersionSetId: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apiVersionSets/aa9c59e6-c0cd-4258-9356-9ca7d2f0b458
      description: Create Echo API into a new Version using Existing Version Set and Copy all Operations.
      displayName: Echo API2
      isCurrent: true
      path: echo2
      protocols:
        - http
        - https
      resourceGroupName: rg1
      serviceName: apimService1
      serviceUrl: http://echoapi.cloudapp.net/api
      sourceApiId: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apis/echoPath
      subscriptionRequired: true

```

{{% /example %}}
{{% example %}}
### ApiManagementCreateApiRevisionFromExistingApi
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var api = new AzureNative.ApiManagement.Api("api", new()
    {
        ApiId = "echo-api;rev=3",
        ApiRevisionDescription = "Creating a Revision of an existing API",
        Path = "echo",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        ServiceUrl = "http://echoapi.cloudapp.net/apiv3",
        SourceApiId = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apis/echo-api",
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
		_, err := apimanagement.NewApi(ctx, "api", &apimanagement.ApiArgs{
			ApiId:                  pulumi.String("echo-api;rev=3"),
			ApiRevisionDescription: pulumi.String("Creating a Revision of an existing API"),
			Path:                   pulumi.String("echo"),
			ResourceGroupName:      pulumi.String("rg1"),
			ServiceName:            pulumi.String("apimService1"),
			ServiceUrl:             pulumi.String("http://echoapi.cloudapp.net/apiv3"),
			SourceApiId:            pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apis/echo-api"),
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
import com.pulumi.azurenative.apimanagement.Api;
import com.pulumi.azurenative.apimanagement.ApiArgs;
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
        var api = new Api("api", ApiArgs.builder()        
            .apiId("echo-api;rev=3")
            .apiRevisionDescription("Creating a Revision of an existing API")
            .path("echo")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .serviceUrl("http://echoapi.cloudapp.net/apiv3")
            .sourceApiId("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apis/echo-api")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const api = new azure_native.apimanagement.Api("api", {
    apiId: "echo-api;rev=3",
    apiRevisionDescription: "Creating a Revision of an existing API",
    path: "echo",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    serviceUrl: "http://echoapi.cloudapp.net/apiv3",
    sourceApiId: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apis/echo-api",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api = azure_native.apimanagement.Api("api",
    api_id="echo-api;rev=3",
    api_revision_description="Creating a Revision of an existing API",
    path="echo",
    resource_group_name="rg1",
    service_name="apimService1",
    service_url="http://echoapi.cloudapp.net/apiv3",
    source_api_id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apis/echo-api")

```

```yaml
resources:
  api:
    type: azure-native:apimanagement:Api
    properties:
      apiId: echo-api;rev=3
      apiRevisionDescription: Creating a Revision of an existing API
      path: echo
      resourceGroupName: rg1
      serviceName: apimService1
      serviceUrl: http://echoapi.cloudapp.net/apiv3
      sourceApiId: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apis/echo-api

```

{{% /example %}}
{{% example %}}
### ApiManagementCreateApiUsingImportOverrideServiceUrl
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var api = new AzureNative.ApiManagement.Api("api", new()
    {
        ApiId = "apidocs",
        Format = "swagger-link",
        Path = "petstoreapi123",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        ServiceUrl = "http://petstore.swagger.wordnik.com/api",
        Value = "http://apimpimportviaurl.azurewebsites.net/api/apidocs/",
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
		_, err := apimanagement.NewApi(ctx, "api", &apimanagement.ApiArgs{
			ApiId:             pulumi.String("apidocs"),
			Format:            pulumi.String("swagger-link"),
			Path:              pulumi.String("petstoreapi123"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			ServiceUrl:        pulumi.String("http://petstore.swagger.wordnik.com/api"),
			Value:             pulumi.String("http://apimpimportviaurl.azurewebsites.net/api/apidocs/"),
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
import com.pulumi.azurenative.apimanagement.Api;
import com.pulumi.azurenative.apimanagement.ApiArgs;
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
        var api = new Api("api", ApiArgs.builder()        
            .apiId("apidocs")
            .format("swagger-link")
            .path("petstoreapi123")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .serviceUrl("http://petstore.swagger.wordnik.com/api")
            .value("http://apimpimportviaurl.azurewebsites.net/api/apidocs/")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const api = new azure_native.apimanagement.Api("api", {
    apiId: "apidocs",
    format: "swagger-link",
    path: "petstoreapi123",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    serviceUrl: "http://petstore.swagger.wordnik.com/api",
    value: "http://apimpimportviaurl.azurewebsites.net/api/apidocs/",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api = azure_native.apimanagement.Api("api",
    api_id="apidocs",
    format="swagger-link",
    path="petstoreapi123",
    resource_group_name="rg1",
    service_name="apimService1",
    service_url="http://petstore.swagger.wordnik.com/api",
    value="http://apimpimportviaurl.azurewebsites.net/api/apidocs/")

```

```yaml
resources:
  api:
    type: azure-native:apimanagement:Api
    properties:
      apiId: apidocs
      format: swagger-link
      path: petstoreapi123
      resourceGroupName: rg1
      serviceName: apimService1
      serviceUrl: http://petstore.swagger.wordnik.com/api
      value: http://apimpimportviaurl.azurewebsites.net/api/apidocs/

```

{{% /example %}}
{{% example %}}
### ApiManagementCreateApiUsingOai3Import
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var api = new AzureNative.ApiManagement.Api("api", new()
    {
        ApiId = "petstore",
        Format = "openapi-link",
        Path = "petstore",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        Value = "https://raw.githubusercontent.com/OAI/OpenAPI-Specification/master/examples/v3.0/petstore.yaml",
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
		_, err := apimanagement.NewApi(ctx, "api", &apimanagement.ApiArgs{
			ApiId:             pulumi.String("petstore"),
			Format:            pulumi.String("openapi-link"),
			Path:              pulumi.String("petstore"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			Value:             pulumi.String("https://raw.githubusercontent.com/OAI/OpenAPI-Specification/master/examples/v3.0/petstore.yaml"),
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
import com.pulumi.azurenative.apimanagement.Api;
import com.pulumi.azurenative.apimanagement.ApiArgs;
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
        var api = new Api("api", ApiArgs.builder()        
            .apiId("petstore")
            .format("openapi-link")
            .path("petstore")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .value("https://raw.githubusercontent.com/OAI/OpenAPI-Specification/master/examples/v3.0/petstore.yaml")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const api = new azure_native.apimanagement.Api("api", {
    apiId: "petstore",
    format: "openapi-link",
    path: "petstore",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    value: "https://raw.githubusercontent.com/OAI/OpenAPI-Specification/master/examples/v3.0/petstore.yaml",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api = azure_native.apimanagement.Api("api",
    api_id="petstore",
    format="openapi-link",
    path="petstore",
    resource_group_name="rg1",
    service_name="apimService1",
    value="https://raw.githubusercontent.com/OAI/OpenAPI-Specification/master/examples/v3.0/petstore.yaml")

```

```yaml
resources:
  api:
    type: azure-native:apimanagement:Api
    properties:
      apiId: petstore
      format: openapi-link
      path: petstore
      resourceGroupName: rg1
      serviceName: apimService1
      value: https://raw.githubusercontent.com/OAI/OpenAPI-Specification/master/examples/v3.0/petstore.yaml

```

{{% /example %}}
{{% example %}}
### ApiManagementCreateApiUsingOai3ImportWithTranslateRequiredQueryParametersConduct
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var api = new AzureNative.ApiManagement.Api("api", new()
    {
        ApiId = "petstore",
        Format = "openapi-link",
        Path = "petstore",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        TranslateRequiredQueryParametersConduct = "template",
        Value = "https://raw.githubusercontent.com/OAI/OpenAPI-Specification/master/examples/v3.0/petstore.yaml",
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
		_, err := apimanagement.NewApi(ctx, "api", &apimanagement.ApiArgs{
			ApiId:                                   pulumi.String("petstore"),
			Format:                                  pulumi.String("openapi-link"),
			Path:                                    pulumi.String("petstore"),
			ResourceGroupName:                       pulumi.String("rg1"),
			ServiceName:                             pulumi.String("apimService1"),
			TranslateRequiredQueryParametersConduct: pulumi.String("template"),
			Value:                                   pulumi.String("https://raw.githubusercontent.com/OAI/OpenAPI-Specification/master/examples/v3.0/petstore.yaml"),
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
import com.pulumi.azurenative.apimanagement.Api;
import com.pulumi.azurenative.apimanagement.ApiArgs;
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
        var api = new Api("api", ApiArgs.builder()        
            .apiId("petstore")
            .format("openapi-link")
            .path("petstore")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .translateRequiredQueryParametersConduct("template")
            .value("https://raw.githubusercontent.com/OAI/OpenAPI-Specification/master/examples/v3.0/petstore.yaml")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const api = new azure_native.apimanagement.Api("api", {
    apiId: "petstore",
    format: "openapi-link",
    path: "petstore",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    translateRequiredQueryParametersConduct: "template",
    value: "https://raw.githubusercontent.com/OAI/OpenAPI-Specification/master/examples/v3.0/petstore.yaml",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api = azure_native.apimanagement.Api("api",
    api_id="petstore",
    format="openapi-link",
    path="petstore",
    resource_group_name="rg1",
    service_name="apimService1",
    translate_required_query_parameters_conduct="template",
    value="https://raw.githubusercontent.com/OAI/OpenAPI-Specification/master/examples/v3.0/petstore.yaml")

```

```yaml
resources:
  api:
    type: azure-native:apimanagement:Api
    properties:
      apiId: petstore
      format: openapi-link
      path: petstore
      resourceGroupName: rg1
      serviceName: apimService1
      translateRequiredQueryParametersConduct: template
      value: https://raw.githubusercontent.com/OAI/OpenAPI-Specification/master/examples/v3.0/petstore.yaml

```

{{% /example %}}
{{% example %}}
### ApiManagementCreateApiUsingSwaggerImport
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var api = new AzureNative.ApiManagement.Api("api", new()
    {
        ApiId = "petstore",
        Format = "swagger-link-json",
        Path = "petstore",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        Value = "http://petstore.swagger.io/v2/swagger.json",
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
		_, err := apimanagement.NewApi(ctx, "api", &apimanagement.ApiArgs{
			ApiId:             pulumi.String("petstore"),
			Format:            pulumi.String("swagger-link-json"),
			Path:              pulumi.String("petstore"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			Value:             pulumi.String("http://petstore.swagger.io/v2/swagger.json"),
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
import com.pulumi.azurenative.apimanagement.Api;
import com.pulumi.azurenative.apimanagement.ApiArgs;
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
        var api = new Api("api", ApiArgs.builder()        
            .apiId("petstore")
            .format("swagger-link-json")
            .path("petstore")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .value("http://petstore.swagger.io/v2/swagger.json")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const api = new azure_native.apimanagement.Api("api", {
    apiId: "petstore",
    format: "swagger-link-json",
    path: "petstore",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    value: "http://petstore.swagger.io/v2/swagger.json",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api = azure_native.apimanagement.Api("api",
    api_id="petstore",
    format="swagger-link-json",
    path="petstore",
    resource_group_name="rg1",
    service_name="apimService1",
    value="http://petstore.swagger.io/v2/swagger.json")

```

```yaml
resources:
  api:
    type: azure-native:apimanagement:Api
    properties:
      apiId: petstore
      format: swagger-link-json
      path: petstore
      resourceGroupName: rg1
      serviceName: apimService1
      value: http://petstore.swagger.io/v2/swagger.json

```

{{% /example %}}
{{% example %}}
### ApiManagementCreateApiUsingWadlImport
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var api = new AzureNative.ApiManagement.Api("api", new()
    {
        ApiId = "petstore",
        Format = "wadl-link-json",
        Path = "collector",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        Value = "https://developer.cisco.com/media/wae-release-6-2-api-reference/wae-collector-rest-api/application.wadl",
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
		_, err := apimanagement.NewApi(ctx, "api", &apimanagement.ApiArgs{
			ApiId:             pulumi.String("petstore"),
			Format:            pulumi.String("wadl-link-json"),
			Path:              pulumi.String("collector"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			Value:             pulumi.String("https://developer.cisco.com/media/wae-release-6-2-api-reference/wae-collector-rest-api/application.wadl"),
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
import com.pulumi.azurenative.apimanagement.Api;
import com.pulumi.azurenative.apimanagement.ApiArgs;
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
        var api = new Api("api", ApiArgs.builder()        
            .apiId("petstore")
            .format("wadl-link-json")
            .path("collector")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .value("https://developer.cisco.com/media/wae-release-6-2-api-reference/wae-collector-rest-api/application.wadl")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const api = new azure_native.apimanagement.Api("api", {
    apiId: "petstore",
    format: "wadl-link-json",
    path: "collector",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    value: "https://developer.cisco.com/media/wae-release-6-2-api-reference/wae-collector-rest-api/application.wadl",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api = azure_native.apimanagement.Api("api",
    api_id="petstore",
    format="wadl-link-json",
    path="collector",
    resource_group_name="rg1",
    service_name="apimService1",
    value="https://developer.cisco.com/media/wae-release-6-2-api-reference/wae-collector-rest-api/application.wadl")

```

```yaml
resources:
  api:
    type: azure-native:apimanagement:Api
    properties:
      apiId: petstore
      format: wadl-link-json
      path: collector
      resourceGroupName: rg1
      serviceName: apimService1
      value: https://developer.cisco.com/media/wae-release-6-2-api-reference/wae-collector-rest-api/application.wadl

```

{{% /example %}}
{{% example %}}
### ApiManagementCreateApiWithMultipleAuthServers
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var api = new AzureNative.ApiManagement.Api("api", new()
    {
        ApiId = "tempgroup",
        AuthenticationSettings = new AzureNative.ApiManagement.Inputs.AuthenticationSettingsContractArgs
        {
            OAuth2AuthenticationSettings = new[]
            {
                new AzureNative.ApiManagement.Inputs.OAuth2AuthenticationSettingsContractArgs
                {
                    AuthorizationServerId = "authorizationServerId2283",
                    Scope = "oauth2scope2580",
                },
                new AzureNative.ApiManagement.Inputs.OAuth2AuthenticationSettingsContractArgs
                {
                    AuthorizationServerId = "authorizationServerId2284",
                    Scope = "oauth2scope2581",
                },
            },
        },
        Description = "apidescription5200",
        DisplayName = "apiname1463",
        Path = "newapiPath",
        Protocols = new[]
        {
            "https",
            "http",
        },
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        ServiceUrl = "http://newechoapi.cloudapp.net/api",
        SubscriptionKeyParameterNames = new AzureNative.ApiManagement.Inputs.SubscriptionKeyParameterNamesContractArgs
        {
            Header = "header4520",
            Query = "query3037",
        },
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
		_, err := apimanagement.NewApi(ctx, "api", &apimanagement.ApiArgs{
			ApiId: pulumi.String("tempgroup"),
			AuthenticationSettings: apimanagement.AuthenticationSettingsContractResponse{
				OAuth2AuthenticationSettings: apimanagement.OAuth2AuthenticationSettingsContractArray{
					&apimanagement.OAuth2AuthenticationSettingsContractArgs{
						AuthorizationServerId: pulumi.String("authorizationServerId2283"),
						Scope:                 pulumi.String("oauth2scope2580"),
					},
					&apimanagement.OAuth2AuthenticationSettingsContractArgs{
						AuthorizationServerId: pulumi.String("authorizationServerId2284"),
						Scope:                 pulumi.String("oauth2scope2581"),
					},
				},
			},
			Description: pulumi.String("apidescription5200"),
			DisplayName: pulumi.String("apiname1463"),
			Path:        pulumi.String("newapiPath"),
			Protocols: pulumi.StringArray{
				pulumi.String("https"),
				pulumi.String("http"),
			},
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			ServiceUrl:        pulumi.String("http://newechoapi.cloudapp.net/api"),
			SubscriptionKeyParameterNames: &apimanagement.SubscriptionKeyParameterNamesContractArgs{
				Header: pulumi.String("header4520"),
				Query:  pulumi.String("query3037"),
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
import com.pulumi.azurenative.apimanagement.Api;
import com.pulumi.azurenative.apimanagement.ApiArgs;
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
        var api = new Api("api", ApiArgs.builder()        
            .apiId("tempgroup")
            .authenticationSettings(Map.of("oAuth2AuthenticationSettings",             
                Map.ofEntries(
                    Map.entry("authorizationServerId", "authorizationServerId2283"),
                    Map.entry("scope", "oauth2scope2580")
                ),
                Map.ofEntries(
                    Map.entry("authorizationServerId", "authorizationServerId2284"),
                    Map.entry("scope", "oauth2scope2581")
                )))
            .description("apidescription5200")
            .displayName("apiname1463")
            .path("newapiPath")
            .protocols(            
                "https",
                "http")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .serviceUrl("http://newechoapi.cloudapp.net/api")
            .subscriptionKeyParameterNames(Map.ofEntries(
                Map.entry("header", "header4520"),
                Map.entry("query", "query3037")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const api = new azure_native.apimanagement.Api("api", {
    apiId: "tempgroup",
    authenticationSettings: {
        oAuth2AuthenticationSettings: [
            {
                authorizationServerId: "authorizationServerId2283",
                scope: "oauth2scope2580",
            },
            {
                authorizationServerId: "authorizationServerId2284",
                scope: "oauth2scope2581",
            },
        ],
    },
    description: "apidescription5200",
    displayName: "apiname1463",
    path: "newapiPath",
    protocols: [
        "https",
        "http",
    ],
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    serviceUrl: "http://newechoapi.cloudapp.net/api",
    subscriptionKeyParameterNames: {
        header: "header4520",
        query: "query3037",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api = azure_native.apimanagement.Api("api",
    api_id="tempgroup",
    authentication_settings=azure_native.apimanagement.AuthenticationSettingsContractResponseArgs(
        o_auth2_authentication_settings=[
            azure_native.apimanagement.OAuth2AuthenticationSettingsContractArgs(
                authorization_server_id="authorizationServerId2283",
                scope="oauth2scope2580",
            ),
            azure_native.apimanagement.OAuth2AuthenticationSettingsContractArgs(
                authorization_server_id="authorizationServerId2284",
                scope="oauth2scope2581",
            ),
        ],
    ),
    description="apidescription5200",
    display_name="apiname1463",
    path="newapiPath",
    protocols=[
        "https",
        "http",
    ],
    resource_group_name="rg1",
    service_name="apimService1",
    service_url="http://newechoapi.cloudapp.net/api",
    subscription_key_parameter_names=azure_native.apimanagement.SubscriptionKeyParameterNamesContractArgs(
        header="header4520",
        query="query3037",
    ))

```

```yaml
resources:
  api:
    type: azure-native:apimanagement:Api
    properties:
      apiId: tempgroup
      authenticationSettings:
        oAuth2AuthenticationSettings:
          - authorizationServerId: authorizationServerId2283
            scope: oauth2scope2580
          - authorizationServerId: authorizationServerId2284
            scope: oauth2scope2581
      description: apidescription5200
      displayName: apiname1463
      path: newapiPath
      protocols:
        - https
        - http
      resourceGroupName: rg1
      serviceName: apimService1
      serviceUrl: http://newechoapi.cloudapp.net/api
      subscriptionKeyParameterNames:
        header: header4520
        query: query3037

```

{{% /example %}}
{{% example %}}
### ApiManagementCreateApiWithMultipleOpenIdConnectProviders
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var api = new AzureNative.ApiManagement.Api("api", new()
    {
        ApiId = "tempgroup",
        AuthenticationSettings = new AzureNative.ApiManagement.Inputs.AuthenticationSettingsContractArgs
        {
            OpenidAuthenticationSettings = new[]
            {
                new AzureNative.ApiManagement.Inputs.OpenIdAuthenticationSettingsContractArgs
                {
                    BearerTokenSendingMethods = new[]
                    {
                        "authorizationHeader",
                    },
                    OpenidProviderId = "openidProviderId2283",
                },
                new AzureNative.ApiManagement.Inputs.OpenIdAuthenticationSettingsContractArgs
                {
                    BearerTokenSendingMethods = new[]
                    {
                        "authorizationHeader",
                    },
                    OpenidProviderId = "openidProviderId2284",
                },
            },
        },
        Description = "apidescription5200",
        DisplayName = "apiname1463",
        Path = "newapiPath",
        Protocols = new[]
        {
            "https",
            "http",
        },
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        ServiceUrl = "http://newechoapi.cloudapp.net/api",
        SubscriptionKeyParameterNames = new AzureNative.ApiManagement.Inputs.SubscriptionKeyParameterNamesContractArgs
        {
            Header = "header4520",
            Query = "query3037",
        },
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
		_, err := apimanagement.NewApi(ctx, "api", &apimanagement.ApiArgs{
			ApiId: pulumi.String("tempgroup"),
			AuthenticationSettings: apimanagement.AuthenticationSettingsContractResponse{
				OpenidAuthenticationSettings: apimanagement.OpenIdAuthenticationSettingsContractArray{
					&apimanagement.OpenIdAuthenticationSettingsContractArgs{
						BearerTokenSendingMethods: pulumi.StringArray{
							pulumi.String("authorizationHeader"),
						},
						OpenidProviderId: pulumi.String("openidProviderId2283"),
					},
					&apimanagement.OpenIdAuthenticationSettingsContractArgs{
						BearerTokenSendingMethods: pulumi.StringArray{
							pulumi.String("authorizationHeader"),
						},
						OpenidProviderId: pulumi.String("openidProviderId2284"),
					},
				},
			},
			Description: pulumi.String("apidescription5200"),
			DisplayName: pulumi.String("apiname1463"),
			Path:        pulumi.String("newapiPath"),
			Protocols: pulumi.StringArray{
				pulumi.String("https"),
				pulumi.String("http"),
			},
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			ServiceUrl:        pulumi.String("http://newechoapi.cloudapp.net/api"),
			SubscriptionKeyParameterNames: &apimanagement.SubscriptionKeyParameterNamesContractArgs{
				Header: pulumi.String("header4520"),
				Query:  pulumi.String("query3037"),
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
import com.pulumi.azurenative.apimanagement.Api;
import com.pulumi.azurenative.apimanagement.ApiArgs;
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
        var api = new Api("api", ApiArgs.builder()        
            .apiId("tempgroup")
            .authenticationSettings(Map.of("openidAuthenticationSettings",             
                Map.ofEntries(
                    Map.entry("bearerTokenSendingMethods", "authorizationHeader"),
                    Map.entry("openidProviderId", "openidProviderId2283")
                ),
                Map.ofEntries(
                    Map.entry("bearerTokenSendingMethods", "authorizationHeader"),
                    Map.entry("openidProviderId", "openidProviderId2284")
                )))
            .description("apidescription5200")
            .displayName("apiname1463")
            .path("newapiPath")
            .protocols(            
                "https",
                "http")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .serviceUrl("http://newechoapi.cloudapp.net/api")
            .subscriptionKeyParameterNames(Map.ofEntries(
                Map.entry("header", "header4520"),
                Map.entry("query", "query3037")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const api = new azure_native.apimanagement.Api("api", {
    apiId: "tempgroup",
    authenticationSettings: {
        openidAuthenticationSettings: [
            {
                bearerTokenSendingMethods: ["authorizationHeader"],
                openidProviderId: "openidProviderId2283",
            },
            {
                bearerTokenSendingMethods: ["authorizationHeader"],
                openidProviderId: "openidProviderId2284",
            },
        ],
    },
    description: "apidescription5200",
    displayName: "apiname1463",
    path: "newapiPath",
    protocols: [
        "https",
        "http",
    ],
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    serviceUrl: "http://newechoapi.cloudapp.net/api",
    subscriptionKeyParameterNames: {
        header: "header4520",
        query: "query3037",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api = azure_native.apimanagement.Api("api",
    api_id="tempgroup",
    authentication_settings=azure_native.apimanagement.AuthenticationSettingsContractResponseArgs(
        openid_authentication_settings=[
            azure_native.apimanagement.OpenIdAuthenticationSettingsContractArgs(
                bearer_token_sending_methods=["authorizationHeader"],
                openid_provider_id="openidProviderId2283",
            ),
            azure_native.apimanagement.OpenIdAuthenticationSettingsContractArgs(
                bearer_token_sending_methods=["authorizationHeader"],
                openid_provider_id="openidProviderId2284",
            ),
        ],
    ),
    description="apidescription5200",
    display_name="apiname1463",
    path="newapiPath",
    protocols=[
        "https",
        "http",
    ],
    resource_group_name="rg1",
    service_name="apimService1",
    service_url="http://newechoapi.cloudapp.net/api",
    subscription_key_parameter_names=azure_native.apimanagement.SubscriptionKeyParameterNamesContractArgs(
        header="header4520",
        query="query3037",
    ))

```

```yaml
resources:
  api:
    type: azure-native:apimanagement:Api
    properties:
      apiId: tempgroup
      authenticationSettings:
        openidAuthenticationSettings:
          - bearerTokenSendingMethods:
              - authorizationHeader
            openidProviderId: openidProviderId2283
          - bearerTokenSendingMethods:
              - authorizationHeader
            openidProviderId: openidProviderId2284
      description: apidescription5200
      displayName: apiname1463
      path: newapiPath
      protocols:
        - https
        - http
      resourceGroupName: rg1
      serviceName: apimService1
      serviceUrl: http://newechoapi.cloudapp.net/api
      subscriptionKeyParameterNames:
        header: header4520
        query: query3037

```

{{% /example %}}
{{% example %}}
### ApiManagementCreateApiWithOpenIdConnect
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var api = new AzureNative.ApiManagement.Api("api", new()
    {
        ApiId = "tempgroup",
        AuthenticationSettings = new AzureNative.ApiManagement.Inputs.AuthenticationSettingsContractArgs
        {
            Openid = new AzureNative.ApiManagement.Inputs.OpenIdAuthenticationSettingsContractArgs
            {
                BearerTokenSendingMethods = new[]
                {
                    "authorizationHeader",
                },
                OpenidProviderId = "testopenid",
            },
        },
        Description = "This is a sample server Petstore server.  You can find out more about Swagger at [http://swagger.io](http://swagger.io) or on [irc.freenode.net, #swagger](http://swagger.io/irc/).  For this sample, you can use the api key `special-key` to test the authorization filters.",
        DisplayName = "Swagger Petstore",
        Path = "petstore",
        Protocols = new[]
        {
            "https",
        },
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        ServiceUrl = "http://petstore.swagger.io/v2",
        SubscriptionKeyParameterNames = new AzureNative.ApiManagement.Inputs.SubscriptionKeyParameterNamesContractArgs
        {
            Header = "Ocp-Apim-Subscription-Key",
            Query = "subscription-key",
        },
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
		_, err := apimanagement.NewApi(ctx, "api", &apimanagement.ApiArgs{
			ApiId: pulumi.String("tempgroup"),
			AuthenticationSettings: apimanagement.AuthenticationSettingsContractResponse{
				Openid: &apimanagement.OpenIdAuthenticationSettingsContractArgs{
					BearerTokenSendingMethods: pulumi.StringArray{
						pulumi.String("authorizationHeader"),
					},
					OpenidProviderId: pulumi.String("testopenid"),
				},
			},
			Description: pulumi.String("This is a sample server Petstore server.  You can find out more about Swagger at [http://swagger.io](http://swagger.io) or on [irc.freenode.net, #swagger](http://swagger.io/irc/).  For this sample, you can use the api key `special-key` to test the authorization filters."),
			DisplayName: pulumi.String("Swagger Petstore"),
			Path:        pulumi.String("petstore"),
			Protocols: pulumi.StringArray{
				pulumi.String("https"),
			},
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			ServiceUrl:        pulumi.String("http://petstore.swagger.io/v2"),
			SubscriptionKeyParameterNames: &apimanagement.SubscriptionKeyParameterNamesContractArgs{
				Header: pulumi.String("Ocp-Apim-Subscription-Key"),
				Query:  pulumi.String("subscription-key"),
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
import com.pulumi.azurenative.apimanagement.Api;
import com.pulumi.azurenative.apimanagement.ApiArgs;
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
        var api = new Api("api", ApiArgs.builder()        
            .apiId("tempgroup")
            .authenticationSettings(Map.of("openid", Map.ofEntries(
                Map.entry("bearerTokenSendingMethods", "authorizationHeader"),
                Map.entry("openidProviderId", "testopenid")
            )))
            .description("This is a sample server Petstore server.  You can find out more about Swagger at [http://swagger.io](http://swagger.io) or on [irc.freenode.net, #swagger](http://swagger.io/irc/).  For this sample, you can use the api key `special-key` to test the authorization filters.")
            .displayName("Swagger Petstore")
            .path("petstore")
            .protocols("https")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .serviceUrl("http://petstore.swagger.io/v2")
            .subscriptionKeyParameterNames(Map.ofEntries(
                Map.entry("header", "Ocp-Apim-Subscription-Key"),
                Map.entry("query", "subscription-key")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const api = new azure_native.apimanagement.Api("api", {
    apiId: "tempgroup",
    authenticationSettings: {
        openid: {
            bearerTokenSendingMethods: ["authorizationHeader"],
            openidProviderId: "testopenid",
        },
    },
    description: "This is a sample server Petstore server.  You can find out more about Swagger at [http://swagger.io](http://swagger.io) or on [irc.freenode.net, #swagger](http://swagger.io/irc/).  For this sample, you can use the api key `special-key` to test the authorization filters.",
    displayName: "Swagger Petstore",
    path: "petstore",
    protocols: ["https"],
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    serviceUrl: "http://petstore.swagger.io/v2",
    subscriptionKeyParameterNames: {
        header: "Ocp-Apim-Subscription-Key",
        query: "subscription-key",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api = azure_native.apimanagement.Api("api",
    api_id="tempgroup",
    authentication_settings=azure_native.apimanagement.AuthenticationSettingsContractResponseArgs(
        openid=azure_native.apimanagement.OpenIdAuthenticationSettingsContractArgs(
            bearer_token_sending_methods=["authorizationHeader"],
            openid_provider_id="testopenid",
        ),
    ),
    description="This is a sample server Petstore server.  You can find out more about Swagger at [http://swagger.io](http://swagger.io) or on [irc.freenode.net, #swagger](http://swagger.io/irc/).  For this sample, you can use the api key `special-key` to test the authorization filters.",
    display_name="Swagger Petstore",
    path="petstore",
    protocols=["https"],
    resource_group_name="rg1",
    service_name="apimService1",
    service_url="http://petstore.swagger.io/v2",
    subscription_key_parameter_names=azure_native.apimanagement.SubscriptionKeyParameterNamesContractArgs(
        header="Ocp-Apim-Subscription-Key",
        query="subscription-key",
    ))

```

```yaml
resources:
  api:
    type: azure-native:apimanagement:Api
    properties:
      apiId: tempgroup
      authenticationSettings:
        openid:
          bearerTokenSendingMethods:
            - authorizationHeader
          openidProviderId: testopenid
      description: 'This is a sample server Petstore server.  You can find out more about Swagger at [http://swagger.io](http://swagger.io) or on [irc.freenode.net, #swagger](http://swagger.io/irc/).  For this sample, you can use the api key `special-key` to test the authorization filters.'
      displayName: Swagger Petstore
      path: petstore
      protocols:
        - https
      resourceGroupName: rg1
      serviceName: apimService1
      serviceUrl: http://petstore.swagger.io/v2
      subscriptionKeyParameterNames:
        header: Ocp-Apim-Subscription-Key
        query: subscription-key

```

{{% /example %}}
{{% example %}}
### ApiManagementCreateGraphQLApi
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var api = new AzureNative.ApiManagement.Api("api", new()
    {
        ApiId = "tempgroup",
        ApiType = "graphql",
        Description = "apidescription5200",
        DisplayName = "apiname1463",
        Path = "graphql-api",
        Protocols = new[]
        {
            "http",
            "https",
        },
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        ServiceUrl = "https://api.spacex.land/graphql",
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
		_, err := apimanagement.NewApi(ctx, "api", &apimanagement.ApiArgs{
			ApiId:       pulumi.String("tempgroup"),
			ApiType:     pulumi.String("graphql"),
			Description: pulumi.String("apidescription5200"),
			DisplayName: pulumi.String("apiname1463"),
			Path:        pulumi.String("graphql-api"),
			Protocols: pulumi.StringArray{
				pulumi.String("http"),
				pulumi.String("https"),
			},
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			ServiceUrl:        pulumi.String("https://api.spacex.land/graphql"),
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
import com.pulumi.azurenative.apimanagement.Api;
import com.pulumi.azurenative.apimanagement.ApiArgs;
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
        var api = new Api("api", ApiArgs.builder()        
            .apiId("tempgroup")
            .apiType("graphql")
            .description("apidescription5200")
            .displayName("apiname1463")
            .path("graphql-api")
            .protocols(            
                "http",
                "https")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .serviceUrl("https://api.spacex.land/graphql")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const api = new azure_native.apimanagement.Api("api", {
    apiId: "tempgroup",
    apiType: "graphql",
    description: "apidescription5200",
    displayName: "apiname1463",
    path: "graphql-api",
    protocols: [
        "http",
        "https",
    ],
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    serviceUrl: "https://api.spacex.land/graphql",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api = azure_native.apimanagement.Api("api",
    api_id="tempgroup",
    api_type="graphql",
    description="apidescription5200",
    display_name="apiname1463",
    path="graphql-api",
    protocols=[
        "http",
        "https",
    ],
    resource_group_name="rg1",
    service_name="apimService1",
    service_url="https://api.spacex.land/graphql")

```

```yaml
resources:
  api:
    type: azure-native:apimanagement:Api
    properties:
      apiId: tempgroup
      apiType: graphql
      description: apidescription5200
      displayName: apiname1463
      path: graphql-api
      protocols:
        - http
        - https
      resourceGroupName: rg1
      serviceName: apimService1
      serviceUrl: https://api.spacex.land/graphql

```

{{% /example %}}
{{% example %}}
### ApiManagementCreateSoapPassThroughApiUsingWsdlImport
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var api = new AzureNative.ApiManagement.Api("api", new()
    {
        ApiId = "soapApi",
        Format = "wsdl-link",
        Path = "currency",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        SoapApiType = "soap",
        Value = "http://www.webservicex.net/CurrencyConvertor.asmx?WSDL",
        WsdlSelector = new AzureNative.ApiManagement.Inputs.ApiCreateOrUpdatePropertiesWsdlSelectorArgs
        {
            WsdlEndpointName = "CurrencyConvertorSoap",
            WsdlServiceName = "CurrencyConvertor",
        },
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
		_, err := apimanagement.NewApi(ctx, "api", &apimanagement.ApiArgs{
			ApiId:             pulumi.String("soapApi"),
			Format:            pulumi.String("wsdl-link"),
			Path:              pulumi.String("currency"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			SoapApiType:       pulumi.String("soap"),
			Value:             pulumi.String("http://www.webservicex.net/CurrencyConvertor.asmx?WSDL"),
			WsdlSelector: &apimanagement.ApiCreateOrUpdatePropertiesWsdlSelectorArgs{
				WsdlEndpointName: pulumi.String("CurrencyConvertorSoap"),
				WsdlServiceName:  pulumi.String("CurrencyConvertor"),
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
import com.pulumi.azurenative.apimanagement.Api;
import com.pulumi.azurenative.apimanagement.ApiArgs;
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
        var api = new Api("api", ApiArgs.builder()        
            .apiId("soapApi")
            .format("wsdl-link")
            .path("currency")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .soapApiType("soap")
            .value("http://www.webservicex.net/CurrencyConvertor.asmx?WSDL")
            .wsdlSelector(Map.ofEntries(
                Map.entry("wsdlEndpointName", "CurrencyConvertorSoap"),
                Map.entry("wsdlServiceName", "CurrencyConvertor")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const api = new azure_native.apimanagement.Api("api", {
    apiId: "soapApi",
    format: "wsdl-link",
    path: "currency",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    soapApiType: "soap",
    value: "http://www.webservicex.net/CurrencyConvertor.asmx?WSDL",
    wsdlSelector: {
        wsdlEndpointName: "CurrencyConvertorSoap",
        wsdlServiceName: "CurrencyConvertor",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api = azure_native.apimanagement.Api("api",
    api_id="soapApi",
    format="wsdl-link",
    path="currency",
    resource_group_name="rg1",
    service_name="apimService1",
    soap_api_type="soap",
    value="http://www.webservicex.net/CurrencyConvertor.asmx?WSDL",
    wsdl_selector=azure_native.apimanagement.ApiCreateOrUpdatePropertiesWsdlSelectorArgs(
        wsdl_endpoint_name="CurrencyConvertorSoap",
        wsdl_service_name="CurrencyConvertor",
    ))

```

```yaml
resources:
  api:
    type: azure-native:apimanagement:Api
    properties:
      apiId: soapApi
      format: wsdl-link
      path: currency
      resourceGroupName: rg1
      serviceName: apimService1
      soapApiType: soap
      value: http://www.webservicex.net/CurrencyConvertor.asmx?WSDL
      wsdlSelector:
        wsdlEndpointName: CurrencyConvertorSoap
        wsdlServiceName: CurrencyConvertor

```

{{% /example %}}
{{% example %}}
### ApiManagementCreateSoapToRestApiUsingWsdlImport
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var api = new AzureNative.ApiManagement.Api("api", new()
    {
        ApiId = "soapApi",
        Format = "wsdl-link",
        Path = "currency",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        Value = "http://www.webservicex.net/CurrencyConvertor.asmx?WSDL",
        WsdlSelector = new AzureNative.ApiManagement.Inputs.ApiCreateOrUpdatePropertiesWsdlSelectorArgs
        {
            WsdlEndpointName = "CurrencyConvertorSoap",
            WsdlServiceName = "CurrencyConvertor",
        },
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
		_, err := apimanagement.NewApi(ctx, "api", &apimanagement.ApiArgs{
			ApiId:             pulumi.String("soapApi"),
			Format:            pulumi.String("wsdl-link"),
			Path:              pulumi.String("currency"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			Value:             pulumi.String("http://www.webservicex.net/CurrencyConvertor.asmx?WSDL"),
			WsdlSelector: &apimanagement.ApiCreateOrUpdatePropertiesWsdlSelectorArgs{
				WsdlEndpointName: pulumi.String("CurrencyConvertorSoap"),
				WsdlServiceName:  pulumi.String("CurrencyConvertor"),
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
import com.pulumi.azurenative.apimanagement.Api;
import com.pulumi.azurenative.apimanagement.ApiArgs;
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
        var api = new Api("api", ApiArgs.builder()        
            .apiId("soapApi")
            .format("wsdl-link")
            .path("currency")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .value("http://www.webservicex.net/CurrencyConvertor.asmx?WSDL")
            .wsdlSelector(Map.ofEntries(
                Map.entry("wsdlEndpointName", "CurrencyConvertorSoap"),
                Map.entry("wsdlServiceName", "CurrencyConvertor")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const api = new azure_native.apimanagement.Api("api", {
    apiId: "soapApi",
    format: "wsdl-link",
    path: "currency",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    value: "http://www.webservicex.net/CurrencyConvertor.asmx?WSDL",
    wsdlSelector: {
        wsdlEndpointName: "CurrencyConvertorSoap",
        wsdlServiceName: "CurrencyConvertor",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api = azure_native.apimanagement.Api("api",
    api_id="soapApi",
    format="wsdl-link",
    path="currency",
    resource_group_name="rg1",
    service_name="apimService1",
    value="http://www.webservicex.net/CurrencyConvertor.asmx?WSDL",
    wsdl_selector=azure_native.apimanagement.ApiCreateOrUpdatePropertiesWsdlSelectorArgs(
        wsdl_endpoint_name="CurrencyConvertorSoap",
        wsdl_service_name="CurrencyConvertor",
    ))

```

```yaml
resources:
  api:
    type: azure-native:apimanagement:Api
    properties:
      apiId: soapApi
      format: wsdl-link
      path: currency
      resourceGroupName: rg1
      serviceName: apimService1
      value: http://www.webservicex.net/CurrencyConvertor.asmx?WSDL
      wsdlSelector:
        wsdlEndpointName: CurrencyConvertorSoap
        wsdlServiceName: CurrencyConvertor

```

{{% /example %}}
{{% example %}}
### ApiManagementCreateWebSocketApi
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var api = new AzureNative.ApiManagement.Api("api", new()
    {
        ApiId = "tempgroup",
        ApiType = "websocket",
        Description = "apidescription5200",
        DisplayName = "apiname1463",
        Path = "newapiPath",
        Protocols = new[]
        {
            "wss",
            "ws",
        },
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        ServiceUrl = "wss://echo.websocket.org",
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
		_, err := apimanagement.NewApi(ctx, "api", &apimanagement.ApiArgs{
			ApiId:       pulumi.String("tempgroup"),
			ApiType:     pulumi.String("websocket"),
			Description: pulumi.String("apidescription5200"),
			DisplayName: pulumi.String("apiname1463"),
			Path:        pulumi.String("newapiPath"),
			Protocols: pulumi.StringArray{
				pulumi.String("wss"),
				pulumi.String("ws"),
			},
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			ServiceUrl:        pulumi.String("wss://echo.websocket.org"),
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
import com.pulumi.azurenative.apimanagement.Api;
import com.pulumi.azurenative.apimanagement.ApiArgs;
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
        var api = new Api("api", ApiArgs.builder()        
            .apiId("tempgroup")
            .apiType("websocket")
            .description("apidescription5200")
            .displayName("apiname1463")
            .path("newapiPath")
            .protocols(            
                "wss",
                "ws")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .serviceUrl("wss://echo.websocket.org")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const api = new azure_native.apimanagement.Api("api", {
    apiId: "tempgroup",
    apiType: "websocket",
    description: "apidescription5200",
    displayName: "apiname1463",
    path: "newapiPath",
    protocols: [
        "wss",
        "ws",
    ],
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    serviceUrl: "wss://echo.websocket.org",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api = azure_native.apimanagement.Api("api",
    api_id="tempgroup",
    api_type="websocket",
    description="apidescription5200",
    display_name="apiname1463",
    path="newapiPath",
    protocols=[
        "wss",
        "ws",
    ],
    resource_group_name="rg1",
    service_name="apimService1",
    service_url="wss://echo.websocket.org")

```

```yaml
resources:
  api:
    type: azure-native:apimanagement:Api
    properties:
      apiId: tempgroup
      apiType: websocket
      description: apidescription5200
      displayName: apiname1463
      path: newapiPath
      protocols:
        - wss
        - ws
      resourceGroupName: rg1
      serviceName: apimService1
      serviceUrl: wss://echo.websocket.org

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:Api apiid9419 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apis/apiid9419 
```
