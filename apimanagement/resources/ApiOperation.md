API Operation details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateApiOperation
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var apiOperation = new AzureNative.ApiManagement.ApiOperation("apiOperation", new()
    {
        ApiId = "PetStoreTemplate2",
        Description = "This can only be done by the logged in user.",
        DisplayName = "createUser2",
        Method = "POST",
        OperationId = "newoperations",
        Request = new AzureNative.ApiManagement.Inputs.RequestContractArgs
        {
            Description = "Created user object",
            Headers = new[] {},
            QueryParameters = new[] {},
            Representations = new[]
            {
                new AzureNative.ApiManagement.Inputs.RepresentationContractArgs
                {
                    ContentType = "application/json",
                    SchemaId = "592f6c1d0af5840ca8897f0c",
                    TypeName = "User",
                },
            },
        },
        ResourceGroupName = "rg1",
        Responses = new[]
        {
            new AzureNative.ApiManagement.Inputs.ResponseContractArgs
            {
                Description = "successful operation",
                Headers = new[] {},
                Representations = new[]
                {
                    new AzureNative.ApiManagement.Inputs.RepresentationContractArgs
                    {
                        ContentType = "application/xml",
                    },
                    new AzureNative.ApiManagement.Inputs.RepresentationContractArgs
                    {
                        ContentType = "application/json",
                    },
                },
                StatusCode = 200,
            },
        },
        ServiceName = "apimService1",
        TemplateParameters = new[] {},
        UrlTemplate = "/user1",
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
		_, err := apimanagement.NewApiOperation(ctx, "apiOperation", &apimanagement.ApiOperationArgs{
			ApiId:       pulumi.String("PetStoreTemplate2"),
			Description: pulumi.String("This can only be done by the logged in user."),
			DisplayName: pulumi.String("createUser2"),
			Method:      pulumi.String("POST"),
			OperationId: pulumi.String("newoperations"),
			Request: apimanagement.RequestContractResponse{
				Description:     pulumi.String("Created user object"),
				Headers:         apimanagement.ParameterContractArray{},
				QueryParameters: apimanagement.ParameterContractArray{},
				Representations: apimanagement.RepresentationContractArray{
					&apimanagement.RepresentationContractArgs{
						ContentType: pulumi.String("application/json"),
						SchemaId:    pulumi.String("592f6c1d0af5840ca8897f0c"),
						TypeName:    pulumi.String("User"),
					},
				},
			},
			ResourceGroupName: pulumi.String("rg1"),
			Responses: []apimanagement.ResponseContractArgs{
				{
					Description: pulumi.String("successful operation"),
					Headers:     apimanagement.ParameterContractArray{},
					Representations: apimanagement.RepresentationContractArray{
						{
							ContentType: pulumi.String("application/xml"),
						},
						{
							ContentType: pulumi.String("application/json"),
						},
					},
					StatusCode: pulumi.Int(200),
				},
			},
			ServiceName:        pulumi.String("apimService1"),
			TemplateParameters: apimanagement.ParameterContractArray{},
			UrlTemplate:        pulumi.String("/user1"),
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
import com.pulumi.azurenative.apimanagement.ApiOperation;
import com.pulumi.azurenative.apimanagement.ApiOperationArgs;
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
        var apiOperation = new ApiOperation("apiOperation", ApiOperationArgs.builder()        
            .apiId("PetStoreTemplate2")
            .description("This can only be done by the logged in user.")
            .displayName("createUser2")
            .method("POST")
            .operationId("newoperations")
            .request(Map.ofEntries(
                Map.entry("description", "Created user object"),
                Map.entry("headers", ),
                Map.entry("queryParameters", ),
                Map.entry("representations", Map.ofEntries(
                    Map.entry("contentType", "application/json"),
                    Map.entry("schemaId", "592f6c1d0af5840ca8897f0c"),
                    Map.entry("typeName", "User")
                ))
            ))
            .resourceGroupName("rg1")
            .responses(Map.ofEntries(
                Map.entry("description", "successful operation"),
                Map.entry("headers", ),
                Map.entry("representations",                 
                    Map.of("contentType", "application/xml"),
                    Map.of("contentType", "application/json")),
                Map.entry("statusCode", 200)
            ))
            .serviceName("apimService1")
            .templateParameters()
            .urlTemplate("/user1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const apiOperation = new azure_native.apimanagement.ApiOperation("apiOperation", {
    apiId: "PetStoreTemplate2",
    description: "This can only be done by the logged in user.",
    displayName: "createUser2",
    method: "POST",
    operationId: "newoperations",
    request: {
        description: "Created user object",
        headers: [],
        queryParameters: [],
        representations: [{
            contentType: "application/json",
            schemaId: "592f6c1d0af5840ca8897f0c",
            typeName: "User",
        }],
    },
    resourceGroupName: "rg1",
    responses: [{
        description: "successful operation",
        headers: [],
        representations: [
            {
                contentType: "application/xml",
            },
            {
                contentType: "application/json",
            },
        ],
        statusCode: 200,
    }],
    serviceName: "apimService1",
    templateParameters: [],
    urlTemplate: "/user1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api_operation = azure_native.apimanagement.ApiOperation("apiOperation",
    api_id="PetStoreTemplate2",
    description="This can only be done by the logged in user.",
    display_name="createUser2",
    method="POST",
    operation_id="newoperations",
    request=azure_native.apimanagement.RequestContractResponseArgs(
        description="Created user object",
        headers=[],
        query_parameters=[],
        representations=[azure_native.apimanagement.RepresentationContractArgs(
            content_type="application/json",
            schema_id="592f6c1d0af5840ca8897f0c",
            type_name="User",
        )],
    ),
    resource_group_name="rg1",
    responses=[{
        "description": "successful operation",
        "headers": [],
        "representations": [
            azure_native.apimanagement.RepresentationContractArgs(
                content_type="application/xml",
            ),
            azure_native.apimanagement.RepresentationContractArgs(
                content_type="application/json",
            ),
        ],
        "statusCode": 200,
    }],
    service_name="apimService1",
    template_parameters=[],
    url_template="/user1")

```

```yaml
resources:
  apiOperation:
    type: azure-native:apimanagement:ApiOperation
    properties:
      apiId: PetStoreTemplate2
      description: This can only be done by the logged in user.
      displayName: createUser2
      method: POST
      operationId: newoperations
      request:
        description: Created user object
        headers: []
        queryParameters: []
        representations:
          - contentType: application/json
            schemaId: 592f6c1d0af5840ca8897f0c
            typeName: User
      resourceGroupName: rg1
      responses:
        - description: successful operation
          headers: []
          representations:
            - contentType: application/xml
            - contentType: application/json
          statusCode: 200
      serviceName: apimService1
      templateParameters: []
      urlTemplate: /user1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:ApiOperation newoperations /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apis/PetStoreTemplate2/operations/newoperations 
```
