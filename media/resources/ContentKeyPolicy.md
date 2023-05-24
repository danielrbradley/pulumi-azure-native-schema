A Content Key Policy resource.
API Version: 2022-08-01.
Previous API Version: 2020-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates a Content Key Policy with ClearKey option and Token Restriction
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var contentKeyPolicy = new AzureNative.Media.ContentKeyPolicy("contentKeyPolicy", new()
    {
        AccountName = "contosomedia",
        ContentKeyPolicyName = "PolicyWithClearKeyOptionAndSwtTokenRestriction",
        Description = "ArmPolicyDescription",
        Options = new[]
        {
            new AzureNative.Media.Inputs.ContentKeyPolicyOptionArgs
            {
                Configuration = new AzureNative.Media.Inputs.ContentKeyPolicyClearKeyConfigurationArgs
                {
                    OdataType = "#Microsoft.Media.ContentKeyPolicyClearKeyConfiguration",
                },
                Name = "ClearKeyOption",
                Restriction = new AzureNative.Media.Inputs.ContentKeyPolicyTokenRestrictionArgs
                {
                    Audience = "urn:audience",
                    Issuer = "urn:issuer",
                    OdataType = "#Microsoft.Media.ContentKeyPolicyTokenRestriction",
                    PrimaryVerificationKey = new AzureNative.Media.Inputs.ContentKeyPolicySymmetricTokenKeyArgs
                    {
                        KeyValue = "AAAAAAAAAAAAAAAAAAAAAA==",
                        OdataType = "#Microsoft.Media.ContentKeyPolicySymmetricTokenKey",
                    },
                    RestrictionTokenType = "Swt",
                },
            },
        },
        ResourceGroupName = "contosorg",
    });

});


```

```go
package main

