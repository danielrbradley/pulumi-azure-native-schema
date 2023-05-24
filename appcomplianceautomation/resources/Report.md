A class represent an AppComplianceAutomation report resource.
API Version: 2022-11-16-preview.
Previous API Version: 2022-11-16-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Report_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var report = new AzureNative.AppComplianceAutomation.Report("report", new()
    {
        Properties = new AzureNative.AppComplianceAutomation.Inputs.ReportPropertiesArgs
        {
            OfferGuid = "0000",
            Resources = new[]
            {
                new AzureNative.AppComplianceAutomation.Inputs.ResourceMetadataArgs
                {
                    ResourceId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.Network/privateEndpoints/myPrivateEndpoint",
                    Tags = 
                    {
                        { "key1", "value1" },
                    },
                },
            },
            TimeZone = "GMT Standard Time",
            TriggerTime = "2022-03-04T05:11:56.197Z",
        },
        ReportName = "testReportName",
    });

});


```

```go
package main

import (
	appcomplianceautomation "github.com/pulumi/pulumi-azure-native-sdk/appcomplianceautomation"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := appcomplianceautomation.NewReport(ctx, "report", &appcomplianceautomation.ReportArgs{
			Properties: appcomplianceautomation.ReportPropertiesResponse{
				OfferGuid: pulumi.String("0000"),
				Resources: appcomplianceautomation.ResourceMetadataArray{
					&appcomplianceautomation.ResourceMetadataArgs{
						ResourceId: pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.Network/privateEndpoints/myPrivateEndpoint"),
						Tags: pulumi.StringMap{
							"key1": pulumi.String("value1"),
						},
					},
				},
				TimeZone:    pulumi.String("GMT Standard Time"),
				TriggerTime: pulumi.String("2022-03-04T05:11:56.197Z"),
			},
			ReportName: pulumi.String("testReportName"),
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
import com.pulumi.azurenative.appcomplianceautomation.Report;
import com.pulumi.azurenative.appcomplianceautomation.ReportArgs;
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
        var report = new Report("report", ReportArgs.builder()        
            .properties(Map.ofEntries(
                Map.entry("offerGuid", "0000"),
                Map.entry("resources", Map.ofEntries(
                    Map.entry("resourceId", "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.Network/privateEndpoints/myPrivateEndpoint"),
                    Map.entry("tags", Map.of("key1", "value1"))
                )),
                Map.entry("timeZone", "GMT Standard Time"),
                Map.entry("triggerTime", "2022-03-04T05:11:56.197Z")
            ))
            .reportName("testReportName")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const report = new azure_native.appcomplianceautomation.Report("report", {
    properties: {
        offerGuid: "0000",
        resources: [{
            resourceId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.Network/privateEndpoints/myPrivateEndpoint",
            tags: {
                key1: "value1",
            },
        }],
        timeZone: "GMT Standard Time",
        triggerTime: "2022-03-04T05:11:56.197Z",
    },
    reportName: "testReportName",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

report = azure_native.appcomplianceautomation.Report("report",
    properties=azure_native.appcomplianceautomation.ReportPropertiesResponseArgs(
        offer_guid="0000",
        resources=[azure_native.appcomplianceautomation.ResourceMetadataArgs(
            resource_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.Network/privateEndpoints/myPrivateEndpoint",
            tags={
                "key1": "value1",
            },
        )],
        time_zone="GMT Standard Time",
        trigger_time="2022-03-04T05:11:56.197Z",
    ),
    report_name="testReportName")

```

```yaml
resources:
  report:
    type: azure-native:appcomplianceautomation:Report
    properties:
      properties:
        offerGuid: '0000'
        resources:
          - resourceId: /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.Network/privateEndpoints/myPrivateEndpoint
            tags:
              key1: value1
        timeZone: GMT Standard Time
        triggerTime: 2022-03-04T05:11:56.197Z
      reportName: testReportName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:appcomplianceautomation:Report testReportName /provider/Microsfot.AppComplianceAutomation/reports/testReportName 
```
