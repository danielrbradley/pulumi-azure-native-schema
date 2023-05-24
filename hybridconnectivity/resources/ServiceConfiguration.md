The service configuration details associated with the target resource.
API Version: 2023-03-15.

{{% examples %}}
## Example Usage
{{% example %}}
### ServiceConfigurationsPutSSH
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var serviceConfiguration = new AzureNative.HybridConnectivity.ServiceConfiguration("serviceConfiguration", new()
    {
        EndpointName = "default",
        Port = 22,
        ResourceUri = "subscriptions/f5bcc1d9-23af-4ae9-aca1-041d0f593a63/resourceGroups/hybridRG/providers/Microsoft.HybridCompute/machines/testMachine/providers/Microsoft.HybridConnectivity/endpoints/default",
        ServiceConfigurationName = "SSH",
        ServiceName = "SSH",
    });

});


```

```go
package main

import (
	hybridconnectivity "github.com/pulumi/pulumi-azure-native-sdk/hybridconnectivity"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := hybridconnectivity.NewServiceConfiguration(ctx, "serviceConfiguration", &hybridconnectivity.ServiceConfigurationArgs{
			EndpointName:             pulumi.String("default"),
			Port:                     pulumi.Float64(22),
			ResourceUri:              pulumi.String("subscriptions/f5bcc1d9-23af-4ae9-aca1-041d0f593a63/resourceGroups/hybridRG/providers/Microsoft.HybridCompute/machines/testMachine/providers/Microsoft.HybridConnectivity/endpoints/default"),
			ServiceConfigurationName: pulumi.String("SSH"),
			ServiceName:              pulumi.String("SSH"),
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
import com.pulumi.azurenative.hybridconnectivity.ServiceConfiguration;
import com.pulumi.azurenative.hybridconnectivity.ServiceConfigurationArgs;
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
        var serviceConfiguration = new ServiceConfiguration("serviceConfiguration", ServiceConfigurationArgs.builder()        
            .endpointName("default")
            .port(22)
            .resourceUri("subscriptions/f5bcc1d9-23af-4ae9-aca1-041d0f593a63/resourceGroups/hybridRG/providers/Microsoft.HybridCompute/machines/testMachine/providers/Microsoft.HybridConnectivity/endpoints/default")
            .serviceConfigurationName("SSH")
            .serviceName("SSH")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const serviceConfiguration = new azure_native.hybridconnectivity.ServiceConfiguration("serviceConfiguration", {
    endpointName: "default",
    port: 22,
    resourceUri: "subscriptions/f5bcc1d9-23af-4ae9-aca1-041d0f593a63/resourceGroups/hybridRG/providers/Microsoft.HybridCompute/machines/testMachine/providers/Microsoft.HybridConnectivity/endpoints/default",
    serviceConfigurationName: "SSH",
    serviceName: "SSH",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service_configuration = azure_native.hybridconnectivity.ServiceConfiguration("serviceConfiguration",
    endpoint_name="default",
    port=22,
    resource_uri="subscriptions/f5bcc1d9-23af-4ae9-aca1-041d0f593a63/resourceGroups/hybridRG/providers/Microsoft.HybridCompute/machines/testMachine/providers/Microsoft.HybridConnectivity/endpoints/default",
    service_configuration_name="SSH",
    service_name="SSH")

```

```yaml
resources:
  serviceConfiguration:
    type: azure-native:hybridconnectivity:ServiceConfiguration
    properties:
      endpointName: default
      port: 22
      resourceUri: subscriptions/f5bcc1d9-23af-4ae9-aca1-041d0f593a63/resourceGroups/hybridRG/providers/Microsoft.HybridCompute/machines/testMachine/providers/Microsoft.HybridConnectivity/endpoints/default
      serviceConfigurationName: SSH
      serviceName: SSH

```

{{% /example %}}
{{% example %}}
### ServiceConfigurationsPutWAC
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var serviceConfiguration = new AzureNative.HybridConnectivity.ServiceConfiguration("serviceConfiguration", new()
    {
        EndpointName = "default",
        Port = 6516,
        ResourceUri = "subscriptions/f5bcc1d9-23af-4ae9-aca1-041d0f593a63/resourceGroups/hybridRG/providers/Microsoft.HybridCompute/machines/testMachine/providers/Microsoft.HybridConnectivity/endpoints/default",
        ServiceConfigurationName = "WAC",
        ServiceName = "WAC",
    });

});


```

```go
package main

import (
	hybridconnectivity "github.com/pulumi/pulumi-azure-native-sdk/hybridconnectivity"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := hybridconnectivity.NewServiceConfiguration(ctx, "serviceConfiguration", &hybridconnectivity.ServiceConfigurationArgs{
			EndpointName:             pulumi.String("default"),
			Port:                     pulumi.Float64(6516),
			ResourceUri:              pulumi.String("subscriptions/f5bcc1d9-23af-4ae9-aca1-041d0f593a63/resourceGroups/hybridRG/providers/Microsoft.HybridCompute/machines/testMachine/providers/Microsoft.HybridConnectivity/endpoints/default"),
			ServiceConfigurationName: pulumi.String("WAC"),
			ServiceName:              pulumi.String("WAC"),
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
import com.pulumi.azurenative.hybridconnectivity.ServiceConfiguration;
import com.pulumi.azurenative.hybridconnectivity.ServiceConfigurationArgs;
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
        var serviceConfiguration = new ServiceConfiguration("serviceConfiguration", ServiceConfigurationArgs.builder()        
            .endpointName("default")
            .port(6516)
            .resourceUri("subscriptions/f5bcc1d9-23af-4ae9-aca1-041d0f593a63/resourceGroups/hybridRG/providers/Microsoft.HybridCompute/machines/testMachine/providers/Microsoft.HybridConnectivity/endpoints/default")
            .serviceConfigurationName("WAC")
            .serviceName("WAC")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const serviceConfiguration = new azure_native.hybridconnectivity.ServiceConfiguration("serviceConfiguration", {
    endpointName: "default",
    port: 6516,
    resourceUri: "subscriptions/f5bcc1d9-23af-4ae9-aca1-041d0f593a63/resourceGroups/hybridRG/providers/Microsoft.HybridCompute/machines/testMachine/providers/Microsoft.HybridConnectivity/endpoints/default",
    serviceConfigurationName: "WAC",
    serviceName: "WAC",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service_configuration = azure_native.hybridconnectivity.ServiceConfiguration("serviceConfiguration",
    endpoint_name="default",
    port=6516,
    resource_uri="subscriptions/f5bcc1d9-23af-4ae9-aca1-041d0f593a63/resourceGroups/hybridRG/providers/Microsoft.HybridCompute/machines/testMachine/providers/Microsoft.HybridConnectivity/endpoints/default",
    service_configuration_name="WAC",
    service_name="WAC")

```

```yaml
resources:
  serviceConfiguration:
    type: azure-native:hybridconnectivity:ServiceConfiguration
    properties:
      endpointName: default
      port: 6516
      resourceUri: subscriptions/f5bcc1d9-23af-4ae9-aca1-041d0f593a63/resourceGroups/hybridRG/providers/Microsoft.HybridCompute/machines/testMachine/providers/Microsoft.HybridConnectivity/endpoints/default
      serviceConfigurationName: WAC
      serviceName: WAC

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:hybridconnectivity:ServiceConfiguration myresource1 /subscriptions/f5bcc1d9-23af-4ae9-aca1-041d0f593a63/resourceGroups/hybridRG/providers/Microsoft.HybridCompute/machines/testMachine/providers/Microsoft.HybridConnectivity/endpoints/default/serviceconfigurations/WAC 
```
