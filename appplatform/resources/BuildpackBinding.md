Buildpack Binding Resource object
API Version: 2022-12-01.
Previous API Version: 2022-01-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### BuildpackBinding_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var buildpackBinding = new AzureNative.AppPlatform.BuildpackBinding("buildpackBinding", new()
    {
        BuildServiceName = "default",
        BuilderName = "default",
        BuildpackBindingName = "myBuildpackBinding",
        Properties = new AzureNative.AppPlatform.Inputs.BuildpackBindingPropertiesArgs
        {
            BindingType = "ApplicationInsights",
            LaunchProperties = new AzureNative.AppPlatform.Inputs.BuildpackBindingLaunchPropertiesArgs
            {
                Properties = 
                {
                    { "abc", "def" },
                    { "any-string", "any-string" },
                    { "sampling-rate", "12.0" },
                },
                Secrets = 
                {
                    { "connection-string", "XXXXXXXXXXXXXXXXX=XXXXXXXXXXXXX-XXXXXXXXXXXXXXXXXXX;XXXXXXXXXXXXXXXXX=XXXXXXXXXXXXXXXXXXX" },
                },
            },
        },
        ResourceGroupName = "myResourceGroup",
        ServiceName = "myservice",
    });

});


```

```go
package main

import (
	appplatform "github.com/pulumi/pulumi-azure-native-sdk/appplatform"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := appplatform.NewBuildpackBinding(ctx, "buildpackBinding", &appplatform.BuildpackBindingArgs{
			BuildServiceName:     pulumi.String("default"),
			BuilderName:          pulumi.String("default"),
			BuildpackBindingName: pulumi.String("myBuildpackBinding"),
			Properties: appplatform.BuildpackBindingPropertiesResponse{
				BindingType: pulumi.String("ApplicationInsights"),
				LaunchProperties: &appplatform.BuildpackBindingLaunchPropertiesArgs{
					Properties: pulumi.StringMap{
						"abc":           pulumi.String("def"),
						"any-string":    pulumi.String("any-string"),
						"sampling-rate": pulumi.String("12.0"),
					},
					Secrets: pulumi.StringMap{
						"connection-string": pulumi.String("XXXXXXXXXXXXXXXXX=XXXXXXXXXXXXX-XXXXXXXXXXXXXXXXXXX;XXXXXXXXXXXXXXXXX=XXXXXXXXXXXXXXXXXXX"),
					},
				},
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
			ServiceName:       pulumi.String("myservice"),
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
import com.pulumi.azurenative.appplatform.BuildpackBinding;
import com.pulumi.azurenative.appplatform.BuildpackBindingArgs;
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
        var buildpackBinding = new BuildpackBinding("buildpackBinding", BuildpackBindingArgs.builder()        
            .buildServiceName("default")
            .builderName("default")
            .buildpackBindingName("myBuildpackBinding")
            .properties(Map.ofEntries(
                Map.entry("bindingType", "ApplicationInsights"),
                Map.entry("launchProperties", Map.ofEntries(
                    Map.entry("properties", Map.ofEntries(
                        Map.entry("abc", "def"),
                        Map.entry("any-string", "any-string"),
                        Map.entry("sampling-rate", "12.0")
                    )),
                    Map.entry("secrets", Map.of("connection-string", "XXXXXXXXXXXXXXXXX=XXXXXXXXXXXXX-XXXXXXXXXXXXXXXXXXX;XXXXXXXXXXXXXXXXX=XXXXXXXXXXXXXXXXXXX"))
                ))
            ))
            .resourceGroupName("myResourceGroup")
            .serviceName("myservice")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const buildpackBinding = new azure_native.appplatform.BuildpackBinding("buildpackBinding", {
    buildServiceName: "default",
    builderName: "default",
    buildpackBindingName: "myBuildpackBinding",
    properties: {
        bindingType: "ApplicationInsights",
        launchProperties: {
            properties: {
                abc: "def",
                "any-string": "any-string",
                "sampling-rate": "12.0",
            },
            secrets: {
                "connection-string": "XXXXXXXXXXXXXXXXX=XXXXXXXXXXXXX-XXXXXXXXXXXXXXXXXXX;XXXXXXXXXXXXXXXXX=XXXXXXXXXXXXXXXXXXX",
            },
        },
    },
    resourceGroupName: "myResourceGroup",
    serviceName: "myservice",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

buildpack_binding = azure_native.appplatform.BuildpackBinding("buildpackBinding",
    build_service_name="default",
    builder_name="default",
    buildpack_binding_name="myBuildpackBinding",
    properties=azure_native.appplatform.BuildpackBindingPropertiesResponseArgs(
        binding_type="ApplicationInsights",
        launch_properties=azure_native.appplatform.BuildpackBindingLaunchPropertiesArgs(
            properties={
                "abc": "def",
                "any-string": "any-string",
                "sampling-rate": "12.0",
            },
            secrets={
                "connection-string": "XXXXXXXXXXXXXXXXX=XXXXXXXXXXXXX-XXXXXXXXXXXXXXXXXXX;XXXXXXXXXXXXXXXXX=XXXXXXXXXXXXXXXXXXX",
            },
        ),
    ),
    resource_group_name="myResourceGroup",
    service_name="myservice")

```

```yaml
resources:
  buildpackBinding:
    type: azure-native:appplatform:BuildpackBinding
    properties:
      buildServiceName: default
      builderName: default
      buildpackBindingName: myBuildpackBinding
      properties:
        bindingType: ApplicationInsights
        launchProperties:
          properties:
            abc: def
            any-string: any-string
            sampling-rate: '12.0'
          secrets:
            connection-string: XXXXXXXXXXXXXXXXX=XXXXXXXXXXXXX-XXXXXXXXXXXXXXXXXXX;XXXXXXXXXXXXXXXXX=XXXXXXXXXXXXXXXXXXX
      resourceGroupName: myResourceGroup
      serviceName: myservice

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:appplatform:BuildpackBinding myBuildpackBinding /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.AppPlatform/Spring/myservice/buildServices/default/builders/default/buildpackBindings/myBuildpackBinding 
```
