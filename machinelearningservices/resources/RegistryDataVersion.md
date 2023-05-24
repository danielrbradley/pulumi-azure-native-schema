Azure Resource Manager resource envelope.
API Version: 2023-04-01.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrUpdate Registry Data Version Base.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var registryDataVersion = new AzureNative.MachineLearningServices.RegistryDataVersion("registryDataVersion", new()
    {
        DataVersionBaseProperties = new AzureNative.MachineLearningServices.Inputs.MLTableDataArgs
        {
            DataType = "mltable",
            DataUri = "string",
            Description = "string",
            IsAnonymous = false,
            IsArchived = false,
            Properties = 
            {
                { "string", "string" },
            },
            ReferencedUris = new[]
            {
                "string",
            },
            Tags = 
            {
                { "string", "string" },
            },
        },
        Name = "string",
        RegistryName = "registryName",
        ResourceGroupName = "test-rg",
        Version = "string",
    });

});


```

```go
package main

import (
	machinelearningservices "github.com/pulumi/pulumi-azure-native-sdk/machinelearningservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := machinelearningservices.NewRegistryDataVersion(ctx, "registryDataVersion", &machinelearningservices.RegistryDataVersionArgs{
			DataVersionBaseProperties: machinelearningservices.MLTableData{
				DataType:    "mltable",
				DataUri:     "string",
				Description: "string",
				IsAnonymous: false,
				IsArchived:  false,
				Properties: map[string]interface{}{
					"string": "string",
				},
				ReferencedUris: []string{
					"string",
				},
				Tags: map[string]interface{}{
					"string": "string",
				},
			},
			Name:              pulumi.String("string"),
			RegistryName:      pulumi.String("registryName"),
			ResourceGroupName: pulumi.String("test-rg"),
			Version:           pulumi.String("string"),
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
import com.pulumi.azurenative.machinelearningservices.RegistryDataVersion;
import com.pulumi.azurenative.machinelearningservices.RegistryDataVersionArgs;
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
        var registryDataVersion = new RegistryDataVersion("registryDataVersion", RegistryDataVersionArgs.builder()        
            .dataVersionBaseProperties(Map.ofEntries(
                Map.entry("dataType", "mltable"),
                Map.entry("dataUri", "string"),
                Map.entry("description", "string"),
                Map.entry("isAnonymous", false),
                Map.entry("isArchived", false),
                Map.entry("properties", MLTableDataArgs.builder()
                    .string("string")
                    .build()),
                Map.entry("referencedUris", "string"),
                Map.entry("tags", MLTableDataArgs.builder()
                    .string("string")
                    .build())
            ))
            .name("string")
            .registryName("registryName")
            .resourceGroupName("test-rg")
            .version("string")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const registryDataVersion = new azure_native.machinelearningservices.RegistryDataVersion("registryDataVersion", {
    dataVersionBaseProperties: {
        dataType: "mltable",
        dataUri: "string",
        description: "string",
        isAnonymous: false,
        isArchived: false,
        properties: {
            string: "string",
        },
        referencedUris: ["string"],
        tags: {
            string: "string",
        },
    },
    name: "string",
    registryName: "registryName",
    resourceGroupName: "test-rg",
    version: "string",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

registry_data_version = azure_native.machinelearningservices.RegistryDataVersion("registryDataVersion",
    data_version_base_properties=azure_native.machinelearningservices.MLTableDataArgs(
        data_type="mltable",
        data_uri="string",
        description="string",
        is_anonymous=False,
        is_archived=False,
        properties={
            "string": "string",
        },
        referenced_uris=["string"],
        tags={
            "string": "string",
        },
    ),
    name="string",
    registry_name="registryName",
    resource_group_name="test-rg",
    version="string")

```

```yaml
resources:
  registryDataVersion:
    type: azure-native:machinelearningservices:RegistryDataVersion
    properties:
      dataVersionBaseProperties:
        dataType: mltable
        dataUri: string
        description: string
        isAnonymous: false
        isArchived: false
        properties:
          string: string
        referencedUris:
          - string
        tags:
          string: string
      name: string
      registryName: registryName
      resourceGroupName: test-rg
      version: string

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:machinelearningservices:RegistryDataVersion string string 
```
