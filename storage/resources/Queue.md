
API Version: 2022-09-01.
Previous API Version: 2021-02-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### QueueOperationPut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var queue = new AzureNative.Storage.Queue("queue", new()
    {
        AccountName = "sto328",
        QueueName = "queue6185",
        ResourceGroupName = "res3376",
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
		_, err := storage.NewQueue(ctx, "queue", &storage.QueueArgs{
			AccountName:       pulumi.String("sto328"),
			QueueName:         pulumi.String("queue6185"),
			ResourceGroupName: pulumi.String("res3376"),
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
import com.pulumi.azurenative.storage.Queue;
import com.pulumi.azurenative.storage.QueueArgs;
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
        var queue = new Queue("queue", QueueArgs.builder()        
            .accountName("sto328")
            .queueName("queue6185")
            .resourceGroupName("res3376")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const queue = new azure_native.storage.Queue("queue", {
    accountName: "sto328",
    queueName: "queue6185",
    resourceGroupName: "res3376",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

queue = azure_native.storage.Queue("queue",
    account_name="sto328",
    queue_name="queue6185",
    resource_group_name="res3376")

```

```yaml
resources:
  queue:
    type: azure-native:storage:Queue
    properties:
      accountName: sto328
      queueName: queue6185
      resourceGroupName: res3376

```

{{% /example %}}
{{% example %}}
### QueueOperationPutWithMetadata
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var queue = new AzureNative.Storage.Queue("queue", new()
    {
        AccountName = "sto328",
        Metadata = 
        {
            { "sample1", "meta1" },
            { "sample2", "meta2" },
        },
        QueueName = "queue6185",
        ResourceGroupName = "res3376",
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
		_, err := storage.NewQueue(ctx, "queue", &storage.QueueArgs{
			AccountName: pulumi.String("sto328"),
			Metadata: pulumi.StringMap{
				"sample1": pulumi.String("meta1"),
				"sample2": pulumi.String("meta2"),
			},
			QueueName:         pulumi.String("queue6185"),
			ResourceGroupName: pulumi.String("res3376"),
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
import com.pulumi.azurenative.storage.Queue;
import com.pulumi.azurenative.storage.QueueArgs;
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
        var queue = new Queue("queue", QueueArgs.builder()        
            .accountName("sto328")
            .metadata(Map.ofEntries(
                Map.entry("sample1", "meta1"),
                Map.entry("sample2", "meta2")
            ))
            .queueName("queue6185")
            .resourceGroupName("res3376")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const queue = new azure_native.storage.Queue("queue", {
    accountName: "sto328",
    metadata: {
        sample1: "meta1",
        sample2: "meta2",
    },
    queueName: "queue6185",
    resourceGroupName: "res3376",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

queue = azure_native.storage.Queue("queue",
    account_name="sto328",
    metadata={
        "sample1": "meta1",
        "sample2": "meta2",
    },
    queue_name="queue6185",
    resource_group_name="res3376")

```

```yaml
resources:
  queue:
    type: azure-native:storage:Queue
    properties:
      accountName: sto328
      metadata:
        sample1: meta1
        sample2: meta2
      queueName: queue6185
      resourceGroupName: res3376

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storage:Queue queue6185 /subscriptions/{subscription-id}/resourceGroups/res3376/providers/Microsoft.Storage/storageAccounts/sto328/queueServices/default/queues/queue6185 
```
