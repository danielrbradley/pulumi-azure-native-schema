Properties of the table, including Id, resource name, resource type.
API Version: 2022-09-01.
Previous API Version: 2021-02-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### TableOperationPut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var table = new AzureNative.Storage.Table("table", new()
    {
        AccountName = "sto328",
        ResourceGroupName = "res3376",
        TableName = "table6185",
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
		_, err := storage.NewTable(ctx, "table", &storage.TableArgs{
			AccountName:       pulumi.String("sto328"),
			ResourceGroupName: pulumi.String("res3376"),
			TableName:         pulumi.String("table6185"),
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
import com.pulumi.azurenative.storage.Table;
import com.pulumi.azurenative.storage.TableArgs;
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
        var table = new Table("table", TableArgs.builder()        
            .accountName("sto328")
            .resourceGroupName("res3376")
            .tableName("table6185")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const table = new azure_native.storage.Table("table", {
    accountName: "sto328",
    resourceGroupName: "res3376",
    tableName: "table6185",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

table = azure_native.storage.Table("table",
    account_name="sto328",
    resource_group_name="res3376",
    table_name="table6185")

```

```yaml
resources:
  table:
    type: azure-native:storage:Table
    properties:
      accountName: sto328
      resourceGroupName: res3376
      tableName: table6185

```

{{% /example %}}
{{% example %}}
### TableOperationPutOrPatchAcls
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var table = new AzureNative.Storage.Table("table", new()
    {
        AccountName = "sto328",
        ResourceGroupName = "res3376",
        SignedIdentifiers = new[]
        {
            new AzureNative.Storage.Inputs.TableSignedIdentifierArgs
            {
                AccessPolicy = new AzureNative.Storage.Inputs.TableAccessPolicyArgs
                {
                    ExpiryTime = "2022-03-20T08:49:37.0000000Z",
                    Permission = "raud",
                    StartTime = "2022-03-17T08:49:37.0000000Z",
                },
                Id = "MTIzNDU2Nzg5MDEyMzQ1Njc4OTAxMjM0NTY3ODkwMTI",
            },
            new AzureNative.Storage.Inputs.TableSignedIdentifierArgs
            {
                AccessPolicy = new AzureNative.Storage.Inputs.TableAccessPolicyArgs
                {
                    ExpiryTime = "2022-03-20T08:49:37.0000000Z",
                    Permission = "rad",
                    StartTime = "2022-03-17T08:49:37.0000000Z",
                },
                Id = "PTIzNDU2Nzg5MDEyMzQ1Njc4OTAxMjM0NTY3ODklMTI",
            },
        },
        TableName = "table6185",
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
		_, err := storage.NewTable(ctx, "table", &storage.TableArgs{
			AccountName:       pulumi.String("sto328"),
			ResourceGroupName: pulumi.String("res3376"),
			SignedIdentifiers: []storage.TableSignedIdentifierArgs{
				{
					AccessPolicy: {
						ExpiryTime: pulumi.String("2022-03-20T08:49:37.0000000Z"),
						Permission: pulumi.String("raud"),
						StartTime:  pulumi.String("2022-03-17T08:49:37.0000000Z"),
					},
					Id: pulumi.String("MTIzNDU2Nzg5MDEyMzQ1Njc4OTAxMjM0NTY3ODkwMTI"),
				},
				{
					AccessPolicy: {
						ExpiryTime: pulumi.String("2022-03-20T08:49:37.0000000Z"),
						Permission: pulumi.String("rad"),
						StartTime:  pulumi.String("2022-03-17T08:49:37.0000000Z"),
					},
					Id: pulumi.String("PTIzNDU2Nzg5MDEyMzQ1Njc4OTAxMjM0NTY3ODklMTI"),
				},
			},
			TableName: pulumi.String("table6185"),
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
import com.pulumi.azurenative.storage.Table;
import com.pulumi.azurenative.storage.TableArgs;
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
        var table = new Table("table", TableArgs.builder()        
            .accountName("sto328")
            .resourceGroupName("res3376")
            .signedIdentifiers(            
                Map.ofEntries(
                    Map.entry("accessPolicy", Map.ofEntries(
                        Map.entry("expiryTime", "2022-03-20T08:49:37.0000000Z"),
                        Map.entry("permission", "raud"),
                        Map.entry("startTime", "2022-03-17T08:49:37.0000000Z")
                    )),
                    Map.entry("id", "MTIzNDU2Nzg5MDEyMzQ1Njc4OTAxMjM0NTY3ODkwMTI")
                ),
                Map.ofEntries(
                    Map.entry("accessPolicy", Map.ofEntries(
                        Map.entry("expiryTime", "2022-03-20T08:49:37.0000000Z"),
                        Map.entry("permission", "rad"),
                        Map.entry("startTime", "2022-03-17T08:49:37.0000000Z")
                    )),
                    Map.entry("id", "PTIzNDU2Nzg5MDEyMzQ1Njc4OTAxMjM0NTY3ODklMTI")
                ))
            .tableName("table6185")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const table = new azure_native.storage.Table("table", {
    accountName: "sto328",
    resourceGroupName: "res3376",
    signedIdentifiers: [
        {
            accessPolicy: {
                expiryTime: "2022-03-20T08:49:37.0000000Z",
                permission: "raud",
                startTime: "2022-03-17T08:49:37.0000000Z",
            },
            id: "MTIzNDU2Nzg5MDEyMzQ1Njc4OTAxMjM0NTY3ODkwMTI",
        },
        {
            accessPolicy: {
                expiryTime: "2022-03-20T08:49:37.0000000Z",
                permission: "rad",
                startTime: "2022-03-17T08:49:37.0000000Z",
            },
            id: "PTIzNDU2Nzg5MDEyMzQ1Njc4OTAxMjM0NTY3ODklMTI",
        },
    ],
    tableName: "table6185",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

table = azure_native.storage.Table("table",
    account_name="sto328",
    resource_group_name="res3376",
    signed_identifiers=[
        {
            "accessPolicy": azure_native.storage.TableAccessPolicyArgs(
                expiry_time="2022-03-20T08:49:37.0000000Z",
                permission="raud",
                start_time="2022-03-17T08:49:37.0000000Z",
            ),
            "id": "MTIzNDU2Nzg5MDEyMzQ1Njc4OTAxMjM0NTY3ODkwMTI",
        },
        {
            "accessPolicy": azure_native.storage.TableAccessPolicyArgs(
                expiry_time="2022-03-20T08:49:37.0000000Z",
                permission="rad",
                start_time="2022-03-17T08:49:37.0000000Z",
            ),
            "id": "PTIzNDU2Nzg5MDEyMzQ1Njc4OTAxMjM0NTY3ODklMTI",
        },
    ],
    table_name="table6185")

```

```yaml
resources:
  table:
    type: azure-native:storage:Table
    properties:
      accountName: sto328
      resourceGroupName: res3376
      signedIdentifiers:
        - accessPolicy:
            expiryTime: 2022-03-20T08:49:37.0000000Z
            permission: raud
            startTime: 2022-03-17T08:49:37.0000000Z
          id: MTIzNDU2Nzg5MDEyMzQ1Njc4OTAxMjM0NTY3ODkwMTI
        - accessPolicy:
            expiryTime: 2022-03-20T08:49:37.0000000Z
            permission: rad
            startTime: 2022-03-17T08:49:37.0000000Z
          id: PTIzNDU2Nzg5MDEyMzQ1Njc4OTAxMjM0NTY3ODklMTI
      tableName: table6185

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storage:Table table6185 /subscriptions/{subscription-id}/resourceGroups/res3376/providers/Microsoft.Storage/storageAccounts/sto328/tableServices/default/tables/table6185 
```
