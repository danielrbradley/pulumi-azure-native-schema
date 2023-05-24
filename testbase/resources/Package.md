The Test Base Package resource.
API Version: 2022-04-01-preview.
Previous API Version: 2022-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PackageCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var package = new AzureNative.TestBase.Package("package", new()
    {
        ApplicationName = "contoso-package2",
        BlobPath = "storageAccountPath/package.zip",
        FlightingRing = "Insider Beta Channel",
        Location = "westus",
        PackageName = "contoso-package2",
        ResourceGroupName = "contoso-rg1",
        Tags = null,
        TargetOSList = new[]
        {
            new AzureNative.TestBase.Inputs.TargetOSInfoArgs
            {
                OsUpdateType = "Security updates",
                TargetOSs = new[]
                {
                    "Windows 10 2004",
                    "Windows 10 1903",
                },
            },
        },
        TestBaseAccountName = "contoso-testBaseAccount1",
        Tests = new[]
        {
            new AzureNative.TestBase.Inputs.TestArgs
            {
                Commands = new[]
                {
                    new AzureNative.TestBase.Inputs.CommandArgs
                    {
                        Action = "Install",
                        AlwaysRun = true,
                        ApplyUpdateBefore = false,
                        Content = "app/scripts/install/job.ps1",
                        ContentType = "Path",
                        MaxRunTime = 1800,
                        Name = "Install",
                        RestartAfter = true,
                        RunAsInteractive = true,
                        RunElevated = true,
                    },
                    new AzureNative.TestBase.Inputs.CommandArgs
                    {
                        Action = "Launch",
                        AlwaysRun = false,
                        ApplyUpdateBefore = true,
                        Content = "app/scripts/launch/job.ps1",
                        ContentType = "Path",
                        MaxRunTime = 1800,
                        Name = "Launch",
                        RestartAfter = false,
                        RunAsInteractive = true,
                        RunElevated = true,
                    },
                    new AzureNative.TestBase.Inputs.CommandArgs
                    {
                        Action = "Close",
                        AlwaysRun = false,
                        ApplyUpdateBefore = false,
                        Content = "app/scripts/close/job.ps1",
                        ContentType = "Path",
                        MaxRunTime = 1800,
                        Name = "Close",
                        RestartAfter = false,
                        RunAsInteractive = true,
                        RunElevated = true,
                    },
                    new AzureNative.TestBase.Inputs.CommandArgs
                    {
                        Action = "Uninstall",
                        AlwaysRun = true,
                        ApplyUpdateBefore = false,
                        Content = "app/scripts/uninstall/job.ps1",
                        ContentType = "Path",
                        MaxRunTime = 1800,
                        Name = "Uninstall",
                        RestartAfter = false,
                        RunAsInteractive = true,
                        RunElevated = true,
                    },
                },
                IsActive = true,
                TestType = "OutOfBoxTest",
            },
        },
        Version = "1.0.0",
    });

});


```

```go
package main

