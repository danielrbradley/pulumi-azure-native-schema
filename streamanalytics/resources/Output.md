An output object, containing all information associated with the named output. All outputs are contained under a streaming job.
API Version: 2020-03-01.
Previous API Version: 2016-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a DocumentDB output
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var output = new AzureNative.StreamAnalytics.Output("output", new()
    {
        Datasource = new AzureNative.StreamAnalytics.Inputs.DocumentDbOutputDataSourceArgs
        {
            AccountId = "someAccountId",
            AccountKey = "accountKey==",
            CollectionNamePattern = "collection",
            Database = "db01",
            DocumentId = "documentId",
            PartitionKey = "key",
            Type = "Microsoft.Storage/DocumentDB",
        },
        JobName = "sj2331",
        OutputName = "output3022",
        ResourceGroupName = "sjrg7983",
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
		_, err := streamanalytics.NewOutput(ctx, "output", &streamanalytics.OutputArgs{
			Datasource: streamanalytics.DocumentDbOutputDataSource{
				AccountId:             "someAccountId",
				AccountKey:            "accountKey==",
				CollectionNamePattern: "collection",
				Database:              "db01",
				DocumentId:            "documentId",
				PartitionKey:          "key",
				Type:                  "Microsoft.Storage/DocumentDB",
			},
			JobName:           pulumi.String("sj2331"),
			OutputName:        pulumi.String("output3022"),
			ResourceGroupName: pulumi.String("sjrg7983"),
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
import com.pulumi.azurenative.streamanalytics.Output;
import com.pulumi.azurenative.streamanalytics.OutputArgs;
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
        var output = new Output("output", OutputArgs.builder()        
            .datasource(Map.ofEntries(
                Map.entry("accountId", "someAccountId"),
                Map.entry("accountKey", "accountKey=="),
                Map.entry("collectionNamePattern", "collection"),
                Map.entry("database", "db01"),
                Map.entry("documentId", "documentId"),
                Map.entry("partitionKey", "key"),
                Map.entry("type", "Microsoft.Storage/DocumentDB")
            ))
            .jobName("sj2331")
            .outputName("output3022")
            .resourceGroupName("sjrg7983")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const output = new azure_native.streamanalytics.Output("output", {
    datasource: {
        accountId: "someAccountId",
        accountKey: "accountKey==",
        collectionNamePattern: "collection",
        database: "db01",
        documentId: "documentId",
        partitionKey: "key",
        type: "Microsoft.Storage/DocumentDB",
    },
    jobName: "sj2331",
    outputName: "output3022",
    resourceGroupName: "sjrg7983",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

output = azure_native.streamanalytics.Output("output",
    datasource=azure_native.streamanalytics.DocumentDbOutputDataSourceArgs(
        account_id="someAccountId",
        account_key="accountKey==",
        collection_name_pattern="collection",
        database="db01",
        document_id="documentId",
        partition_key="key",
        type="Microsoft.Storage/DocumentDB",
    ),
    job_name="sj2331",
    output_name="output3022",
    resource_group_name="sjrg7983")

```

```yaml
resources:
  output:
    type: azure-native:streamanalytics:Output
    properties:
      datasource:
        accountId: someAccountId
        accountKey: accountKey==
        collectionNamePattern: collection
        database: db01
        documentId: documentId
        partitionKey: key
        type: Microsoft.Storage/DocumentDB
      jobName: sj2331
      outputName: output3022
      resourceGroupName: sjrg7983

```

{{% /example %}}
{{% example %}}
### Create a Gateway Message Bus output
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var output = new AzureNative.StreamAnalytics.Output("output", new()
    {
        Datasource = new AzureNative.StreamAnalytics.Inputs.GatewayMessageBusOutputDataSourceArgs
        {
            Topic = "EdgeTopic1",
            Type = "GatewayMessageBus",
        },
        JobName = "sj2331",
        OutputName = "output3022",
        ResourceGroupName = "sjrg7983",
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
		_, err := streamanalytics.NewOutput(ctx, "output", &streamanalytics.OutputArgs{
			Datasource: streamanalytics.GatewayMessageBusOutputDataSource{
				Topic: "EdgeTopic1",
				Type:  "GatewayMessageBus",
			},
			JobName:           pulumi.String("sj2331"),
			OutputName:        pulumi.String("output3022"),
			ResourceGroupName: pulumi.String("sjrg7983"),
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
import com.pulumi.azurenative.streamanalytics.Output;
import com.pulumi.azurenative.streamanalytics.OutputArgs;
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
        var output = new Output("output", OutputArgs.builder()        
            .datasource(Map.ofEntries(
                Map.entry("topic", "EdgeTopic1"),
                Map.entry("type", "GatewayMessageBus")
            ))
            .jobName("sj2331")
            .outputName("output3022")
            .resourceGroupName("sjrg7983")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const output = new azure_native.streamanalytics.Output("output", {
    datasource: {
        topic: "EdgeTopic1",
        type: "GatewayMessageBus",
    },
    jobName: "sj2331",
    outputName: "output3022",
    resourceGroupName: "sjrg7983",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

output = azure_native.streamanalytics.Output("output",
    datasource=azure_native.streamanalytics.GatewayMessageBusOutputDataSourceArgs(
        topic="EdgeTopic1",
        type="GatewayMessageBus",
    ),
    job_name="sj2331",
    output_name="output3022",
    resource_group_name="sjrg7983")

```

```yaml
resources:
  output:
    type: azure-native:streamanalytics:Output
    properties:
      datasource:
        topic: EdgeTopic1
        type: GatewayMessageBus
      jobName: sj2331
      outputName: output3022
      resourceGroupName: sjrg7983

```

{{% /example %}}
{{% example %}}
### Create a Power BI output
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var output = new AzureNative.StreamAnalytics.Output("output", new()
    {
        Datasource = new AzureNative.StreamAnalytics.Inputs.PowerBIOutputDataSourceArgs
        {
            Dataset = "someDataset",
            GroupId = "ac40305e-3e8d-43ac-8161-c33799f43e95",
            GroupName = "MyPowerBIGroup",
            RefreshToken = "someRefreshToken==",
            Table = "someTable",
            TokenUserDisplayName = "Bob Smith",
            TokenUserPrincipalName = "bobsmith@contoso.com",
            Type = "PowerBI",
        },
        JobName = "sj2331",
        OutputName = "output3022",
        ResourceGroupName = "sjrg7983",
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
		_, err := streamanalytics.NewOutput(ctx, "output", &streamanalytics.OutputArgs{
			Datasource: streamanalytics.PowerBIOutputDataSource{
				Dataset:                "someDataset",
				GroupId:                "ac40305e-3e8d-43ac-8161-c33799f43e95",
				GroupName:              "MyPowerBIGroup",
				RefreshToken:           "someRefreshToken==",
				Table:                  "someTable",
				TokenUserDisplayName:   "Bob Smith",
				TokenUserPrincipalName: "bobsmith@contoso.com",
				Type:                   "PowerBI",
			},
			JobName:           pulumi.String("sj2331"),
			OutputName:        pulumi.String("output3022"),
			ResourceGroupName: pulumi.String("sjrg7983"),
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
import com.pulumi.azurenative.streamanalytics.Output;
import com.pulumi.azurenative.streamanalytics.OutputArgs;
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
        var output = new Output("output", OutputArgs.builder()        
            .datasource(Map.ofEntries(
                Map.entry("dataset", "someDataset"),
                Map.entry("groupId", "ac40305e-3e8d-43ac-8161-c33799f43e95"),
                Map.entry("groupName", "MyPowerBIGroup"),
                Map.entry("refreshToken", "someRefreshToken=="),
                Map.entry("table", "someTable"),
                Map.entry("tokenUserDisplayName", "Bob Smith"),
                Map.entry("tokenUserPrincipalName", "bobsmith@contoso.com"),
                Map.entry("type", "PowerBI")
            ))
            .jobName("sj2331")
            .outputName("output3022")
            .resourceGroupName("sjrg7983")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const output = new azure_native.streamanalytics.Output("output", {
    datasource: {
        dataset: "someDataset",
        groupId: "ac40305e-3e8d-43ac-8161-c33799f43e95",
        groupName: "MyPowerBIGroup",
        refreshToken: "someRefreshToken==",
        table: "someTable",
        tokenUserDisplayName: "Bob Smith",
        tokenUserPrincipalName: "bobsmith@contoso.com",
        type: "PowerBI",
    },
    jobName: "sj2331",
    outputName: "output3022",
    resourceGroupName: "sjrg7983",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

output = azure_native.streamanalytics.Output("output",
    datasource=azure_native.streamanalytics.PowerBIOutputDataSourceArgs(
        dataset="someDataset",
        group_id="ac40305e-3e8d-43ac-8161-c33799f43e95",
        group_name="MyPowerBIGroup",
        refresh_token="someRefreshToken==",
        table="someTable",
        token_user_display_name="Bob Smith",
        token_user_principal_name="bobsmith@contoso.com",
        type="PowerBI",
    ),
    job_name="sj2331",
    output_name="output3022",
    resource_group_name="sjrg7983")

```

```yaml
resources:
  output:
    type: azure-native:streamanalytics:Output
    properties:
      datasource:
        dataset: someDataset
        groupId: ac40305e-3e8d-43ac-8161-c33799f43e95
        groupName: MyPowerBIGroup
        refreshToken: someRefreshToken==
        table: someTable
        tokenUserDisplayName: Bob Smith
        tokenUserPrincipalName: bobsmith@contoso.com
        type: PowerBI
      jobName: sj2331
      outputName: output3022
      resourceGroupName: sjrg7983

```

{{% /example %}}
{{% example %}}
### Create a Service Bus Queue output with Avro serialization
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var output = new AzureNative.StreamAnalytics.Output("output", new()
    {
        Datasource = new AzureNative.StreamAnalytics.Inputs.ServiceBusQueueOutputDataSourceArgs
        {
            PropertyColumns = new[]
            {
                "column1",
                "column2",
            },
            QueueName = "sdkqueue",
            ServiceBusNamespace = "sdktest",
            SharedAccessPolicyKey = "sharedAccessPolicyKey=",
            SharedAccessPolicyName = "RootManageSharedAccessKey",
            SystemPropertyColumns = 
            {
                { "MessageId", "col3" },
                { "PartitionKey", "col4" },
            },
            Type = "Microsoft.ServiceBus/Queue",
        },
        JobName = "sj5095",
        OutputName = "output3456",
        ResourceGroupName = "sjrg3410",
        Serialization = new AzureNative.StreamAnalytics.Inputs.AvroSerializationArgs
        {
            Type = "Avro",
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
		_, err := streamanalytics.NewOutput(ctx, "output", &streamanalytics.OutputArgs{
			Datasource: streamanalytics.ServiceBusQueueOutputDataSource{
				PropertyColumns: []string{
					"column1",
					"column2",
				},
				QueueName:              "sdkqueue",
				ServiceBusNamespace:    "sdktest",
				SharedAccessPolicyKey:  "sharedAccessPolicyKey=",
				SharedAccessPolicyName: "RootManageSharedAccessKey",
				SystemPropertyColumns: map[string]interface{}{
					"MessageId":    "col3",
					"PartitionKey": "col4",
				},
				Type: "Microsoft.ServiceBus/Queue",
			},
			JobName:           pulumi.String("sj5095"),
			OutputName:        pulumi.String("output3456"),
			ResourceGroupName: pulumi.String("sjrg3410"),
			Serialization: streamanalytics.AvroSerialization{
				Type: "Avro",
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
import com.pulumi.azurenative.streamanalytics.Output;
import com.pulumi.azurenative.streamanalytics.OutputArgs;
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
        var output = new Output("output", OutputArgs.builder()        
            .datasource(Map.ofEntries(
                Map.entry("propertyColumns",                 
                    "column1",
                    "column2"),
                Map.entry("queueName", "sdkqueue"),
                Map.entry("serviceBusNamespace", "sdktest"),
                Map.entry("sharedAccessPolicyKey", "sharedAccessPolicyKey="),
                Map.entry("sharedAccessPolicyName", "RootManageSharedAccessKey"),
                Map.entry("systemPropertyColumns", AzureDataLakeStoreOutputDataSourceArgs.builder()
                    .messageId("col3")
                    .partitionKey("col4")
                    .build()),
                Map.entry("type", "Microsoft.ServiceBus/Queue")
            ))
            .jobName("sj5095")
            .outputName("output3456")
            .resourceGroupName("sjrg3410")
            .serialization(Map.of("type", "Avro"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const output = new azure_native.streamanalytics.Output("output", {
    datasource: {
        propertyColumns: [
            "column1",
            "column2",
        ],
        queueName: "sdkqueue",
        serviceBusNamespace: "sdktest",
        sharedAccessPolicyKey: "sharedAccessPolicyKey=",
        sharedAccessPolicyName: "RootManageSharedAccessKey",
        systemPropertyColumns: {
            MessageId: "col3",
            PartitionKey: "col4",
        },
        type: "Microsoft.ServiceBus/Queue",
    },
    jobName: "sj5095",
    outputName: "output3456",
    resourceGroupName: "sjrg3410",
    serialization: {
        type: "Avro",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

output = azure_native.streamanalytics.Output("output",
    datasource=azure_native.streamanalytics.ServiceBusQueueOutputDataSourceArgs(
        property_columns=[
            "column1",
            "column2",
        ],
        queue_name="sdkqueue",
        service_bus_namespace="sdktest",
        shared_access_policy_key="sharedAccessPolicyKey=",
        shared_access_policy_name="RootManageSharedAccessKey",
        system_property_columns={
            "MessageId": "col3",
            "PartitionKey": "col4",
        },
        type="Microsoft.ServiceBus/Queue",
    ),
    job_name="sj5095",
    output_name="output3456",
    resource_group_name="sjrg3410",
    serialization=azure_native.streamanalytics.AvroSerializationArgs(
        type="Avro",
    ))

```

```yaml
resources:
  output:
    type: azure-native:streamanalytics:Output
    properties:
      datasource:
        propertyColumns:
          - column1
          - column2
        queueName: sdkqueue
        serviceBusNamespace: sdktest
        sharedAccessPolicyKey: sharedAccessPolicyKey=
        sharedAccessPolicyName: RootManageSharedAccessKey
        systemPropertyColumns:
          MessageId: col3
          PartitionKey: col4
        type: Microsoft.ServiceBus/Queue
      jobName: sj5095
      outputName: output3456
      resourceGroupName: sjrg3410
      serialization:
        type: Avro

```

{{% /example %}}
{{% example %}}
### Create a Service Bus Topic output with CSV serialization
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var output = new AzureNative.StreamAnalytics.Output("output", new()
    {
        Datasource = new AzureNative.StreamAnalytics.Inputs.ServiceBusTopicOutputDataSourceArgs
        {
            PropertyColumns = new[]
            {
                "column1",
                "column2",
            },
            ServiceBusNamespace = "sdktest",
            SharedAccessPolicyKey = "sharedAccessPolicyKey=",
            SharedAccessPolicyName = "RootManageSharedAccessKey",
            TopicName = "sdktopic",
            Type = "Microsoft.ServiceBus/Topic",
        },
        JobName = "sj7094",
        OutputName = "output7886",
        ResourceGroupName = "sjrg6450",
        Serialization = new AzureNative.StreamAnalytics.Inputs.CsvSerializationArgs
        {
            Encoding = "UTF8",
            FieldDelimiter = ",",
            Type = "Csv",
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
		_, err := streamanalytics.NewOutput(ctx, "output", &streamanalytics.OutputArgs{
			Datasource: streamanalytics.ServiceBusTopicOutputDataSource{
				PropertyColumns: []string{
					"column1",
					"column2",
				},
				ServiceBusNamespace:    "sdktest",
				SharedAccessPolicyKey:  "sharedAccessPolicyKey=",
				SharedAccessPolicyName: "RootManageSharedAccessKey",
				TopicName:              "sdktopic",
				Type:                   "Microsoft.ServiceBus/Topic",
			},
			JobName:           pulumi.String("sj7094"),
			OutputName:        pulumi.String("output7886"),
			ResourceGroupName: pulumi.String("sjrg6450"),
			Serialization: streamanalytics.CsvSerialization{
				Encoding:       "UTF8",
				FieldDelimiter: ",",
				Type:           "Csv",
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
import com.pulumi.azurenative.streamanalytics.Output;
import com.pulumi.azurenative.streamanalytics.OutputArgs;
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
        var output = new Output("output", OutputArgs.builder()        
            .datasource(Map.ofEntries(
                Map.entry("propertyColumns",                 
                    "column1",
                    "column2"),
                Map.entry("serviceBusNamespace", "sdktest"),
                Map.entry("sharedAccessPolicyKey", "sharedAccessPolicyKey="),
                Map.entry("sharedAccessPolicyName", "RootManageSharedAccessKey"),
                Map.entry("topicName", "sdktopic"),
                Map.entry("type", "Microsoft.ServiceBus/Topic")
            ))
            .jobName("sj7094")
            .outputName("output7886")
            .resourceGroupName("sjrg6450")
            .serialization(Map.ofEntries(
                Map.entry("encoding", "UTF8"),
                Map.entry("fieldDelimiter", ","),
                Map.entry("type", "Csv")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const output = new azure_native.streamanalytics.Output("output", {
    datasource: {
        propertyColumns: [
            "column1",
            "column2",
        ],
        serviceBusNamespace: "sdktest",
        sharedAccessPolicyKey: "sharedAccessPolicyKey=",
        sharedAccessPolicyName: "RootManageSharedAccessKey",
        topicName: "sdktopic",
        type: "Microsoft.ServiceBus/Topic",
    },
    jobName: "sj7094",
    outputName: "output7886",
    resourceGroupName: "sjrg6450",
    serialization: {
        encoding: "UTF8",
        fieldDelimiter: ",",
        type: "Csv",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

output = azure_native.streamanalytics.Output("output",
    datasource=azure_native.streamanalytics.ServiceBusTopicOutputDataSourceArgs(
        property_columns=[
            "column1",
            "column2",
        ],
        service_bus_namespace="sdktest",
        shared_access_policy_key="sharedAccessPolicyKey=",
        shared_access_policy_name="RootManageSharedAccessKey",
        topic_name="sdktopic",
        type="Microsoft.ServiceBus/Topic",
    ),
    job_name="sj7094",
    output_name="output7886",
    resource_group_name="sjrg6450",
    serialization=azure_native.streamanalytics.CsvSerializationArgs(
        encoding="UTF8",
        field_delimiter=",",
        type="Csv",
    ))

```

```yaml
resources:
  output:
    type: azure-native:streamanalytics:Output
    properties:
      datasource:
        propertyColumns:
          - column1
          - column2
        serviceBusNamespace: sdktest
        sharedAccessPolicyKey: sharedAccessPolicyKey=
        sharedAccessPolicyName: RootManageSharedAccessKey
        topicName: sdktopic
        type: Microsoft.ServiceBus/Topic
      jobName: sj7094
      outputName: output7886
      resourceGroupName: sjrg6450
      serialization:
        encoding: UTF8
        fieldDelimiter: ','
        type: Csv

```

{{% /example %}}
{{% example %}}
### Create a blob output with CSV serialization
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var output = new AzureNative.StreamAnalytics.Output("output", new()
    {
        Datasource = new AzureNative.StreamAnalytics.Inputs.BlobOutputDataSourceArgs
        {
            Container = "state",
            DateFormat = "yyyy/MM/dd",
            PathPattern = "{date}/{time}",
            StorageAccounts = new[]
            {
                new AzureNative.StreamAnalytics.Inputs.StorageAccountArgs
                {
                    AccountKey = "accountKey==",
                    AccountName = "someAccountName",
                },
            },
            TimeFormat = "HH",
            Type = "Microsoft.Storage/Blob",
        },
        JobName = "sj900",
        OutputName = "output1623",
        ResourceGroupName = "sjrg5023",
        Serialization = new AzureNative.StreamAnalytics.Inputs.CsvSerializationArgs
        {
            Encoding = "UTF8",
            FieldDelimiter = ",",
            Type = "Csv",
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
		_, err := streamanalytics.NewOutput(ctx, "output", &streamanalytics.OutputArgs{
			Datasource: streamanalytics.BlobOutputDataSource{
				Container:   "state",
				DateFormat:  "yyyy/MM/dd",
				PathPattern: "{date}/{time}",
				StorageAccounts: []streamanalytics.StorageAccount{
					{
						AccountKey:  "accountKey==",
						AccountName: "someAccountName",
					},
				},
				TimeFormat: "HH",
				Type:       "Microsoft.Storage/Blob",
			},
			JobName:           pulumi.String("sj900"),
			OutputName:        pulumi.String("output1623"),
			ResourceGroupName: pulumi.String("sjrg5023"),
			Serialization: streamanalytics.CsvSerialization{
				Encoding:       "UTF8",
				FieldDelimiter: ",",
				Type:           "Csv",
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
import com.pulumi.azurenative.streamanalytics.Output;
import com.pulumi.azurenative.streamanalytics.OutputArgs;
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
        var output = new Output("output", OutputArgs.builder()        
            .datasource(Map.ofEntries(
                Map.entry("container", "state"),
                Map.entry("dateFormat", "yyyy/MM/dd"),
                Map.entry("pathPattern", "{date}/{time}"),
                Map.entry("storageAccounts", Map.ofEntries(
                    Map.entry("accountKey", "accountKey=="),
                    Map.entry("accountName", "someAccountName")
                )),
                Map.entry("timeFormat", "HH"),
                Map.entry("type", "Microsoft.Storage/Blob")
            ))
            .jobName("sj900")
            .outputName("output1623")
            .resourceGroupName("sjrg5023")
            .serialization(Map.ofEntries(
                Map.entry("encoding", "UTF8"),
                Map.entry("fieldDelimiter", ","),
                Map.entry("type", "Csv")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const output = new azure_native.streamanalytics.Output("output", {
    datasource: {
        container: "state",
        dateFormat: "yyyy/MM/dd",
        pathPattern: "{date}/{time}",
        storageAccounts: [{
            accountKey: "accountKey==",
            accountName: "someAccountName",
        }],
        timeFormat: "HH",
        type: "Microsoft.Storage/Blob",
    },
    jobName: "sj900",
    outputName: "output1623",
    resourceGroupName: "sjrg5023",
    serialization: {
        encoding: "UTF8",
        fieldDelimiter: ",",
        type: "Csv",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

output = azure_native.streamanalytics.Output("output",
    datasource=azure_native.streamanalytics.BlobOutputDataSourceArgs(
        container="state",
        date_format="yyyy/MM/dd",
        path_pattern="{date}/{time}",
        storage_accounts=[azure_native.streamanalytics.StorageAccountArgs(
            account_key="accountKey==",
            account_name="someAccountName",
        )],
        time_format="HH",
        type="Microsoft.Storage/Blob",
    ),
    job_name="sj900",
    output_name="output1623",
    resource_group_name="sjrg5023",
    serialization=azure_native.streamanalytics.CsvSerializationArgs(
        encoding="UTF8",
        field_delimiter=",",
        type="Csv",
    ))

```

```yaml
resources:
  output:
    type: azure-native:streamanalytics:Output
    properties:
      datasource:
        container: state
        dateFormat: yyyy/MM/dd
        pathPattern: '{date}/{time}'
        storageAccounts:
          - accountKey: accountKey==
            accountName: someAccountName
        timeFormat: HH
        type: Microsoft.Storage/Blob
      jobName: sj900
      outputName: output1623
      resourceGroupName: sjrg5023
      serialization:
        encoding: UTF8
        fieldDelimiter: ','
        type: Csv

```

{{% /example %}}
{{% example %}}
### Create an Azure Data Lake Store output with JSON serialization
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var output = new AzureNative.StreamAnalytics.Output("output", new()
    {
        Datasource = new AzureNative.StreamAnalytics.Inputs.AzureDataLakeStoreOutputDataSourceArgs
        {
            AccountName = "someaccount",
            DateFormat = "yyyy/MM/dd",
            FilePathPrefix = "{date}/{time}",
            RefreshToken = "someRefreshToken==",
            TenantId = "cea4e98b-c798-49e7-8c40-4a2b3beb47dd",
            TimeFormat = "HH",
            TokenUserDisplayName = "Bob Smith",
            TokenUserPrincipalName = "bobsmith@contoso.com",
            Type = "Microsoft.DataLake/Accounts",
        },
        JobName = "sj3310",
        OutputName = "output5195",
        ResourceGroupName = "sjrg6912",
        Serialization = new AzureNative.StreamAnalytics.Inputs.JsonSerializationArgs
        {
            Encoding = "UTF8",
            Format = "Array",
            Type = "Json",
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
		_, err := streamanalytics.NewOutput(ctx, "output", &streamanalytics.OutputArgs{
			Datasource: streamanalytics.AzureDataLakeStoreOutputDataSource{
				AccountName:            "someaccount",
				DateFormat:             "yyyy/MM/dd",
				FilePathPrefix:         "{date}/{time}",
				RefreshToken:           "someRefreshToken==",
				TenantId:               "cea4e98b-c798-49e7-8c40-4a2b3beb47dd",
				TimeFormat:             "HH",
				TokenUserDisplayName:   "Bob Smith",
				TokenUserPrincipalName: "bobsmith@contoso.com",
				Type:                   "Microsoft.DataLake/Accounts",
			},
			JobName:           pulumi.String("sj3310"),
			OutputName:        pulumi.String("output5195"),
			ResourceGroupName: pulumi.String("sjrg6912"),
			Serialization: streamanalytics.JsonSerialization{
				Encoding: "UTF8",
				Format:   "Array",
				Type:     "Json",
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
import com.pulumi.azurenative.streamanalytics.Output;
import com.pulumi.azurenative.streamanalytics.OutputArgs;
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
        var output = new Output("output", OutputArgs.builder()        
            .datasource(Map.ofEntries(
                Map.entry("accountName", "someaccount"),
                Map.entry("dateFormat", "yyyy/MM/dd"),
                Map.entry("filePathPrefix", "{date}/{time}"),
                Map.entry("refreshToken", "someRefreshToken=="),
                Map.entry("tenantId", "cea4e98b-c798-49e7-8c40-4a2b3beb47dd"),
                Map.entry("timeFormat", "HH"),
                Map.entry("tokenUserDisplayName", "Bob Smith"),
                Map.entry("tokenUserPrincipalName", "bobsmith@contoso.com"),
                Map.entry("type", "Microsoft.DataLake/Accounts")
            ))
            .jobName("sj3310")
            .outputName("output5195")
            .resourceGroupName("sjrg6912")
            .serialization(Map.ofEntries(
                Map.entry("encoding", "UTF8"),
                Map.entry("format", "Array"),
                Map.entry("type", "Json")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const output = new azure_native.streamanalytics.Output("output", {
    datasource: {
        accountName: "someaccount",
        dateFormat: "yyyy/MM/dd",
        filePathPrefix: "{date}/{time}",
        refreshToken: "someRefreshToken==",
        tenantId: "cea4e98b-c798-49e7-8c40-4a2b3beb47dd",
        timeFormat: "HH",
        tokenUserDisplayName: "Bob Smith",
        tokenUserPrincipalName: "bobsmith@contoso.com",
        type: "Microsoft.DataLake/Accounts",
    },
    jobName: "sj3310",
    outputName: "output5195",
    resourceGroupName: "sjrg6912",
    serialization: {
        encoding: "UTF8",
        format: "Array",
        type: "Json",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

output = azure_native.streamanalytics.Output("output",
    datasource=azure_native.streamanalytics.AzureDataLakeStoreOutputDataSourceArgs(
        account_name="someaccount",
        date_format="yyyy/MM/dd",
        file_path_prefix="{date}/{time}",
        refresh_token="someRefreshToken==",
        tenant_id="cea4e98b-c798-49e7-8c40-4a2b3beb47dd",
        time_format="HH",
        token_user_display_name="Bob Smith",
        token_user_principal_name="bobsmith@contoso.com",
        type="Microsoft.DataLake/Accounts",
    ),
    job_name="sj3310",
    output_name="output5195",
    resource_group_name="sjrg6912",
    serialization=azure_native.streamanalytics.JsonSerializationArgs(
        encoding="UTF8",
        format="Array",
        type="Json",
    ))

```

```yaml
resources:
  output:
    type: azure-native:streamanalytics:Output
    properties:
      datasource:
        accountName: someaccount
        dateFormat: yyyy/MM/dd
        filePathPrefix: '{date}/{time}'
        refreshToken: someRefreshToken==
        tenantId: cea4e98b-c798-49e7-8c40-4a2b3beb47dd
        timeFormat: HH
        tokenUserDisplayName: Bob Smith
        tokenUserPrincipalName: bobsmith@contoso.com
        type: Microsoft.DataLake/Accounts
      jobName: sj3310
      outputName: output5195
      resourceGroupName: sjrg6912
      serialization:
        encoding: UTF8
        format: Array
        type: Json

```

{{% /example %}}
{{% example %}}
### Create an Azure Data Warehouse output
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var output = new AzureNative.StreamAnalytics.Output("output", new()
    {
        Datasource = new AzureNative.StreamAnalytics.Inputs.AzureSynapseOutputDataSourceArgs
        {
            Database = "zhayaSQLpool",
            Password = "password123",
            Server = "asatestserver",
            Table = "test2",
            Type = "Microsoft.Sql/Server/DataWarehouse",
            User = "tolladmin",
        },
        JobName = "sjName",
        OutputName = "dwOutput",
        ResourceGroupName = "sjrg",
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
		_, err := streamanalytics.NewOutput(ctx, "output", &streamanalytics.OutputArgs{
			Datasource: streamanalytics.AzureSynapseOutputDataSource{
				Database: "zhayaSQLpool",
				Password: "password123",
				Server:   "asatestserver",
				Table:    "test2",
				Type:     "Microsoft.Sql/Server/DataWarehouse",
				User:     "tolladmin",
			},
			JobName:           pulumi.String("sjName"),
			OutputName:        pulumi.String("dwOutput"),
			ResourceGroupName: pulumi.String("sjrg"),
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
import com.pulumi.azurenative.streamanalytics.Output;
import com.pulumi.azurenative.streamanalytics.OutputArgs;
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
        var output = new Output("output", OutputArgs.builder()        
            .datasource(Map.ofEntries(
                Map.entry("database", "zhayaSQLpool"),
                Map.entry("password", "password123"),
                Map.entry("server", "asatestserver"),
                Map.entry("table", "test2"),
                Map.entry("type", "Microsoft.Sql/Server/DataWarehouse"),
                Map.entry("user", "tolladmin")
            ))
            .jobName("sjName")
            .outputName("dwOutput")
            .resourceGroupName("sjrg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const output = new azure_native.streamanalytics.Output("output", {
    datasource: {
        database: "zhayaSQLpool",
        password: "password123",
        server: "asatestserver",
        table: "test2",
        type: "Microsoft.Sql/Server/DataWarehouse",
        user: "tolladmin",
    },
    jobName: "sjName",
    outputName: "dwOutput",
    resourceGroupName: "sjrg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

output = azure_native.streamanalytics.Output("output",
    datasource=azure_native.streamanalytics.AzureSynapseOutputDataSourceArgs(
        database="zhayaSQLpool",
        password="password123",
        server="asatestserver",
        table="test2",
        type="Microsoft.Sql/Server/DataWarehouse",
        user="tolladmin",
    ),
    job_name="sjName",
    output_name="dwOutput",
    resource_group_name="sjrg")

```

```yaml
resources:
  output:
    type: azure-native:streamanalytics:Output
    properties:
      datasource:
        database: zhayaSQLpool
        password: password123
        server: asatestserver
        table: test2
        type: Microsoft.Sql/Server/DataWarehouse
        user: tolladmin
      jobName: sjName
      outputName: dwOutput
      resourceGroupName: sjrg

```

{{% /example %}}
{{% example %}}
### Create an Azure Function output
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var output = new AzureNative.StreamAnalytics.Output("output", new()
    {
        Datasource = new AzureNative.StreamAnalytics.Inputs.AzureFunctionOutputDataSourceArgs
        {
            FunctionAppName = "functionappforasaautomation",
            FunctionName = "HttpTrigger2",
            MaxBatchCount = 100,
            MaxBatchSize = 256,
            Type = "Microsoft.AzureFunction",
        },
        JobName = "sjName",
        OutputName = "azureFunction1",
        ResourceGroupName = "sjrg",
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
		_, err := streamanalytics.NewOutput(ctx, "output", &streamanalytics.OutputArgs{
			Datasource: streamanalytics.AzureFunctionOutputDataSource{
				FunctionAppName: "functionappforasaautomation",
				FunctionName:    "HttpTrigger2",
				MaxBatchCount:   100,
				MaxBatchSize:    256,
				Type:            "Microsoft.AzureFunction",
			},
			JobName:           pulumi.String("sjName"),
			OutputName:        pulumi.String("azureFunction1"),
			ResourceGroupName: pulumi.String("sjrg"),
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
import com.pulumi.azurenative.streamanalytics.Output;
import com.pulumi.azurenative.streamanalytics.OutputArgs;
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
        var output = new Output("output", OutputArgs.builder()        
            .datasource(Map.ofEntries(
                Map.entry("functionAppName", "functionappforasaautomation"),
                Map.entry("functionName", "HttpTrigger2"),
                Map.entry("maxBatchCount", 100),
                Map.entry("maxBatchSize", 256),
                Map.entry("type", "Microsoft.AzureFunction")
            ))
            .jobName("sjName")
            .outputName("azureFunction1")
            .resourceGroupName("sjrg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const output = new azure_native.streamanalytics.Output("output", {
    datasource: {
        functionAppName: "functionappforasaautomation",
        functionName: "HttpTrigger2",
        maxBatchCount: 100,
        maxBatchSize: 256,
        type: "Microsoft.AzureFunction",
    },
    jobName: "sjName",
    outputName: "azureFunction1",
    resourceGroupName: "sjrg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

output = azure_native.streamanalytics.Output("output",
    datasource=azure_native.streamanalytics.AzureFunctionOutputDataSourceArgs(
        function_app_name="functionappforasaautomation",
        function_name="HttpTrigger2",
        max_batch_count=100,
        max_batch_size=256,
        type="Microsoft.AzureFunction",
    ),
    job_name="sjName",
    output_name="azureFunction1",
    resource_group_name="sjrg")

```

```yaml
resources:
  output:
    type: azure-native:streamanalytics:Output
    properties:
      datasource:
        functionAppName: functionappforasaautomation
        functionName: HttpTrigger2
        maxBatchCount: 100
        maxBatchSize: 256
        type: Microsoft.AzureFunction
      jobName: sjName
      outputName: azureFunction1
      resourceGroupName: sjrg

```

{{% /example %}}
{{% example %}}
### Create an Azure SQL database output
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var output = new AzureNative.StreamAnalytics.Output("output", new()
    {
        Datasource = new AzureNative.StreamAnalytics.Inputs.AzureSqlDatabaseOutputDataSourceArgs
        {
            Database = "someDatabase",
            Password = "somePassword",
            Server = "someServer",
            Table = "someTable",
            Type = "Microsoft.Sql/Server/Database",
            User = "<user>",
        },
        JobName = "sj6458",
        OutputName = "output1755",
        ResourceGroupName = "sjrg2157",
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
		_, err := streamanalytics.NewOutput(ctx, "output", &streamanalytics.OutputArgs{
			Datasource: streamanalytics.AzureSqlDatabaseOutputDataSource{
				Database: "someDatabase",
				Password: "somePassword",
				Server:   "someServer",
				Table:    "someTable",
				Type:     "Microsoft.Sql/Server/Database",
				User:     "<user>",
			},
			JobName:           pulumi.String("sj6458"),
			OutputName:        pulumi.String("output1755"),
			ResourceGroupName: pulumi.String("sjrg2157"),
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
import com.pulumi.azurenative.streamanalytics.Output;
import com.pulumi.azurenative.streamanalytics.OutputArgs;
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
        var output = new Output("output", OutputArgs.builder()        
            .datasource(Map.ofEntries(
                Map.entry("database", "someDatabase"),
                Map.entry("password", "somePassword"),
                Map.entry("server", "someServer"),
                Map.entry("table", "someTable"),
                Map.entry("type", "Microsoft.Sql/Server/Database"),
                Map.entry("user", "<user>")
            ))
            .jobName("sj6458")
            .outputName("output1755")
            .resourceGroupName("sjrg2157")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const output = new azure_native.streamanalytics.Output("output", {
    datasource: {
        database: "someDatabase",
        password: "somePassword",
        server: "someServer",
        table: "someTable",
        type: "Microsoft.Sql/Server/Database",
        user: "<user>",
    },
    jobName: "sj6458",
    outputName: "output1755",
    resourceGroupName: "sjrg2157",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

output = azure_native.streamanalytics.Output("output",
    datasource=azure_native.streamanalytics.AzureSqlDatabaseOutputDataSourceArgs(
        database="someDatabase",
        password="somePassword",
        server="someServer",
        table="someTable",
        type="Microsoft.Sql/Server/Database",
        user="<user>",
    ),
    job_name="sj6458",
    output_name="output1755",
    resource_group_name="sjrg2157")

```

```yaml
resources:
  output:
    type: azure-native:streamanalytics:Output
    properties:
      datasource:
        database: someDatabase
        password: somePassword
        server: someServer
        table: someTable
        type: Microsoft.Sql/Server/Database
        user: <user>
      jobName: sj6458
      outputName: output1755
      resourceGroupName: sjrg2157

```

{{% /example %}}
{{% example %}}
### Create an Azure Table output
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var output = new AzureNative.StreamAnalytics.Output("output", new()
    {
        Datasource = new AzureNative.StreamAnalytics.Inputs.AzureTableOutputDataSourceArgs
        {
            AccountKey = "accountKey==",
            AccountName = "someAccountName",
            BatchSize = 25,
            ColumnsToRemove = new[]
            {
                "column1",
                "column2",
            },
            PartitionKey = "partitionKey",
            RowKey = "rowKey",
            Table = "samples",
            Type = "Microsoft.Storage/Table",
        },
        JobName = "sj2790",
        OutputName = "output958",
        ResourceGroupName = "sjrg5176",
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
		_, err := streamanalytics.NewOutput(ctx, "output", &streamanalytics.OutputArgs{
			Datasource: streamanalytics.AzureTableOutputDataSource{
				AccountKey:  "accountKey==",
				AccountName: "someAccountName",
				BatchSize:   25,
				ColumnsToRemove: []string{
					"column1",
					"column2",
				},
				PartitionKey: "partitionKey",
				RowKey:       "rowKey",
				Table:        "samples",
				Type:         "Microsoft.Storage/Table",
			},
			JobName:           pulumi.String("sj2790"),
			OutputName:        pulumi.String("output958"),
			ResourceGroupName: pulumi.String("sjrg5176"),
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
import com.pulumi.azurenative.streamanalytics.Output;
import com.pulumi.azurenative.streamanalytics.OutputArgs;
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
        var output = new Output("output", OutputArgs.builder()        
            .datasource(Map.ofEntries(
                Map.entry("accountKey", "accountKey=="),
                Map.entry("accountName", "someAccountName"),
                Map.entry("batchSize", 25),
                Map.entry("columnsToRemove",                 
                    "column1",
                    "column2"),
                Map.entry("partitionKey", "partitionKey"),
                Map.entry("rowKey", "rowKey"),
                Map.entry("table", "samples"),
                Map.entry("type", "Microsoft.Storage/Table")
            ))
            .jobName("sj2790")
            .outputName("output958")
            .resourceGroupName("sjrg5176")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const output = new azure_native.streamanalytics.Output("output", {
    datasource: {
        accountKey: "accountKey==",
        accountName: "someAccountName",
        batchSize: 25,
        columnsToRemove: [
            "column1",
            "column2",
        ],
        partitionKey: "partitionKey",
        rowKey: "rowKey",
        table: "samples",
        type: "Microsoft.Storage/Table",
    },
    jobName: "sj2790",
    outputName: "output958",
    resourceGroupName: "sjrg5176",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

output = azure_native.streamanalytics.Output("output",
    datasource=azure_native.streamanalytics.AzureTableOutputDataSourceArgs(
        account_key="accountKey==",
        account_name="someAccountName",
        batch_size=25,
        columns_to_remove=[
            "column1",
            "column2",
        ],
        partition_key="partitionKey",
        row_key="rowKey",
        table="samples",
        type="Microsoft.Storage/Table",
    ),
    job_name="sj2790",
    output_name="output958",
    resource_group_name="sjrg5176")

```

```yaml
resources:
  output:
    type: azure-native:streamanalytics:Output
    properties:
      datasource:
        accountKey: accountKey==
        accountName: someAccountName
        batchSize: 25
        columnsToRemove:
          - column1
          - column2
        partitionKey: partitionKey
        rowKey: rowKey
        table: samples
        type: Microsoft.Storage/Table
      jobName: sj2790
      outputName: output958
      resourceGroupName: sjrg5176

```

{{% /example %}}
{{% example %}}
### Create an Event Hub output with JSON serialization
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var output = new AzureNative.StreamAnalytics.Output("output", new()
    {
        Datasource = new AzureNative.StreamAnalytics.Inputs.EventHubOutputDataSourceArgs
        {
            EventHubName = "sdkeventhub",
            PartitionKey = "partitionKey",
            ServiceBusNamespace = "sdktest",
            SharedAccessPolicyKey = "sharedAccessPolicyKey=",
            SharedAccessPolicyName = "RootManageSharedAccessKey",
            Type = "Microsoft.ServiceBus/EventHub",
        },
        JobName = "sj3310",
        OutputName = "output5195",
        ResourceGroupName = "sjrg6912",
        Serialization = new AzureNative.StreamAnalytics.Inputs.JsonSerializationArgs
        {
            Encoding = "UTF8",
            Format = "Array",
            Type = "Json",
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
		_, err := streamanalytics.NewOutput(ctx, "output", &streamanalytics.OutputArgs{
			Datasource: streamanalytics.EventHubOutputDataSource{
				EventHubName:           "sdkeventhub",
				PartitionKey:           "partitionKey",
				ServiceBusNamespace:    "sdktest",
				SharedAccessPolicyKey:  "sharedAccessPolicyKey=",
				SharedAccessPolicyName: "RootManageSharedAccessKey",
				Type:                   "Microsoft.ServiceBus/EventHub",
			},
			JobName:           pulumi.String("sj3310"),
			OutputName:        pulumi.String("output5195"),
			ResourceGroupName: pulumi.String("sjrg6912"),
			Serialization: streamanalytics.JsonSerialization{
				Encoding: "UTF8",
				Format:   "Array",
				Type:     "Json",
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
import com.pulumi.azurenative.streamanalytics.Output;
import com.pulumi.azurenative.streamanalytics.OutputArgs;
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
        var output = new Output("output", OutputArgs.builder()        
            .datasource(Map.ofEntries(
                Map.entry("eventHubName", "sdkeventhub"),
                Map.entry("partitionKey", "partitionKey"),
                Map.entry("serviceBusNamespace", "sdktest"),
                Map.entry("sharedAccessPolicyKey", "sharedAccessPolicyKey="),
                Map.entry("sharedAccessPolicyName", "RootManageSharedAccessKey"),
                Map.entry("type", "Microsoft.ServiceBus/EventHub")
            ))
            .jobName("sj3310")
            .outputName("output5195")
            .resourceGroupName("sjrg6912")
            .serialization(Map.ofEntries(
                Map.entry("encoding", "UTF8"),
                Map.entry("format", "Array"),
                Map.entry("type", "Json")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const output = new azure_native.streamanalytics.Output("output", {
    datasource: {
        eventHubName: "sdkeventhub",
        partitionKey: "partitionKey",
        serviceBusNamespace: "sdktest",
        sharedAccessPolicyKey: "sharedAccessPolicyKey=",
        sharedAccessPolicyName: "RootManageSharedAccessKey",
        type: "Microsoft.ServiceBus/EventHub",
    },
    jobName: "sj3310",
    outputName: "output5195",
    resourceGroupName: "sjrg6912",
    serialization: {
        encoding: "UTF8",
        format: "Array",
        type: "Json",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

output = azure_native.streamanalytics.Output("output",
    datasource=azure_native.streamanalytics.EventHubOutputDataSourceArgs(
        event_hub_name="sdkeventhub",
        partition_key="partitionKey",
        service_bus_namespace="sdktest",
        shared_access_policy_key="sharedAccessPolicyKey=",
        shared_access_policy_name="RootManageSharedAccessKey",
        type="Microsoft.ServiceBus/EventHub",
    ),
    job_name="sj3310",
    output_name="output5195",
    resource_group_name="sjrg6912",
    serialization=azure_native.streamanalytics.JsonSerializationArgs(
        encoding="UTF8",
        format="Array",
        type="Json",
    ))

```

```yaml
resources:
  output:
    type: azure-native:streamanalytics:Output
    properties:
      datasource:
        eventHubName: sdkeventhub
        partitionKey: partitionKey
        serviceBusNamespace: sdktest
        sharedAccessPolicyKey: sharedAccessPolicyKey=
        sharedAccessPolicyName: RootManageSharedAccessKey
        type: Microsoft.ServiceBus/EventHub
      jobName: sj3310
      outputName: output5195
      resourceGroupName: sjrg6912
      serialization:
        encoding: UTF8
        format: Array
        type: Json

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:streamanalytics:Output output5195 /subscriptions/56b5e0a9-b645-407d-99b0-c64f86013e3d/resourceGroups/sjrg6912/providers/Microsoft.StreamAnalytics/streamingjobs/sj3310/outputs/output5195 
```
