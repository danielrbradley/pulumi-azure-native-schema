
API Version: 2020-01-01.
Previous API Version: 2020-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Update an application control machine group by adding a new application
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var adaptiveApplicationControl = new AzureNative.Security.AdaptiveApplicationControl("adaptiveApplicationControl", new()
    {
        AscLocation = "centralus",
        EnforcementMode = "Audit",
        GroupName = "ERELGROUP1",
        PathRecommendations = new[]
        {
            new AzureNative.Security.Inputs.PathRecommendationArgs
            {
                Action = "Recommended",
                Common = true,
                ConfigurationStatus = "Configured",
                FileType = "Exe",
                Path = "[Exe] O=MICROSOFT CORPORATION, L=REDMOND, S=WASHINGTON, C=US\\*\\*\\0.0.0.0",
                PublisherInfo = new AzureNative.Security.Inputs.PublisherInfoArgs
                {
                    BinaryName = "*",
                    ProductName = "*",
                    PublisherName = "O=MICROSOFT CORPORATION, L=REDMOND, S=WASHINGTON, C=US",
                    Version = "0.0.0.0",
                },
                Type = "PublisherSignature",
                UserSids = new[]
                {
                    "S-1-1-0",
                },
                Usernames = new[]
                {
                    new AzureNative.Security.Inputs.UserRecommendationArgs
                    {
                        RecommendationAction = "Recommended",
                        Username = "Everyone",
                    },
                },
            },
            new AzureNative.Security.Inputs.PathRecommendationArgs
            {
                Action = "Recommended",
                Common = true,
                ConfigurationStatus = "Configured",
                FileType = "Exe",
                Path = "%OSDRIVE%\\WINDOWSAZURE\\SECAGENT\\WASECAGENTPROV.EXE",
                PublisherInfo = new AzureNative.Security.Inputs.PublisherInfoArgs
                {
                    BinaryName = "*",
                    ProductName = "MICROSOFT® COREXT",
                    PublisherName = "CN=MICROSOFT AZURE DEPENDENCY CODE SIGN",
                    Version = "0.0.0.0",
                },
                Type = "ProductSignature",
                UserSids = new[]
                {
                    "S-1-1-0",
                },
                Usernames = new[]
                {
                    new AzureNative.Security.Inputs.UserRecommendationArgs
                    {
                        RecommendationAction = "Recommended",
                        Username = "NT AUTHORITY\\SYSTEM",
                    },
                },
            },
            new AzureNative.Security.Inputs.PathRecommendationArgs
            {
                Action = "Recommended",
                Common = true,
                ConfigurationStatus = "Configured",
                FileType = "Exe",
                Path = "%OSDRIVE%\\WINDOWSAZURE\\PACKAGES_201973_7415\\COLLECTGUESTLOGS.EXE",
                PublisherInfo = new AzureNative.Security.Inputs.PublisherInfoArgs
                {
                    BinaryName = "*",
                    ProductName = "*",
                    PublisherName = "CN=MICROSOFT AZURE DEPENDENCY CODE SIGN",
                    Version = "0.0.0.0",
                },
                Type = "PublisherSignature",
                UserSids = new[]
                {
                    "S-1-1-0",
                },
                Usernames = new[]
                {
                    new AzureNative.Security.Inputs.UserRecommendationArgs
                    {
                        RecommendationAction = "Recommended",
                        Username = "NT AUTHORITY\\SYSTEM",
                    },
                },
            },
            new AzureNative.Security.Inputs.PathRecommendationArgs
            {
                Action = "Add",
                Common = true,
                Path = "C:\\directory\\file.exe",
                Type = "File",
            },
        },
        ProtectionMode = new AzureNative.Security.Inputs.ProtectionModeArgs
        {
            Exe = "Audit",
            Msi = "None",
            Script = "None",
        },
        VmRecommendations = new[]
        {
            new AzureNative.Security.Inputs.VmRecommendationArgs
            {
                ConfigurationStatus = "Configured",
                EnforcementSupport = "Supported",
                RecommendationAction = "Recommended",
                ResourceId = "/subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourcegroups/erelh-stable/providers/microsoft.compute/virtualmachines/erelh-16090",
            },
            new AzureNative.Security.Inputs.VmRecommendationArgs
            {
                ConfigurationStatus = "Configured",
                EnforcementSupport = "Supported",
                RecommendationAction = "Recommended",
                ResourceId = "/subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourcegroups/matanvs/providers/microsoft.compute/virtualmachines/matanvs19",
            },
        },
    });

});


```

```go
package main

