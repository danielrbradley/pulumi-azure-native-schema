Issue Attachment Contract details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateApiIssueAttachment
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var apiIssueAttachment = new AzureNative.ApiManagement.ApiIssueAttachment("apiIssueAttachment", new()
    {
        ApiId = "57d1f7558aa04f15146d9d8a",
        AttachmentId = "57d2ef278aa04f0888cba3f3",
        Content = "IEJhc2U2NA==",
        ContentFormat = "image/jpeg",
        IssueId = "57d2ef278aa04f0ad01d6cdc",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        Title = "Issue attachment.",
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
		_, err := apimanagement.NewApiIssueAttachment(ctx, "apiIssueAttachment", &apimanagement.ApiIssueAttachmentArgs{
			ApiId:             pulumi.String("57d1f7558aa04f15146d9d8a"),
			AttachmentId:      pulumi.String("57d2ef278aa04f0888cba3f3"),
			Content:           pulumi.String("IEJhc2U2NA=="),
			ContentFormat:     pulumi.String("image/jpeg"),
			IssueId:           pulumi.String("57d2ef278aa04f0ad01d6cdc"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			Title:             pulumi.String("Issue attachment."),
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
import com.pulumi.azurenative.apimanagement.ApiIssueAttachment;
import com.pulumi.azurenative.apimanagement.ApiIssueAttachmentArgs;
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
        var apiIssueAttachment = new ApiIssueAttachment("apiIssueAttachment", ApiIssueAttachmentArgs.builder()        
            .apiId("57d1f7558aa04f15146d9d8a")
            .attachmentId("57d2ef278aa04f0888cba3f3")
            .content("IEJhc2U2NA==")
            .contentFormat("image/jpeg")
            .issueId("57d2ef278aa04f0ad01d6cdc")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .title("Issue attachment.")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const apiIssueAttachment = new azure_native.apimanagement.ApiIssueAttachment("apiIssueAttachment", {
    apiId: "57d1f7558aa04f15146d9d8a",
    attachmentId: "57d2ef278aa04f0888cba3f3",
    content: "IEJhc2U2NA==",
    contentFormat: "image/jpeg",
    issueId: "57d2ef278aa04f0ad01d6cdc",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    title: "Issue attachment.",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api_issue_attachment = azure_native.apimanagement.ApiIssueAttachment("apiIssueAttachment",
    api_id="57d1f7558aa04f15146d9d8a",
    attachment_id="57d2ef278aa04f0888cba3f3",
    content="IEJhc2U2NA==",
    content_format="image/jpeg",
    issue_id="57d2ef278aa04f0ad01d6cdc",
    resource_group_name="rg1",
    service_name="apimService1",
    title="Issue attachment.")

```

```yaml
resources:
  apiIssueAttachment:
    type: azure-native:apimanagement:ApiIssueAttachment
    properties:
      apiId: 57d1f7558aa04f15146d9d8a
      attachmentId: 57d2ef278aa04f0888cba3f3
      content: IEJhc2U2NA==
      contentFormat: image/jpeg
      issueId: 57d2ef278aa04f0ad01d6cdc
      resourceGroupName: rg1
      serviceName: apimService1
      title: Issue attachment.

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:ApiIssueAttachment 57d2ef278aa04f0888cba3f3 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apis/57d1f7558aa04f15146d9d8a/issues/57d2ef278aa04f0ad01d6cdc/attachments/57d2ef278aa04f0888cba3f3 
```
