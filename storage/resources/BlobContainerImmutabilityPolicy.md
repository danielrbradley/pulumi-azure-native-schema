The ImmutabilityPolicy property of a blob container, including Id, resource name, resource type, Etag.
API Version: 2022-09-01.
Previous API Version: 2021-02-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrUpdateImmutabilityPolicy
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var blobContainerImmutabilityPolicy = new AzureNative.Storage.BlobContainerImmutabilityPolicy("blobContainerImmutabilityPolicy", new()
    {
        AccountName = "sto7069",
        AllowProtectedAppendWrites = true,
        ContainerName = "container6397",
        ImmutabilityPeriodSinceCreationInDays = 3,
        ImmutabilityPolicyName = "default",
        ResourceGroupName = "res1782",
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
		_, err := storage.NewBlobContainerImmutabilityPolicy(ctx, "blobContainerImmutabilityPolicy", &storage.BlobContainerImmutabilityPolicyArgs{
			AccountName:                           pulumi.String("sto7069"),
			AllowProtectedAppendWrites:            pulumi.Bool(true),
			ContainerName:                         pulumi.String("container6397"),
			ImmutabilityPeriodSinceCreationInDays: pulumi.Int(3),
			ImmutabilityPolicyName:                pulumi.String("default"),
			ResourceGroupName:                     pulumi.String("res1782"),
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
import com.pulumi.azurenative.storage.BlobContainerImmutabilityPolicy;
import com.pulumi.azurenative.storage.BlobContainerImmutabilityPolicyArgs;
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
        var blobContainerImmutabilityPolicy = new BlobContainerImmutabilityPolicy("blobContainerImmutabilityPolicy", BlobContainerImmutabilityPolicyArgs.builder()        
            .accountName("sto7069")
            .allowProtectedAppendWrites(true)
            .containerName("container6397")
            .immutabilityPeriodSinceCreationInDays(3)
            .immutabilityPolicyName("default")
            .resourceGroupName("res1782")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const blobContainerImmutabilityPolicy = new azure_native.storage.BlobContainerImmutabilityPolicy("blobContainerImmutabilityPolicy", {
    accountName: "sto7069",
    allowProtectedAppendWrites: true,
    containerName: "container6397",
    immutabilityPeriodSinceCreationInDays: 3,
    immutabilityPolicyName: "default",
    resourceGroupName: "res1782",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

blob_container_immutability_policy = azure_native.storage.BlobContainerImmutabilityPolicy("blobContainerImmutabilityPolicy",
    account_name="sto7069",
    allow_protected_append_writes=True,
    container_name="container6397",
    immutability_period_since_creation_in_days=3,
    immutability_policy_name="default",
    resource_group_name="res1782")

```

```yaml
resources:
  blobContainerImmutabilityPolicy:
    type: azure-native:storage:BlobContainerImmutabilityPolicy
    properties:
      accountName: sto7069
      allowProtectedAppendWrites: true
      containerName: container6397
      immutabilityPeriodSinceCreationInDays: 3
      immutabilityPolicyName: default
      resourceGroupName: res1782

```

{{% /example %}}
{{% example %}}
### CreateOrUpdateImmutabilityPolicyWithAllowProtectedAppendWritesAll
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var blobContainerImmutabilityPolicy = new AzureNative.Storage.BlobContainerImmutabilityPolicy("blobContainerImmutabilityPolicy", new()
    {
        AccountName = "sto7069",
        AllowProtectedAppendWritesAll = true,
        ContainerName = "container6397",
        ImmutabilityPeriodSinceCreationInDays = 3,
        ImmutabilityPolicyName = "default",
        ResourceGroupName = "res1782",
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
		_, err := storage.NewBlobContainerImmutabilityPolicy(ctx, "blobContainerImmutabilityPolicy", &storage.BlobContainerImmutabilityPolicyArgs{
			AccountName:                           pulumi.String("sto7069"),
			AllowProtectedAppendWritesAll:         pulumi.Bool(true),
			ContainerName:                         pulumi.String("container6397"),
			ImmutabilityPeriodSinceCreationInDays: pulumi.Int(3),
			ImmutabilityPolicyName:                pulumi.String("default"),
			ResourceGroupName:                     pulumi.String("res1782"),
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
import com.pulumi.azurenative.storage.BlobContainerImmutabilityPolicy;
import com.pulumi.azurenative.storage.BlobContainerImmutabilityPolicyArgs;
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
        var blobContainerImmutabilityPolicy = new BlobContainerImmutabilityPolicy("blobContainerImmutabilityPolicy", BlobContainerImmutabilityPolicyArgs.builder()        
            .accountName("sto7069")
            .allowProtectedAppendWritesAll(true)
            .containerName("container6397")
            .immutabilityPeriodSinceCreationInDays(3)
            .immutabilityPolicyName("default")
            .resourceGroupName("res1782")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const blobContainerImmutabilityPolicy = new azure_native.storage.BlobContainerImmutabilityPolicy("blobContainerImmutabilityPolicy", {
    accountName: "sto7069",
    allowProtectedAppendWritesAll: true,
    containerName: "container6397",
    immutabilityPeriodSinceCreationInDays: 3,
    immutabilityPolicyName: "default",
    resourceGroupName: "res1782",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

blob_container_immutability_policy = azure_native.storage.BlobContainerImmutabilityPolicy("blobContainerImmutabilityPolicy",
    account_name="sto7069",
    allow_protected_append_writes_all=True,
    container_name="container6397",
    immutability_period_since_creation_in_days=3,
    immutability_policy_name="default",
    resource_group_name="res1782")

```

```yaml
resources:
  blobContainerImmutabilityPolicy:
    type: azure-native:storage:BlobContainerImmutabilityPolicy
    properties:
      accountName: sto7069
      allowProtectedAppendWritesAll: true
      containerName: container6397
      immutabilityPeriodSinceCreationInDays: 3
      immutabilityPolicyName: default
      resourceGroupName: res1782

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storage:BlobContainerImmutabilityPolicy default /subscriptions/{subscription-id}/resourceGroups/res1782/providers/Microsoft.Storage/storageAccounts/sto7069/blobServices/default/containers/container6397/immutabilityPolicies/default 
```
