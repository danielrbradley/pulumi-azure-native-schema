A Streaming Policy resource
API Version: 2022-08-01.
Previous API Version: 2020-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates a Streaming Policy with ClearKey encryption in commonEncryptionCbcs.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var streamingPolicy = new AzureNative.Media.StreamingPolicy("streamingPolicy", new()
    {
        AccountName = "contosomedia",
        CommonEncryptionCbcs = new AzureNative.Media.Inputs.CommonEncryptionCbcsArgs
        {
            ClearKeyEncryptionConfiguration = new AzureNative.Media.Inputs.ClearKeyEncryptionConfigurationArgs
            {
                CustomKeysAcquisitionUrlTemplate = "https://contoso.com/{AlternativeMediaId}/clearkey/",
            },
            ContentKeys = new AzureNative.Media.Inputs.StreamingPolicyContentKeysArgs
            {
                DefaultKey = new AzureNative.Media.Inputs.DefaultKeyArgs
                {
                    Label = "cbcsDefaultKey",
                },
            },
            EnabledProtocols = new AzureNative.Media.Inputs.EnabledProtocolsArgs
            {
                Dash = false,
                Download = false,
                Hls = true,
                SmoothStreaming = false,
            },
        },
        DefaultContentKeyPolicyName = "PolicyWithMultipleOptions",
        ResourceGroupName = "contosorg",
        StreamingPolicyName = "UserCreatedSecureStreamingPolicyWithCommonEncryptionCbcsOnly",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.media.StreamingPolicy;
import com.pulumi.azurenative.media.StreamingPolicyArgs;
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
        var streamingPolicy = new StreamingPolicy("streamingPolicy", StreamingPolicyArgs.builder()        
            .accountName("contosomedia")
            .commonEncryptionCbcs(Map.ofEntries(
                Map.entry("clearKeyEncryptionConfiguration", Map.of("customKeysAcquisitionUrlTemplate", "https://contoso.com/{AlternativeMediaId}/clearkey/")),
                Map.entry("contentKeys", Map.of("defaultKey", Map.of("label", "cbcsDefaultKey"))),
                Map.entry("enabledProtocols", Map.ofEntries(
                    Map.entry("dash", false),
                    Map.entry("download", false),
                    Map.entry("hls", true),
                    Map.entry("smoothStreaming", false)
                ))
            ))
            .defaultContentKeyPolicyName("PolicyWithMultipleOptions")
            .resourceGroupName("contosorg")
            .streamingPolicyName("UserCreatedSecureStreamingPolicyWithCommonEncryptionCbcsOnly")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const streamingPolicy = new azure_native.media.StreamingPolicy("streamingPolicy", {
    accountName: "contosomedia",
    commonEncryptionCbcs: {
        clearKeyEncryptionConfiguration: {
            customKeysAcquisitionUrlTemplate: "https://contoso.com/{AlternativeMediaId}/clearkey/",
        },
        contentKeys: {
            defaultKey: {
                label: "cbcsDefaultKey",
            },
        },
        enabledProtocols: {
            dash: false,
            download: false,
            hls: true,
            smoothStreaming: false,
        },
    },
    defaultContentKeyPolicyName: "PolicyWithMultipleOptions",
    resourceGroupName: "contosorg",
    streamingPolicyName: "UserCreatedSecureStreamingPolicyWithCommonEncryptionCbcsOnly",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

streaming_policy = azure_native.media.StreamingPolicy("streamingPolicy",
    account_name="contosomedia",
    common_encryption_cbcs=azure_native.media.CommonEncryptionCbcsResponseArgs(
        clear_key_encryption_configuration=azure_native.media.ClearKeyEncryptionConfigurationArgs(
            custom_keys_acquisition_url_template="https://contoso.com/{AlternativeMediaId}/clearkey/",
        ),
        content_keys={
            "defaultKey": azure_native.media.DefaultKeyArgs(
                label="cbcsDefaultKey",
            ),
        },
        enabled_protocols=azure_native.media.EnabledProtocolsArgs(
            dash=False,
            download=False,
            hls=True,
            smooth_streaming=False,
        ),
    ),
    default_content_key_policy_name="PolicyWithMultipleOptions",
    resource_group_name="contosorg",
    streaming_policy_name="UserCreatedSecureStreamingPolicyWithCommonEncryptionCbcsOnly")

```

```yaml
resources:
  streamingPolicy:
    type: azure-native:media:StreamingPolicy
    properties:
      accountName: contosomedia
      commonEncryptionCbcs:
        clearKeyEncryptionConfiguration:
          customKeysAcquisitionUrlTemplate: https://contoso.com/{AlternativeMediaId}/clearkey/
        contentKeys:
          defaultKey:
            label: cbcsDefaultKey
        enabledProtocols:
          dash: false
          download: false
          hls: true
          smoothStreaming: false
      defaultContentKeyPolicyName: PolicyWithMultipleOptions
      resourceGroupName: contosorg
      streamingPolicyName: UserCreatedSecureStreamingPolicyWithCommonEncryptionCbcsOnly

```

{{% /example %}}
{{% example %}}
### Creates a Streaming Policy with ClearKey encryption in commonEncryptionCenc.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var streamingPolicy = new AzureNative.Media.StreamingPolicy("streamingPolicy", new()
    {
        AccountName = "contosomedia",
        CommonEncryptionCenc = new AzureNative.Media.Inputs.CommonEncryptionCencArgs
        {
            ClearKeyEncryptionConfiguration = new AzureNative.Media.Inputs.ClearKeyEncryptionConfigurationArgs
            {
                CustomKeysAcquisitionUrlTemplate = "https://contoso.com/{AlternativeMediaId}/clearkey/",
            },
            ClearTracks = new[]
            {
                new AzureNative.Media.Inputs.TrackSelectionArgs
                {
                    TrackSelections = new[]
                    {
                        new AzureNative.Media.Inputs.TrackPropertyConditionArgs
                        {
                            Operation = "Equal",
                            Property = "FourCC",
                            Value = "hev1",
                        },
                    },
                },
            },
            ContentKeys = new AzureNative.Media.Inputs.StreamingPolicyContentKeysArgs
            {
                DefaultKey = new AzureNative.Media.Inputs.DefaultKeyArgs
                {
                    Label = "cencDefaultKey",
                },
            },
            EnabledProtocols = new AzureNative.Media.Inputs.EnabledProtocolsArgs
            {
                Dash = true,
                Download = false,
                Hls = false,
                SmoothStreaming = true,
            },
        },
        DefaultContentKeyPolicyName = "PolicyWithPlayReadyOptionAndOpenRestriction",
        ResourceGroupName = "contosorg",
        StreamingPolicyName = "UserCreatedSecureStreamingPolicyWithCommonEncryptionCencOnly",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.media.StreamingPolicy;
import com.pulumi.azurenative.media.StreamingPolicyArgs;
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
        var streamingPolicy = new StreamingPolicy("streamingPolicy", StreamingPolicyArgs.builder()        
            .accountName("contosomedia")
            .commonEncryptionCenc(Map.ofEntries(
                Map.entry("clearKeyEncryptionConfiguration", Map.of("customKeysAcquisitionUrlTemplate", "https://contoso.com/{AlternativeMediaId}/clearkey/")),
                Map.entry("clearTracks", Map.of("trackSelections", Map.ofEntries(
                    Map.entry("operation", "Equal"),
                    Map.entry("property", "FourCC"),
                    Map.entry("value", "hev1")
                ))),
                Map.entry("contentKeys", Map.of("defaultKey", Map.of("label", "cencDefaultKey"))),
                Map.entry("enabledProtocols", Map.ofEntries(
                    Map.entry("dash", true),
                    Map.entry("download", false),
                    Map.entry("hls", false),
                    Map.entry("smoothStreaming", true)
                ))
            ))
            .defaultContentKeyPolicyName("PolicyWithPlayReadyOptionAndOpenRestriction")
            .resourceGroupName("contosorg")
            .streamingPolicyName("UserCreatedSecureStreamingPolicyWithCommonEncryptionCencOnly")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const streamingPolicy = new azure_native.media.StreamingPolicy("streamingPolicy", {
    accountName: "contosomedia",
    commonEncryptionCenc: {
        clearKeyEncryptionConfiguration: {
            customKeysAcquisitionUrlTemplate: "https://contoso.com/{AlternativeMediaId}/clearkey/",
        },
        clearTracks: [{
            trackSelections: [{
                operation: "Equal",
                property: "FourCC",
                value: "hev1",
            }],
        }],
        contentKeys: {
            defaultKey: {
                label: "cencDefaultKey",
            },
        },
        enabledProtocols: {
            dash: true,
            download: false,
            hls: false,
            smoothStreaming: true,
        },
    },
    defaultContentKeyPolicyName: "PolicyWithPlayReadyOptionAndOpenRestriction",
    resourceGroupName: "contosorg",
    streamingPolicyName: "UserCreatedSecureStreamingPolicyWithCommonEncryptionCencOnly",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

streaming_policy = azure_native.media.StreamingPolicy("streamingPolicy",
    account_name="contosomedia",
    common_encryption_cenc=azure_native.media.CommonEncryptionCencResponseArgs(
        clear_key_encryption_configuration=azure_native.media.ClearKeyEncryptionConfigurationArgs(
            custom_keys_acquisition_url_template="https://contoso.com/{AlternativeMediaId}/clearkey/",
        ),
        clear_tracks=[{
            "trackSelections": [azure_native.media.TrackPropertyConditionArgs(
                operation="Equal",
                property="FourCC",
                value="hev1",
            )],
        }],
        content_keys={
            "defaultKey": azure_native.media.DefaultKeyArgs(
                label="cencDefaultKey",
            ),
        },
        enabled_protocols=azure_native.media.EnabledProtocolsArgs(
            dash=True,
            download=False,
            hls=False,
            smooth_streaming=True,
        ),
    ),
    default_content_key_policy_name="PolicyWithPlayReadyOptionAndOpenRestriction",
    resource_group_name="contosorg",
    streaming_policy_name="UserCreatedSecureStreamingPolicyWithCommonEncryptionCencOnly")

```

```yaml
resources:
  streamingPolicy:
    type: azure-native:media:StreamingPolicy
    properties:
      accountName: contosomedia
      commonEncryptionCenc:
        clearKeyEncryptionConfiguration:
          customKeysAcquisitionUrlTemplate: https://contoso.com/{AlternativeMediaId}/clearkey/
        clearTracks:
          - trackSelections:
              - operation: Equal
                property: FourCC
                value: hev1
        contentKeys:
          defaultKey:
            label: cencDefaultKey
        enabledProtocols:
          dash: true
          download: false
          hls: false
          smoothStreaming: true
      defaultContentKeyPolicyName: PolicyWithPlayReadyOptionAndOpenRestriction
      resourceGroupName: contosorg
      streamingPolicyName: UserCreatedSecureStreamingPolicyWithCommonEncryptionCencOnly

```

{{% /example %}}
{{% example %}}
### Creates a Streaming Policy with clear streaming
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var streamingPolicy = new AzureNative.Media.StreamingPolicy("streamingPolicy", new()
    {
        AccountName = "contosomedia",
        NoEncryption = new AzureNative.Media.Inputs.NoEncryptionArgs
        {
            EnabledProtocols = new AzureNative.Media.Inputs.EnabledProtocolsArgs
            {
                Dash = true,
                Download = true,
                Hls = true,
                SmoothStreaming = true,
            },
        },
        ResourceGroupName = "contosorg",
        StreamingPolicyName = "clearStreamingPolicy",
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
		_, err := media.NewStreamingPolicy(ctx, "streamingPolicy", &media.StreamingPolicyArgs{
			AccountName: pulumi.String("contosomedia"),
			NoEncryption: media.NoEncryptionResponse{
				EnabledProtocols: &media.EnabledProtocolsArgs{
					Dash:            pulumi.Bool(true),
					Download:        pulumi.Bool(true),
					Hls:             pulumi.Bool(true),
					SmoothStreaming: pulumi.Bool(true),
				},
			},
			ResourceGroupName:   pulumi.String("contosorg"),
			StreamingPolicyName: pulumi.String("clearStreamingPolicy"),
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
import com.pulumi.azurenative.media.StreamingPolicy;
import com.pulumi.azurenative.media.StreamingPolicyArgs;
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
        var streamingPolicy = new StreamingPolicy("streamingPolicy", StreamingPolicyArgs.builder()        
            .accountName("contosomedia")
            .noEncryption(Map.of("enabledProtocols", Map.ofEntries(
                Map.entry("dash", true),
                Map.entry("download", true),
                Map.entry("hls", true),
                Map.entry("smoothStreaming", true)
            )))
            .resourceGroupName("contosorg")
            .streamingPolicyName("clearStreamingPolicy")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const streamingPolicy = new azure_native.media.StreamingPolicy("streamingPolicy", {
    accountName: "contosomedia",
    noEncryption: {
        enabledProtocols: {
            dash: true,
            download: true,
            hls: true,
            smoothStreaming: true,
        },
    },
    resourceGroupName: "contosorg",
    streamingPolicyName: "clearStreamingPolicy",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

streaming_policy = azure_native.media.StreamingPolicy("streamingPolicy",
    account_name="contosomedia",
    no_encryption=azure_native.media.NoEncryptionResponseArgs(
        enabled_protocols=azure_native.media.EnabledProtocolsArgs(
            dash=True,
            download=True,
            hls=True,
            smooth_streaming=True,
        ),
    ),
    resource_group_name="contosorg",
    streaming_policy_name="clearStreamingPolicy")

```

```yaml
resources:
  streamingPolicy:
    type: azure-native:media:StreamingPolicy
    properties:
      accountName: contosomedia
      noEncryption:
        enabledProtocols:
          dash: true
          download: true
          hls: true
          smoothStreaming: true
      resourceGroupName: contosorg
      streamingPolicyName: clearStreamingPolicy

```

{{% /example %}}
{{% example %}}
### Creates a Streaming Policy with commonEncryptionCbcs only
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var streamingPolicy = new AzureNative.Media.StreamingPolicy("streamingPolicy", new()
    {
        AccountName = "contosomedia",
        CommonEncryptionCbcs = new AzureNative.Media.Inputs.CommonEncryptionCbcsArgs
        {
            ContentKeys = new AzureNative.Media.Inputs.StreamingPolicyContentKeysArgs
            {
                DefaultKey = new AzureNative.Media.Inputs.DefaultKeyArgs
                {
                    Label = "cbcsDefaultKey",
                },
            },
            Drm = new AzureNative.Media.Inputs.CbcsDrmConfigurationArgs
            {
                FairPlay = new AzureNative.Media.Inputs.StreamingPolicyFairPlayConfigurationArgs
                {
                    AllowPersistentLicense = true,
                    CustomLicenseAcquisitionUrlTemplate = "https://contoso.com/{AssetAlternativeId}/fairplay/{ContentKeyId}",
                },
            },
            EnabledProtocols = new AzureNative.Media.Inputs.EnabledProtocolsArgs
            {
                Dash = false,
                Download = false,
                Hls = true,
                SmoothStreaming = false,
            },
        },
        DefaultContentKeyPolicyName = "PolicyWithMultipleOptions",
        ResourceGroupName = "contosorg",
        StreamingPolicyName = "UserCreatedSecureStreamingPolicyWithCommonEncryptionCbcsOnly",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.media.StreamingPolicy;
import com.pulumi.azurenative.media.StreamingPolicyArgs;
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
        var streamingPolicy = new StreamingPolicy("streamingPolicy", StreamingPolicyArgs.builder()        
            .accountName("contosomedia")
            .commonEncryptionCbcs(Map.ofEntries(
                Map.entry("contentKeys", Map.of("defaultKey", Map.of("label", "cbcsDefaultKey"))),
                Map.entry("drm", Map.of("fairPlay", Map.ofEntries(
                    Map.entry("allowPersistentLicense", true),
                    Map.entry("customLicenseAcquisitionUrlTemplate", "https://contoso.com/{AssetAlternativeId}/fairplay/{ContentKeyId}")
                ))),
                Map.entry("enabledProtocols", Map.ofEntries(
                    Map.entry("dash", false),
                    Map.entry("download", false),
                    Map.entry("hls", true),
                    Map.entry("smoothStreaming", false)
                ))
            ))
            .defaultContentKeyPolicyName("PolicyWithMultipleOptions")
            .resourceGroupName("contosorg")
            .streamingPolicyName("UserCreatedSecureStreamingPolicyWithCommonEncryptionCbcsOnly")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const streamingPolicy = new azure_native.media.StreamingPolicy("streamingPolicy", {
    accountName: "contosomedia",
    commonEncryptionCbcs: {
        contentKeys: {
            defaultKey: {
                label: "cbcsDefaultKey",
            },
        },
        drm: {
            fairPlay: {
                allowPersistentLicense: true,
                customLicenseAcquisitionUrlTemplate: "https://contoso.com/{AssetAlternativeId}/fairplay/{ContentKeyId}",
            },
        },
        enabledProtocols: {
            dash: false,
            download: false,
            hls: true,
            smoothStreaming: false,
        },
    },
    defaultContentKeyPolicyName: "PolicyWithMultipleOptions",
    resourceGroupName: "contosorg",
    streamingPolicyName: "UserCreatedSecureStreamingPolicyWithCommonEncryptionCbcsOnly",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

streaming_policy = azure_native.media.StreamingPolicy("streamingPolicy",
    account_name="contosomedia",
    common_encryption_cbcs=azure_native.media.CommonEncryptionCbcsResponseArgs(
        content_keys={
            "defaultKey": azure_native.media.DefaultKeyArgs(
                label="cbcsDefaultKey",
            ),
        },
        drm={
            "fairPlay": azure_native.media.StreamingPolicyFairPlayConfigurationArgs(
                allow_persistent_license=True,
                custom_license_acquisition_url_template="https://contoso.com/{AssetAlternativeId}/fairplay/{ContentKeyId}",
            ),
        },
        enabled_protocols=azure_native.media.EnabledProtocolsArgs(
            dash=False,
            download=False,
            hls=True,
            smooth_streaming=False,
        ),
    ),
    default_content_key_policy_name="PolicyWithMultipleOptions",
    resource_group_name="contosorg",
    streaming_policy_name="UserCreatedSecureStreamingPolicyWithCommonEncryptionCbcsOnly")

```

```yaml
resources:
  streamingPolicy:
    type: azure-native:media:StreamingPolicy
    properties:
      accountName: contosomedia
      commonEncryptionCbcs:
        contentKeys:
          defaultKey:
            label: cbcsDefaultKey
        drm:
          fairPlay:
            allowPersistentLicense: true
            customLicenseAcquisitionUrlTemplate: https://contoso.com/{AssetAlternativeId}/fairplay/{ContentKeyId}
        enabledProtocols:
          dash: false
          download: false
          hls: true
          smoothStreaming: false
      defaultContentKeyPolicyName: PolicyWithMultipleOptions
      resourceGroupName: contosorg
      streamingPolicyName: UserCreatedSecureStreamingPolicyWithCommonEncryptionCbcsOnly

```

{{% /example %}}
{{% example %}}
### Creates a Streaming Policy with commonEncryptionCenc only
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var streamingPolicy = new AzureNative.Media.StreamingPolicy("streamingPolicy", new()
    {
        AccountName = "contosomedia",
        CommonEncryptionCenc = new AzureNative.Media.Inputs.CommonEncryptionCencArgs
        {
            ClearTracks = new[]
            {
                new AzureNative.Media.Inputs.TrackSelectionArgs
                {
                    TrackSelections = new[]
                    {
                        new AzureNative.Media.Inputs.TrackPropertyConditionArgs
                        {
                            Operation = "Equal",
                            Property = "FourCC",
                            Value = "hev1",
                        },
                    },
                },
            },
            ContentKeys = new AzureNative.Media.Inputs.StreamingPolicyContentKeysArgs
            {
                DefaultKey = new AzureNative.Media.Inputs.DefaultKeyArgs
                {
                    Label = "cencDefaultKey",
                },
            },
            Drm = new AzureNative.Media.Inputs.CencDrmConfigurationArgs
            {
                PlayReady = new AzureNative.Media.Inputs.StreamingPolicyPlayReadyConfigurationArgs
                {
                    CustomLicenseAcquisitionUrlTemplate = "https://contoso.com/{AssetAlternativeId}/playready/{ContentKeyId}",
                    PlayReadyCustomAttributes = "PlayReady CustomAttributes",
                },
                Widevine = new AzureNative.Media.Inputs.StreamingPolicyWidevineConfigurationArgs
                {
                    CustomLicenseAcquisitionUrlTemplate = "https://contoso.com/{AssetAlternativeId}/widevine/{ContentKeyId",
                },
            },
            EnabledProtocols = new AzureNative.Media.Inputs.EnabledProtocolsArgs
            {
                Dash = true,
                Download = false,
                Hls = false,
                SmoothStreaming = true,
            },
        },
        DefaultContentKeyPolicyName = "PolicyWithPlayReadyOptionAndOpenRestriction",
        ResourceGroupName = "contosorg",
        StreamingPolicyName = "UserCreatedSecureStreamingPolicyWithCommonEncryptionCencOnly",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.media.StreamingPolicy;
import com.pulumi.azurenative.media.StreamingPolicyArgs;
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
        var streamingPolicy = new StreamingPolicy("streamingPolicy", StreamingPolicyArgs.builder()        
            .accountName("contosomedia")
            .commonEncryptionCenc(Map.ofEntries(
                Map.entry("clearTracks", Map.of("trackSelections", Map.ofEntries(
                    Map.entry("operation", "Equal"),
                    Map.entry("property", "FourCC"),
                    Map.entry("value", "hev1")
                ))),
                Map.entry("contentKeys", Map.of("defaultKey", Map.of("label", "cencDefaultKey"))),
                Map.entry("drm", Map.ofEntries(
                    Map.entry("playReady", Map.ofEntries(
                        Map.entry("customLicenseAcquisitionUrlTemplate", "https://contoso.com/{AssetAlternativeId}/playready/{ContentKeyId}"),
                        Map.entry("playReadyCustomAttributes", "PlayReady CustomAttributes")
                    )),
                    Map.entry("widevine", Map.of("customLicenseAcquisitionUrlTemplate", "https://contoso.com/{AssetAlternativeId}/widevine/{ContentKeyId"))
                )),
                Map.entry("enabledProtocols", Map.ofEntries(
                    Map.entry("dash", true),
                    Map.entry("download", false),
                    Map.entry("hls", false),
                    Map.entry("smoothStreaming", true)
                ))
            ))
            .defaultContentKeyPolicyName("PolicyWithPlayReadyOptionAndOpenRestriction")
            .resourceGroupName("contosorg")
            .streamingPolicyName("UserCreatedSecureStreamingPolicyWithCommonEncryptionCencOnly")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const streamingPolicy = new azure_native.media.StreamingPolicy("streamingPolicy", {
    accountName: "contosomedia",
    commonEncryptionCenc: {
        clearTracks: [{
            trackSelections: [{
                operation: "Equal",
                property: "FourCC",
                value: "hev1",
            }],
        }],
        contentKeys: {
            defaultKey: {
                label: "cencDefaultKey",
            },
        },
        drm: {
            playReady: {
                customLicenseAcquisitionUrlTemplate: "https://contoso.com/{AssetAlternativeId}/playready/{ContentKeyId}",
                playReadyCustomAttributes: "PlayReady CustomAttributes",
            },
            widevine: {
                customLicenseAcquisitionUrlTemplate: "https://contoso.com/{AssetAlternativeId}/widevine/{ContentKeyId",
            },
        },
        enabledProtocols: {
            dash: true,
            download: false,
            hls: false,
            smoothStreaming: true,
        },
    },
    defaultContentKeyPolicyName: "PolicyWithPlayReadyOptionAndOpenRestriction",
    resourceGroupName: "contosorg",
    streamingPolicyName: "UserCreatedSecureStreamingPolicyWithCommonEncryptionCencOnly",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

streaming_policy = azure_native.media.StreamingPolicy("streamingPolicy",
    account_name="contosomedia",
    common_encryption_cenc=azure_native.media.CommonEncryptionCencResponseArgs(
        clear_tracks=[{
            "trackSelections": [azure_native.media.TrackPropertyConditionArgs(
                operation="Equal",
                property="FourCC",
                value="hev1",
            )],
        }],
        content_keys={
            "defaultKey": azure_native.media.DefaultKeyArgs(
                label="cencDefaultKey",
            ),
        },
        drm={
            "playReady": azure_native.media.StreamingPolicyPlayReadyConfigurationArgs(
                custom_license_acquisition_url_template="https://contoso.com/{AssetAlternativeId}/playready/{ContentKeyId}",
                play_ready_custom_attributes="PlayReady CustomAttributes",
            ),
            "widevine": azure_native.media.StreamingPolicyWidevineConfigurationArgs(
                custom_license_acquisition_url_template="https://contoso.com/{AssetAlternativeId}/widevine/{ContentKeyId",
            ),
        },
        enabled_protocols=azure_native.media.EnabledProtocolsArgs(
            dash=True,
            download=False,
            hls=False,
            smooth_streaming=True,
        ),
    ),
    default_content_key_policy_name="PolicyWithPlayReadyOptionAndOpenRestriction",
    resource_group_name="contosorg",
    streaming_policy_name="UserCreatedSecureStreamingPolicyWithCommonEncryptionCencOnly")

```

```yaml
resources:
  streamingPolicy:
    type: azure-native:media:StreamingPolicy
    properties:
      accountName: contosomedia
      commonEncryptionCenc:
        clearTracks:
          - trackSelections:
              - operation: Equal
                property: FourCC
                value: hev1
        contentKeys:
          defaultKey:
            label: cencDefaultKey
        drm:
          playReady:
            customLicenseAcquisitionUrlTemplate: https://contoso.com/{AssetAlternativeId}/playready/{ContentKeyId}
            playReadyCustomAttributes: PlayReady CustomAttributes
          widevine:
            customLicenseAcquisitionUrlTemplate: https://contoso.com/{AssetAlternativeId}/widevine/{ContentKeyId
        enabledProtocols:
          dash: true
          download: false
          hls: false
          smoothStreaming: true
      defaultContentKeyPolicyName: PolicyWithPlayReadyOptionAndOpenRestriction
      resourceGroupName: contosorg
      streamingPolicyName: UserCreatedSecureStreamingPolicyWithCommonEncryptionCencOnly

```

{{% /example %}}
{{% example %}}
### Creates a Streaming Policy with envelopeEncryption only
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var streamingPolicy = new AzureNative.Media.StreamingPolicy("streamingPolicy", new()
    {
        AccountName = "contosomedia",
        DefaultContentKeyPolicyName = "PolicyWithClearKeyOptionAndTokenRestriction",
        EnvelopeEncryption = new AzureNative.Media.Inputs.EnvelopeEncryptionArgs
        {
            ContentKeys = new AzureNative.Media.Inputs.StreamingPolicyContentKeysArgs
            {
                DefaultKey = new AzureNative.Media.Inputs.DefaultKeyArgs
                {
                    Label = "aesDefaultKey",
                },
            },
            CustomKeyAcquisitionUrlTemplate = "https://contoso.com/{AssetAlternativeId}/envelope/{ContentKeyId}",
            EnabledProtocols = new AzureNative.Media.Inputs.EnabledProtocolsArgs
            {
                Dash = true,
                Download = false,
                Hls = true,
                SmoothStreaming = true,
            },
        },
        ResourceGroupName = "contosorg",
        StreamingPolicyName = "UserCreatedSecureStreamingPolicyWithEnvelopeEncryptionOnly",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.media.StreamingPolicy;
import com.pulumi.azurenative.media.StreamingPolicyArgs;
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
        var streamingPolicy = new StreamingPolicy("streamingPolicy", StreamingPolicyArgs.builder()        
            .accountName("contosomedia")
            .defaultContentKeyPolicyName("PolicyWithClearKeyOptionAndTokenRestriction")
            .envelopeEncryption(Map.ofEntries(
                Map.entry("contentKeys", Map.of("defaultKey", Map.of("label", "aesDefaultKey"))),
                Map.entry("customKeyAcquisitionUrlTemplate", "https://contoso.com/{AssetAlternativeId}/envelope/{ContentKeyId}"),
                Map.entry("enabledProtocols", Map.ofEntries(
                    Map.entry("dash", true),
                    Map.entry("download", false),
                    Map.entry("hls", true),
                    Map.entry("smoothStreaming", true)
                ))
            ))
            .resourceGroupName("contosorg")
            .streamingPolicyName("UserCreatedSecureStreamingPolicyWithEnvelopeEncryptionOnly")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const streamingPolicy = new azure_native.media.StreamingPolicy("streamingPolicy", {
    accountName: "contosomedia",
    defaultContentKeyPolicyName: "PolicyWithClearKeyOptionAndTokenRestriction",
    envelopeEncryption: {
        contentKeys: {
            defaultKey: {
                label: "aesDefaultKey",
            },
        },
        customKeyAcquisitionUrlTemplate: "https://contoso.com/{AssetAlternativeId}/envelope/{ContentKeyId}",
        enabledProtocols: {
            dash: true,
            download: false,
            hls: true,
            smoothStreaming: true,
        },
    },
    resourceGroupName: "contosorg",
    streamingPolicyName: "UserCreatedSecureStreamingPolicyWithEnvelopeEncryptionOnly",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

streaming_policy = azure_native.media.StreamingPolicy("streamingPolicy",
    account_name="contosomedia",
    default_content_key_policy_name="PolicyWithClearKeyOptionAndTokenRestriction",
    envelope_encryption=azure_native.media.EnvelopeEncryptionResponseArgs(
        content_keys={
            "defaultKey": azure_native.media.DefaultKeyArgs(
                label="aesDefaultKey",
            ),
        },
        custom_key_acquisition_url_template="https://contoso.com/{AssetAlternativeId}/envelope/{ContentKeyId}",
        enabled_protocols=azure_native.media.EnabledProtocolsArgs(
            dash=True,
            download=False,
            hls=True,
            smooth_streaming=True,
        ),
    ),
    resource_group_name="contosorg",
    streaming_policy_name="UserCreatedSecureStreamingPolicyWithEnvelopeEncryptionOnly")

```

```yaml
resources:
  streamingPolicy:
    type: azure-native:media:StreamingPolicy
    properties:
      accountName: contosomedia
      defaultContentKeyPolicyName: PolicyWithClearKeyOptionAndTokenRestriction
      envelopeEncryption:
        contentKeys:
          defaultKey:
            label: aesDefaultKey
        customKeyAcquisitionUrlTemplate: https://contoso.com/{AssetAlternativeId}/envelope/{ContentKeyId}
        enabledProtocols:
          dash: true
          download: false
          hls: true
          smoothStreaming: true
      resourceGroupName: contosorg
      streamingPolicyName: UserCreatedSecureStreamingPolicyWithEnvelopeEncryptionOnly

```

{{% /example %}}
{{% example %}}
### Creates a Streaming Policy with secure streaming
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var streamingPolicy = new AzureNative.Media.StreamingPolicy("streamingPolicy", new()
    {
        AccountName = "contosomedia",
        CommonEncryptionCbcs = new AzureNative.Media.Inputs.CommonEncryptionCbcsArgs
        {
            ContentKeys = new AzureNative.Media.Inputs.StreamingPolicyContentKeysArgs
            {
                DefaultKey = new AzureNative.Media.Inputs.DefaultKeyArgs
                {
                    Label = "cbcsDefaultKey",
                },
            },
            Drm = new AzureNative.Media.Inputs.CbcsDrmConfigurationArgs
            {
                FairPlay = new AzureNative.Media.Inputs.StreamingPolicyFairPlayConfigurationArgs
                {
                    AllowPersistentLicense = true,
                    CustomLicenseAcquisitionUrlTemplate = "https://contoso.com/{AssetAlternativeId}/fairplay/{ContentKeyId}",
                },
            },
            EnabledProtocols = new AzureNative.Media.Inputs.EnabledProtocolsArgs
            {
                Dash = false,
                Download = false,
                Hls = true,
                SmoothStreaming = false,
            },
        },
        CommonEncryptionCenc = new AzureNative.Media.Inputs.CommonEncryptionCencArgs
        {
            ClearTracks = new[]
            {
                new AzureNative.Media.Inputs.TrackSelectionArgs
                {
                    TrackSelections = new[]
                    {
                        new AzureNative.Media.Inputs.TrackPropertyConditionArgs
                        {
                            Operation = "Equal",
                            Property = "FourCC",
                            Value = "hev1",
                        },
                    },
                },
            },
            ContentKeys = new AzureNative.Media.Inputs.StreamingPolicyContentKeysArgs
            {
                DefaultKey = new AzureNative.Media.Inputs.DefaultKeyArgs
                {
                    Label = "cencDefaultKey",
                },
            },
            Drm = new AzureNative.Media.Inputs.CencDrmConfigurationArgs
            {
                PlayReady = new AzureNative.Media.Inputs.StreamingPolicyPlayReadyConfigurationArgs
                {
                    CustomLicenseAcquisitionUrlTemplate = "https://contoso.com/{AssetAlternativeId}/playready/{ContentKeyId}",
                    PlayReadyCustomAttributes = "PlayReady CustomAttributes",
                },
                Widevine = new AzureNative.Media.Inputs.StreamingPolicyWidevineConfigurationArgs
                {
                    CustomLicenseAcquisitionUrlTemplate = "https://contoso.com/{AssetAlternativeId}/widevine/{ContentKeyId",
                },
            },
            EnabledProtocols = new AzureNative.Media.Inputs.EnabledProtocolsArgs
            {
                Dash = true,
                Download = false,
                Hls = false,
                SmoothStreaming = true,
            },
        },
        DefaultContentKeyPolicyName = "PolicyWithMultipleOptions",
        EnvelopeEncryption = new AzureNative.Media.Inputs.EnvelopeEncryptionArgs
        {
            ContentKeys = new AzureNative.Media.Inputs.StreamingPolicyContentKeysArgs
            {
                DefaultKey = new AzureNative.Media.Inputs.DefaultKeyArgs
                {
                    Label = "aesDefaultKey",
                },
            },
            CustomKeyAcquisitionUrlTemplate = "https://contoso.com/{AssetAlternativeId}/envelope/{ContentKeyId}",
            EnabledProtocols = new AzureNative.Media.Inputs.EnabledProtocolsArgs
            {
                Dash = true,
                Download = false,
                Hls = true,
                SmoothStreaming = true,
            },
        },
        ResourceGroupName = "contosorg",
        StreamingPolicyName = "UserCreatedSecureStreamingPolicy",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.media.StreamingPolicy;
import com.pulumi.azurenative.media.StreamingPolicyArgs;
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
        var streamingPolicy = new StreamingPolicy("streamingPolicy", StreamingPolicyArgs.builder()        
            .accountName("contosomedia")
            .commonEncryptionCbcs(Map.ofEntries(
                Map.entry("contentKeys", Map.of("defaultKey", Map.of("label", "cbcsDefaultKey"))),
                Map.entry("drm", Map.of("fairPlay", Map.ofEntries(
                    Map.entry("allowPersistentLicense", true),
                    Map.entry("customLicenseAcquisitionUrlTemplate", "https://contoso.com/{AssetAlternativeId}/fairplay/{ContentKeyId}")
                ))),
                Map.entry("enabledProtocols", Map.ofEntries(
                    Map.entry("dash", false),
                    Map.entry("download", false),
                    Map.entry("hls", true),
                    Map.entry("smoothStreaming", false)
                ))
            ))
            .commonEncryptionCenc(Map.ofEntries(
                Map.entry("clearTracks", Map.of("trackSelections", Map.ofEntries(
                    Map.entry("operation", "Equal"),
                    Map.entry("property", "FourCC"),
                    Map.entry("value", "hev1")
                ))),
                Map.entry("contentKeys", Map.of("defaultKey", Map.of("label", "cencDefaultKey"))),
                Map.entry("drm", Map.ofEntries(
                    Map.entry("playReady", Map.ofEntries(
                        Map.entry("customLicenseAcquisitionUrlTemplate", "https://contoso.com/{AssetAlternativeId}/playready/{ContentKeyId}"),
                        Map.entry("playReadyCustomAttributes", "PlayReady CustomAttributes")
                    )),
                    Map.entry("widevine", Map.of("customLicenseAcquisitionUrlTemplate", "https://contoso.com/{AssetAlternativeId}/widevine/{ContentKeyId"))
                )),
                Map.entry("enabledProtocols", Map.ofEntries(
                    Map.entry("dash", true),
                    Map.entry("download", false),
                    Map.entry("hls", false),
                    Map.entry("smoothStreaming", true)
                ))
            ))
            .defaultContentKeyPolicyName("PolicyWithMultipleOptions")
            .envelopeEncryption(Map.ofEntries(
                Map.entry("contentKeys", Map.of("defaultKey", Map.of("label", "aesDefaultKey"))),
                Map.entry("customKeyAcquisitionUrlTemplate", "https://contoso.com/{AssetAlternativeId}/envelope/{ContentKeyId}"),
                Map.entry("enabledProtocols", Map.ofEntries(
                    Map.entry("dash", true),
                    Map.entry("download", false),
                    Map.entry("hls", true),
                    Map.entry("smoothStreaming", true)
                ))
            ))
            .resourceGroupName("contosorg")
            .streamingPolicyName("UserCreatedSecureStreamingPolicy")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const streamingPolicy = new azure_native.media.StreamingPolicy("streamingPolicy", {
    accountName: "contosomedia",
    commonEncryptionCbcs: {
        contentKeys: {
            defaultKey: {
                label: "cbcsDefaultKey",
            },
        },
        drm: {
            fairPlay: {
                allowPersistentLicense: true,
                customLicenseAcquisitionUrlTemplate: "https://contoso.com/{AssetAlternativeId}/fairplay/{ContentKeyId}",
            },
        },
        enabledProtocols: {
            dash: false,
            download: false,
            hls: true,
            smoothStreaming: false,
        },
    },
    commonEncryptionCenc: {
        clearTracks: [{
            trackSelections: [{
                operation: "Equal",
                property: "FourCC",
                value: "hev1",
            }],
        }],
        contentKeys: {
            defaultKey: {
                label: "cencDefaultKey",
            },
        },
        drm: {
            playReady: {
                customLicenseAcquisitionUrlTemplate: "https://contoso.com/{AssetAlternativeId}/playready/{ContentKeyId}",
                playReadyCustomAttributes: "PlayReady CustomAttributes",
            },
            widevine: {
                customLicenseAcquisitionUrlTemplate: "https://contoso.com/{AssetAlternativeId}/widevine/{ContentKeyId",
            },
        },
        enabledProtocols: {
            dash: true,
            download: false,
            hls: false,
            smoothStreaming: true,
        },
    },
    defaultContentKeyPolicyName: "PolicyWithMultipleOptions",
    envelopeEncryption: {
        contentKeys: {
            defaultKey: {
                label: "aesDefaultKey",
            },
        },
        customKeyAcquisitionUrlTemplate: "https://contoso.com/{AssetAlternativeId}/envelope/{ContentKeyId}",
        enabledProtocols: {
            dash: true,
            download: false,
            hls: true,
            smoothStreaming: true,
        },
    },
    resourceGroupName: "contosorg",
    streamingPolicyName: "UserCreatedSecureStreamingPolicy",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

streaming_policy = azure_native.media.StreamingPolicy("streamingPolicy",
    account_name="contosomedia",
    common_encryption_cbcs=azure_native.media.CommonEncryptionCbcsResponseArgs(
        content_keys={
            "defaultKey": azure_native.media.DefaultKeyArgs(
                label="cbcsDefaultKey",
            ),
        },
        drm={
            "fairPlay": azure_native.media.StreamingPolicyFairPlayConfigurationArgs(
                allow_persistent_license=True,
                custom_license_acquisition_url_template="https://contoso.com/{AssetAlternativeId}/fairplay/{ContentKeyId}",
            ),
        },
        enabled_protocols=azure_native.media.EnabledProtocolsArgs(
            dash=False,
            download=False,
            hls=True,
            smooth_streaming=False,
        ),
    ),
    common_encryption_cenc=azure_native.media.CommonEncryptionCencResponseArgs(
        clear_tracks=[{
            "trackSelections": [azure_native.media.TrackPropertyConditionArgs(
                operation="Equal",
                property="FourCC",
                value="hev1",
            )],
        }],
        content_keys={
            "defaultKey": azure_native.media.DefaultKeyArgs(
                label="cencDefaultKey",
            ),
        },
        drm={
            "playReady": azure_native.media.StreamingPolicyPlayReadyConfigurationArgs(
                custom_license_acquisition_url_template="https://contoso.com/{AssetAlternativeId}/playready/{ContentKeyId}",
                play_ready_custom_attributes="PlayReady CustomAttributes",
            ),
            "widevine": azure_native.media.StreamingPolicyWidevineConfigurationArgs(
                custom_license_acquisition_url_template="https://contoso.com/{AssetAlternativeId}/widevine/{ContentKeyId",
            ),
        },
        enabled_protocols=azure_native.media.EnabledProtocolsArgs(
            dash=True,
            download=False,
            hls=False,
            smooth_streaming=True,
        ),
    ),
    default_content_key_policy_name="PolicyWithMultipleOptions",
    envelope_encryption=azure_native.media.EnvelopeEncryptionResponseArgs(
        content_keys={
            "defaultKey": azure_native.media.DefaultKeyArgs(
                label="aesDefaultKey",
            ),
        },
        custom_key_acquisition_url_template="https://contoso.com/{AssetAlternativeId}/envelope/{ContentKeyId}",
        enabled_protocols=azure_native.media.EnabledProtocolsArgs(
            dash=True,
            download=False,
            hls=True,
            smooth_streaming=True,
        ),
    ),
    resource_group_name="contosorg",
    streaming_policy_name="UserCreatedSecureStreamingPolicy")

```

```yaml
resources:
  streamingPolicy:
    type: azure-native:media:StreamingPolicy
    properties:
      accountName: contosomedia
      commonEncryptionCbcs:
        contentKeys:
          defaultKey:
            label: cbcsDefaultKey
        drm:
          fairPlay:
            allowPersistentLicense: true
            customLicenseAcquisitionUrlTemplate: https://contoso.com/{AssetAlternativeId}/fairplay/{ContentKeyId}
        enabledProtocols:
          dash: false
          download: false
          hls: true
          smoothStreaming: false
      commonEncryptionCenc:
        clearTracks:
          - trackSelections:
              - operation: Equal
                property: FourCC
                value: hev1
        contentKeys:
          defaultKey:
            label: cencDefaultKey
        drm:
          playReady:
            customLicenseAcquisitionUrlTemplate: https://contoso.com/{AssetAlternativeId}/playready/{ContentKeyId}
            playReadyCustomAttributes: PlayReady CustomAttributes
          widevine:
            customLicenseAcquisitionUrlTemplate: https://contoso.com/{AssetAlternativeId}/widevine/{ContentKeyId
        enabledProtocols:
          dash: true
          download: false
          hls: false
          smoothStreaming: true
      defaultContentKeyPolicyName: PolicyWithMultipleOptions
      envelopeEncryption:
        contentKeys:
          defaultKey:
            label: aesDefaultKey
        customKeyAcquisitionUrlTemplate: https://contoso.com/{AssetAlternativeId}/envelope/{ContentKeyId}
        enabledProtocols:
          dash: true
          download: false
          hls: true
          smoothStreaming: true
      resourceGroupName: contosorg
      streamingPolicyName: UserCreatedSecureStreamingPolicy

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:media:StreamingPolicy UserCreatedSecureStreamingPolicy /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/contosorg/providers/Microsoft.Media/mediaservices/contosomedia/streamingPolicies/UserCreatedSecureStreamingPolicy 
```
