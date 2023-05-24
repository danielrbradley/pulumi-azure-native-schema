A profile object that contains change analysis configuration, such as notification settings, for this subscription
API Version: 2020-04-01-preview.
Previous API Version: 2020-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ConfigurationProfile_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var configurationProfile = new AzureNative.ChangeAnalysis.ConfigurationProfile("configurationProfile", new()
    {
        ProfileName = "default",
    });

});


```

```go
package main

import (
	changeanalysis "github.com/pulumi/pulumi-azure-native-sdk/changeanalysis"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := changeanalysis.NewConfigurationProfile(ctx, "configurationProfile", &changeanalysis.ConfigurationProfileArgs{
			ProfileName: pulumi.String("default"),
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
import com.pulumi.azurenative.changeanalysis.ConfigurationProfile;
import com.pulumi.azurenative.changeanalysis.ConfigurationProfileArgs;
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
        var configurationProfile = new ConfigurationProfile("configurationProfile", ConfigurationProfileArgs.builder()        
            .profileName("default")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const configurationProfile = new azure_native.changeanalysis.ConfigurationProfile("configurationProfile", {profileName: "default"});

```

```python
import pulumi
import pulumi_azure_native as azure_native

configuration_profile = azure_native.changeanalysis.ConfigurationProfile("configurationProfile", profile_name="default")

```

```yaml
resources:
  configurationProfile:
    type: azure-native:changeanalysis:ConfigurationProfile
    properties:
      profileName: default

```

{{% /example %}}
{{% example %}}
### ConfigurationProfile_CreateWithIdentity
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var configurationProfile = new AzureNative.ChangeAnalysis.ConfigurationProfile("configurationProfile", new()
    {
        ProfileName = "default",
    });

});


```

```go
package main

import (
	changeanalysis "github.com/pulumi/pulumi-azure-native-sdk/changeanalysis"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := changeanalysis.NewConfigurationProfile(ctx, "configurationProfile", &changeanalysis.ConfigurationProfileArgs{
			ProfileName: pulumi.String("default"),
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
import com.pulumi.azurenative.changeanalysis.ConfigurationProfile;
import com.pulumi.azurenative.changeanalysis.ConfigurationProfileArgs;
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
        var configurationProfile = new ConfigurationProfile("configurationProfile", ConfigurationProfileArgs.builder()        
            .profileName("default")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const configurationProfile = new azure_native.changeanalysis.ConfigurationProfile("configurationProfile", {profileName: "default"});

```

```python
import pulumi
import pulumi_azure_native as azure_native

configuration_profile = azure_native.changeanalysis.ConfigurationProfile("configurationProfile", profile_name="default")

```

```yaml
resources:
  configurationProfile:
    type: azure-native:changeanalysis:ConfigurationProfile
    properties:
      profileName: default

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:changeanalysis:ConfigurationProfile default /subscriptions/c80fb759-c965-4c6a-9110-9b2b2d038882/providers/Microsoft.ChangeAnalysis/profile/default 
```