import (
	testbase "github.com/pulumi/pulumi-azure-native-sdk/testbase"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := testbase.NewPackage(ctx, "package", &testbase.PackageArgs{
			ApplicationName:   pulumi.String("contoso-package2"),
			BlobPath:          pulumi.String("storageAccountPath/package.zip"),
			FlightingRing:     pulumi.String("Insider Beta Channel"),
			Location:          pulumi.String("westus"),
			PackageName:       pulumi.String("contoso-package2"),
			ResourceGroupName: pulumi.String("contoso-rg1"),
			Tags:              nil,
			TargetOSList: []testbase.TargetOSInfoArgs{
				{
					OsUpdateType: pulumi.String("Security updates"),
					TargetOSs: pulumi.StringArray{
						pulumi.String("Windows 10 2004"),
						pulumi.String("Windows 10 1903"),
					},
				},
			},
			TestBaseAccountName: pulumi.String("contoso-testBaseAccount1"),
			Tests: []testbase.TestArgs{
				{
					Commands: testbase.CommandArray{
						{
							Action:            pulumi.String("Install"),
							AlwaysRun:         pulumi.Bool(true),
							ApplyUpdateBefore: pulumi.Bool(false),
							Content:           pulumi.String("app/scripts/install/job.ps1"),
							ContentType:       pulumi.String("Path"),
							MaxRunTime:        pulumi.Int(1800),
							Name:              pulumi.String("Install"),
							RestartAfter:      pulumi.Bool(true),
							RunAsInteractive:  pulumi.Bool(true),
							RunElevated:       pulumi.Bool(true),
						},
						{
							Action:            pulumi.String("Launch"),
							AlwaysRun:         pulumi.Bool(false),
							ApplyUpdateBefore: pulumi.Bool(true),
							Content:           pulumi.String("app/scripts/launch/job.ps1"),
							ContentType:       pulumi.String("Path"),
							MaxRunTime:        pulumi.Int(1800),
							Name:              pulumi.String("Launch"),
							RestartAfter:      pulumi.Bool(false),
							RunAsInteractive:  pulumi.Bool(true),
							RunElevated:       pulumi.Bool(true),
						},
						{
							Action:            pulumi.String("Close"),
							AlwaysRun:         pulumi.Bool(false),
							ApplyUpdateBefore: pulumi.Bool(false),
							Content:           pulumi.String("app/scripts/close/job.ps1"),
							ContentType:       pulumi.String("Path"),
							MaxRunTime:        pulumi.Int(1800),
							Name:              pulumi.String("Close"),
							RestartAfter:      pulumi.Bool(false),
							RunAsInteractive:  pulumi.Bool(true),
							RunElevated:       pulumi.Bool(true),
						},
						{
							Action:            pulumi.String("Uninstall"),
							AlwaysRun:         pulumi.Bool(true),
							ApplyUpdateBefore: pulumi.Bool(false),
							Content:           pulumi.String("app/scripts/uninstall/job.ps1"),
							ContentType:       pulumi.String("Path"),
							MaxRunTime:        pulumi.Int(1800),
							Name:              pulumi.String("Uninstall"),
							RestartAfter:      pulumi.Bool(false),
							RunAsInteractive:  pulumi.Bool(true),
							RunElevated:       pulumi.Bool(true),
						},
					},
					IsActive: pulumi.Bool(true),
					TestType: pulumi.String("OutOfBoxTest"),
				},
			},
			Version: pulumi.String("1.0.0"),
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
import com.pulumi.azurenative.testbase.Package;
import com.pulumi.azurenative.testbase.PackageArgs;
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
        var package_ = new Package("package", PackageArgs.builder()        
            .applicationName("contoso-package2")
            .blobPath("storageAccountPath/package.zip")
            .flightingRing("Insider Beta Channel")
            .location("westus")
            .packageName("contoso-package2")
            .resourceGroupName("contoso-rg1")
            .tags()
            .targetOSList(Map.ofEntries(
                Map.entry("osUpdateType", "Security updates"),
                Map.entry("targetOSs",                 
                    "Windows 10 2004",
                    "Windows 10 1903")
            ))
            .testBaseAccountName("contoso-testBaseAccount1")
            .tests(Map.ofEntries(
                Map.entry("commands",                 
                    Map.ofEntries(
                        Map.entry("action", "Install"),
                        Map.entry("alwaysRun", true),
                        Map.entry("applyUpdateBefore", false),
                        Map.entry("content", "app/scripts/install/job.ps1"),
                        Map.entry("contentType", "Path"),
                        Map.entry("maxRunTime", 1800),
                        Map.entry("name", "Install"),
                        Map.entry("restartAfter", true),
                        Map.entry("runAsInteractive", true),
                        Map.entry("runElevated", true)
                    ),
                    Map.ofEntries(
                        Map.entry("action", "Launch"),
                        Map.entry("alwaysRun", false),
                        Map.entry("applyUpdateBefore", true),
                        Map.entry("content", "app/scripts/launch/job.ps1"),
                        Map.entry("contentType", "Path"),
                        Map.entry("maxRunTime", 1800),
                        Map.entry("name", "Launch"),
                        Map.entry("restartAfter", false),
                        Map.entry("runAsInteractive", true),
                        Map.entry("runElevated", true)
                    ),
                    Map.ofEntries(
                        Map.entry("action", "Close"),
                        Map.entry("alwaysRun", false),
                        Map.entry("applyUpdateBefore", false),
                        Map.entry("content", "app/scripts/close/job.ps1"),
                        Map.entry("contentType", "Path"),
                        Map.entry("maxRunTime", 1800),
                        Map.entry("name", "Close"),
                        Map.entry("restartAfter", false),
                        Map.entry("runAsInteractive", true),
                        Map.entry("runElevated", true)
                    ),
                    Map.ofEntries(
                        Map.entry("action", "Uninstall"),
                        Map.entry("alwaysRun", true),
                        Map.entry("applyUpdateBefore", false),
                        Map.entry("content", "app/scripts/uninstall/job.ps1"),
                        Map.entry("contentType", "Path"),
                        Map.entry("maxRunTime", 1800),
                        Map.entry("name", "Uninstall"),
                        Map.entry("restartAfter", false),
                        Map.entry("runAsInteractive", true),
                        Map.entry("runElevated", true)
                    )),
                Map.entry("isActive", true),
                Map.entry("testType", "OutOfBoxTest")
            ))
            .version("1.0.0")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const _package = new azure_native.testbase.Package("package", {
    applicationName: "contoso-package2",
    blobPath: "storageAccountPath/package.zip",
    flightingRing: "Insider Beta Channel",
    location: "westus",
    packageName: "contoso-package2",
    resourceGroupName: "contoso-rg1",
    tags: {},
    targetOSList: [{
        osUpdateType: "Security updates",
        targetOSs: [
            "Windows 10 2004",
            "Windows 10 1903",
        ],
    }],
    testBaseAccountName: "contoso-testBaseAccount1",
    tests: [{
        commands: [
            {
                action: "Install",
                alwaysRun: true,
                applyUpdateBefore: false,
                content: "app/scripts/install/job.ps1",
                contentType: "Path",
                maxRunTime: 1800,
                name: "Install",
                restartAfter: true,
                runAsInteractive: true,
                runElevated: true,
            },
            {
                action: "Launch",
                alwaysRun: false,
                applyUpdateBefore: true,
                content: "app/scripts/launch/job.ps1",
                contentType: "Path",
                maxRunTime: 1800,
                name: "Launch",
                restartAfter: false,
                runAsInteractive: true,
                runElevated: true,
            },
            {
                action: "Close",
                alwaysRun: false,
                applyUpdateBefore: false,
                content: "app/scripts/close/job.ps1",
                contentType: "Path",
                maxRunTime: 1800,
                name: "Close",
                restartAfter: false,
                runAsInteractive: true,
                runElevated: true,
            },
            {
                action: "Uninstall",
                alwaysRun: true,
                applyUpdateBefore: false,
                content: "app/scripts/uninstall/job.ps1",
                contentType: "Path",
                maxRunTime: 1800,
                name: "Uninstall",
                restartAfter: false,
                runAsInteractive: true,
                runElevated: true,
            },
        ],
        isActive: true,
        testType: "OutOfBoxTest",
    }],
    version: "1.0.0",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

package = azure_native.testbase.Package("package",
    application_name="contoso-package2",
    blob_path="storageAccountPath/package.zip",
    flighting_ring="Insider Beta Channel",
    location="westus",
    package_name="contoso-package2",
    resource_group_name="contoso-rg1",
    tags={},
    target_os_list=[azure_native.testbase.TargetOSInfoArgs(
        os_update_type="Security updates",
        target_oss=[
            "Windows 10 2004",
            "Windows 10 1903",
        ],
    )],
    test_base_account_name="contoso-testBaseAccount1",
    tests=[{
        "commands": [
            azure_native.testbase.CommandArgs(
                action="Install",
                always_run=True,
                apply_update_before=False,
                content="app/scripts/install/job.ps1",
                content_type="Path",
                max_run_time=1800,
                name="Install",
                restart_after=True,
                run_as_interactive=True,
                run_elevated=True,
            ),
            azure_native.testbase.CommandArgs(
                action="Launch",
                always_run=False,
                apply_update_before=True,
                content="app/scripts/launch/job.ps1",
                content_type="Path",
                max_run_time=1800,
                name="Launch",
                restart_after=False,
                run_as_interactive=True,
                run_elevated=True,
            ),
            azure_native.testbase.CommandArgs(
                action="Close",
                always_run=False,
                apply_update_before=False,
                content="app/scripts/close/job.ps1",
                content_type="Path",
                max_run_time=1800,
                name="Close",
                restart_after=False,
                run_as_interactive=True,
                run_elevated=True,
            ),
            azure_native.testbase.CommandArgs(
                action="Uninstall",
                always_run=True,
                apply_update_before=False,
                content="app/scripts/uninstall/job.ps1",
                content_type="Path",
                max_run_time=1800,
                name="Uninstall",
                restart_after=False,
                run_as_interactive=True,
                run_elevated=True,
            ),
        ],
        "isActive": True,
        "testType": "OutOfBoxTest",
    }],
    version="1.0.0")

```

```yaml
resources:
  package:
    type: azure-native:testbase:Package
    properties:
      applicationName: contoso-package2
      blobPath: storageAccountPath/package.zip
      flightingRing: Insider Beta Channel
      location: westus
      packageName: contoso-package2
      resourceGroupName: contoso-rg1
      tags: {}
      targetOSList:
        - osUpdateType: Security updates
          targetOSs:
            - Windows 10 2004
            - Windows 10 1903
      testBaseAccountName: contoso-testBaseAccount1
      tests:
        - commands:
            - action: Install
              alwaysRun: true
              applyUpdateBefore: false
              content: app/scripts/install/job.ps1
              contentType: Path
              maxRunTime: 1800
              name: Install
              restartAfter: true
              runAsInteractive: true
              runElevated: true
            - action: Launch
              alwaysRun: false
              applyUpdateBefore: true
              content: app/scripts/launch/job.ps1
              contentType: Path
              maxRunTime: 1800
              name: Launch
              restartAfter: false
              runAsInteractive: true
              runElevated: true
            - action: Close
              alwaysRun: false
              applyUpdateBefore: false
              content: app/scripts/close/job.ps1
              contentType: Path
              maxRunTime: 1800
              name: Close
              restartAfter: false
              runAsInteractive: true
              runElevated: true
            - action: Uninstall
              alwaysRun: true
              applyUpdateBefore: false
              content: app/scripts/uninstall/job.ps1
              contentType: Path
              maxRunTime: 1800
              name: Uninstall
              restartAfter: false
              runAsInteractive: true
              runElevated: true
          isActive: true
          testType: OutOfBoxTest
      version: 1.0.0

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:testbase:Package contoso-package2 /subscriptions/subscription-id/resourceGroups/contoso-rg1/providers/Microsoft.TestBase/testBaseAccounts/contoso-testBaseAccount1/packages/contoso-package2 
```
