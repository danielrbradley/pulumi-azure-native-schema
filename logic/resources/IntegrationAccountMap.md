The integration account map.
API Version: 2019-05-01.
Previous API Version: 2019-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a map
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var integrationAccountMap = new AzureNative.Logic.IntegrationAccountMap("integrationAccountMap", new()
    {
        Content = @"<?xml version=""1.0"" encoding=""UTF-16""?>
<xsl:stylesheet xmlns:xsl=""http://www.w3.org/1999/XSL/Transform"" xmlns:msxsl=""urn:schemas-microsoft-com:xslt"" xmlns:var=""http://schemas.microsoft.com/BizTalk/2003/var"" exclude-result-prefixes=""msxsl var s0 userCSharp"" version=""1.0"" xmlns:ns0=""http://BizTalk_Server_Project4.StringFunctoidsDestinationSchema"" xmlns:s0=""http://BizTalk_Server_Project4.StringFunctoidsSourceSchema"" xmlns:userCSharp=""http://schemas.microsoft.com/BizTalk/2003/userCSharp"">
  <xsl:import href=""http://btsfunctoids.blob.core.windows.net/functoids/functoids.xslt"" />
  <xsl:output omit-xml-declaration=""yes"" method=""xml"" version=""1.0"" />
  <xsl:template match=""/"">
    <xsl:apply-templates select=""/s0:Root"" />
  </xsl:template>
  <xsl:template match=""/s0:Root"">
    <xsl:variable name=""var:v1"" select=""userCSharp:StringFind(string(StringFindSource/text()) , &quot;SearchString&quot;)"" />
    <xsl:variable name=""var:v2"" select=""userCSharp:StringLeft(string(StringLeftSource/text()) , &quot;2&quot;)"" />
    <xsl:variable name=""var:v3"" select=""userCSharp:StringRight(string(StringRightSource/text()) , &quot;2&quot;)"" />
    <xsl:variable name=""var:v4"" select=""userCSharp:StringUpperCase(string(UppercaseSource/text()))"" />
    <xsl:variable name=""var:v5"" select=""userCSharp:StringLowerCase(string(LowercaseSource/text()))"" />
    <xsl:variable name=""var:v6"" select=""userCSharp:StringSize(string(SizeSource/text()))"" />
    <xsl:variable name=""var:v7"" select=""userCSharp:StringSubstring(string(StringExtractSource/text()) , &quot;0&quot; , &quot;2&quot;)"" />
    <xsl:variable name=""var:v8"" select=""userCSharp:StringConcat(string(StringConcatSource/text()))"" />
    <xsl:variable name=""var:v9"" select=""userCSharp:StringTrimLeft(string(StringLeftTrimSource/text()))"" />
    <xsl:variable name=""var:v10"" select=""userCSharp:StringTrimRight(string(StringRightTrimSource/text()))"" />
    <ns0:Root>
      <StringFindDestination>
        <xsl:value-of select=""$var:v1"" />
      </StringFindDestination>
      <StringLeftDestination>
        <xsl:value-of select=""$var:v2"" />
      </StringLeftDestination>
      <StringRightDestination>
        <xsl:value-of select=""$var:v3"" />
      </StringRightDestination>
      <UppercaseDestination>
        <xsl:value-of select=""$var:v4"" />
      </UppercaseDestination>
      <LowercaseDestination>
        <xsl:value-of select=""$var:v5"" />
      </LowercaseDestination>
      <SizeDestination>
        <xsl:value-of select=""$var:v6"" />
      </SizeDestination>
      <StringExtractDestination>
        <xsl:value-of select=""$var:v7"" />
      </StringExtractDestination>
      <StringConcatDestination>
        <xsl:value-of select=""$var:v8"" />
      </StringConcatDestination>
      <StringLeftTrimDestination>
        <xsl:value-of select=""$var:v9"" />
      </StringLeftTrimDestination>
      <StringRightTrimDestination>
        <xsl:value-of select=""$var:v10"" />
      </StringRightTrimDestination>
    </ns0:Root>
  </xsl:template>
</xsl:stylesheet>",
        ContentType = "application/xml",
        IntegrationAccountName = "testIntegrationAccount",
        Location = "westus",
        MapName = "testMap",
        MapType = "Xslt",
        Metadata = null,
        ResourceGroupName = "testResourceGroup",
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
		_, err := logic.NewIntegrationAccountMap(ctx, "integrationAccountMap", &logic.IntegrationAccountMapArgs{
			Content:                pulumi.String("<?xml version=\"1.0\" encoding=\"UTF-16\"?>\n<xsl:stylesheet xmlns:xsl=\"http://www.w3.org/1999/XSL/Transform\" xmlns:msxsl=\"urn:schemas-microsoft-com:xslt\" xmlns:var=\"http://schemas.microsoft.com/BizTalk/2003/var\" exclude-result-prefixes=\"msxsl var s0 userCSharp\" version=\"1.0\" xmlns:ns0=\"http://BizTalk_Server_Project4.StringFunctoidsDestinationSchema\" xmlns:s0=\"http://BizTalk_Server_Project4.StringFunctoidsSourceSchema\" xmlns:userCSharp=\"http://schemas.microsoft.com/BizTalk/2003/userCSharp\">\n  <xsl:import href=\"http://btsfunctoids.blob.core.windows.net/functoids/functoids.xslt\" />\n  <xsl:output omit-xml-declaration=\"yes\" method=\"xml\" version=\"1.0\" />\n  <xsl:template match=\"/\">\n    <xsl:apply-templates select=\"/s0:Root\" />\n  </xsl:template>\n  <xsl:template match=\"/s0:Root\">\n    <xsl:variable name=\"var:v1\" select=\"userCSharp:StringFind(string(StringFindSource/text()) , &quot;SearchString&quot;)\" />\n    <xsl:variable name=\"var:v2\" select=\"userCSharp:StringLeft(string(StringLeftSource/text()) , &quot;2&quot;)\" />\n    <xsl:variable name=\"var:v3\" select=\"userCSharp:StringRight(string(StringRightSource/text()) , &quot;2&quot;)\" />\n    <xsl:variable name=\"var:v4\" select=\"userCSharp:StringUpperCase(string(UppercaseSource/text()))\" />\n    <xsl:variable name=\"var:v5\" select=\"userCSharp:StringLowerCase(string(LowercaseSource/text()))\" />\n    <xsl:variable name=\"var:v6\" select=\"userCSharp:StringSize(string(SizeSource/text()))\" />\n    <xsl:variable name=\"var:v7\" select=\"userCSharp:StringSubstring(string(StringExtractSource/text()) , &quot;0&quot; , &quot;2&quot;)\" />\n    <xsl:variable name=\"var:v8\" select=\"userCSharp:StringConcat(string(StringConcatSource/text()))\" />\n    <xsl:variable name=\"var:v9\" select=\"userCSharp:StringTrimLeft(string(StringLeftTrimSource/text()))\" />\n    <xsl:variable name=\"var:v10\" select=\"userCSharp:StringTrimRight(string(StringRightTrimSource/text()))\" />\n    <ns0:Root>\n      <StringFindDestination>\n        <xsl:value-of select=\"$var:v1\" />\n      </StringFindDestination>\n      <StringLeftDestination>\n        <xsl:value-of select=\"$var:v2\" />\n      </StringLeftDestination>\n      <StringRightDestination>\n        <xsl:value-of select=\"$var:v3\" />\n      </StringRightDestination>\n      <UppercaseDestination>\n        <xsl:value-of select=\"$var:v4\" />\n      </UppercaseDestination>\n      <LowercaseDestination>\n        <xsl:value-of select=\"$var:v5\" />\n      </LowercaseDestination>\n      <SizeDestination>\n        <xsl:value-of select=\"$var:v6\" />\n      </SizeDestination>\n      <StringExtractDestination>\n        <xsl:value-of select=\"$var:v7\" />\n      </StringExtractDestination>\n      <StringConcatDestination>\n        <xsl:value-of select=\"$var:v8\" />\n      </StringConcatDestination>\n      <StringLeftTrimDestination>\n        <xsl:value-of select=\"$var:v9\" />\n      </StringLeftTrimDestination>\n      <StringRightTrimDestination>\n        <xsl:value-of select=\"$var:v10\" />\n      </StringRightTrimDestination>\n    </ns0:Root>\n  </xsl:template>\n</xsl:stylesheet>"),
			ContentType:            pulumi.String("application/xml"),
			IntegrationAccountName: pulumi.String("testIntegrationAccount"),
			Location:               pulumi.String("westus"),
			MapName:                pulumi.String("testMap"),
			MapType:                pulumi.String("Xslt"),
			Metadata:               nil,
			ResourceGroupName:      pulumi.String("testResourceGroup"),
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
import com.pulumi.azurenative.logic.IntegrationAccountMap;
import com.pulumi.azurenative.logic.IntegrationAccountMapArgs;
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
        var integrationAccountMap = new IntegrationAccountMap("integrationAccountMap", IntegrationAccountMapArgs.builder()        
            .content("""
<?xml version="1.0" encoding="UTF-16"?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:msxsl="urn:schemas-microsoft-com:xslt" xmlns:var="http://schemas.microsoft.com/BizTalk/2003/var" exclude-result-prefixes="msxsl var s0 userCSharp" version="1.0" xmlns:ns0="http://BizTalk_Server_Project4.StringFunctoidsDestinationSchema" xmlns:s0="http://BizTalk_Server_Project4.StringFunctoidsSourceSchema" xmlns:userCSharp="http://schemas.microsoft.com/BizTalk/2003/userCSharp">
  <xsl:import href="http://btsfunctoids.blob.core.windows.net/functoids/functoids.xslt" />
  <xsl:output omit-xml-declaration="yes" method="xml" version="1.0" />
  <xsl:template match="/">
    <xsl:apply-templates select="/s0:Root" />
  </xsl:template>
  <xsl:template match="/s0:Root">
    <xsl:variable name="var:v1" select="userCSharp:StringFind(string(StringFindSource/text()) , &quot;SearchString&quot;)" />
    <xsl:variable name="var:v2" select="userCSharp:StringLeft(string(StringLeftSource/text()) , &quot;2&quot;)" />
    <xsl:variable name="var:v3" select="userCSharp:StringRight(string(StringRightSource/text()) , &quot;2&quot;)" />
    <xsl:variable name="var:v4" select="userCSharp:StringUpperCase(string(UppercaseSource/text()))" />
    <xsl:variable name="var:v5" select="userCSharp:StringLowerCase(string(LowercaseSource/text()))" />
    <xsl:variable name="var:v6" select="userCSharp:StringSize(string(SizeSource/text()))" />
    <xsl:variable name="var:v7" select="userCSharp:StringSubstring(string(StringExtractSource/text()) , &quot;0&quot; , &quot;2&quot;)" />
    <xsl:variable name="var:v8" select="userCSharp:StringConcat(string(StringConcatSource/text()))" />
    <xsl:variable name="var:v9" select="userCSharp:StringTrimLeft(string(StringLeftTrimSource/text()))" />
    <xsl:variable name="var:v10" select="userCSharp:StringTrimRight(string(StringRightTrimSource/text()))" />
    <ns0:Root>
      <StringFindDestination>
        <xsl:value-of select="$var:v1" />
      </StringFindDestination>
      <StringLeftDestination>
        <xsl:value-of select="$var:v2" />
      </StringLeftDestination>
      <StringRightDestination>
        <xsl:value-of select="$var:v3" />
      </StringRightDestination>
      <UppercaseDestination>
        <xsl:value-of select="$var:v4" />
      </UppercaseDestination>
      <LowercaseDestination>
        <xsl:value-of select="$var:v5" />
      </LowercaseDestination>
      <SizeDestination>
        <xsl:value-of select="$var:v6" />
      </SizeDestination>
      <StringExtractDestination>
        <xsl:value-of select="$var:v7" />
      </StringExtractDestination>
      <StringConcatDestination>
        <xsl:value-of select="$var:v8" />
      </StringConcatDestination>
      <StringLeftTrimDestination>
        <xsl:value-of select="$var:v9" />
      </StringLeftTrimDestination>
      <StringRightTrimDestination>
        <xsl:value-of select="$var:v10" />
      </StringRightTrimDestination>
    </ns0:Root>
  </xsl:template>
</xsl:stylesheet>            """)
            .contentType("application/xml")
            .integrationAccountName("testIntegrationAccount")
            .location("westus")
            .mapName("testMap")
            .mapType("Xslt")
            .metadata()
            .resourceGroupName("testResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const integrationAccountMap = new azure_native.logic.IntegrationAccountMap("integrationAccountMap", {
    content: `<?xml version="1.0" encoding="UTF-16"?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:msxsl="urn:schemas-microsoft-com:xslt" xmlns:var="http://schemas.microsoft.com/BizTalk/2003/var" exclude-result-prefixes="msxsl var s0 userCSharp" version="1.0" xmlns:ns0="http://BizTalk_Server_Project4.StringFunctoidsDestinationSchema" xmlns:s0="http://BizTalk_Server_Project4.StringFunctoidsSourceSchema" xmlns:userCSharp="http://schemas.microsoft.com/BizTalk/2003/userCSharp">
  <xsl:import href="http://btsfunctoids.blob.core.windows.net/functoids/functoids.xslt" />
  <xsl:output omit-xml-declaration="yes" method="xml" version="1.0" />
  <xsl:template match="/">
    <xsl:apply-templates select="/s0:Root" />
  </xsl:template>
  <xsl:template match="/s0:Root">
    <xsl:variable name="var:v1" select="userCSharp:StringFind(string(StringFindSource/text()) , &quot;SearchString&quot;)" />
    <xsl:variable name="var:v2" select="userCSharp:StringLeft(string(StringLeftSource/text()) , &quot;2&quot;)" />
    <xsl:variable name="var:v3" select="userCSharp:StringRight(string(StringRightSource/text()) , &quot;2&quot;)" />
    <xsl:variable name="var:v4" select="userCSharp:StringUpperCase(string(UppercaseSource/text()))" />
    <xsl:variable name="var:v5" select="userCSharp:StringLowerCase(string(LowercaseSource/text()))" />
    <xsl:variable name="var:v6" select="userCSharp:StringSize(string(SizeSource/text()))" />
    <xsl:variable name="var:v7" select="userCSharp:StringSubstring(string(StringExtractSource/text()) , &quot;0&quot; , &quot;2&quot;)" />
    <xsl:variable name="var:v8" select="userCSharp:StringConcat(string(StringConcatSource/text()))" />
    <xsl:variable name="var:v9" select="userCSharp:StringTrimLeft(string(StringLeftTrimSource/text()))" />
    <xsl:variable name="var:v10" select="userCSharp:StringTrimRight(string(StringRightTrimSource/text()))" />
    <ns0:Root>
      <StringFindDestination>
        <xsl:value-of select="$var:v1" />
      </StringFindDestination>
      <StringLeftDestination>
        <xsl:value-of select="$var:v2" />
      </StringLeftDestination>
      <StringRightDestination>
        <xsl:value-of select="$var:v3" />
      </StringRightDestination>
      <UppercaseDestination>
        <xsl:value-of select="$var:v4" />
      </UppercaseDestination>
      <LowercaseDestination>
        <xsl:value-of select="$var:v5" />
      </LowercaseDestination>
      <SizeDestination>
        <xsl:value-of select="$var:v6" />
      </SizeDestination>
      <StringExtractDestination>
        <xsl:value-of select="$var:v7" />
      </StringExtractDestination>
      <StringConcatDestination>
        <xsl:value-of select="$var:v8" />
      </StringConcatDestination>
      <StringLeftTrimDestination>
        <xsl:value-of select="$var:v9" />
      </StringLeftTrimDestination>
      <StringRightTrimDestination>
        <xsl:value-of select="$var:v10" />
      </StringRightTrimDestination>
    </ns0:Root>
  </xsl:template>
</xsl:stylesheet>`,
    contentType: "application/xml",
    integrationAccountName: "testIntegrationAccount",
    location: "westus",
    mapName: "testMap",
    mapType: "Xslt",
    metadata: {},
    resourceGroupName: "testResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

integration_account_map = azure_native.logic.IntegrationAccountMap("integrationAccountMap",
    content="""<?xml version="1.0" encoding="UTF-16"?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:msxsl="urn:schemas-microsoft-com:xslt" xmlns:var="http://schemas.microsoft.com/BizTalk/2003/var" exclude-result-prefixes="msxsl var s0 userCSharp" version="1.0" xmlns:ns0="http://BizTalk_Server_Project4.StringFunctoidsDestinationSchema" xmlns:s0="http://BizTalk_Server_Project4.StringFunctoidsSourceSchema" xmlns:userCSharp="http://schemas.microsoft.com/BizTalk/2003/userCSharp">
  <xsl:import href="http://btsfunctoids.blob.core.windows.net/functoids/functoids.xslt" />
  <xsl:output omit-xml-declaration="yes" method="xml" version="1.0" />
  <xsl:template match="/">
    <xsl:apply-templates select="/s0:Root" />
  </xsl:template>
  <xsl:template match="/s0:Root">
    <xsl:variable name="var:v1" select="userCSharp:StringFind(string(StringFindSource/text()) , &quot;SearchString&quot;)" />
    <xsl:variable name="var:v2" select="userCSharp:StringLeft(string(StringLeftSource/text()) , &quot;2&quot;)" />
    <xsl:variable name="var:v3" select="userCSharp:StringRight(string(StringRightSource/text()) , &quot;2&quot;)" />
    <xsl:variable name="var:v4" select="userCSharp:StringUpperCase(string(UppercaseSource/text()))" />
    <xsl:variable name="var:v5" select="userCSharp:StringLowerCase(string(LowercaseSource/text()))" />
    <xsl:variable name="var:v6" select="userCSharp:StringSize(string(SizeSource/text()))" />
    <xsl:variable name="var:v7" select="userCSharp:StringSubstring(string(StringExtractSource/text()) , &quot;0&quot; , &quot;2&quot;)" />
    <xsl:variable name="var:v8" select="userCSharp:StringConcat(string(StringConcatSource/text()))" />
    <xsl:variable name="var:v9" select="userCSharp:StringTrimLeft(string(StringLeftTrimSource/text()))" />
    <xsl:variable name="var:v10" select="userCSharp:StringTrimRight(string(StringRightTrimSource/text()))" />
    <ns0:Root>
      <StringFindDestination>
        <xsl:value-of select="$var:v1" />
      </StringFindDestination>
      <StringLeftDestination>
        <xsl:value-of select="$var:v2" />
      </StringLeftDestination>
      <StringRightDestination>
        <xsl:value-of select="$var:v3" />
      </StringRightDestination>
      <UppercaseDestination>
        <xsl:value-of select="$var:v4" />
      </UppercaseDestination>
      <LowercaseDestination>
        <xsl:value-of select="$var:v5" />
      </LowercaseDestination>
      <SizeDestination>
        <xsl:value-of select="$var:v6" />
      </SizeDestination>
      <StringExtractDestination>
        <xsl:value-of select="$var:v7" />
      </StringExtractDestination>
      <StringConcatDestination>
        <xsl:value-of select="$var:v8" />
      </StringConcatDestination>
      <StringLeftTrimDestination>
        <xsl:value-of select="$var:v9" />
      </StringLeftTrimDestination>
      <StringRightTrimDestination>
        <xsl:value-of select="$var:v10" />
      </StringRightTrimDestination>
    </ns0:Root>
  </xsl:template>
</xsl:stylesheet>""",
    content_type="application/xml",
    integration_account_name="testIntegrationAccount",
    location="westus",
    map_name="testMap",
    map_type="Xslt",
    metadata={},
    resource_group_name="testResourceGroup")

```

```yaml
resources:
  integrationAccountMap:
    type: azure-native:logic:IntegrationAccountMap
    properties:
      content: "<?xml version=\"1.0\" encoding=\"UTF-16\"?>\r\n<xsl:stylesheet xmlns:xsl=\"http://www.w3.org/1999/XSL/Transform\" xmlns:msxsl=\"urn:schemas-microsoft-com:xslt\" xmlns:var=\"http://schemas.microsoft.com/BizTalk/2003/var\" exclude-result-prefixes=\"msxsl var s0 userCSharp\" version=\"1.0\" xmlns:ns0=\"http://BizTalk_Server_Project4.StringFunctoidsDestinationSchema\" xmlns:s0=\"http://BizTalk_Server_Project4.StringFunctoidsSourceSchema\" xmlns:userCSharp=\"http://schemas.microsoft.com/BizTalk/2003/userCSharp\">\r\n  <xsl:import href=\"http://btsfunctoids.blob.core.windows.net/functoids/functoids.xslt\" />\r\n  <xsl:output omit-xml-declaration=\"yes\" method=\"xml\" version=\"1.0\" />\r\n  <xsl:template match=\"/\">\r\n    <xsl:apply-templates select=\"/s0:Root\" />\r\n  </xsl:template>\r\n  <xsl:template match=\"/s0:Root\">\r\n    <xsl:variable name=\"var:v1\" select=\"userCSharp:StringFind(string(StringFindSource/text()) , &quot;SearchString&quot;)\" />\r\n    <xsl:variable name=\"var:v2\" select=\"userCSharp:StringLeft(string(StringLeftSource/text()) , &quot;2&quot;)\" />\r\n    <xsl:variable name=\"var:v3\" select=\"userCSharp:StringRight(string(StringRightSource/text()) , &quot;2&quot;)\" />\r\n    <xsl:variable name=\"var:v4\" select=\"userCSharp:StringUpperCase(string(UppercaseSource/text()))\" />\r\n    <xsl:variable name=\"var:v5\" select=\"userCSharp:StringLowerCase(string(LowercaseSource/text()))\" />\r\n    <xsl:variable name=\"var:v6\" select=\"userCSharp:StringSize(string(SizeSource/text()))\" />\r\n    <xsl:variable name=\"var:v7\" select=\"userCSharp:StringSubstring(string(StringExtractSource/text()) , &quot;0&quot; , &quot;2&quot;)\" />\r\n    <xsl:variable name=\"var:v8\" select=\"userCSharp:StringConcat(string(StringConcatSource/text()))\" />\r\n    <xsl:variable name=\"var:v9\" select=\"userCSharp:StringTrimLeft(string(StringLeftTrimSource/text()))\" />\r\n    <xsl:variable name=\"var:v10\" select=\"userCSharp:StringTrimRight(string(StringRightTrimSource/text()))\" />\r\n    <ns0:Root>\r\n      <StringFindDestination>\r\n        <xsl:value-of select=\"$var:v1\" />\r\n      </StringFindDestination>\r\n      <StringLeftDestination>\r\n        <xsl:value-of select=\"$var:v2\" />\r\n      </StringLeftDestination>\r\n      <StringRightDestination>\r\n        <xsl:value-of select=\"$var:v3\" />\r\n      </StringRightDestination>\r\n      <UppercaseDestination>\r\n        <xsl:value-of select=\"$var:v4\" />\r\n      </UppercaseDestination>\r\n      <LowercaseDestination>\r\n        <xsl:value-of select=\"$var:v5\" />\r\n      </LowercaseDestination>\r\n      <SizeDestination>\r\n        <xsl:value-of select=\"$var:v6\" />\r\n      </SizeDestination>\r\n      <StringExtractDestination>\r\n        <xsl:value-of select=\"$var:v7\" />\r\n      </StringExtractDestination>\r\n      <StringConcatDestination>\r\n        <xsl:value-of select=\"$var:v8\" />\r\n      </StringConcatDestination>\r\n      <StringLeftTrimDestination>\r\n        <xsl:value-of select=\"$var:v9\" />\r\n      </StringLeftTrimDestination>\r\n      <StringRightTrimDestination>\r\n        <xsl:value-of select=\"$var:v10\" />\r\n      </StringRightTrimDestination>\r\n    </ns0:Root>\r\n  </xsl:template>\r\n</xsl:stylesheet>"
      contentType: application/xml
      integrationAccountName: testIntegrationAccount
      location: westus
      mapName: testMap
      mapType: Xslt
      metadata: {}
      resourceGroupName: testResourceGroup

```

{{% /example %}}
{{% example %}}
### Create or update a map larger than 4 MB
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var integrationAccountMap = new AzureNative.Logic.IntegrationAccountMap("integrationAccountMap", new()
    {
        ContentType = "application/xml",
        IntegrationAccountName = "testIntegrationAccount",
        Location = "westus",
        MapName = "testMap",
        MapType = "Xslt",
        Metadata = null,
        ResourceGroupName = "testResourceGroup",
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
		_, err := logic.NewIntegrationAccountMap(ctx, "integrationAccountMap", &logic.IntegrationAccountMapArgs{
			ContentType:            pulumi.String("application/xml"),
			IntegrationAccountName: pulumi.String("testIntegrationAccount"),
			Location:               pulumi.String("westus"),
			MapName:                pulumi.String("testMap"),
			MapType:                pulumi.String("Xslt"),
			Metadata:               nil,
			ResourceGroupName:      pulumi.String("testResourceGroup"),
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
import com.pulumi.azurenative.logic.IntegrationAccountMap;
import com.pulumi.azurenative.logic.IntegrationAccountMapArgs;
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
        var integrationAccountMap = new IntegrationAccountMap("integrationAccountMap", IntegrationAccountMapArgs.builder()        
            .contentType("application/xml")
            .integrationAccountName("testIntegrationAccount")
            .location("westus")
            .mapName("testMap")
            .mapType("Xslt")
            .metadata()
            .resourceGroupName("testResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const integrationAccountMap = new azure_native.logic.IntegrationAccountMap("integrationAccountMap", {
    contentType: "application/xml",
    integrationAccountName: "testIntegrationAccount",
    location: "westus",
    mapName: "testMap",
    mapType: "Xslt",
    metadata: {},
    resourceGroupName: "testResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

integration_account_map = azure_native.logic.IntegrationAccountMap("integrationAccountMap",
    content_type="application/xml",
    integration_account_name="testIntegrationAccount",
    location="westus",
    map_name="testMap",
    map_type="Xslt",
    metadata={},
    resource_group_name="testResourceGroup")

```

```yaml
resources:
  integrationAccountMap:
    type: azure-native:logic:IntegrationAccountMap
    properties:
      contentType: application/xml
      integrationAccountName: testIntegrationAccount
      location: westus
      mapName: testMap
      mapType: Xslt
      metadata: {}
      resourceGroupName: testResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:logic:IntegrationAccountMap testMap /subscriptions/<Azure-subscription-ID>/resourceGroups/refresh/providers/Microsoft.Logic/integrationAccounts/testIntegrationAccount/maps/testMap 
```
