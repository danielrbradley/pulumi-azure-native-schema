Properties that define a Continuous Export configuration.
API Version: 2015-05-01.
Previous API Version: 2015-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ExportConfigurationUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var exportConfiguration = new AzureNative.Insights.ExportConfiguration("exportConfiguration", new()
    {
        DestinationAccountId = "/subscriptions/subid/resourceGroups/my-resource-group/providers/Microsoft.ClassicStorage/storageAccounts/mystorageblob",
        DestinationAddress = "https://mystorageblob.blob.core.windows.net/fchentest?sv=2015-04-05&sr=c&sig=token",
        DestinationStorageLocationId = "eastus",
        DestinationStorageSubscriptionId = "subid",
        DestinationType = "Blob",
        ExportId = "uGOoki0jQsyEs3IdQ83Q4QsNr4=",
        IsEnabled = "true",
        NotificationQueueEnabled = "false",
        NotificationQueueUri = "",
        RecordTypes = "Requests, Event, Exceptions, Metrics, PageViews, PageViewPerformance, Rdd, PerformanceCounters, Availability",
        ResourceGroupName = "my-resource-group",
        ResourceName = "my-component",
    });

});


```

```go
package main

import (
	insights "github.com/pulumi/pulumi-azure-native-sdk/insights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := insights.NewExportConfiguration(ctx, "exportConfiguration", &insights.ExportConfigurationArgs{
			DestinationAccountId:             pulumi.String("/subscriptions/subid/resourceGroups/my-resource-group/providers/Microsoft.ClassicStorage/storageAccounts/mystorageblob"),
			DestinationAddress:               pulumi.String("https://mystorageblob.blob.core.windows.net/fchentest?sv=2015-04-05&sr=c&sig=token"),
			DestinationStorageLocationId:     pulumi.String("eastus"),
			DestinationStorageSubscriptionId: pulumi.String("subid"),
			DestinationType:                  pulumi.String("Blob"),
			ExportId:                         pulumi.String("uGOoki0jQsyEs3IdQ83Q4QsNr4="),
			IsEnabled:                        pulumi.String("true"),
			NotificationQueueEnabled:         pulumi.String("false"),
			NotificationQueueUri:             pulumi.String(""),
			RecordTypes:                      pulumi.String("Requests, Event, Exceptions, Metrics, PageViews, PageViewPerformance, Rdd, PerformanceCounters, Availability"),
			ResourceGroupName:                pulumi.String("my-resource-group"),
			ResourceName:                     pulumi.String("my-component"),
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
import com.pulumi.azurenative.insights.ExportConfiguration;
import com.pulumi.azurenative.insights.ExportConfigurationArgs;
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
        var exportConfiguration = new ExportConfiguration("exportConfiguration", ExportConfigurationArgs.builder()        
            .destinationAccountId("/subscriptions/subid/resourceGroups/my-resource-group/providers/Microsoft.ClassicStorage/storageAccounts/mystorageblob")
            .destinationAddress("https://mystorageblob.blob.core.windows.net/fchentest?sv=2015-04-05&sr=c&sig=token")
            .destinationStorageLocationId("eastus")
            .destinationStorageSubscriptionId("subid")
            .destinationType("Blob")
            .exportId("uGOoki0jQsyEs3IdQ83Q4QsNr4=")
            .isEnabled("true")
            .notificationQueueEnabled("false")
            .notificationQueueUri("")
            .recordTypes("Requests, Event, Exceptions, Metrics, PageViews, PageViewPerformance, Rdd, PerformanceCounters, Availability")
            .resourceGroupName("my-resource-group")
            .resourceName("my-component")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const exportConfiguration = new azure_native.insights.ExportConfiguration("exportConfiguration", {
    destinationAccountId: "/subscriptions/subid/resourceGroups/my-resource-group/providers/Microsoft.ClassicStorage/storageAccounts/mystorageblob",
    destinationAddress: "https://mystorageblob.blob.core.windows.net/fchentest?sv=2015-04-05&sr=c&sig=token",
    destinationStorageLocationId: "eastus",
    destinationStorageSubscriptionId: "subid",
    destinationType: "Blob",
    exportId: "uGOoki0jQsyEs3IdQ83Q4QsNr4=",
    isEnabled: "true",
    notificationQueueEnabled: "false",
    notificationQueueUri: "",
    recordTypes: "Requests, Event, Exceptions, Metrics, PageViews, PageViewPerformance, Rdd, PerformanceCounters, Availability",
    resourceGroupName: "my-resource-group",
    resourceName: "my-component",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

export_configuration = azure_native.insights.ExportConfiguration("exportConfiguration",
    destination_account_id="/subscriptions/subid/resourceGroups/my-resource-group/providers/Microsoft.ClassicStorage/storageAccounts/mystorageblob",
    destination_address="https://mystorageblob.blob.core.windows.net/fchentest?sv=2015-04-05&sr=c&sig=token",
    destination_storage_location_id="eastus",
    destination_storage_subscription_id="subid",
    destination_type="Blob",
    export_id="uGOoki0jQsyEs3IdQ83Q4QsNr4=",
    is_enabled="true",
    notification_queue_enabled="false",
    notification_queue_uri="",
    record_types="Requests, Event, Exceptions, Metrics, PageViews, PageViewPerformance, Rdd, PerformanceCounters, Availability",
    resource_group_name="my-resource-group",
    resource_name_="my-component")

```

```yaml
resources:
  exportConfiguration:
    type: azure-native:insights:ExportConfiguration
    properties:
      destinationAccountId: /subscriptions/subid/resourceGroups/my-resource-group/providers/Microsoft.ClassicStorage/storageAccounts/mystorageblob
      destinationAddress: https://mystorageblob.blob.core.windows.net/fchentest?sv=2015-04-05&sr=c&sig=token
      destinationStorageLocationId: eastus
      destinationStorageSubscriptionId: subid
      destinationType: Blob
      exportId: uGOoki0jQsyEs3IdQ83Q4QsNr4=
      isEnabled: 'true'
      notificationQueueEnabled: 'false'
      notificationQueueUri:
      recordTypes: Requests, Event, Exceptions, Metrics, PageViews, PageViewPerformance, Rdd, PerformanceCounters, Availability
      resourceGroupName: my-resource-group
      resourceName: my-component

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:insights:ExportConfiguration myresource1 /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Insights/components/{resourceName}/exportconfiguration/{exportId} 
```
