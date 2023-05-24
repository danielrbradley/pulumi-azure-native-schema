Storage resource payload.
API Version: 2022-12-01.
Previous API Version: 2021-09-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Storages_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var storage = new AzureNative.AppPlatform.Storage("storage", new()
    {
        Properties = new AzureNative.AppPlatform.Inputs.StorageAccountArgs
        {
            AccountKey = "account-key-of-storage-account",
            AccountName = "storage-account-name",
            StorageType = "StorageAccount",
        },
        ResourceGroupName = "myResourceGroup",
        ServiceName = "myservice",
        StorageName = "mystorage",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.appplatform.Storage;
import com.pulumi.azurenative.appplatform.StorageArgs;
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
        var storage = new Storage("storage", StorageArgs.builder()        
            .properties(Map.ofEntries(
                Map.entry("accountKey", "account-key-of-storage-account"),
                Map.entry("accountName", "storage-account-name"),
                Map.entry("storageType", "StorageAccount")
            ))
            .resourceGroupName("myResourceGroup")
            .serviceName("myservice")
            .storageName("mystorage")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const storage = new azure_native.appplatform.Storage("storage", {
    properties: {
        accountKey: "account-key-of-storage-account",
        accountName: "storage-account-name",
        storageType: "StorageAccount",
    },
    resourceGroupName: "myResourceGroup",
    serviceName: "myservice",
    storageName: "mystorage",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

storage = azure_native.appplatform.Storage("storage",
    properties=azure_native.appplatform.StorageAccountResponseArgs(
        account_key="account-key-of-storage-account",
        account_name="storage-account-name",
        storage_type="StorageAccount",
    ),
    resource_group_name="myResourceGroup",
    service_name="myservice",
    storage_name="mystorage")

```

```yaml
resources:
  storage:
    type: azure-native:appplatform:Storage
    properties:
      properties:
        accountKey: account-key-of-storage-account
        accountName: storage-account-name
        storageType: StorageAccount
      resourceGroupName: myResourceGroup
      serviceName: myservice
      storageName: mystorage

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:appplatform:Storage mystorage /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.AppPlatform/Spring/myservice/storages/mystorage 
```
