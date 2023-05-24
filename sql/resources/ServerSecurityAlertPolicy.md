A server security alert policy.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Update a server's threat detection policy with all parameters
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var serverSecurityAlertPolicy = new AzureNative.Sql.ServerSecurityAlertPolicy("serverSecurityAlertPolicy", new()
    {
        DisabledAlerts = new[]
        {
            "Access_Anomaly",
            "Usage_Anomaly",
        },
        EmailAccountAdmins = true,
        EmailAddresses = new[]
        {
            "testSecurityAlert@microsoft.com",
        },
        ResourceGroupName = "securityalert-4799",
        RetentionDays = 5,
        SecurityAlertPolicyName = "Default",
        ServerName = "securityalert-6440",
        State = AzureNative.Sql.SecurityAlertsPolicyState.Enabled,
        StorageAccountAccessKey = "sdlfkjabc+sdlfkjsdlkfsjdfLDKFTERLKFDFKLjsdfksjdflsdkfD2342309432849328476458/3RSD==",
        StorageEndpoint = "https://mystorage.blob.core.windows.net",
    });

});


```

```go
package main

import (
	sql "github.com/pulumi/pulumi-azure-native-sdk/sql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := sql.NewServerSecurityAlertPolicy(ctx, "serverSecurityAlertPolicy", &sql.ServerSecurityAlertPolicyArgs{
			DisabledAlerts: pulumi.StringArray{
				pulumi.String("Access_Anomaly"),
				pulumi.String("Usage_Anomaly"),
			},
			EmailAccountAdmins: pulumi.Bool(true),
			EmailAddresses: pulumi.StringArray{
				pulumi.String("testSecurityAlert@microsoft.com"),
			},
			ResourceGroupName:       pulumi.String("securityalert-4799"),
			RetentionDays:           pulumi.Int(5),
			SecurityAlertPolicyName: pulumi.String("Default"),
			ServerName:              pulumi.String("securityalert-6440"),
			State:                   sql.SecurityAlertsPolicyStateEnabled,
			StorageAccountAccessKey: pulumi.String("sdlfkjabc+sdlfkjsdlkfsjdfLDKFTERLKFDFKLjsdfksjdflsdkfD2342309432849328476458/3RSD=="),
			StorageEndpoint:         pulumi.String("https://mystorage.blob.core.windows.net"),
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
import com.pulumi.azurenative.sql.ServerSecurityAlertPolicy;
import com.pulumi.azurenative.sql.ServerSecurityAlertPolicyArgs;
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
        var serverSecurityAlertPolicy = new ServerSecurityAlertPolicy("serverSecurityAlertPolicy", ServerSecurityAlertPolicyArgs.builder()        
            .disabledAlerts(            
                "Access_Anomaly",
                "Usage_Anomaly")
            .emailAccountAdmins(true)
            .emailAddresses("testSecurityAlert@microsoft.com")
            .resourceGroupName("securityalert-4799")
            .retentionDays(5)
            .securityAlertPolicyName("Default")
            .serverName("securityalert-6440")
            .state("Enabled")
            .storageAccountAccessKey("sdlfkjabc+sdlfkjsdlkfsjdfLDKFTERLKFDFKLjsdfksjdflsdkfD2342309432849328476458/3RSD==")
            .storageEndpoint("https://mystorage.blob.core.windows.net")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const serverSecurityAlertPolicy = new azure_native.sql.ServerSecurityAlertPolicy("serverSecurityAlertPolicy", {
    disabledAlerts: [
        "Access_Anomaly",
        "Usage_Anomaly",
    ],
    emailAccountAdmins: true,
    emailAddresses: ["testSecurityAlert@microsoft.com"],
    resourceGroupName: "securityalert-4799",
    retentionDays: 5,
    securityAlertPolicyName: "Default",
    serverName: "securityalert-6440",
    state: azure_native.sql.SecurityAlertsPolicyState.Enabled,
    storageAccountAccessKey: "sdlfkjabc+sdlfkjsdlkfsjdfLDKFTERLKFDFKLjsdfksjdflsdkfD2342309432849328476458/3RSD==",
    storageEndpoint: "https://mystorage.blob.core.windows.net",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

server_security_alert_policy = azure_native.sql.ServerSecurityAlertPolicy("serverSecurityAlertPolicy",
    disabled_alerts=[
        "Access_Anomaly",
        "Usage_Anomaly",
    ],
    email_account_admins=True,
    email_addresses=["testSecurityAlert@microsoft.com"],
    resource_group_name="securityalert-4799",
    retention_days=5,
    security_alert_policy_name="Default",
    server_name="securityalert-6440",
    state=azure_native.sql.SecurityAlertsPolicyState.ENABLED,
    storage_account_access_key="sdlfkjabc+sdlfkjsdlkfsjdfLDKFTERLKFDFKLjsdfksjdflsdkfD2342309432849328476458/3RSD==",
    storage_endpoint="https://mystorage.blob.core.windows.net")

```

```yaml
resources:
  serverSecurityAlertPolicy:
    type: azure-native:sql:ServerSecurityAlertPolicy
    properties:
      disabledAlerts:
        - Access_Anomaly
        - Usage_Anomaly
      emailAccountAdmins: true
      emailAddresses:
        - testSecurityAlert@microsoft.com
      resourceGroupName: securityalert-4799
      retentionDays: 5
      securityAlertPolicyName: Default
      serverName: securityalert-6440
      state: Enabled
      storageAccountAccessKey: sdlfkjabc+sdlfkjsdlkfsjdfLDKFTERLKFDFKLjsdfksjdflsdkfD2342309432849328476458/3RSD==
      storageEndpoint: https://mystorage.blob.core.windows.net

```

{{% /example %}}
{{% example %}}
### Update a server's threat detection policy with minimal parameters
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var serverSecurityAlertPolicy = new AzureNative.Sql.ServerSecurityAlertPolicy("serverSecurityAlertPolicy", new()
    {
        ResourceGroupName = "securityalert-4799",
        SecurityAlertPolicyName = "Default",
        ServerName = "securityalert-6440",
        State = AzureNative.Sql.SecurityAlertsPolicyState.Enabled,
    });

});


```

```go
package main

import (
	sql "github.com/pulumi/pulumi-azure-native-sdk/sql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := sql.NewServerSecurityAlertPolicy(ctx, "serverSecurityAlertPolicy", &sql.ServerSecurityAlertPolicyArgs{
			ResourceGroupName:       pulumi.String("securityalert-4799"),
			SecurityAlertPolicyName: pulumi.String("Default"),
			ServerName:              pulumi.String("securityalert-6440"),
			State:                   sql.SecurityAlertsPolicyStateEnabled,
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
import com.pulumi.azurenative.sql.ServerSecurityAlertPolicy;
import com.pulumi.azurenative.sql.ServerSecurityAlertPolicyArgs;
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
        var serverSecurityAlertPolicy = new ServerSecurityAlertPolicy("serverSecurityAlertPolicy", ServerSecurityAlertPolicyArgs.builder()        
            .resourceGroupName("securityalert-4799")
            .securityAlertPolicyName("Default")
            .serverName("securityalert-6440")
            .state("Enabled")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const serverSecurityAlertPolicy = new azure_native.sql.ServerSecurityAlertPolicy("serverSecurityAlertPolicy", {
    resourceGroupName: "securityalert-4799",
    securityAlertPolicyName: "Default",
    serverName: "securityalert-6440",
    state: azure_native.sql.SecurityAlertsPolicyState.Enabled,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

server_security_alert_policy = azure_native.sql.ServerSecurityAlertPolicy("serverSecurityAlertPolicy",
    resource_group_name="securityalert-4799",
    security_alert_policy_name="Default",
    server_name="securityalert-6440",
    state=azure_native.sql.SecurityAlertsPolicyState.ENABLED)

```

```yaml
resources:
  serverSecurityAlertPolicy:
    type: azure-native:sql:ServerSecurityAlertPolicy
    properties:
      resourceGroupName: securityalert-4799
      securityAlertPolicyName: Default
      serverName: securityalert-6440
      state: Enabled

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:ServerSecurityAlertPolicy Default /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/securityalert-4799/providers/Microsoft.Sql/servers/securityalert-6440/securityAlertPolicies/default 
```
