A provider instance associated with a SAP monitor.
API Version: 2020-02-07-preview.
Previous API Version: 2020-02-07-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a SAP Monitor
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var providerInstance = new AzureNative.HanaOnAzure.ProviderInstance("providerInstance", new()
    {
        Metadata = "{\"key\":\"value\"}",
        Properties = "{\"hostname\":\"10.0.0.6\",\"dbName\":\"SYSTEMDB\",\"sqlPort\":30013,\"dbUsername\":\"SYSTEM\",\"dbPassword\":\"PASSWORD\"}",
        ProviderInstanceName = "myProviderInstance",
        ResourceGroupName = "myResourceGroup",
        SapMonitorName = "mySapMonitor",
        Type = "hana",
    });

});


```

```go
package main

import (
	hanaonazure "github.com/pulumi/pulumi-azure-native-sdk/hanaonazure"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := hanaonazure.NewProviderInstance(ctx, "providerInstance", &hanaonazure.ProviderInstanceArgs{
			Metadata:             pulumi.String("{\"key\":\"value\"}"),
			Properties:           pulumi.String("{\"hostname\":\"10.0.0.6\",\"dbName\":\"SYSTEMDB\",\"sqlPort\":30013,\"dbUsername\":\"SYSTEM\",\"dbPassword\":\"PASSWORD\"}"),
			ProviderInstanceName: pulumi.String("myProviderInstance"),
			ResourceGroupName:    pulumi.String("myResourceGroup"),
			SapMonitorName:       pulumi.String("mySapMonitor"),
			Type:                 pulumi.String("hana"),
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
import com.pulumi.azurenative.hanaonazure.ProviderInstance;
import com.pulumi.azurenative.hanaonazure.ProviderInstanceArgs;
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
        var providerInstance = new ProviderInstance("providerInstance", ProviderInstanceArgs.builder()        
            .metadata("{\"key\":\"value\"}")
            .properties("{\"hostname\":\"10.0.0.6\",\"dbName\":\"SYSTEMDB\",\"sqlPort\":30013,\"dbUsername\":\"SYSTEM\",\"dbPassword\":\"PASSWORD\"}")
            .providerInstanceName("myProviderInstance")
            .resourceGroupName("myResourceGroup")
            .sapMonitorName("mySapMonitor")
            .type("hana")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const providerInstance = new azure_native.hanaonazure.ProviderInstance("providerInstance", {
    metadata: "{\"key\":\"value\"}",
    properties: "{\"hostname\":\"10.0.0.6\",\"dbName\":\"SYSTEMDB\",\"sqlPort\":30013,\"dbUsername\":\"SYSTEM\",\"dbPassword\":\"PASSWORD\"}",
    providerInstanceName: "myProviderInstance",
    resourceGroupName: "myResourceGroup",
    sapMonitorName: "mySapMonitor",
    type: "hana",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

provider_instance = azure_native.hanaonazure.ProviderInstance("providerInstance",
    metadata="{\"key\":\"value\"}",
    properties="{\"hostname\":\"10.0.0.6\",\"dbName\":\"SYSTEMDB\",\"sqlPort\":30013,\"dbUsername\":\"SYSTEM\",\"dbPassword\":\"PASSWORD\"}",
    provider_instance_name="myProviderInstance",
    resource_group_name="myResourceGroup",
    sap_monitor_name="mySapMonitor",
    type="hana")

```

```yaml
resources:
  providerInstance:
    type: azure-native:hanaonazure:ProviderInstance
    properties:
      metadata: '{"key":"value"}'
      properties: '{"hostname":"10.0.0.6","dbName":"SYSTEMDB","sqlPort":30013,"dbUsername":"SYSTEM","dbPassword":"PASSWORD"}'
      providerInstanceName: myProviderInstance
      resourceGroupName: myResourceGroup
      sapMonitorName: mySapMonitor
      type: hana

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:hanaonazure:ProviderInstance myProviderInstance /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.HanaOnAzure/sapMonitors/mySapMonitor/providerInstances/myProviderInstance 
```
