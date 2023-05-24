Represents threat intelligence data connector.
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
    var tiDataConnector = new AzureNative.SecurityInsights.TIDataConnector("tiDataConnector", new()
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
		_, err := securityinsights.NewTIDataConnector(ctx, "tiDataConnector", &securityinsights.TIDataConnectorArgs{
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
import com.pulumi.azurenative.securityinsights.TIDataConnector;
import com.pulumi.azurenative.securityinsights.TIDataConnectorArgs;
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
        var tiDataConnector = new TIDataConnector("tiDataConnector", TIDataConnectorArgs.builder()        
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

const tiDataConnector = new azure_native.securityinsights.TIDataConnector("tiDataConnector", {
    dataConnectorId: "73e01a99-5cd7-4139-a149-9f2736ff2ab5",
    resourceGroupName: "myRg",
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

ti_data_connector = azure_native.securityinsights.TIDataConnector("tiDataConnector",
    data_connector_id="73e01a99-5cd7-4139-a149-9f2736ff2ab5",
    resource_group_name="myRg",
    workspace_name="myWorkspace")

```

```yaml
resources:
  tiDataConnector:
    type: azure-native:securityinsights:TIDataConnector
    properties:
      dataConnectorId: 73e01a99-5cd7-4139-a149-9f2736ff2ab5
      resourceGroupName: myRg
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
    var tiDataConnector = new AzureNative.SecurityInsights.TIDataConnector("tiDataConnector", new()
    {
        DataConnectorId = "73e01a99-5cd7-4139-a149-9f2736ff2ab5",
        DataTypes = new AzureNative.SecurityInsights.Inputs.TIDataConnectorDataTypesArgs
        {
            Indicators = new AzureNative.SecurityInsights.Inputs.TIDataConnectorDataTypesIndicatorsArgs
            {
                State = "Enabled",
            },
        },
        Kind = "ThreatIntelligence",
        ResourceGroupName = "myRg",
        TenantId = "06b3ccb8-1384-4bcc-aec7-852f6d57161b",
        TipLookbackPeriod = "2020-01-01T13:00:30.123Z",
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
		_, err := securityinsights.NewTIDataConnector(ctx, "tiDataConnector", &securityinsights.TIDataConnectorArgs{
			DataConnectorId: pulumi.String("73e01a99-5cd7-4139-a149-9f2736ff2ab5"),
			DataTypes: securityinsights.TIDataConnectorDataTypesResponse{
				Indicators: &securityinsights.TIDataConnectorDataTypesIndicatorsArgs{
					State: pulumi.String("Enabled"),
				},
			},
			Kind:              pulumi.String("ThreatIntelligence"),
			ResourceGroupName: pulumi.String("myRg"),
			TenantId:          pulumi.String("06b3ccb8-1384-4bcc-aec7-852f6d57161b"),
			TipLookbackPeriod: pulumi.String("2020-01-01T13:00:30.123Z"),
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
import com.pulumi.azurenative.securityinsights.TIDataConnector;
import com.pulumi.azurenative.securityinsights.TIDataConnectorArgs;
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
        var tiDataConnector = new TIDataConnector("tiDataConnector", TIDataConnectorArgs.builder()        
            .dataConnectorId("73e01a99-5cd7-4139-a149-9f2736ff2ab5")
            .dataTypes(Map.of("indicators", Map.of("state", "Enabled")))
            .kind("ThreatIntelligence")
            .resourceGroupName("myRg")
            .tenantId("06b3ccb8-1384-4bcc-aec7-852f6d57161b")
            .tipLookbackPeriod("2020-01-01T13:00:30.123Z")
            .workspaceName("myWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const tiDataConnector = new azure_native.securityinsights.TIDataConnector("tiDataConnector", {
    dataConnectorId: "73e01a99-5cd7-4139-a149-9f2736ff2ab5",
    dataTypes: {
        indicators: {
            state: "Enabled",
        },
    },
    kind: "ThreatIntelligence",
    resourceGroupName: "myRg",
    tenantId: "06b3ccb8-1384-4bcc-aec7-852f6d57161b",
    tipLookbackPeriod: "2020-01-01T13:00:30.123Z",
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

ti_data_connector = azure_native.securityinsights.TIDataConnector("tiDataConnector",
    data_connector_id="73e01a99-5cd7-4139-a149-9f2736ff2ab5",
    data_types=azure_native.securityinsights.TIDataConnectorDataTypesResponseArgs(
        indicators=azure_native.securityinsights.TIDataConnectorDataTypesIndicatorsArgs(
            state="Enabled",
        ),
    ),
    kind="ThreatIntelligence",
    resource_group_name="myRg",
    tenant_id="06b3ccb8-1384-4bcc-aec7-852f6d57161b",
    tip_lookback_period="2020-01-01T13:00:30.123Z",
    workspace_name="myWorkspace")

```

```yaml
resources:
  tiDataConnector:
    type: azure-native:securityinsights:TIDataConnector
    properties:
      dataConnectorId: 73e01a99-5cd7-4139-a149-9f2736ff2ab5
      dataTypes:
        indicators:
          state: Enabled
      kind: ThreatIntelligence
      resourceGroupName: myRg
      tenantId: 06b3ccb8-1384-4bcc-aec7-852f6d57161b
      tipLookbackPeriod: 2020-01-01T13:00:30.123Z
      workspaceName: myWorkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:securityinsights:TIDataConnector 73e01a99-5cd7-4139-a149-9f2736ff2ab5 /subscriptions/d0cfe6b2-9ac0-4464-9919-dccaee2e48c0/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace/providers/Microsoft.SecurityInsights/dataConnectors/73e01a99-5cd7-4139-a149-9f2736ff2ab5 
```
