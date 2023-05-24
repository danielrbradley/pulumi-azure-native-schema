Specifies information about the SSH public key.
API Version: 2022-11-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a new SSH public key resource.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sshPublicKey = new AzureNative.Compute.SshPublicKey("sshPublicKey", new()
    {
        Location = "westus",
        PublicKey = "{ssh-rsa public key}",
        ResourceGroupName = "myResourceGroup",
        SshPublicKeyName = "mySshPublicKeyName",
    });

});


```

```go
package main

import (
	compute "github.com/pulumi/pulumi-azure-native-sdk/compute"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := compute.NewSshPublicKey(ctx, "sshPublicKey", &compute.SshPublicKeyArgs{
			Location:          pulumi.String("westus"),
			PublicKey:         pulumi.String("{ssh-rsa public key}"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			SshPublicKeyName:  pulumi.String("mySshPublicKeyName"),
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
import com.pulumi.azurenative.compute.SshPublicKey;
import com.pulumi.azurenative.compute.SshPublicKeyArgs;
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
        var sshPublicKey = new SshPublicKey("sshPublicKey", SshPublicKeyArgs.builder()        
            .location("westus")
            .publicKey("{ssh-rsa public key}")
            .resourceGroupName("myResourceGroup")
            .sshPublicKeyName("mySshPublicKeyName")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sshPublicKey = new azure_native.compute.SshPublicKey("sshPublicKey", {
    location: "westus",
    publicKey: "{ssh-rsa public key}",
    resourceGroupName: "myResourceGroup",
    sshPublicKeyName: "mySshPublicKeyName",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

ssh_public_key = azure_native.compute.SshPublicKey("sshPublicKey",
    location="westus",
    public_key="{ssh-rsa public key}",
    resource_group_name="myResourceGroup",
    ssh_public_key_name="mySshPublicKeyName")

```

```yaml
resources:
  sshPublicKey:
    type: azure-native:compute:SshPublicKey
    properties:
      location: westus
      publicKey: '{ssh-rsa public key}'
      resourceGroupName: myResourceGroup
      sshPublicKeyName: mySshPublicKeyName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:compute:SshPublicKey mySshPublicKeyName /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/sshPublicKeys/mySshPublicKeyName 
```
