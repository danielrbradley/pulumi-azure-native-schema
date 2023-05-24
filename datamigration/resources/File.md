A file resource
API Version: 2021-06-30.
Previous API Version: 2018-07-15-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Files_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var file = new AzureNative.DataMigration.File("file", new()
    {
        FileName = "x114d023d8",
        GroupName = "DmsSdkRg",
        ProjectName = "DmsSdkProject",
        Properties = new AzureNative.DataMigration.Inputs.ProjectFilePropertiesArgs
        {
            FilePath = "DmsSdkFilePath/DmsSdkFile.sql",
        },
        ServiceName = "DmsSdkService",
    });

});


```

```go
package main

import (
	datamigration "github.com/pulumi/pulumi-azure-native-sdk/datamigration"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := datamigration.NewFile(ctx, "file", &datamigration.FileArgs{
			FileName:    pulumi.String("x114d023d8"),
			GroupName:   pulumi.String("DmsSdkRg"),
			ProjectName: pulumi.String("DmsSdkProject"),
			Properties: &datamigration.ProjectFilePropertiesArgs{
				FilePath: pulumi.String("DmsSdkFilePath/DmsSdkFile.sql"),
			},
			ServiceName: pulumi.String("DmsSdkService"),
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
import com.pulumi.azurenative.datamigration.File;
import com.pulumi.azurenative.datamigration.FileArgs;
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
        var file = new File("file", FileArgs.builder()        
            .fileName("x114d023d8")
            .groupName("DmsSdkRg")
            .projectName("DmsSdkProject")
            .properties(Map.of("filePath", "DmsSdkFilePath/DmsSdkFile.sql"))
            .serviceName("DmsSdkService")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const file = new azure_native.datamigration.File("file", {
    fileName: "x114d023d8",
    groupName: "DmsSdkRg",
    projectName: "DmsSdkProject",
    properties: {
        filePath: "DmsSdkFilePath/DmsSdkFile.sql",
    },
    serviceName: "DmsSdkService",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

file = azure_native.datamigration.File("file",
    file_name="x114d023d8",
    group_name="DmsSdkRg",
    project_name="DmsSdkProject",
    properties=azure_native.datamigration.ProjectFilePropertiesArgs(
        file_path="DmsSdkFilePath/DmsSdkFile.sql",
    ),
    service_name="DmsSdkService")

```

```yaml
resources:
  file:
    type: azure-native:datamigration:File
    properties:
      fileName: x114d023d8
      groupName: DmsSdkRg
      projectName: DmsSdkProject
      properties:
        filePath: DmsSdkFilePath/DmsSdkFile.sql
      serviceName: DmsSdkService

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:datamigration:File x114d023d8 /subscriptions/fc04246f-04c5-437e-ac5e-206a19e7193f/resourceGroups/DmsSdkRg/providers/Microsoft.DataMigration/services/DmsSdkService/projects/DmsSdkProject/files/x114d023d8 
```
