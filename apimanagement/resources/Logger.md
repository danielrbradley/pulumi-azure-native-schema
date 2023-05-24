Logger details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateAILogger
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var logger = new AzureNative.ApiManagement.Logger("logger", new()
    {
        Credentials = 
        {
            { "instrumentationKey", "11................a1" },
        },
        Description = "adding a new logger",
        LoggerId = "loggerId",
        LoggerType = "applicationInsights",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
    });

});


```

```go
package main

import (
	apimanagement "github.com/pulumi/pulumi-azure-native-sdk/apimanagement"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := apimanagement.NewLogger(ctx, "logger", &apimanagement.LoggerArgs{
			Credentials: pulumi.StringMap{
				"instrumentationKey": pulumi.String("11................a1"),
			},
			Description:       pulumi.String("adding a new logger"),
			LoggerId:          pulumi.String("loggerId"),
			LoggerType:        pulumi.String("applicationInsights"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
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
import com.pulumi.azurenative.apimanagement.Logger;
import com.pulumi.azurenative.apimanagement.LoggerArgs;
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
        var logger = new Logger("logger", LoggerArgs.builder()        
            .credentials(Map.of("instrumentationKey", "11................a1"))
            .description("adding a new logger")
            .loggerId("loggerId")
            .loggerType("applicationInsights")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const logger = new azure_native.apimanagement.Logger("logger", {
    credentials: {
        instrumentationKey: "11................a1",
    },
    description: "adding a new logger",
    loggerId: "loggerId",
    loggerType: "applicationInsights",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

logger = azure_native.apimanagement.Logger("logger",
    credentials={
        "instrumentationKey": "11................a1",
    },
    description="adding a new logger",
    logger_id="loggerId",
    logger_type="applicationInsights",
    resource_group_name="rg1",
    service_name="apimService1")

```

```yaml
resources:
  logger:
    type: azure-native:apimanagement:Logger
    properties:
      credentials:
        instrumentationKey: 11................a1
      description: adding a new logger
      loggerId: loggerId
      loggerType: applicationInsights
      resourceGroupName: rg1
      serviceName: apimService1

```

{{% /example %}}
{{% example %}}
### ApiManagementCreateEHLogger
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var logger = new AzureNative.ApiManagement.Logger("logger", new()
    {
        Credentials = 
        {
            { "connectionString", "Endpoint=sb://hydraeventhub-ns.servicebus.windows.net/;SharedAccessKeyName=RootManageSharedAccessKey;SharedAccessKey=********=" },
            { "name", "hydraeventhub" },
        },
        Description = "adding a new logger",
        LoggerId = "eh1",
        LoggerType = "azureEventHub",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
    });

});


```

```go
package main

import (
	apimanagement "github.com/pulumi/pulumi-azure-native-sdk/apimanagement"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := apimanagement.NewLogger(ctx, "logger", &apimanagement.LoggerArgs{
			Credentials: pulumi.StringMap{
				"connectionString": pulumi.String("Endpoint=sb://hydraeventhub-ns.servicebus.windows.net/;SharedAccessKeyName=RootManageSharedAccessKey;SharedAccessKey=********="),
				"name":             pulumi.String("hydraeventhub"),
			},
			Description:       pulumi.String("adding a new logger"),
			LoggerId:          pulumi.String("eh1"),
			LoggerType:        pulumi.String("azureEventHub"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
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
import com.pulumi.azurenative.apimanagement.Logger;
import com.pulumi.azurenative.apimanagement.LoggerArgs;
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
        var logger = new Logger("logger", LoggerArgs.builder()        
            .credentials(Map.ofEntries(
                Map.entry("connectionString", "Endpoint=sb://hydraeventhub-ns.servicebus.windows.net/;SharedAccessKeyName=RootManageSharedAccessKey;SharedAccessKey=********="),
                Map.entry("name", "hydraeventhub")
            ))
            .description("adding a new logger")
            .loggerId("eh1")
            .loggerType("azureEventHub")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const logger = new azure_native.apimanagement.Logger("logger", {
    credentials: {
        connectionString: "Endpoint=sb://hydraeventhub-ns.servicebus.windows.net/;SharedAccessKeyName=RootManageSharedAccessKey;SharedAccessKey=********=",
        name: "hydraeventhub",
    },
    description: "adding a new logger",
    loggerId: "eh1",
    loggerType: "azureEventHub",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

logger = azure_native.apimanagement.Logger("logger",
    credentials={
        "connectionString": "Endpoint=sb://hydraeventhub-ns.servicebus.windows.net/;SharedAccessKeyName=RootManageSharedAccessKey;SharedAccessKey=********=",
        "name": "hydraeventhub",
    },
    description="adding a new logger",
    logger_id="eh1",
    logger_type="azureEventHub",
    resource_group_name="rg1",
    service_name="apimService1")

```

```yaml
resources:
  logger:
    type: azure-native:apimanagement:Logger
    properties:
      credentials:
        connectionString: Endpoint=sb://hydraeventhub-ns.servicebus.windows.net/;SharedAccessKeyName=RootManageSharedAccessKey;SharedAccessKey=********=
        name: hydraeventhub
      description: adding a new logger
      loggerId: eh1
      loggerType: azureEventHub
      resourceGroupName: rg1
      serviceName: apimService1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:Logger eh1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/loggers/eh1 
```
