OpenId Connect Provider details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateOpenIdConnectProvider
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var openIdConnectProvider = new AzureNative.ApiManagement.OpenIdConnectProvider("openIdConnectProvider", new()
    {
        ClientId = "oidprovidertemplate3",
        ClientSecret = "x",
        DisplayName = "templateoidprovider3",
        MetadataEndpoint = "https://oidprovider-template3.net",
        Opid = "templateOpenIdConnect3",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
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
		_, err := apimanagement.NewOpenIdConnectProvider(ctx, "openIdConnectProvider", &apimanagement.OpenIdConnectProviderArgs{
			ClientId:              pulumi.String("oidprovidertemplate3"),
			ClientSecret:          pulumi.String("x"),
			DisplayName:           pulumi.String("templateoidprovider3"),
			MetadataEndpoint:      pulumi.String("https://oidprovider-template3.net"),
			Opid:                  pulumi.String("templateOpenIdConnect3"),
			ResourceGroupName:     pulumi.String("rg1"),
			ServiceName:           pulumi.String("apimService1"),
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
import com.pulumi.azurenative.apimanagement.OpenIdConnectProvider;
import com.pulumi.azurenative.apimanagement.OpenIdConnectProviderArgs;
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
        var openIdConnectProvider = new OpenIdConnectProvider("openIdConnectProvider", OpenIdConnectProviderArgs.builder()        
            .clientId("oidprovidertemplate3")
            .clientSecret("x")
            .displayName("templateoidprovider3")
            .metadataEndpoint("https://oidprovider-template3.net")
            .opid("templateOpenIdConnect3")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .useInApiDocumentation(true)
            .useInTestConsole(false)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const openIdConnectProvider = new azure_native.apimanagement.OpenIdConnectProvider("openIdConnectProvider", {
    clientId: "oidprovidertemplate3",
    clientSecret: "x",
    displayName: "templateoidprovider3",
    metadataEndpoint: "https://oidprovider-template3.net",
    opid: "templateOpenIdConnect3",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    useInApiDocumentation: true,
    useInTestConsole: false,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

open_id_connect_provider = azure_native.apimanagement.OpenIdConnectProvider("openIdConnectProvider",
    client_id="oidprovidertemplate3",
    client_secret="x",
    display_name="templateoidprovider3",
    metadata_endpoint="https://oidprovider-template3.net",
    opid="templateOpenIdConnect3",
    resource_group_name="rg1",
    service_name="apimService1",
    use_in_api_documentation=True,
    use_in_test_console=False)

```

```yaml
resources:
  openIdConnectProvider:
    type: azure-native:apimanagement:OpenIdConnectProvider
    properties:
      clientId: oidprovidertemplate3
      clientSecret: x
      displayName: templateoidprovider3
      metadataEndpoint: https://oidprovider-template3.net
      opid: templateOpenIdConnect3
      resourceGroupName: rg1
      serviceName: apimService1
      useInApiDocumentation: true
      useInTestConsole: false

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:OpenIdConnectProvider templateOpenIdConnect3 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/openidConnectProviders/templateOpenIdConnect3 
```
