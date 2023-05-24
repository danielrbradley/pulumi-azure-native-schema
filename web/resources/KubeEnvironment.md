A Kubernetes cluster specialized for web workloads by Azure App Service
API Version: 2022-09-01.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create kube environments
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var kubeEnvironment = new AzureNative.Web.KubeEnvironment("kubeEnvironment", new()
    {
        Location = "East US",
        Name = "testkubeenv",
        ResourceGroupName = "examplerg",
        StaticIp = "1.2.3.4",
    });

});


```

```go
package main

import (
	web "github.com/pulumi/pulumi-azure-native-sdk/web"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := web.NewKubeEnvironment(ctx, "kubeEnvironment", &web.KubeEnvironmentArgs{
			Location:          pulumi.String("East US"),
			Name:              pulumi.String("testkubeenv"),
			ResourceGroupName: pulumi.String("examplerg"),
			StaticIp:          pulumi.String("1.2.3.4"),
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
import com.pulumi.azurenative.web.KubeEnvironment;
import com.pulumi.azurenative.web.KubeEnvironmentArgs;
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
        var kubeEnvironment = new KubeEnvironment("kubeEnvironment", KubeEnvironmentArgs.builder()        
            .location("East US")
            .name("testkubeenv")
            .resourceGroupName("examplerg")
            .staticIp("1.2.3.4")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const kubeEnvironment = new azure_native.web.KubeEnvironment("kubeEnvironment", {
    location: "East US",
    name: "testkubeenv",
    resourceGroupName: "examplerg",
    staticIp: "1.2.3.4",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

kube_environment = azure_native.web.KubeEnvironment("kubeEnvironment",
    location="East US",
    name="testkubeenv",
    resource_group_name="examplerg",
    static_ip="1.2.3.4")

```

```yaml
resources:
  kubeEnvironment:
    type: azure-native:web:KubeEnvironment
    properties:
      location: East US
      name: testkubeenv
      resourceGroupName: examplerg
      staticIp: 1.2.3.4

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:web:KubeEnvironment testkubeenv /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/examplerg/providers/Microsoft.Web/kubeEnvironments/testkubeenv 
```
