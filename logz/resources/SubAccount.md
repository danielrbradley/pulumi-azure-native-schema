
API Version: 2022-01-01-preview.
Previous API Version: 2020-10-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### subAccount_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var subAccount = new AzureNative.Logz.SubAccount("subAccount", new()
    {
        MonitorName = "myMonitor",
        ResourceGroupName = "myResourceGroup",
        SubAccountName = "SubAccount1",
    });

});


```

```go
package main

import (
	logz "github.com/pulumi/pulumi-azure-native-sdk/logz"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := logz.NewSubAccount(ctx, "subAccount", &logz.SubAccountArgs{
			MonitorName:       pulumi.String("myMonitor"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			SubAccountName:    pulumi.String("SubAccount1"),
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
import com.pulumi.azurenative.logz.SubAccount;
import com.pulumi.azurenative.logz.SubAccountArgs;
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
        var subAccount = new SubAccount("subAccount", SubAccountArgs.builder()        
            .monitorName("myMonitor")
            .resourceGroupName("myResourceGroup")
            .subAccountName("SubAccount1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const subAccount = new azure_native.logz.SubAccount("subAccount", {
    monitorName: "myMonitor",
    resourceGroupName: "myResourceGroup",
    subAccountName: "SubAccount1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sub_account = azure_native.logz.SubAccount("subAccount",
    monitor_name="myMonitor",
    resource_group_name="myResourceGroup",
    sub_account_name="SubAccount1")

```

```yaml
resources:
  subAccount:
    type: azure-native:logz:SubAccount
    properties:
      monitorName: myMonitor
      resourceGroupName: myResourceGroup
      subAccountName: SubAccount1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:logz:SubAccount myMonitor /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/monitors/myMonitor/accounts/SubAccount1 
```
