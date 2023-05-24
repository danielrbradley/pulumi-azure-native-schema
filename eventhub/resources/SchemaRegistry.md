Single item in List or Get Schema Group operation
API Version: 2021-11-01.
Previous API Version: 2022-01-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### SchemaRegistryCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var schemaRegistry = new AzureNative.EventHub.SchemaRegistry("schemaRegistry", new()
    {
        GroupProperties = null,
        NamespaceName = "ali-ua-test-eh-system-1",
        ResourceGroupName = "alitest",
        SchemaCompatibility = "Forward",
        SchemaGroupName = "testSchemaGroup1",
        SchemaType = "Avro",
    });

});


```

```go
package main

import (
	eventhub "github.com/pulumi/pulumi-azure-native-sdk/eventhub"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := eventhub.NewSchemaRegistry(ctx, "schemaRegistry", &eventhub.SchemaRegistryArgs{
			GroupProperties:     nil,
			NamespaceName:       pulumi.String("ali-ua-test-eh-system-1"),
			ResourceGroupName:   pulumi.String("alitest"),
			SchemaCompatibility: pulumi.String("Forward"),
			SchemaGroupName:     pulumi.String("testSchemaGroup1"),
			SchemaType:          pulumi.String("Avro"),
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
import com.pulumi.azurenative.eventhub.SchemaRegistry;
import com.pulumi.azurenative.eventhub.SchemaRegistryArgs;
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
        var schemaRegistry = new SchemaRegistry("schemaRegistry", SchemaRegistryArgs.builder()        
            .groupProperties()
            .namespaceName("ali-ua-test-eh-system-1")
            .resourceGroupName("alitest")
            .schemaCompatibility("Forward")
            .schemaGroupName("testSchemaGroup1")
            .schemaType("Avro")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const schemaRegistry = new azure_native.eventhub.SchemaRegistry("schemaRegistry", {
    groupProperties: {},
    namespaceName: "ali-ua-test-eh-system-1",
    resourceGroupName: "alitest",
    schemaCompatibility: "Forward",
    schemaGroupName: "testSchemaGroup1",
    schemaType: "Avro",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

schema_registry = azure_native.eventhub.SchemaRegistry("schemaRegistry",
    group_properties={},
    namespace_name="ali-ua-test-eh-system-1",
    resource_group_name="alitest",
    schema_compatibility="Forward",
    schema_group_name="testSchemaGroup1",
    schema_type="Avro")

```

```yaml
resources:
  schemaRegistry:
    type: azure-native:eventhub:SchemaRegistry
    properties:
      groupProperties: {}
      namespaceName: ali-ua-test-eh-system-1
      resourceGroupName: alitest
      schemaCompatibility: Forward
      schemaGroupName: testSchemaGroup1
      schemaType: Avro

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:eventhub:SchemaRegistry testSchemaGroup1 /subscriptions/e8baea74-64ce-459b-bee3-5aa4c47b3ae3/resourceGroups/alitest/providers/Microsoft.EventHub/namespaces/ali-ua-test-eh-system-1/schemagroups/testSchemaGroup1 
```
