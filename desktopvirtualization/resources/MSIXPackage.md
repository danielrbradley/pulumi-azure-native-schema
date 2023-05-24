Schema for MSIX Package properties.
API Version: 2022-09-09.
Previous API Version: 2021-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### MSIXPackage_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var msixPackage = new AzureNative.DesktopVirtualization.MSIXPackage("msixPackage", new()
    {
        DisplayName = "displayname",
        HostPoolName = "hostpool1",
        ImagePath = "imagepath",
        IsActive = false,
        IsRegularRegistration = false,
        LastUpdated = "2008-09-22T14:01:54.9571247Z",
        MsixPackageFullName = "msixpackagefullname",
        PackageApplications = new[]
        {
            new AzureNative.DesktopVirtualization.Inputs.MsixPackageApplicationsArgs
            {
                AppId = "ApplicationId",
                AppUserModelID = "AppUserModelId",
                Description = "application-desc",
                FriendlyName = "friendlyname",
                IconImageName = "Apptile",
                RawIcon = "VGhpcyBpcyBhIHN0cmluZyB0byBoYXNo",
                RawPng = "VGhpcyBpcyBhIHN0cmluZyB0byBoYXNo",
            },
        },
        PackageDependencies = new[]
        {
            new AzureNative.DesktopVirtualization.Inputs.MsixPackageDependenciesArgs
            {
                DependencyName = "MsixTest_Dependency_Name",
                MinVersion = "version",
                Publisher = "PublishedName",
            },
        },
        PackageFamilyName = "MsixPackage_FamilyName",
        PackageName = "MsixPackage_name",
        PackageRelativePath = "packagerelativepath",
        ResourceGroupName = "resourceGroup1",
        Version = "version",
    });

});


```

```go
package main

