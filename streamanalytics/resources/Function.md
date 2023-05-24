A function object, containing all information associated with the named function. All functions are contained under a streaming job.
API Version: 2020-03-01.
Previous API Version: 2016-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a JavaScript function
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var function = new AzureNative.StreamAnalytics.Function("function", new()
    {
        FunctionName = "function8197",
        JobName = "sj8653",
        Properties = new AzureNative.StreamAnalytics.Inputs.ScalarFunctionPropertiesArgs
        {
            Binding = new AzureNative.StreamAnalytics.Inputs.JavaScriptFunctionBindingArgs
            {
                Script = "function (x, y) { return x + y; }",
                Type = "Microsoft.StreamAnalytics/JavascriptUdf",
            },
            Inputs = new[]
            {
                new AzureNative.StreamAnalytics.Inputs.FunctionInputArgs
                {
                    DataType = "Any",
                },
            },
            Output = new AzureNative.StreamAnalytics.Inputs.FunctionOutputArgs
            {
                DataType = "Any",
            },
            Type = "Scalar",
        },
        ResourceGroupName = "sjrg1637",
    });

});


```

```go
package main

import (
	streamanalytics "github.com/pulumi/pulumi-azure-native-sdk/streamanalytics"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := streamanalytics.NewFunction(ctx, "function", &streamanalytics.FunctionArgs{
			FunctionName: pulumi.String("function8197"),
			JobName:      pulumi.String("sj8653"),
			Properties: streamanalytics.ScalarFunctionProperties{
				Binding: streamanalytics.JavaScriptFunctionBinding{
					Script: "function (x, y) { return x + y; }",
					Type:   "Microsoft.StreamAnalytics/JavascriptUdf",
				},
				Inputs: []streamanalytics.FunctionInputType{
					{
						DataType: "Any",
					},
				},
				Output: streamanalytics.FunctionOutputType{
					DataType: "Any",
				},
				Type: "Scalar",
			},
			ResourceGroupName: pulumi.String("sjrg1637"),
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
import com.pulumi.azurenative.streamanalytics.Function;
import com.pulumi.azurenative.streamanalytics.FunctionArgs;
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
        var function = new Function("function", FunctionArgs.builder()        
            .functionName("function8197")
            .jobName("sj8653")
            .properties(Map.ofEntries(
                Map.entry("binding", Map.ofEntries(
                    Map.entry("script", "function (x, y) { return x + y; }"),
                    Map.entry("type", "Microsoft.StreamAnalytics/JavascriptUdf")
                )),
                Map.entry("inputs", Map.of("dataType", "Any")),
                Map.entry("output", Map.of("dataType", "Any")),
                Map.entry("type", "Scalar")
            ))
            .resourceGroupName("sjrg1637")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const _function = new azure_native.streamanalytics.Function("function", {
    functionName: "function8197",
    jobName: "sj8653",
    properties: {
        binding: {
            script: "function (x, y) { return x + y; }",
            type: "Microsoft.StreamAnalytics/JavascriptUdf",
        },
        inputs: [{
            dataType: "Any",
        }],
        output: {
            dataType: "Any",
        },
        type: "Scalar",
    },
    resourceGroupName: "sjrg1637",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

function = azure_native.streamanalytics.Function("function",
    function_name="function8197",
    job_name="sj8653",
    properties=azure_native.streamanalytics.ScalarFunctionPropertiesArgs(
        binding=azure_native.streamanalytics.JavaScriptFunctionBindingArgs(
            script="function (x, y) { return x + y; }",
            type="Microsoft.StreamAnalytics/JavascriptUdf",
        ),
        inputs=[azure_native.streamanalytics.FunctionInputArgs(
            data_type="Any",
        )],
        output=azure_native.streamanalytics.FunctionOutputArgs(
            data_type="Any",
        ),
        type="Scalar",
    ),
    resource_group_name="sjrg1637")

```

```yaml
resources:
  function:
    type: azure-native:streamanalytics:Function
    properties:
      functionName: function8197
      jobName: sj8653
      properties:
        binding:
          script: function (x, y) { return x + y; }
          type: Microsoft.StreamAnalytics/JavascriptUdf
        inputs:
          - dataType: Any
        output:
          dataType: Any
        type: Scalar
      resourceGroupName: sjrg1637

```

{{% /example %}}
{{% example %}}
### Create an Azure ML function
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var function = new AzureNative.StreamAnalytics.Function("function", new()
    {
        FunctionName = "function588",
        JobName = "sj9093",
        Properties = new AzureNative.StreamAnalytics.Inputs.ScalarFunctionPropertiesArgs
        {
            Binding = new AzureNative.StreamAnalytics.Inputs.AzureMachineLearningWebServiceFunctionBindingArgs
            {
                ApiKey = "someApiKey==",
                BatchSize = 1000,
                Endpoint = "someAzureMLEndpointURL",
                Inputs = new AzureNative.StreamAnalytics.Inputs.AzureMachineLearningWebServiceInputsArgs
                {
                    ColumnNames = new[]
                    {
                        new AzureNative.StreamAnalytics.Inputs.AzureMachineLearningWebServiceInputColumnArgs
                        {
                            DataType = "string",
                            MapTo = 0,
                            Name = "tweet",
                        },
                    },
                    Name = "input1",
                },
                Outputs = new[]
                {
                    new AzureNative.StreamAnalytics.Inputs.AzureMachineLearningWebServiceOutputColumnArgs
                    {
                        DataType = "string",
                        Name = "Sentiment",
                    },
                },
                Type = "Microsoft.MachineLearning/WebService",
            },
            Inputs = new[]
            {
                new AzureNative.StreamAnalytics.Inputs.FunctionInputArgs
                {
                    DataType = "nvarchar(max)",
                },
            },
            Output = new AzureNative.StreamAnalytics.Inputs.FunctionOutputArgs
            {
                DataType = "nvarchar(max)",
            },
            Type = "Scalar",
        },
        ResourceGroupName = "sjrg7",
    });

});


```

```go
package main

import (
	streamanalytics "github.com/pulumi/pulumi-azure-native-sdk/streamanalytics"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := streamanalytics.NewFunction(ctx, "function", &streamanalytics.FunctionArgs{
			FunctionName: pulumi.String("function588"),
			JobName:      pulumi.String("sj9093"),
			Properties: streamanalytics.ScalarFunctionProperties{
				Binding: streamanalytics.AzureMachineLearningWebServiceFunctionBinding{
					ApiKey:    "someApiKey==",
					BatchSize: 1000,
					Endpoint:  "someAzureMLEndpointURL",
					Inputs: streamanalytics.AzureMachineLearningWebServiceInputs{
						ColumnNames: []streamanalytics.AzureMachineLearningWebServiceInputColumn{
							{
								DataType: "string",
								MapTo:    0,
								Name:     "tweet",
							},
						},
						Name: "input1",
					},
					Outputs: []streamanalytics.AzureMachineLearningWebServiceOutputColumn{
						{
							DataType: "string",
							Name:     "Sentiment",
						},
					},
					Type: "Microsoft.MachineLearning/WebService",
				},
				Inputs: []streamanalytics.FunctionInputType{
					{
						DataType: "nvarchar(max)",
					},
				},
				Output: streamanalytics.FunctionOutputType{
					DataType: "nvarchar(max)",
				},
				Type: "Scalar",
			},
			ResourceGroupName: pulumi.String("sjrg7"),
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
import com.pulumi.azurenative.streamanalytics.Function;
import com.pulumi.azurenative.streamanalytics.FunctionArgs;
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
        var function = new Function("function", FunctionArgs.builder()        
            .functionName("function588")
            .jobName("sj9093")
            .properties(Map.ofEntries(
                Map.entry("binding", Map.ofEntries(
                    Map.entry("apiKey", "someApiKey=="),
                    Map.entry("batchSize", 1000),
                    Map.entry("endpoint", "someAzureMLEndpointURL"),
                    Map.entry("inputs", Map.ofEntries(
                        Map.entry("columnNames", Map.ofEntries(
                            Map.entry("dataType", "string"),
                            Map.entry("mapTo", 0),
                            Map.entry("name", "tweet")
                        )),
                        Map.entry("name", "input1")
                    )),
                    Map.entry("outputs", Map.ofEntries(
                        Map.entry("dataType", "string"),
                        Map.entry("name", "Sentiment")
                    )),
                    Map.entry("type", "Microsoft.MachineLearning/WebService")
                )),
                Map.entry("inputs", Map.of("dataType", "nvarchar(max)")),
                Map.entry("output", Map.of("dataType", "nvarchar(max)")),
                Map.entry("type", "Scalar")
            ))
            .resourceGroupName("sjrg7")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const _function = new azure_native.streamanalytics.Function("function", {
    functionName: "function588",
    jobName: "sj9093",
    properties: {
        binding: {
            apiKey: "someApiKey==",
            batchSize: 1000,
            endpoint: "someAzureMLEndpointURL",
            inputs: {
                columnNames: [{
                    dataType: "string",
                    mapTo: 0,
                    name: "tweet",
                }],
                name: "input1",
            },
            outputs: [{
                dataType: "string",
                name: "Sentiment",
            }],
            type: "Microsoft.MachineLearning/WebService",
        },
        inputs: [{
            dataType: "nvarchar(max)",
        }],
        output: {
            dataType: "nvarchar(max)",
        },
        type: "Scalar",
    },
    resourceGroupName: "sjrg7",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

function = azure_native.streamanalytics.Function("function",
    function_name="function588",
    job_name="sj9093",
    properties=azure_native.streamanalytics.ScalarFunctionPropertiesArgs(
        binding=azure_native.streamanalytics.AzureMachineLearningWebServiceFunctionBindingArgs(
            api_key="someApiKey==",
            batch_size=1000,
            endpoint="someAzureMLEndpointURL",
            inputs=azure_native.streamanalytics.AzureMachineLearningWebServiceInputsArgs(
                column_names=[azure_native.streamanalytics.AzureMachineLearningWebServiceInputColumnArgs(
                    data_type="string",
                    map_to=0,
                    name="tweet",
                )],
                name="input1",
            ),
            outputs=[azure_native.streamanalytics.AzureMachineLearningWebServiceOutputColumnArgs(
                data_type="string",
                name="Sentiment",
            )],
            type="Microsoft.MachineLearning/WebService",
        ),
        inputs=[azure_native.streamanalytics.FunctionInputArgs(
            data_type="nvarchar(max)",
        )],
        output=azure_native.streamanalytics.FunctionOutputArgs(
            data_type="nvarchar(max)",
        ),
        type="Scalar",
    ),
    resource_group_name="sjrg7")

```

```yaml
resources:
  function:
    type: azure-native:streamanalytics:Function
    properties:
      functionName: function588
      jobName: sj9093
      properties:
        binding:
          apiKey: someApiKey==
          batchSize: 1000
          endpoint: someAzureMLEndpointURL
          inputs:
            columnNames:
              - dataType: string
                mapTo: 0
                name: tweet
            name: input1
          outputs:
            - dataType: string
              name: Sentiment
          type: Microsoft.MachineLearning/WebService
        inputs:
          - dataType: nvarchar(max)
        output:
          dataType: nvarchar(max)
        type: Scalar
      resourceGroupName: sjrg7

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:streamanalytics:Function function588 /subscriptions/56b5e0a9-b645-407d-99b0-c64f86013e3d/resourceGroups/sjrg7/providers/Microsoft.StreamAnalytics/streamingjobs/sj9093/functions/function588 
```
