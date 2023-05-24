
API Version: 2022-12-12-preview.
Previous API Version: 2022-12-12-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update virtual machine console
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var console = new AzureNative.NetworkCloud.Console("console", new()
    {
        ConsoleName = "default",
        Enabled = "True",
        Expiration = "2022-06-01T01:27:03.008Z",
        ExtendedLocation = new AzureNative.NetworkCloud.Inputs.ExtendedLocationArgs
        {
            Name = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterManagerExtendedLocationName",
            Type = "CustomLocation",
        },
        Location = "location",
        ResourceGroupName = "resourceGroupName",
        SshPublicKey = new AzureNative.NetworkCloud.Inputs.SshPublicKeyArgs
        {
            KeyData = "ssh-rsa AAtsE3njSONzDYRIZv/WLjVuMfrUSByHp+jfaaOLHTIIB4fJvo6dQUZxE20w2iDHV3tEkmnTo84eba97VMueQD6OzJPEyWZMRpz8UYWOd0IXeRqiFu1lawNblZhwNT/ojNZfpB3af/YDzwQCZgTcTRyNNhL4o/blKUmug0daSsSXISTRnIDpcf5qytjs1Xo+yYyJMvzLL59mhAyb3p/cD+Y3/s3WhAx+l0XOKpzXnblrv9d3q4c2tWmm/SyFqthaqd0= admin@vm",
        },
        Tags = 
        {
            { "key1", "myvalue1" },
            { "key2", "myvalue2" },
        },
        VirtualMachineName = "virtualMachineName",
    });

});


```

```go
package main

