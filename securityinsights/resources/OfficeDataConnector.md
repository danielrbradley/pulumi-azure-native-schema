Represents office data connector.
API Version: 2023-02-01.
Previous API Version: 2020-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates or updates an Office365 data connector.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var officeDataConnector = new AzureNative.SecurityInsights.OfficeDataConnector("officeDataConnector", new()
    {
        DataConnectorId = "73e01a99-5cd7-4139-a149-9f2736ff2ab5",
        DataTypes = new AzureNative.SecurityInsights.Inputs.OfficeDataConnectorDataTypesArgs
        {
            Exchange = new AzureNative.SecurityInsights.Inputs.OfficeDataConnectorDataTypesExchangeArgs
            {
                State = "Enabled",
            },
            SharePoint = new AzureNative.SecurityInsights.Inputs.OfficeDataConnectorDataTypesSharePointArgs
            {
                State = "Enabled",
            },
            Teams = new AzureNative.SecurityInsights.Inputs.OfficeDataConnectorDataTypesTeamsArgs
            {
                State = "Enabled",
            },
        },
        Kind = "Office365",
        ResourceGroupName = "myRg",
        TenantId = "2070ecc9-b4d5-4ae4-adaa-936fa1954fa8",
        WorkspaceName = "myWorkspace",
    });

});


```

```go
package main