import (
	security "github.com/pulumi/pulumi-azure-native-sdk/security"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := security.NewAdaptiveApplicationControl(ctx, "adaptiveApplicationControl", &security.AdaptiveApplicationControlArgs{
			AscLocation:     pulumi.String("centralus"),
			EnforcementMode: pulumi.String("Audit"),
			GroupName:       pulumi.String("ERELGROUP1"),
			PathRecommendations: []security.PathRecommendationArgs{
				{
					Action:              pulumi.String("Recommended"),
					Common:              pulumi.Bool(true),
					ConfigurationStatus: pulumi.String("Configured"),
					FileType:            pulumi.String("Exe"),
					Path:                pulumi.String("[Exe] O=MICROSOFT CORPORATION, L=REDMOND, S=WASHINGTON, C=US\\*\\*\\0.0.0.0"),
					PublisherInfo: {
						BinaryName:    pulumi.String("*"),
						ProductName:   pulumi.String("*"),
						PublisherName: pulumi.String("O=MICROSOFT CORPORATION, L=REDMOND, S=WASHINGTON, C=US"),
						Version:       pulumi.String("0.0.0.0"),
					},
					Type: pulumi.String("PublisherSignature"),
					UserSids: pulumi.StringArray{
						pulumi.String("S-1-1-0"),
					},
					Usernames: security.UserRecommendationArray{
						{
							RecommendationAction: pulumi.String("Recommended"),
							Username:             pulumi.String("Everyone"),
						},
					},
				},
				{
					Action:              pulumi.String("Recommended"),
					Common:              pulumi.Bool(true),
					ConfigurationStatus: pulumi.String("Configured"),
					FileType:            pulumi.String("Exe"),
					Path:                pulumi.String("%OSDRIVE%\\WINDOWSAZURE\\SECAGENT\\WASECAGENTPROV.EXE"),
					PublisherInfo: {
						BinaryName:    pulumi.String("*"),
						ProductName:   pulumi.String("MICROSOFT® COREXT"),
						PublisherName: pulumi.String("CN=MICROSOFT AZURE DEPENDENCY CODE SIGN"),
						Version:       pulumi.String("0.0.0.0"),
					},
					Type: pulumi.String("ProductSignature"),
					UserSids: pulumi.StringArray{
						pulumi.String("S-1-1-0"),
					},
					Usernames: security.UserRecommendationArray{
						{
							RecommendationAction: pulumi.String("Recommended"),
							Username:             pulumi.String("NT AUTHORITY\\SYSTEM"),
						},
					},
				},
				{
					Action:              pulumi.String("Recommended"),
					Common:              pulumi.Bool(true),
					ConfigurationStatus: pulumi.String("Configured"),
					FileType:            pulumi.String("Exe"),
					Path:                pulumi.String("%OSDRIVE%\\WINDOWSAZURE\\PACKAGES_201973_7415\\COLLECTGUESTLOGS.EXE"),
					PublisherInfo: {
						BinaryName:    pulumi.String("*"),
						ProductName:   pulumi.String("*"),
						PublisherName: pulumi.String("CN=MICROSOFT AZURE DEPENDENCY CODE SIGN"),
						Version:       pulumi.String("0.0.0.0"),
					},
					Type: pulumi.String("PublisherSignature"),
					UserSids: pulumi.StringArray{
						pulumi.String("S-1-1-0"),
					},
					Usernames: security.UserRecommendationArray{
						{
							RecommendationAction: pulumi.String("Recommended"),
							Username:             pulumi.String("NT AUTHORITY\\SYSTEM"),
						},
					},
				},
				{
					Action: pulumi.String("Add"),
					Common: pulumi.Bool(true),
					Path:   pulumi.String("C:\\directory\\file.exe"),
					Type:   pulumi.String("File"),
				},
			},
			ProtectionMode: &security.ProtectionModeArgs{
				Exe:    pulumi.String("Audit"),
				Msi:    pulumi.String("None"),
				Script: pulumi.String("None"),
			},
			VmRecommendations: []security.VmRecommendationArgs{
				{
					ConfigurationStatus:  pulumi.String("Configured"),
					EnforcementSupport:   pulumi.String("Supported"),
					RecommendationAction: pulumi.String("Recommended"),
					ResourceId:           pulumi.String("/subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourcegroups/erelh-stable/providers/microsoft.compute/virtualmachines/erelh-16090"),
				},
				{
					ConfigurationStatus:  pulumi.String("Configured"),
					EnforcementSupport:   pulumi.String("Supported"),
					RecommendationAction: pulumi.String("Recommended"),
					ResourceId:           pulumi.String("/subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourcegroups/matanvs/providers/microsoft.compute/virtualmachines/matanvs19"),
				},
			},
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
import com.pulumi.azurenative.security.AdaptiveApplicationControl;
import com.pulumi.azurenative.security.AdaptiveApplicationControlArgs;
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
        var adaptiveApplicationControl = new AdaptiveApplicationControl("adaptiveApplicationControl", AdaptiveApplicationControlArgs.builder()        
            .ascLocation("centralus")
            .enforcementMode("Audit")
            .groupName("ERELGROUP1")
            .pathRecommendations(            
                Map.ofEntries(
                    Map.entry("action", "Recommended"),
                    Map.entry("common", true),
                    Map.entry("configurationStatus", "Configured"),
                    Map.entry("fileType", "Exe"),
                    Map.entry("path", "[Exe] O=MICROSOFT CORPORATION, L=REDMOND, S=WASHINGTON, C=US\\*\\*\\0.0.0.0"),
                    Map.entry("publisherInfo", Map.ofEntries(
                        Map.entry("binaryName", "*"),
                        Map.entry("productName", "*"),
                        Map.entry("publisherName", "O=MICROSOFT CORPORATION, L=REDMOND, S=WASHINGTON, C=US"),
                        Map.entry("version", "0.0.0.0")
                    )),
                    Map.entry("type", "PublisherSignature"),
                    Map.entry("userSids", "S-1-1-0"),
                    Map.entry("usernames", Map.ofEntries(
                        Map.entry("recommendationAction", "Recommended"),
                        Map.entry("username", "Everyone")
                    ))
                ),
                Map.ofEntries(
                    Map.entry("action", "Recommended"),
                    Map.entry("common", true),
                    Map.entry("configurationStatus", "Configured"),
                    Map.entry("fileType", "Exe"),
                    Map.entry("path", "%OSDRIVE%\\WINDOWSAZURE\\SECAGENT\\WASECAGENTPROV.EXE"),
                    Map.entry("publisherInfo", Map.ofEntries(
                        Map.entry("binaryName", "*"),
                        Map.entry("productName", "MICROSOFT® COREXT"),
                        Map.entry("publisherName", "CN=MICROSOFT AZURE DEPENDENCY CODE SIGN"),
                        Map.entry("version", "0.0.0.0")
                    )),
                    Map.entry("type", "ProductSignature"),
                    Map.entry("userSids", "S-1-1-0"),
                    Map.entry("usernames", Map.ofEntries(
                        Map.entry("recommendationAction", "Recommended"),
                        Map.entry("username", "NT AUTHORITY\\SYSTEM")
                    ))
                ),
                Map.ofEntries(
                    Map.entry("action", "Recommended"),
                    Map.entry("common", true),
                    Map.entry("configurationStatus", "Configured"),
                    Map.entry("fileType", "Exe"),
                    Map.entry("path", "%OSDRIVE%\\WINDOWSAZURE\\PACKAGES_201973_7415\\COLLECTGUESTLOGS.EXE"),
                    Map.entry("publisherInfo", Map.ofEntries(
                        Map.entry("binaryName", "*"),
                        Map.entry("productName", "*"),
                        Map.entry("publisherName", "CN=MICROSOFT AZURE DEPENDENCY CODE SIGN"),
                        Map.entry("version", "0.0.0.0")
                    )),
                    Map.entry("type", "PublisherSignature"),
                    Map.entry("userSids", "S-1-1-0"),
                    Map.entry("usernames", Map.ofEntries(
                        Map.entry("recommendationAction", "Recommended"),
                        Map.entry("username", "NT AUTHORITY\\SYSTEM")
                    ))
                ),
                Map.ofEntries(
                    Map.entry("action", "Add"),
                    Map.entry("common", true),
                    Map.entry("path", "C:\\directory\\file.exe"),
                    Map.entry("type", "File")
                ))
            .protectionMode(Map.ofEntries(
                Map.entry("exe", "Audit"),
                Map.entry("msi", "None"),
                Map.entry("script", "None")
            ))
            .vmRecommendations(            
                Map.ofEntries(
                    Map.entry("configurationStatus", "Configured"),
                    Map.entry("enforcementSupport", "Supported"),
                    Map.entry("recommendationAction", "Recommended"),
                    Map.entry("resourceId", "/subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourcegroups/erelh-stable/providers/microsoft.compute/virtualmachines/erelh-16090")
                ),
                Map.ofEntries(
                    Map.entry("configurationStatus", "Configured"),
                    Map.entry("enforcementSupport", "Supported"),
                    Map.entry("recommendationAction", "Recommended"),
                    Map.entry("resourceId", "/subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourcegroups/matanvs/providers/microsoft.compute/virtualmachines/matanvs19")
                ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const adaptiveApplicationControl = new azure_native.security.AdaptiveApplicationControl("adaptiveApplicationControl", {
    ascLocation: "centralus",
    enforcementMode: "Audit",
    groupName: "ERELGROUP1",
    pathRecommendations: [
        {
            action: "Recommended",
            common: true,
            configurationStatus: "Configured",
            fileType: "Exe",
            path: "[Exe] O=MICROSOFT CORPORATION, L=REDMOND, S=WASHINGTON, C=US\\*\\*\\0.0.0.0",
            publisherInfo: {
                binaryName: "*",
                productName: "*",
                publisherName: "O=MICROSOFT CORPORATION, L=REDMOND, S=WASHINGTON, C=US",
                version: "0.0.0.0",
            },
            type: "PublisherSignature",
            userSids: ["S-1-1-0"],
            usernames: [{
                recommendationAction: "Recommended",
                username: "Everyone",
            }],
        },
        {
            action: "Recommended",
            common: true,
            configurationStatus: "Configured",
            fileType: "Exe",
            path: "%OSDRIVE%\\WINDOWSAZURE\\SECAGENT\\WASECAGENTPROV.EXE",
            publisherInfo: {
                binaryName: "*",
                productName: "MICROSOFT® COREXT",
                publisherName: "CN=MICROSOFT AZURE DEPENDENCY CODE SIGN",
                version: "0.0.0.0",
            },
            type: "ProductSignature",
            userSids: ["S-1-1-0"],
            usernames: [{
                recommendationAction: "Recommended",
                username: "NT AUTHORITY\\SYSTEM",
            }],
        },
        {
            action: "Recommended",
            common: true,
            configurationStatus: "Configured",
            fileType: "Exe",
            path: "%OSDRIVE%\\WINDOWSAZURE\\PACKAGES_201973_7415\\COLLECTGUESTLOGS.EXE",
            publisherInfo: {
                binaryName: "*",
                productName: "*",
                publisherName: "CN=MICROSOFT AZURE DEPENDENCY CODE SIGN",
                version: "0.0.0.0",
            },
            type: "PublisherSignature",
            userSids: ["S-1-1-0"],
            usernames: [{
                recommendationAction: "Recommended",
                username: "NT AUTHORITY\\SYSTEM",
            }],
        },
        {
            action: "Add",
            common: true,
            path: "C:\\directory\\file.exe",
            type: "File",
        },
    ],
    protectionMode: {
        exe: "Audit",
        msi: "None",
        script: "None",
    },
    vmRecommendations: [
        {
            configurationStatus: "Configured",
            enforcementSupport: "Supported",
            recommendationAction: "Recommended",
            resourceId: "/subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourcegroups/erelh-stable/providers/microsoft.compute/virtualmachines/erelh-16090",
        },
        {
            configurationStatus: "Configured",
            enforcementSupport: "Supported",
            recommendationAction: "Recommended",
            resourceId: "/subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourcegroups/matanvs/providers/microsoft.compute/virtualmachines/matanvs19",
        },
    ],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

adaptive_application_control = azure_native.security.AdaptiveApplicationControl("adaptiveApplicationControl",
    asc_location="centralus",
    enforcement_mode="Audit",
    group_name="ERELGROUP1",
    path_recommendations=[
        {
            "action": "Recommended",
            "common": True,
            "configurationStatus": "Configured",
            "fileType": "Exe",
            "path": "[Exe] O=MICROSOFT CORPORATION, L=REDMOND, S=WASHINGTON, C=US\\*\\*\\0.0.0.0",
            "publisherInfo": azure_native.security.PublisherInfoArgs(
                binary_name="*",
                product_name="*",
                publisher_name="O=MICROSOFT CORPORATION, L=REDMOND, S=WASHINGTON, C=US",
                version="0.0.0.0",
            ),
            "type": "PublisherSignature",
            "userSids": ["S-1-1-0"],
            "usernames": [azure_native.security.UserRecommendationArgs(
                recommendation_action="Recommended",
                username="Everyone",
            )],
        },
        {
            "action": "Recommended",
            "common": True,
            "configurationStatus": "Configured",
            "fileType": "Exe",
            "path": "%OSDRIVE%\\WINDOWSAZURE\\SECAGENT\\WASECAGENTPROV.EXE",
            "publisherInfo": azure_native.security.PublisherInfoArgs(
                binary_name="*",
                product_name="MICROSOFT® COREXT",
                publisher_name="CN=MICROSOFT AZURE DEPENDENCY CODE SIGN",
                version="0.0.0.0",
            ),
            "type": "ProductSignature",
            "userSids": ["S-1-1-0"],
            "usernames": [azure_native.security.UserRecommendationArgs(
                recommendation_action="Recommended",
                username="NT AUTHORITY\\SYSTEM",
            )],
        },
        {
            "action": "Recommended",
            "common": True,
            "configurationStatus": "Configured",
            "fileType": "Exe",
            "path": "%OSDRIVE%\\WINDOWSAZURE\\PACKAGES_201973_7415\\COLLECTGUESTLOGS.EXE",
            "publisherInfo": azure_native.security.PublisherInfoArgs(
                binary_name="*",
                product_name="*",
                publisher_name="CN=MICROSOFT AZURE DEPENDENCY CODE SIGN",
                version="0.0.0.0",
            ),
            "type": "PublisherSignature",
            "userSids": ["S-1-1-0"],
            "usernames": [azure_native.security.UserRecommendationArgs(
                recommendation_action="Recommended",
                username="NT AUTHORITY\\SYSTEM",
            )],
        },
        azure_native.security.PathRecommendationArgs(
            action="Add",
            common=True,
            path="C:\\directory\\file.exe",
            type="File",
        ),
    ],
    protection_mode=azure_native.security.ProtectionModeArgs(
        exe="Audit",
        msi="None",
        script="None",
    ),
    vm_recommendations=[
        azure_native.security.VmRecommendationArgs(
            configuration_status="Configured",
            enforcement_support="Supported",
            recommendation_action="Recommended",
            resource_id="/subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourcegroups/erelh-stable/providers/microsoft.compute/virtualmachines/erelh-16090",
        ),
        azure_native.security.VmRecommendationArgs(
            configuration_status="Configured",
            enforcement_support="Supported",
            recommendation_action="Recommended",
            resource_id="/subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourcegroups/matanvs/providers/microsoft.compute/virtualmachines/matanvs19",
        ),
    ])

```

```yaml
resources:
  adaptiveApplicationControl:
    type: azure-native:security:AdaptiveApplicationControl
    properties:
      ascLocation: centralus
      enforcementMode: Audit
      groupName: ERELGROUP1
      pathRecommendations:
        - action: Recommended
          common: true
          configurationStatus: Configured
          fileType: Exe
          path: '[Exe] O=MICROSOFT CORPORATION, L=REDMOND, S=WASHINGTON, C=US\*\*\0.0.0.0'
          publisherInfo:
            binaryName: '*'
            productName: '*'
            publisherName: O=MICROSOFT CORPORATION, L=REDMOND, S=WASHINGTON, C=US
            version: 0.0.0.0
          type: PublisherSignature
          userSids:
            - S-1-1-0
          usernames:
            - recommendationAction: Recommended
              username: Everyone
        - action: Recommended
          common: true
          configurationStatus: Configured
          fileType: Exe
          path: '%OSDRIVE%\WINDOWSAZURE\SECAGENT\WASECAGENTPROV.EXE'
          publisherInfo:
            binaryName: '*'
            productName: MICROSOFT® COREXT
            publisherName: CN=MICROSOFT AZURE DEPENDENCY CODE SIGN
            version: 0.0.0.0
          type: ProductSignature
          userSids:
            - S-1-1-0
          usernames:
            - recommendationAction: Recommended
              username: NT AUTHORITY\SYSTEM
        - action: Recommended
          common: true
          configurationStatus: Configured
          fileType: Exe
          path: '%OSDRIVE%\WINDOWSAZURE\PACKAGES_201973_7415\COLLECTGUESTLOGS.EXE'
          publisherInfo:
            binaryName: '*'
            productName: '*'
            publisherName: CN=MICROSOFT AZURE DEPENDENCY CODE SIGN
            version: 0.0.0.0
          type: PublisherSignature
          userSids:
            - S-1-1-0
          usernames:
            - recommendationAction: Recommended
              username: NT AUTHORITY\SYSTEM
        - action: Add
          common: true
          path: C:\directory\file.exe
          type: File
      protectionMode:
        exe: Audit
        msi: None
        script: None
      vmRecommendations:
        - configurationStatus: Configured
          enforcementSupport: Supported
          recommendationAction: Recommended
          resourceId: /subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourcegroups/erelh-stable/providers/microsoft.compute/virtualmachines/erelh-16090
        - configurationStatus: Configured
          enforcementSupport: Supported
          recommendationAction: Recommended
          resourceId: /subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourcegroups/matanvs/providers/microsoft.compute/virtualmachines/matanvs19

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:security:AdaptiveApplicationControl ERELGROUP1 /subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/providers/Microsoft.Security/locations/centralus/applicationWhitelistings/ERELGROUP1 
```
