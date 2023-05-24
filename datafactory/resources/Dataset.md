Dataset resource type.
API Version: 2018-06-01.
Previous API Version: 2018-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Datasets_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var dataset = new AzureNative.DataFactory.Dataset("dataset", new()
    {
        DatasetName = "exampleDataset",
        FactoryName = "exampleFactoryName",
        Properties = new AzureNative.DataFactory.Inputs.AzureBlobDatasetArgs
        {
            FileName = 
            {
                { "type", "Expression" },
                { "value", "@dataset().MyFileName" },
            },
            FolderPath = 
            {
                { "type", "Expression" },
                { "value", "@dataset().MyFolderPath" },
            },
            Format = new AzureNative.DataFactory.Inputs.TextFormatArgs
            {
                Type = "TextFormat",
            },
            LinkedServiceName = new AzureNative.DataFactory.Inputs.LinkedServiceReferenceArgs
            {
                ReferenceName = "exampleLinkedService",
                Type = "LinkedServiceReference",
            },
            Parameters = 
            {
                { "MyFileName", new AzureNative.DataFactory.Inputs.ParameterSpecificationArgs
                {
                    Type = "String",
                } },
                { "MyFolderPath", new AzureNative.DataFactory.Inputs.ParameterSpecificationArgs
                {
                    Type = "String",
                } },
            },
            Type = "AzureBlob",
        },
        ResourceGroupName = "exampleResourceGroup",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.datafactory.Dataset;
import com.pulumi.azurenative.datafactory.DatasetArgs;
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
        var dataset = new Dataset("dataset", DatasetArgs.builder()        
            .datasetName("exampleDataset")
            .factoryName("exampleFactoryName")
            .properties(Map.ofEntries(
                Map.entry("fileName", AmazonMWSObjectDatasetArgs.builder()
                    .type("Expression")
                    .value("@dataset().MyFileName")
                    .build()),
                Map.entry("folderPath", AmazonMWSObjectDatasetArgs.builder()
                    .type("Expression")
                    .value("@dataset().MyFolderPath")
                    .build()),
                Map.entry("format", Map.of("type", "TextFormat")),
                Map.entry("linkedServiceName", Map.ofEntries(
                    Map.entry("referenceName", "exampleLinkedService"),
                    Map.entry("type", "LinkedServiceReference")
                )),
                Map.entry("parameters", Map.ofEntries(
                    Map.entry("MyFileName", Map.of("type", "String")),
                    Map.entry("MyFolderPath", Map.of("type", "String"))
                )),
                Map.entry("type", "AzureBlob")
            ))
            .resourceGroupName("exampleResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const dataset = new azure_native.datafactory.Dataset("dataset", {
    datasetName: "exampleDataset",
    factoryName: "exampleFactoryName",
    properties: {
        fileName: {
            type: "Expression",
            value: "@dataset().MyFileName",
        },
        folderPath: {
            type: "Expression",
            value: "@dataset().MyFolderPath",
        },
        format: {
            type: "TextFormat",
        },
        linkedServiceName: {
            referenceName: "exampleLinkedService",
            type: "LinkedServiceReference",
        },
        parameters: {
            MyFileName: {
                type: "String",
            },
            MyFolderPath: {
                type: "String",
            },
        },
        type: "AzureBlob",
    },
    resourceGroupName: "exampleResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

dataset = azure_native.datafactory.Dataset("dataset",
    dataset_name="exampleDataset",
    factory_name="exampleFactoryName",
    properties=azure_native.datafactory.AzureBlobDatasetArgs(
        file_name={
            "type": "Expression",
            "value": "@dataset().MyFileName",
        },
        folder_path={
            "type": "Expression",
            "value": "@dataset().MyFolderPath",
        },
        format=azure_native.datafactory.TextFormatArgs(
            type="TextFormat",
        ),
        linked_service_name=azure_native.datafactory.LinkedServiceReferenceArgs(
            reference_name="exampleLinkedService",
            type="LinkedServiceReference",
        ),
        parameters={
            "MyFileName": azure_native.datafactory.ParameterSpecificationArgs(
                type="String",
            ),
            "MyFolderPath": azure_native.datafactory.ParameterSpecificationArgs(
                type="String",
            ),
        },
        type="AzureBlob",
    ),
    resource_group_name="exampleResourceGroup")

```

```yaml
resources:
  dataset:
    type: azure-native:datafactory:Dataset
    properties:
      datasetName: exampleDataset
      factoryName: exampleFactoryName
      properties:
        fileName:
          type: Expression
          value: '@dataset().MyFileName'
        folderPath:
          type: Expression
          value: '@dataset().MyFolderPath'
        format:
          type: TextFormat
        linkedServiceName:
          referenceName: exampleLinkedService
          type: LinkedServiceReference
        parameters:
          MyFileName:
            type: String
          MyFolderPath:
            type: String
        type: AzureBlob
      resourceGroupName: exampleResourceGroup

```

{{% /example %}}
{{% example %}}
### Datasets_Update
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var dataset = new AzureNative.DataFactory.Dataset("dataset", new()
    {
        DatasetName = "exampleDataset",
        FactoryName = "exampleFactoryName",
        Properties = new AzureNative.DataFactory.Inputs.AzureBlobDatasetArgs
        {
            Description = "Example description",
            FileName = 
            {
                { "type", "Expression" },
                { "value", "@dataset().MyFileName" },
            },
            FolderPath = 
            {
                { "type", "Expression" },
                { "value", "@dataset().MyFolderPath" },
            },
            Format = new AzureNative.DataFactory.Inputs.TextFormatArgs
            {
                Type = "TextFormat",
            },
            LinkedServiceName = new AzureNative.DataFactory.Inputs.LinkedServiceReferenceArgs
            {
                ReferenceName = "exampleLinkedService",
                Type = "LinkedServiceReference",
            },
            Parameters = 
            {
                { "MyFileName", new AzureNative.DataFactory.Inputs.ParameterSpecificationArgs
                {
                    Type = "String",
                } },
                { "MyFolderPath", new AzureNative.DataFactory.Inputs.ParameterSpecificationArgs
                {
                    Type = "String",
                } },
            },
            Type = "AzureBlob",
        },
        ResourceGroupName = "exampleResourceGroup",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.datafactory.Dataset;
import com.pulumi.azurenative.datafactory.DatasetArgs;
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
        var dataset = new Dataset("dataset", DatasetArgs.builder()        
            .datasetName("exampleDataset")
            .factoryName("exampleFactoryName")
            .properties(Map.ofEntries(
                Map.entry("description", "Example description"),
                Map.entry("fileName", AmazonMWSObjectDatasetArgs.builder()
                    .type("Expression")
                    .value("@dataset().MyFileName")
                    .build()),
                Map.entry("folderPath", AmazonMWSObjectDatasetArgs.builder()
                    .type("Expression")
                    .value("@dataset().MyFolderPath")
                    .build()),
                Map.entry("format", Map.of("type", "TextFormat")),
                Map.entry("linkedServiceName", Map.ofEntries(
                    Map.entry("referenceName", "exampleLinkedService"),
                    Map.entry("type", "LinkedServiceReference")
                )),
                Map.entry("parameters", Map.ofEntries(
                    Map.entry("MyFileName", Map.of("type", "String")),
                    Map.entry("MyFolderPath", Map.of("type", "String"))
                )),
                Map.entry("type", "AzureBlob")
            ))
            .resourceGroupName("exampleResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const dataset = new azure_native.datafactory.Dataset("dataset", {
    datasetName: "exampleDataset",
    factoryName: "exampleFactoryName",
    properties: {
        description: "Example description",
        fileName: {
            type: "Expression",
            value: "@dataset().MyFileName",
        },
        folderPath: {
            type: "Expression",
            value: "@dataset().MyFolderPath",
        },
        format: {
            type: "TextFormat",
        },
        linkedServiceName: {
            referenceName: "exampleLinkedService",
            type: "LinkedServiceReference",
        },
        parameters: {
            MyFileName: {
                type: "String",
            },
            MyFolderPath: {
                type: "String",
            },
        },
        type: "AzureBlob",
    },
    resourceGroupName: "exampleResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

dataset = azure_native.datafactory.Dataset("dataset",
    dataset_name="exampleDataset",
    factory_name="exampleFactoryName",
    properties=azure_native.datafactory.AzureBlobDatasetArgs(
        description="Example description",
        file_name={
            "type": "Expression",
            "value": "@dataset().MyFileName",
        },
        folder_path={
            "type": "Expression",
            "value": "@dataset().MyFolderPath",
        },
        format=azure_native.datafactory.TextFormatArgs(
            type="TextFormat",
        ),
        linked_service_name=azure_native.datafactory.LinkedServiceReferenceArgs(
            reference_name="exampleLinkedService",
            type="LinkedServiceReference",
        ),
        parameters={
            "MyFileName": azure_native.datafactory.ParameterSpecificationArgs(
                type="String",
            ),
            "MyFolderPath": azure_native.datafactory.ParameterSpecificationArgs(
                type="String",
            ),
        },
        type="AzureBlob",
    ),
    resource_group_name="exampleResourceGroup")

```

```yaml
resources:
  dataset:
    type: azure-native:datafactory:Dataset
    properties:
      datasetName: exampleDataset
      factoryName: exampleFactoryName
      properties:
        description: Example description
        fileName:
          type: Expression
          value: '@dataset().MyFileName'
        folderPath:
          type: Expression
          value: '@dataset().MyFolderPath'
        format:
          type: TextFormat
        linkedServiceName:
          referenceName: exampleLinkedService
          type: LinkedServiceReference
        parameters:
          MyFileName:
            type: String
          MyFolderPath:
            type: String
        type: AzureBlob
      resourceGroupName: exampleResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:datafactory:Dataset exampleDataset /subscriptions/12345678-1234-1234-1234-12345678abc/resourceGroups/exampleResourceGroup/providers/Microsoft.DataFactory/factories/exampleFactoryName/datasets/exampleDataset 
```
