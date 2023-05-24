The integration account schema.
API Version: 2019-05-01.
Previous API Version: 2019-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update schema
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var integrationAccountSchema = new AzureNative.Logic.IntegrationAccountSchema("integrationAccountSchema", new()
    {
        Content = @"<?xml version=""1.0"" encoding=""utf-16""?>
<xs:schema xmlns:b=""http://schemas.microsoft.com/BizTalk/2003"" xmlns=""http://Inbound_EDI.OrderFile"" targetNamespace=""http://Inbound_EDI.OrderFile"" xmlns:xs=""http://www.w3.org/2001/XMLSchema"">
  <xs:annotation>
    <xs:appinfo>
      <b:schemaInfo default_pad_char="" "" count_positions_by_byte=""false"" parser_optimization=""speed"" lookahead_depth=""3"" suppress_empty_nodes=""false"" generate_empty_nodes=""true"" allow_early_termination=""false"" early_terminate_optional_fields=""false"" allow_message_breakup_of_infix_root=""false"" compile_parse_tables=""false"" standard=""Flat File"" root_reference=""OrderFile"" />
      <schemaEditorExtension:schemaInfo namespaceAlias=""b"" extensionClass=""Microsoft.BizTalk.FlatFileExtension.FlatFileExtension"" standardName=""Flat File"" xmlns:schemaEditorExtension=""http://schemas.microsoft.com/BizTalk/2003/SchemaEditorExtensions"" />
    </xs:appinfo>
  </xs:annotation>
  <xs:element name=""OrderFile"">
    <xs:annotation>
      <xs:appinfo>
        <b:recordInfo structure=""delimited"" preserve_delimiter_for_empty_data=""true"" suppress_trailing_delimiters=""false"" sequence_number=""1"" />
      </xs:appinfo>
    </xs:annotation>
    <xs:complexType>
      <xs:sequence>
        <xs:annotation>
          <xs:appinfo>
            <b:groupInfo sequence_number=""0"" />
          </xs:appinfo>
        </xs:annotation>
        <xs:element name=""Order"">
          <xs:annotation>
            <xs:appinfo>
              <b:recordInfo sequence_number=""1"" structure=""delimited"" preserve_delimiter_for_empty_data=""true"" suppress_trailing_delimiters=""false"" child_delimiter_type=""hex"" child_delimiter=""0x0D 0x0A"" child_order=""infix"" />
            </xs:appinfo>
          </xs:annotation>
          <xs:complexType>
            <xs:sequence>
              <xs:annotation>
                <xs:appinfo>
                  <b:groupInfo sequence_number=""0"" />
                </xs:appinfo>
              </xs:annotation>
              <xs:element name=""Header"">
                <xs:annotation>
                  <xs:appinfo>
                    <b:recordInfo sequence_number=""1"" structure=""delimited"" preserve_delimiter_for_empty_data=""true"" suppress_trailing_delimiters=""false"" child_delimiter_type=""char"" child_delimiter=""|"" child_order=""infix"" tag_name=""HDR|"" />
                  </xs:appinfo>
                </xs:annotation>
                <xs:complexType>
                  <xs:sequence>
                    <xs:annotation>
                      <xs:appinfo>
                        <b:groupInfo sequence_number=""0"" />
                      </xs:appinfo>
                    </xs:annotation>
                    <xs:element name=""PODate"" type=""xs:string"">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number=""1"" justification=""left"" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name=""PONumber"" type=""xs:string"">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo justification=""left"" sequence_number=""2"" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name=""CustomerID"" type=""xs:string"">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number=""3"" justification=""left"" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name=""CustomerContactName"" type=""xs:string"">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number=""4"" justification=""left"" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name=""CustomerContactPhone"" type=""xs:string"">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number=""5"" justification=""left"" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                  </xs:sequence>
                </xs:complexType>
              </xs:element>
              <xs:element minOccurs=""1"" maxOccurs=""unbounded"" name=""LineItems"">
                <xs:annotation>
                  <xs:appinfo>
                    <b:recordInfo sequence_number=""2"" structure=""delimited"" preserve_delimiter_for_empty_data=""true"" suppress_trailing_delimiters=""false"" child_delimiter_type=""char"" child_delimiter=""|"" child_order=""infix"" tag_name=""DTL|"" />
                  </xs:appinfo>
                </xs:annotation>
                <xs:complexType>
                  <xs:sequence>
                    <xs:annotation>
                      <xs:appinfo>
                        <b:groupInfo sequence_number=""0"" />
                      </xs:appinfo>
                    </xs:annotation>
                    <xs:element name=""PONumber"" type=""xs:string"">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number=""1"" justification=""left"" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name=""ItemOrdered"" type=""xs:string"">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number=""2"" justification=""left"" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name=""Quantity"" type=""xs:string"">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number=""3"" justification=""left"" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name=""UOM"" type=""xs:string"">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number=""4"" justification=""left"" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name=""Price"" type=""xs:string"">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number=""5"" justification=""left"" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name=""ExtendedPrice"" type=""xs:string"">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number=""6"" justification=""left"" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name=""Description"" type=""xs:string"">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number=""7"" justification=""left"" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                  </xs:sequence>
                </xs:complexType>
              </xs:element>
            </xs:sequence>
          </xs:complexType>
        </xs:element>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>",
        ContentType = "application/xml",
        IntegrationAccountName = "testIntegrationAccount",
        Location = "westus",
        Metadata = null,
        ResourceGroupName = "testResourceGroup",
        SchemaName = "testSchema",
        SchemaType = "Xml",
        Tags = 
        {
            { "integrationAccountSchemaName", "IntegrationAccountSchema8120" },
        },
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
		_, err := logic.NewIntegrationAccountSchema(ctx, "integrationAccountSchema", &logic.IntegrationAccountSchemaArgs{
			Content:                pulumi.String("<?xml version=\"1.0\" encoding=\"utf-16\"?>\n<xs:schema xmlns:b=\"http://schemas.microsoft.com/BizTalk/2003\" xmlns=\"http://Inbound_EDI.OrderFile\" targetNamespace=\"http://Inbound_EDI.OrderFile\" xmlns:xs=\"http://www.w3.org/2001/XMLSchema\">\n  <xs:annotation>\n    <xs:appinfo>\n      <b:schemaInfo default_pad_char=\" \" count_positions_by_byte=\"false\" parser_optimization=\"speed\" lookahead_depth=\"3\" suppress_empty_nodes=\"false\" generate_empty_nodes=\"true\" allow_early_termination=\"false\" early_terminate_optional_fields=\"false\" allow_message_breakup_of_infix_root=\"false\" compile_parse_tables=\"false\" standard=\"Flat File\" root_reference=\"OrderFile\" />\n      <schemaEditorExtension:schemaInfo namespaceAlias=\"b\" extensionClass=\"Microsoft.BizTalk.FlatFileExtension.FlatFileExtension\" standardName=\"Flat File\" xmlns:schemaEditorExtension=\"http://schemas.microsoft.com/BizTalk/2003/SchemaEditorExtensions\" />\n    </xs:appinfo>\n  </xs:annotation>\n  <xs:element name=\"OrderFile\">\n    <xs:annotation>\n      <xs:appinfo>\n        <b:recordInfo structure=\"delimited\" preserve_delimiter_for_empty_data=\"true\" suppress_trailing_delimiters=\"false\" sequence_number=\"1\" />\n      </xs:appinfo>\n    </xs:annotation>\n    <xs:complexType>\n      <xs:sequence>\n        <xs:annotation>\n          <xs:appinfo>\n            <b:groupInfo sequence_number=\"0\" />\n          </xs:appinfo>\n        </xs:annotation>\n        <xs:element name=\"Order\">\n          <xs:annotation>\n            <xs:appinfo>\n              <b:recordInfo sequence_number=\"1\" structure=\"delimited\" preserve_delimiter_for_empty_data=\"true\" suppress_trailing_delimiters=\"false\" child_delimiter_type=\"hex\" child_delimiter=\"0x0D 0x0A\" child_order=\"infix\" />\n            </xs:appinfo>\n          </xs:annotation>\n          <xs:complexType>\n            <xs:sequence>\n              <xs:annotation>\n                <xs:appinfo>\n                  <b:groupInfo sequence_number=\"0\" />\n                </xs:appinfo>\n              </xs:annotation>\n              <xs:element name=\"Header\">\n                <xs:annotation>\n                  <xs:appinfo>\n                    <b:recordInfo sequence_number=\"1\" structure=\"delimited\" preserve_delimiter_for_empty_data=\"true\" suppress_trailing_delimiters=\"false\" child_delimiter_type=\"char\" child_delimiter=\"|\" child_order=\"infix\" tag_name=\"HDR|\" />\n                  </xs:appinfo>\n                </xs:annotation>\n                <xs:complexType>\n                  <xs:sequence>\n                    <xs:annotation>\n                      <xs:appinfo>\n                        <b:groupInfo sequence_number=\"0\" />\n                      </xs:appinfo>\n                    </xs:annotation>\n                    <xs:element name=\"PODate\" type=\"xs:string\">\n                      <xs:annotation>\n                        <xs:appinfo>\n                          <b:fieldInfo sequence_number=\"1\" justification=\"left\" />\n                        </xs:appinfo>\n                      </xs:annotation>\n                    </xs:element>\n                    <xs:element name=\"PONumber\" type=\"xs:string\">\n                      <xs:annotation>\n                        <xs:appinfo>\n                          <b:fieldInfo justification=\"left\" sequence_number=\"2\" />\n                        </xs:appinfo>\n                      </xs:annotation>\n                    </xs:element>\n                    <xs:element name=\"CustomerID\" type=\"xs:string\">\n                      <xs:annotation>\n                        <xs:appinfo>\n                          <b:fieldInfo sequence_number=\"3\" justification=\"left\" />\n                        </xs:appinfo>\n                      </xs:annotation>\n                    </xs:element>\n                    <xs:element name=\"CustomerContactName\" type=\"xs:string\">\n                      <xs:annotation>\n                        <xs:appinfo>\n                          <b:fieldInfo sequence_number=\"4\" justification=\"left\" />\n                        </xs:appinfo>\n                      </xs:annotation>\n                    </xs:element>\n                    <xs:element name=\"CustomerContactPhone\" type=\"xs:string\">\n                      <xs:annotation>\n                        <xs:appinfo>\n                          <b:fieldInfo sequence_number=\"5\" justification=\"left\" />\n                        </xs:appinfo>\n                      </xs:annotation>\n                    </xs:element>\n                  </xs:sequence>\n                </xs:complexType>\n              </xs:element>\n              <xs:element minOccurs=\"1\" maxOccurs=\"unbounded\" name=\"LineItems\">\n                <xs:annotation>\n                  <xs:appinfo>\n                    <b:recordInfo sequence_number=\"2\" structure=\"delimited\" preserve_delimiter_for_empty_data=\"true\" suppress_trailing_delimiters=\"false\" child_delimiter_type=\"char\" child_delimiter=\"|\" child_order=\"infix\" tag_name=\"DTL|\" />\n                  </xs:appinfo>\n                </xs:annotation>\n                <xs:complexType>\n                  <xs:sequence>\n                    <xs:annotation>\n                      <xs:appinfo>\n                        <b:groupInfo sequence_number=\"0\" />\n                      </xs:appinfo>\n                    </xs:annotation>\n                    <xs:element name=\"PONumber\" type=\"xs:string\">\n                      <xs:annotation>\n                        <xs:appinfo>\n                          <b:fieldInfo sequence_number=\"1\" justification=\"left\" />\n                        </xs:appinfo>\n                      </xs:annotation>\n                    </xs:element>\n                    <xs:element name=\"ItemOrdered\" type=\"xs:string\">\n                      <xs:annotation>\n                        <xs:appinfo>\n                          <b:fieldInfo sequence_number=\"2\" justification=\"left\" />\n                        </xs:appinfo>\n                      </xs:annotation>\n                    </xs:element>\n                    <xs:element name=\"Quantity\" type=\"xs:string\">\n                      <xs:annotation>\n                        <xs:appinfo>\n                          <b:fieldInfo sequence_number=\"3\" justification=\"left\" />\n                        </xs:appinfo>\n                      </xs:annotation>\n                    </xs:element>\n                    <xs:element name=\"UOM\" type=\"xs:string\">\n                      <xs:annotation>\n                        <xs:appinfo>\n                          <b:fieldInfo sequence_number=\"4\" justification=\"left\" />\n                        </xs:appinfo>\n                      </xs:annotation>\n                    </xs:element>\n                    <xs:element name=\"Price\" type=\"xs:string\">\n                      <xs:annotation>\n                        <xs:appinfo>\n                          <b:fieldInfo sequence_number=\"5\" justification=\"left\" />\n                        </xs:appinfo>\n                      </xs:annotation>\n                    </xs:element>\n                    <xs:element name=\"ExtendedPrice\" type=\"xs:string\">\n                      <xs:annotation>\n                        <xs:appinfo>\n                          <b:fieldInfo sequence_number=\"6\" justification=\"left\" />\n                        </xs:appinfo>\n                      </xs:annotation>\n                    </xs:element>\n                    <xs:element name=\"Description\" type=\"xs:string\">\n                      <xs:annotation>\n                        <xs:appinfo>\n                          <b:fieldInfo sequence_number=\"7\" justification=\"left\" />\n                        </xs:appinfo>\n                      </xs:annotation>\n                    </xs:element>\n                  </xs:sequence>\n                </xs:complexType>\n              </xs:element>\n            </xs:sequence>\n          </xs:complexType>\n        </xs:element>\n      </xs:sequence>\n    </xs:complexType>\n  </xs:element>\n</xs:schema>"),
			ContentType:            pulumi.String("application/xml"),
			IntegrationAccountName: pulumi.String("testIntegrationAccount"),
			Location:               pulumi.String("westus"),
			Metadata:               nil,
			ResourceGroupName:      pulumi.String("testResourceGroup"),
			SchemaName:             pulumi.String("testSchema"),
			SchemaType:             pulumi.String("Xml"),
			Tags: pulumi.StringMap{
				"integrationAccountSchemaName": pulumi.String("IntegrationAccountSchema8120"),
			},
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
import com.pulumi.azurenative.logic.IntegrationAccountSchema;
import com.pulumi.azurenative.logic.IntegrationAccountSchemaArgs;
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
        var integrationAccountSchema = new IntegrationAccountSchema("integrationAccountSchema", IntegrationAccountSchemaArgs.builder()        
            .content("""
<?xml version="1.0" encoding="utf-16"?>
<xs:schema xmlns:b="http://schemas.microsoft.com/BizTalk/2003" xmlns="http://Inbound_EDI.OrderFile" targetNamespace="http://Inbound_EDI.OrderFile" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:annotation>
    <xs:appinfo>
      <b:schemaInfo default_pad_char=" " count_positions_by_byte="false" parser_optimization="speed" lookahead_depth="3" suppress_empty_nodes="false" generate_empty_nodes="true" allow_early_termination="false" early_terminate_optional_fields="false" allow_message_breakup_of_infix_root="false" compile_parse_tables="false" standard="Flat File" root_reference="OrderFile" />
      <schemaEditorExtension:schemaInfo namespaceAlias="b" extensionClass="Microsoft.BizTalk.FlatFileExtension.FlatFileExtension" standardName="Flat File" xmlns:schemaEditorExtension="http://schemas.microsoft.com/BizTalk/2003/SchemaEditorExtensions" />
    </xs:appinfo>
  </xs:annotation>
  <xs:element name="OrderFile">
    <xs:annotation>
      <xs:appinfo>
        <b:recordInfo structure="delimited" preserve_delimiter_for_empty_data="true" suppress_trailing_delimiters="false" sequence_number="1" />
      </xs:appinfo>
    </xs:annotation>
    <xs:complexType>
      <xs:sequence>
        <xs:annotation>
          <xs:appinfo>
            <b:groupInfo sequence_number="0" />
          </xs:appinfo>
        </xs:annotation>
        <xs:element name="Order">
          <xs:annotation>
            <xs:appinfo>
              <b:recordInfo sequence_number="1" structure="delimited" preserve_delimiter_for_empty_data="true" suppress_trailing_delimiters="false" child_delimiter_type="hex" child_delimiter="0x0D 0x0A" child_order="infix" />
            </xs:appinfo>
          </xs:annotation>
          <xs:complexType>
            <xs:sequence>
              <xs:annotation>
                <xs:appinfo>
                  <b:groupInfo sequence_number="0" />
                </xs:appinfo>
              </xs:annotation>
              <xs:element name="Header">
                <xs:annotation>
                  <xs:appinfo>
                    <b:recordInfo sequence_number="1" structure="delimited" preserve_delimiter_for_empty_data="true" suppress_trailing_delimiters="false" child_delimiter_type="char" child_delimiter="|" child_order="infix" tag_name="HDR|" />
                  </xs:appinfo>
                </xs:annotation>
                <xs:complexType>
                  <xs:sequence>
                    <xs:annotation>
                      <xs:appinfo>
                        <b:groupInfo sequence_number="0" />
                      </xs:appinfo>
                    </xs:annotation>
                    <xs:element name="PODate" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number="1" justification="left" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name="PONumber" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo justification="left" sequence_number="2" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name="CustomerID" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number="3" justification="left" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name="CustomerContactName" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number="4" justification="left" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name="CustomerContactPhone" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number="5" justification="left" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                  </xs:sequence>
                </xs:complexType>
              </xs:element>
              <xs:element minOccurs="1" maxOccurs="unbounded" name="LineItems">
                <xs:annotation>
                  <xs:appinfo>
                    <b:recordInfo sequence_number="2" structure="delimited" preserve_delimiter_for_empty_data="true" suppress_trailing_delimiters="false" child_delimiter_type="char" child_delimiter="|" child_order="infix" tag_name="DTL|" />
                  </xs:appinfo>
                </xs:annotation>
                <xs:complexType>
                  <xs:sequence>
                    <xs:annotation>
                      <xs:appinfo>
                        <b:groupInfo sequence_number="0" />
                      </xs:appinfo>
                    </xs:annotation>
                    <xs:element name="PONumber" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number="1" justification="left" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name="ItemOrdered" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number="2" justification="left" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name="Quantity" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number="3" justification="left" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name="UOM" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number="4" justification="left" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name="Price" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number="5" justification="left" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name="ExtendedPrice" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number="6" justification="left" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name="Description" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number="7" justification="left" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                  </xs:sequence>
                </xs:complexType>
              </xs:element>
            </xs:sequence>
          </xs:complexType>
        </xs:element>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>            """)
            .contentType("application/xml")
            .integrationAccountName("testIntegrationAccount")
            .location("westus")
            .metadata()
            .resourceGroupName("testResourceGroup")
            .schemaName("testSchema")
            .schemaType("Xml")
            .tags(Map.of("integrationAccountSchemaName", "IntegrationAccountSchema8120"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const integrationAccountSchema = new azure_native.logic.IntegrationAccountSchema("integrationAccountSchema", {
    content: `<?xml version="1.0" encoding="utf-16"?>
<xs:schema xmlns:b="http://schemas.microsoft.com/BizTalk/2003" xmlns="http://Inbound_EDI.OrderFile" targetNamespace="http://Inbound_EDI.OrderFile" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:annotation>
    <xs:appinfo>
      <b:schemaInfo default_pad_char=" " count_positions_by_byte="false" parser_optimization="speed" lookahead_depth="3" suppress_empty_nodes="false" generate_empty_nodes="true" allow_early_termination="false" early_terminate_optional_fields="false" allow_message_breakup_of_infix_root="false" compile_parse_tables="false" standard="Flat File" root_reference="OrderFile" />
      <schemaEditorExtension:schemaInfo namespaceAlias="b" extensionClass="Microsoft.BizTalk.FlatFileExtension.FlatFileExtension" standardName="Flat File" xmlns:schemaEditorExtension="http://schemas.microsoft.com/BizTalk/2003/SchemaEditorExtensions" />
    </xs:appinfo>
  </xs:annotation>
  <xs:element name="OrderFile">
    <xs:annotation>
      <xs:appinfo>
        <b:recordInfo structure="delimited" preserve_delimiter_for_empty_data="true" suppress_trailing_delimiters="false" sequence_number="1" />
      </xs:appinfo>
    </xs:annotation>
    <xs:complexType>
      <xs:sequence>
        <xs:annotation>
          <xs:appinfo>
            <b:groupInfo sequence_number="0" />
          </xs:appinfo>
        </xs:annotation>
        <xs:element name="Order">
          <xs:annotation>
            <xs:appinfo>
              <b:recordInfo sequence_number="1" structure="delimited" preserve_delimiter_for_empty_data="true" suppress_trailing_delimiters="false" child_delimiter_type="hex" child_delimiter="0x0D 0x0A" child_order="infix" />
            </xs:appinfo>
          </xs:annotation>
          <xs:complexType>
            <xs:sequence>
              <xs:annotation>
                <xs:appinfo>
                  <b:groupInfo sequence_number="0" />
                </xs:appinfo>
              </xs:annotation>
              <xs:element name="Header">
                <xs:annotation>
                  <xs:appinfo>
                    <b:recordInfo sequence_number="1" structure="delimited" preserve_delimiter_for_empty_data="true" suppress_trailing_delimiters="false" child_delimiter_type="char" child_delimiter="|" child_order="infix" tag_name="HDR|" />
                  </xs:appinfo>
                </xs:annotation>
                <xs:complexType>
                  <xs:sequence>
                    <xs:annotation>
                      <xs:appinfo>
                        <b:groupInfo sequence_number="0" />
                      </xs:appinfo>
                    </xs:annotation>
                    <xs:element name="PODate" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number="1" justification="left" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name="PONumber" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo justification="left" sequence_number="2" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name="CustomerID" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number="3" justification="left" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name="CustomerContactName" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number="4" justification="left" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name="CustomerContactPhone" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number="5" justification="left" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                  </xs:sequence>
                </xs:complexType>
              </xs:element>
              <xs:element minOccurs="1" maxOccurs="unbounded" name="LineItems">
                <xs:annotation>
                  <xs:appinfo>
                    <b:recordInfo sequence_number="2" structure="delimited" preserve_delimiter_for_empty_data="true" suppress_trailing_delimiters="false" child_delimiter_type="char" child_delimiter="|" child_order="infix" tag_name="DTL|" />
                  </xs:appinfo>
                </xs:annotation>
                <xs:complexType>
                  <xs:sequence>
                    <xs:annotation>
                      <xs:appinfo>
                        <b:groupInfo sequence_number="0" />
                      </xs:appinfo>
                    </xs:annotation>
                    <xs:element name="PONumber" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number="1" justification="left" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name="ItemOrdered" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number="2" justification="left" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name="Quantity" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number="3" justification="left" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name="UOM" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number="4" justification="left" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name="Price" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number="5" justification="left" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name="ExtendedPrice" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number="6" justification="left" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name="Description" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number="7" justification="left" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                  </xs:sequence>
                </xs:complexType>
              </xs:element>
            </xs:sequence>
          </xs:complexType>
        </xs:element>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>`,
    contentType: "application/xml",
    integrationAccountName: "testIntegrationAccount",
    location: "westus",
    metadata: {},
    resourceGroupName: "testResourceGroup",
    schemaName: "testSchema",
    schemaType: "Xml",
    tags: {
        integrationAccountSchemaName: "IntegrationAccountSchema8120",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

integration_account_schema = azure_native.logic.IntegrationAccountSchema("integrationAccountSchema",
    content="""<?xml version="1.0" encoding="utf-16"?>
<xs:schema xmlns:b="http://schemas.microsoft.com/BizTalk/2003" xmlns="http://Inbound_EDI.OrderFile" targetNamespace="http://Inbound_EDI.OrderFile" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:annotation>
    <xs:appinfo>
      <b:schemaInfo default_pad_char=" " count_positions_by_byte="false" parser_optimization="speed" lookahead_depth="3" suppress_empty_nodes="false" generate_empty_nodes="true" allow_early_termination="false" early_terminate_optional_fields="false" allow_message_breakup_of_infix_root="false" compile_parse_tables="false" standard="Flat File" root_reference="OrderFile" />
      <schemaEditorExtension:schemaInfo namespaceAlias="b" extensionClass="Microsoft.BizTalk.FlatFileExtension.FlatFileExtension" standardName="Flat File" xmlns:schemaEditorExtension="http://schemas.microsoft.com/BizTalk/2003/SchemaEditorExtensions" />
    </xs:appinfo>
  </xs:annotation>
  <xs:element name="OrderFile">
    <xs:annotation>
      <xs:appinfo>
        <b:recordInfo structure="delimited" preserve_delimiter_for_empty_data="true" suppress_trailing_delimiters="false" sequence_number="1" />
      </xs:appinfo>
    </xs:annotation>
    <xs:complexType>
      <xs:sequence>
        <xs:annotation>
          <xs:appinfo>
            <b:groupInfo sequence_number="0" />
          </xs:appinfo>
        </xs:annotation>
        <xs:element name="Order">
          <xs:annotation>
            <xs:appinfo>
              <b:recordInfo sequence_number="1" structure="delimited" preserve_delimiter_for_empty_data="true" suppress_trailing_delimiters="false" child_delimiter_type="hex" child_delimiter="0x0D 0x0A" child_order="infix" />
            </xs:appinfo>
          </xs:annotation>
          <xs:complexType>
            <xs:sequence>
              <xs:annotation>
                <xs:appinfo>
                  <b:groupInfo sequence_number="0" />
                </xs:appinfo>
              </xs:annotation>
              <xs:element name="Header">
                <xs:annotation>
                  <xs:appinfo>
                    <b:recordInfo sequence_number="1" structure="delimited" preserve_delimiter_for_empty_data="true" suppress_trailing_delimiters="false" child_delimiter_type="char" child_delimiter="|" child_order="infix" tag_name="HDR|" />
                  </xs:appinfo>
                </xs:annotation>
                <xs:complexType>
                  <xs:sequence>
                    <xs:annotation>
                      <xs:appinfo>
                        <b:groupInfo sequence_number="0" />
                      </xs:appinfo>
                    </xs:annotation>
                    <xs:element name="PODate" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number="1" justification="left" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name="PONumber" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo justification="left" sequence_number="2" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name="CustomerID" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number="3" justification="left" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name="CustomerContactName" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number="4" justification="left" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name="CustomerContactPhone" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number="5" justification="left" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                  </xs:sequence>
                </xs:complexType>
              </xs:element>
              <xs:element minOccurs="1" maxOccurs="unbounded" name="LineItems">
                <xs:annotation>
                  <xs:appinfo>
                    <b:recordInfo sequence_number="2" structure="delimited" preserve_delimiter_for_empty_data="true" suppress_trailing_delimiters="false" child_delimiter_type="char" child_delimiter="|" child_order="infix" tag_name="DTL|" />
                  </xs:appinfo>
                </xs:annotation>
                <xs:complexType>
                  <xs:sequence>
                    <xs:annotation>
                      <xs:appinfo>
                        <b:groupInfo sequence_number="0" />
                      </xs:appinfo>
                    </xs:annotation>
                    <xs:element name="PONumber" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number="1" justification="left" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name="ItemOrdered" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number="2" justification="left" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name="Quantity" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number="3" justification="left" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name="UOM" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number="4" justification="left" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name="Price" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number="5" justification="left" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name="ExtendedPrice" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number="6" justification="left" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                    <xs:element name="Description" type="xs:string">
                      <xs:annotation>
                        <xs:appinfo>
                          <b:fieldInfo sequence_number="7" justification="left" />
                        </xs:appinfo>
                      </xs:annotation>
                    </xs:element>
                  </xs:sequence>
                </xs:complexType>
              </xs:element>
            </xs:sequence>
          </xs:complexType>
        </xs:element>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>""",
    content_type="application/xml",
    integration_account_name="testIntegrationAccount",
    location="westus",
    metadata={},
    resource_group_name="testResourceGroup",
    schema_name="testSchema",
    schema_type="Xml",
    tags={
        "integrationAccountSchemaName": "IntegrationAccountSchema8120",
    })

```

```yaml
resources:
  integrationAccountSchema:
    type: azure-native:logic:IntegrationAccountSchema
    properties:
      content: "<?xml version=\"1.0\" encoding=\"utf-16\"?>\r\n<xs:schema xmlns:b=\"http://schemas.microsoft.com/BizTalk/2003\" xmlns=\"http://Inbound_EDI.OrderFile\" targetNamespace=\"http://Inbound_EDI.OrderFile\" xmlns:xs=\"http://www.w3.org/2001/XMLSchema\">\r\n  <xs:annotation>\r\n    <xs:appinfo>\r\n      <b:schemaInfo default_pad_char=\" \" count_positions_by_byte=\"false\" parser_optimization=\"speed\" lookahead_depth=\"3\" suppress_empty_nodes=\"false\" generate_empty_nodes=\"true\" allow_early_termination=\"false\" early_terminate_optional_fields=\"false\" allow_message_breakup_of_infix_root=\"false\" compile_parse_tables=\"false\" standard=\"Flat File\" root_reference=\"OrderFile\" />\r\n      <schemaEditorExtension:schemaInfo namespaceAlias=\"b\" extensionClass=\"Microsoft.BizTalk.FlatFileExtension.FlatFileExtension\" standardName=\"Flat File\" xmlns:schemaEditorExtension=\"http://schemas.microsoft.com/BizTalk/2003/SchemaEditorExtensions\" />\r\n    </xs:appinfo>\r\n  </xs:annotation>\r\n  <xs:element name=\"OrderFile\">\r\n    <xs:annotation>\r\n      <xs:appinfo>\r\n        <b:recordInfo structure=\"delimited\" preserve_delimiter_for_empty_data=\"true\" suppress_trailing_delimiters=\"false\" sequence_number=\"1\" />\r\n      </xs:appinfo>\r\n    </xs:annotation>\r\n    <xs:complexType>\r\n      <xs:sequence>\r\n        <xs:annotation>\r\n          <xs:appinfo>\r\n            <b:groupInfo sequence_number=\"0\" />\r\n          </xs:appinfo>\r\n        </xs:annotation>\r\n        <xs:element name=\"Order\">\r\n          <xs:annotation>\r\n            <xs:appinfo>\r\n              <b:recordInfo sequence_number=\"1\" structure=\"delimited\" preserve_delimiter_for_empty_data=\"true\" suppress_trailing_delimiters=\"false\" child_delimiter_type=\"hex\" child_delimiter=\"0x0D 0x0A\" child_order=\"infix\" />\r\n            </xs:appinfo>\r\n          </xs:annotation>\r\n          <xs:complexType>\r\n            <xs:sequence>\r\n              <xs:annotation>\r\n                <xs:appinfo>\r\n                  <b:groupInfo sequence_number=\"0\" />\r\n                </xs:appinfo>\r\n              </xs:annotation>\r\n              <xs:element name=\"Header\">\r\n                <xs:annotation>\r\n                  <xs:appinfo>\r\n                    <b:recordInfo sequence_number=\"1\" structure=\"delimited\" preserve_delimiter_for_empty_data=\"true\" suppress_trailing_delimiters=\"false\" child_delimiter_type=\"char\" child_delimiter=\"|\" child_order=\"infix\" tag_name=\"HDR|\" />\r\n                  </xs:appinfo>\r\n                </xs:annotation>\r\n                <xs:complexType>\r\n                  <xs:sequence>\r\n                    <xs:annotation>\r\n                      <xs:appinfo>\r\n                        <b:groupInfo sequence_number=\"0\" />\r\n                      </xs:appinfo>\r\n                    </xs:annotation>\r\n                    <xs:element name=\"PODate\" type=\"xs:string\">\r\n                      <xs:annotation>\r\n                        <xs:appinfo>\r\n                          <b:fieldInfo sequence_number=\"1\" justification=\"left\" />\r\n                        </xs:appinfo>\r\n                      </xs:annotation>\r\n                    </xs:element>\r\n                    <xs:element name=\"PONumber\" type=\"xs:string\">\r\n                      <xs:annotation>\r\n                        <xs:appinfo>\r\n                          <b:fieldInfo justification=\"left\" sequence_number=\"2\" />\r\n                        </xs:appinfo>\r\n                      </xs:annotation>\r\n                    </xs:element>\r\n                    <xs:element name=\"CustomerID\" type=\"xs:string\">\r\n                      <xs:annotation>\r\n                        <xs:appinfo>\r\n                          <b:fieldInfo sequence_number=\"3\" justification=\"left\" />\r\n                        </xs:appinfo>\r\n                      </xs:annotation>\r\n                    </xs:element>\r\n                    <xs:element name=\"CustomerContactName\" type=\"xs:string\">\r\n                      <xs:annotation>\r\n                        <xs:appinfo>\r\n                          <b:fieldInfo sequence_number=\"4\" justification=\"left\" />\r\n                        </xs:appinfo>\r\n                      </xs:annotation>\r\n                    </xs:element>\r\n                    <xs:element name=\"CustomerContactPhone\" type=\"xs:string\">\r\n                      <xs:annotation>\r\n                        <xs:appinfo>\r\n                          <b:fieldInfo sequence_number=\"5\" justification=\"left\" />\r\n                        </xs:appinfo>\r\n                      </xs:annotation>\r\n                    </xs:element>\r\n                  </xs:sequence>\r\n                </xs:complexType>\r\n              </xs:element>\r\n              <xs:element minOccurs=\"1\" maxOccurs=\"unbounded\" name=\"LineItems\">\r\n                <xs:annotation>\r\n                  <xs:appinfo>\r\n                    <b:recordInfo sequence_number=\"2\" structure=\"delimited\" preserve_delimiter_for_empty_data=\"true\" suppress_trailing_delimiters=\"false\" child_delimiter_type=\"char\" child_delimiter=\"|\" child_order=\"infix\" tag_name=\"DTL|\" />\r\n                  </xs:appinfo>\r\n                </xs:annotation>\r\n                <xs:complexType>\r\n                  <xs:sequence>\r\n                    <xs:annotation>\r\n                      <xs:appinfo>\r\n                        <b:groupInfo sequence_number=\"0\" />\r\n                      </xs:appinfo>\r\n                    </xs:annotation>\r\n                    <xs:element name=\"PONumber\" type=\"xs:string\">\r\n                      <xs:annotation>\r\n                        <xs:appinfo>\r\n                          <b:fieldInfo sequence_number=\"1\" justification=\"left\" />\r\n                        </xs:appinfo>\r\n                      </xs:annotation>\r\n                    </xs:element>\r\n                    <xs:element name=\"ItemOrdered\" type=\"xs:string\">\r\n                      <xs:annotation>\r\n                        <xs:appinfo>\r\n                          <b:fieldInfo sequence_number=\"2\" justification=\"left\" />\r\n                        </xs:appinfo>\r\n                      </xs:annotation>\r\n                    </xs:element>\r\n                    <xs:element name=\"Quantity\" type=\"xs:string\">\r\n                      <xs:annotation>\r\n                        <xs:appinfo>\r\n                          <b:fieldInfo sequence_number=\"3\" justification=\"left\" />\r\n                        </xs:appinfo>\r\n                      </xs:annotation>\r\n                    </xs:element>\r\n                    <xs:element name=\"UOM\" type=\"xs:string\">\r\n                      <xs:annotation>\r\n                        <xs:appinfo>\r\n                          <b:fieldInfo sequence_number=\"4\" justification=\"left\" />\r\n                        </xs:appinfo>\r\n                      </xs:annotation>\r\n                    </xs:element>\r\n                    <xs:element name=\"Price\" type=\"xs:string\">\r\n                      <xs:annotation>\r\n                        <xs:appinfo>\r\n                          <b:fieldInfo sequence_number=\"5\" justification=\"left\" />\r\n                        </xs:appinfo>\r\n                      </xs:annotation>\r\n                    </xs:element>\r\n                    <xs:element name=\"ExtendedPrice\" type=\"xs:string\">\r\n                      <xs:annotation>\r\n                        <xs:appinfo>\r\n                          <b:fieldInfo sequence_number=\"6\" justification=\"left\" />\r\n                        </xs:appinfo>\r\n                      </xs:annotation>\r\n                    </xs:element>\r\n                    <xs:element name=\"Description\" type=\"xs:string\">\r\n                      <xs:annotation>\r\n                        <xs:appinfo>\r\n                          <b:fieldInfo sequence_number=\"7\" justification=\"left\" />\r\n                        </xs:appinfo>\r\n                      </xs:annotation>\r\n                    </xs:element>\r\n                  </xs:sequence>\r\n                </xs:complexType>\r\n              </xs:element>\r\n            </xs:sequence>\r\n          </xs:complexType>\r\n        </xs:element>\r\n      </xs:sequence>\r\n    </xs:complexType>\r\n  </xs:element>\r\n</xs:schema>"
      contentType: application/xml
      integrationAccountName: testIntegrationAccount
      location: westus
      metadata: {}
      resourceGroupName: testResourceGroup
      schemaName: testSchema
      schemaType: Xml
      tags:
        integrationAccountSchemaName: IntegrationAccountSchema8120

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:logic:IntegrationAccountSchema IntegrationAccountSchema5349 /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testResourceGroup/providers/Microsoft.Logic/integrationAccounts/testIntegrationAccount/schemas/testSchema 
```
