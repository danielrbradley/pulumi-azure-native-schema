The integration account session.
API Version: 2019-05-01.
Previous API Version: 2019-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update an integration account session
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var integrationAccountSession = new AzureNative.Logic.IntegrationAccountSession("integrationAccountSession", new()
    {
        Content = 
        {
            { "controlNumber", "1234" },
            { "controlNumberChangedTime", "2017-02-21T22:30:11.9923759Z" },
        },
        IntegrationAccountName = "testia123",
        ResourceGroupName = "testrg123",
        SessionName = "testsession123-ICN",
    });

});


```

```go
package main

import (
	logic "github.com/pulumi/pulumi-azure-native-sdk/logic"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := logic.NewIntegrationAccountSession(ctx, "integrationAccountSession", &logic.IntegrationAccountSessionArgs{
			Content: pulumi.Any{
				ControlNumber:            "1234",
				ControlNumberChangedTime: "2017-02-21T22:30:11.9923759Z",
			},
			IntegrationAccountName: pulumi.String("testia123"),
			ResourceGroupName:      pulumi.String("testrg123"),
			SessionName:            pulumi.String("testsession123-ICN"),
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
import com.pulumi.azurenative.logic.IntegrationAccountSession;
import com.pulumi.azurenative.logic.IntegrationAccountSessionArgs;
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
        var integrationAccountSession = new IntegrationAccountSession("integrationAccountSession", IntegrationAccountSessionArgs.builder()        
            .content(Map.ofEntries(
                Map.entry("controlNumber", "1234"),
                Map.entry("controlNumberChangedTime", "2017-02-21T22:30:11.9923759Z")
            ))
            .integrationAccountName("testia123")
            .resourceGroupName("testrg123")
            .sessionName("testsession123-ICN")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const integrationAccountSession = new azure_native.logic.IntegrationAccountSession("integrationAccountSession", {
    content: {
        controlNumber: "1234",
        controlNumberChangedTime: "2017-02-21T22:30:11.9923759Z",
    },
    integrationAccountName: "testia123",
    resourceGroupName: "testrg123",
    sessionName: "testsession123-ICN",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

integration_account_session = azure_native.logic.IntegrationAccountSession("integrationAccountSession",
    content={
        "controlNumber": "1234",
        "controlNumberChangedTime": "2017-02-21T22:30:11.9923759Z",
    },
    integration_account_name="testia123",
    resource_group_name="testrg123",
    session_name="testsession123-ICN")

```

```yaml
resources:
  integrationAccountSession:
    type: azure-native:logic:IntegrationAccountSession
    properties:
      content:
        controlNumber: '1234'
        controlNumberChangedTime: 2017-02-21T22:30:11.9923759Z
      integrationAccountName: testia123
      resourceGroupName: testrg123
      sessionName: testsession123-ICN

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:logic:IntegrationAccountSession testsession123-ICN /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Logic/integrationAccounts/testia123/sessions/testsession123-ICN 
```
