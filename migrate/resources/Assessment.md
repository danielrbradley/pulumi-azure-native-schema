An assessment created for a group in the Migration project.
API Version: 2019-10-01.
Previous API Version: 2019-10-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Assessments_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var assessment = new AzureNative.Migrate.Assessment("assessment", new()
    {
        AssessmentName = "assessment_5_14_2019_16_48_47",
        ETag = "\"1e000c2c-0000-0d00-0000-5cdaa4190000\"",
        GroupName = "Group2",
        ProjectName = "abgoyalWEselfhostb72bproject",
        Properties = new AzureNative.Migrate.Inputs.AssessmentPropertiesArgs
        {
            AzureDiskType = "StandardOrPremium",
            AzureHybridUseBenefit = "Yes",
            AzureLocation = "NorthEurope",
            AzureOfferCode = "MSAZR0003P",
            AzurePricingTier = "Standard",
            AzureStorageRedundancy = "LocallyRedundant",
            AzureVmFamilies = new[]
            {
                "Dv2_series",
                "F_series",
                "Dv3_series",
                "DS_series",
                "DSv2_series",
                "Fs_series",
                "Dsv3_series",
                "Ev3_series",
                "Esv3_series",
                "D_series",
                "M_series",
                "Fsv2_series",
                "H_series",
            },
            Currency = "USD",
            DiscountPercentage = 100,
            Percentile = "Percentile95",
            ReservedInstance = "RI3Year",
            ScalingFactor = 1,
            SizingCriterion = "PerformanceBased",
            Stage = "InProgress",
            TimeRange = "Day",
            VmUptime = new AzureNative.Migrate.Inputs.VmUptimeArgs
            {
                DaysPerMonth = 31,
                HoursPerDay = 24,
            },
        },
        ResourceGroupName = "abgoyal-westEurope",
    });

});


```

```go
package main