import (
	media "github.com/pulumi/pulumi-azure-native-sdk/media"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := media.NewContentKeyPolicy(ctx, "contentKeyPolicy", &media.ContentKeyPolicyArgs{
			AccountName:          pulumi.String("contosomedia"),
			ContentKeyPolicyName: pulumi.String("PolicyWithClearKeyOptionAndSwtTokenRestriction"),
			Description:          pulumi.String("ArmPolicyDescription"),
			Options: []media.ContentKeyPolicyOptionArgs{
				{
					Configuration: {
						OdataType: "#Microsoft.Media.ContentKeyPolicyClearKeyConfiguration",
					},
					Name: pulumi.String("ClearKeyOption"),
					Restriction: {
						Audience:  "urn:audience",
						Issuer:    "urn:issuer",
						OdataType: "#Microsoft.Media.ContentKeyPolicyTokenRestriction",
						PrimaryVerificationKey: {
							KeyValue:  "AAAAAAAAAAAAAAAAAAAAAA==",
							OdataType: "#Microsoft.Media.ContentKeyPolicySymmetricTokenKey",
						},
						RestrictionTokenType: "Swt",
					},
				},
			},
			ResourceGroupName: pulumi.String("contosorg"),
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
import com.pulumi.azurenative.media.ContentKeyPolicy;
import com.pulumi.azurenative.media.ContentKeyPolicyArgs;
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
        var contentKeyPolicy = new ContentKeyPolicy("contentKeyPolicy", ContentKeyPolicyArgs.builder()        
            .accountName("contosomedia")
            .contentKeyPolicyName("PolicyWithClearKeyOptionAndSwtTokenRestriction")
            .description("ArmPolicyDescription")
            .options(Map.ofEntries(
                Map.entry("configuration", Map.of("odataType", "#Microsoft.Media.ContentKeyPolicyClearKeyConfiguration")),
                Map.entry("name", "ClearKeyOption"),
                Map.entry("restriction", Map.ofEntries(
                    Map.entry("audience", "urn:audience"),
                    Map.entry("issuer", "urn:issuer"),
                    Map.entry("odataType", "#Microsoft.Media.ContentKeyPolicyTokenRestriction"),
                    Map.entry("primaryVerificationKey", Map.ofEntries(
                        Map.entry("keyValue", "AAAAAAAAAAAAAAAAAAAAAA=="),
                        Map.entry("odataType", "#Microsoft.Media.ContentKeyPolicySymmetricTokenKey")
                    )),
                    Map.entry("restrictionTokenType", "Swt")
                ))
            ))
            .resourceGroupName("contosorg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const contentKeyPolicy = new azure_native.media.ContentKeyPolicy("contentKeyPolicy", {
    accountName: "contosomedia",
    contentKeyPolicyName: "PolicyWithClearKeyOptionAndSwtTokenRestriction",
    description: "ArmPolicyDescription",
    options: [{
        configuration: {
            odataType: "#Microsoft.Media.ContentKeyPolicyClearKeyConfiguration",
        },
        name: "ClearKeyOption",
        restriction: {
            audience: "urn:audience",
            issuer: "urn:issuer",
            odataType: "#Microsoft.Media.ContentKeyPolicyTokenRestriction",
            primaryVerificationKey: {
                keyValue: "AAAAAAAAAAAAAAAAAAAAAA==",
                odataType: "#Microsoft.Media.ContentKeyPolicySymmetricTokenKey",
            },
            restrictionTokenType: "Swt",
        },
    }],
    resourceGroupName: "contosorg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

content_key_policy = azure_native.media.ContentKeyPolicy("contentKeyPolicy",
    account_name="contosomedia",
    content_key_policy_name="PolicyWithClearKeyOptionAndSwtTokenRestriction",
    description="ArmPolicyDescription",
    options=[azure_native.media.ContentKeyPolicyOptionArgs(
        configuration=azure_native.media.ContentKeyPolicyClearKeyConfigurationArgs(
            odata_type="#Microsoft.Media.ContentKeyPolicyClearKeyConfiguration",
        ),
        name="ClearKeyOption",
        restriction=azure_native.media.ContentKeyPolicyTokenRestrictionArgs(
            audience="urn:audience",
            issuer="urn:issuer",
            odata_type="#Microsoft.Media.ContentKeyPolicyTokenRestriction",
            primary_verification_key=azure_native.media.ContentKeyPolicySymmetricTokenKeyArgs(
                key_value="AAAAAAAAAAAAAAAAAAAAAA==",
                odata_type="#Microsoft.Media.ContentKeyPolicySymmetricTokenKey",
            ),
            restriction_token_type="Swt",
        ),
    )],
    resource_group_name="contosorg")

```

```yaml
resources:
  contentKeyPolicy:
    type: azure-native:media:ContentKeyPolicy
    properties:
      accountName: contosomedia
      contentKeyPolicyName: PolicyWithClearKeyOptionAndSwtTokenRestriction
      description: ArmPolicyDescription
      options:
        - configuration:
            odataType: '#Microsoft.Media.ContentKeyPolicyClearKeyConfiguration'
          name: ClearKeyOption
          restriction:
            audience: urn:audience
            issuer: urn:issuer
            odataType: '#Microsoft.Media.ContentKeyPolicyTokenRestriction'
            primaryVerificationKey:
              keyValue: AAAAAAAAAAAAAAAAAAAAAA==
              odataType: '#Microsoft.Media.ContentKeyPolicySymmetricTokenKey'
            restrictionTokenType: Swt
      resourceGroupName: contosorg

```

{{% /example %}}
{{% example %}}
### Creates a Content Key Policy with PlayReady option and Open Restriction
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var contentKeyPolicy = new AzureNative.Media.ContentKeyPolicy("contentKeyPolicy", new()
    {
        AccountName = "contosomedia",
        ContentKeyPolicyName = "PolicyWithPlayReadyOptionAndOpenRestriction",
        Description = "ArmPolicyDescription",
        Options = new[]
        {
            new AzureNative.Media.Inputs.ContentKeyPolicyOptionArgs
            {
                Configuration = new AzureNative.Media.Inputs.ContentKeyPolicyPlayReadyConfigurationArgs
                {
                    Licenses = new[]
                    {
                        new AzureNative.Media.Inputs.ContentKeyPolicyPlayReadyLicenseArgs
                        {
                            AllowTestDevices = true,
                            BeginDate = "2017-10-16T18:22:53.46Z",
                            ContentKeyLocation = new AzureNative.Media.Inputs.ContentKeyPolicyPlayReadyContentEncryptionKeyFromHeaderArgs
                            {
                                OdataType = "#Microsoft.Media.ContentKeyPolicyPlayReadyContentEncryptionKeyFromHeader",
                            },
                            ContentType = "UltraVioletDownload",
                            LicenseType = "Persistent",
                            PlayRight = new AzureNative.Media.Inputs.ContentKeyPolicyPlayReadyPlayRightArgs
                            {
                                AllowPassingVideoContentToUnknownOutput = "NotAllowed",
                                DigitalVideoOnlyContentRestriction = false,
                                ImageConstraintForAnalogComponentVideoRestriction = true,
                                ImageConstraintForAnalogComputerMonitorRestriction = false,
                                ScmsRestriction = 2,
                            },
                            SecurityLevel = "SL150",
                        },
                    },
                    OdataType = "#Microsoft.Media.ContentKeyPolicyPlayReadyConfiguration",
                },
                Name = "ArmPolicyOptionName",
                Restriction = new AzureNative.Media.Inputs.ContentKeyPolicyOpenRestrictionArgs
                {
                    OdataType = "#Microsoft.Media.ContentKeyPolicyOpenRestriction",
                },
            },
        },
        ResourceGroupName = "contosorg",
    });

});


```

```go
package main

import (
	media "github.com/pulumi/pulumi-azure-native-sdk/media"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := media.NewContentKeyPolicy(ctx, "contentKeyPolicy", &media.ContentKeyPolicyArgs{
			AccountName:          pulumi.String("contosomedia"),
			ContentKeyPolicyName: pulumi.String("PolicyWithPlayReadyOptionAndOpenRestriction"),
			Description:          pulumi.String("ArmPolicyDescription"),
			Options: []media.ContentKeyPolicyOptionArgs{
				{
					Configuration: {
						Licenses: []media.ContentKeyPolicyPlayReadyLicense{
							{
								AllowTestDevices: true,
								BeginDate:        "2017-10-16T18:22:53.46Z",
								ContentKeyLocation: {
									OdataType: "#Microsoft.Media.ContentKeyPolicyPlayReadyContentEncryptionKeyFromHeader",
								},
								ContentType: "UltraVioletDownload",
								LicenseType: "Persistent",
								PlayRight: {
									AllowPassingVideoContentToUnknownOutput:            "NotAllowed",
									DigitalVideoOnlyContentRestriction:                 false,
									ImageConstraintForAnalogComponentVideoRestriction:  true,
									ImageConstraintForAnalogComputerMonitorRestriction: false,
									ScmsRestriction: 2,
								},
								SecurityLevel: "SL150",
							},
						},
						OdataType: "#Microsoft.Media.ContentKeyPolicyPlayReadyConfiguration",
					},
					Name: pulumi.String("ArmPolicyOptionName"),
					Restriction: {
						OdataType: "#Microsoft.Media.ContentKeyPolicyOpenRestriction",
					},
				},
			},
			ResourceGroupName: pulumi.String("contosorg"),
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
import com.pulumi.azurenative.media.ContentKeyPolicy;
import com.pulumi.azurenative.media.ContentKeyPolicyArgs;
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
        var contentKeyPolicy = new ContentKeyPolicy("contentKeyPolicy", ContentKeyPolicyArgs.builder()        
            .accountName("contosomedia")
            .contentKeyPolicyName("PolicyWithPlayReadyOptionAndOpenRestriction")
            .description("ArmPolicyDescription")
            .options(Map.ofEntries(
                Map.entry("configuration", Map.ofEntries(
                    Map.entry("licenses", Map.ofEntries(
                        Map.entry("allowTestDevices", true),
                        Map.entry("beginDate", "2017-10-16T18:22:53.46Z"),
                        Map.entry("contentKeyLocation", Map.of("odataType", "#Microsoft.Media.ContentKeyPolicyPlayReadyContentEncryptionKeyFromHeader")),
                        Map.entry("contentType", "UltraVioletDownload"),
                        Map.entry("licenseType", "Persistent"),
                        Map.entry("playRight", Map.ofEntries(
                            Map.entry("allowPassingVideoContentToUnknownOutput", "NotAllowed"),
                            Map.entry("digitalVideoOnlyContentRestriction", false),
                            Map.entry("imageConstraintForAnalogComponentVideoRestriction", true),
                            Map.entry("imageConstraintForAnalogComputerMonitorRestriction", false),
                            Map.entry("scmsRestriction", 2)
                        )),
                        Map.entry("securityLevel", "SL150")
                    )),
                    Map.entry("odataType", "#Microsoft.Media.ContentKeyPolicyPlayReadyConfiguration")
                )),
                Map.entry("name", "ArmPolicyOptionName"),
                Map.entry("restriction", Map.of("odataType", "#Microsoft.Media.ContentKeyPolicyOpenRestriction"))
            ))
            .resourceGroupName("contosorg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const contentKeyPolicy = new azure_native.media.ContentKeyPolicy("contentKeyPolicy", {
    accountName: "contosomedia",
    contentKeyPolicyName: "PolicyWithPlayReadyOptionAndOpenRestriction",
    description: "ArmPolicyDescription",
    options: [{
        configuration: {
            licenses: [{
                allowTestDevices: true,
                beginDate: "2017-10-16T18:22:53.46Z",
                contentKeyLocation: {
                    odataType: "#Microsoft.Media.ContentKeyPolicyPlayReadyContentEncryptionKeyFromHeader",
                },
                contentType: "UltraVioletDownload",
                licenseType: "Persistent",
                playRight: {
                    allowPassingVideoContentToUnknownOutput: "NotAllowed",
                    digitalVideoOnlyContentRestriction: false,
                    imageConstraintForAnalogComponentVideoRestriction: true,
                    imageConstraintForAnalogComputerMonitorRestriction: false,
                    scmsRestriction: 2,
                },
                securityLevel: "SL150",
            }],
            odataType: "#Microsoft.Media.ContentKeyPolicyPlayReadyConfiguration",
        },
        name: "ArmPolicyOptionName",
        restriction: {
            odataType: "#Microsoft.Media.ContentKeyPolicyOpenRestriction",
        },
    }],
    resourceGroupName: "contosorg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

content_key_policy = azure_native.media.ContentKeyPolicy("contentKeyPolicy",
    account_name="contosomedia",
    content_key_policy_name="PolicyWithPlayReadyOptionAndOpenRestriction",
    description="ArmPolicyDescription",
    options=[azure_native.media.ContentKeyPolicyOptionArgs(
        configuration=azure_native.media.ContentKeyPolicyPlayReadyConfigurationArgs(
            licenses=[azure_native.media.ContentKeyPolicyPlayReadyLicenseArgs(
                allow_test_devices=True,
                begin_date="2017-10-16T18:22:53.46Z",
                content_key_location=azure_native.media.ContentKeyPolicyPlayReadyContentEncryptionKeyFromHeaderArgs(
                    odata_type="#Microsoft.Media.ContentKeyPolicyPlayReadyContentEncryptionKeyFromHeader",
                ),
                content_type="UltraVioletDownload",
                license_type="Persistent",
                play_right=azure_native.media.ContentKeyPolicyPlayReadyPlayRightArgs(
                    allow_passing_video_content_to_unknown_output="NotAllowed",
                    digital_video_only_content_restriction=False,
                    image_constraint_for_analog_component_video_restriction=True,
                    image_constraint_for_analog_computer_monitor_restriction=False,
                    scms_restriction=2,
                ),
                security_level="SL150",
            )],
            odata_type="#Microsoft.Media.ContentKeyPolicyPlayReadyConfiguration",
        ),
        name="ArmPolicyOptionName",
        restriction=azure_native.media.ContentKeyPolicyOpenRestrictionArgs(
            odata_type="#Microsoft.Media.ContentKeyPolicyOpenRestriction",
        ),
    )],
    resource_group_name="contosorg")

```

```yaml
resources:
  contentKeyPolicy:
    type: azure-native:media:ContentKeyPolicy
    properties:
      accountName: contosomedia
      contentKeyPolicyName: PolicyWithPlayReadyOptionAndOpenRestriction
      description: ArmPolicyDescription
      options:
        - configuration:
            licenses:
              - allowTestDevices: true
                beginDate: 2017-10-16T18:22:53.46Z
                contentKeyLocation:
                  odataType: '#Microsoft.Media.ContentKeyPolicyPlayReadyContentEncryptionKeyFromHeader'
                contentType: UltraVioletDownload
                licenseType: Persistent
                playRight:
                  allowPassingVideoContentToUnknownOutput: NotAllowed
                  digitalVideoOnlyContentRestriction: false
                  imageConstraintForAnalogComponentVideoRestriction: true
                  imageConstraintForAnalogComputerMonitorRestriction: false
                  scmsRestriction: 2
                securityLevel: SL150
            odataType: '#Microsoft.Media.ContentKeyPolicyPlayReadyConfiguration'
          name: ArmPolicyOptionName
          restriction:
            odataType: '#Microsoft.Media.ContentKeyPolicyOpenRestriction'
      resourceGroupName: contosorg

```

{{% /example %}}
{{% example %}}
### Creates a Content Key Policy with Widevine option and Token Restriction
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var contentKeyPolicy = new AzureNative.Media.ContentKeyPolicy("contentKeyPolicy", new()
    {
        AccountName = "contosomedia",
        ContentKeyPolicyName = "PolicyWithWidevineOptionAndJwtTokenRestriction",
        Description = "ArmPolicyDescription",
        Options = new[]
        {
            new AzureNative.Media.Inputs.ContentKeyPolicyOptionArgs
            {
                Configuration = new AzureNative.Media.Inputs.ContentKeyPolicyWidevineConfigurationArgs
                {
                    OdataType = "#Microsoft.Media.ContentKeyPolicyWidevineConfiguration",
                    WidevineTemplate = "{\"allowed_track_types\":\"SD_HD\",\"content_key_specs\":[{\"track_type\":\"SD\",\"security_level\":1,\"required_output_protection\":{\"hdcp\":\"HDCP_V2\"}}],\"policy_overrides\":{\"can_play\":true,\"can_persist\":true,\"can_renew\":false}}",
                },
                Name = "widevineoption",
                Restriction = new AzureNative.Media.Inputs.ContentKeyPolicyTokenRestrictionArgs
                {
                    AlternateVerificationKeys = new[]
                    {
                        new AzureNative.Media.Inputs.ContentKeyPolicySymmetricTokenKeyArgs
                        {
                            KeyValue = "AAAAAAAAAAAAAAAAAAAAAA==",
                            OdataType = "#Microsoft.Media.ContentKeyPolicySymmetricTokenKey",
                        },
                    },
                    Audience = "urn:audience",
                    Issuer = "urn:issuer",
                    OdataType = "#Microsoft.Media.ContentKeyPolicyTokenRestriction",
                    PrimaryVerificationKey = new AzureNative.Media.Inputs.ContentKeyPolicyRsaTokenKeyArgs
                    {
                        Exponent = "AQAB",
                        Modulus = "AQAD",
                        OdataType = "#Microsoft.Media.ContentKeyPolicyRsaTokenKey",
                    },
                    RestrictionTokenType = "Jwt",
                },
            },
        },
        ResourceGroupName = "contosorg",
    });

});


```

```go
package main

import (
	media "github.com/pulumi/pulumi-azure-native-sdk/media"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := media.NewContentKeyPolicy(ctx, "contentKeyPolicy", &media.ContentKeyPolicyArgs{
			AccountName:          pulumi.String("contosomedia"),
			ContentKeyPolicyName: pulumi.String("PolicyWithWidevineOptionAndJwtTokenRestriction"),
			Description:          pulumi.String("ArmPolicyDescription"),
			Options: []media.ContentKeyPolicyOptionArgs{
				{
					Configuration: {
						OdataType:        "#Microsoft.Media.ContentKeyPolicyWidevineConfiguration",
						WidevineTemplate: "{\"allowed_track_types\":\"SD_HD\",\"content_key_specs\":[{\"track_type\":\"SD\",\"security_level\":1,\"required_output_protection\":{\"hdcp\":\"HDCP_V2\"}}],\"policy_overrides\":{\"can_play\":true,\"can_persist\":true,\"can_renew\":false}}",
					},
					Name: pulumi.String("widevineoption"),
					Restriction: {
						AlternateVerificationKeys: []interface{}{
							{
								KeyValue:  "AAAAAAAAAAAAAAAAAAAAAA==",
								OdataType: "#Microsoft.Media.ContentKeyPolicySymmetricTokenKey",
							},
						},
						Audience:  "urn:audience",
						Issuer:    "urn:issuer",
						OdataType: "#Microsoft.Media.ContentKeyPolicyTokenRestriction",
						PrimaryVerificationKey: {
							Exponent:  "AQAB",
							Modulus:   "AQAD",
							OdataType: "#Microsoft.Media.ContentKeyPolicyRsaTokenKey",
						},
						RestrictionTokenType: "Jwt",
					},
				},
			},
			ResourceGroupName: pulumi.String("contosorg"),
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
import com.pulumi.azurenative.media.ContentKeyPolicy;
import com.pulumi.azurenative.media.ContentKeyPolicyArgs;
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
        var contentKeyPolicy = new ContentKeyPolicy("contentKeyPolicy", ContentKeyPolicyArgs.builder()        
            .accountName("contosomedia")
            .contentKeyPolicyName("PolicyWithWidevineOptionAndJwtTokenRestriction")
            .description("ArmPolicyDescription")
            .options(Map.ofEntries(
                Map.entry("configuration", Map.ofEntries(
                    Map.entry("odataType", "#Microsoft.Media.ContentKeyPolicyWidevineConfiguration"),
                    Map.entry("widevineTemplate", "{\"allowed_track_types\":\"SD_HD\",\"content_key_specs\":[{\"track_type\":\"SD\",\"security_level\":1,\"required_output_protection\":{\"hdcp\":\"HDCP_V2\"}}],\"policy_overrides\":{\"can_play\":true,\"can_persist\":true,\"can_renew\":false}}")
                )),
                Map.entry("name", "widevineoption"),
                Map.entry("restriction", Map.ofEntries(
                    Map.entry("alternateVerificationKeys", Map.ofEntries(
                        Map.entry("keyValue", "AAAAAAAAAAAAAAAAAAAAAA=="),
                        Map.entry("odataType", "#Microsoft.Media.ContentKeyPolicySymmetricTokenKey")
                    )),
                    Map.entry("audience", "urn:audience"),
                    Map.entry("issuer", "urn:issuer"),
                    Map.entry("odataType", "#Microsoft.Media.ContentKeyPolicyTokenRestriction"),
                    Map.entry("primaryVerificationKey", Map.ofEntries(
                        Map.entry("exponent", "AQAB"),
                        Map.entry("modulus", "AQAD"),
                        Map.entry("odataType", "#Microsoft.Media.ContentKeyPolicyRsaTokenKey")
                    )),
                    Map.entry("restrictionTokenType", "Jwt")
                ))
            ))
            .resourceGroupName("contosorg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const contentKeyPolicy = new azure_native.media.ContentKeyPolicy("contentKeyPolicy", {
    accountName: "contosomedia",
    contentKeyPolicyName: "PolicyWithWidevineOptionAndJwtTokenRestriction",
    description: "ArmPolicyDescription",
    options: [{
        configuration: {
            odataType: "#Microsoft.Media.ContentKeyPolicyWidevineConfiguration",
            widevineTemplate: "{\"allowed_track_types\":\"SD_HD\",\"content_key_specs\":[{\"track_type\":\"SD\",\"security_level\":1,\"required_output_protection\":{\"hdcp\":\"HDCP_V2\"}}],\"policy_overrides\":{\"can_play\":true,\"can_persist\":true,\"can_renew\":false}}",
        },
        name: "widevineoption",
        restriction: {
            alternateVerificationKeys: [{
                keyValue: "AAAAAAAAAAAAAAAAAAAAAA==",
                odataType: "#Microsoft.Media.ContentKeyPolicySymmetricTokenKey",
            }],
            audience: "urn:audience",
            issuer: "urn:issuer",
            odataType: "#Microsoft.Media.ContentKeyPolicyTokenRestriction",
            primaryVerificationKey: {
                exponent: "AQAB",
                modulus: "AQAD",
                odataType: "#Microsoft.Media.ContentKeyPolicyRsaTokenKey",
            },
            restrictionTokenType: "Jwt",
        },
    }],
    resourceGroupName: "contosorg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

content_key_policy = azure_native.media.ContentKeyPolicy("contentKeyPolicy",
    account_name="contosomedia",
    content_key_policy_name="PolicyWithWidevineOptionAndJwtTokenRestriction",
    description="ArmPolicyDescription",
    options=[azure_native.media.ContentKeyPolicyOptionArgs(
        configuration=azure_native.media.ContentKeyPolicyWidevineConfigurationArgs(
            odata_type="#Microsoft.Media.ContentKeyPolicyWidevineConfiguration",
            widevine_template="{\"allowed_track_types\":\"SD_HD\",\"content_key_specs\":[{\"track_type\":\"SD\",\"security_level\":1,\"required_output_protection\":{\"hdcp\":\"HDCP_V2\"}}],\"policy_overrides\":{\"can_play\":true,\"can_persist\":true,\"can_renew\":false}}",
        ),
        name="widevineoption",
        restriction=azure_native.media.ContentKeyPolicyTokenRestrictionArgs(
            alternate_verification_keys=[azure_native.media.ContentKeyPolicySymmetricTokenKeyArgs(
                key_value="AAAAAAAAAAAAAAAAAAAAAA==",
                odata_type="#Microsoft.Media.ContentKeyPolicySymmetricTokenKey",
            )],
            audience="urn:audience",
            issuer="urn:issuer",
            odata_type="#Microsoft.Media.ContentKeyPolicyTokenRestriction",
            primary_verification_key=azure_native.media.ContentKeyPolicyRsaTokenKeyArgs(
                exponent="AQAB",
                modulus="AQAD",
                odata_type="#Microsoft.Media.ContentKeyPolicyRsaTokenKey",
            ),
            restriction_token_type="Jwt",
        ),
    )],
    resource_group_name="contosorg")

```

```yaml
resources:
  contentKeyPolicy:
    type: azure-native:media:ContentKeyPolicy
    properties:
      accountName: contosomedia
      contentKeyPolicyName: PolicyWithWidevineOptionAndJwtTokenRestriction
      description: ArmPolicyDescription
      options:
        - configuration:
            odataType: '#Microsoft.Media.ContentKeyPolicyWidevineConfiguration'
            widevineTemplate: '{"allowed_track_types":"SD_HD","content_key_specs":[{"track_type":"SD","security_level":1,"required_output_protection":{"hdcp":"HDCP_V2"}}],"policy_overrides":{"can_play":true,"can_persist":true,"can_renew":false}}'
          name: widevineoption
          restriction:
            alternateVerificationKeys:
              - keyValue: AAAAAAAAAAAAAAAAAAAAAA==
                odataType: '#Microsoft.Media.ContentKeyPolicySymmetricTokenKey'
            audience: urn:audience
            issuer: urn:issuer
            odataType: '#Microsoft.Media.ContentKeyPolicyTokenRestriction'
            primaryVerificationKey:
              exponent: AQAB
              modulus: AQAD
              odataType: '#Microsoft.Media.ContentKeyPolicyRsaTokenKey'
            restrictionTokenType: Jwt
      resourceGroupName: contosorg

```

{{% /example %}}
{{% example %}}
### Creates a Content Key Policy with multiple options
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var contentKeyPolicy = new AzureNative.Media.ContentKeyPolicy("contentKeyPolicy", new()
    {
        AccountName = "contosomedia",
        ContentKeyPolicyName = "PolicyCreatedWithMultipleOptions",
        Description = "ArmPolicyDescription",
        Options = new[]
        {
            new AzureNative.Media.Inputs.ContentKeyPolicyOptionArgs
            {
                Configuration = new AzureNative.Media.Inputs.ContentKeyPolicyClearKeyConfigurationArgs
                {
                    OdataType = "#Microsoft.Media.ContentKeyPolicyClearKeyConfiguration",
                },
                Name = "ClearKeyOption",
                Restriction = new AzureNative.Media.Inputs.ContentKeyPolicyTokenRestrictionArgs
                {
                    Audience = "urn:audience",
                    Issuer = "urn:issuer",
                    OdataType = "#Microsoft.Media.ContentKeyPolicyTokenRestriction",
                    PrimaryVerificationKey = new AzureNative.Media.Inputs.ContentKeyPolicySymmetricTokenKeyArgs
                    {
                        KeyValue = "AAAAAAAAAAAAAAAAAAAAAA==",
                        OdataType = "#Microsoft.Media.ContentKeyPolicySymmetricTokenKey",
                    },
                    RestrictionTokenType = "Swt",
                },
            },
            new AzureNative.Media.Inputs.ContentKeyPolicyOptionArgs
            {
                Configuration = new AzureNative.Media.Inputs.ContentKeyPolicyWidevineConfigurationArgs
                {
                    OdataType = "#Microsoft.Media.ContentKeyPolicyWidevineConfiguration",
                    WidevineTemplate = "{\"allowed_track_types\":\"SD_HD\",\"content_key_specs\":[{\"track_type\":\"SD\",\"security_level\":1,\"required_output_protection\":{\"hdcp\":\"HDCP_V2\"}}],\"policy_overrides\":{\"can_play\":true,\"can_persist\":true,\"can_renew\":false}}",
                },
                Name = "widevineoption",
                Restriction = new AzureNative.Media.Inputs.ContentKeyPolicyOpenRestrictionArgs
                {
                    OdataType = "#Microsoft.Media.ContentKeyPolicyOpenRestriction",
                },
            },
        },
        ResourceGroupName = "contosorg",
    });

});


```

```go
package main

import (
	media "github.com/pulumi/pulumi-azure-native-sdk/media"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := media.NewContentKeyPolicy(ctx, "contentKeyPolicy", &media.ContentKeyPolicyArgs{
			AccountName:          pulumi.String("contosomedia"),
			ContentKeyPolicyName: pulumi.String("PolicyCreatedWithMultipleOptions"),
			Description:          pulumi.String("ArmPolicyDescription"),
			Options: []media.ContentKeyPolicyOptionArgs{
				{
					Configuration: {
						OdataType: "#Microsoft.Media.ContentKeyPolicyClearKeyConfiguration",
					},
					Name: pulumi.String("ClearKeyOption"),
					Restriction: {
						Audience:  "urn:audience",
						Issuer:    "urn:issuer",
						OdataType: "#Microsoft.Media.ContentKeyPolicyTokenRestriction",
						PrimaryVerificationKey: {
							KeyValue:  "AAAAAAAAAAAAAAAAAAAAAA==",
							OdataType: "#Microsoft.Media.ContentKeyPolicySymmetricTokenKey",
						},
						RestrictionTokenType: "Swt",
					},
				},
				{
					Configuration: {
						OdataType:        "#Microsoft.Media.ContentKeyPolicyWidevineConfiguration",
						WidevineTemplate: "{\"allowed_track_types\":\"SD_HD\",\"content_key_specs\":[{\"track_type\":\"SD\",\"security_level\":1,\"required_output_protection\":{\"hdcp\":\"HDCP_V2\"}}],\"policy_overrides\":{\"can_play\":true,\"can_persist\":true,\"can_renew\":false}}",
					},
					Name: pulumi.String("widevineoption"),
					Restriction: {
						OdataType: "#Microsoft.Media.ContentKeyPolicyOpenRestriction",
					},
				},
			},
			ResourceGroupName: pulumi.String("contosorg"),
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
import com.pulumi.azurenative.media.ContentKeyPolicy;
import com.pulumi.azurenative.media.ContentKeyPolicyArgs;
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
        var contentKeyPolicy = new ContentKeyPolicy("contentKeyPolicy", ContentKeyPolicyArgs.builder()        
            .accountName("contosomedia")
            .contentKeyPolicyName("PolicyCreatedWithMultipleOptions")
            .description("ArmPolicyDescription")
            .options(            
                Map.ofEntries(
                    Map.entry("configuration", Map.of("odataType", "#Microsoft.Media.ContentKeyPolicyClearKeyConfiguration")),
                    Map.entry("name", "ClearKeyOption"),
                    Map.entry("restriction", Map.ofEntries(
                        Map.entry("audience", "urn:audience"),
                        Map.entry("issuer", "urn:issuer"),
                        Map.entry("odataType", "#Microsoft.Media.ContentKeyPolicyTokenRestriction"),
                        Map.entry("primaryVerificationKey", Map.ofEntries(
                            Map.entry("keyValue", "AAAAAAAAAAAAAAAAAAAAAA=="),
                            Map.entry("odataType", "#Microsoft.Media.ContentKeyPolicySymmetricTokenKey")
                        )),
                        Map.entry("restrictionTokenType", "Swt")
                    ))
                ),
                Map.ofEntries(
                    Map.entry("configuration", Map.ofEntries(
                        Map.entry("odataType", "#Microsoft.Media.ContentKeyPolicyWidevineConfiguration"),
                        Map.entry("widevineTemplate", "{\"allowed_track_types\":\"SD_HD\",\"content_key_specs\":[{\"track_type\":\"SD\",\"security_level\":1,\"required_output_protection\":{\"hdcp\":\"HDCP_V2\"}}],\"policy_overrides\":{\"can_play\":true,\"can_persist\":true,\"can_renew\":false}}")
                    )),
                    Map.entry("name", "widevineoption"),
                    Map.entry("restriction", Map.of("odataType", "#Microsoft.Media.ContentKeyPolicyOpenRestriction"))
                ))
            .resourceGroupName("contosorg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const contentKeyPolicy = new azure_native.media.ContentKeyPolicy("contentKeyPolicy", {
    accountName: "contosomedia",
    contentKeyPolicyName: "PolicyCreatedWithMultipleOptions",
    description: "ArmPolicyDescription",
    options: [
        {
            configuration: {
                odataType: "#Microsoft.Media.ContentKeyPolicyClearKeyConfiguration",
            },
            name: "ClearKeyOption",
            restriction: {
                audience: "urn:audience",
                issuer: "urn:issuer",
                odataType: "#Microsoft.Media.ContentKeyPolicyTokenRestriction",
                primaryVerificationKey: {
                    keyValue: "AAAAAAAAAAAAAAAAAAAAAA==",
                    odataType: "#Microsoft.Media.ContentKeyPolicySymmetricTokenKey",
                },
                restrictionTokenType: "Swt",
            },
        },
        {
            configuration: {
                odataType: "#Microsoft.Media.ContentKeyPolicyWidevineConfiguration",
                widevineTemplate: "{\"allowed_track_types\":\"SD_HD\",\"content_key_specs\":[{\"track_type\":\"SD\",\"security_level\":1,\"required_output_protection\":{\"hdcp\":\"HDCP_V2\"}}],\"policy_overrides\":{\"can_play\":true,\"can_persist\":true,\"can_renew\":false}}",
            },
            name: "widevineoption",
            restriction: {
                odataType: "#Microsoft.Media.ContentKeyPolicyOpenRestriction",
            },
        },
    ],
    resourceGroupName: "contosorg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

content_key_policy = azure_native.media.ContentKeyPolicy("contentKeyPolicy",
    account_name="contosomedia",
    content_key_policy_name="PolicyCreatedWithMultipleOptions",
    description="ArmPolicyDescription",
    options=[
        azure_native.media.ContentKeyPolicyOptionArgs(
            configuration=azure_native.media.ContentKeyPolicyClearKeyConfigurationArgs(
                odata_type="#Microsoft.Media.ContentKeyPolicyClearKeyConfiguration",
            ),
            name="ClearKeyOption",
            restriction=azure_native.media.ContentKeyPolicyTokenRestrictionArgs(
                audience="urn:audience",
                issuer="urn:issuer",
                odata_type="#Microsoft.Media.ContentKeyPolicyTokenRestriction",
                primary_verification_key=azure_native.media.ContentKeyPolicySymmetricTokenKeyArgs(
                    key_value="AAAAAAAAAAAAAAAAAAAAAA==",
                    odata_type="#Microsoft.Media.ContentKeyPolicySymmetricTokenKey",
                ),
                restriction_token_type="Swt",
            ),
        ),
        azure_native.media.ContentKeyPolicyOptionArgs(
            configuration=azure_native.media.ContentKeyPolicyWidevineConfigurationArgs(
                odata_type="#Microsoft.Media.ContentKeyPolicyWidevineConfiguration",
                widevine_template="{\"allowed_track_types\":\"SD_HD\",\"content_key_specs\":[{\"track_type\":\"SD\",\"security_level\":1,\"required_output_protection\":{\"hdcp\":\"HDCP_V2\"}}],\"policy_overrides\":{\"can_play\":true,\"can_persist\":true,\"can_renew\":false}}",
            ),
            name="widevineoption",
            restriction=azure_native.media.ContentKeyPolicyOpenRestrictionArgs(
                odata_type="#Microsoft.Media.ContentKeyPolicyOpenRestriction",
            ),
        ),
    ],
    resource_group_name="contosorg")

```

```yaml
resources:
  contentKeyPolicy:
    type: azure-native:media:ContentKeyPolicy
    properties:
      accountName: contosomedia
      contentKeyPolicyName: PolicyCreatedWithMultipleOptions
      description: ArmPolicyDescription
      options:
        - configuration:
            odataType: '#Microsoft.Media.ContentKeyPolicyClearKeyConfiguration'
          name: ClearKeyOption
          restriction:
            audience: urn:audience
            issuer: urn:issuer
            odataType: '#Microsoft.Media.ContentKeyPolicyTokenRestriction'
            primaryVerificationKey:
              keyValue: AAAAAAAAAAAAAAAAAAAAAA==
              odataType: '#Microsoft.Media.ContentKeyPolicySymmetricTokenKey'
            restrictionTokenType: Swt
        - configuration:
            odataType: '#Microsoft.Media.ContentKeyPolicyWidevineConfiguration'
            widevineTemplate: '{"allowed_track_types":"SD_HD","content_key_specs":[{"track_type":"SD","security_level":1,"required_output_protection":{"hdcp":"HDCP_V2"}}],"policy_overrides":{"can_play":true,"can_persist":true,"can_renew":false}}'
          name: widevineoption
          restriction:
            odataType: '#Microsoft.Media.ContentKeyPolicyOpenRestriction'
      resourceGroupName: contosorg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:media:ContentKeyPolicy PolicyCreatedWithMultipleOptions /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/contosorg/providers/Microsoft.Media/mediaservices/contosomedia/contentKeyPolicies/PolicyCreatedWithMultipleOptions 
```
