An export resource.
API Version: 2022-10-01.
Previous API Version: 2020-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ExportCreateOrUpdateByBillingAccount
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var export = new AzureNative.CostManagement.Export("export", new()
    {
        Definition = new AzureNative.CostManagement.Inputs.ExportDefinitionArgs
        {
            DataSet = new AzureNative.CostManagement.Inputs.ExportDatasetArgs
            {
                Configuration = new AzureNative.CostManagement.Inputs.ExportDatasetConfigurationArgs
                {
                    Columns = new[]
                    {
                        "Date",
                        "MeterId",
                        "ResourceId",
                        "ResourceLocation",
                        "Quantity",
                    },
                },
                Granularity = "Daily",
            },
            Timeframe = "MonthToDate",
            Type = "ActualCost",
        },
        DeliveryInfo = new AzureNative.CostManagement.Inputs.ExportDeliveryInfoArgs
        {
            Destination = new AzureNative.CostManagement.Inputs.ExportDeliveryDestinationArgs
            {
                Container = "exports",
                ResourceId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Storage/storageAccounts/ccmeastusdiag182",
                RootFolderPath = "ad-hoc",
            },
        },
        ExportName = "TestExport",
        Format = "Csv",
        Schedule = new AzureNative.CostManagement.Inputs.ExportScheduleArgs
        {
            Recurrence = "Weekly",
            RecurrencePeriod = new AzureNative.CostManagement.Inputs.ExportRecurrencePeriodArgs
            {
                From = "2020-06-01T00:00:00Z",
                To = "2020-10-31T00:00:00Z",
            },
            Status = "Active",
        },
        Scope = "providers/Microsoft.Billing/billingAccounts/123456",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.costmanagement.Export;
import com.pulumi.azurenative.costmanagement.ExportArgs;
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
        var export = new Export("export", ExportArgs.builder()        
            .definition(Map.ofEntries(
                Map.entry("dataSet", Map.ofEntries(
                    Map.entry("configuration", Map.of("columns",                     
                        "Date",
                        "MeterId",
                        "ResourceId",
                        "ResourceLocation",
                        "Quantity")),
                    Map.entry("granularity", "Daily")
                )),
                Map.entry("timeframe", "MonthToDate"),
                Map.entry("type", "ActualCost")
            ))
            .deliveryInfo(Map.of("destination", Map.ofEntries(
                Map.entry("container", "exports"),
                Map.entry("resourceId", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Storage/storageAccounts/ccmeastusdiag182"),
                Map.entry("rootFolderPath", "ad-hoc")
            )))
            .exportName("TestExport")
            .format("Csv")
            .schedule(Map.ofEntries(
                Map.entry("recurrence", "Weekly"),
                Map.entry("recurrencePeriod", Map.ofEntries(
                    Map.entry("from", "2020-06-01T00:00:00Z"),
                    Map.entry("to", "2020-10-31T00:00:00Z")
                )),
                Map.entry("status", "Active")
            ))
            .scope("providers/Microsoft.Billing/billingAccounts/123456")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const _export = new azure_native.costmanagement.Export("export", {
    definition: {
        dataSet: {
            configuration: {
                columns: [
                    "Date",
                    "MeterId",
                    "ResourceId",
                    "ResourceLocation",
                    "Quantity",
                ],
            },
            granularity: "Daily",
        },
        timeframe: "MonthToDate",
        type: "ActualCost",
    },
    deliveryInfo: {
        destination: {
            container: "exports",
            resourceId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Storage/storageAccounts/ccmeastusdiag182",
            rootFolderPath: "ad-hoc",
        },
    },
    exportName: "TestExport",
    format: "Csv",
    schedule: {
        recurrence: "Weekly",
        recurrencePeriod: {
            from: "2020-06-01T00:00:00Z",
            to: "2020-10-31T00:00:00Z",
        },
        status: "Active",
    },
    scope: "providers/Microsoft.Billing/billingAccounts/123456",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

export = azure_native.costmanagement.Export("export",
    definition=azure_native.costmanagement.ExportDefinitionResponseArgs(
        data_set={
            "configuration": azure_native.costmanagement.ExportDatasetConfigurationArgs(
                columns=[
                    "Date",
                    "MeterId",
                    "ResourceId",
                    "ResourceLocation",
                    "Quantity",
                ],
            ),
            "granularity": "Daily",
        },
        timeframe="MonthToDate",
        type="ActualCost",
    ),
    delivery_info=azure_native.costmanagement.ExportDeliveryInfoResponseArgs(
        destination=azure_native.costmanagement.ExportDeliveryDestinationArgs(
            container="exports",
            resource_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Storage/storageAccounts/ccmeastusdiag182",
            root_folder_path="ad-hoc",
        ),
    ),
    export_name="TestExport",
    format="Csv",
    schedule=azure_native.costmanagement.ExportScheduleResponseArgs(
        recurrence="Weekly",
        recurrence_period=azure_native.costmanagement.ExportRecurrencePeriodArgs(
            from_="2020-06-01T00:00:00Z",
            to="2020-10-31T00:00:00Z",
        ),
        status="Active",
    ),
    scope="providers/Microsoft.Billing/billingAccounts/123456")

```

```yaml
resources:
  export:
    type: azure-native:costmanagement:Export
    properties:
      definition:
        dataSet:
          configuration:
            columns:
              - Date
              - MeterId
              - ResourceId
              - ResourceLocation
              - Quantity
          granularity: Daily
        timeframe: MonthToDate
        type: ActualCost
      deliveryInfo:
        destination:
          container: exports
          resourceId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Storage/storageAccounts/ccmeastusdiag182
          rootFolderPath: ad-hoc
      exportName: TestExport
      format: Csv
      schedule:
        recurrence: Weekly
        recurrencePeriod:
          from: 2020-06-01T00:00:00Z
          to: 2020-10-31T00:00:00Z
        status: Active
      scope: providers/Microsoft.Billing/billingAccounts/123456

```

{{% /example %}}
{{% example %}}
### ExportCreateOrUpdateByDepartment
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var export = new AzureNative.CostManagement.Export("export", new()
    {
        Definition = new AzureNative.CostManagement.Inputs.ExportDefinitionArgs
        {
            DataSet = new AzureNative.CostManagement.Inputs.ExportDatasetArgs
            {
                Configuration = new AzureNative.CostManagement.Inputs.ExportDatasetConfigurationArgs
                {
                    Columns = new[]
                    {
                        "Date",
                        "MeterId",
                        "ResourceId",
                        "ResourceLocation",
                        "Quantity",
                    },
                },
                Granularity = "Daily",
            },
            Timeframe = "MonthToDate",
            Type = "ActualCost",
        },
        DeliveryInfo = new AzureNative.CostManagement.Inputs.ExportDeliveryInfoArgs
        {
            Destination = new AzureNative.CostManagement.Inputs.ExportDeliveryDestinationArgs
            {
                Container = "exports",
                ResourceId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Storage/storageAccounts/ccmeastusdiag182",
                RootFolderPath = "ad-hoc",
            },
        },
        ExportName = "TestExport",
        Format = "Csv",
        Schedule = new AzureNative.CostManagement.Inputs.ExportScheduleArgs
        {
            Recurrence = "Weekly",
            RecurrencePeriod = new AzureNative.CostManagement.Inputs.ExportRecurrencePeriodArgs
            {
                From = "2020-06-01T00:00:00Z",
                To = "2020-10-31T00:00:00Z",
            },
            Status = "Active",
        },
        Scope = "providers/Microsoft.Billing/billingAccounts/12/departments/1234",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.costmanagement.Export;
import com.pulumi.azurenative.costmanagement.ExportArgs;
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
        var export = new Export("export", ExportArgs.builder()        
            .definition(Map.ofEntries(
                Map.entry("dataSet", Map.ofEntries(
                    Map.entry("configuration", Map.of("columns",                     
                        "Date",
                        "MeterId",
                        "ResourceId",
                        "ResourceLocation",
                        "Quantity")),
                    Map.entry("granularity", "Daily")
                )),
                Map.entry("timeframe", "MonthToDate"),
                Map.entry("type", "ActualCost")
            ))
            .deliveryInfo(Map.of("destination", Map.ofEntries(
                Map.entry("container", "exports"),
                Map.entry("resourceId", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Storage/storageAccounts/ccmeastusdiag182"),
                Map.entry("rootFolderPath", "ad-hoc")
            )))
            .exportName("TestExport")
            .format("Csv")
            .schedule(Map.ofEntries(
                Map.entry("recurrence", "Weekly"),
                Map.entry("recurrencePeriod", Map.ofEntries(
                    Map.entry("from", "2020-06-01T00:00:00Z"),
                    Map.entry("to", "2020-10-31T00:00:00Z")
                )),
                Map.entry("status", "Active")
            ))
            .scope("providers/Microsoft.Billing/billingAccounts/12/departments/1234")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const _export = new azure_native.costmanagement.Export("export", {
    definition: {
        dataSet: {
            configuration: {
                columns: [
                    "Date",
                    "MeterId",
                    "ResourceId",
                    "ResourceLocation",
                    "Quantity",
                ],
            },
            granularity: "Daily",
        },
        timeframe: "MonthToDate",
        type: "ActualCost",
    },
    deliveryInfo: {
        destination: {
            container: "exports",
            resourceId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Storage/storageAccounts/ccmeastusdiag182",
            rootFolderPath: "ad-hoc",
        },
    },
    exportName: "TestExport",
    format: "Csv",
    schedule: {
        recurrence: "Weekly",
        recurrencePeriod: {
            from: "2020-06-01T00:00:00Z",
            to: "2020-10-31T00:00:00Z",
        },
        status: "Active",
    },
    scope: "providers/Microsoft.Billing/billingAccounts/12/departments/1234",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

export = azure_native.costmanagement.Export("export",
    definition=azure_native.costmanagement.ExportDefinitionResponseArgs(
        data_set={
            "configuration": azure_native.costmanagement.ExportDatasetConfigurationArgs(
                columns=[
                    "Date",
                    "MeterId",
                    "ResourceId",
                    "ResourceLocation",
                    "Quantity",
                ],
            ),
            "granularity": "Daily",
        },
        timeframe="MonthToDate",
        type="ActualCost",
    ),
    delivery_info=azure_native.costmanagement.ExportDeliveryInfoResponseArgs(
        destination=azure_native.costmanagement.ExportDeliveryDestinationArgs(
            container="exports",
            resource_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Storage/storageAccounts/ccmeastusdiag182",
            root_folder_path="ad-hoc",
        ),
    ),
    export_name="TestExport",
    format="Csv",
    schedule=azure_native.costmanagement.ExportScheduleResponseArgs(
        recurrence="Weekly",
        recurrence_period=azure_native.costmanagement.ExportRecurrencePeriodArgs(
            from_="2020-06-01T00:00:00Z",
            to="2020-10-31T00:00:00Z",
        ),
        status="Active",
    ),
    scope="providers/Microsoft.Billing/billingAccounts/12/departments/1234")

```

```yaml
resources:
  export:
    type: azure-native:costmanagement:Export
    properties:
      definition:
        dataSet:
          configuration:
            columns:
              - Date
              - MeterId
              - ResourceId
              - ResourceLocation
              - Quantity
          granularity: Daily
        timeframe: MonthToDate
        type: ActualCost
      deliveryInfo:
        destination:
          container: exports
          resourceId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Storage/storageAccounts/ccmeastusdiag182
          rootFolderPath: ad-hoc
      exportName: TestExport
      format: Csv
      schedule:
        recurrence: Weekly
        recurrencePeriod:
          from: 2020-06-01T00:00:00Z
          to: 2020-10-31T00:00:00Z
        status: Active
      scope: providers/Microsoft.Billing/billingAccounts/12/departments/1234

```

{{% /example %}}
{{% example %}}
### ExportCreateOrUpdateByEnrollmentAccount
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var export = new AzureNative.CostManagement.Export("export", new()
    {
        Definition = new AzureNative.CostManagement.Inputs.ExportDefinitionArgs
        {
            DataSet = new AzureNative.CostManagement.Inputs.ExportDatasetArgs
            {
                Configuration = new AzureNative.CostManagement.Inputs.ExportDatasetConfigurationArgs
                {
                    Columns = new[]
                    {
                        "Date",
                        "MeterId",
                        "ResourceId",
                        "ResourceLocation",
                        "Quantity",
                    },
                },
                Granularity = "Daily",
            },
            Timeframe = "MonthToDate",
            Type = "ActualCost",
        },
        DeliveryInfo = new AzureNative.CostManagement.Inputs.ExportDeliveryInfoArgs
        {
            Destination = new AzureNative.CostManagement.Inputs.ExportDeliveryDestinationArgs
            {
                Container = "exports",
                ResourceId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Storage/storageAccounts/ccmeastusdiag182",
                RootFolderPath = "ad-hoc",
            },
        },
        ExportName = "TestExport",
        Format = "Csv",
        Schedule = new AzureNative.CostManagement.Inputs.ExportScheduleArgs
        {
            Recurrence = "Weekly",
            RecurrencePeriod = new AzureNative.CostManagement.Inputs.ExportRecurrencePeriodArgs
            {
                From = "2020-06-01T00:00:00Z",
                To = "2020-10-31T00:00:00Z",
            },
            Status = "Active",
        },
        Scope = "providers/Microsoft.Billing/billingAccounts/100/enrollmentAccounts/456",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.costmanagement.Export;
import com.pulumi.azurenative.costmanagement.ExportArgs;
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
        var export = new Export("export", ExportArgs.builder()        
            .definition(Map.ofEntries(
                Map.entry("dataSet", Map.ofEntries(
                    Map.entry("configuration", Map.of("columns",                     
                        "Date",
                        "MeterId",
                        "ResourceId",
                        "ResourceLocation",
                        "Quantity")),
                    Map.entry("granularity", "Daily")
                )),
                Map.entry("timeframe", "MonthToDate"),
                Map.entry("type", "ActualCost")
            ))
            .deliveryInfo(Map.of("destination", Map.ofEntries(
                Map.entry("container", "exports"),
                Map.entry("resourceId", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Storage/storageAccounts/ccmeastusdiag182"),
                Map.entry("rootFolderPath", "ad-hoc")
            )))
            .exportName("TestExport")
            .format("Csv")
            .schedule(Map.ofEntries(
                Map.entry("recurrence", "Weekly"),
                Map.entry("recurrencePeriod", Map.ofEntries(
                    Map.entry("from", "2020-06-01T00:00:00Z"),
                    Map.entry("to", "2020-10-31T00:00:00Z")
                )),
                Map.entry("status", "Active")
            ))
            .scope("providers/Microsoft.Billing/billingAccounts/100/enrollmentAccounts/456")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const _export = new azure_native.costmanagement.Export("export", {
    definition: {
        dataSet: {
            configuration: {
                columns: [
                    "Date",
                    "MeterId",
                    "ResourceId",
                    "ResourceLocation",
                    "Quantity",
                ],
            },
            granularity: "Daily",
        },
        timeframe: "MonthToDate",
        type: "ActualCost",
    },
    deliveryInfo: {
        destination: {
            container: "exports",
            resourceId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Storage/storageAccounts/ccmeastusdiag182",
            rootFolderPath: "ad-hoc",
        },
    },
    exportName: "TestExport",
    format: "Csv",
    schedule: {
        recurrence: "Weekly",
        recurrencePeriod: {
            from: "2020-06-01T00:00:00Z",
            to: "2020-10-31T00:00:00Z",
        },
        status: "Active",
    },
    scope: "providers/Microsoft.Billing/billingAccounts/100/enrollmentAccounts/456",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

export = azure_native.costmanagement.Export("export",
    definition=azure_native.costmanagement.ExportDefinitionResponseArgs(
        data_set={
            "configuration": azure_native.costmanagement.ExportDatasetConfigurationArgs(
                columns=[
                    "Date",
                    "MeterId",
                    "ResourceId",
                    "ResourceLocation",
                    "Quantity",
                ],
            ),
            "granularity": "Daily",
        },
        timeframe="MonthToDate",
        type="ActualCost",
    ),
    delivery_info=azure_native.costmanagement.ExportDeliveryInfoResponseArgs(
        destination=azure_native.costmanagement.ExportDeliveryDestinationArgs(
            container="exports",
            resource_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Storage/storageAccounts/ccmeastusdiag182",
            root_folder_path="ad-hoc",
        ),
    ),
    export_name="TestExport",
    format="Csv",
    schedule=azure_native.costmanagement.ExportScheduleResponseArgs(
        recurrence="Weekly",
        recurrence_period=azure_native.costmanagement.ExportRecurrencePeriodArgs(
            from_="2020-06-01T00:00:00Z",
            to="2020-10-31T00:00:00Z",
        ),
        status="Active",
    ),
    scope="providers/Microsoft.Billing/billingAccounts/100/enrollmentAccounts/456")

```

```yaml
resources:
  export:
    type: azure-native:costmanagement:Export
    properties:
      definition:
        dataSet:
          configuration:
            columns:
              - Date
              - MeterId
              - ResourceId
              - ResourceLocation
              - Quantity
          granularity: Daily
        timeframe: MonthToDate
        type: ActualCost
      deliveryInfo:
        destination:
          container: exports
          resourceId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Storage/storageAccounts/ccmeastusdiag182
          rootFolderPath: ad-hoc
      exportName: TestExport
      format: Csv
      schedule:
        recurrence: Weekly
        recurrencePeriod:
          from: 2020-06-01T00:00:00Z
          to: 2020-10-31T00:00:00Z
        status: Active
      scope: providers/Microsoft.Billing/billingAccounts/100/enrollmentAccounts/456

```

{{% /example %}}
{{% example %}}
### ExportCreateOrUpdateByManagementGroup
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var export = new AzureNative.CostManagement.Export("export", new()
    {
        Definition = new AzureNative.CostManagement.Inputs.ExportDefinitionArgs
        {
            DataSet = new AzureNative.CostManagement.Inputs.ExportDatasetArgs
            {
                Configuration = new AzureNative.CostManagement.Inputs.ExportDatasetConfigurationArgs
                {
                    Columns = new[]
                    {
                        "Date",
                        "MeterId",
                        "ResourceId",
                        "ResourceLocation",
                        "Quantity",
                    },
                },
                Granularity = "Daily",
            },
            Timeframe = "MonthToDate",
            Type = "ActualCost",
        },
        DeliveryInfo = new AzureNative.CostManagement.Inputs.ExportDeliveryInfoArgs
        {
            Destination = new AzureNative.CostManagement.Inputs.ExportDeliveryDestinationArgs
            {
                Container = "exports",
                ResourceId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Storage/storageAccounts/ccmeastusdiag182",
                RootFolderPath = "ad-hoc",
            },
        },
        ExportName = "TestExport",
        Format = "Csv",
        Schedule = new AzureNative.CostManagement.Inputs.ExportScheduleArgs
        {
            Recurrence = "Weekly",
            RecurrencePeriod = new AzureNative.CostManagement.Inputs.ExportRecurrencePeriodArgs
            {
                From = "2020-06-01T00:00:00Z",
                To = "2020-10-31T00:00:00Z",
            },
            Status = "Active",
        },
        Scope = "providers/Microsoft.Management/managementGroups/TestMG",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.costmanagement.Export;
import com.pulumi.azurenative.costmanagement.ExportArgs;
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
        var export = new Export("export", ExportArgs.builder()        
            .definition(Map.ofEntries(
                Map.entry("dataSet", Map.ofEntries(
                    Map.entry("configuration", Map.of("columns",                     
                        "Date",
                        "MeterId",
                        "ResourceId",
                        "ResourceLocation",
                        "Quantity")),
                    Map.entry("granularity", "Daily")
                )),
                Map.entry("timeframe", "MonthToDate"),
                Map.entry("type", "ActualCost")
            ))
            .deliveryInfo(Map.of("destination", Map.ofEntries(
                Map.entry("container", "exports"),
                Map.entry("resourceId", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Storage/storageAccounts/ccmeastusdiag182"),
                Map.entry("rootFolderPath", "ad-hoc")
            )))
            .exportName("TestExport")
            .format("Csv")
            .schedule(Map.ofEntries(
                Map.entry("recurrence", "Weekly"),
                Map.entry("recurrencePeriod", Map.ofEntries(
                    Map.entry("from", "2020-06-01T00:00:00Z"),
                    Map.entry("to", "2020-10-31T00:00:00Z")
                )),
                Map.entry("status", "Active")
            ))
            .scope("providers/Microsoft.Management/managementGroups/TestMG")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const _export = new azure_native.costmanagement.Export("export", {
    definition: {
        dataSet: {
            configuration: {
                columns: [
                    "Date",
                    "MeterId",
                    "ResourceId",
                    "ResourceLocation",
                    "Quantity",
                ],
            },
            granularity: "Daily",
        },
        timeframe: "MonthToDate",
        type: "ActualCost",
    },
    deliveryInfo: {
        destination: {
            container: "exports",
            resourceId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Storage/storageAccounts/ccmeastusdiag182",
            rootFolderPath: "ad-hoc",
        },
    },
    exportName: "TestExport",
    format: "Csv",
    schedule: {
        recurrence: "Weekly",
        recurrencePeriod: {
            from: "2020-06-01T00:00:00Z",
            to: "2020-10-31T00:00:00Z",
        },
        status: "Active",
    },
    scope: "providers/Microsoft.Management/managementGroups/TestMG",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

export = azure_native.costmanagement.Export("export",
    definition=azure_native.costmanagement.ExportDefinitionResponseArgs(
        data_set={
            "configuration": azure_native.costmanagement.ExportDatasetConfigurationArgs(
                columns=[
                    "Date",
                    "MeterId",
                    "ResourceId",
                    "ResourceLocation",
                    "Quantity",
                ],
            ),
            "granularity": "Daily",
        },
        timeframe="MonthToDate",
        type="ActualCost",
    ),
    delivery_info=azure_native.costmanagement.ExportDeliveryInfoResponseArgs(
        destination=azure_native.costmanagement.ExportDeliveryDestinationArgs(
            container="exports",
            resource_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Storage/storageAccounts/ccmeastusdiag182",
            root_folder_path="ad-hoc",
        ),
    ),
    export_name="TestExport",
    format="Csv",
    schedule=azure_native.costmanagement.ExportScheduleResponseArgs(
        recurrence="Weekly",
        recurrence_period=azure_native.costmanagement.ExportRecurrencePeriodArgs(
            from_="2020-06-01T00:00:00Z",
            to="2020-10-31T00:00:00Z",
        ),
        status="Active",
    ),
    scope="providers/Microsoft.Management/managementGroups/TestMG")

```

```yaml
resources:
  export:
    type: azure-native:costmanagement:Export
    properties:
      definition:
        dataSet:
          configuration:
            columns:
              - Date
              - MeterId
              - ResourceId
              - ResourceLocation
              - Quantity
          granularity: Daily
        timeframe: MonthToDate
        type: ActualCost
      deliveryInfo:
        destination:
          container: exports
          resourceId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Storage/storageAccounts/ccmeastusdiag182
          rootFolderPath: ad-hoc
      exportName: TestExport
      format: Csv
      schedule:
        recurrence: Weekly
        recurrencePeriod:
          from: 2020-06-01T00:00:00Z
          to: 2020-10-31T00:00:00Z
        status: Active
      scope: providers/Microsoft.Management/managementGroups/TestMG

```

{{% /example %}}
{{% example %}}
### ExportCreateOrUpdateByResourceGroup
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var export = new AzureNative.CostManagement.Export("export", new()
    {
        Definition = new AzureNative.CostManagement.Inputs.ExportDefinitionArgs
        {
            DataSet = new AzureNative.CostManagement.Inputs.ExportDatasetArgs
            {
                Configuration = new AzureNative.CostManagement.Inputs.ExportDatasetConfigurationArgs
                {
                    Columns = new[]
                    {
                        "Date",
                        "MeterId",
                        "ResourceId",
                        "ResourceLocation",
                        "Quantity",
                    },
                },
                Granularity = "Daily",
            },
            Timeframe = "MonthToDate",
            Type = "ActualCost",
        },
        DeliveryInfo = new AzureNative.CostManagement.Inputs.ExportDeliveryInfoArgs
        {
            Destination = new AzureNative.CostManagement.Inputs.ExportDeliveryDestinationArgs
            {
                Container = "exports",
                ResourceId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Storage/storageAccounts/ccmeastusdiag182",
                RootFolderPath = "ad-hoc",
            },
        },
        ExportName = "TestExport",
        Format = "Csv",
        Schedule = new AzureNative.CostManagement.Inputs.ExportScheduleArgs
        {
            Recurrence = "Weekly",
            RecurrencePeriod = new AzureNative.CostManagement.Inputs.ExportRecurrencePeriodArgs
            {
                From = "2020-06-01T00:00:00Z",
                To = "2020-10-31T00:00:00Z",
            },
            Status = "Active",
        },
        Scope = "subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.costmanagement.Export;
import com.pulumi.azurenative.costmanagement.ExportArgs;
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
        var export = new Export("export", ExportArgs.builder()        
            .definition(Map.ofEntries(
                Map.entry("dataSet", Map.ofEntries(
                    Map.entry("configuration", Map.of("columns",                     
                        "Date",
                        "MeterId",
                        "ResourceId",
                        "ResourceLocation",
                        "Quantity")),
                    Map.entry("granularity", "Daily")
                )),
                Map.entry("timeframe", "MonthToDate"),
                Map.entry("type", "ActualCost")
            ))
            .deliveryInfo(Map.of("destination", Map.ofEntries(
                Map.entry("container", "exports"),
                Map.entry("resourceId", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Storage/storageAccounts/ccmeastusdiag182"),
                Map.entry("rootFolderPath", "ad-hoc")
            )))
            .exportName("TestExport")
            .format("Csv")
            .schedule(Map.ofEntries(
                Map.entry("recurrence", "Weekly"),
                Map.entry("recurrencePeriod", Map.ofEntries(
                    Map.entry("from", "2020-06-01T00:00:00Z"),
                    Map.entry("to", "2020-10-31T00:00:00Z")
                )),
                Map.entry("status", "Active")
            ))
            .scope("subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const _export = new azure_native.costmanagement.Export("export", {
    definition: {
        dataSet: {
            configuration: {
                columns: [
                    "Date",
                    "MeterId",
                    "ResourceId",
                    "ResourceLocation",
                    "Quantity",
                ],
            },
            granularity: "Daily",
        },
        timeframe: "MonthToDate",
        type: "ActualCost",
    },
    deliveryInfo: {
        destination: {
            container: "exports",
            resourceId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Storage/storageAccounts/ccmeastusdiag182",
            rootFolderPath: "ad-hoc",
        },
    },
    exportName: "TestExport",
    format: "Csv",
    schedule: {
        recurrence: "Weekly",
        recurrencePeriod: {
            from: "2020-06-01T00:00:00Z",
            to: "2020-10-31T00:00:00Z",
        },
        status: "Active",
    },
    scope: "subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

export = azure_native.costmanagement.Export("export",
    definition=azure_native.costmanagement.ExportDefinitionResponseArgs(
        data_set={
            "configuration": azure_native.costmanagement.ExportDatasetConfigurationArgs(
                columns=[
                    "Date",
                    "MeterId",
                    "ResourceId",
                    "ResourceLocation",
                    "Quantity",
                ],
            ),
            "granularity": "Daily",
        },
        timeframe="MonthToDate",
        type="ActualCost",
    ),
    delivery_info=azure_native.costmanagement.ExportDeliveryInfoResponseArgs(
        destination=azure_native.costmanagement.ExportDeliveryDestinationArgs(
            container="exports",
            resource_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Storage/storageAccounts/ccmeastusdiag182",
            root_folder_path="ad-hoc",
        ),
    ),
    export_name="TestExport",
    format="Csv",
    schedule=azure_native.costmanagement.ExportScheduleResponseArgs(
        recurrence="Weekly",
        recurrence_period=azure_native.costmanagement.ExportRecurrencePeriodArgs(
            from_="2020-06-01T00:00:00Z",
            to="2020-10-31T00:00:00Z",
        ),
        status="Active",
    ),
    scope="subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG")

```

```yaml
resources:
  export:
    type: azure-native:costmanagement:Export
    properties:
      definition:
        dataSet:
          configuration:
            columns:
              - Date
              - MeterId
              - ResourceId
              - ResourceLocation
              - Quantity
          granularity: Daily
        timeframe: MonthToDate
        type: ActualCost
      deliveryInfo:
        destination:
          container: exports
          resourceId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Storage/storageAccounts/ccmeastusdiag182
          rootFolderPath: ad-hoc
      exportName: TestExport
      format: Csv
      schedule:
        recurrence: Weekly
        recurrencePeriod:
          from: 2020-06-01T00:00:00Z
          to: 2020-10-31T00:00:00Z
        status: Active
      scope: subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG

```

{{% /example %}}
{{% example %}}
### ExportCreateOrUpdateBySubscription
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var export = new AzureNative.CostManagement.Export("export", new()
    {
        Definition = new AzureNative.CostManagement.Inputs.ExportDefinitionArgs
        {
            DataSet = new AzureNative.CostManagement.Inputs.ExportDatasetArgs
            {
                Configuration = new AzureNative.CostManagement.Inputs.ExportDatasetConfigurationArgs
                {
                    Columns = new[]
                    {
                        "Date",
                        "MeterId",
                        "ResourceId",
                        "ResourceLocation",
                        "Quantity",
                    },
                },
                Granularity = "Daily",
            },
            Timeframe = "MonthToDate",
            Type = "ActualCost",
        },
        DeliveryInfo = new AzureNative.CostManagement.Inputs.ExportDeliveryInfoArgs
        {
            Destination = new AzureNative.CostManagement.Inputs.ExportDeliveryDestinationArgs
            {
                Container = "exports",
                ResourceId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Storage/storageAccounts/ccmeastusdiag182",
                RootFolderPath = "ad-hoc",
            },
        },
        ExportName = "TestExport",
        Format = "Csv",
        Schedule = new AzureNative.CostManagement.Inputs.ExportScheduleArgs
        {
            Recurrence = "Weekly",
            RecurrencePeriod = new AzureNative.CostManagement.Inputs.ExportRecurrencePeriodArgs
            {
                From = "2020-06-01T00:00:00Z",
                To = "2020-10-31T00:00:00Z",
            },
            Status = "Active",
        },
        Scope = "subscriptions/00000000-0000-0000-0000-000000000000",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.costmanagement.Export;
import com.pulumi.azurenative.costmanagement.ExportArgs;
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
        var export = new Export("export", ExportArgs.builder()        
            .definition(Map.ofEntries(
                Map.entry("dataSet", Map.ofEntries(
                    Map.entry("configuration", Map.of("columns",                     
                        "Date",
                        "MeterId",
                        "ResourceId",
                        "ResourceLocation",
                        "Quantity")),
                    Map.entry("granularity", "Daily")
                )),
                Map.entry("timeframe", "MonthToDate"),
                Map.entry("type", "ActualCost")
            ))
            .deliveryInfo(Map.of("destination", Map.ofEntries(
                Map.entry("container", "exports"),
                Map.entry("resourceId", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Storage/storageAccounts/ccmeastusdiag182"),
                Map.entry("rootFolderPath", "ad-hoc")
            )))
            .exportName("TestExport")
            .format("Csv")
            .schedule(Map.ofEntries(
                Map.entry("recurrence", "Weekly"),
                Map.entry("recurrencePeriod", Map.ofEntries(
                    Map.entry("from", "2020-06-01T00:00:00Z"),
                    Map.entry("to", "2020-10-31T00:00:00Z")
                )),
                Map.entry("status", "Active")
            ))
            .scope("subscriptions/00000000-0000-0000-0000-000000000000")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const _export = new azure_native.costmanagement.Export("export", {
    definition: {
        dataSet: {
            configuration: {
                columns: [
                    "Date",
                    "MeterId",
                    "ResourceId",
                    "ResourceLocation",
                    "Quantity",
                ],
            },
            granularity: "Daily",
        },
        timeframe: "MonthToDate",
        type: "ActualCost",
    },
    deliveryInfo: {
        destination: {
            container: "exports",
            resourceId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Storage/storageAccounts/ccmeastusdiag182",
            rootFolderPath: "ad-hoc",
        },
    },
    exportName: "TestExport",
    format: "Csv",
    schedule: {
        recurrence: "Weekly",
        recurrencePeriod: {
            from: "2020-06-01T00:00:00Z",
            to: "2020-10-31T00:00:00Z",
        },
        status: "Active",
    },
    scope: "subscriptions/00000000-0000-0000-0000-000000000000",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

export = azure_native.costmanagement.Export("export",
    definition=azure_native.costmanagement.ExportDefinitionResponseArgs(
        data_set={
            "configuration": azure_native.costmanagement.ExportDatasetConfigurationArgs(
                columns=[
                    "Date",
                    "MeterId",
                    "ResourceId",
                    "ResourceLocation",
                    "Quantity",
                ],
            ),
            "granularity": "Daily",
        },
        timeframe="MonthToDate",
        type="ActualCost",
    ),
    delivery_info=azure_native.costmanagement.ExportDeliveryInfoResponseArgs(
        destination=azure_native.costmanagement.ExportDeliveryDestinationArgs(
            container="exports",
            resource_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Storage/storageAccounts/ccmeastusdiag182",
            root_folder_path="ad-hoc",
        ),
    ),
    export_name="TestExport",
    format="Csv",
    schedule=azure_native.costmanagement.ExportScheduleResponseArgs(
        recurrence="Weekly",
        recurrence_period=azure_native.costmanagement.ExportRecurrencePeriodArgs(
            from_="2020-06-01T00:00:00Z",
            to="2020-10-31T00:00:00Z",
        ),
        status="Active",
    ),
    scope="subscriptions/00000000-0000-0000-0000-000000000000")

```

```yaml
resources:
  export:
    type: azure-native:costmanagement:Export
    properties:
      definition:
        dataSet:
          configuration:
            columns:
              - Date
              - MeterId
              - ResourceId
              - ResourceLocation
              - Quantity
          granularity: Daily
        timeframe: MonthToDate
        type: ActualCost
      deliveryInfo:
        destination:
          container: exports
          resourceId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Storage/storageAccounts/ccmeastusdiag182
          rootFolderPath: ad-hoc
      exportName: TestExport
      format: Csv
      schedule:
        recurrence: Weekly
        recurrencePeriod:
          from: 2020-06-01T00:00:00Z
          to: 2020-10-31T00:00:00Z
        status: Active
      scope: subscriptions/00000000-0000-0000-0000-000000000000

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:costmanagement:Export TestExport subscriptions/00000000-0000-0000-0000-000000000000/providers/Microsoft.CostManagement/exports/TestExport 
```