import (
	migrate "github.com/pulumi/pulumi-azure-native-sdk/migrate"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := migrate.NewAssessment(ctx, "assessment", &migrate.AssessmentArgs{
			AssessmentName: pulumi.String("assessment_5_14_2019_16_48_47"),
			ETag:           pulumi.String("\"1e000c2c-0000-0d00-0000-5cdaa4190000\""),
			GroupName:      pulumi.String("Group2"),
			ProjectName:    pulumi.String("abgoyalWEselfhostb72bproject"),
			Properties: migrate.AssessmentPropertiesResponse{
				AzureDiskType:          pulumi.String("StandardOrPremium"),
				AzureHybridUseBenefit:  pulumi.String("Yes"),
				AzureLocation:          pulumi.String("NorthEurope"),
				AzureOfferCode:         pulumi.String("MSAZR0003P"),
				AzurePricingTier:       pulumi.String("Standard"),
				AzureStorageRedundancy: pulumi.String("LocallyRedundant"),
				AzureVmFamilies: pulumi.StringArray{
					pulumi.String("Dv2_series"),
					pulumi.String("F_series"),
					pulumi.String("Dv3_series"),
					pulumi.String("DS_series"),
					pulumi.String("DSv2_series"),
					pulumi.String("Fs_series"),
					pulumi.String("Dsv3_series"),
					pulumi.String("Ev3_series"),
					pulumi.String("Esv3_series"),
					pulumi.String("D_series"),
					pulumi.String("M_series"),
					pulumi.String("Fsv2_series"),
					pulumi.String("H_series"),
				},
				Currency:           pulumi.String("USD"),
				DiscountPercentage: pulumi.Float64(100),
				Percentile:         pulumi.String("Percentile95"),
				ReservedInstance:   pulumi.String("RI3Year"),
				ScalingFactor:      pulumi.Float64(1),
				SizingCriterion:    pulumi.String("PerformanceBased"),
				Stage:              pulumi.String("InProgress"),
				TimeRange:          pulumi.String("Day"),
				VmUptime: &migrate.VmUptimeArgs{
					DaysPerMonth: pulumi.Float64(31),
					HoursPerDay:  pulumi.Float64(24),
				},
			},
			ResourceGroupName: pulumi.String("abgoyal-westEurope"),
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
import com.pulumi.azurenative.migrate.Assessment;
import com.pulumi.azurenative.migrate.AssessmentArgs;
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
        var assessment = new Assessment("assessment", AssessmentArgs.builder()        
            .assessmentName("assessment_5_14_2019_16_48_47")
            .eTag("\"1e000c2c-0000-0d00-0000-5cdaa4190000\"")
            .groupName("Group2")
            .projectName("abgoyalWEselfhostb72bproject")
            .properties(Map.ofEntries(
                Map.entry("azureDiskType", "StandardOrPremium"),
                Map.entry("azureHybridUseBenefit", "Yes"),
                Map.entry("azureLocation", "NorthEurope"),
                Map.entry("azureOfferCode", "MSAZR0003P"),
                Map.entry("azurePricingTier", "Standard"),
                Map.entry("azureStorageRedundancy", "LocallyRedundant"),
                Map.entry("azureVmFamilies",                 
                    "Dv2_series",
                    "F_series",
                    "Dv3_series",
                    "DS_series",
                    "DSv2_series",
                    "Fs_series",
                    "Dsv3_series",
                    "Ev3_series",
                    "Esv3_series",
                    "D_series",
                    "M_series",
                    "Fsv2_series",
                    "H_series"),
                Map.entry("currency", "USD"),
                Map.entry("discountPercentage", 100),
                Map.entry("percentile", "Percentile95"),
                Map.entry("reservedInstance", "RI3Year"),
                Map.entry("scalingFactor", 1),
                Map.entry("sizingCriterion", "PerformanceBased"),
                Map.entry("stage", "InProgress"),
                Map.entry("timeRange", "Day"),
                Map.entry("vmUptime", Map.ofEntries(
                    Map.entry("daysPerMonth", 31),
                    Map.entry("hoursPerDay", 24)
                ))
            ))
            .resourceGroupName("abgoyal-westEurope")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const assessment = new azure_native.migrate.Assessment("assessment", {
    assessmentName: "assessment_5_14_2019_16_48_47",
    eTag: "\"1e000c2c-0000-0d00-0000-5cdaa4190000\"",
    groupName: "Group2",
    projectName: "abgoyalWEselfhostb72bproject",
    properties: {
        azureDiskType: "StandardOrPremium",
        azureHybridUseBenefit: "Yes",
        azureLocation: "NorthEurope",
        azureOfferCode: "MSAZR0003P",
        azurePricingTier: "Standard",
        azureStorageRedundancy: "LocallyRedundant",
        azureVmFamilies: [
            "Dv2_series",
            "F_series",
            "Dv3_series",
            "DS_series",
            "DSv2_series",
            "Fs_series",
            "Dsv3_series",
            "Ev3_series",
            "Esv3_series",
            "D_series",
            "M_series",
            "Fsv2_series",
            "H_series",
        ],
        currency: "USD",
        discountPercentage: 100,
        percentile: "Percentile95",
        reservedInstance: "RI3Year",
        scalingFactor: 1,
        sizingCriterion: "PerformanceBased",
        stage: "InProgress",
        timeRange: "Day",
        vmUptime: {
            daysPerMonth: 31,
            hoursPerDay: 24,
        },
    },
    resourceGroupName: "abgoyal-westEurope",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

assessment = azure_native.migrate.Assessment("assessment",
    assessment_name="assessment_5_14_2019_16_48_47",
    e_tag="\"1e000c2c-0000-0d00-0000-5cdaa4190000\"",
    group_name="Group2",
    project_name="abgoyalWEselfhostb72bproject",
    properties=azure_native.migrate.AssessmentPropertiesResponseArgs(
        azure_disk_type="StandardOrPremium",
        azure_hybrid_use_benefit="Yes",
        azure_location="NorthEurope",
        azure_offer_code="MSAZR0003P",
        azure_pricing_tier="Standard",
        azure_storage_redundancy="LocallyRedundant",
        azure_vm_families=[
            "Dv2_series",
            "F_series",
            "Dv3_series",
            "DS_series",
            "DSv2_series",
            "Fs_series",
            "Dsv3_series",
            "Ev3_series",
            "Esv3_series",
            "D_series",
            "M_series",
            "Fsv2_series",
            "H_series",
        ],
        currency="USD",
        discount_percentage=100,
        percentile="Percentile95",
        reserved_instance="RI3Year",
        scaling_factor=1,
        sizing_criterion="PerformanceBased",
        stage="InProgress",
        time_range="Day",
        vm_uptime=azure_native.migrate.VmUptimeArgs(
            days_per_month=31,
            hours_per_day=24,
        ),
    ),
    resource_group_name="abgoyal-westEurope")

```

```yaml
resources:
  assessment:
    type: azure-native:migrate:Assessment
    properties:
      assessmentName: assessment_5_14_2019_16_48_47
      eTag: '"1e000c2c-0000-0d00-0000-5cdaa4190000"'
      groupName: Group2
      projectName: abgoyalWEselfhostb72bproject
      properties:
        azureDiskType: StandardOrPremium
        azureHybridUseBenefit: Yes
        azureLocation: NorthEurope
        azureOfferCode: MSAZR0003P
        azurePricingTier: Standard
        azureStorageRedundancy: LocallyRedundant
        azureVmFamilies:
          - Dv2_series
          - F_series
          - Dv3_series
          - DS_series
          - DSv2_series
          - Fs_series
          - Dsv3_series
          - Ev3_series
          - Esv3_series
          - D_series
          - M_series
          - Fsv2_series
          - H_series
        currency: USD
        discountPercentage: 100
        percentile: Percentile95
        reservedInstance: RI3Year
        scalingFactor: 1
        sizingCriterion: PerformanceBased
        stage: InProgress
        timeRange: Day
        vmUptime:
          daysPerMonth: 31
          hoursPerDay: 24
      resourceGroupName: abgoyal-westEurope

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:migrate:Assessment assessment_5_14_2019_16_48_47 /subscriptions/6393a73f-8d55-47ef-b6dd-179b3e0c7910/resourceGroups/abgoyal-westeurope/providers/Microsoft.Migrate/assessmentprojects/abgoyalWEselfhostb72bproject/groups/Group2/assessments/assessment_5_14_2019_16_48_47 
```
