Global Schema Contract details.
API Version: 2022-08-01.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateSchema1
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var globalSchema = new AzureNative.ApiManagement.GlobalSchema("globalSchema", new()
    {
        Description = "sample schema description",
        ResourceGroupName = "rg1",
        SchemaId = "schema1",
        SchemaType = "xml",
        ServiceName = "apimService1",
        Value = @"<xsd:schema xmlns:xsd=""http://www.w3.org/2001/XMLSchema""
           xmlns:tns=""http://tempuri.org/PurchaseOrderSchema.xsd""
           targetNamespace=""http://tempuri.org/PurchaseOrderSchema.xsd""
           elementFormDefault=""qualified"">
 <xsd:element name=""PurchaseOrder"" type=""tns:PurchaseOrderType""/>
 <xsd:complexType name=""PurchaseOrderType"">
  <xsd:sequence>
   <xsd:element name=""ShipTo"" type=""tns:USAddress"" maxOccurs=""2""/>
   <xsd:element name=""BillTo"" type=""tns:USAddress""/>
  </xsd:sequence>
  <xsd:attribute name=""OrderDate"" type=""xsd:date""/>
 </xsd:complexType>

 <xsd:complexType name=""USAddress"">
  <xsd:sequence>
   <xsd:element name=""name""   type=""xsd:string""/>
   <xsd:element name=""street"" type=""xsd:string""/>
   <xsd:element name=""city""   type=""xsd:string""/>
   <xsd:element name=""state""  type=""xsd:string""/>
   <xsd:element name=""zip""    type=""xsd:integer""/>
  </xsd:sequence>
  <xsd:attribute name=""country"" type=""xsd:NMTOKEN"" fixed=""US""/>
 </xsd:complexType>
</xsd:schema>",
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
		_, err := apimanagement.NewGlobalSchema(ctx, "globalSchema", &apimanagement.GlobalSchemaArgs{
			Description:       pulumi.String("sample schema description"),
			ResourceGroupName: pulumi.String("rg1"),
			SchemaId:          pulumi.String("schema1"),
			SchemaType:        pulumi.String("xml"),
			ServiceName:       pulumi.String("apimService1"),
			Value:             pulumi.Any("<xsd:schema xmlns:xsd=\"http://www.w3.org/2001/XMLSchema\"\n           xmlns:tns=\"http://tempuri.org/PurchaseOrderSchema.xsd\"\n           targetNamespace=\"http://tempuri.org/PurchaseOrderSchema.xsd\"\n           elementFormDefault=\"qualified\">\n <xsd:element name=\"PurchaseOrder\" type=\"tns:PurchaseOrderType\"/>\n <xsd:complexType name=\"PurchaseOrderType\">\n  <xsd:sequence>\n   <xsd:element name=\"ShipTo\" type=\"tns:USAddress\" maxOccurs=\"2\"/>\n   <xsd:element name=\"BillTo\" type=\"tns:USAddress\"/>\n  </xsd:sequence>\n  <xsd:attribute name=\"OrderDate\" type=\"xsd:date\"/>\n </xsd:complexType>\n\n <xsd:complexType name=\"USAddress\">\n  <xsd:sequence>\n   <xsd:element name=\"name\"   type=\"xsd:string\"/>\n   <xsd:element name=\"street\" type=\"xsd:string\"/>\n   <xsd:element name=\"city\"   type=\"xsd:string\"/>\n   <xsd:element name=\"state\"  type=\"xsd:string\"/>\n   <xsd:element name=\"zip\"    type=\"xsd:integer\"/>\n  </xsd:sequence>\n  <xsd:attribute name=\"country\" type=\"xsd:NMTOKEN\" fixed=\"US\"/>\n </xsd:complexType>\n</xsd:schema>"),
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
import com.pulumi.azurenative.apimanagement.GlobalSchema;
import com.pulumi.azurenative.apimanagement.GlobalSchemaArgs;
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
        var globalSchema = new GlobalSchema("globalSchema", GlobalSchemaArgs.builder()        
            .description("sample schema description")
            .resourceGroupName("rg1")
            .schemaId("schema1")
            .schemaType("xml")
            .serviceName("apimService1")
            .value("""
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
           xmlns:tns="http://tempuri.org/PurchaseOrderSchema.xsd"
           targetNamespace="http://tempuri.org/PurchaseOrderSchema.xsd"
           elementFormDefault="qualified">
 <xsd:element name="PurchaseOrder" type="tns:PurchaseOrderType"/>
 <xsd:complexType name="PurchaseOrderType">
  <xsd:sequence>
   <xsd:element name="ShipTo" type="tns:USAddress" maxOccurs="2"/>
   <xsd:element name="BillTo" type="tns:USAddress"/>
  </xsd:sequence>
  <xsd:attribute name="OrderDate" type="xsd:date"/>
 </xsd:complexType>

 <xsd:complexType name="USAddress">
  <xsd:sequence>
   <xsd:element name="name"   type="xsd:string"/>
   <xsd:element name="street" type="xsd:string"/>
   <xsd:element name="city"   type="xsd:string"/>
   <xsd:element name="state"  type="xsd:string"/>
   <xsd:element name="zip"    type="xsd:integer"/>
  </xsd:sequence>
  <xsd:attribute name="country" type="xsd:NMTOKEN" fixed="US"/>
 </xsd:complexType>
</xsd:schema>            """)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const globalSchema = new azure_native.apimanagement.GlobalSchema("globalSchema", {
    description: "sample schema description",
    resourceGroupName: "rg1",
    schemaId: "schema1",
    schemaType: "xml",
    serviceName: "apimService1",
    value: `<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
           xmlns:tns="http://tempuri.org/PurchaseOrderSchema.xsd"
           targetNamespace="http://tempuri.org/PurchaseOrderSchema.xsd"
           elementFormDefault="qualified">
 <xsd:element name="PurchaseOrder" type="tns:PurchaseOrderType"/>
 <xsd:complexType name="PurchaseOrderType">
  <xsd:sequence>
   <xsd:element name="ShipTo" type="tns:USAddress" maxOccurs="2"/>
   <xsd:element name="BillTo" type="tns:USAddress"/>
  </xsd:sequence>
  <xsd:attribute name="OrderDate" type="xsd:date"/>
 </xsd:complexType>

 <xsd:complexType name="USAddress">
  <xsd:sequence>
   <xsd:element name="name"   type="xsd:string"/>
   <xsd:element name="street" type="xsd:string"/>
   <xsd:element name="city"   type="xsd:string"/>
   <xsd:element name="state"  type="xsd:string"/>
   <xsd:element name="zip"    type="xsd:integer"/>
  </xsd:sequence>
  <xsd:attribute name="country" type="xsd:NMTOKEN" fixed="US"/>
 </xsd:complexType>
</xsd:schema>`,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

global_schema = azure_native.apimanagement.GlobalSchema("globalSchema",
    description="sample schema description",
    resource_group_name="rg1",
    schema_id="schema1",
    schema_type="xml",
    service_name="apimService1",
    value="""<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
           xmlns:tns="http://tempuri.org/PurchaseOrderSchema.xsd"
           targetNamespace="http://tempuri.org/PurchaseOrderSchema.xsd"
           elementFormDefault="qualified">
 <xsd:element name="PurchaseOrder" type="tns:PurchaseOrderType"/>
 <xsd:complexType name="PurchaseOrderType">
  <xsd:sequence>
   <xsd:element name="ShipTo" type="tns:USAddress" maxOccurs="2"/>
   <xsd:element name="BillTo" type="tns:USAddress"/>
  </xsd:sequence>
  <xsd:attribute name="OrderDate" type="xsd:date"/>
 </xsd:complexType>

 <xsd:complexType name="USAddress">
  <xsd:sequence>
   <xsd:element name="name"   type="xsd:string"/>
   <xsd:element name="street" type="xsd:string"/>
   <xsd:element name="city"   type="xsd:string"/>
   <xsd:element name="state"  type="xsd:string"/>
   <xsd:element name="zip"    type="xsd:integer"/>
  </xsd:sequence>
  <xsd:attribute name="country" type="xsd:NMTOKEN" fixed="US"/>
 </xsd:complexType>
</xsd:schema>""")

```

```yaml
resources:
  globalSchema:
    type: azure-native:apimanagement:GlobalSchema
    properties:
      description: sample schema description
      resourceGroupName: rg1
      schemaId: schema1
      schemaType: xml
      serviceName: apimService1
      value: "<xsd:schema xmlns:xsd=\"http://www.w3.org/2001/XMLSchema\"\r\n           xmlns:tns=\"http://tempuri.org/PurchaseOrderSchema.xsd\"\r\n           targetNamespace=\"http://tempuri.org/PurchaseOrderSchema.xsd\"\r\n           elementFormDefault=\"qualified\">\r\n <xsd:element name=\"PurchaseOrder\" type=\"tns:PurchaseOrderType\"/>\r\n <xsd:complexType name=\"PurchaseOrderType\">\r\n  <xsd:sequence>\r\n   <xsd:element name=\"ShipTo\" type=\"tns:USAddress\" maxOccurs=\"2\"/>\r\n   <xsd:element name=\"BillTo\" type=\"tns:USAddress\"/>\r\n  </xsd:sequence>\r\n  <xsd:attribute name=\"OrderDate\" type=\"xsd:date\"/>\r\n </xsd:complexType>\r\n\r\n <xsd:complexType name=\"USAddress\">\r\n  <xsd:sequence>\r\n   <xsd:element name=\"name\"   type=\"xsd:string\"/>\r\n   <xsd:element name=\"street\" type=\"xsd:string\"/>\r\n   <xsd:element name=\"city\"   type=\"xsd:string\"/>\r\n   <xsd:element name=\"state\"  type=\"xsd:string\"/>\r\n   <xsd:element name=\"zip\"    type=\"xsd:integer\"/>\r\n  </xsd:sequence>\r\n  <xsd:attribute name=\"country\" type=\"xsd:NMTOKEN\" fixed=\"US\"/>\r\n </xsd:complexType>\r\n</xsd:schema>"

```

{{% /example %}}
{{% example %}}
### ApiManagementCreateSchema2
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var globalSchema = new AzureNative.ApiManagement.GlobalSchema("globalSchema", new()
    {
        Description = "sample schema description",
        ResourceGroupName = "rg1",
        SchemaId = "schema1",
        SchemaType = "json",
        ServiceName = "apimService1",
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
		_, err := apimanagement.NewGlobalSchema(ctx, "globalSchema", &apimanagement.GlobalSchemaArgs{
			Description:       pulumi.String("sample schema description"),
			ResourceGroupName: pulumi.String("rg1"),
			SchemaId:          pulumi.String("schema1"),
			SchemaType:        pulumi.String("json"),
			ServiceName:       pulumi.String("apimService1"),
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
import com.pulumi.azurenative.apimanagement.GlobalSchema;
import com.pulumi.azurenative.apimanagement.GlobalSchemaArgs;
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
        var globalSchema = new GlobalSchema("globalSchema", GlobalSchemaArgs.builder()        
            .description("sample schema description")
            .resourceGroupName("rg1")
            .schemaId("schema1")
            .schemaType("json")
            .serviceName("apimService1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const globalSchema = new azure_native.apimanagement.GlobalSchema("globalSchema", {
    description: "sample schema description",
    resourceGroupName: "rg1",
    schemaId: "schema1",
    schemaType: "json",
    serviceName: "apimService1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

global_schema = azure_native.apimanagement.GlobalSchema("globalSchema",
    description="sample schema description",
    resource_group_name="rg1",
    schema_id="schema1",
    schema_type="json",
    service_name="apimService1")

```

```yaml
resources:
  globalSchema:
    type: azure-native:apimanagement:GlobalSchema
    properties:
      description: sample schema description
      resourceGroupName: rg1
      schemaId: schema1
      schemaType: json
      serviceName: apimService1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:GlobalSchema schema1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/schemas/schema1 
```
