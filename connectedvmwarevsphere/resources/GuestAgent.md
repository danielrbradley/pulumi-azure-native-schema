Defines the GuestAgent.
API Version: 2022-07-15-preview.
Previous API Version: 2020-10-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateGuestAgent
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var guestAgent = new AzureNative.ConnectedVMwarevSphere.GuestAgent("guestAgent", new()
    {
        Credentials = new AzureNative.ConnectedVMwarevSphere.Inputs.GuestCredentialArgs
        {
            Password = "<password>",
            Username = "tempuser",
        },
        HttpProxyConfig = new AzureNative.ConnectedVMwarevSphere.Inputs.HttpProxyConfigurationArgs
        {
            HttpsProxy = "http://192.1.2.3:8080",
        },
        Name = "default",
        ProvisioningAction = "install",
        ResourceGroupName = "testrg",
        VirtualMachineName = "ContosoVm",
    });

});


```

```go
package main

import (
	connectedvmwarevsphere "github.com/pulumi/pulumi-azure-native-sdk/connectedvmwarevsphere"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := connectedvmwarevsphere.NewGuestAgent(ctx, "guestAgent", &connectedvmwarevsphere.GuestAgentArgs{
			Credentials: &connectedvmwarevsphere.GuestCredentialArgs{
				Password: pulumi.String("<password>"),
				Username: pulumi.String("tempuser"),
			},
			HttpProxyConfig: &connectedvmwarevsphere.HttpProxyConfigurationArgs{
				HttpsProxy: pulumi.String("http://192.1.2.3:8080"),
			},
			Name:               pulumi.String("default"),
			ProvisioningAction: pulumi.String("install"),
			ResourceGroupName:  pulumi.String("testrg"),
			VirtualMachineName: pulumi.String("ContosoVm"),
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
import com.pulumi.azurenative.connectedvmwarevsphere.GuestAgent;
import com.pulumi.azurenative.connectedvmwarevsphere.GuestAgentArgs;
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
        var guestAgent = new GuestAgent("guestAgent", GuestAgentArgs.builder()        
            .credentials(Map.ofEntries(
                Map.entry("password", "<password>"),
                Map.entry("username", "tempuser")
            ))
            .httpProxyConfig(Map.of("httpsProxy", "http://192.1.2.3:8080"))
            .name("default")
            .provisioningAction("install")
            .resourceGroupName("testrg")
            .virtualMachineName("ContosoVm")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const guestAgent = new azure_native.connectedvmwarevsphere.GuestAgent("guestAgent", {
    credentials: {
        password: "<password>",
        username: "tempuser",
    },
    httpProxyConfig: {
        httpsProxy: "http://192.1.2.3:8080",
    },
    name: "default",
    provisioningAction: "install",
    resourceGroupName: "testrg",
    virtualMachineName: "ContosoVm",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

guest_agent = azure_native.connectedvmwarevsphere.GuestAgent("guestAgent",
    credentials=azure_native.connectedvmwarevsphere.GuestCredentialArgs(
        password="<password>",
        username="tempuser",
    ),
    http_proxy_config=azure_native.connectedvmwarevsphere.HttpProxyConfigurationArgs(
        https_proxy="http://192.1.2.3:8080",
    ),
    name="default",
    provisioning_action="install",
    resource_group_name="testrg",
    virtual_machine_name="ContosoVm")

```

```yaml
resources:
  guestAgent:
    type: azure-native:connectedvmwarevsphere:GuestAgent
    properties:
      credentials:
        password: <password>
        username: tempuser
      httpProxyConfig:
        httpsProxy: http://192.1.2.3:8080
      name: default
      provisioningAction: install
      resourceGroupName: testrg
      virtualMachineName: ContosoVm

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:connectedvmwarevsphere:GuestAgent default /subscriptions/fd3c3665-1729-4b7b-9a38-238e83b0f98b/resourceGroups/testrg/providers/Microsoft.ConnectedVMwarevSphere/VitualMachines/ContosoVm/guestAgents/default 
```
