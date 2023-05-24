API Version Set Contract details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateApiVersionSet
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var apiVersionSet = new AzureNative.ApiManagement.ApiVersionSet("apiVersionSet", new()
    {
        Description = "Version configuration",
        DisplayName = "api set 1",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        VersionSetId = "api1",
        VersioningScheme = "Segment",
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
		_, err := apimanagement.NewApiVersionSet(ctx, "apiVersionSet", &apimanagement.ApiVersionSetArgs{
			Description:       pulumi.String("Version configuration"),
			DisplayName:       pulumi.String("api set 1"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			VersionSetId:      pulumi.String("api1"),
			VersioningScheme:  pulumi.String("Segment"),
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
import com.pulumi.azurenative.apimanagement.ApiVersionSet;
import com.pulumi.azurenative.apimanagement.ApiVersionSetArgs;
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
        var apiVersionSet = new ApiVersionSet("apiVersionSet", ApiVersionSetArgs.builder()        
            .description("Version configuration")
            .displayName("api set 1")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .versionSetId("api1")
            .versioningScheme("Segment")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const apiVersionSet = new azure_native.apimanagement.ApiVersionSet("apiVersionSet", {
    description: "Version configuration",
    displayName: "api set 1",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    versionSetId: "api1",
    versioningScheme: "Segment",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api_version_set = azure_native.apimanagement.ApiVersionSet("apiVersionSet",
    description="Version configuration",
    display_name="api set 1",
    resource_group_name="rg1",
    service_name="apimService1",
    version_set_id="api1",
    versioning_scheme="Segment")

```

```yaml
resources:
  apiVersionSet:
    type: azure-native:apimanagement:ApiVersionSet
    properties:
      description: Version configuration
      displayName: api set 1
      resourceGroupName: rg1
      serviceName: apimService1
      versionSetId: api1
      versioningScheme: Segment

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:ApiVersionSet api1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apiVersionSets/api1 
```
