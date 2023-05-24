A streaming job object, containing all information associated with the named streaming job.
API Version: 2020-03-01.
Previous API Version: 2016-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a complete streaming job (a streaming job with a transformation, at least 1 input and at least 1 output)
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var streamingJob = new AzureNative.StreamAnalytics.StreamingJob("streamingJob", new()
    {
        CompatibilityLevel = "1.0",
        DataLocale = "en-US",
        EventsLateArrivalMaxDelayInSeconds = 5,
        EventsOutOfOrderMaxDelayInSeconds = 0,
        EventsOutOfOrderPolicy = "Drop",
        Functions = new[] {},
        Inputs = new[]
        {
            new AzureNative.StreamAnalytics.Inputs.InputArgs
            {
                Name = "inputtest",
                Properties = new AzureNative.StreamAnalytics.Inputs.StreamInputPropertiesArgs
                {
                    Datasource = new AzureNative.StreamAnalytics.Inputs.BlobStreamInputDataSourceArgs
                    {
                        Container = "containerName",
                        PathPattern = "",
                        StorageAccounts = new[]
                        {
                            new AzureNative.StreamAnalytics.Inputs.StorageAccountArgs
                            {
                                AccountKey = "yourAccountKey==",
                                AccountName = "yourAccountName",
                            },
                        },
                        Type = "Microsoft.Storage/Blob",
                    },
                    Serialization = new AzureNative.StreamAnalytics.Inputs.JsonSerializationArgs
                    {
                        Encoding = "UTF8",
                        Type = "Json",
                    },
                    Type = "Stream",
                },
            },
        },
        JobName = "sj7804",
        Location = "West US",
        OutputErrorPolicy = "Drop",
        Outputs = new[]
        {
            new AzureNative.StreamAnalytics.Inputs.OutputArgs
            {
                Datasource = new AzureNative.StreamAnalytics.Inputs.AzureSqlDatabaseOutputDataSourceArgs
                {
                    Database = "databaseName",
                    Password = "userPassword",
                    Server = "serverName",
                    Table = "tableName",
                    Type = "Microsoft.Sql/Server/Database",
                    User = "<user>",
                },
                Name = "outputtest",
            },
        },
        ResourceGroupName = "sjrg3276",
        Sku = new AzureNative.StreamAnalytics.Inputs.SkuArgs
        {
            Name = "Standard",
        },
        Tags = 
        {
            { "key1", "value1" },
            { "key3", "value3" },
            { "randomKey", "randomValue" },
        },
        Transformation = new AzureNative.StreamAnalytics.Inputs.TransformationArgs
        {
            Name = "transformationtest",
            Query = "Select Id, Name from inputtest",
            StreamingUnits = 1,
        },
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
		_, err := streamanalytics.NewStreamingJob(ctx, "streamingJob", &streamanalytics.StreamingJobArgs{
			CompatibilityLevel:                 pulumi.String("1.0"),
			DataLocale:                         pulumi.String("en-US"),
			EventsLateArrivalMaxDelayInSeconds: pulumi.Int(5),
			EventsOutOfOrderMaxDelayInSeconds:  pulumi.Int(0),
			EventsOutOfOrderPolicy:             pulumi.String("Drop"),
			Functions:                          streamanalytics.FunctionTypeArray{},
			Inputs: []streamanalytics.InputTypeArgs{
				{
					Name: pulumi.String("inputtest"),
					Properties: {
						Datasource: {
							Container:   "containerName",
							PathPattern: "",
							StorageAccounts: []streamanalytics.StorageAccount{
								{
									AccountKey:  "yourAccountKey==",
									AccountName: "yourAccountName",
								},
							},
							Type: "Microsoft.Storage/Blob",
						},
						Serialization: {
							Encoding: "UTF8",
							Type:     "Json",
						},
						Type: "Stream",
					},
				},
			},
			JobName:           pulumi.String("sj7804"),
			Location:          pulumi.String("West US"),
			OutputErrorPolicy: pulumi.String("Drop"),
			Outputs: []streamanalytics.OutputTypeArgs{
				{
					Datasource: {
						Database: "databaseName",
						Password: "userPassword",
						Server:   "serverName",
						Table:    "tableName",
						Type:     "Microsoft.Sql/Server/Database",
						User:     "<user>",
					},
					Name: pulumi.String("outputtest"),
				},
			},
			ResourceGroupName: pulumi.String("sjrg3276"),
			Sku: &streamanalytics.SkuArgs{
				Name: pulumi.String("Standard"),
			},
			Tags: pulumi.StringMap{
				"key1":      pulumi.String("value1"),
				"key3":      pulumi.String("value3"),
				"randomKey": pulumi.String("randomValue"),
			},
			Transformation: &streamanalytics.TransformationArgs{
				Name:           pulumi.String("transformationtest"),
				Query:          pulumi.String("Select Id, Name from inputtest"),
				StreamingUnits: pulumi.Int(1),
			},
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
import com.pulumi.azurenative.streamanalytics.StreamingJob;
import com.pulumi.azurenative.streamanalytics.StreamingJobArgs;
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
        var streamingJob = new StreamingJob("streamingJob", StreamingJobArgs.builder()        
            .compatibilityLevel("1.0")
            .dataLocale("en-US")
            .eventsLateArrivalMaxDelayInSeconds(5)
            .eventsOutOfOrderMaxDelayInSeconds(0)
            .eventsOutOfOrderPolicy("Drop")
            .functions()
            .inputs(Map.ofEntries(
                Map.entry("name", "inputtest"),
                Map.entry("properties", Map.ofEntries(
                    Map.entry("datasource", Map.ofEntries(
                        Map.entry("container", "containerName"),
                        Map.entry("pathPattern", ""),
                        Map.entry("storageAccounts", Map.ofEntries(
                            Map.entry("accountKey", "yourAccountKey=="),
                            Map.entry("accountName", "yourAccountName")
                        )),
                        Map.entry("type", "Microsoft.Storage/Blob")
                    )),
                    Map.entry("serialization", Map.ofEntries(
                        Map.entry("encoding", "UTF8"),
                        Map.entry("type", "Json")
                    )),
                    Map.entry("type", "Stream")
                ))
            ))
            .jobName("sj7804")
            .location("West US")
            .outputErrorPolicy("Drop")
            .outputs(Map.ofEntries(
                Map.entry("datasource", Map.ofEntries(
                    Map.entry("database", "databaseName"),
                    Map.entry("password", "userPassword"),
                    Map.entry("server", "serverName"),
                    Map.entry("table", "tableName"),
                    Map.entry("type", "Microsoft.Sql/Server/Database"),
                    Map.entry("user", "<user>")
                )),
                Map.entry("name", "outputtest")
            ))
            .resourceGroupName("sjrg3276")
            .sku(Map.of("name", "Standard"))
            .tags(Map.ofEntries(
                Map.entry("key1", "value1"),
                Map.entry("key3", "value3"),
                Map.entry("randomKey", "randomValue")
            ))
            .transformation(Map.ofEntries(
                Map.entry("name", "transformationtest"),
                Map.entry("query", "Select Id, Name from inputtest"),
                Map.entry("streamingUnits", 1)
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const streamingJob = new azure_native.streamanalytics.StreamingJob("streamingJob", {
    compatibilityLevel: "1.0",
    dataLocale: "en-US",
    eventsLateArrivalMaxDelayInSeconds: 5,
    eventsOutOfOrderMaxDelayInSeconds: 0,
    eventsOutOfOrderPolicy: "Drop",
    functions: [],
    inputs: [{
        name: "inputtest",
        properties: {
            datasource: {
                container: "containerName",
                pathPattern: "",
                storageAccounts: [{
                    accountKey: "yourAccountKey==",
                    accountName: "yourAccountName",
                }],
                type: "Microsoft.Storage/Blob",
            },
            serialization: {
                encoding: "UTF8",
                type: "Json",
            },
            type: "Stream",
        },
    }],
    jobName: "sj7804",
    location: "West US",
    outputErrorPolicy: "Drop",
    outputs: [{
        datasource: {
            database: "databaseName",
            password: "userPassword",
            server: "serverName",
            table: "tableName",
            type: "Microsoft.Sql/Server/Database",
            user: "<user>",
        },
        name: "outputtest",
    }],
    resourceGroupName: "sjrg3276",
    sku: {
        name: "Standard",
    },
    tags: {
        key1: "value1",
        key3: "value3",
        randomKey: "randomValue",
    },
    transformation: {
        name: "transformationtest",
        query: "Select Id, Name from inputtest",
        streamingUnits: 1,
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

streaming_job = azure_native.streamanalytics.StreamingJob("streamingJob",
    compatibility_level="1.0",
    data_locale="en-US",
    events_late_arrival_max_delay_in_seconds=5,
    events_out_of_order_max_delay_in_seconds=0,
    events_out_of_order_policy="Drop",
    functions=[],
    inputs=[azure_native.streamanalytics.InputArgs(
        name="inputtest",
        properties=azure_native.streamanalytics.StreamInputPropertiesArgs(
            datasource=azure_native.streamanalytics.BlobStreamInputDataSourceArgs(
                container="containerName",
                path_pattern="",
                storage_accounts=[azure_native.streamanalytics.StorageAccountArgs(
                    account_key="yourAccountKey==",
                    account_name="yourAccountName",
                )],
                type="Microsoft.Storage/Blob",
            ),
            serialization=azure_native.streamanalytics.JsonSerializationArgs(
                encoding="UTF8",
                type="Json",
            ),
            type="Stream",
        ),
    )],
    job_name="sj7804",
    location="West US",
    output_error_policy="Drop",
    outputs=[azure_native.streamanalytics.OutputArgs(
        datasource=azure_native.streamanalytics.AzureSqlDatabaseOutputDataSourceArgs(
            database="databaseName",
            password="userPassword",
            server="serverName",
            table="tableName",
            type="Microsoft.Sql/Server/Database",
            user="<user>",
        ),
        name="outputtest",
    )],
    resource_group_name="sjrg3276",
    sku=azure_native.streamanalytics.SkuArgs(
        name="Standard",
    ),
    tags={
        "key1": "value1",
        "key3": "value3",
        "randomKey": "randomValue",
    },
    transformation=azure_native.streamanalytics.TransformationArgs(
        name="transformationtest",
        query="Select Id, Name from inputtest",
        streaming_units=1,
    ))

```

```yaml
resources:
  streamingJob:
    type: azure-native:streamanalytics:StreamingJob
    properties:
      compatibilityLevel: '1.0'
      dataLocale: en-US
      eventsLateArrivalMaxDelayInSeconds: 5
      eventsOutOfOrderMaxDelayInSeconds: 0
      eventsOutOfOrderPolicy: Drop
      functions: []
      inputs:
        - name: inputtest
          properties:
            datasource:
              container: containerName
              pathPattern:
              storageAccounts:
                - accountKey: yourAccountKey==
                  accountName: yourAccountName
              type: Microsoft.Storage/Blob
            serialization:
              encoding: UTF8
              type: Json
            type: Stream
      jobName: sj7804
      location: West US
      outputErrorPolicy: Drop
      outputs:
        - datasource:
            database: databaseName
            password: userPassword
            server: serverName
            table: tableName
            type: Microsoft.Sql/Server/Database
            user: <user>
          name: outputtest
      resourceGroupName: sjrg3276
      sku:
        name: Standard
      tags:
        key1: value1
        key3: value3
        randomKey: randomValue
      transformation:
        name: transformationtest
        query: Select Id, Name from inputtest
        streamingUnits: 1

```

{{% /example %}}
{{% example %}}
### Create a streaming job shell (a streaming job with no inputs, outputs, transformation, or functions)
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var streamingJob = new AzureNative.StreamAnalytics.StreamingJob("streamingJob", new()
    {
        CompatibilityLevel = "1.0",
        DataLocale = "en-US",
        EventsLateArrivalMaxDelayInSeconds = 16,
        EventsOutOfOrderMaxDelayInSeconds = 5,
        EventsOutOfOrderPolicy = "Drop",
        Functions = new[] {},
        Inputs = new[] {},
        JobName = "sj59",
        Location = "West US",
        OutputErrorPolicy = "Drop",
        Outputs = new[] {},
        ResourceGroupName = "sjrg6936",
        Sku = new AzureNative.StreamAnalytics.Inputs.SkuArgs
        {
            Name = "Standard",
        },
        Tags = 
        {
            { "key1", "value1" },
            { "key3", "value3" },
            { "randomKey", "randomValue" },
        },
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
		_, err := streamanalytics.NewStreamingJob(ctx, "streamingJob", &streamanalytics.StreamingJobArgs{
			CompatibilityLevel:                 pulumi.String("1.0"),
			DataLocale:                         pulumi.String("en-US"),
			EventsLateArrivalMaxDelayInSeconds: pulumi.Int(16),
			EventsOutOfOrderMaxDelayInSeconds:  pulumi.Int(5),
			EventsOutOfOrderPolicy:             pulumi.String("Drop"),
			Functions:                          streamanalytics.FunctionTypeArray{},
			Inputs:                             streamanalytics.InputTypeArray{},
			JobName:                            pulumi.String("sj59"),
			Location:                           pulumi.String("West US"),
			OutputErrorPolicy:                  pulumi.String("Drop"),
			Outputs:                            streamanalytics.OutputTypeArray{},
			ResourceGroupName:                  pulumi.String("sjrg6936"),
			Sku: &streamanalytics.SkuArgs{
				Name: pulumi.String("Standard"),
			},
			Tags: pulumi.StringMap{
				"key1":      pulumi.String("value1"),
				"key3":      pulumi.String("value3"),
				"randomKey": pulumi.String("randomValue"),
			},
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
import com.pulumi.azurenative.streamanalytics.StreamingJob;
import com.pulumi.azurenative.streamanalytics.StreamingJobArgs;
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
        var streamingJob = new StreamingJob("streamingJob", StreamingJobArgs.builder()        
            .compatibilityLevel("1.0")
            .dataLocale("en-US")
            .eventsLateArrivalMaxDelayInSeconds(16)
            .eventsOutOfOrderMaxDelayInSeconds(5)
            .eventsOutOfOrderPolicy("Drop")
            .functions()
            .inputs()
            .jobName("sj59")
            .location("West US")
            .outputErrorPolicy("Drop")
            .outputs()
            .resourceGroupName("sjrg6936")
            .sku(Map.of("name", "Standard"))
            .tags(Map.ofEntries(
                Map.entry("key1", "value1"),
                Map.entry("key3", "value3"),
                Map.entry("randomKey", "randomValue")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const streamingJob = new azure_native.streamanalytics.StreamingJob("streamingJob", {
    compatibilityLevel: "1.0",
    dataLocale: "en-US",
    eventsLateArrivalMaxDelayInSeconds: 16,
    eventsOutOfOrderMaxDelayInSeconds: 5,
    eventsOutOfOrderPolicy: "Drop",
    functions: [],
    inputs: [],
    jobName: "sj59",
    location: "West US",
    outputErrorPolicy: "Drop",
    outputs: [],
    resourceGroupName: "sjrg6936",
    sku: {
        name: "Standard",
    },
    tags: {
        key1: "value1",
        key3: "value3",
        randomKey: "randomValue",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

streaming_job = azure_native.streamanalytics.StreamingJob("streamingJob",
    compatibility_level="1.0",
    data_locale="en-US",
    events_late_arrival_max_delay_in_seconds=16,
    events_out_of_order_max_delay_in_seconds=5,
    events_out_of_order_policy="Drop",
    functions=[],
    inputs=[],
    job_name="sj59",
    location="West US",
    output_error_policy="Drop",
    outputs=[],
    resource_group_name="sjrg6936",
    sku=azure_native.streamanalytics.SkuArgs(
        name="Standard",
    ),
    tags={
        "key1": "value1",
        "key3": "value3",
        "randomKey": "randomValue",
    })

```

```yaml
resources:
  streamingJob:
    type: azure-native:streamanalytics:StreamingJob
    properties:
      compatibilityLevel: '1.0'
      dataLocale: en-US
      eventsLateArrivalMaxDelayInSeconds: 16
      eventsOutOfOrderMaxDelayInSeconds: 5
      eventsOutOfOrderPolicy: Drop
      functions: []
      inputs: []
      jobName: sj59
      location: West US
      outputErrorPolicy: Drop
      outputs: []
      resourceGroupName: sjrg6936
      sku:
        name: Standard
      tags:
        key1: value1
        key3: value3
        randomKey: randomValue

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:streamanalytics:StreamingJob sj59 /subscriptions/56b5e0a9-b645-407d-99b0-c64f86013e3d/resourceGroups/sjrg6936/providers/Microsoft.StreamAnalytics/streamingjobs/sj59 
```
