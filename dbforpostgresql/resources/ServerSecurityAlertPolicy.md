A server security alert policy.
API Version: 2017-12-01.
Previous API Version: 2017-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

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
    var serverSecurityAlertPolicy = new AzureNative.DBforPostgreSQL.ServerSecurityAlertPolicy("serverSecurityAlertPolicy", new()
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
        State = AzureNative.DBforPostgreSQL.ServerSecurityAlertPolicyState.Enabled,
        StorageAccountAccessKey = "sdlfkjabc+sdlfkjsdlkfsjdfLDKFTERLKFDFKLjsdfksjdflsdkfD2342309432849328476458/3RSD==",
        StorageEndpoint = "https://mystorage.blob.core.windows.net",
    });

});


```

```go
package main

import (
	dbforpostgresql "github.com/pulumi/pulumi-azure-native-sdk/dbforpostgresql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := dbforpostgresql.NewServerSecurityAlertPolicy(ctx, "serverSecurityAlertPolicy", &dbforpostgresql.ServerSecurityAlertPolicyArgs{
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
			State:                   dbforpostgresql.ServerSecurityAlertPolicyStateEnabled,
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
import com.pulumi.azurenative.dbforpostgresql.ServerSecurityAlertPolicy;
import com.pulumi.azurenative.dbforpostgresql.ServerSecurityAlertPolicyArgs;
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

const serverSecurityAlertPolicy = new azure_native.dbforpostgresql.ServerSecurityAlertPolicy("serverSecurityAlertPolicy", {
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
    state: azure_native.dbforpostgresql.ServerSecurityAlertPolicyState.Enabled,
    storageAccountAccessKey: "sdlfkjabc+sdlfkjsdlkfsjdfLDKFTERLKFDFKLjsdfksjdflsdkfD2342309432849328476458/3RSD==",
    storageEndpoint: "https://mystorage.blob.core.windows.net",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

server_security_alert_policy = azure_native.dbforpostgresql.ServerSecurityAlertPolicy("serverSecurityAlertPolicy",
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
    state=azure_native.dbforpostgresql.ServerSecurityAlertPolicyState.ENABLED,
    storage_account_access_key="sdlfkjabc+sdlfkjsdlkfsjdfLDKFTERLKFDFKLjsdfksjdflsdkfD2342309432849328476458/3RSD==",
    storage_endpoint="https://mystorage.blob.core.windows.net")

```

```yaml
resources:
  serverSecurityAlertPolicy:
    type: azure-native:dbforpostgresql:ServerSecurityAlertPolicy
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
    var serverSecurityAlertPolicy = new AzureNative.DBforPostgreSQL.ServerSecurityAlertPolicy("serverSecurityAlertPolicy", new()
    {
        EmailAccountAdmins = true,
        ResourceGroupName = "securityalert-4799",
        SecurityAlertPolicyName = "Default",
        ServerName = "securityalert-6440",
        State = AzureNative.DBforPostgreSQL.ServerSecurityAlertPolicyState.Disabled,
    });

});


```

```go
package main

import (
	dbforpostgresql "github.com/pulumi/pulumi-azure-native-sdk/dbforpostgresql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := dbforpostgresql.NewServerSecurityAlertPolicy(ctx, "serverSecurityAlertPolicy", &dbforpostgresql.ServerSecurityAlertPolicyArgs{
			EmailAccountAdmins:      pulumi.Bool(true),
			ResourceGroupName:       pulumi.String("securityalert-4799"),
			SecurityAlertPolicyName: pulumi.String("Default"),
			ServerName:              pulumi.String("securityalert-6440"),
			State:                   dbforpostgresql.ServerSecurityAlertPolicyStateDisabled,
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
import com.pulumi.azurenative.dbforpostgresql.ServerSecurityAlertPolicy;
import com.pulumi.azurenative.dbforpostgresql.ServerSecurityAlertPolicyArgs;
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
            .emailAccountAdmins(true)
            .resourceGroupName("securityalert-4799")
            .securityAlertPolicyName("Default")
            .serverName("securityalert-6440")
            .state("Disabled")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const serverSecurityAlertPolicy = new azure_native.dbforpostgresql.ServerSecurityAlertPolicy("serverSecurityAlertPolicy", {
    emailAccountAdmins: true,
    resourceGroupName: "securityalert-4799",
    securityAlertPolicyName: "Default",
    serverName: "securityalert-6440",
    state: azure_native.dbforpostgresql.ServerSecurityAlertPolicyState.Disabled,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

server_security_alert_policy = azure_native.dbforpostgresql.ServerSecurityAlertPolicy("serverSecurityAlertPolicy",
    email_account_admins=True,
    resource_group_name="securityalert-4799",
    security_alert_policy_name="Default",
    server_name="securityalert-6440",
    state=azure_native.dbforpostgresql.ServerSecurityAlertPolicyState.DISABLED)

```

```yaml
resources:
  serverSecurityAlertPolicy:
    type: azure-native:dbforpostgresql:ServerSecurityAlertPolicy
    properties:
      emailAccountAdmins: true
      resourceGroupName: securityalert-4799
      securityAlertPolicyName: Default
      serverName: securityalert-6440
      state: Disabled

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:dbforpostgresql:ServerSecurityAlertPolicy Default /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/securityalert-4799/providers/Microsoft.DBforPostgreSQL/servers/securityalert-6440/securityAlertPolicies/default 
```
