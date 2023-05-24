Maintenance configuration record type
API Version: 2022-11-01-preview.
Previous API Version: 2020-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### MaintenanceConfigurations_CreateOrUpdateForResource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var maintenanceConfiguration = new AzureNative.Maintenance.MaintenanceConfiguration("maintenanceConfiguration", new()
    {
        Duration = "05:00",
        ExpirationDateTime = "9999-12-31 00:00",
        Location = "westus2",
        MaintenanceScope = "OSImage",
        Namespace = "Microsoft.Maintenance",
        RecurEvery = "Day",
        ResourceGroupName = "examplerg",
        ResourceName = "configuration1",
        StartDateTime = "2020-04-30 08:00",
        TimeZone = "Pacific Standard Time",
        Visibility = "Custom",
    });

});


```

```go
package main

import (
	maintenance "github.com/pulumi/pulumi-azure-native-sdk/maintenance"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := maintenance.NewMaintenanceConfiguration(ctx, "maintenanceConfiguration", &maintenance.MaintenanceConfigurationArgs{
			Duration:           pulumi.String("05:00"),
			ExpirationDateTime: pulumi.String("9999-12-31 00:00"),
			Location:           pulumi.String("westus2"),
			MaintenanceScope:   pulumi.String("OSImage"),
			Namespace:          pulumi.String("Microsoft.Maintenance"),
			RecurEvery:         pulumi.String("Day"),
			ResourceGroupName:  pulumi.String("examplerg"),
			ResourceName:       pulumi.String("configuration1"),
			StartDateTime:      pulumi.String("2020-04-30 08:00"),
			TimeZone:           pulumi.String("Pacific Standard Time"),
			Visibility:         pulumi.String("Custom"),
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
import com.pulumi.azurenative.maintenance.MaintenanceConfiguration;
import com.pulumi.azurenative.maintenance.MaintenanceConfigurationArgs;
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
        var maintenanceConfiguration = new MaintenanceConfiguration("maintenanceConfiguration", MaintenanceConfigurationArgs.builder()        
            .duration("05:00")
            .expirationDateTime("9999-12-31 00:00")
            .location("westus2")
            .maintenanceScope("OSImage")
            .namespace("Microsoft.Maintenance")
            .recurEvery("Day")
            .resourceGroupName("examplerg")
            .resourceName("configuration1")
            .startDateTime("2020-04-30 08:00")
            .timeZone("Pacific Standard Time")
            .visibility("Custom")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const maintenanceConfiguration = new azure_native.maintenance.MaintenanceConfiguration("maintenanceConfiguration", {
    duration: "05:00",
    expirationDateTime: "9999-12-31 00:00",
    location: "westus2",
    maintenanceScope: "OSImage",
    namespace: "Microsoft.Maintenance",
    recurEvery: "Day",
    resourceGroupName: "examplerg",
    resourceName: "configuration1",
    startDateTime: "2020-04-30 08:00",
    timeZone: "Pacific Standard Time",
    visibility: "Custom",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

maintenance_configuration = azure_native.maintenance.MaintenanceConfiguration("maintenanceConfiguration",
    duration="05:00",
    expiration_date_time="9999-12-31 00:00",
    location="westus2",
    maintenance_scope="OSImage",
    namespace="Microsoft.Maintenance",
    recur_every="Day",
    resource_group_name="examplerg",
    resource_name_="configuration1",
    start_date_time="2020-04-30 08:00",
    time_zone="Pacific Standard Time",
    visibility="Custom")

```

```yaml
resources:
  maintenanceConfiguration:
    type: azure-native:maintenance:MaintenanceConfiguration
    properties:
      duration: 05:00
      expirationDateTime: 9999-12-31 00:00
      location: westus2
      maintenanceScope: OSImage
      namespace: Microsoft.Maintenance
      recurEvery: Day
      resourceGroupName: examplerg
      resourceName: configuration1
      startDateTime: 2020-04-30 08:00
      timeZone: Pacific Standard Time
      visibility: Custom

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:maintenance:MaintenanceConfiguration configuration1 /subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.Maintenance/maintenanceConfigurations/configuration1 
```
