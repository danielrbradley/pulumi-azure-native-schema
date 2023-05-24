Single item in List or Get Event Hub operation
API Version: 2021-11-01.
Previous API Version: 2017-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### EventHubCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var eventHub = new AzureNative.EventHub.EventHub("eventHub", new()
    {
        CaptureDescription = new AzureNative.EventHub.Inputs.CaptureDescriptionArgs
        {
            Destination = new AzureNative.EventHub.Inputs.DestinationArgs
            {
                ArchiveNameFormat = "{Namespace}/{EventHub}/{PartitionId}/{Year}/{Month}/{Day}/{Hour}/{Minute}/{Second}",
                BlobContainer = "container",
                Name = "EventHubArchive.AzureBlockBlob",
                StorageAccountResourceId = "/subscriptions/e2f361f0-3b27-4503-a9cc-21cfba380093/resourceGroups/Default-Storage-SouthCentralUS/providers/Microsoft.ClassicStorage/storageAccounts/arjunteststorage",
            },
            Enabled = true,
            Encoding = AzureNative.EventHub.EncodingCaptureDescription.Avro,
            IntervalInSeconds = 120,
            SizeLimitInBytes = 10485763,
        },
        EventHubName = "sdk-EventHub-6547",
        MessageRetentionInDays = 4,
        NamespaceName = "sdk-Namespace-5357",
        PartitionCount = 4,
        ResourceGroupName = "Default-NotificationHubs-AustraliaEast",
        Status = AzureNative.EventHub.EntityStatus.Active,
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
		_, err := eventhub.NewEventHub(ctx, "eventHub", &eventhub.EventHubArgs{
			CaptureDescription: eventhub.CaptureDescriptionResponse{
				Destination: &eventhub.DestinationArgs{
					ArchiveNameFormat:        pulumi.String("{Namespace}/{EventHub}/{PartitionId}/{Year}/{Month}/{Day}/{Hour}/{Minute}/{Second}"),
					BlobContainer:            pulumi.String("container"),
					Name:                     pulumi.String("EventHubArchive.AzureBlockBlob"),
					StorageAccountResourceId: pulumi.String("/subscriptions/e2f361f0-3b27-4503-a9cc-21cfba380093/resourceGroups/Default-Storage-SouthCentralUS/providers/Microsoft.ClassicStorage/storageAccounts/arjunteststorage"),
				},
				Enabled:           pulumi.Bool(true),
				Encoding:          eventhub.EncodingCaptureDescriptionAvro,
				IntervalInSeconds: pulumi.Int(120),
				SizeLimitInBytes:  pulumi.Int(10485763),
			},
			EventHubName:           pulumi.String("sdk-EventHub-6547"),
			MessageRetentionInDays: pulumi.Float64(4),
			NamespaceName:          pulumi.String("sdk-Namespace-5357"),
			PartitionCount:         pulumi.Float64(4),
			ResourceGroupName:      pulumi.String("Default-NotificationHubs-AustraliaEast"),
			Status:                 eventhub.EntityStatusActive,
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
import com.pulumi.azurenative.eventhub.EventHub;
import com.pulumi.azurenative.eventhub.EventHubArgs;
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
        var eventHub = new EventHub("eventHub", EventHubArgs.builder()        
            .captureDescription(Map.ofEntries(
                Map.entry("destination", Map.ofEntries(
                    Map.entry("archiveNameFormat", "{Namespace}/{EventHub}/{PartitionId}/{Year}/{Month}/{Day}/{Hour}/{Minute}/{Second}"),
                    Map.entry("blobContainer", "container"),
                    Map.entry("name", "EventHubArchive.AzureBlockBlob"),
                    Map.entry("storageAccountResourceId", "/subscriptions/e2f361f0-3b27-4503-a9cc-21cfba380093/resourceGroups/Default-Storage-SouthCentralUS/providers/Microsoft.ClassicStorage/storageAccounts/arjunteststorage")
                )),
                Map.entry("enabled", true),
                Map.entry("encoding", "Avro"),
                Map.entry("intervalInSeconds", 120),
                Map.entry("sizeLimitInBytes", 10485763)
            ))
            .eventHubName("sdk-EventHub-6547")
            .messageRetentionInDays(4)
            .namespaceName("sdk-Namespace-5357")
            .partitionCount(4)
            .resourceGroupName("Default-NotificationHubs-AustraliaEast")
            .status("Active")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const eventHub = new azure_native.eventhub.EventHub("eventHub", {
    captureDescription: {
        destination: {
            archiveNameFormat: "{Namespace}/{EventHub}/{PartitionId}/{Year}/{Month}/{Day}/{Hour}/{Minute}/{Second}",
            blobContainer: "container",
            name: "EventHubArchive.AzureBlockBlob",
            storageAccountResourceId: "/subscriptions/e2f361f0-3b27-4503-a9cc-21cfba380093/resourceGroups/Default-Storage-SouthCentralUS/providers/Microsoft.ClassicStorage/storageAccounts/arjunteststorage",
        },
        enabled: true,
        encoding: azure_native.eventhub.EncodingCaptureDescription.Avro,
        intervalInSeconds: 120,
        sizeLimitInBytes: 10485763,
    },
    eventHubName: "sdk-EventHub-6547",
    messageRetentionInDays: 4,
    namespaceName: "sdk-Namespace-5357",
    partitionCount: 4,
    resourceGroupName: "Default-NotificationHubs-AustraliaEast",
    status: azure_native.eventhub.EntityStatus.Active,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

event_hub = azure_native.eventhub.EventHub("eventHub",
    capture_description=azure_native.eventhub.CaptureDescriptionResponseArgs(
        destination=azure_native.eventhub.DestinationArgs(
            archive_name_format="{Namespace}/{EventHub}/{PartitionId}/{Year}/{Month}/{Day}/{Hour}/{Minute}/{Second}",
            blob_container="container",
            name="EventHubArchive.AzureBlockBlob",
            storage_account_resource_id="/subscriptions/e2f361f0-3b27-4503-a9cc-21cfba380093/resourceGroups/Default-Storage-SouthCentralUS/providers/Microsoft.ClassicStorage/storageAccounts/arjunteststorage",
        ),
        enabled=True,
        encoding=azure_native.eventhub.EncodingCaptureDescription.AVRO,
        interval_in_seconds=120,
        size_limit_in_bytes=10485763,
    ),
    event_hub_name="sdk-EventHub-6547",
    message_retention_in_days=4,
    namespace_name="sdk-Namespace-5357",
    partition_count=4,
    resource_group_name="Default-NotificationHubs-AustraliaEast",
    status=azure_native.eventhub.EntityStatus.ACTIVE)

```

```yaml
resources:
  eventHub:
    type: azure-native:eventhub:EventHub
    properties:
      captureDescription:
        destination:
          archiveNameFormat: '{Namespace}/{EventHub}/{PartitionId}/{Year}/{Month}/{Day}/{Hour}/{Minute}/{Second}'
          blobContainer: container
          name: EventHubArchive.AzureBlockBlob
          storageAccountResourceId: /subscriptions/e2f361f0-3b27-4503-a9cc-21cfba380093/resourceGroups/Default-Storage-SouthCentralUS/providers/Microsoft.ClassicStorage/storageAccounts/arjunteststorage
        enabled: true
        encoding: Avro
        intervalInSeconds: 120
        sizeLimitInBytes: 1.0485763e+07
      eventHubName: sdk-EventHub-6547
      messageRetentionInDays: 4
      namespaceName: sdk-Namespace-5357
      partitionCount: 4
      resourceGroupName: Default-NotificationHubs-AustraliaEast
      status: Active

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:eventhub:EventHub sdk-EventHub-10 /subscriptions/e2f361f0-3b27-4503-a9cc-21cfba380093/resourceGroups/Default-NotificationHubs-AustraliaEast/providers/Microsoft.EventHub/namespaces/sdk-Namespace-716/eventhubs/sdk-EventHub-10 
```
