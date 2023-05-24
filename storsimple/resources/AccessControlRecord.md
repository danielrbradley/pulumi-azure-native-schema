The access control record.
API Version: 2017-06-01.
Previous API Version: 2017-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### AccessControlRecordsCreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var accessControlRecord = new AzureNative.StorSimple.AccessControlRecord("accessControlRecord", new()
    {
        AccessControlRecordName = "ACRForTest",
        InitiatorName = "iqn.2017-06.com.contoso:ForTest",
        ManagerName = "ManagerForSDKTest1",
        ResourceGroupName = "ResourceGroupForSDKTest",
    });

});


```

```go
package main

import (
	storsimple "github.com/pulumi/pulumi-azure-native-sdk/storsimple"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := storsimple.NewAccessControlRecord(ctx, "accessControlRecord", &storsimple.AccessControlRecordArgs{
			AccessControlRecordName: pulumi.String("ACRForTest"),
			InitiatorName:           pulumi.String("iqn.2017-06.com.contoso:ForTest"),
			ManagerName:             pulumi.String("ManagerForSDKTest1"),
			ResourceGroupName:       pulumi.String("ResourceGroupForSDKTest"),
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
import com.pulumi.azurenative.storsimple.AccessControlRecord;
import com.pulumi.azurenative.storsimple.AccessControlRecordArgs;
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
        var accessControlRecord = new AccessControlRecord("accessControlRecord", AccessControlRecordArgs.builder()        
            .accessControlRecordName("ACRForTest")
            .initiatorName("iqn.2017-06.com.contoso:ForTest")
            .managerName("ManagerForSDKTest1")
            .resourceGroupName("ResourceGroupForSDKTest")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const accessControlRecord = new azure_native.storsimple.AccessControlRecord("accessControlRecord", {
    accessControlRecordName: "ACRForTest",
    initiatorName: "iqn.2017-06.com.contoso:ForTest",
    managerName: "ManagerForSDKTest1",
    resourceGroupName: "ResourceGroupForSDKTest",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

access_control_record = azure_native.storsimple.AccessControlRecord("accessControlRecord",
    access_control_record_name="ACRForTest",
    initiator_name="iqn.2017-06.com.contoso:ForTest",
    manager_name="ManagerForSDKTest1",
    resource_group_name="ResourceGroupForSDKTest")

```

```yaml
resources:
  accessControlRecord:
    type: azure-native:storsimple:AccessControlRecord
    properties:
      accessControlRecordName: ACRForTest
      initiatorName: iqn.2017-06.com.contoso:ForTest
      managerName: ManagerForSDKTest1
      resourceGroupName: ResourceGroupForSDKTest

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storsimple:AccessControlRecord ACRForTest /subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.StorSimple/managers/ManagerForSDKTest1/accessControlRecords/ACRForTest 
```
