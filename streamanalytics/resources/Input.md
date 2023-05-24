An input object, containing all information associated with the named input. All inputs are contained under a streaming job.
API Version: 2020-03-01.
Previous API Version: 2016-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a Gateway Message Bus input
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var input = new AzureNative.StreamAnalytics.Input("input", new()
    {
        InputName = "input7970",
        JobName = "sj9742",
        Properties = new AzureNative.StreamAnalytics.Inputs.StreamInputPropertiesArgs
        {
            Datasource = new AzureNative.StreamAnalytics.Inputs.GatewayMessageBusStreamInputDataSourceArgs
            {
                Topic = "EdgeTopic1",
                Type = "GatewayMessageBus",
            },
            Type = "Stream",
        },
        ResourceGroupName = "sjrg3467",
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
		_, err := streamanalytics.NewInput(ctx, "input", &streamanalytics.InputArgs{
			InputName: pulumi.String("input7970"),
			JobName:   pulumi.String("sj9742"),
			Properties: streamanalytics.StreamInputProperties{
				Datasource: streamanalytics.GatewayMessageBusStreamInputDataSource{
					Topic: "EdgeTopic1",
					Type:  "GatewayMessageBus",
				},
				Type: "Stream",
			},
			ResourceGroupName: pulumi.String("sjrg3467"),
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
import com.pulumi.azurenative.streamanalytics.Input;
import com.pulumi.azurenative.streamanalytics.InputArgs;
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
        var input = new Input("input", InputArgs.builder()        
            .inputName("input7970")
            .jobName("sj9742")
            .properties(Map.ofEntries(
                Map.entry("datasource", Map.ofEntries(
                    Map.entry("topic", "EdgeTopic1"),
                    Map.entry("type", "GatewayMessageBus")
                )),
                Map.entry("type", "Stream")
            ))
            .resourceGroupName("sjrg3467")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const input = new azure_native.streamanalytics.Input("input", {
    inputName: "input7970",
    jobName: "sj9742",
    properties: {
        datasource: {
            topic: "EdgeTopic1",
            type: "GatewayMessageBus",
        },
        type: "Stream",
    },
    resourceGroupName: "sjrg3467",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

input = azure_native.streamanalytics.Input("input",
    input_name="input7970",
    job_name="sj9742",
    properties=azure_native.streamanalytics.StreamInputPropertiesArgs(
        datasource=azure_native.streamanalytics.GatewayMessageBusStreamInputDataSourceArgs(
            topic="EdgeTopic1",
            type="GatewayMessageBus",
        ),
        type="Stream",
    ),
    resource_group_name="sjrg3467")

```

```yaml
resources:
  input:
    type: azure-native:streamanalytics:Input
    properties:
      inputName: input7970
      jobName: sj9742
      properties:
        datasource:
          topic: EdgeTopic1
          type: GatewayMessageBus
        type: Stream
      resourceGroupName: sjrg3467

```

{{% /example %}}
{{% example %}}
### Create a reference blob input with CSV serialization
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var input = new AzureNative.StreamAnalytics.Input("input", new()
    {
        InputName = "input7225",
        JobName = "sj9597",
        Properties = new AzureNative.StreamAnalytics.Inputs.ReferenceInputPropertiesArgs
        {
            Datasource = new AzureNative.StreamAnalytics.Inputs.BlobReferenceInputDataSourceArgs
            {
                Container = "state",
                DateFormat = "yyyy/MM/dd",
                PathPattern = "{date}/{time}",
                StorageAccounts = new[]
                {
                    new AzureNative.StreamAnalytics.Inputs.StorageAccountArgs
                    {
                        AccountKey = "someAccountKey==",
                        AccountName = "someAccountName",
                    },
                },
                TimeFormat = "HH",
                Type = "Microsoft.Storage/Blob",
            },
            Serialization = new AzureNative.StreamAnalytics.Inputs.CsvSerializationArgs
            {
                Encoding = "UTF8",
                FieldDelimiter = ",",
                Type = "Csv",
            },
            Type = "Reference",
        },
        ResourceGroupName = "sjrg8440",
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
		_, err := streamanalytics.NewInput(ctx, "input", &streamanalytics.InputArgs{
			InputName: pulumi.String("input7225"),
			JobName:   pulumi.String("sj9597"),
			Properties: streamanalytics.ReferenceInputProperties{
				Datasource: streamanalytics.BlobReferenceInputDataSource{
					Container:   "state",
					DateFormat:  "yyyy/MM/dd",
					PathPattern: "{date}/{time}",
					StorageAccounts: []streamanalytics.StorageAccount{
						{
							AccountKey:  "someAccountKey==",
							AccountName: "someAccountName",
						},
					},
					TimeFormat: "HH",
					Type:       "Microsoft.Storage/Blob",
				},
				Serialization: streamanalytics.CsvSerialization{
					Encoding:       "UTF8",
					FieldDelimiter: ",",
					Type:           "Csv",
				},
				Type: "Reference",
			},
			ResourceGroupName: pulumi.String("sjrg8440"),
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
import com.pulumi.azurenative.streamanalytics.Input;
import com.pulumi.azurenative.streamanalytics.InputArgs;
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
        var input = new Input("input", InputArgs.builder()        
            .inputName("input7225")
            .jobName("sj9597")
            .properties(Map.ofEntries(
                Map.entry("datasource", Map.ofEntries(
                    Map.entry("container", "state"),
                    Map.entry("dateFormat", "yyyy/MM/dd"),
                    Map.entry("pathPattern", "{date}/{time}"),
                    Map.entry("storageAccounts", Map.ofEntries(
                        Map.entry("accountKey", "someAccountKey=="),
                        Map.entry("accountName", "someAccountName")
                    )),
                    Map.entry("timeFormat", "HH"),
                    Map.entry("type", "Microsoft.Storage/Blob")
                )),
                Map.entry("serialization", Map.ofEntries(
                    Map.entry("encoding", "UTF8"),
                    Map.entry("fieldDelimiter", ","),
                    Map.entry("type", "Csv")
                )),
                Map.entry("type", "Reference")
            ))
            .resourceGroupName("sjrg8440")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const input = new azure_native.streamanalytics.Input("input", {
    inputName: "input7225",
    jobName: "sj9597",
    properties: {
        datasource: {
            container: "state",
            dateFormat: "yyyy/MM/dd",
            pathPattern: "{date}/{time}",
            storageAccounts: [{
                accountKey: "someAccountKey==",
                accountName: "someAccountName",
            }],
            timeFormat: "HH",
            type: "Microsoft.Storage/Blob",
        },
        serialization: {
            encoding: "UTF8",
            fieldDelimiter: ",",
            type: "Csv",
        },
        type: "Reference",
    },
    resourceGroupName: "sjrg8440",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

input = azure_native.streamanalytics.Input("input",
    input_name="input7225",
    job_name="sj9597",
    properties=azure_native.streamanalytics.ReferenceInputPropertiesArgs(
        datasource=azure_native.streamanalytics.BlobReferenceInputDataSourceArgs(
            container="state",
            date_format="yyyy/MM/dd",
            path_pattern="{date}/{time}",
            storage_accounts=[azure_native.streamanalytics.StorageAccountArgs(
                account_key="someAccountKey==",
                account_name="someAccountName",
            )],
            time_format="HH",
            type="Microsoft.Storage/Blob",
        ),
        serialization=azure_native.streamanalytics.CsvSerializationArgs(
            encoding="UTF8",
            field_delimiter=",",
            type="Csv",
        ),
        type="Reference",
    ),
    resource_group_name="sjrg8440")

```

```yaml
resources:
  input:
    type: azure-native:streamanalytics:Input
    properties:
      inputName: input7225
      jobName: sj9597
      properties:
        datasource:
          container: state
          dateFormat: yyyy/MM/dd
          pathPattern: '{date}/{time}'
          storageAccounts:
            - accountKey: someAccountKey==
              accountName: someAccountName
          timeFormat: HH
          type: Microsoft.Storage/Blob
        serialization:
          encoding: UTF8
          fieldDelimiter: ','
          type: Csv
        type: Reference
      resourceGroupName: sjrg8440

```

{{% /example %}}
{{% example %}}
### Create a reference file input
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var input = new AzureNative.StreamAnalytics.Input("input", new()
    {
        InputName = "input7225",
        JobName = "sj9597",
        Properties = new AzureNative.StreamAnalytics.Inputs.ReferenceInputPropertiesArgs
        {
            Datasource = new AzureNative.StreamAnalytics.Inputs.FileReferenceInputDataSourceArgs
            {
                Path = "my/path",
                Type = "File",
            },
            Type = "Reference",
        },
        ResourceGroupName = "sjrg8440",
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
		_, err := streamanalytics.NewInput(ctx, "input", &streamanalytics.InputArgs{
			InputName: pulumi.String("input7225"),
			JobName:   pulumi.String("sj9597"),
			Properties: streamanalytics.ReferenceInputProperties{
				Datasource: streamanalytics.FileReferenceInputDataSource{
					Path: "my/path",
					Type: "File",
				},
				Type: "Reference",
			},
			ResourceGroupName: pulumi.String("sjrg8440"),
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
import com.pulumi.azurenative.streamanalytics.Input;
import com.pulumi.azurenative.streamanalytics.InputArgs;
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
        var input = new Input("input", InputArgs.builder()        
            .inputName("input7225")
            .jobName("sj9597")
            .properties(Map.ofEntries(
                Map.entry("datasource", Map.ofEntries(
                    Map.entry("path", "my/path"),
                    Map.entry("type", "File")
                )),
                Map.entry("type", "Reference")
            ))
            .resourceGroupName("sjrg8440")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const input = new azure_native.streamanalytics.Input("input", {
    inputName: "input7225",
    jobName: "sj9597",
    properties: {
        datasource: {
            path: "my/path",
            type: "File",
        },
        type: "Reference",
    },
    resourceGroupName: "sjrg8440",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

input = azure_native.streamanalytics.Input("input",
    input_name="input7225",
    job_name="sj9597",
    properties=azure_native.streamanalytics.ReferenceInputPropertiesArgs(
        datasource=azure_native.streamanalytics.FileReferenceInputDataSourceArgs(
            path="my/path",
            type="File",
        ),
        type="Reference",
    ),
    resource_group_name="sjrg8440")

```

```yaml
resources:
  input:
    type: azure-native:streamanalytics:Input
    properties:
      inputName: input7225
      jobName: sj9597
      properties:
        datasource:
          path: my/path
          type: File
        type: Reference
      resourceGroupName: sjrg8440

```

{{% /example %}}
{{% example %}}
### Create a stream Event Hub input with JSON serialization
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var input = new AzureNative.StreamAnalytics.Input("input", new()
    {
        InputName = "input7425",
        JobName = "sj197",
        Properties = new AzureNative.StreamAnalytics.Inputs.StreamInputPropertiesArgs
        {
            Datasource = new AzureNative.StreamAnalytics.Inputs.EventHubStreamInputDataSourceArgs
            {
                ConsumerGroupName = "sdkconsumergroup",
                EventHubName = "sdkeventhub",
                ServiceBusNamespace = "sdktest",
                SharedAccessPolicyKey = "someSharedAccessPolicyKey==",
                SharedAccessPolicyName = "RootManageSharedAccessKey",
                Type = "Microsoft.ServiceBus/EventHub",
            },
            Serialization = new AzureNative.StreamAnalytics.Inputs.JsonSerializationArgs
            {
                Encoding = "UTF8",
                Type = "Json",
            },
            Type = "Stream",
        },
        ResourceGroupName = "sjrg3139",
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
		_, err := streamanalytics.NewInput(ctx, "input", &streamanalytics.InputArgs{
			InputName: pulumi.String("input7425"),
			JobName:   pulumi.String("sj197"),
			Properties: streamanalytics.StreamInputProperties{
				Datasource: streamanalytics.EventHubStreamInputDataSource{
					ConsumerGroupName:      "sdkconsumergroup",
					EventHubName:           "sdkeventhub",
					ServiceBusNamespace:    "sdktest",
					SharedAccessPolicyKey:  "someSharedAccessPolicyKey==",
					SharedAccessPolicyName: "RootManageSharedAccessKey",
					Type:                   "Microsoft.ServiceBus/EventHub",
				},
				Serialization: streamanalytics.JsonSerialization{
					Encoding: "UTF8",
					Type:     "Json",
				},
				Type: "Stream",
			},
			ResourceGroupName: pulumi.String("sjrg3139"),
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
import com.pulumi.azurenative.streamanalytics.Input;
import com.pulumi.azurenative.streamanalytics.InputArgs;
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
        var input = new Input("input", InputArgs.builder()        
            .inputName("input7425")
            .jobName("sj197")
            .properties(Map.ofEntries(
                Map.entry("datasource", Map.ofEntries(
                    Map.entry("consumerGroupName", "sdkconsumergroup"),
                    Map.entry("eventHubName", "sdkeventhub"),
                    Map.entry("serviceBusNamespace", "sdktest"),
                    Map.entry("sharedAccessPolicyKey", "someSharedAccessPolicyKey=="),
                    Map.entry("sharedAccessPolicyName", "RootManageSharedAccessKey"),
                    Map.entry("type", "Microsoft.ServiceBus/EventHub")
                )),
                Map.entry("serialization", Map.ofEntries(
                    Map.entry("encoding", "UTF8"),
                    Map.entry("type", "Json")
                )),
                Map.entry("type", "Stream")
            ))
            .resourceGroupName("sjrg3139")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const input = new azure_native.streamanalytics.Input("input", {
    inputName: "input7425",
    jobName: "sj197",
    properties: {
        datasource: {
            consumerGroupName: "sdkconsumergroup",
            eventHubName: "sdkeventhub",
            serviceBusNamespace: "sdktest",
            sharedAccessPolicyKey: "someSharedAccessPolicyKey==",
            sharedAccessPolicyName: "RootManageSharedAccessKey",
            type: "Microsoft.ServiceBus/EventHub",
        },
        serialization: {
            encoding: "UTF8",
            type: "Json",
        },
        type: "Stream",
    },
    resourceGroupName: "sjrg3139",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

input = azure_native.streamanalytics.Input("input",
    input_name="input7425",
    job_name="sj197",
    properties=azure_native.streamanalytics.StreamInputPropertiesArgs(
        datasource=azure_native.streamanalytics.EventHubStreamInputDataSourceArgs(
            consumer_group_name="sdkconsumergroup",
            event_hub_name="sdkeventhub",
            service_bus_namespace="sdktest",
            shared_access_policy_key="someSharedAccessPolicyKey==",
            shared_access_policy_name="RootManageSharedAccessKey",
            type="Microsoft.ServiceBus/EventHub",
        ),
        serialization=azure_native.streamanalytics.JsonSerializationArgs(
            encoding="UTF8",
            type="Json",
        ),
        type="Stream",
    ),
    resource_group_name="sjrg3139")

```

```yaml
resources:
  input:
    type: azure-native:streamanalytics:Input
    properties:
      inputName: input7425
      jobName: sj197
      properties:
        datasource:
          consumerGroupName: sdkconsumergroup
          eventHubName: sdkeventhub
          serviceBusNamespace: sdktest
          sharedAccessPolicyKey: someSharedAccessPolicyKey==
          sharedAccessPolicyName: RootManageSharedAccessKey
          type: Microsoft.ServiceBus/EventHub
        serialization:
          encoding: UTF8
          type: Json
        type: Stream
      resourceGroupName: sjrg3139

```

{{% /example %}}
{{% example %}}
### Create a stream IoT Hub input with Avro serialization
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var input = new AzureNative.StreamAnalytics.Input("input", new()
    {
        InputName = "input7970",
        JobName = "sj9742",
        Properties = new AzureNative.StreamAnalytics.Inputs.StreamInputPropertiesArgs
        {
            Datasource = new AzureNative.StreamAnalytics.Inputs.IoTHubStreamInputDataSourceArgs
            {
                ConsumerGroupName = "sdkconsumergroup",
                Endpoint = "messages/events",
                IotHubNamespace = "iothub",
                SharedAccessPolicyKey = "sharedAccessPolicyKey=",
                SharedAccessPolicyName = "owner",
                Type = "Microsoft.Devices/IotHubs",
            },
            Serialization = new AzureNative.StreamAnalytics.Inputs.AvroSerializationArgs
            {
                Type = "Avro",
            },
            Type = "Stream",
        },
        ResourceGroupName = "sjrg3467",
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
		_, err := streamanalytics.NewInput(ctx, "input", &streamanalytics.InputArgs{
			InputName: pulumi.String("input7970"),
			JobName:   pulumi.String("sj9742"),
			Properties: streamanalytics.StreamInputProperties{
				Datasource: streamanalytics.IoTHubStreamInputDataSource{
					ConsumerGroupName:      "sdkconsumergroup",
					Endpoint:               "messages/events",
					IotHubNamespace:        "iothub",
					SharedAccessPolicyKey:  "sharedAccessPolicyKey=",
					SharedAccessPolicyName: "owner",
					Type:                   "Microsoft.Devices/IotHubs",
				},
				Serialization: streamanalytics.AvroSerialization{
					Type: "Avro",
				},
				Type: "Stream",
			},
			ResourceGroupName: pulumi.String("sjrg3467"),
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
import com.pulumi.azurenative.streamanalytics.Input;
import com.pulumi.azurenative.streamanalytics.InputArgs;
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
        var input = new Input("input", InputArgs.builder()        
            .inputName("input7970")
            .jobName("sj9742")
            .properties(Map.ofEntries(
                Map.entry("datasource", Map.ofEntries(
                    Map.entry("consumerGroupName", "sdkconsumergroup"),
                    Map.entry("endpoint", "messages/events"),
                    Map.entry("iotHubNamespace", "iothub"),
                    Map.entry("sharedAccessPolicyKey", "sharedAccessPolicyKey="),
                    Map.entry("sharedAccessPolicyName", "owner"),
                    Map.entry("type", "Microsoft.Devices/IotHubs")
                )),
                Map.entry("serialization", Map.of("type", "Avro")),
                Map.entry("type", "Stream")
            ))
            .resourceGroupName("sjrg3467")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const input = new azure_native.streamanalytics.Input("input", {
    inputName: "input7970",
    jobName: "sj9742",
    properties: {
        datasource: {
            consumerGroupName: "sdkconsumergroup",
            endpoint: "messages/events",
            iotHubNamespace: "iothub",
            sharedAccessPolicyKey: "sharedAccessPolicyKey=",
            sharedAccessPolicyName: "owner",
            type: "Microsoft.Devices/IotHubs",
        },
        serialization: {
            type: "Avro",
        },
        type: "Stream",
    },
    resourceGroupName: "sjrg3467",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

input = azure_native.streamanalytics.Input("input",
    input_name="input7970",
    job_name="sj9742",
    properties=azure_native.streamanalytics.StreamInputPropertiesArgs(
        datasource=azure_native.streamanalytics.IoTHubStreamInputDataSourceArgs(
            consumer_group_name="sdkconsumergroup",
            endpoint="messages/events",
            iot_hub_namespace="iothub",
            shared_access_policy_key="sharedAccessPolicyKey=",
            shared_access_policy_name="owner",
            type="Microsoft.Devices/IotHubs",
        ),
        serialization=azure_native.streamanalytics.AvroSerializationArgs(
            type="Avro",
        ),
        type="Stream",
    ),
    resource_group_name="sjrg3467")

```

```yaml
resources:
  input:
    type: azure-native:streamanalytics:Input
    properties:
      inputName: input7970
      jobName: sj9742
      properties:
        datasource:
          consumerGroupName: sdkconsumergroup
          endpoint: messages/events
          iotHubNamespace: iothub
          sharedAccessPolicyKey: sharedAccessPolicyKey=
          sharedAccessPolicyName: owner
          type: Microsoft.Devices/IotHubs
        serialization:
          type: Avro
        type: Stream
      resourceGroupName: sjrg3467

```

{{% /example %}}
{{% example %}}
### Create a stream blob input with CSV serialization
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var input = new AzureNative.StreamAnalytics.Input("input", new()
    {
        InputName = "input8899",
        JobName = "sj6695",
        Properties = new AzureNative.StreamAnalytics.Inputs.StreamInputPropertiesArgs
        {
            Datasource = new AzureNative.StreamAnalytics.Inputs.BlobStreamInputDataSourceArgs
            {
                Container = "state",
                DateFormat = "yyyy/MM/dd",
                PathPattern = "{date}/{time}",
                SourcePartitionCount = 16,
                StorageAccounts = new[]
                {
                    new AzureNative.StreamAnalytics.Inputs.StorageAccountArgs
                    {
                        AccountKey = "someAccountKey==",
                        AccountName = "someAccountName",
                    },
                },
                TimeFormat = "HH",
                Type = "Microsoft.Storage/Blob",
            },
            Serialization = new AzureNative.StreamAnalytics.Inputs.CsvSerializationArgs
            {
                Encoding = "UTF8",
                FieldDelimiter = ",",
                Type = "Csv",
            },
            Type = "Stream",
        },
        ResourceGroupName = "sjrg8161",
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
		_, err := streamanalytics.NewInput(ctx, "input", &streamanalytics.InputArgs{
			InputName: pulumi.String("input8899"),
			JobName:   pulumi.String("sj6695"),
			Properties: streamanalytics.StreamInputProperties{
				Datasource: streamanalytics.BlobStreamInputDataSource{
					Container:            "state",
					DateFormat:           "yyyy/MM/dd",
					PathPattern:          "{date}/{time}",
					SourcePartitionCount: 16,
					StorageAccounts: []streamanalytics.StorageAccount{
						{
							AccountKey:  "someAccountKey==",
							AccountName: "someAccountName",
						},
					},
					TimeFormat: "HH",
					Type:       "Microsoft.Storage/Blob",
				},
				Serialization: streamanalytics.CsvSerialization{
					Encoding:       "UTF8",
					FieldDelimiter: ",",
					Type:           "Csv",
				},
				Type: "Stream",
			},
			ResourceGroupName: pulumi.String("sjrg8161"),
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
import com.pulumi.azurenative.streamanalytics.Input;
import com.pulumi.azurenative.streamanalytics.InputArgs;
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
        var input = new Input("input", InputArgs.builder()        
            .inputName("input8899")
            .jobName("sj6695")
            .properties(Map.ofEntries(
                Map.entry("datasource", Map.ofEntries(
                    Map.entry("container", "state"),
                    Map.entry("dateFormat", "yyyy/MM/dd"),
                    Map.entry("pathPattern", "{date}/{time}"),
                    Map.entry("sourcePartitionCount", 16),
                    Map.entry("storageAccounts", Map.ofEntries(
                        Map.entry("accountKey", "someAccountKey=="),
                        Map.entry("accountName", "someAccountName")
                    )),
                    Map.entry("timeFormat", "HH"),
                    Map.entry("type", "Microsoft.Storage/Blob")
                )),
                Map.entry("serialization", Map.ofEntries(
                    Map.entry("encoding", "UTF8"),
                    Map.entry("fieldDelimiter", ","),
                    Map.entry("type", "Csv")
                )),
                Map.entry("type", "Stream")
            ))
            .resourceGroupName("sjrg8161")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const input = new azure_native.streamanalytics.Input("input", {
    inputName: "input8899",
    jobName: "sj6695",
    properties: {
        datasource: {
            container: "state",
            dateFormat: "yyyy/MM/dd",
            pathPattern: "{date}/{time}",
            sourcePartitionCount: 16,
            storageAccounts: [{
                accountKey: "someAccountKey==",
                accountName: "someAccountName",
            }],
            timeFormat: "HH",
            type: "Microsoft.Storage/Blob",
        },
        serialization: {
            encoding: "UTF8",
            fieldDelimiter: ",",
            type: "Csv",
        },
        type: "Stream",
    },
    resourceGroupName: "sjrg8161",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

input = azure_native.streamanalytics.Input("input",
    input_name="input8899",
    job_name="sj6695",
    properties=azure_native.streamanalytics.StreamInputPropertiesArgs(
        datasource=azure_native.streamanalytics.BlobStreamInputDataSourceArgs(
            container="state",
            date_format="yyyy/MM/dd",
            path_pattern="{date}/{time}",
            source_partition_count=16,
            storage_accounts=[azure_native.streamanalytics.StorageAccountArgs(
                account_key="someAccountKey==",
                account_name="someAccountName",
            )],
            time_format="HH",
            type="Microsoft.Storage/Blob",
        ),
        serialization=azure_native.streamanalytics.CsvSerializationArgs(
            encoding="UTF8",
            field_delimiter=",",
            type="Csv",
        ),
        type="Stream",
    ),
    resource_group_name="sjrg8161")

```

```yaml
resources:
  input:
    type: azure-native:streamanalytics:Input
    properties:
      inputName: input8899
      jobName: sj6695
      properties:
        datasource:
          container: state
          dateFormat: yyyy/MM/dd
          pathPattern: '{date}/{time}'
          sourcePartitionCount: 16
          storageAccounts:
            - accountKey: someAccountKey==
              accountName: someAccountName
          timeFormat: HH
          type: Microsoft.Storage/Blob
        serialization:
          encoding: UTF8
          fieldDelimiter: ','
          type: Csv
        type: Stream
      resourceGroupName: sjrg8161

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:streamanalytics:Input input8899 /subscriptions/56b5e0a9-b645-407d-99b0-c64f86013e3d/resourceGroups/sjrg8161/providers/Microsoft.StreamAnalytics/streamingjobs/sj6695/inputs/input8899 
```