import (
	networkcloud "github.com/pulumi/pulumi-azure-native-sdk/networkcloud"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := networkcloud.NewConsole(ctx, "console", &networkcloud.ConsoleArgs{
			ConsoleName: pulumi.String("default"),
			Enabled:     pulumi.String("True"),
			Expiration:  pulumi.String("2022-06-01T01:27:03.008Z"),
			ExtendedLocation: &networkcloud.ExtendedLocationArgs{
				Name: pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterManagerExtendedLocationName"),
				Type: pulumi.String("CustomLocation"),
			},
			Location:          pulumi.String("location"),
			ResourceGroupName: pulumi.String("resourceGroupName"),
			SshPublicKey: &networkcloud.SshPublicKeyArgs{
				KeyData: pulumi.String("ssh-rsa AAtsE3njSONzDYRIZv/WLjVuMfrUSByHp+jfaaOLHTIIB4fJvo6dQUZxE20w2iDHV3tEkmnTo84eba97VMueQD6OzJPEyWZMRpz8UYWOd0IXeRqiFu1lawNblZhwNT/ojNZfpB3af/YDzwQCZgTcTRyNNhL4o/blKUmug0daSsSXISTRnIDpcf5qytjs1Xo+yYyJMvzLL59mhAyb3p/cD+Y3/s3WhAx+l0XOKpzXnblrv9d3q4c2tWmm/SyFqthaqd0= admin@vm"),
			},
			Tags: pulumi.StringMap{
				"key1": pulumi.String("myvalue1"),
				"key2": pulumi.String("myvalue2"),
			},
			VirtualMachineName: pulumi.String("virtualMachineName"),
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
import com.pulumi.azurenative.networkcloud.Console;
import com.pulumi.azurenative.networkcloud.ConsoleArgs;
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
        var console = new Console("console", ConsoleArgs.builder()        
            .consoleName("default")
            .enabled("True")
            .expiration("2022-06-01T01:27:03.008Z")
            .extendedLocation(Map.ofEntries(
                Map.entry("name", "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterManagerExtendedLocationName"),
                Map.entry("type", "CustomLocation")
            ))
            .location("location")
            .resourceGroupName("resourceGroupName")
            .sshPublicKey(Map.of("keyData", "ssh-rsa AAtsE3njSONzDYRIZv/WLjVuMfrUSByHp+jfaaOLHTIIB4fJvo6dQUZxE20w2iDHV3tEkmnTo84eba97VMueQD6OzJPEyWZMRpz8UYWOd0IXeRqiFu1lawNblZhwNT/ojNZfpB3af/YDzwQCZgTcTRyNNhL4o/blKUmug0daSsSXISTRnIDpcf5qytjs1Xo+yYyJMvzLL59mhAyb3p/cD+Y3/s3WhAx+l0XOKpzXnblrv9d3q4c2tWmm/SyFqthaqd0= admin@vm"))
            .tags(Map.ofEntries(
                Map.entry("key1", "myvalue1"),
                Map.entry("key2", "myvalue2")
            ))
            .virtualMachineName("virtualMachineName")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const console = new azure_native.networkcloud.Console("console", {
    consoleName: "default",
    enabled: "True",
    expiration: "2022-06-01T01:27:03.008Z",
    extendedLocation: {
        name: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterManagerExtendedLocationName",
        type: "CustomLocation",
    },
    location: "location",
    resourceGroupName: "resourceGroupName",
    sshPublicKey: {
        keyData: "ssh-rsa AAtsE3njSONzDYRIZv/WLjVuMfrUSByHp+jfaaOLHTIIB4fJvo6dQUZxE20w2iDHV3tEkmnTo84eba97VMueQD6OzJPEyWZMRpz8UYWOd0IXeRqiFu1lawNblZhwNT/ojNZfpB3af/YDzwQCZgTcTRyNNhL4o/blKUmug0daSsSXISTRnIDpcf5qytjs1Xo+yYyJMvzLL59mhAyb3p/cD+Y3/s3WhAx+l0XOKpzXnblrv9d3q4c2tWmm/SyFqthaqd0= admin@vm",
    },
    tags: {
        key1: "myvalue1",
        key2: "myvalue2",
    },
    virtualMachineName: "virtualMachineName",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

console = azure_native.networkcloud.Console("console",
    console_name="default",
    enabled="True",
    expiration="2022-06-01T01:27:03.008Z",
    extended_location=azure_native.networkcloud.ExtendedLocationArgs(
        name="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterManagerExtendedLocationName",
        type="CustomLocation",
    ),
    location="location",
    resource_group_name="resourceGroupName",
    ssh_public_key=azure_native.networkcloud.SshPublicKeyArgs(
        key_data="ssh-rsa AAtsE3njSONzDYRIZv/WLjVuMfrUSByHp+jfaaOLHTIIB4fJvo6dQUZxE20w2iDHV3tEkmnTo84eba97VMueQD6OzJPEyWZMRpz8UYWOd0IXeRqiFu1lawNblZhwNT/ojNZfpB3af/YDzwQCZgTcTRyNNhL4o/blKUmug0daSsSXISTRnIDpcf5qytjs1Xo+yYyJMvzLL59mhAyb3p/cD+Y3/s3WhAx+l0XOKpzXnblrv9d3q4c2tWmm/SyFqthaqd0= admin@vm",
    ),
    tags={
        "key1": "myvalue1",
        "key2": "myvalue2",
    },
    virtual_machine_name="virtualMachineName")

```

```yaml
resources:
  console:
    type: azure-native:networkcloud:Console
    properties:
      consoleName: default
      enabled: True
      expiration: 2022-06-01T01:27:03.008Z
      extendedLocation:
        name: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterManagerExtendedLocationName
        type: CustomLocation
      location: location
      resourceGroupName: resourceGroupName
      sshPublicKey:
        keyData: ssh-rsa AAtsE3njSONzDYRIZv/WLjVuMfrUSByHp+jfaaOLHTIIB4fJvo6dQUZxE20w2iDHV3tEkmnTo84eba97VMueQD6OzJPEyWZMRpz8UYWOd0IXeRqiFu1lawNblZhwNT/ojNZfpB3af/YDzwQCZgTcTRyNNhL4o/blKUmug0daSsSXISTRnIDpcf5qytjs1Xo+yYyJMvzLL59mhAyb3p/cD+Y3/s3WhAx+l0XOKpzXnblrv9d3q4c2tWmm/SyFqthaqd0= admin@vm
      tags:
        key1: myvalue1
        key2: myvalue2
      virtualMachineName: virtualMachineName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:networkcloud:Console default /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/virtualMachines/virtualMachineName/consoles/default 
```
