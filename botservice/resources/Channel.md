Bot channel resource definition
API Version: 2022-09-15.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Alexa Channel
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var channel = new AzureNative.BotService.Channel("channel", new()
    {
        ChannelName = "AlexaChannel",
        Location = "global",
        Properties = new AzureNative.BotService.Inputs.AlexaChannelArgs
        {
            ChannelName = "AlexaChannel",
            Properties = new AzureNative.BotService.Inputs.AlexaChannelPropertiesArgs
            {
                AlexaSkillId = "XAlexaSkillIdX",
                IsEnabled = true,
            },
        },
        ResourceGroupName = "OneResourceGroupName",
        ResourceName = "samplebotname",
    });

});


```

```go
package main

import (
	botservice "github.com/pulumi/pulumi-azure-native-sdk/botservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := botservice.NewChannel(ctx, "channel", &botservice.ChannelArgs{
			ChannelName: pulumi.String("AlexaChannel"),
			Location:    pulumi.String("global"),
			Properties: botservice.AlexaChannel{
				ChannelName: "AlexaChannel",
				Properties: botservice.AlexaChannelProperties{
					AlexaSkillId: "XAlexaSkillIdX",
					IsEnabled:    true,
				},
			},
			ResourceGroupName: pulumi.String("OneResourceGroupName"),
			ResourceName:      pulumi.String("samplebotname"),
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
import com.pulumi.azurenative.botservice.Channel;
import com.pulumi.azurenative.botservice.ChannelArgs;
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
        var channel = new Channel("channel", ChannelArgs.builder()        
            .channelName("AlexaChannel")
            .location("global")
            .properties(Map.ofEntries(
                Map.entry("channelName", "AlexaChannel"),
                Map.entry("properties", Map.ofEntries(
                    Map.entry("alexaSkillId", "XAlexaSkillIdX"),
                    Map.entry("isEnabled", true)
                ))
            ))
            .resourceGroupName("OneResourceGroupName")
            .resourceName("samplebotname")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const channel = new azure_native.botservice.Channel("channel", {
    channelName: "AlexaChannel",
    location: "global",
    properties: {
        channelName: "AlexaChannel",
        properties: {
            alexaSkillId: "XAlexaSkillIdX",
            isEnabled: true,
        },
    },
    resourceGroupName: "OneResourceGroupName",
    resourceName: "samplebotname",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

channel = azure_native.botservice.Channel("channel",
    channel_name="AlexaChannel",
    location="global",
    properties=azure_native.botservice.AlexaChannelArgs(
        channel_name="AlexaChannel",
        properties=azure_native.botservice.AlexaChannelPropertiesArgs(
            alexa_skill_id="XAlexaSkillIdX",
            is_enabled=True,
        ),
    ),
    resource_group_name="OneResourceGroupName",
    resource_name_="samplebotname")

```

```yaml
resources:
  channel:
    type: azure-native:botservice:Channel
    properties:
      channelName: AlexaChannel
      location: global
      properties:
        channelName: AlexaChannel
        properties:
          alexaSkillId: XAlexaSkillIdX
          isEnabled: true
      resourceGroupName: OneResourceGroupName
      resourceName: samplebotname

```

{{% /example %}}
{{% example %}}
### Create Channel
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var channel = new AzureNative.BotService.Channel("channel", new()
    {
        ChannelName = "EmailChannel",
        Location = "global",
        Properties = new AzureNative.BotService.Inputs.EmailChannelArgs
        {
            ChannelName = "EmailChannel",
            Properties = new AzureNative.BotService.Inputs.EmailChannelPropertiesArgs
            {
                EmailAddress = "a@b.com",
                IsEnabled = true,
                Password = "pwd",
            },
        },
        ResourceGroupName = "OneResourceGroupName",
        ResourceName = "samplebotname",
    });

});


```

```go
package main

import (
	botservice "github.com/pulumi/pulumi-azure-native-sdk/botservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := botservice.NewChannel(ctx, "channel", &botservice.ChannelArgs{
			ChannelName: pulumi.String("EmailChannel"),
			Location:    pulumi.String("global"),
			Properties: botservice.EmailChannel{
				ChannelName: "EmailChannel",
				Properties: botservice.EmailChannelProperties{
					EmailAddress: "a@b.com",
					IsEnabled:    true,
					Password:     "pwd",
				},
			},
			ResourceGroupName: pulumi.String("OneResourceGroupName"),
			ResourceName:      pulumi.String("samplebotname"),
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
import com.pulumi.azurenative.botservice.Channel;
import com.pulumi.azurenative.botservice.ChannelArgs;
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
        var channel = new Channel("channel", ChannelArgs.builder()        
            .channelName("EmailChannel")
            .location("global")
            .properties(Map.ofEntries(
                Map.entry("channelName", "EmailChannel"),
                Map.entry("properties", Map.ofEntries(
                    Map.entry("emailAddress", "a@b.com"),
                    Map.entry("isEnabled", true),
                    Map.entry("password", "pwd")
                ))
            ))
            .resourceGroupName("OneResourceGroupName")
            .resourceName("samplebotname")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const channel = new azure_native.botservice.Channel("channel", {
    channelName: "EmailChannel",
    location: "global",
    properties: {
        channelName: "EmailChannel",
        properties: {
            emailAddress: "a@b.com",
            isEnabled: true,
            password: "pwd",
        },
    },
    resourceGroupName: "OneResourceGroupName",
    resourceName: "samplebotname",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

channel = azure_native.botservice.Channel("channel",
    channel_name="EmailChannel",
    location="global",
    properties=azure_native.botservice.EmailChannelArgs(
        channel_name="EmailChannel",
        properties=azure_native.botservice.EmailChannelPropertiesArgs(
            email_address="a@b.com",
            is_enabled=True,
            password="pwd",
        ),
    ),
    resource_group_name="OneResourceGroupName",
    resource_name_="samplebotname")

```

```yaml
resources:
  channel:
    type: azure-native:botservice:Channel
    properties:
      channelName: EmailChannel
      location: global
      properties:
        channelName: EmailChannel
        properties:
          emailAddress: a@b.com
          isEnabled: true
          password: pwd
      resourceGroupName: OneResourceGroupName
      resourceName: samplebotname

```

{{% /example %}}
{{% example %}}
### Create DirectLine Speech Channel
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var channel = new AzureNative.BotService.Channel("channel", new()
    {
        ChannelName = "DirectLineSpeechChannel",
        Location = "global",
        Properties = new AzureNative.BotService.Inputs.DirectLineSpeechChannelArgs
        {
            ChannelName = "DirectLineSpeechChannel",
            Properties = new AzureNative.BotService.Inputs.DirectLineSpeechChannelPropertiesArgs
            {
                CognitiveServiceRegion = "XcognitiveServiceRegionX",
                CognitiveServiceSubscriptionKey = "XcognitiveServiceSubscriptionKeyX",
                IsEnabled = true,
            },
        },
        ResourceGroupName = "OneResourceGroupName",
        ResourceName = "samplebotname",
    });

});


```

```go
package main

import (
	botservice "github.com/pulumi/pulumi-azure-native-sdk/botservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := botservice.NewChannel(ctx, "channel", &botservice.ChannelArgs{
			ChannelName: pulumi.String("DirectLineSpeechChannel"),
			Location:    pulumi.String("global"),
			Properties: botservice.DirectLineSpeechChannel{
				ChannelName: "DirectLineSpeechChannel",
				Properties: botservice.DirectLineSpeechChannelProperties{
					CognitiveServiceRegion:          "XcognitiveServiceRegionX",
					CognitiveServiceSubscriptionKey: "XcognitiveServiceSubscriptionKeyX",
					IsEnabled:                       true,
				},
			},
			ResourceGroupName: pulumi.String("OneResourceGroupName"),
			ResourceName:      pulumi.String("samplebotname"),
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
import com.pulumi.azurenative.botservice.Channel;
import com.pulumi.azurenative.botservice.ChannelArgs;
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
        var channel = new Channel("channel", ChannelArgs.builder()        
            .channelName("DirectLineSpeechChannel")
            .location("global")
            .properties(Map.ofEntries(
                Map.entry("channelName", "DirectLineSpeechChannel"),
                Map.entry("properties", Map.ofEntries(
                    Map.entry("cognitiveServiceRegion", "XcognitiveServiceRegionX"),
                    Map.entry("cognitiveServiceSubscriptionKey", "XcognitiveServiceSubscriptionKeyX"),
                    Map.entry("isEnabled", true)
                ))
            ))
            .resourceGroupName("OneResourceGroupName")
            .resourceName("samplebotname")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const channel = new azure_native.botservice.Channel("channel", {
    channelName: "DirectLineSpeechChannel",
    location: "global",
    properties: {
        channelName: "DirectLineSpeechChannel",
        properties: {
            cognitiveServiceRegion: "XcognitiveServiceRegionX",
            cognitiveServiceSubscriptionKey: "XcognitiveServiceSubscriptionKeyX",
            isEnabled: true,
        },
    },
    resourceGroupName: "OneResourceGroupName",
    resourceName: "samplebotname",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

channel = azure_native.botservice.Channel("channel",
    channel_name="DirectLineSpeechChannel",
    location="global",
    properties=azure_native.botservice.DirectLineSpeechChannelArgs(
        channel_name="DirectLineSpeechChannel",
        properties=azure_native.botservice.DirectLineSpeechChannelPropertiesArgs(
            cognitive_service_region="XcognitiveServiceRegionX",
            cognitive_service_subscription_key="XcognitiveServiceSubscriptionKeyX",
            is_enabled=True,
        ),
    ),
    resource_group_name="OneResourceGroupName",
    resource_name_="samplebotname")

```

```yaml
resources:
  channel:
    type: azure-native:botservice:Channel
    properties:
      channelName: DirectLineSpeechChannel
      location: global
      properties:
        channelName: DirectLineSpeechChannel
        properties:
          cognitiveServiceRegion: XcognitiveServiceRegionX
          cognitiveServiceSubscriptionKey: XcognitiveServiceSubscriptionKeyX
          isEnabled: true
      resourceGroupName: OneResourceGroupName
      resourceName: samplebotname

```

{{% /example %}}
{{% example %}}
### Create Email Channel
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var channel = new AzureNative.BotService.Channel("channel", new()
    {
        ChannelName = "EmailChannel",
        Location = "global",
        Properties = new AzureNative.BotService.Inputs.EmailChannelArgs
        {
            ChannelName = "EmailChannel",
            Properties = new AzureNative.BotService.Inputs.EmailChannelPropertiesArgs
            {
                AuthMethod = 1,
                EmailAddress = "a@b.com",
                IsEnabled = true,
                MagicCode = "000000",
            },
        },
        ResourceGroupName = "OneResourceGroupName",
        ResourceName = "samplebotname",
    });

});


```

```go
package main

import (
	botservice "github.com/pulumi/pulumi-azure-native-sdk/botservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := botservice.NewChannel(ctx, "channel", &botservice.ChannelArgs{
			ChannelName: pulumi.String("EmailChannel"),
			Location:    pulumi.String("global"),
			Properties: botservice.EmailChannel{
				ChannelName: "EmailChannel",
				Properties: botservice.EmailChannelProperties{
					AuthMethod:   1,
					EmailAddress: "a@b.com",
					IsEnabled:    true,
					MagicCode:    "000000",
				},
			},
			ResourceGroupName: pulumi.String("OneResourceGroupName"),
			ResourceName:      pulumi.String("samplebotname"),
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
import com.pulumi.azurenative.botservice.Channel;
import com.pulumi.azurenative.botservice.ChannelArgs;
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
        var channel = new Channel("channel", ChannelArgs.builder()        
            .channelName("EmailChannel")
            .location("global")
            .properties(Map.ofEntries(
                Map.entry("channelName", "EmailChannel"),
                Map.entry("properties", Map.ofEntries(
                    Map.entry("authMethod", 1),
                    Map.entry("emailAddress", "a@b.com"),
                    Map.entry("isEnabled", true),
                    Map.entry("magicCode", "000000")
                ))
            ))
            .resourceGroupName("OneResourceGroupName")
            .resourceName("samplebotname")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const channel = new azure_native.botservice.Channel("channel", {
    channelName: "EmailChannel",
    location: "global",
    properties: {
        channelName: "EmailChannel",
        properties: {
            authMethod: 1,
            emailAddress: "a@b.com",
            isEnabled: true,
            magicCode: "000000",
        },
    },
    resourceGroupName: "OneResourceGroupName",
    resourceName: "samplebotname",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

channel = azure_native.botservice.Channel("channel",
    channel_name="EmailChannel",
    location="global",
    properties=azure_native.botservice.EmailChannelArgs(
        channel_name="EmailChannel",
        properties=azure_native.botservice.EmailChannelPropertiesArgs(
            auth_method=1,
            email_address="a@b.com",
            is_enabled=True,
            magic_code="000000",
        ),
    ),
    resource_group_name="OneResourceGroupName",
    resource_name_="samplebotname")

```

```yaml
resources:
  channel:
    type: azure-native:botservice:Channel
    properties:
      channelName: EmailChannel
      location: global
      properties:
        channelName: EmailChannel
        properties:
          authMethod: 1
          emailAddress: a@b.com
          isEnabled: true
          magicCode: '000000'
      resourceGroupName: OneResourceGroupName
      resourceName: samplebotname

```

{{% /example %}}
{{% example %}}
### Create Line Channel
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var channel = new AzureNative.BotService.Channel("channel", new()
    {
        ChannelName = "LineChannel",
        Location = "global",
        Properties = new AzureNative.BotService.Inputs.LineChannelArgs
        {
            ChannelName = "LineChannel",
            Properties = new AzureNative.BotService.Inputs.LineChannelPropertiesArgs
            {
                LineRegistrations = new[]
                {
                    new AzureNative.BotService.Inputs.LineRegistrationArgs
                    {
                        ChannelAccessToken = "channelAccessToken",
                        ChannelSecret = "channelSecret",
                    },
                },
            },
        },
        ResourceGroupName = "OneResourceGroupName",
        ResourceName = "samplebotname",
    });

});


```

```go
package main

import (
	botservice "github.com/pulumi/pulumi-azure-native-sdk/botservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := botservice.NewChannel(ctx, "channel", &botservice.ChannelArgs{
			ChannelName: pulumi.String("LineChannel"),
			Location:    pulumi.String("global"),
			Properties: botservice.LineChannel{
				ChannelName: "LineChannel",
				Properties: botservice.LineChannelProperties{
					LineRegistrations: []botservice.LineRegistration{
						{
							ChannelAccessToken: "channelAccessToken",
							ChannelSecret:      "channelSecret",
						},
					},
				},
			},
			ResourceGroupName: pulumi.String("OneResourceGroupName"),
			ResourceName:      pulumi.String("samplebotname"),
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
import com.pulumi.azurenative.botservice.Channel;
import com.pulumi.azurenative.botservice.ChannelArgs;
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
        var channel = new Channel("channel", ChannelArgs.builder()        
            .channelName("LineChannel")
            .location("global")
            .properties(Map.ofEntries(
                Map.entry("channelName", "LineChannel"),
                Map.entry("properties", Map.of("lineRegistrations", Map.ofEntries(
                    Map.entry("channelAccessToken", "channelAccessToken"),
                    Map.entry("channelSecret", "channelSecret")
                )))
            ))
            .resourceGroupName("OneResourceGroupName")
            .resourceName("samplebotname")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const channel = new azure_native.botservice.Channel("channel", {
    channelName: "LineChannel",
    location: "global",
    properties: {
        channelName: "LineChannel",
        properties: {
            lineRegistrations: [{
                channelAccessToken: "channelAccessToken",
                channelSecret: "channelSecret",
            }],
        },
    },
    resourceGroupName: "OneResourceGroupName",
    resourceName: "samplebotname",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

channel = azure_native.botservice.Channel("channel",
    channel_name="LineChannel",
    location="global",
    properties=azure_native.botservice.LineChannelArgs(
        channel_name="LineChannel",
        properties=azure_native.botservice.LineChannelPropertiesArgs(
            line_registrations=[azure_native.botservice.LineRegistrationArgs(
                channel_access_token="channelAccessToken",
                channel_secret="channelSecret",
            )],
        ),
    ),
    resource_group_name="OneResourceGroupName",
    resource_name_="samplebotname")

```

```yaml
resources:
  channel:
    type: azure-native:botservice:Channel
    properties:
      channelName: LineChannel
      location: global
      properties:
        channelName: LineChannel
        properties:
          lineRegistrations:
            - channelAccessToken: channelAccessToken
              channelSecret: channelSecret
      resourceGroupName: OneResourceGroupName
      resourceName: samplebotname

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:botservice:Channel myresource1 /subscriptions/subscription-id/providers/Microsoft.BotService/botServices 
```