import (
	desktopvirtualization "github.com/pulumi/pulumi-azure-native-sdk/desktopvirtualization"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := desktopvirtualization.NewMSIXPackage(ctx, "msixPackage", &desktopvirtualization.MSIXPackageArgs{
			DisplayName:           pulumi.String("displayname"),
			HostPoolName:          pulumi.String("hostpool1"),
			ImagePath:             pulumi.String("imagepath"),
			IsActive:              pulumi.Bool(false),
			IsRegularRegistration: pulumi.Bool(false),
			LastUpdated:           pulumi.String("2008-09-22T14:01:54.9571247Z"),
			MsixPackageFullName:   pulumi.String("msixpackagefullname"),
			PackageApplications: []desktopvirtualization.MsixPackageApplicationsArgs{
				{
					AppId:          pulumi.String("ApplicationId"),
					AppUserModelID: pulumi.String("AppUserModelId"),
					Description:    pulumi.String("application-desc"),
					FriendlyName:   pulumi.String("friendlyname"),
					IconImageName:  pulumi.String("Apptile"),
					RawIcon:        pulumi.String("VGhpcyBpcyBhIHN0cmluZyB0byBoYXNo"),
					RawPng:         pulumi.String("VGhpcyBpcyBhIHN0cmluZyB0byBoYXNo"),
				},
			},
			PackageDependencies: []desktopvirtualization.MsixPackageDependenciesArgs{
				{
					DependencyName: pulumi.String("MsixTest_Dependency_Name"),
					MinVersion:     pulumi.String("version"),
					Publisher:      pulumi.String("PublishedName"),
				},
			},
			PackageFamilyName:   pulumi.String("MsixPackage_FamilyName"),
			PackageName:         pulumi.String("MsixPackage_name"),
			PackageRelativePath: pulumi.String("packagerelativepath"),
			ResourceGroupName:   pulumi.String("resourceGroup1"),
			Version:             pulumi.String("version"),
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
import com.pulumi.azurenative.desktopvirtualization.MSIXPackage;
import com.pulumi.azurenative.desktopvirtualization.MSIXPackageArgs;
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
        var msixPackage = new MSIXPackage("msixPackage", MSIXPackageArgs.builder()        
            .displayName("displayname")
            .hostPoolName("hostpool1")
            .imagePath("imagepath")
            .isActive(false)
            .isRegularRegistration(false)
            .lastUpdated("2008-09-22T14:01:54.9571247Z")
            .msixPackageFullName("msixpackagefullname")
            .packageApplications(Map.ofEntries(
                Map.entry("appId", "ApplicationId"),
                Map.entry("appUserModelID", "AppUserModelId"),
                Map.entry("description", "application-desc"),
                Map.entry("friendlyName", "friendlyname"),
                Map.entry("iconImageName", "Apptile"),
                Map.entry("rawIcon", "VGhpcyBpcyBhIHN0cmluZyB0byBoYXNo"),
                Map.entry("rawPng", "VGhpcyBpcyBhIHN0cmluZyB0byBoYXNo")
            ))
            .packageDependencies(Map.ofEntries(
                Map.entry("dependencyName", "MsixTest_Dependency_Name"),
                Map.entry("minVersion", "version"),
                Map.entry("publisher", "PublishedName")
            ))
            .packageFamilyName("MsixPackage_FamilyName")
            .packageName("MsixPackage_name")
            .packageRelativePath("packagerelativepath")
            .resourceGroupName("resourceGroup1")
            .version("version")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const msixPackage = new azure_native.desktopvirtualization.MSIXPackage("msixPackage", {
    displayName: "displayname",
    hostPoolName: "hostpool1",
    imagePath: "imagepath",
    isActive: false,
    isRegularRegistration: false,
    lastUpdated: "2008-09-22T14:01:54.9571247Z",
    msixPackageFullName: "msixpackagefullname",
    packageApplications: [{
        appId: "ApplicationId",
        appUserModelID: "AppUserModelId",
        description: "application-desc",
        friendlyName: "friendlyname",
        iconImageName: "Apptile",
        rawIcon: "VGhpcyBpcyBhIHN0cmluZyB0byBoYXNo",
        rawPng: "VGhpcyBpcyBhIHN0cmluZyB0byBoYXNo",
    }],
    packageDependencies: [{
        dependencyName: "MsixTest_Dependency_Name",
        minVersion: "version",
        publisher: "PublishedName",
    }],
    packageFamilyName: "MsixPackage_FamilyName",
    packageName: "MsixPackage_name",
    packageRelativePath: "packagerelativepath",
    resourceGroupName: "resourceGroup1",
    version: "version",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

msix_package = azure_native.desktopvirtualization.MSIXPackage("msixPackage",
    display_name="displayname",
    host_pool_name="hostpool1",
    image_path="imagepath",
    is_active=False,
    is_regular_registration=False,
    last_updated="2008-09-22T14:01:54.9571247Z",
    msix_package_full_name="msixpackagefullname",
    package_applications=[azure_native.desktopvirtualization.MsixPackageApplicationsArgs(
        app_id="ApplicationId",
        app_user_model_id="AppUserModelId",
        description="application-desc",
        friendly_name="friendlyname",
        icon_image_name="Apptile",
        raw_icon="VGhpcyBpcyBhIHN0cmluZyB0byBoYXNo",
        raw_png="VGhpcyBpcyBhIHN0cmluZyB0byBoYXNo",
    )],
    package_dependencies=[azure_native.desktopvirtualization.MsixPackageDependenciesArgs(
        dependency_name="MsixTest_Dependency_Name",
        min_version="version",
        publisher="PublishedName",
    )],
    package_family_name="MsixPackage_FamilyName",
    package_name="MsixPackage_name",
    package_relative_path="packagerelativepath",
    resource_group_name="resourceGroup1",
    version="version")

```

```yaml
resources:
  msixPackage:
    type: azure-native:desktopvirtualization:MSIXPackage
    properties:
      displayName: displayname
      hostPoolName: hostpool1
      imagePath: imagepath
      isActive: false
      isRegularRegistration: false
      lastUpdated: 2008-09-22T14:01:54.9571247Z
      msixPackageFullName: msixpackagefullname
      packageApplications:
        - appId: ApplicationId
          appUserModelID: AppUserModelId
          description: application-desc
          friendlyName: friendlyname
          iconImageName: Apptile
          rawIcon: VGhpcyBpcyBhIHN0cmluZyB0byBoYXNo
          rawPng: VGhpcyBpcyBhIHN0cmluZyB0byBoYXNo
      packageDependencies:
        - dependencyName: MsixTest_Dependency_Name
          minVersion: version
          publisher: PublishedName
      packageFamilyName: MsixPackage_FamilyName
      packageName: MsixPackage_name
      packageRelativePath: packagerelativepath
      resourceGroupName: resourceGroup1
      version: version

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:desktopvirtualization:MSIXPackage hostpool1/MsixPackageFullName /subscriptions/daefabc0-95b4-48b3-b645-8a753a63c4fa/resourcegroups/resourcegroup1/providers/Microsoft.DesktopVirtualization/hostpools/hostpool1/msixpackages/msixPackageFullName 
```
