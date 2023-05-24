A Streaming Locator resource
API Version: 2022-08-01.
Previous API Version: 2020-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates a Streaming Locator with clear streaming
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var streamingLocator = new AzureNative.Media.StreamingLocator("streamingLocator", new()
    {
        AccountName = "contosomedia",
        AssetName = "ClimbingMountRainier",
        ResourceGroupName = "contosorg",
        StreamingLocatorName = "UserCreatedClearStreamingLocator",
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
		_, err := media.NewStreamingLocator(ctx, "streamingLocator", &media.StreamingLocatorArgs{
			AccountName:          pulumi.String("contosomedia"),
			AssetName:            pulumi.String("ClimbingMountRainier"),
			ResourceGroupName:    pulumi.String("contosorg"),
			StreamingLocatorName: pulumi.String("UserCreatedClearStreamingLocator"),
			StreamingPolicyName:  pulumi.String("clearStreamingPolicy"),
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
import com.pulumi.azurenative.media.StreamingLocator;
import com.pulumi.azurenative.media.StreamingLocatorArgs;
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
        var streamingLocator = new StreamingLocator("streamingLocator", StreamingLocatorArgs.builder()        
            .accountName("contosomedia")
            .assetName("ClimbingMountRainier")
            .resourceGroupName("contosorg")
            .streamingLocatorName("UserCreatedClearStreamingLocator")
            .streamingPolicyName("clearStreamingPolicy")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const streamingLocator = new azure_native.media.StreamingLocator("streamingLocator", {
    accountName: "contosomedia",
    assetName: "ClimbingMountRainier",
    resourceGroupName: "contosorg",
    streamingLocatorName: "UserCreatedClearStreamingLocator",
    streamingPolicyName: "clearStreamingPolicy",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

streaming_locator = azure_native.media.StreamingLocator("streamingLocator",
    account_name="contosomedia",
    asset_name="ClimbingMountRainier",
    resource_group_name="contosorg",
    streaming_locator_name="UserCreatedClearStreamingLocator",
    streaming_policy_name="clearStreamingPolicy")

```

```yaml
resources:
  streamingLocator:
    type: azure-native:media:StreamingLocator
    properties:
      accountName: contosomedia
      assetName: ClimbingMountRainier
      resourceGroupName: contosorg
      streamingLocatorName: UserCreatedClearStreamingLocator
      streamingPolicyName: clearStreamingPolicy

```

{{% /example %}}
{{% example %}}
### Creates a Streaming Locator with secure streaming
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var streamingLocator = new AzureNative.Media.StreamingLocator("streamingLocator", new()
    {
        AccountName = "contosomedia",
        AssetName = "ClimbingMountRainier",
        EndTime = "2028-12-31T23:59:59.9999999Z",
        ResourceGroupName = "contosorg",
        StartTime = "2018-03-01T00:00:00Z",
        StreamingLocatorName = "UserCreatedSecureStreamingLocator",
        StreamingPolicyName = "UserCreatedSecureStreamingPolicy",
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
		_, err := media.NewStreamingLocator(ctx, "streamingLocator", &media.StreamingLocatorArgs{
			AccountName:          pulumi.String("contosomedia"),
			AssetName:            pulumi.String("ClimbingMountRainier"),
			EndTime:              pulumi.String("2028-12-31T23:59:59.9999999Z"),
			ResourceGroupName:    pulumi.String("contosorg"),
			StartTime:            pulumi.String("2018-03-01T00:00:00Z"),
			StreamingLocatorName: pulumi.String("UserCreatedSecureStreamingLocator"),
			StreamingPolicyName:  pulumi.String("UserCreatedSecureStreamingPolicy"),
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
import com.pulumi.azurenative.media.StreamingLocator;
import com.pulumi.azurenative.media.StreamingLocatorArgs;
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
        var streamingLocator = new StreamingLocator("streamingLocator", StreamingLocatorArgs.builder()        
            .accountName("contosomedia")
            .assetName("ClimbingMountRainier")
            .endTime("2028-12-31T23:59:59.9999999Z")
            .resourceGroupName("contosorg")
            .startTime("2018-03-01T00:00:00Z")
            .streamingLocatorName("UserCreatedSecureStreamingLocator")
            .streamingPolicyName("UserCreatedSecureStreamingPolicy")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const streamingLocator = new azure_native.media.StreamingLocator("streamingLocator", {
    accountName: "contosomedia",
    assetName: "ClimbingMountRainier",
    endTime: "2028-12-31T23:59:59.9999999Z",
    resourceGroupName: "contosorg",
    startTime: "2018-03-01T00:00:00Z",
    streamingLocatorName: "UserCreatedSecureStreamingLocator",
    streamingPolicyName: "UserCreatedSecureStreamingPolicy",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

streaming_locator = azure_native.media.StreamingLocator("streamingLocator",
    account_name="contosomedia",
    asset_name="ClimbingMountRainier",
    end_time="2028-12-31T23:59:59.9999999Z",
    resource_group_name="contosorg",
    start_time="2018-03-01T00:00:00Z",
    streaming_locator_name="UserCreatedSecureStreamingLocator",
    streaming_policy_name="UserCreatedSecureStreamingPolicy")

```

```yaml
resources:
  streamingLocator:
    type: azure-native:media:StreamingLocator
    properties:
      accountName: contosomedia
      assetName: ClimbingMountRainier
      endTime: 2028-12-31T23:59:59.9999999Z
      resourceGroupName: contosorg
      startTime: 2018-03-01T00:00:00Z
      streamingLocatorName: UserCreatedSecureStreamingLocator
      streamingPolicyName: UserCreatedSecureStreamingPolicy

```

{{% /example %}}
{{% example %}}
### Creates a Streaming Locator with user defined content keys
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var streamingLocator = new AzureNative.Media.StreamingLocator("streamingLocator", new()
    {
        AccountName = "contosomedia",
        AssetName = "ClimbingMountRainier",
        ContentKeys = new[]
        {
            new AzureNative.Media.Inputs.StreamingLocatorContentKeyArgs
            {
                Id = "60000000-0000-0000-0000-000000000001",
                LabelReferenceInStreamingPolicy = "aesDefaultKey",
                Value = "1UqLohAfWsEGkULYxHjYZg==",
            },
            new AzureNative.Media.Inputs.StreamingLocatorContentKeyArgs
            {
                Id = "60000000-0000-0000-0000-000000000004",
                LabelReferenceInStreamingPolicy = "cencDefaultKey",
                Value = "4UqLohAfWsEGkULYxHjYZg==",
            },
            new AzureNative.Media.Inputs.StreamingLocatorContentKeyArgs
            {
                Id = "60000000-0000-0000-0000-000000000007",
                LabelReferenceInStreamingPolicy = "cbcsDefaultKey",
                Value = "7UqLohAfWsEGkULYxHjYZg==",
            },
        },
        ResourceGroupName = "contosorg",
        StreamingLocatorId = "90000000-0000-0000-0000-00000000000A",
        StreamingLocatorName = "UserCreatedSecureStreamingLocatorWithUserDefinedContentKeys",
        StreamingPolicyName = "secureStreamingPolicy",
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
		_, err := media.NewStreamingLocator(ctx, "streamingLocator", &media.StreamingLocatorArgs{
			AccountName: pulumi.String("contosomedia"),
			AssetName:   pulumi.String("ClimbingMountRainier"),
			ContentKeys: []media.StreamingLocatorContentKeyArgs{
				{
					Id:                              pulumi.String("60000000-0000-0000-0000-000000000001"),
					LabelReferenceInStreamingPolicy: pulumi.String("aesDefaultKey"),
					Value:                           pulumi.String("1UqLohAfWsEGkULYxHjYZg=="),
				},
				{
					Id:                              pulumi.String("60000000-0000-0000-0000-000000000004"),
					LabelReferenceInStreamingPolicy: pulumi.String("cencDefaultKey"),
					Value:                           pulumi.String("4UqLohAfWsEGkULYxHjYZg=="),
				},
				{
					Id:                              pulumi.String("60000000-0000-0000-0000-000000000007"),
					LabelReferenceInStreamingPolicy: pulumi.String("cbcsDefaultKey"),
					Value:                           pulumi.String("7UqLohAfWsEGkULYxHjYZg=="),
				},
			},
			ResourceGroupName:    pulumi.String("contosorg"),
			StreamingLocatorId:   pulumi.String("90000000-0000-0000-0000-00000000000A"),
			StreamingLocatorName: pulumi.String("UserCreatedSecureStreamingLocatorWithUserDefinedContentKeys"),
			StreamingPolicyName:  pulumi.String("secureStreamingPolicy"),
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
import com.pulumi.azurenative.media.StreamingLocator;
import com.pulumi.azurenative.media.StreamingLocatorArgs;
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
        var streamingLocator = new StreamingLocator("streamingLocator", StreamingLocatorArgs.builder()        
            .accountName("contosomedia")
            .assetName("ClimbingMountRainier")
            .contentKeys(            
                Map.ofEntries(
                    Map.entry("id", "60000000-0000-0000-0000-000000000001"),
                    Map.entry("labelReferenceInStreamingPolicy", "aesDefaultKey"),
                    Map.entry("value", "1UqLohAfWsEGkULYxHjYZg==")
                ),
                Map.ofEntries(
                    Map.entry("id", "60000000-0000-0000-0000-000000000004"),
                    Map.entry("labelReferenceInStreamingPolicy", "cencDefaultKey"),
                    Map.entry("value", "4UqLohAfWsEGkULYxHjYZg==")
                ),
                Map.ofEntries(
                    Map.entry("id", "60000000-0000-0000-0000-000000000007"),
                    Map.entry("labelReferenceInStreamingPolicy", "cbcsDefaultKey"),
                    Map.entry("value", "7UqLohAfWsEGkULYxHjYZg==")
                ))
            .resourceGroupName("contosorg")
            .streamingLocatorId("90000000-0000-0000-0000-00000000000A")
            .streamingLocatorName("UserCreatedSecureStreamingLocatorWithUserDefinedContentKeys")
            .streamingPolicyName("secureStreamingPolicy")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const streamingLocator = new azure_native.media.StreamingLocator("streamingLocator", {
    accountName: "contosomedia",
    assetName: "ClimbingMountRainier",
    contentKeys: [
        {
            id: "60000000-0000-0000-0000-000000000001",
            labelReferenceInStreamingPolicy: "aesDefaultKey",
            value: "1UqLohAfWsEGkULYxHjYZg==",
        },
        {
            id: "60000000-0000-0000-0000-000000000004",
            labelReferenceInStreamingPolicy: "cencDefaultKey",
            value: "4UqLohAfWsEGkULYxHjYZg==",
        },
        {
            id: "60000000-0000-0000-0000-000000000007",
            labelReferenceInStreamingPolicy: "cbcsDefaultKey",
            value: "7UqLohAfWsEGkULYxHjYZg==",
        },
    ],
    resourceGroupName: "contosorg",
    streamingLocatorId: "90000000-0000-0000-0000-00000000000A",
    streamingLocatorName: "UserCreatedSecureStreamingLocatorWithUserDefinedContentKeys",
    streamingPolicyName: "secureStreamingPolicy",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

streaming_locator = azure_native.media.StreamingLocator("streamingLocator",
    account_name="contosomedia",
    asset_name="ClimbingMountRainier",
    content_keys=[
        azure_native.media.StreamingLocatorContentKeyArgs(
            id="60000000-0000-0000-0000-000000000001",
            label_reference_in_streaming_policy="aesDefaultKey",
            value="1UqLohAfWsEGkULYxHjYZg==",
        ),
        azure_native.media.StreamingLocatorContentKeyArgs(
            id="60000000-0000-0000-0000-000000000004",
            label_reference_in_streaming_policy="cencDefaultKey",
            value="4UqLohAfWsEGkULYxHjYZg==",
        ),
        azure_native.media.StreamingLocatorContentKeyArgs(
            id="60000000-0000-0000-0000-000000000007",
            label_reference_in_streaming_policy="cbcsDefaultKey",
            value="7UqLohAfWsEGkULYxHjYZg==",
        ),
    ],
    resource_group_name="contosorg",
    streaming_locator_id="90000000-0000-0000-0000-00000000000A",
    streaming_locator_name="UserCreatedSecureStreamingLocatorWithUserDefinedContentKeys",
    streaming_policy_name="secureStreamingPolicy")

```

```yaml
resources:
  streamingLocator:
    type: azure-native:media:StreamingLocator
    properties:
      accountName: contosomedia
      assetName: ClimbingMountRainier
      contentKeys:
        - id: 60000000-0000-0000-0000-000000000001
          labelReferenceInStreamingPolicy: aesDefaultKey
          value: 1UqLohAfWsEGkULYxHjYZg==
        - id: 60000000-0000-0000-0000-000000000004
          labelReferenceInStreamingPolicy: cencDefaultKey
          value: 4UqLohAfWsEGkULYxHjYZg==
        - id: 60000000-0000-0000-0000-000000000007
          labelReferenceInStreamingPolicy: cbcsDefaultKey
          value: 7UqLohAfWsEGkULYxHjYZg==
      resourceGroupName: contosorg
      streamingLocatorId: 90000000-0000-0000-0000-00000000000A
      streamingLocatorName: UserCreatedSecureStreamingLocatorWithUserDefinedContentKeys
      streamingPolicyName: secureStreamingPolicy

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:media:StreamingLocator UserCreatedSecureStreamingLocatorWithUserDefinedContentKeys /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/contosorg/providers/Microsoft.Media/mediaservices/contosomedia/streamingLocators/UserCreatedSecureStreamingLocatorWithUserDefinedContentKeys 
```
