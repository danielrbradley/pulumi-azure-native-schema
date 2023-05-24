A budget resource.
API Version: 2021-10-01.
Previous API Version: 2019-10-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrUpdateBudget
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var budget = new AzureNative.Consumption.Budget("budget", new()
    {
        Amount = 100.65,
        BudgetName = "TestBudget",
        Category = "Cost",
        ETag = "\"1d34d016a593709\"",
        Filter = new AzureNative.Consumption.Inputs.BudgetFilterArgs
        {
            And = new[]
            {
                new AzureNative.Consumption.Inputs.BudgetFilterPropertiesArgs
                {
                    Dimensions = new AzureNative.Consumption.Inputs.BudgetComparisonExpressionArgs
                    {
                        Name = "ResourceId",
                        Operator = "In",
                        Values = new[]
                        {
                            "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Compute/virtualMachines/MSVM2",
                            "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Compute/virtualMachines/platformcloudplatformGeneric1",
                        },
                    },
                },
                new AzureNative.Consumption.Inputs.BudgetFilterPropertiesArgs
                {
                    Tags = new AzureNative.Consumption.Inputs.BudgetComparisonExpressionArgs
                    {
                        Name = "category",
                        Operator = "In",
                        Values = new[]
                        {
                            "Dev",
                            "Prod",
                        },
                    },
                },
                new AzureNative.Consumption.Inputs.BudgetFilterPropertiesArgs
                {
                    Tags = new AzureNative.Consumption.Inputs.BudgetComparisonExpressionArgs
                    {
                        Name = "department",
                        Operator = "In",
                        Values = new[]
                        {
                            "engineering",
                            "sales",
                        },
                    },
                },
            },
        },
        Notifications = 
        {
            { "Actual_GreaterThan_80_Percent", new AzureNative.Consumption.Inputs.NotificationArgs
            {
                ContactEmails = new[]
                {
                    "johndoe@contoso.com",
                    "janesmith@contoso.com",
                },
                ContactGroups = new[]
                {
                    "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/microsoft.insights/actionGroups/SampleActionGroup",
                },
                ContactRoles = new[]
                {
                    "Contributor",
                    "Reader",
                },
                Enabled = true,
                Locale = "en-us",
                Operator = "GreaterThan",
                Threshold = 80,
                ThresholdType = "Actual",
            } },
        },
        Scope = "subscriptions/00000000-0000-0000-0000-000000000000",
        TimeGrain = "Monthly",
        TimePeriod = new AzureNative.Consumption.Inputs.BudgetTimePeriodArgs
        {
            EndDate = "2018-10-31T00:00:00Z",
            StartDate = "2017-10-01T00:00:00Z",
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.consumption.Budget;
import com.pulumi.azurenative.consumption.BudgetArgs;
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
        var budget = new Budget("budget", BudgetArgs.builder()        
            .amount(100.65)
            .budgetName("TestBudget")
            .category("Cost")
            .eTag("\"1d34d016a593709\"")
            .filter(Map.of("and",             
                Map.of("dimensions", Map.ofEntries(
                    Map.entry("name", "ResourceId"),
                    Map.entry("operator", "In"),
                    Map.entry("values",                     
                        "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Compute/virtualMachines/MSVM2",
                        "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Compute/virtualMachines/platformcloudplatformGeneric1")
                )),
                Map.of("tags", Map.ofEntries(
                    Map.entry("name", "category"),
                    Map.entry("operator", "In"),
                    Map.entry("values",                     
                        "Dev",
                        "Prod")
                )),
                Map.of("tags", Map.ofEntries(
                    Map.entry("name", "department"),
                    Map.entry("operator", "In"),
                    Map.entry("values",                     
                        "engineering",
                        "sales")
                ))))
            .notifications(Map.of("Actual_GreaterThan_80_Percent", Map.ofEntries(
                Map.entry("contactEmails",                 
                    "johndoe@contoso.com",
                    "janesmith@contoso.com"),
                Map.entry("contactGroups", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/microsoft.insights/actionGroups/SampleActionGroup"),
                Map.entry("contactRoles",                 
                    "Contributor",
                    "Reader"),
                Map.entry("enabled", true),
                Map.entry("locale", "en-us"),
                Map.entry("operator", "GreaterThan"),
                Map.entry("threshold", 80),
                Map.entry("thresholdType", "Actual")
            )))
            .scope("subscriptions/00000000-0000-0000-0000-000000000000")
            .timeGrain("Monthly")
            .timePeriod(Map.ofEntries(
                Map.entry("endDate", "2018-10-31T00:00:00Z"),
                Map.entry("startDate", "2017-10-01T00:00:00Z")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const budget = new azure_native.consumption.Budget("budget", {
    amount: 100.65,
    budgetName: "TestBudget",
    category: "Cost",
    eTag: "\"1d34d016a593709\"",
    filter: {
        and: [
            {
                dimensions: {
                    name: "ResourceId",
                    operator: "In",
                    values: [
                        "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Compute/virtualMachines/MSVM2",
                        "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Compute/virtualMachines/platformcloudplatformGeneric1",
                    ],
                },
            },
            {
                tags: {
                    name: "category",
                    operator: "In",
                    values: [
                        "Dev",
                        "Prod",
                    ],
                },
            },
            {
                tags: {
                    name: "department",
                    operator: "In",
                    values: [
                        "engineering",
                        "sales",
                    ],
                },
            },
        ],
    },
    notifications: {
        Actual_GreaterThan_80_Percent: {
            contactEmails: [
                "johndoe@contoso.com",
                "janesmith@contoso.com",
            ],
            contactGroups: ["/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/microsoft.insights/actionGroups/SampleActionGroup"],
            contactRoles: [
                "Contributor",
                "Reader",
            ],
            enabled: true,
            locale: "en-us",
            operator: "GreaterThan",
            threshold: 80,
            thresholdType: "Actual",
        },
    },
    scope: "subscriptions/00000000-0000-0000-0000-000000000000",
    timeGrain: "Monthly",
    timePeriod: {
        endDate: "2018-10-31T00:00:00Z",
        startDate: "2017-10-01T00:00:00Z",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

budget = azure_native.consumption.Budget("budget",
    amount=100.65,
    budget_name="TestBudget",
    category="Cost",
    e_tag="\"1d34d016a593709\"",
    filter=azure_native.consumption.BudgetFilterResponseArgs(
        and_=[
            {
                "dimensions": azure_native.consumption.BudgetComparisonExpressionArgs(
                    name="ResourceId",
                    operator="In",
                    values=[
                        "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Compute/virtualMachines/MSVM2",
                        "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Compute/virtualMachines/platformcloudplatformGeneric1",
                    ],
                ),
            },
            {
                "tags": azure_native.consumption.BudgetComparisonExpressionArgs(
                    name="category",
                    operator="In",
                    values=[
                        "Dev",
                        "Prod",
                    ],
                ),
            },
            {
                "tags": azure_native.consumption.BudgetComparisonExpressionArgs(
                    name="department",
                    operator="In",
                    values=[
                        "engineering",
                        "sales",
                    ],
                ),
            },
        ],
    ),
    notifications={
        "Actual_GreaterThan_80_Percent": azure_native.consumption.NotificationArgs(
            contact_emails=[
                "johndoe@contoso.com",
                "janesmith@contoso.com",
            ],
            contact_groups=["/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/microsoft.insights/actionGroups/SampleActionGroup"],
            contact_roles=[
                "Contributor",
                "Reader",
            ],
            enabled=True,
            locale="en-us",
            operator="GreaterThan",
            threshold=80,
            threshold_type="Actual",
        ),
    },
    scope="subscriptions/00000000-0000-0000-0000-000000000000",
    time_grain="Monthly",
    time_period=azure_native.consumption.BudgetTimePeriodArgs(
        end_date="2018-10-31T00:00:00Z",
        start_date="2017-10-01T00:00:00Z",
    ))

```

```yaml
resources:
  budget:
    type: azure-native:consumption:Budget
    properties:
      amount: 100.65
      budgetName: TestBudget
      category: Cost
      eTag: '"1d34d016a593709"'
      filter:
        and:
          - dimensions:
              name: ResourceId
              operator: In
              values:
                - /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Compute/virtualMachines/MSVM2
                - /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Compute/virtualMachines/platformcloudplatformGeneric1
          - tags:
              name: category
              operator: In
              values:
                - Dev
                - Prod
          - tags:
              name: department
              operator: In
              values:
                - engineering
                - sales
      notifications:
        Actual_GreaterThan_80_Percent:
          contactEmails:
            - johndoe@contoso.com
            - janesmith@contoso.com
          contactGroups:
            - /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/microsoft.insights/actionGroups/SampleActionGroup
          contactRoles:
            - Contributor
            - Reader
          enabled: true
          locale: en-us
          operator: GreaterThan
          threshold: 80
          thresholdType: Actual
      scope: subscriptions/00000000-0000-0000-0000-000000000000
      timeGrain: Monthly
      timePeriod:
        endDate: 2018-10-31T00:00:00Z
        startDate: 2017-10-01T00:00:00Z

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:consumption:Budget TestBudget subscriptions/00000000-0000-0000-0000-000000000000/providers/Microsoft.Consumption/budgets/TestBudget 
```
