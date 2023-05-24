Issue Contract details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateApiIssue
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var apiIssue = new AzureNative.ApiManagement.ApiIssue("apiIssue", new()
    {
        ApiId = "57d1f7558aa04f15146d9d8a",
        CreatedDate = "2018-02-01T22:21:20.467Z",
        Description = "New API issue description",
        IssueId = "57d2ef278aa04f0ad01d6cdc",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        State = "open",
        Title = "New API issue",
        UserId = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/users/1",
    });

});


```

```go
package main

import (
	apimanagement "github.com/pulumi/pulumi-azure-native-sdk/apimanagement"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := apimanagement.NewApiIssue(ctx, "apiIssue", &apimanagement.ApiIssueArgs{
			ApiId:             pulumi.String("57d1f7558aa04f15146d9d8a"),
			CreatedDate:       pulumi.String("2018-02-01T22:21:20.467Z"),
			Description:       pulumi.String("New API issue description"),
			IssueId:           pulumi.String("57d2ef278aa04f0ad01d6cdc"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			State:             pulumi.String("open"),
			Title:             pulumi.String("New API issue"),
			UserId:            pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/users/1"),
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
import com.pulumi.azurenative.apimanagement.ApiIssue;
import com.pulumi.azurenative.apimanagement.ApiIssueArgs;
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
        var apiIssue = new ApiIssue("apiIssue", ApiIssueArgs.builder()        
            .apiId("57d1f7558aa04f15146d9d8a")
            .createdDate("2018-02-01T22:21:20.467Z")
            .description("New API issue description")
            .issueId("57d2ef278aa04f0ad01d6cdc")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .state("open")
            .title("New API issue")
            .userId("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/users/1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const apiIssue = new azure_native.apimanagement.ApiIssue("apiIssue", {
    apiId: "57d1f7558aa04f15146d9d8a",
    createdDate: "2018-02-01T22:21:20.467Z",
    description: "New API issue description",
    issueId: "57d2ef278aa04f0ad01d6cdc",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    state: "open",
    title: "New API issue",
    userId: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/users/1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api_issue = azure_native.apimanagement.ApiIssue("apiIssue",
    api_id="57d1f7558aa04f15146d9d8a",
    created_date="2018-02-01T22:21:20.467Z",
    description="New API issue description",
    issue_id="57d2ef278aa04f0ad01d6cdc",
    resource_group_name="rg1",
    service_name="apimService1",
    state="open",
    title="New API issue",
    user_id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/users/1")

```

```yaml
resources:
  apiIssue:
    type: azure-native:apimanagement:ApiIssue
    properties:
      apiId: 57d1f7558aa04f15146d9d8a
      createdDate: 2018-02-01T22:21:20.467Z
      description: New API issue description
      issueId: 57d2ef278aa04f0ad01d6cdc
      resourceGroupName: rg1
      serviceName: apimService1
      state: open
      title: New API issue
      userId: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/users/1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:ApiIssue 57d2ef278aa04f0ad01d6cdc /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apis/57d1f7558aa04f15146d9d8a/issues/57d2ef278aa04f0ad01d6cdc 
```
