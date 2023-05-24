Service Registry resource
API Version: 2022-12-01.
Previous API Version: 2022-01-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ServiceRegistries_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var serviceRegistry = new AzureNative.AppPlatform.ServiceRegistry("serviceRegistry", new()
    {
        ResourceGroupName = "myResourceGroup",
        ServiceName = "myservice",
        ServiceRegistryName = "default",
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
		_, err := appplatform.NewServiceRegistry(ctx, "serviceRegistry", &appplatform.ServiceRegistryArgs{
			ResourceGroupName:   pulumi.String("myResourceGroup"),
			ServiceName:         pulumi.String("myservice"),
			ServiceRegistryName: pulumi.String("default"),
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
import com.pulumi.azurenative.appplatform.ServiceRegistry;
import com.pulumi.azurenative.appplatform.ServiceRegistryArgs;
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
        var serviceRegistry = new ServiceRegistry("serviceRegistry", ServiceRegistryArgs.builder()        
            .resourceGroupName("myResourceGroup")
            .serviceName("myservice")
            .serviceRegistryName("default")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const serviceRegistry = new azure_native.appplatform.ServiceRegistry("serviceRegistry", {
    resourceGroupName: "myResourceGroup",
    serviceName: "myservice",
    serviceRegistryName: "default",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service_registry = azure_native.appplatform.ServiceRegistry("serviceRegistry",
    resource_group_name="myResourceGroup",
    service_name="myservice",
    service_registry_name="default")

```

```yaml
resources:
  serviceRegistry:
    type: azure-native:appplatform:ServiceRegistry
    properties:
      resourceGroupName: myResourceGroup
      serviceName: myservice
      serviceRegistryName: default

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:appplatform:ServiceRegistry default /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.AppPlatform/Spring/myservice/serviceRegistries/default 
```
