The batch configuration resource definition.
API Version: 2019-05-01.
Previous API Version: 2019-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a batch configuration
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var integrationAccountBatchConfiguration = new AzureNative.Logic.IntegrationAccountBatchConfiguration("integrationAccountBatchConfiguration", new()
    {
        BatchConfigurationName = "testBatchConfiguration",
        IntegrationAccountName = "testIntegrationAccount",
        Location = "westus",
        Properties = new AzureNative.Logic.Inputs.BatchConfigurationPropertiesArgs
        {
            BatchGroupName = "DEFAULT",
            ReleaseCriteria = new AzureNative.Logic.Inputs.BatchReleaseCriteriaArgs
            {
                BatchSize = 234567,
                MessageCount = 10,
                Recurrence = new AzureNative.Logic.Inputs.WorkflowTriggerRecurrenceArgs
                {
                    Frequency = "Minute",
                    Interval = 1,
                    StartTime = "2017-03-24T11:43:00",
                    TimeZone = "India Standard Time",
                },
            },
        },
        ResourceGroupName = "testResourceGroup",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.logic.IntegrationAccountBatchConfiguration;
import com.pulumi.azurenative.logic.IntegrationAccountBatchConfigurationArgs;
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
        var integrationAccountBatchConfiguration = new IntegrationAccountBatchConfiguration("integrationAccountBatchConfiguration", IntegrationAccountBatchConfigurationArgs.builder()        
            .batchConfigurationName("testBatchConfiguration")
            .integrationAccountName("testIntegrationAccount")
            .location("westus")
            .properties(Map.ofEntries(
                Map.entry("batchGroupName", "DEFAULT"),
                Map.entry("releaseCriteria", Map.ofEntries(
                    Map.entry("batchSize", 234567),
                    Map.entry("messageCount", 10),
                    Map.entry("recurrence", Map.ofEntries(
                        Map.entry("frequency", "Minute"),
                        Map.entry("interval", 1),
                        Map.entry("startTime", "2017-03-24T11:43:00"),
                        Map.entry("timeZone", "India Standard Time")
                    ))
                ))
            ))
            .resourceGroupName("testResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const integrationAccountBatchConfiguration = new azure_native.logic.IntegrationAccountBatchConfiguration("integrationAccountBatchConfiguration", {
    batchConfigurationName: "testBatchConfiguration",
    integrationAccountName: "testIntegrationAccount",
    location: "westus",
    properties: {
        batchGroupName: "DEFAULT",
        releaseCriteria: {
            batchSize: 234567,
            messageCount: 10,
            recurrence: {
                frequency: "Minute",
                interval: 1,
                startTime: "2017-03-24T11:43:00",
                timeZone: "India Standard Time",
            },
        },
    },
    resourceGroupName: "testResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

integration_account_batch_configuration = azure_native.logic.IntegrationAccountBatchConfiguration("integrationAccountBatchConfiguration",
    batch_configuration_name="testBatchConfiguration",
    integration_account_name="testIntegrationAccount",
    location="westus",
    properties=azure_native.logic.BatchConfigurationPropertiesResponseArgs(
        batch_group_name="DEFAULT",
        release_criteria={
            "batchSize": 234567,
            "messageCount": 10,
            "recurrence": azure_native.logic.WorkflowTriggerRecurrenceArgs(
                frequency="Minute",
                interval=1,
                start_time="2017-03-24T11:43:00",
                time_zone="India Standard Time",
            ),
        },
    ),
    resource_group_name="testResourceGroup")

```

```yaml
resources:
  integrationAccountBatchConfiguration:
    type: azure-native:logic:IntegrationAccountBatchConfiguration
    properties:
      batchConfigurationName: testBatchConfiguration
      integrationAccountName: testIntegrationAccount
      location: westus
      properties:
        batchGroupName: DEFAULT
        releaseCriteria:
          batchSize: 234567
          messageCount: 10
          recurrence:
            frequency: Minute
            interval: 1
            startTime: 2017-03-24T11:43:00
            timeZone: India Standard Time
      resourceGroupName: testResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:logic:IntegrationAccountBatchConfiguration testBatchConfiguration /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testResourceGroup/providers/Microsoft.Logic/integrationAccounts/testIntegrationAccount/batchConfigurations/testBatchConfiguration 
```
