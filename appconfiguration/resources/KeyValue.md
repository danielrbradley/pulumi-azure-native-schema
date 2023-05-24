The key-value resource along with all resource properties.
API Version: 2022-05-01.
Previous API Version: 2020-07-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### KeyValues_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var keyValue = new AzureNative.AppConfiguration.KeyValue("keyValue", new()
    {
        ConfigStoreName = "contoso",
        KeyValueName = "myKey$myLabel",
        ResourceGroupName = "myResourceGroup",
        Tags = 
        {
            { "tag1", "tagValue1" },
            { "tag2", "tagValue2" },
        },
        Value = "myValue",
    });

});


```

```go
package main

import (
	appconfiguration "github.com/pulumi/pulumi-azure-native-sdk/appconfiguration"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := appconfiguration.NewKeyValue(ctx, "keyValue", &appconfiguration.KeyValueArgs{
			ConfigStoreName:   pulumi.String("contoso"),
			KeyValueName:      pulumi.String("myKey$myLabel"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			Tags: pulumi.StringMap{
				"tag1": pulumi.String("tagValue1"),
				"tag2": pulumi.String("tagValue2"),
			},
			Value: pulumi.String("myValue"),
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
import com.pulumi.azurenative.appconfiguration.KeyValue;
import com.pulumi.azurenative.appconfiguration.KeyValueArgs;
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
        var keyValue = new KeyValue("keyValue", KeyValueArgs.builder()        
            .configStoreName("contoso")
            .keyValueName("myKey$myLabel")
            .resourceGroupName("myResourceGroup")
            .tags(Map.ofEntries(
                Map.entry("tag1", "tagValue1"),
                Map.entry("tag2", "tagValue2")
            ))
            .value("myValue")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const keyValue = new azure_native.appconfiguration.KeyValue("keyValue", {
    configStoreName: "contoso",
    keyValueName: "myKey$myLabel",
    resourceGroupName: "myResourceGroup",
    tags: {
        tag1: "tagValue1",
        tag2: "tagValue2",
    },
    value: "myValue",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

key_value = azure_native.appconfiguration.KeyValue("keyValue",
    config_store_name="contoso",
    key_value_name="myKey$myLabel",
    resource_group_name="myResourceGroup",
    tags={
        "tag1": "tagValue1",
        "tag2": "tagValue2",
    },
    value="myValue")

```

```yaml
resources:
  keyValue:
    type: azure-native:appconfiguration:KeyValue
    properties:
      configStoreName: contoso
      keyValueName: myKey$myLabel
      resourceGroupName: myResourceGroup
      tags:
        tag1: tagValue1
        tag2: tagValue2
      value: myValue

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:appconfiguration:KeyValue myKey$myLabel /subscriptions/c80fb759-c965-4c6a-9110-9b2b2d038882/resourceGroups/myResourceGroup/providers/Microsoft.AppConfiguration/configurationStores/contoso/keyValues/myKey$myLabel 
```
