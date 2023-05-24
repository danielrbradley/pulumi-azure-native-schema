Update details
API Version: 2023-02-01.

{{% examples %}}
## Example Usage
{{% example %}}
### Put a specific update
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var update = new AzureNative.AzureStackHCI.Update("update", new()
    {
        AdditionalProperties = "additional properties",
        AvailabilityType = "Local",
        ClusterName = "testcluster",
        Description = "AzS Update 4.2203.2.32",
        DisplayName = "AzS Update - 4.2203.2.32",
        InstalledDate = "2022-04-06T14:08:18.254Z",
        NotifyMessage = "Brief message with instructions for updates of AvailabilityType Notify",
        PackagePath = "\\\\SU1FileServer\\SU1_Infrastructure_2\\Updates\\Packages\\Microsoft4.2203.2.32",
        PackageSizeInMb = 18858,
        PackageType = "Infrastructure",
        Prerequisites = new[]
        {
            new AzureNative.AzureStackHCI.Inputs.UpdatePrerequisiteArgs
            {
                PackageName = "update package name",
                UpdateType = "update type",
                Version = "prerequisite version",
            },
        },
        ProgressPercentage = 0,
        Publisher = "Microsoft",
        ReleaseLink = "https://docs.microsoft.com/azure-stack/operator/release-notes?view=azs-2203",
        ResourceGroupName = "testrg",
        State = "Installed",
        UpdateName = "Microsoft4.2203.2.32",
        Version = "4.2203.2.32",
    });

});


```

```go
package main

