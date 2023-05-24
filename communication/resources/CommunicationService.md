A class representing a CommunicationService resource.
API Version: 2023-03-01-preview.
Previous API Version: 2020-08-20. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update resource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var communicationService = new AzureNative.Communication.CommunicationService("communicationService", new()
    {
        CommunicationServiceName = "MyCommunicationResource",
        DataLocation = "United States",
        Location = "Global",
        ResourceGroupName = "MyResourceGroup",
    });

});


```

```go
package main

import (
	communication "github.com/pulumi/pulumi-azure-native-sdk/communication"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := communication.NewCommunicationService(ctx, "communicationService", &communication.CommunicationServiceArgs{
			CommunicationServiceName: pulumi.String("MyCommunicationResource"),
			DataLocation:             pulumi.String("United States"),
			Location:                 pulumi.String("Global"),
			ResourceGroupName:        pulumi.String("MyResourceGroup"),
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
import com.pulumi.azurenative.communication.CommunicationService;
import com.pulumi.azurenative.communication.CommunicationServiceArgs;
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
        var communicationService = new CommunicationService("communicationService", CommunicationServiceArgs.builder()        
            .communicationServiceName("MyCommunicationResource")
            .dataLocation("United States")
            .location("Global")
            .resourceGroupName("MyResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const communicationService = new azure_native.communication.CommunicationService("communicationService", {
    communicationServiceName: "MyCommunicationResource",
    dataLocation: "United States",
    location: "Global",
    resourceGroupName: "MyResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

communication_service = azure_native.communication.CommunicationService("communicationService",
    communication_service_name="MyCommunicationResource",
    data_location="United States",
    location="Global",
    resource_group_name="MyResourceGroup")

```

```yaml
resources:
  communicationService:
    type: azure-native:communication:CommunicationService
    properties:
      communicationServiceName: MyCommunicationResource
      dataLocation: United States
      location: Global
      resourceGroupName: MyResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:communication:CommunicationService MyCommunicationResource /subscriptions/11112222-3333-4444-5555-666677778888/resourceGroups/MyResourceGroup/providers/Microsoft.Communication/CommunicationServices/MyCommunicationResource 
```
