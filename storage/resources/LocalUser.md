The local user associated with the storage accounts.
API Version: 2022-09-01.
Previous API Version: 2021-08-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateLocalUser
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var localUser = new AzureNative.Storage.LocalUser("localUser", new()
    {
        AccountName = "sto2527",
        HasSshPassword = true,
        HomeDirectory = "homedirectory",
        PermissionScopes = new[]
        {
            new AzureNative.Storage.Inputs.PermissionScopeArgs
            {
                Permissions = "rwd",
                ResourceName = "share1",
                Service = "file",
            },
            new AzureNative.Storage.Inputs.PermissionScopeArgs
            {
                Permissions = "rw",
                ResourceName = "share2",
                Service = "file",
            },
        },
        ResourceGroupName = "res6977",
        SshAuthorizedKeys = new[]
        {
            new AzureNative.Storage.Inputs.SshPublicKeyArgs
            {
                Description = "key name",
                Key = "ssh-rsa keykeykeykeykey=",
            },
        },
        Username = "user1",
    });

});


```

```go
package main

import (
	storage "github.com/pulumi/pulumi-azure-native-sdk/storage"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := storage.NewLocalUser(ctx, "localUser", &storage.LocalUserArgs{
			AccountName:    pulumi.String("sto2527"),
			HasSshPassword: pulumi.Bool(true),
			HomeDirectory:  pulumi.String("homedirectory"),
			PermissionScopes: []storage.PermissionScopeArgs{
				{
					Permissions:  pulumi.String("rwd"),
					ResourceName: pulumi.String("share1"),
					Service:      pulumi.String("file"),
				},
				{
					Permissions:  pulumi.String("rw"),
					ResourceName: pulumi.String("share2"),
					Service:      pulumi.String("file"),
				},
			},
			ResourceGroupName: pulumi.String("res6977"),
			SshAuthorizedKeys: []storage.SshPublicKeyArgs{
				{
					Description: pulumi.String("key name"),
					Key:         pulumi.String("ssh-rsa keykeykeykeykey="),
				},
			},
			Username: pulumi.String("user1"),
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
import com.pulumi.azurenative.storage.LocalUser;
import com.pulumi.azurenative.storage.LocalUserArgs;
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
        var localUser = new LocalUser("localUser", LocalUserArgs.builder()        
            .accountName("sto2527")
            .hasSshPassword(true)
            .homeDirectory("homedirectory")
            .permissionScopes(            
                Map.ofEntries(
                    Map.entry("permissions", "rwd"),
                    Map.entry("resourceName", "share1"),
                    Map.entry("service", "file")
                ),
                Map.ofEntries(
                    Map.entry("permissions", "rw"),
                    Map.entry("resourceName", "share2"),
                    Map.entry("service", "file")
                ))
            .resourceGroupName("res6977")
            .sshAuthorizedKeys(Map.ofEntries(
                Map.entry("description", "key name"),
                Map.entry("key", "ssh-rsa keykeykeykeykey=")
            ))
            .username("user1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const localUser = new azure_native.storage.LocalUser("localUser", {
    accountName: "sto2527",
    hasSshPassword: true,
    homeDirectory: "homedirectory",
    permissionScopes: [
        {
            permissions: "rwd",
            resourceName: "share1",
            service: "file",
        },
        {
            permissions: "rw",
            resourceName: "share2",
            service: "file",
        },
    ],
    resourceGroupName: "res6977",
    sshAuthorizedKeys: [{
        description: "key name",
        key: "ssh-rsa keykeykeykeykey=",
    }],
    username: "user1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

local_user = azure_native.storage.LocalUser("localUser",
    account_name="sto2527",
    has_ssh_password=True,
    home_directory="homedirectory",
    permission_scopes=[
        azure_native.storage.PermissionScopeArgs(
            permissions="rwd",
            resource_name="share1",
            service="file",
        ),
        azure_native.storage.PermissionScopeArgs(
            permissions="rw",
            resource_name="share2",
            service="file",
        ),
    ],
    resource_group_name="res6977",
    ssh_authorized_keys=[azure_native.storage.SshPublicKeyArgs(
        description="key name",
        key="ssh-rsa keykeykeykeykey=",
    )],
    username="user1")

```

```yaml
resources:
  localUser:
    type: azure-native:storage:LocalUser
    properties:
      accountName: sto2527
      hasSshPassword: true
      homeDirectory: homedirectory
      permissionScopes:
        - permissions: rwd
          resourceName: share1
          service: file
        - permissions: rw
          resourceName: share2
          service: file
      resourceGroupName: res6977
      sshAuthorizedKeys:
        - description: key name
          key: ssh-rsa keykeykeykeykey=
      username: user1

```

{{% /example %}}
{{% example %}}
### UpdateLocalUser
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var localUser = new AzureNative.Storage.LocalUser("localUser", new()
    {
        AccountName = "sto2527",
        HasSharedKey = false,
        HasSshKey = false,
        HasSshPassword = false,
        HomeDirectory = "homedirectory2",
        ResourceGroupName = "res6977",
        Username = "user1",
    });

});


```

```go
package main

import (
	storage "github.com/pulumi/pulumi-azure-native-sdk/storage"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := storage.NewLocalUser(ctx, "localUser", &storage.LocalUserArgs{
			AccountName:       pulumi.String("sto2527"),
			HasSharedKey:      pulumi.Bool(false),
			HasSshKey:         pulumi.Bool(false),
			HasSshPassword:    pulumi.Bool(false),
			HomeDirectory:     pulumi.String("homedirectory2"),
			ResourceGroupName: pulumi.String("res6977"),
			Username:          pulumi.String("user1"),
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
import com.pulumi.azurenative.storage.LocalUser;
import com.pulumi.azurenative.storage.LocalUserArgs;
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
        var localUser = new LocalUser("localUser", LocalUserArgs.builder()        
            .accountName("sto2527")
            .hasSharedKey(false)
            .hasSshKey(false)
            .hasSshPassword(false)
            .homeDirectory("homedirectory2")
            .resourceGroupName("res6977")
            .username("user1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const localUser = new azure_native.storage.LocalUser("localUser", {
    accountName: "sto2527",
    hasSharedKey: false,
    hasSshKey: false,
    hasSshPassword: false,
    homeDirectory: "homedirectory2",
    resourceGroupName: "res6977",
    username: "user1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

local_user = azure_native.storage.LocalUser("localUser",
    account_name="sto2527",
    has_shared_key=False,
    has_ssh_key=False,
    has_ssh_password=False,
    home_directory="homedirectory2",
    resource_group_name="res6977",
    username="user1")

```

```yaml
resources:
  localUser:
    type: azure-native:storage:LocalUser
    properties:
      accountName: sto2527
      hasSharedKey: false
      hasSshKey: false
      hasSshPassword: false
      homeDirectory: homedirectory2
      resourceGroupName: res6977
      username: user1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storage:LocalUser user1 /subscriptions/{subscription-id}/resourceGroups/res6977/providers/Microsoft.Storage/storageAccounts/sto2527/loalUsers/user1 
```