import (
	securityinsights "github.com/pulumi/pulumi-azure-native-sdk/securityinsights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := securityinsights.NewOfficeDataConnector(ctx, "officeDataConnector", &securityinsights.OfficeDataConnectorArgs{
			DataConnectorId: pulumi.String("73e01a99-5cd7-4139-a149-9f2736ff2ab5"),
			DataTypes: securityinsights.OfficeDataConnectorDataTypesResponse{
				Exchange: &securityinsights.OfficeDataConnectorDataTypesExchangeArgs{
					State: pulumi.String("Enabled"),
				},
				SharePoint: &securityinsights.OfficeDataConnectorDataTypesSharePointArgs{
					State: pulumi.String("Enabled"),
				},
				Teams: &securityinsights.OfficeDataConnectorDataTypesTeamsArgs{
					State: pulumi.String("Enabled"),
				},
			},
			Kind:              pulumi.String("Office365"),
			ResourceGroupName: pulumi.String("myRg"),
			TenantId:          pulumi.String("2070ecc9-b4d5-4ae4-adaa-936fa1954fa8"),
			WorkspaceName:     pulumi.String("myWorkspace"),
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
import com.pulumi.azurenative.securityinsights.OfficeDataConnector;
import com.pulumi.azurenative.securityinsights.OfficeDataConnectorArgs;
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
        var officeDataConnector = new OfficeDataConnector("officeDataConnector", OfficeDataConnectorArgs.builder()        
            .dataConnectorId("73e01a99-5cd7-4139-a149-9f2736ff2ab5")
            .dataTypes(Map.ofEntries(
                Map.entry("exchange", Map.of("state", "Enabled")),
                Map.entry("sharePoint", Map.of("state", "Enabled")),
                Map.entry("teams", Map.of("state", "Enabled"))
            ))
            .kind("Office365")
            .resourceGroupName("myRg")
            .tenantId("2070ecc9-b4d5-4ae4-adaa-936fa1954fa8")
            .workspaceName("myWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const officeDataConnector = new azure_native.securityinsights.OfficeDataConnector("officeDataConnector", {
    dataConnectorId: "73e01a99-5cd7-4139-a149-9f2736ff2ab5",
    dataTypes: {
        exchange: {
            state: "Enabled",
        },
        sharePoint: {
            state: "Enabled",
        },
        teams: {
            state: "Enabled",
        },
    },
    kind: "Office365",
    resourceGroupName: "myRg",
    tenantId: "2070ecc9-b4d5-4ae4-adaa-936fa1954fa8",
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

office_data_connector = azure_native.securityinsights.OfficeDataConnector("officeDataConnector",
    data_connector_id="73e01a99-5cd7-4139-a149-9f2736ff2ab5",
    data_types=azure_native.securityinsights.OfficeDataConnectorDataTypesResponseArgs(
        exchange=azure_native.securityinsights.OfficeDataConnectorDataTypesExchangeArgs(
            state="Enabled",
        ),
        share_point=azure_native.securityinsights.OfficeDataConnectorDataTypesSharePointArgs(
            state="Enabled",
        ),
        teams=azure_native.securityinsights.OfficeDataConnectorDataTypesTeamsArgs(
            state="Enabled",
        ),
    ),
    kind="Office365",
    resource_group_name="myRg",
    tenant_id="2070ecc9-b4d5-4ae4-adaa-936fa1954fa8",
    workspace_name="myWorkspace")

```

```yaml
resources:
  officeDataConnector:
    type: azure-native:securityinsights:OfficeDataConnector
    properties:
      dataConnectorId: 73e01a99-5cd7-4139-a149-9f2736ff2ab5
      dataTypes:
        exchange:
          state: Enabled
        sharePoint:
          state: Enabled
        teams:
          state: Enabled
      kind: Office365
      resourceGroupName: myRg
      tenantId: 2070ecc9-b4d5-4ae4-adaa-936fa1954fa8
      workspaceName: myWorkspace

```

{{% /example %}}
{{% example %}}
### Creates or updates an Threat Intelligence Platform data connector.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var officeDataConnector = new AzureNative.SecurityInsights.OfficeDataConnector("officeDataConnector", new()
    {
        DataConnectorId = "73e01a99-5cd7-4139-a149-9f2736ff2ab5",
        ResourceGroupName = "myRg",
        WorkspaceName = "myWorkspace",
    });

});


```

```go
package main

import (
	securityinsights "github.com/pulumi/pulumi-azure-native-sdk/securityinsights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := securityinsights.NewOfficeDataConnector(ctx, "officeDataConnector", &securityinsights.OfficeDataConnectorArgs{
			DataConnectorId:   pulumi.String("73e01a99-5cd7-4139-a149-9f2736ff2ab5"),
			ResourceGroupName: pulumi.String("myRg"),
			WorkspaceName:     pulumi.String("myWorkspace"),
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
import com.pulumi.azurenative.securityinsights.OfficeDataConnector;
import com.pulumi.azurenative.securityinsights.OfficeDataConnectorArgs;
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
        var officeDataConnector = new OfficeDataConnector("officeDataConnector", OfficeDataConnectorArgs.builder()        
            .dataConnectorId("73e01a99-5cd7-4139-a149-9f2736ff2ab5")
            .resourceGroupName("myRg")
            .workspaceName("myWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const officeDataConnector = new azure_native.securityinsights.OfficeDataConnector("officeDataConnector", {
    dataConnectorId: "73e01a99-5cd7-4139-a149-9f2736ff2ab5",
    resourceGroupName: "myRg",
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

office_data_connector = azure_native.securityinsights.OfficeDataConnector("officeDataConnector",
    data_connector_id="73e01a99-5cd7-4139-a149-9f2736ff2ab5",
    resource_group_name="myRg",
    workspace_name="myWorkspace")

```

```yaml
resources:
  officeDataConnector:
    type: azure-native:securityinsights:OfficeDataConnector
    properties:
      dataConnectorId: 73e01a99-5cd7-4139-a149-9f2736ff2ab5
      resourceGroupName: myRg
      workspaceName: myWorkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:securityinsights:OfficeDataConnector 73e01a99-5cd7-4139-a149-9f2736ff2ab5 /subscriptions/d0cfe6b2-9ac0-4464-9919-dccaee2e48c0/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace/providers/Microsoft.SecurityInsights/dataConnectors/73e01a99-5cd7-4139-a149-9f2736ff2ab5 
```
