Data flow resource type.
API Version: 2018-06-01.
Previous API Version: 2018-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### DataFlows_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var dataFlow = new AzureNative.DataFactory.DataFlow("dataFlow", new()
    {
        DataFlowName = "exampleDataFlow",
        FactoryName = "exampleFactoryName",
        Properties = new AzureNative.DataFactory.Inputs.MappingDataFlowArgs
        {
            Description = "Sample demo data flow to convert currencies showing usage of union, derive and conditional split transformation.",
            ScriptLines = new[]
            {
                "source(output(",
                "PreviousConversionRate as double,",
                "Country as string,",
                "DateTime1 as string,",
                "CurrentConversionRate as double",
                "),",
                "allowSchemaDrift: false,",
                "validateSchema: false) ~> USDCurrency",
                "source(output(",
                "PreviousConversionRate as double,",
                "Country as string,",
                "DateTime1 as string,",
                "CurrentConversionRate as double",
                "),",
                "allowSchemaDrift: true,",
                "validateSchema: false) ~> CADSource",
                "USDCurrency, CADSource union(byName: true)~> Union",
                "Union derive(NewCurrencyRate = round(CurrentConversionRate*1.25)) ~> NewCurrencyColumn",
                "NewCurrencyColumn split(Country == 'USD',",
                "Country == 'CAD',disjoint: false) ~> ConditionalSplit1@(USD, CAD)",
                "ConditionalSplit1@USD sink(saveMode:'overwrite' ) ~> USDSink",
                "ConditionalSplit1@CAD sink(saveMode:'overwrite' ) ~> CADSink",
            },
            Sinks = new[]
            {
                new AzureNative.DataFactory.Inputs.DataFlowSinkArgs
                {
                    Dataset = new AzureNative.DataFactory.Inputs.DatasetReferenceArgs
                    {
                        ReferenceName = "USDOutput",
                        Type = "DatasetReference",
                    },
                    Name = "USDSink",
                },
                new AzureNative.DataFactory.Inputs.DataFlowSinkArgs
                {
                    Dataset = new AzureNative.DataFactory.Inputs.DatasetReferenceArgs
                    {
                        ReferenceName = "CADOutput",
                        Type = "DatasetReference",
                    },
                    Name = "CADSink",
                },
            },
            Sources = new[]
            {
                new AzureNative.DataFactory.Inputs.DataFlowSourceArgs
                {
                    Dataset = new AzureNative.DataFactory.Inputs.DatasetReferenceArgs
                    {
                        ReferenceName = "CurrencyDatasetUSD",
                        Type = "DatasetReference",
                    },
                    Name = "USDCurrency",
                },
                new AzureNative.DataFactory.Inputs.DataFlowSourceArgs
                {
                    Dataset = new AzureNative.DataFactory.Inputs.DatasetReferenceArgs
                    {
                        ReferenceName = "CurrencyDatasetCAD",
                        Type = "DatasetReference",
                    },
                    Name = "CADSource",
                },
            },
            Type = "MappingDataFlow",
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
		_, err := datafactory.NewDataFlow(ctx, "dataFlow", &datafactory.DataFlowArgs{
			DataFlowName: pulumi.String("exampleDataFlow"),
			FactoryName:  pulumi.String("exampleFactoryName"),
			Properties: datafactory.MappingDataFlow{
				Description: "Sample demo data flow to convert currencies showing usage of union, derive and conditional split transformation.",
				ScriptLines: []string{
					"source(output(",
					"PreviousConversionRate as double,",
					"Country as string,",
					"DateTime1 as string,",
					"CurrentConversionRate as double",
					"),",
					"allowSchemaDrift: false,",
					"validateSchema: false) ~> USDCurrency",
					"source(output(",
					"PreviousConversionRate as double,",
					"Country as string,",
					"DateTime1 as string,",
					"CurrentConversionRate as double",
					"),",
					"allowSchemaDrift: true,",
					"validateSchema: false) ~> CADSource",
					"USDCurrency, CADSource union(byName: true)~> Union",
					"Union derive(NewCurrencyRate = round(CurrentConversionRate*1.25)) ~> NewCurrencyColumn",
					"NewCurrencyColumn split(Country == 'USD',",
					"Country == 'CAD',disjoint: false) ~> ConditionalSplit1@(USD, CAD)",
					"ConditionalSplit1@USD sink(saveMode:'overwrite' ) ~> USDSink",
					"ConditionalSplit1@CAD sink(saveMode:'overwrite' ) ~> CADSink",
				},
				Sinks: []datafactory.DataFlowSink{
					{
						Dataset: {
							ReferenceName: "USDOutput",
							Type:          "DatasetReference",
						},
						Name: "USDSink",
					},
					{
						Dataset: {
							ReferenceName: "CADOutput",
							Type:          "DatasetReference",
						},
						Name: "CADSink",
					},
				},
				Sources: []datafactory.DataFlowSource{
					{
						Dataset: {
							ReferenceName: "CurrencyDatasetUSD",
							Type:          "DatasetReference",
						},
						Name: "USDCurrency",
					},
					{
						Dataset: {
							ReferenceName: "CurrencyDatasetCAD",
							Type:          "DatasetReference",
						},
						Name: "CADSource",
					},
				},
				Type: "MappingDataFlow",
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
import com.pulumi.azurenative.datafactory.DataFlow;
import com.pulumi.azurenative.datafactory.DataFlowArgs;
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
        var dataFlow = new DataFlow("dataFlow", DataFlowArgs.builder()        
            .dataFlowName("exampleDataFlow")
            .factoryName("exampleFactoryName")
            .properties(Map.ofEntries(
                Map.entry("description", "Sample demo data flow to convert currencies showing usage of union, derive and conditional split transformation."),
                Map.entry("scriptLines",                 
                    "source(output(",
                    "PreviousConversionRate as double,",
                    "Country as string,",
                    "DateTime1 as string,",
                    "CurrentConversionRate as double",
                    "),",
                    "allowSchemaDrift: false,",
                    "validateSchema: false) ~> USDCurrency",
                    "source(output(",
                    "PreviousConversionRate as double,",
                    "Country as string,",
                    "DateTime1 as string,",
                    "CurrentConversionRate as double",
                    "),",
                    "allowSchemaDrift: true,",
                    "validateSchema: false) ~> CADSource",
                    "USDCurrency, CADSource union(byName: true)~> Union",
                    "Union derive(NewCurrencyRate = round(CurrentConversionRate*1.25)) ~> NewCurrencyColumn",
                    "NewCurrencyColumn split(Country == 'USD',",
                    "Country == 'CAD',disjoint: false) ~> ConditionalSplit1@(USD, CAD)",
                    "ConditionalSplit1@USD sink(saveMode:'overwrite' ) ~> USDSink",
                    "ConditionalSplit1@CAD sink(saveMode:'overwrite' ) ~> CADSink"),
                Map.entry("sinks",                 
                    Map.ofEntries(
                        Map.entry("dataset", Map.ofEntries(
                            Map.entry("referenceName", "USDOutput"),
                            Map.entry("type", "DatasetReference")
                        )),
                        Map.entry("name", "USDSink")
                    ),
                    Map.ofEntries(
                        Map.entry("dataset", Map.ofEntries(
                            Map.entry("referenceName", "CADOutput"),
                            Map.entry("type", "DatasetReference")
                        )),
                        Map.entry("name", "CADSink")
                    )),
                Map.entry("sources",                 
                    Map.ofEntries(
                        Map.entry("dataset", Map.ofEntries(
                            Map.entry("referenceName", "CurrencyDatasetUSD"),
                            Map.entry("type", "DatasetReference")
                        )),
                        Map.entry("name", "USDCurrency")
                    ),
                    Map.ofEntries(
                        Map.entry("dataset", Map.ofEntries(
                            Map.entry("referenceName", "CurrencyDatasetCAD"),
                            Map.entry("type", "DatasetReference")
                        )),
                        Map.entry("name", "CADSource")
                    )),
                Map.entry("type", "MappingDataFlow")
            ))
            .resourceGroupName("exampleResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const dataFlow = new azure_native.datafactory.DataFlow("dataFlow", {
    dataFlowName: "exampleDataFlow",
    factoryName: "exampleFactoryName",
    properties: {
        description: "Sample demo data flow to convert currencies showing usage of union, derive and conditional split transformation.",
        scriptLines: [
            "source(output(",
            "PreviousConversionRate as double,",
            "Country as string,",
            "DateTime1 as string,",
            "CurrentConversionRate as double",
            "),",
            "allowSchemaDrift: false,",
            "validateSchema: false) ~> USDCurrency",
            "source(output(",
            "PreviousConversionRate as double,",
            "Country as string,",
            "DateTime1 as string,",
            "CurrentConversionRate as double",
            "),",
            "allowSchemaDrift: true,",
            "validateSchema: false) ~> CADSource",
            "USDCurrency, CADSource union(byName: true)~> Union",
            "Union derive(NewCurrencyRate = round(CurrentConversionRate*1.25)) ~> NewCurrencyColumn",
            "NewCurrencyColumn split(Country == 'USD',",
            "Country == 'CAD',disjoint: false) ~> ConditionalSplit1@(USD, CAD)",
            "ConditionalSplit1@USD sink(saveMode:'overwrite' ) ~> USDSink",
            "ConditionalSplit1@CAD sink(saveMode:'overwrite' ) ~> CADSink",
        ],
        sinks: [
            {
                dataset: {
                    referenceName: "USDOutput",
                    type: "DatasetReference",
                },
                name: "USDSink",
            },
            {
                dataset: {
                    referenceName: "CADOutput",
                    type: "DatasetReference",
                },
                name: "CADSink",
            },
        ],
        sources: [
            {
                dataset: {
                    referenceName: "CurrencyDatasetUSD",
                    type: "DatasetReference",
                },
                name: "USDCurrency",
            },
            {
                dataset: {
                    referenceName: "CurrencyDatasetCAD",
                    type: "DatasetReference",
                },
                name: "CADSource",
            },
        ],
        type: "MappingDataFlow",
    },
    resourceGroupName: "exampleResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

data_flow = azure_native.datafactory.DataFlow("dataFlow",
    data_flow_name="exampleDataFlow",
    factory_name="exampleFactoryName",
    properties=azure_native.datafactory.MappingDataFlowArgs(
        description="Sample demo data flow to convert currencies showing usage of union, derive and conditional split transformation.",
        script_lines=[
            "source(output(",
            "PreviousConversionRate as double,",
            "Country as string,",
            "DateTime1 as string,",
            "CurrentConversionRate as double",
            "),",
            "allowSchemaDrift: false,",
            "validateSchema: false) ~> USDCurrency",
            "source(output(",
            "PreviousConversionRate as double,",
            "Country as string,",
            "DateTime1 as string,",
            "CurrentConversionRate as double",
            "),",
            "allowSchemaDrift: true,",
            "validateSchema: false) ~> CADSource",
            "USDCurrency, CADSource union(byName: true)~> Union",
            "Union derive(NewCurrencyRate = round(CurrentConversionRate*1.25)) ~> NewCurrencyColumn",
            "NewCurrencyColumn split(Country == 'USD',",
            "Country == 'CAD',disjoint: false) ~> ConditionalSplit1@(USD, CAD)",
            "ConditionalSplit1@USD sink(saveMode:'overwrite' ) ~> USDSink",
            "ConditionalSplit1@CAD sink(saveMode:'overwrite' ) ~> CADSink",
        ],
        sinks=[
            azure_native.datafactory.DataFlowSinkArgs(
                dataset=azure_native.datafactory.DatasetReferenceArgs(
                    reference_name="USDOutput",
                    type="DatasetReference",
                ),
                name="USDSink",
            ),
            azure_native.datafactory.DataFlowSinkArgs(
                dataset=azure_native.datafactory.DatasetReferenceArgs(
                    reference_name="CADOutput",
                    type="DatasetReference",
                ),
                name="CADSink",
            ),
        ],
        sources=[
            azure_native.datafactory.DataFlowSourceArgs(
                dataset=azure_native.datafactory.DatasetReferenceArgs(
                    reference_name="CurrencyDatasetUSD",
                    type="DatasetReference",
                ),
                name="USDCurrency",
            ),
            azure_native.datafactory.DataFlowSourceArgs(
                dataset=azure_native.datafactory.DatasetReferenceArgs(
                    reference_name="CurrencyDatasetCAD",
                    type="DatasetReference",
                ),
                name="CADSource",
            ),
        ],
        type="MappingDataFlow",
    ),
    resource_group_name="exampleResourceGroup")

```

```yaml
resources:
  dataFlow:
    type: azure-native:datafactory:DataFlow
    properties:
      dataFlowName: exampleDataFlow
      factoryName: exampleFactoryName
      properties:
        description: Sample demo data flow to convert currencies showing usage of union, derive and conditional split transformation.
        scriptLines:
          - source(output(
          - PreviousConversionRate as double,
          - Country as string,
          - DateTime1 as string,
          - CurrentConversionRate as double
          - ),
          - 'allowSchemaDrift: false,'
          - 'validateSchema: false) ~> USDCurrency'
          - source(output(
          - PreviousConversionRate as double,
          - Country as string,
          - DateTime1 as string,
          - CurrentConversionRate as double
          - ),
          - 'allowSchemaDrift: true,'
          - 'validateSchema: false) ~> CADSource'
          - 'USDCurrency, CADSource union(byName: true)~> Union'
          - Union derive(NewCurrencyRate = round(CurrentConversionRate*1.25)) ~> NewCurrencyColumn
          - NewCurrencyColumn split(Country == 'USD',
          - 'Country == ''CAD'',disjoint: false) ~> ConditionalSplit1@(USD, CAD)'
          - ConditionalSplit1@USD sink(saveMode:'overwrite' ) ~> USDSink
          - ConditionalSplit1@CAD sink(saveMode:'overwrite' ) ~> CADSink
        sinks:
          - dataset:
              referenceName: USDOutput
              type: DatasetReference
            name: USDSink
          - dataset:
              referenceName: CADOutput
              type: DatasetReference
            name: CADSink
        sources:
          - dataset:
              referenceName: CurrencyDatasetUSD
              type: DatasetReference
            name: USDCurrency
          - dataset:
              referenceName: CurrencyDatasetCAD
              type: DatasetReference
            name: CADSource
        type: MappingDataFlow
      resourceGroupName: exampleResourceGroup

```

{{% /example %}}
{{% example %}}
### DataFlows_Update
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var dataFlow = new AzureNative.DataFactory.DataFlow("dataFlow", new()
    {
        DataFlowName = "exampleDataFlow",
        FactoryName = "exampleFactoryName",
        Properties = new AzureNative.DataFactory.Inputs.MappingDataFlowArgs
        {
            Description = "Sample demo data flow to convert currencies showing usage of union, derive and conditional split transformation.",
            ScriptLines = new[]
            {
                "source(output(",
                "PreviousConversionRate as double,",
                "Country as string,",
                "DateTime1 as string,",
                "CurrentConversionRate as double",
                "),",
                "allowSchemaDrift: false,",
                "validateSchema: false) ~> USDCurrency",
                "source(output(",
                "PreviousConversionRate as double,",
                "Country as string,",
                "DateTime1 as string,",
                "CurrentConversionRate as double",
                "),",
                "allowSchemaDrift: true,",
                "validateSchema: false) ~> CADSource",
                "USDCurrency, CADSource union(byName: true)~> Union",
                "Union derive(NewCurrencyRate = round(CurrentConversionRate*1.25)) ~> NewCurrencyColumn",
                "NewCurrencyColumn split(Country == 'USD',",
                "Country == 'CAD',disjoint: false) ~> ConditionalSplit1@(USD, CAD)",
                "ConditionalSplit1@USD sink(saveMode:'overwrite' ) ~> USDSink",
                "ConditionalSplit1@CAD sink(saveMode:'overwrite' ) ~> CADSink",
            },
            Sinks = new[]
            {
                new AzureNative.DataFactory.Inputs.DataFlowSinkArgs
                {
                    Dataset = new AzureNative.DataFactory.Inputs.DatasetReferenceArgs
                    {
                        ReferenceName = "USDOutput",
                        Type = "DatasetReference",
                    },
                    Name = "USDSink",
                },
                new AzureNative.DataFactory.Inputs.DataFlowSinkArgs
                {
                    Dataset = new AzureNative.DataFactory.Inputs.DatasetReferenceArgs
                    {
                        ReferenceName = "CADOutput",
                        Type = "DatasetReference",
                    },
                    Name = "CADSink",
                },
            },
            Sources = new[]
            {
                new AzureNative.DataFactory.Inputs.DataFlowSourceArgs
                {
                    Dataset = new AzureNative.DataFactory.Inputs.DatasetReferenceArgs
                    {
                        ReferenceName = "CurrencyDatasetUSD",
                        Type = "DatasetReference",
                    },
                    Name = "USDCurrency",
                },
                new AzureNative.DataFactory.Inputs.DataFlowSourceArgs
                {
                    Dataset = new AzureNative.DataFactory.Inputs.DatasetReferenceArgs
                    {
                        ReferenceName = "CurrencyDatasetCAD",
                        Type = "DatasetReference",
                    },
                    Name = "CADSource",
                },
            },
            Type = "MappingDataFlow",
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
		_, err := datafactory.NewDataFlow(ctx, "dataFlow", &datafactory.DataFlowArgs{
			DataFlowName: pulumi.String("exampleDataFlow"),
			FactoryName:  pulumi.String("exampleFactoryName"),
			Properties: datafactory.MappingDataFlow{
				Description: "Sample demo data flow to convert currencies showing usage of union, derive and conditional split transformation.",
				ScriptLines: []string{
					"source(output(",
					"PreviousConversionRate as double,",
					"Country as string,",
					"DateTime1 as string,",
					"CurrentConversionRate as double",
					"),",
					"allowSchemaDrift: false,",
					"validateSchema: false) ~> USDCurrency",
					"source(output(",
					"PreviousConversionRate as double,",
					"Country as string,",
					"DateTime1 as string,",
					"CurrentConversionRate as double",
					"),",
					"allowSchemaDrift: true,",
					"validateSchema: false) ~> CADSource",
					"USDCurrency, CADSource union(byName: true)~> Union",
					"Union derive(NewCurrencyRate = round(CurrentConversionRate*1.25)) ~> NewCurrencyColumn",
					"NewCurrencyColumn split(Country == 'USD',",
					"Country == 'CAD',disjoint: false) ~> ConditionalSplit1@(USD, CAD)",
					"ConditionalSplit1@USD sink(saveMode:'overwrite' ) ~> USDSink",
					"ConditionalSplit1@CAD sink(saveMode:'overwrite' ) ~> CADSink",
				},
				Sinks: []datafactory.DataFlowSink{
					{
						Dataset: {
							ReferenceName: "USDOutput",
							Type:          "DatasetReference",
						},
						Name: "USDSink",
					},
					{
						Dataset: {
							ReferenceName: "CADOutput",
							Type:          "DatasetReference",
						},
						Name: "CADSink",
					},
				},
				Sources: []datafactory.DataFlowSource{
					{
						Dataset: {
							ReferenceName: "CurrencyDatasetUSD",
							Type:          "DatasetReference",
						},
						Name: "USDCurrency",
					},
					{
						Dataset: {
							ReferenceName: "CurrencyDatasetCAD",
							Type:          "DatasetReference",
						},
						Name: "CADSource",
					},
				},
				Type: "MappingDataFlow",
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
import com.pulumi.azurenative.datafactory.DataFlow;
import com.pulumi.azurenative.datafactory.DataFlowArgs;
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
        var dataFlow = new DataFlow("dataFlow", DataFlowArgs.builder()        
            .dataFlowName("exampleDataFlow")
            .factoryName("exampleFactoryName")
            .properties(Map.ofEntries(
                Map.entry("description", "Sample demo data flow to convert currencies showing usage of union, derive and conditional split transformation."),
                Map.entry("scriptLines",                 
                    "source(output(",
                    "PreviousConversionRate as double,",
                    "Country as string,",
                    "DateTime1 as string,",
                    "CurrentConversionRate as double",
                    "),",
                    "allowSchemaDrift: false,",
                    "validateSchema: false) ~> USDCurrency",
                    "source(output(",
                    "PreviousConversionRate as double,",
                    "Country as string,",
                    "DateTime1 as string,",
                    "CurrentConversionRate as double",
                    "),",
                    "allowSchemaDrift: true,",
                    "validateSchema: false) ~> CADSource",
                    "USDCurrency, CADSource union(byName: true)~> Union",
                    "Union derive(NewCurrencyRate = round(CurrentConversionRate*1.25)) ~> NewCurrencyColumn",
                    "NewCurrencyColumn split(Country == 'USD',",
                    "Country == 'CAD',disjoint: false) ~> ConditionalSplit1@(USD, CAD)",
                    "ConditionalSplit1@USD sink(saveMode:'overwrite' ) ~> USDSink",
                    "ConditionalSplit1@CAD sink(saveMode:'overwrite' ) ~> CADSink"),
                Map.entry("sinks",                 
                    Map.ofEntries(
                        Map.entry("dataset", Map.ofEntries(
                            Map.entry("referenceName", "USDOutput"),
                            Map.entry("type", "DatasetReference")
                        )),
                        Map.entry("name", "USDSink")
                    ),
                    Map.ofEntries(
                        Map.entry("dataset", Map.ofEntries(
                            Map.entry("referenceName", "CADOutput"),
                            Map.entry("type", "DatasetReference")
                        )),
                        Map.entry("name", "CADSink")
                    )),
                Map.entry("sources",                 
                    Map.ofEntries(
                        Map.entry("dataset", Map.ofEntries(
                            Map.entry("referenceName", "CurrencyDatasetUSD"),
                            Map.entry("type", "DatasetReference")
                        )),
                        Map.entry("name", "USDCurrency")
                    ),
                    Map.ofEntries(
                        Map.entry("dataset", Map.ofEntries(
                            Map.entry("referenceName", "CurrencyDatasetCAD"),
                            Map.entry("type", "DatasetReference")
                        )),
                        Map.entry("name", "CADSource")
                    )),
                Map.entry("type", "MappingDataFlow")
            ))
            .resourceGroupName("exampleResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const dataFlow = new azure_native.datafactory.DataFlow("dataFlow", {
    dataFlowName: "exampleDataFlow",
    factoryName: "exampleFactoryName",
    properties: {
        description: "Sample demo data flow to convert currencies showing usage of union, derive and conditional split transformation.",
        scriptLines: [
            "source(output(",
            "PreviousConversionRate as double,",
            "Country as string,",
            "DateTime1 as string,",
            "CurrentConversionRate as double",
            "),",
            "allowSchemaDrift: false,",
            "validateSchema: false) ~> USDCurrency",
            "source(output(",
            "PreviousConversionRate as double,",
            "Country as string,",
            "DateTime1 as string,",
            "CurrentConversionRate as double",
            "),",
            "allowSchemaDrift: true,",
            "validateSchema: false) ~> CADSource",
            "USDCurrency, CADSource union(byName: true)~> Union",
            "Union derive(NewCurrencyRate = round(CurrentConversionRate*1.25)) ~> NewCurrencyColumn",
            "NewCurrencyColumn split(Country == 'USD',",
            "Country == 'CAD',disjoint: false) ~> ConditionalSplit1@(USD, CAD)",
            "ConditionalSplit1@USD sink(saveMode:'overwrite' ) ~> USDSink",
            "ConditionalSplit1@CAD sink(saveMode:'overwrite' ) ~> CADSink",
        ],
        sinks: [
            {
                dataset: {
                    referenceName: "USDOutput",
                    type: "DatasetReference",
                },
                name: "USDSink",
            },
            {
                dataset: {
                    referenceName: "CADOutput",
                    type: "DatasetReference",
                },
                name: "CADSink",
            },
        ],
        sources: [
            {
                dataset: {
                    referenceName: "CurrencyDatasetUSD",
                    type: "DatasetReference",
                },
                name: "USDCurrency",
            },
            {
                dataset: {
                    referenceName: "CurrencyDatasetCAD",
                    type: "DatasetReference",
                },
                name: "CADSource",
            },
        ],
        type: "MappingDataFlow",
    },
    resourceGroupName: "exampleResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

data_flow = azure_native.datafactory.DataFlow("dataFlow",
    data_flow_name="exampleDataFlow",
    factory_name="exampleFactoryName",
    properties=azure_native.datafactory.MappingDataFlowArgs(
        description="Sample demo data flow to convert currencies showing usage of union, derive and conditional split transformation.",
        script_lines=[
            "source(output(",
            "PreviousConversionRate as double,",
            "Country as string,",
            "DateTime1 as string,",
            "CurrentConversionRate as double",
            "),",
            "allowSchemaDrift: false,",
            "validateSchema: false) ~> USDCurrency",
            "source(output(",
            "PreviousConversionRate as double,",
            "Country as string,",
            "DateTime1 as string,",
            "CurrentConversionRate as double",
            "),",
            "allowSchemaDrift: true,",
            "validateSchema: false) ~> CADSource",
            "USDCurrency, CADSource union(byName: true)~> Union",
            "Union derive(NewCurrencyRate = round(CurrentConversionRate*1.25)) ~> NewCurrencyColumn",
            "NewCurrencyColumn split(Country == 'USD',",
            "Country == 'CAD',disjoint: false) ~> ConditionalSplit1@(USD, CAD)",
            "ConditionalSplit1@USD sink(saveMode:'overwrite' ) ~> USDSink",
            "ConditionalSplit1@CAD sink(saveMode:'overwrite' ) ~> CADSink",
        ],
        sinks=[
            azure_native.datafactory.DataFlowSinkArgs(
                dataset=azure_native.datafactory.DatasetReferenceArgs(
                    reference_name="USDOutput",
                    type="DatasetReference",
                ),
                name="USDSink",
            ),
            azure_native.datafactory.DataFlowSinkArgs(
                dataset=azure_native.datafactory.DatasetReferenceArgs(
                    reference_name="CADOutput",
                    type="DatasetReference",
                ),
                name="CADSink",
            ),
        ],
        sources=[
            azure_native.datafactory.DataFlowSourceArgs(
                dataset=azure_native.datafactory.DatasetReferenceArgs(
                    reference_name="CurrencyDatasetUSD",
                    type="DatasetReference",
                ),
                name="USDCurrency",
            ),
            azure_native.datafactory.DataFlowSourceArgs(
                dataset=azure_native.datafactory.DatasetReferenceArgs(
                    reference_name="CurrencyDatasetCAD",
                    type="DatasetReference",
                ),
                name="CADSource",
            ),
        ],
        type="MappingDataFlow",
    ),
    resource_group_name="exampleResourceGroup")

```

```yaml
resources:
  dataFlow:
    type: azure-native:datafactory:DataFlow
    properties:
      dataFlowName: exampleDataFlow
      factoryName: exampleFactoryName
      properties:
        description: Sample demo data flow to convert currencies showing usage of union, derive and conditional split transformation.
        scriptLines:
          - source(output(
          - PreviousConversionRate as double,
          - Country as string,
          - DateTime1 as string,
          - CurrentConversionRate as double
          - ),
          - 'allowSchemaDrift: false,'
          - 'validateSchema: false) ~> USDCurrency'
          - source(output(
          - PreviousConversionRate as double,
          - Country as string,
          - DateTime1 as string,
          - CurrentConversionRate as double
          - ),
          - 'allowSchemaDrift: true,'
          - 'validateSchema: false) ~> CADSource'
          - 'USDCurrency, CADSource union(byName: true)~> Union'
          - Union derive(NewCurrencyRate = round(CurrentConversionRate*1.25)) ~> NewCurrencyColumn
          - NewCurrencyColumn split(Country == 'USD',
          - 'Country == ''CAD'',disjoint: false) ~> ConditionalSplit1@(USD, CAD)'
          - ConditionalSplit1@USD sink(saveMode:'overwrite' ) ~> USDSink
          - ConditionalSplit1@CAD sink(saveMode:'overwrite' ) ~> CADSink
        sinks:
          - dataset:
              referenceName: USDOutput
              type: DatasetReference
            name: USDSink
          - dataset:
              referenceName: CADOutput
              type: DatasetReference
            name: CADSink
        sources:
          - dataset:
              referenceName: CurrencyDatasetUSD
              type: DatasetReference
            name: USDCurrency
          - dataset:
              referenceName: CurrencyDatasetCAD
              type: DatasetReference
            name: CADSource
        type: MappingDataFlow
      resourceGroupName: exampleResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:datafactory:DataFlow exampleDataFlow /subscriptions/12345678-1234-1234-1234-12345678abc/resourceGroups/exampleResourceGroup/providers/Microsoft.DataFactory/factories/exampleFactoryName/datasets/exampleDataset 
```
