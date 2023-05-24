Issue Comment Contract details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateApiIssueComment
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var apiIssueComment = new AzureNative.ApiManagement.ApiIssueComment("apiIssueComment", new()
    {
        ApiId = "57d1f7558aa04f15146d9d8a",
        CommentId = "599e29ab193c3c0bd0b3e2fb",
        CreatedDate = "2018-02-01T22:21:20.467Z",
        IssueId = "57d2ef278aa04f0ad01d6cdc",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        Text = "Issue comment.",
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
		_, err := apimanagement.NewApiIssueComment(ctx, "apiIssueComment", &apimanagement.ApiIssueCommentArgs{
			ApiId:             pulumi.String("57d1f7558aa04f15146d9d8a"),
			CommentId:         pulumi.String("599e29ab193c3c0bd0b3e2fb"),
			CreatedDate:       pulumi.String("2018-02-01T22:21:20.467Z"),
			IssueId:           pulumi.String("57d2ef278aa04f0ad01d6cdc"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			Text:              pulumi.String("Issue comment."),
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
import com.pulumi.azurenative.apimanagement.ApiIssueComment;
import com.pulumi.azurenative.apimanagement.ApiIssueCommentArgs;
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
        var apiIssueComment = new ApiIssueComment("apiIssueComment", ApiIssueCommentArgs.builder()        
            .apiId("57d1f7558aa04f15146d9d8a")
            .commentId("599e29ab193c3c0bd0b3e2fb")
            .createdDate("2018-02-01T22:21:20.467Z")
            .issueId("57d2ef278aa04f0ad01d6cdc")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .text("Issue comment.")
            .userId("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/users/1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const apiIssueComment = new azure_native.apimanagement.ApiIssueComment("apiIssueComment", {
    apiId: "57d1f7558aa04f15146d9d8a",
    commentId: "599e29ab193c3c0bd0b3e2fb",
    createdDate: "2018-02-01T22:21:20.467Z",
    issueId: "57d2ef278aa04f0ad01d6cdc",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    text: "Issue comment.",
    userId: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/users/1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api_issue_comment = azure_native.apimanagement.ApiIssueComment("apiIssueComment",
    api_id="57d1f7558aa04f15146d9d8a",
    comment_id="599e29ab193c3c0bd0b3e2fb",
    created_date="2018-02-01T22:21:20.467Z",
    issue_id="57d2ef278aa04f0ad01d6cdc",
    resource_group_name="rg1",
    service_name="apimService1",
    text="Issue comment.",
    user_id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/users/1")

```

```yaml
resources:
  apiIssueComment:
    type: azure-native:apimanagement:ApiIssueComment
    properties:
      apiId: 57d1f7558aa04f15146d9d8a
      commentId: 599e29ab193c3c0bd0b3e2fb
      createdDate: 2018-02-01T22:21:20.467Z
      issueId: 57d2ef278aa04f0ad01d6cdc
      resourceGroupName: rg1
      serviceName: apimService1
      text: Issue comment.
      userId: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/users/1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:ApiIssueComment 599e29ab193c3c0bd0b3e2fb /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apis/57d1f7558aa04f15146d9d8a/issues/57d2ef278aa04f0ad01d6cdc/comments/599e29ab193c3c0bd0b3e2fb 
```