import (
	azurestackhci "github.com/pulumi/pulumi-azure-native-sdk/azurestackhci"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := azurestackhci.NewUpdate(ctx, "update", &azurestackhci.UpdateArgs{
			AdditionalProperties: pulumi.String("additional properties"),
			AvailabilityType:     pulumi.String("Local"),
			ClusterName:          pulumi.String("testcluster"),
			Description:          pulumi.String("AzS Update 4.2203.2.32"),
			DisplayName:          pulumi.String("AzS Update - 4.2203.2.32"),
			InstalledDate:        pulumi.String("2022-04-06T14:08:18.254Z"),
			NotifyMessage:        pulumi.String("Brief message with instructions for updates of AvailabilityType Notify"),
			PackagePath:          pulumi.String("\\\\SU1FileServer\\SU1_Infrastructure_2\\Updates\\Packages\\Microsoft4.2203.2.32"),
			PackageSizeInMb:      pulumi.Float64(18858),
			PackageType:          pulumi.String("Infrastructure"),
			Prerequisites: []azurestackhci.UpdatePrerequisiteArgs{
				{
					PackageName: pulumi.String("update package name"),
					UpdateType:  pulumi.String("update type"),
					Version:     pulumi.String("prerequisite version"),
				},
			},
			ProgressPercentage: pulumi.Float64(0),
			Publisher:          pulumi.String("Microsoft"),
			ReleaseLink:        pulumi.String("https://docs.microsoft.com/azure-stack/operator/release-notes?view=azs-2203"),
			ResourceGroupName:  pulumi.String("testrg"),
			State:              pulumi.String("Installed"),
			UpdateName:         pulumi.String("Microsoft4.2203.2.32"),
			Version:            pulumi.String("4.2203.2.32"),
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
import com.pulumi.azurenative.azurestackhci.Update;
import com.pulumi.azurenative.azurestackhci.UpdateArgs;
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
        var update = new Update("update", UpdateArgs.builder()        
            .additionalProperties("additional properties")
            .availabilityType("Local")
            .clusterName("testcluster")
            .description("AzS Update 4.2203.2.32")
            .displayName("AzS Update - 4.2203.2.32")
            .installedDate("2022-04-06T14:08:18.254Z")
            .notifyMessage("Brief message with instructions for updates of AvailabilityType Notify")
            .packagePath("\\\\SU1FileServer\\SU1_Infrastructure_2\\Updates\\Packages\\Microsoft4.2203.2.32")
            .packageSizeInMb(18858)
            .packageType("Infrastructure")
            .prerequisites(Map.ofEntries(
                Map.entry("packageName", "update package name"),
                Map.entry("updateType", "update type"),
                Map.entry("version", "prerequisite version")
            ))
            .progressPercentage(0)
            .publisher("Microsoft")
            .releaseLink("https://docs.microsoft.com/azure-stack/operator/release-notes?view=azs-2203")
            .resourceGroupName("testrg")
            .state("Installed")
            .updateName("Microsoft4.2203.2.32")
            .version("4.2203.2.32")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const update = new azure_native.azurestackhci.Update("update", {
    additionalProperties: "additional properties",
    availabilityType: "Local",
    clusterName: "testcluster",
    description: "AzS Update 4.2203.2.32",
    displayName: "AzS Update - 4.2203.2.32",
    installedDate: "2022-04-06T14:08:18.254Z",
    notifyMessage: "Brief message with instructions for updates of AvailabilityType Notify",
    packagePath: "\\\\SU1FileServer\\SU1_Infrastructure_2\\Updates\\Packages\\Microsoft4.2203.2.32",
    packageSizeInMb: 18858,
    packageType: "Infrastructure",
    prerequisites: [{
        packageName: "update package name",
        updateType: "update type",
        version: "prerequisite version",
    }],
    progressPercentage: 0,
    publisher: "Microsoft",
    releaseLink: "https://docs.microsoft.com/azure-stack/operator/release-notes?view=azs-2203",
    resourceGroupName: "testrg",
    state: "Installed",
    updateName: "Microsoft4.2203.2.32",
    version: "4.2203.2.32",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

update = azure_native.azurestackhci.Update("update",
    additional_properties="additional properties",
    availability_type="Local",
    cluster_name="testcluster",
    description="AzS Update 4.2203.2.32",
    display_name="AzS Update - 4.2203.2.32",
    installed_date="2022-04-06T14:08:18.254Z",
    notify_message="Brief message with instructions for updates of AvailabilityType Notify",
    package_path="\\\\SU1FileServer\\SU1_Infrastructure_2\\Updates\\Packages\\Microsoft4.2203.2.32",
    package_size_in_mb=18858,
    package_type="Infrastructure",
    prerequisites=[azure_native.azurestackhci.UpdatePrerequisiteArgs(
        package_name="update package name",
        update_type="update type",
        version="prerequisite version",
    )],
    progress_percentage=0,
    publisher="Microsoft",
    release_link="https://docs.microsoft.com/azure-stack/operator/release-notes?view=azs-2203",
    resource_group_name="testrg",
    state="Installed",
    update_name="Microsoft4.2203.2.32",
    version="4.2203.2.32")

```

```yaml
resources:
  update:
    type: azure-native:azurestackhci:Update
    properties:
      additionalProperties: additional properties
      availabilityType: Local
      clusterName: testcluster
      description: AzS Update 4.2203.2.32
      displayName: AzS Update - 4.2203.2.32
      installedDate: 2022-04-06T14:08:18.254Z
      notifyMessage: Brief message with instructions for updates of AvailabilityType Notify
      packagePath: \\SU1FileServer\SU1_Infrastructure_2\Updates\Packages\Microsoft4.2203.2.32
      packageSizeInMb: 18858
      packageType: Infrastructure
      prerequisites:
        - packageName: update package name
          updateType: update type
          version: prerequisite version
      progressPercentage: 0
      publisher: Microsoft
      releaseLink: https://docs.microsoft.com/azure-stack/operator/release-notes?view=azs-2203
      resourceGroupName: testrg
      state: Installed
      updateName: Microsoft4.2203.2.32
      version: 4.2203.2.32

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:azurestackhci:Update Microsoft4.2203.2.32 /subscriptions/b8d594e5-51f3-4c11-9c54-a7771b81c712/resourceGroups/testrg/providers/Microsoft.AzureStackHCI/clusters/testcluster/updates/Microsoft4.2203.2.32 
```
