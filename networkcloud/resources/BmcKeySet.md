
API Version: 2022-12-12-preview.
Previous API Version: 2022-12-12-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update baseboard management controller key set of cluster
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var bmcKeySet = new AzureNative.NetworkCloud.BmcKeySet("bmcKeySet", new()
    {
        AzureGroupId = "f110271b-XXXX-4163-9b99-214d91660f0e",
        BmcKeySetName = "bmcKeySetName",
        ClusterName = "clusterName",
        Expiration = "2022-12-31T23:59:59.008Z",
        ExtendedLocation = new AzureNative.NetworkCloud.Inputs.ExtendedLocationArgs
        {
            Name = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName",
            Type = "CustomLocation",
        },
        Location = "location",
        PrivilegeLevel = "Administrator",
        ResourceGroupName = "resourceGroupName",
        Tags = 
        {
            { "key1", "myvalue1" },
            { "key2", "myvalue2" },
        },
        UserList = new[]
        {
            new AzureNative.NetworkCloud.Inputs.KeySetUserArgs
            {
                AzureUserName = "userABC",
                Description = "Needs access for troubleshooting as a part of the support team",
                SshPublicKey = new AzureNative.NetworkCloud.Inputs.SshPublicKeyArgs
                {
                    KeyData = "ssh-rsa AAtsE3njSONzDYRIZv/WLjVuMfrUSByHp+jfaaOLHTIIB4fJvo6dQUZxE20w2iDHV3tEkmnTo84eba97VMueQD6OzJPEyWZMRpz8UYWOd0IXeRqiFu1lawNblZhwNT/ojNZfpB3af/YDzwQCZgTcTRyNNhL4o/blKUmug0daSsSXISTRnIDpcf5qytjs1Xo+yYyJMvzLL59mhAyb3p/cD+Y3/s3WhAx+l0XOKpzXnblrv9d3q4c2tWmm/SyFqthaqd0= admin@vm",
                },
            },
            new AzureNative.NetworkCloud.Inputs.KeySetUserArgs
            {
                AzureUserName = "userXYZ",
                Description = "Needs access for troubleshooting as a part of the support team",
                SshPublicKey = new AzureNative.NetworkCloud.Inputs.SshPublicKeyArgs
                {
                    KeyData = "ssh-rsa AAtsE3njSONzDYRIZv/WLjVuMfrUSByHp+jfaaOLHTIIB4fJvo6dQUZxE20w2iDHV3tEkmnTo84eba97VMueQD6OzJPEyWZMRpz8UYWOd0IXeRqiFu1lawNblZhwNT/ojNZfpB3af/YDzwQCZgTcTRyNNhL4o/blKUmug0daSsSXISTRnIDpcf5qytjs1Xo+yYyJMvzLL59mhAyb3p/cD+Y3/s3WhAx+l0XOKpzXnblrv9d3q4c2tWmm/SyFqthaqd0= admin@vm",
                },
            },
        },
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
		_, err := networkcloud.NewBmcKeySet(ctx, "bmcKeySet", &networkcloud.BmcKeySetArgs{
			AzureGroupId:  pulumi.String("f110271b-XXXX-4163-9b99-214d91660f0e"),
			BmcKeySetName: pulumi.String("bmcKeySetName"),
			ClusterName:   pulumi.String("clusterName"),
			Expiration:    pulumi.String("2022-12-31T23:59:59.008Z"),
			ExtendedLocation: &networkcloud.ExtendedLocationArgs{
				Name: pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName"),
				Type: pulumi.String("CustomLocation"),
			},
			Location:          pulumi.String("location"),
			PrivilegeLevel:    pulumi.String("Administrator"),
			ResourceGroupName: pulumi.String("resourceGroupName"),
			Tags: pulumi.StringMap{
				"key1": pulumi.String("myvalue1"),
				"key2": pulumi.String("myvalue2"),
			},
			UserList: []networkcloud.KeySetUserArgs{
				{
					AzureUserName: pulumi.String("userABC"),
					Description:   pulumi.String("Needs access for troubleshooting as a part of the support team"),
					SshPublicKey: {
						KeyData: pulumi.String("ssh-rsa AAtsE3njSONzDYRIZv/WLjVuMfrUSByHp+jfaaOLHTIIB4fJvo6dQUZxE20w2iDHV3tEkmnTo84eba97VMueQD6OzJPEyWZMRpz8UYWOd0IXeRqiFu1lawNblZhwNT/ojNZfpB3af/YDzwQCZgTcTRyNNhL4o/blKUmug0daSsSXISTRnIDpcf5qytjs1Xo+yYyJMvzLL59mhAyb3p/cD+Y3/s3WhAx+l0XOKpzXnblrv9d3q4c2tWmm/SyFqthaqd0= admin@vm"),
					},
				},
				{
					AzureUserName: pulumi.String("userXYZ"),
					Description:   pulumi.String("Needs access for troubleshooting as a part of the support team"),
					SshPublicKey: {
						KeyData: pulumi.String("ssh-rsa AAtsE3njSONzDYRIZv/WLjVuMfrUSByHp+jfaaOLHTIIB4fJvo6dQUZxE20w2iDHV3tEkmnTo84eba97VMueQD6OzJPEyWZMRpz8UYWOd0IXeRqiFu1lawNblZhwNT/ojNZfpB3af/YDzwQCZgTcTRyNNhL4o/blKUmug0daSsSXISTRnIDpcf5qytjs1Xo+yYyJMvzLL59mhAyb3p/cD+Y3/s3WhAx+l0XOKpzXnblrv9d3q4c2tWmm/SyFqthaqd0= admin@vm"),
					},
				},
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
import com.pulumi.azurenative.networkcloud.BmcKeySet;
import com.pulumi.azurenative.networkcloud.BmcKeySetArgs;
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
        var bmcKeySet = new BmcKeySet("bmcKeySet", BmcKeySetArgs.builder()        
            .azureGroupId("f110271b-XXXX-4163-9b99-214d91660f0e")
            .bmcKeySetName("bmcKeySetName")
            .clusterName("clusterName")
            .expiration("2022-12-31T23:59:59.008Z")
            .extendedLocation(Map.ofEntries(
                Map.entry("name", "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName"),
                Map.entry("type", "CustomLocation")
            ))
            .location("location")
            .privilegeLevel("Administrator")
            .resourceGroupName("resourceGroupName")
            .tags(Map.ofEntries(
                Map.entry("key1", "myvalue1"),
                Map.entry("key2", "myvalue2")
            ))
            .userList(            
                Map.ofEntries(
                    Map.entry("azureUserName", "userABC"),
                    Map.entry("description", "Needs access for troubleshooting as a part of the support team"),
                    Map.entry("sshPublicKey", Map.of("keyData", "ssh-rsa AAtsE3njSONzDYRIZv/WLjVuMfrUSByHp+jfaaOLHTIIB4fJvo6dQUZxE20w2iDHV3tEkmnTo84eba97VMueQD6OzJPEyWZMRpz8UYWOd0IXeRqiFu1lawNblZhwNT/ojNZfpB3af/YDzwQCZgTcTRyNNhL4o/blKUmug0daSsSXISTRnIDpcf5qytjs1Xo+yYyJMvzLL59mhAyb3p/cD+Y3/s3WhAx+l0XOKpzXnblrv9d3q4c2tWmm/SyFqthaqd0= admin@vm"))
                ),
                Map.ofEntries(
                    Map.entry("azureUserName", "userXYZ"),
                    Map.entry("description", "Needs access for troubleshooting as a part of the support team"),
                    Map.entry("sshPublicKey", Map.of("keyData", "ssh-rsa AAtsE3njSONzDYRIZv/WLjVuMfrUSByHp+jfaaOLHTIIB4fJvo6dQUZxE20w2iDHV3tEkmnTo84eba97VMueQD6OzJPEyWZMRpz8UYWOd0IXeRqiFu1lawNblZhwNT/ojNZfpB3af/YDzwQCZgTcTRyNNhL4o/blKUmug0daSsSXISTRnIDpcf5qytjs1Xo+yYyJMvzLL59mhAyb3p/cD+Y3/s3WhAx+l0XOKpzXnblrv9d3q4c2tWmm/SyFqthaqd0= admin@vm"))
                ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const bmcKeySet = new azure_native.networkcloud.BmcKeySet("bmcKeySet", {
    azureGroupId: "f110271b-XXXX-4163-9b99-214d91660f0e",
    bmcKeySetName: "bmcKeySetName",
    clusterName: "clusterName",
    expiration: "2022-12-31T23:59:59.008Z",
    extendedLocation: {
        name: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName",
        type: "CustomLocation",
    },
    location: "location",
    privilegeLevel: "Administrator",
    resourceGroupName: "resourceGroupName",
    tags: {
        key1: "myvalue1",
        key2: "myvalue2",
    },
    userList: [
        {
            azureUserName: "userABC",
            description: "Needs access for troubleshooting as a part of the support team",
            sshPublicKey: {
                keyData: "ssh-rsa AAtsE3njSONzDYRIZv/WLjVuMfrUSByHp+jfaaOLHTIIB4fJvo6dQUZxE20w2iDHV3tEkmnTo84eba97VMueQD6OzJPEyWZMRpz8UYWOd0IXeRqiFu1lawNblZhwNT/ojNZfpB3af/YDzwQCZgTcTRyNNhL4o/blKUmug0daSsSXISTRnIDpcf5qytjs1Xo+yYyJMvzLL59mhAyb3p/cD+Y3/s3WhAx+l0XOKpzXnblrv9d3q4c2tWmm/SyFqthaqd0= admin@vm",
            },
        },
        {
            azureUserName: "userXYZ",
            description: "Needs access for troubleshooting as a part of the support team",
            sshPublicKey: {
                keyData: "ssh-rsa AAtsE3njSONzDYRIZv/WLjVuMfrUSByHp+jfaaOLHTIIB4fJvo6dQUZxE20w2iDHV3tEkmnTo84eba97VMueQD6OzJPEyWZMRpz8UYWOd0IXeRqiFu1lawNblZhwNT/ojNZfpB3af/YDzwQCZgTcTRyNNhL4o/blKUmug0daSsSXISTRnIDpcf5qytjs1Xo+yYyJMvzLL59mhAyb3p/cD+Y3/s3WhAx+l0XOKpzXnblrv9d3q4c2tWmm/SyFqthaqd0= admin@vm",
            },
        },
    ],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

bmc_key_set = azure_native.networkcloud.BmcKeySet("bmcKeySet",
    azure_group_id="f110271b-XXXX-4163-9b99-214d91660f0e",
    bmc_key_set_name="bmcKeySetName",
    cluster_name="clusterName",
    expiration="2022-12-31T23:59:59.008Z",
    extended_location=azure_native.networkcloud.ExtendedLocationArgs(
        name="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName",
        type="CustomLocation",
    ),
    location="location",
    privilege_level="Administrator",
    resource_group_name="resourceGroupName",
    tags={
        "key1": "myvalue1",
        "key2": "myvalue2",
    },
    user_list=[
        {
            "azureUserName": "userABC",
            "description": "Needs access for troubleshooting as a part of the support team",
            "sshPublicKey": azure_native.networkcloud.SshPublicKeyArgs(
                key_data="ssh-rsa AAtsE3njSONzDYRIZv/WLjVuMfrUSByHp+jfaaOLHTIIB4fJvo6dQUZxE20w2iDHV3tEkmnTo84eba97VMueQD6OzJPEyWZMRpz8UYWOd0IXeRqiFu1lawNblZhwNT/ojNZfpB3af/YDzwQCZgTcTRyNNhL4o/blKUmug0daSsSXISTRnIDpcf5qytjs1Xo+yYyJMvzLL59mhAyb3p/cD+Y3/s3WhAx+l0XOKpzXnblrv9d3q4c2tWmm/SyFqthaqd0= admin@vm",
            ),
        },
        {
            "azureUserName": "userXYZ",
            "description": "Needs access for troubleshooting as a part of the support team",
            "sshPublicKey": azure_native.networkcloud.SshPublicKeyArgs(
                key_data="ssh-rsa AAtsE3njSONzDYRIZv/WLjVuMfrUSByHp+jfaaOLHTIIB4fJvo6dQUZxE20w2iDHV3tEkmnTo84eba97VMueQD6OzJPEyWZMRpz8UYWOd0IXeRqiFu1lawNblZhwNT/ojNZfpB3af/YDzwQCZgTcTRyNNhL4o/blKUmug0daSsSXISTRnIDpcf5qytjs1Xo+yYyJMvzLL59mhAyb3p/cD+Y3/s3WhAx+l0XOKpzXnblrv9d3q4c2tWmm/SyFqthaqd0= admin@vm",
            ),
        },
    ])

```

```yaml
resources:
  bmcKeySet:
    type: azure-native:networkcloud:BmcKeySet
    properties:
      azureGroupId: f110271b-XXXX-4163-9b99-214d91660f0e
      bmcKeySetName: bmcKeySetName
      clusterName: clusterName
      expiration: 2022-12-31T23:59:59.008Z
      extendedLocation:
        name: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName
        type: CustomLocation
      location: location
      privilegeLevel: Administrator
      resourceGroupName: resourceGroupName
      tags:
        key1: myvalue1
        key2: myvalue2
      userList:
        - azureUserName: userABC
          description: Needs access for troubleshooting as a part of the support team
          sshPublicKey:
            keyData: ssh-rsa AAtsE3njSONzDYRIZv/WLjVuMfrUSByHp+jfaaOLHTIIB4fJvo6dQUZxE20w2iDHV3tEkmnTo84eba97VMueQD6OzJPEyWZMRpz8UYWOd0IXeRqiFu1lawNblZhwNT/ojNZfpB3af/YDzwQCZgTcTRyNNhL4o/blKUmug0daSsSXISTRnIDpcf5qytjs1Xo+yYyJMvzLL59mhAyb3p/cD+Y3/s3WhAx+l0XOKpzXnblrv9d3q4c2tWmm/SyFqthaqd0= admin@vm
        - azureUserName: userXYZ
          description: Needs access for troubleshooting as a part of the support team
          sshPublicKey:
            keyData: ssh-rsa AAtsE3njSONzDYRIZv/WLjVuMfrUSByHp+jfaaOLHTIIB4fJvo6dQUZxE20w2iDHV3tEkmnTo84eba97VMueQD6OzJPEyWZMRpz8UYWOd0IXeRqiFu1lawNblZhwNT/ojNZfpB3af/YDzwQCZgTcTRyNNhL4o/blKUmug0daSsSXISTRnIDpcf5qytjs1Xo+yYyJMvzLL59mhAyb3p/cD+Y3/s3WhAx+l0XOKpzXnblrv9d3q4c2tWmm/SyFqthaqd0= admin@vm

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:networkcloud:BmcKeySet bmcKeySetName /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/clusters/clusterName/bmcKeySets/bmcKeySetName 
```
