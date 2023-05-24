Linked service resource type.
API Version: 2018-06-01.
Previous API Version: 2018-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### LinkedServices_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var linkedService = new AzureNative.DataFactory.LinkedService("linkedService", new()
    {
        FactoryName = "exampleFactoryName",
        LinkedServiceName = "exampleLinkedService",
        Properties = new AzureNative.DataFactory.Inputs.AzureStorageLinkedServiceArgs
        {
            ConnectionString = 
            {
                { "type", "SecureString" },
                { "value", "DefaultEndpointsProtocol=https;AccountName=examplestorageaccount;AccountKey=<storage key>" },
            },
            Type = "AzureStorage",
        },
        ResourceGroupName = "exampleResourceGroup",
    });

});


```

```go
package main

import (
	datafactory "github.com/pulumi/pulumi-azure-native-sdk/datafactory"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := datafactory.NewLinkedService(ctx, "linkedService", &datafactory.LinkedServiceArgs{
			FactoryName:       pulumi.String("exampleFactoryName"),
			LinkedServiceName: pulumi.String("exampleLinkedService"),
			Properties: datafactory.AzureStorageLinkedService{
				ConnectionString: map[string]interface{}{
					"type":  "SecureString",
					"value": "DefaultEndpointsProtocol=https;AccountName=examplestorageaccount;AccountKey=<storage key>",
				},
				Type: "AzureStorage",
			},
			ResourceGroupName: pulumi.String("exampleResourceGroup"),
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
import com.pulumi.azurenative.datafactory.LinkedService;
import com.pulumi.azurenative.datafactory.LinkedServiceArgs;
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
        var linkedService = new LinkedService("linkedService", LinkedServiceArgs.builder()        
            .factoryName("exampleFactoryName")
            .linkedServiceName("exampleLinkedService")
            .properties(Map.ofEntries(
                Map.entry("connectionString", AmazonMWSLinkedServiceArgs.builder()
                    .type("SecureString")
                    .value("DefaultEndpointsProtocol=https;AccountName=examplestorageaccount;AccountKey=<storage key>")
                    .build()),
                Map.entry("type", "AzureStorage")
            ))
            .resourceGroupName("exampleResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const linkedService = new azure_native.datafactory.LinkedService("linkedService", {
    factoryName: "exampleFactoryName",
    linkedServiceName: "exampleLinkedService",
    properties: {
        connectionString: {
            type: "SecureString",
            value: "DefaultEndpointsProtocol=https;AccountName=examplestorageaccount;AccountKey=<storage key>",
        },
        type: "AzureStorage",
    },
    resourceGroupName: "exampleResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

linked_service = azure_native.datafactory.LinkedService("linkedService",
    factory_name="exampleFactoryName",
    linked_service_name="exampleLinkedService",
    properties=azure_native.datafactory.AzureStorageLinkedServiceArgs(
        connection_string={
            "type": "SecureString",
            "value": "DefaultEndpointsProtocol=https;AccountName=examplestorageaccount;AccountKey=<storage key>",
        },
        type="AzureStorage",
    ),
    resource_group_name="exampleResourceGroup")

```

```yaml
resources:
  linkedService:
    type: azure-native:datafactory:LinkedService
    properties:
      factoryName: exampleFactoryName
      linkedServiceName: exampleLinkedService
      properties:
        connectionString:
          type: SecureString
          value: DefaultEndpointsProtocol=https;AccountName=examplestorageaccount;AccountKey=<storage key>
        type: AzureStorage
      resourceGroupName: exampleResourceGroup

```

{{% /example %}}
{{% example %}}
### LinkedServices_Update
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var linkedService = new AzureNative.DataFactory.LinkedService("linkedService", new()
    {
        FactoryName = "exampleFactoryName",
        LinkedServiceName = "exampleLinkedService",
        Properties = new AzureNative.DataFactory.Inputs.AzureStorageLinkedServiceArgs
        {
            ConnectionString = 
            {
                { "type", "SecureString" },
                { "value", "DefaultEndpointsProtocol=https;AccountName=examplestorageaccount;AccountKey=<storage key>" },
            },
            Description = "Example description",
            Type = "AzureStorage",
        },
        ResourceGroupName = "exampleResourceGroup",
    });

});


```

```go
package main

import (
	datafactory "github.com/pulumi/pulumi-azure-native-sdk/datafactory"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := datafactory.NewLinkedService(ctx, "linkedService", &datafactory.LinkedServiceArgs{
			FactoryName:       pulumi.String("exampleFactoryName"),
			LinkedServiceName: pulumi.String("exampleLinkedService"),
			Properties: datafactory.AzureStorageLinkedService{
				ConnectionString: map[string]interface{}{
					"type":  "SecureString",
					"value": "DefaultEndpointsProtocol=https;AccountName=examplestorageaccount;AccountKey=<storage key>",
				},
				Description: "Example description",
				Type:        "AzureStorage",
			},
			ResourceGroupName: pulumi.String("exampleResourceGroup"),
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
import com.pulumi.azurenative.datafactory.LinkedService;
import com.pulumi.azurenative.datafactory.LinkedServiceArgs;
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
        var linkedService = new LinkedService("linkedService", LinkedServiceArgs.builder()        
            .factoryName("exampleFactoryName")
            .linkedServiceName("exampleLinkedService")
            .properties(Map.ofEntries(
                Map.entry("connectionString", AmazonMWSLinkedServiceArgs.builder()
                    .type("SecureString")
                    .value("DefaultEndpointsProtocol=https;AccountName=examplestorageaccount;AccountKey=<storage key>")
                    .build()),
                Map.entry("description", "Example description"),
                Map.entry("type", "AzureStorage")
            ))
            .resourceGroupName("exampleResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const linkedService = new azure_native.datafactory.LinkedService("linkedService", {
    factoryName: "exampleFactoryName",
    linkedServiceName: "exampleLinkedService",
    properties: {
        connectionString: {
            type: "SecureString",
            value: "DefaultEndpointsProtocol=https;AccountName=examplestorageaccount;AccountKey=<storage key>",
        },
        description: "Example description",
        type: "AzureStorage",
    },
    resourceGroupName: "exampleResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

linked_service = azure_native.datafactory.LinkedService("linkedService",
    factory_name="exampleFactoryName",
    linked_service_name="exampleLinkedService",
    properties=azure_native.datafactory.AzureStorageLinkedServiceArgs(
        connection_string={
            "type": "SecureString",
            "value": "DefaultEndpointsProtocol=https;AccountName=examplestorageaccount;AccountKey=<storage key>",
        },
        description="Example description",
        type="AzureStorage",
    ),
    resource_group_name="exampleResourceGroup")

```

```yaml
resources:
  linkedService:
    type: azure-native:datafactory:LinkedService
    properties:
      factoryName: exampleFactoryName
      linkedServiceName: exampleLinkedService
      properties:
        connectionString:
          type: SecureString
          value: DefaultEndpointsProtocol=https;AccountName=examplestorageaccount;AccountKey=<storage key>
        description: Example description
        type: AzureStorage
      resourceGroupName: exampleResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:datafactory:LinkedService exampleLinkedService /subscriptions/12345678-1234-1234-1234-12345678abc/resourceGroups/exampleResourceGroup/providers/Microsoft.DataFactory/factories/exampleFactoryName/linkedservices/exampleLinkedService 
```
