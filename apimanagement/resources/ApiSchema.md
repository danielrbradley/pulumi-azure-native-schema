API Schema Contract details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateApiSchema
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var apiSchema = new AzureNative.ApiManagement.ApiSchema("apiSchema", new()
    {
        ApiId = "59d6bb8f1f7fab13dc67ec9b",
        ContentType = "application/vnd.ms-azure-apim.xsd+xml",
        ResourceGroupName = "rg1",
        SchemaId = "ec12520d-9d48-4e7b-8f39-698ca2ac63f1",
        ServiceName = "apimService1",
        Value = @"<s:schema elementFormDefault=""qualified"" targetNamespace=""http://ws.cdyne.com/WeatherWS/"" xmlns:tns=""http://ws.cdyne.com/WeatherWS/"" xmlns:s=""http://www.w3.org/2001/XMLSchema"" xmlns:soap12=""http://schemas.xmlsoap.org/wsdl/soap12/"" xmlns:mime=""http://schemas.xmlsoap.org/wsdl/mime/"" xmlns:soap=""http://schemas.xmlsoap.org/wsdl/soap/"" xmlns:tm=""http://microsoft.com/wsdl/mime/textMatching/"" xmlns:http=""http://schemas.xmlsoap.org/wsdl/http/"" xmlns:soapenc=""http://schemas.xmlsoap.org/soap/encoding/"" xmlns:wsdl=""http://schemas.xmlsoap.org/wsdl/"" xmlns:apim-wsdltns=""http://ws.cdyne.com/WeatherWS/"">
  <s:element name=""GetWeatherInformation"">
    <s:complexType />
  </s:element>
  <s:element name=""GetWeatherInformationResponse"">
    <s:complexType>
      <s:sequence>
        <s:element minOccurs=""0"" maxOccurs=""1"" name=""GetWeatherInformationResult"" type=""tns:ArrayOfWeatherDescription"" />
      </s:sequence>
    </s:complexType>
  </s:element>
  <s:complexType name=""ArrayOfWeatherDescription"">
    <s:sequence>
      <s:element minOccurs=""0"" maxOccurs=""unbounded"" name=""WeatherDescription"" type=""tns:WeatherDescription"" />
    </s:sequence>
  </s:complexType>
  <s:complexType name=""WeatherDescription"">
    <s:sequence>
      <s:element minOccurs=""1"" maxOccurs=""1"" name=""WeatherID"" type=""s:short"" />
      <s:element minOccurs=""0"" maxOccurs=""1"" name=""Description"" type=""s:string"" />
      <s:element minOccurs=""0"" maxOccurs=""1"" name=""PictureURL"" type=""s:string"" />
    </s:sequence>
  </s:complexType>
  <s:element name=""GetCityForecastByZIP"">
    <s:complexType>
      <s:sequence>
        <s:element minOccurs=""0"" maxOccurs=""1"" name=""ZIP"" type=""s:string"" />
      </s:sequence>
    </s:complexType>
  </s:element>
  <s:element name=""GetCityForecastByZIPResponse"">
    <s:complexType>
      <s:sequence>
        <s:element minOccurs=""0"" maxOccurs=""1"" name=""GetCityForecastByZIPResult"" type=""tns:ForecastReturn"" />
      </s:sequence>
    </s:complexType>
  </s:element>
  <s:complexType name=""ForecastReturn"">
    <s:sequence>
      <s:element minOccurs=""1"" maxOccurs=""1"" name=""Success"" type=""s:boolean"" />
      <s:element minOccurs=""0"" maxOccurs=""1"" name=""ResponseText"" type=""s:string"" />
      <s:element minOccurs=""0"" maxOccurs=""1"" name=""State"" type=""s:string"" />
      <s:element minOccurs=""0"" maxOccurs=""1"" name=""City"" type=""s:string"" />
      <s:element minOccurs=""0"" maxOccurs=""1"" name=""WeatherStationCity"" type=""s:string"" />
      <s:element minOccurs=""0"" maxOccurs=""1"" name=""ForecastResult"" type=""tns:ArrayOfForecast"" />
    </s:sequence>
  </s:complexType>
  <s:complexType name=""ArrayOfForecast"">
    <s:sequence>
      <s:element minOccurs=""0"" maxOccurs=""unbounded"" name=""Forecast"" nillable=""true"" type=""tns:Forecast"" />
    </s:sequence>
  </s:complexType>
  <s:complexType name=""Forecast"">
    <s:sequence>
      <s:element minOccurs=""1"" maxOccurs=""1"" name=""Date"" type=""s:dateTime"" />
      <s:element minOccurs=""1"" maxOccurs=""1"" name=""WeatherID"" type=""s:short"" />
      <s:element minOccurs=""0"" maxOccurs=""1"" name=""Desciption"" type=""s:string"" />
      <s:element minOccurs=""1"" maxOccurs=""1"" name=""Temperatures"" type=""tns:temp"" />
      <s:element minOccurs=""1"" maxOccurs=""1"" name=""ProbabilityOfPrecipiation"" type=""tns:POP"" />
    </s:sequence>
  </s:complexType>
  <s:complexType name=""temp"">
    <s:sequence>
      <s:element minOccurs=""0"" maxOccurs=""1"" name=""MorningLow"" type=""s:string"" />
      <s:element minOccurs=""0"" maxOccurs=""1"" name=""DaytimeHigh"" type=""s:string"" />
    </s:sequence>
  </s:complexType>
  <s:complexType name=""POP"">
    <s:sequence>
      <s:element minOccurs=""0"" maxOccurs=""1"" name=""Nighttime"" type=""s:string"" />
      <s:element minOccurs=""0"" maxOccurs=""1"" name=""Daytime"" type=""s:string"" />
    </s:sequence>
  </s:complexType>
  <s:element name=""GetCityWeatherByZIP"">
    <s:complexType>
      <s:sequence>
        <s:element minOccurs=""0"" maxOccurs=""1"" name=""ZIP"" type=""s:string"" />
      </s:sequence>
    </s:complexType>
  </s:element>
  <s:element name=""GetCityWeatherByZIPResponse"">
    <s:complexType>
      <s:sequence>
        <s:element minOccurs=""1"" maxOccurs=""1"" name=""GetCityWeatherByZIPResult"" type=""tns:WeatherReturn"" />
      </s:sequence>
    </s:complexType>
  </s:element>
  <s:complexType name=""WeatherReturn"">
    <s:sequence>
      <s:element minOccurs=""1"" maxOccurs=""1"" name=""Success"" type=""s:boolean"" />
      <s:element minOccurs=""0"" maxOccurs=""1"" name=""ResponseText"" type=""s:string"" />
      <s:element minOccurs=""0"" maxOccurs=""1"" name=""State"" type=""s:string"" />
      <s:element minOccurs=""0"" maxOccurs=""1"" name=""City"" type=""s:string"" />
      <s:element minOccurs=""0"" maxOccurs=""1"" name=""WeatherStationCity"" type=""s:string"" />
      <s:element minOccurs=""1"" maxOccurs=""1"" name=""WeatherID"" type=""s:short"" />
      <s:element minOccurs=""0"" maxOccurs=""1"" name=""Description"" type=""s:string"" />
      <s:element minOccurs=""0"" maxOccurs=""1"" name=""Temperature"" type=""s:string"" />
      <s:element minOccurs=""0"" maxOccurs=""1"" name=""RelativeHumidity"" type=""s:string"" />
      <s:element minOccurs=""0"" maxOccurs=""1"" name=""Wind"" type=""s:string"" />
      <s:element minOccurs=""0"" maxOccurs=""1"" name=""Pressure"" type=""s:string"" />
      <s:element minOccurs=""0"" maxOccurs=""1"" name=""Visibility"" type=""s:string"" />
      <s:element minOccurs=""0"" maxOccurs=""1"" name=""WindChill"" type=""s:string"" />
      <s:element minOccurs=""0"" maxOccurs=""1"" name=""Remarks"" type=""s:string"" />
    </s:sequence>
  </s:complexType>
  <s:element name=""ArrayOfWeatherDescription"" nillable=""true"" type=""tns:ArrayOfWeatherDescription"" />
  <s:element name=""ForecastReturn"" nillable=""true"" type=""tns:ForecastReturn"" />
  <s:element name=""WeatherReturn"" type=""tns:WeatherReturn"" />
</s:schema>",
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
		_, err := apimanagement.NewApiSchema(ctx, "apiSchema", &apimanagement.ApiSchemaArgs{
			ApiId:             pulumi.String("59d6bb8f1f7fab13dc67ec9b"),
			ContentType:       pulumi.String("application/vnd.ms-azure-apim.xsd+xml"),
			ResourceGroupName: pulumi.String("rg1"),
			SchemaId:          pulumi.String("ec12520d-9d48-4e7b-8f39-698ca2ac63f1"),
			ServiceName:       pulumi.String("apimService1"),
			Value:             pulumi.String("<s:schema elementFormDefault=\"qualified\" targetNamespace=\"http://ws.cdyne.com/WeatherWS/\" xmlns:tns=\"http://ws.cdyne.com/WeatherWS/\" xmlns:s=\"http://www.w3.org/2001/XMLSchema\" xmlns:soap12=\"http://schemas.xmlsoap.org/wsdl/soap12/\" xmlns:mime=\"http://schemas.xmlsoap.org/wsdl/mime/\" xmlns:soap=\"http://schemas.xmlsoap.org/wsdl/soap/\" xmlns:tm=\"http://microsoft.com/wsdl/mime/textMatching/\" xmlns:http=\"http://schemas.xmlsoap.org/wsdl/http/\" xmlns:soapenc=\"http://schemas.xmlsoap.org/soap/encoding/\" xmlns:wsdl=\"http://schemas.xmlsoap.org/wsdl/\" xmlns:apim-wsdltns=\"http://ws.cdyne.com/WeatherWS/\">\n  <s:element name=\"GetWeatherInformation\">\n    <s:complexType />\n  </s:element>\n  <s:element name=\"GetWeatherInformationResponse\">\n    <s:complexType>\n      <s:sequence>\n        <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"GetWeatherInformationResult\" type=\"tns:ArrayOfWeatherDescription\" />\n      </s:sequence>\n    </s:complexType>\n  </s:element>\n  <s:complexType name=\"ArrayOfWeatherDescription\">\n    <s:sequence>\n      <s:element minOccurs=\"0\" maxOccurs=\"unbounded\" name=\"WeatherDescription\" type=\"tns:WeatherDescription\" />\n    </s:sequence>\n  </s:complexType>\n  <s:complexType name=\"WeatherDescription\">\n    <s:sequence>\n      <s:element minOccurs=\"1\" maxOccurs=\"1\" name=\"WeatherID\" type=\"s:short\" />\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"Description\" type=\"s:string\" />\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"PictureURL\" type=\"s:string\" />\n    </s:sequence>\n  </s:complexType>\n  <s:element name=\"GetCityForecastByZIP\">\n    <s:complexType>\n      <s:sequence>\n        <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"ZIP\" type=\"s:string\" />\n      </s:sequence>\n    </s:complexType>\n  </s:element>\n  <s:element name=\"GetCityForecastByZIPResponse\">\n    <s:complexType>\n      <s:sequence>\n        <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"GetCityForecastByZIPResult\" type=\"tns:ForecastReturn\" />\n      </s:sequence>\n    </s:complexType>\n  </s:element>\n  <s:complexType name=\"ForecastReturn\">\n    <s:sequence>\n      <s:element minOccurs=\"1\" maxOccurs=\"1\" name=\"Success\" type=\"s:boolean\" />\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"ResponseText\" type=\"s:string\" />\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"State\" type=\"s:string\" />\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"City\" type=\"s:string\" />\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"WeatherStationCity\" type=\"s:string\" />\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"ForecastResult\" type=\"tns:ArrayOfForecast\" />\n    </s:sequence>\n  </s:complexType>\n  <s:complexType name=\"ArrayOfForecast\">\n    <s:sequence>\n      <s:element minOccurs=\"0\" maxOccurs=\"unbounded\" name=\"Forecast\" nillable=\"true\" type=\"tns:Forecast\" />\n    </s:sequence>\n  </s:complexType>\n  <s:complexType name=\"Forecast\">\n    <s:sequence>\n      <s:element minOccurs=\"1\" maxOccurs=\"1\" name=\"Date\" type=\"s:dateTime\" />\n      <s:element minOccurs=\"1\" maxOccurs=\"1\" name=\"WeatherID\" type=\"s:short\" />\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"Desciption\" type=\"s:string\" />\n      <s:element minOccurs=\"1\" maxOccurs=\"1\" name=\"Temperatures\" type=\"tns:temp\" />\n      <s:element minOccurs=\"1\" maxOccurs=\"1\" name=\"ProbabilityOfPrecipiation\" type=\"tns:POP\" />\n    </s:sequence>\n  </s:complexType>\n  <s:complexType name=\"temp\">\n    <s:sequence>\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"MorningLow\" type=\"s:string\" />\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"DaytimeHigh\" type=\"s:string\" />\n    </s:sequence>\n  </s:complexType>\n  <s:complexType name=\"POP\">\n    <s:sequence>\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"Nighttime\" type=\"s:string\" />\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"Daytime\" type=\"s:string\" />\n    </s:sequence>\n  </s:complexType>\n  <s:element name=\"GetCityWeatherByZIP\">\n    <s:complexType>\n      <s:sequence>\n        <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"ZIP\" type=\"s:string\" />\n      </s:sequence>\n    </s:complexType>\n  </s:element>\n  <s:element name=\"GetCityWeatherByZIPResponse\">\n    <s:complexType>\n      <s:sequence>\n        <s:element minOccurs=\"1\" maxOccurs=\"1\" name=\"GetCityWeatherByZIPResult\" type=\"tns:WeatherReturn\" />\n      </s:sequence>\n    </s:complexType>\n  </s:element>\n  <s:complexType name=\"WeatherReturn\">\n    <s:sequence>\n      <s:element minOccurs=\"1\" maxOccurs=\"1\" name=\"Success\" type=\"s:boolean\" />\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"ResponseText\" type=\"s:string\" />\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"State\" type=\"s:string\" />\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"City\" type=\"s:string\" />\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"WeatherStationCity\" type=\"s:string\" />\n      <s:element minOccurs=\"1\" maxOccurs=\"1\" name=\"WeatherID\" type=\"s:short\" />\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"Description\" type=\"s:string\" />\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"Temperature\" type=\"s:string\" />\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"RelativeHumidity\" type=\"s:string\" />\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"Wind\" type=\"s:string\" />\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"Pressure\" type=\"s:string\" />\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"Visibility\" type=\"s:string\" />\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"WindChill\" type=\"s:string\" />\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"Remarks\" type=\"s:string\" />\n    </s:sequence>\n  </s:complexType>\n  <s:element name=\"ArrayOfWeatherDescription\" nillable=\"true\" type=\"tns:ArrayOfWeatherDescription\" />\n  <s:element name=\"ForecastReturn\" nillable=\"true\" type=\"tns:ForecastReturn\" />\n  <s:element name=\"WeatherReturn\" type=\"tns:WeatherReturn\" />\n</s:schema>"),
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
import com.pulumi.azurenative.apimanagement.ApiSchema;
import com.pulumi.azurenative.apimanagement.ApiSchemaArgs;
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
        var apiSchema = new ApiSchema("apiSchema", ApiSchemaArgs.builder()        
            .apiId("59d6bb8f1f7fab13dc67ec9b")
            .contentType("application/vnd.ms-azure-apim.xsd+xml")
            .resourceGroupName("rg1")
            .schemaId("ec12520d-9d48-4e7b-8f39-698ca2ac63f1")
            .serviceName("apimService1")
            .value("""
<s:schema elementFormDefault="qualified" targetNamespace="http://ws.cdyne.com/WeatherWS/" xmlns:tns="http://ws.cdyne.com/WeatherWS/" xmlns:s="http://www.w3.org/2001/XMLSchema" xmlns:soap12="http://schemas.xmlsoap.org/wsdl/soap12/" xmlns:mime="http://schemas.xmlsoap.org/wsdl/mime/" xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/" xmlns:tm="http://microsoft.com/wsdl/mime/textMatching/" xmlns:http="http://schemas.xmlsoap.org/wsdl/http/" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/" xmlns:wsdl="http://schemas.xmlsoap.org/wsdl/" xmlns:apim-wsdltns="http://ws.cdyne.com/WeatherWS/">
  <s:element name="GetWeatherInformation">
    <s:complexType />
  </s:element>
  <s:element name="GetWeatherInformationResponse">
    <s:complexType>
      <s:sequence>
        <s:element minOccurs="0" maxOccurs="1" name="GetWeatherInformationResult" type="tns:ArrayOfWeatherDescription" />
      </s:sequence>
    </s:complexType>
  </s:element>
  <s:complexType name="ArrayOfWeatherDescription">
    <s:sequence>
      <s:element minOccurs="0" maxOccurs="unbounded" name="WeatherDescription" type="tns:WeatherDescription" />
    </s:sequence>
  </s:complexType>
  <s:complexType name="WeatherDescription">
    <s:sequence>
      <s:element minOccurs="1" maxOccurs="1" name="WeatherID" type="s:short" />
      <s:element minOccurs="0" maxOccurs="1" name="Description" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="PictureURL" type="s:string" />
    </s:sequence>
  </s:complexType>
  <s:element name="GetCityForecastByZIP">
    <s:complexType>
      <s:sequence>
        <s:element minOccurs="0" maxOccurs="1" name="ZIP" type="s:string" />
      </s:sequence>
    </s:complexType>
  </s:element>
  <s:element name="GetCityForecastByZIPResponse">
    <s:complexType>
      <s:sequence>
        <s:element minOccurs="0" maxOccurs="1" name="GetCityForecastByZIPResult" type="tns:ForecastReturn" />
      </s:sequence>
    </s:complexType>
  </s:element>
  <s:complexType name="ForecastReturn">
    <s:sequence>
      <s:element minOccurs="1" maxOccurs="1" name="Success" type="s:boolean" />
      <s:element minOccurs="0" maxOccurs="1" name="ResponseText" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="State" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="City" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="WeatherStationCity" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="ForecastResult" type="tns:ArrayOfForecast" />
    </s:sequence>
  </s:complexType>
  <s:complexType name="ArrayOfForecast">
    <s:sequence>
      <s:element minOccurs="0" maxOccurs="unbounded" name="Forecast" nillable="true" type="tns:Forecast" />
    </s:sequence>
  </s:complexType>
  <s:complexType name="Forecast">
    <s:sequence>
      <s:element minOccurs="1" maxOccurs="1" name="Date" type="s:dateTime" />
      <s:element minOccurs="1" maxOccurs="1" name="WeatherID" type="s:short" />
      <s:element minOccurs="0" maxOccurs="1" name="Desciption" type="s:string" />
      <s:element minOccurs="1" maxOccurs="1" name="Temperatures" type="tns:temp" />
      <s:element minOccurs="1" maxOccurs="1" name="ProbabilityOfPrecipiation" type="tns:POP" />
    </s:sequence>
  </s:complexType>
  <s:complexType name="temp">
    <s:sequence>
      <s:element minOccurs="0" maxOccurs="1" name="MorningLow" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="DaytimeHigh" type="s:string" />
    </s:sequence>
  </s:complexType>
  <s:complexType name="POP">
    <s:sequence>
      <s:element minOccurs="0" maxOccurs="1" name="Nighttime" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="Daytime" type="s:string" />
    </s:sequence>
  </s:complexType>
  <s:element name="GetCityWeatherByZIP">
    <s:complexType>
      <s:sequence>
        <s:element minOccurs="0" maxOccurs="1" name="ZIP" type="s:string" />
      </s:sequence>
    </s:complexType>
  </s:element>
  <s:element name="GetCityWeatherByZIPResponse">
    <s:complexType>
      <s:sequence>
        <s:element minOccurs="1" maxOccurs="1" name="GetCityWeatherByZIPResult" type="tns:WeatherReturn" />
      </s:sequence>
    </s:complexType>
  </s:element>
  <s:complexType name="WeatherReturn">
    <s:sequence>
      <s:element minOccurs="1" maxOccurs="1" name="Success" type="s:boolean" />
      <s:element minOccurs="0" maxOccurs="1" name="ResponseText" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="State" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="City" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="WeatherStationCity" type="s:string" />
      <s:element minOccurs="1" maxOccurs="1" name="WeatherID" type="s:short" />
      <s:element minOccurs="0" maxOccurs="1" name="Description" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="Temperature" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="RelativeHumidity" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="Wind" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="Pressure" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="Visibility" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="WindChill" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="Remarks" type="s:string" />
    </s:sequence>
  </s:complexType>
  <s:element name="ArrayOfWeatherDescription" nillable="true" type="tns:ArrayOfWeatherDescription" />
  <s:element name="ForecastReturn" nillable="true" type="tns:ForecastReturn" />
  <s:element name="WeatherReturn" type="tns:WeatherReturn" />
</s:schema>            """)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const apiSchema = new azure_native.apimanagement.ApiSchema("apiSchema", {
    apiId: "59d6bb8f1f7fab13dc67ec9b",
    contentType: "application/vnd.ms-azure-apim.xsd+xml",
    resourceGroupName: "rg1",
    schemaId: "ec12520d-9d48-4e7b-8f39-698ca2ac63f1",
    serviceName: "apimService1",
    value: `<s:schema elementFormDefault="qualified" targetNamespace="http://ws.cdyne.com/WeatherWS/" xmlns:tns="http://ws.cdyne.com/WeatherWS/" xmlns:s="http://www.w3.org/2001/XMLSchema" xmlns:soap12="http://schemas.xmlsoap.org/wsdl/soap12/" xmlns:mime="http://schemas.xmlsoap.org/wsdl/mime/" xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/" xmlns:tm="http://microsoft.com/wsdl/mime/textMatching/" xmlns:http="http://schemas.xmlsoap.org/wsdl/http/" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/" xmlns:wsdl="http://schemas.xmlsoap.org/wsdl/" xmlns:apim-wsdltns="http://ws.cdyne.com/WeatherWS/">
  <s:element name="GetWeatherInformation">
    <s:complexType />
  </s:element>
  <s:element name="GetWeatherInformationResponse">
    <s:complexType>
      <s:sequence>
        <s:element minOccurs="0" maxOccurs="1" name="GetWeatherInformationResult" type="tns:ArrayOfWeatherDescription" />
      </s:sequence>
    </s:complexType>
  </s:element>
  <s:complexType name="ArrayOfWeatherDescription">
    <s:sequence>
      <s:element minOccurs="0" maxOccurs="unbounded" name="WeatherDescription" type="tns:WeatherDescription" />
    </s:sequence>
  </s:complexType>
  <s:complexType name="WeatherDescription">
    <s:sequence>
      <s:element minOccurs="1" maxOccurs="1" name="WeatherID" type="s:short" />
      <s:element minOccurs="0" maxOccurs="1" name="Description" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="PictureURL" type="s:string" />
    </s:sequence>
  </s:complexType>
  <s:element name="GetCityForecastByZIP">
    <s:complexType>
      <s:sequence>
        <s:element minOccurs="0" maxOccurs="1" name="ZIP" type="s:string" />
      </s:sequence>
    </s:complexType>
  </s:element>
  <s:element name="GetCityForecastByZIPResponse">
    <s:complexType>
      <s:sequence>
        <s:element minOccurs="0" maxOccurs="1" name="GetCityForecastByZIPResult" type="tns:ForecastReturn" />
      </s:sequence>
    </s:complexType>
  </s:element>
  <s:complexType name="ForecastReturn">
    <s:sequence>
      <s:element minOccurs="1" maxOccurs="1" name="Success" type="s:boolean" />
      <s:element minOccurs="0" maxOccurs="1" name="ResponseText" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="State" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="City" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="WeatherStationCity" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="ForecastResult" type="tns:ArrayOfForecast" />
    </s:sequence>
  </s:complexType>
  <s:complexType name="ArrayOfForecast">
    <s:sequence>
      <s:element minOccurs="0" maxOccurs="unbounded" name="Forecast" nillable="true" type="tns:Forecast" />
    </s:sequence>
  </s:complexType>
  <s:complexType name="Forecast">
    <s:sequence>
      <s:element minOccurs="1" maxOccurs="1" name="Date" type="s:dateTime" />
      <s:element minOccurs="1" maxOccurs="1" name="WeatherID" type="s:short" />
      <s:element minOccurs="0" maxOccurs="1" name="Desciption" type="s:string" />
      <s:element minOccurs="1" maxOccurs="1" name="Temperatures" type="tns:temp" />
      <s:element minOccurs="1" maxOccurs="1" name="ProbabilityOfPrecipiation" type="tns:POP" />
    </s:sequence>
  </s:complexType>
  <s:complexType name="temp">
    <s:sequence>
      <s:element minOccurs="0" maxOccurs="1" name="MorningLow" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="DaytimeHigh" type="s:string" />
    </s:sequence>
  </s:complexType>
  <s:complexType name="POP">
    <s:sequence>
      <s:element minOccurs="0" maxOccurs="1" name="Nighttime" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="Daytime" type="s:string" />
    </s:sequence>
  </s:complexType>
  <s:element name="GetCityWeatherByZIP">
    <s:complexType>
      <s:sequence>
        <s:element minOccurs="0" maxOccurs="1" name="ZIP" type="s:string" />
      </s:sequence>
    </s:complexType>
  </s:element>
  <s:element name="GetCityWeatherByZIPResponse">
    <s:complexType>
      <s:sequence>
        <s:element minOccurs="1" maxOccurs="1" name="GetCityWeatherByZIPResult" type="tns:WeatherReturn" />
      </s:sequence>
    </s:complexType>
  </s:element>
  <s:complexType name="WeatherReturn">
    <s:sequence>
      <s:element minOccurs="1" maxOccurs="1" name="Success" type="s:boolean" />
      <s:element minOccurs="0" maxOccurs="1" name="ResponseText" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="State" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="City" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="WeatherStationCity" type="s:string" />
      <s:element minOccurs="1" maxOccurs="1" name="WeatherID" type="s:short" />
      <s:element minOccurs="0" maxOccurs="1" name="Description" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="Temperature" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="RelativeHumidity" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="Wind" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="Pressure" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="Visibility" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="WindChill" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="Remarks" type="s:string" />
    </s:sequence>
  </s:complexType>
  <s:element name="ArrayOfWeatherDescription" nillable="true" type="tns:ArrayOfWeatherDescription" />
  <s:element name="ForecastReturn" nillable="true" type="tns:ForecastReturn" />
  <s:element name="WeatherReturn" type="tns:WeatherReturn" />
</s:schema>`,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api_schema = azure_native.apimanagement.ApiSchema("apiSchema",
    api_id="59d6bb8f1f7fab13dc67ec9b",
    content_type="application/vnd.ms-azure-apim.xsd+xml",
    resource_group_name="rg1",
    schema_id="ec12520d-9d48-4e7b-8f39-698ca2ac63f1",
    service_name="apimService1",
    value="""<s:schema elementFormDefault="qualified" targetNamespace="http://ws.cdyne.com/WeatherWS/" xmlns:tns="http://ws.cdyne.com/WeatherWS/" xmlns:s="http://www.w3.org/2001/XMLSchema" xmlns:soap12="http://schemas.xmlsoap.org/wsdl/soap12/" xmlns:mime="http://schemas.xmlsoap.org/wsdl/mime/" xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/" xmlns:tm="http://microsoft.com/wsdl/mime/textMatching/" xmlns:http="http://schemas.xmlsoap.org/wsdl/http/" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/" xmlns:wsdl="http://schemas.xmlsoap.org/wsdl/" xmlns:apim-wsdltns="http://ws.cdyne.com/WeatherWS/">
  <s:element name="GetWeatherInformation">
    <s:complexType />
  </s:element>
  <s:element name="GetWeatherInformationResponse">
    <s:complexType>
      <s:sequence>
        <s:element minOccurs="0" maxOccurs="1" name="GetWeatherInformationResult" type="tns:ArrayOfWeatherDescription" />
      </s:sequence>
    </s:complexType>
  </s:element>
  <s:complexType name="ArrayOfWeatherDescription">
    <s:sequence>
      <s:element minOccurs="0" maxOccurs="unbounded" name="WeatherDescription" type="tns:WeatherDescription" />
    </s:sequence>
  </s:complexType>
  <s:complexType name="WeatherDescription">
    <s:sequence>
      <s:element minOccurs="1" maxOccurs="1" name="WeatherID" type="s:short" />
      <s:element minOccurs="0" maxOccurs="1" name="Description" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="PictureURL" type="s:string" />
    </s:sequence>
  </s:complexType>
  <s:element name="GetCityForecastByZIP">
    <s:complexType>
      <s:sequence>
        <s:element minOccurs="0" maxOccurs="1" name="ZIP" type="s:string" />
      </s:sequence>
    </s:complexType>
  </s:element>
  <s:element name="GetCityForecastByZIPResponse">
    <s:complexType>
      <s:sequence>
        <s:element minOccurs="0" maxOccurs="1" name="GetCityForecastByZIPResult" type="tns:ForecastReturn" />
      </s:sequence>
    </s:complexType>
  </s:element>
  <s:complexType name="ForecastReturn">
    <s:sequence>
      <s:element minOccurs="1" maxOccurs="1" name="Success" type="s:boolean" />
      <s:element minOccurs="0" maxOccurs="1" name="ResponseText" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="State" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="City" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="WeatherStationCity" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="ForecastResult" type="tns:ArrayOfForecast" />
    </s:sequence>
  </s:complexType>
  <s:complexType name="ArrayOfForecast">
    <s:sequence>
      <s:element minOccurs="0" maxOccurs="unbounded" name="Forecast" nillable="true" type="tns:Forecast" />
    </s:sequence>
  </s:complexType>
  <s:complexType name="Forecast">
    <s:sequence>
      <s:element minOccurs="1" maxOccurs="1" name="Date" type="s:dateTime" />
      <s:element minOccurs="1" maxOccurs="1" name="WeatherID" type="s:short" />
      <s:element minOccurs="0" maxOccurs="1" name="Desciption" type="s:string" />
      <s:element minOccurs="1" maxOccurs="1" name="Temperatures" type="tns:temp" />
      <s:element minOccurs="1" maxOccurs="1" name="ProbabilityOfPrecipiation" type="tns:POP" />
    </s:sequence>
  </s:complexType>
  <s:complexType name="temp">
    <s:sequence>
      <s:element minOccurs="0" maxOccurs="1" name="MorningLow" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="DaytimeHigh" type="s:string" />
    </s:sequence>
  </s:complexType>
  <s:complexType name="POP">
    <s:sequence>
      <s:element minOccurs="0" maxOccurs="1" name="Nighttime" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="Daytime" type="s:string" />
    </s:sequence>
  </s:complexType>
  <s:element name="GetCityWeatherByZIP">
    <s:complexType>
      <s:sequence>
        <s:element minOccurs="0" maxOccurs="1" name="ZIP" type="s:string" />
      </s:sequence>
    </s:complexType>
  </s:element>
  <s:element name="GetCityWeatherByZIPResponse">
    <s:complexType>
      <s:sequence>
        <s:element minOccurs="1" maxOccurs="1" name="GetCityWeatherByZIPResult" type="tns:WeatherReturn" />
      </s:sequence>
    </s:complexType>
  </s:element>
  <s:complexType name="WeatherReturn">
    <s:sequence>
      <s:element minOccurs="1" maxOccurs="1" name="Success" type="s:boolean" />
      <s:element minOccurs="0" maxOccurs="1" name="ResponseText" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="State" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="City" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="WeatherStationCity" type="s:string" />
      <s:element minOccurs="1" maxOccurs="1" name="WeatherID" type="s:short" />
      <s:element minOccurs="0" maxOccurs="1" name="Description" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="Temperature" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="RelativeHumidity" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="Wind" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="Pressure" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="Visibility" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="WindChill" type="s:string" />
      <s:element minOccurs="0" maxOccurs="1" name="Remarks" type="s:string" />
    </s:sequence>
  </s:complexType>
  <s:element name="ArrayOfWeatherDescription" nillable="true" type="tns:ArrayOfWeatherDescription" />
  <s:element name="ForecastReturn" nillable="true" type="tns:ForecastReturn" />
  <s:element name="WeatherReturn" type="tns:WeatherReturn" />
</s:schema>""")

```

```yaml
resources:
  apiSchema:
    type: azure-native:apimanagement:ApiSchema
    properties:
      apiId: 59d6bb8f1f7fab13dc67ec9b
      contentType: application/vnd.ms-azure-apim.xsd+xml
      resourceGroupName: rg1
      schemaId: ec12520d-9d48-4e7b-8f39-698ca2ac63f1
      serviceName: apimService1
      value: "<s:schema elementFormDefault=\"qualified\" targetNamespace=\"http://ws.cdyne.com/WeatherWS/\" xmlns:tns=\"http://ws.cdyne.com/WeatherWS/\" xmlns:s=\"http://www.w3.org/2001/XMLSchema\" xmlns:soap12=\"http://schemas.xmlsoap.org/wsdl/soap12/\" xmlns:mime=\"http://schemas.xmlsoap.org/wsdl/mime/\" xmlns:soap=\"http://schemas.xmlsoap.org/wsdl/soap/\" xmlns:tm=\"http://microsoft.com/wsdl/mime/textMatching/\" xmlns:http=\"http://schemas.xmlsoap.org/wsdl/http/\" xmlns:soapenc=\"http://schemas.xmlsoap.org/soap/encoding/\" xmlns:wsdl=\"http://schemas.xmlsoap.org/wsdl/\" xmlns:apim-wsdltns=\"http://ws.cdyne.com/WeatherWS/\">\r\n  <s:element name=\"GetWeatherInformation\">\r\n    <s:complexType />\r\n  </s:element>\r\n  <s:element name=\"GetWeatherInformationResponse\">\r\n    <s:complexType>\r\n      <s:sequence>\r\n        <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"GetWeatherInformationResult\" type=\"tns:ArrayOfWeatherDescription\" />\r\n      </s:sequence>\r\n    </s:complexType>\r\n  </s:element>\r\n  <s:complexType name=\"ArrayOfWeatherDescription\">\r\n    <s:sequence>\r\n      <s:element minOccurs=\"0\" maxOccurs=\"unbounded\" name=\"WeatherDescription\" type=\"tns:WeatherDescription\" />\r\n    </s:sequence>\r\n  </s:complexType>\r\n  <s:complexType name=\"WeatherDescription\">\r\n    <s:sequence>\r\n      <s:element minOccurs=\"1\" maxOccurs=\"1\" name=\"WeatherID\" type=\"s:short\" />\r\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"Description\" type=\"s:string\" />\r\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"PictureURL\" type=\"s:string\" />\r\n    </s:sequence>\r\n  </s:complexType>\r\n  <s:element name=\"GetCityForecastByZIP\">\r\n    <s:complexType>\r\n      <s:sequence>\r\n        <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"ZIP\" type=\"s:string\" />\r\n      </s:sequence>\r\n    </s:complexType>\r\n  </s:element>\r\n  <s:element name=\"GetCityForecastByZIPResponse\">\r\n    <s:complexType>\r\n      <s:sequence>\r\n        <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"GetCityForecastByZIPResult\" type=\"tns:ForecastReturn\" />\r\n      </s:sequence>\r\n    </s:complexType>\r\n  </s:element>\r\n  <s:complexType name=\"ForecastReturn\">\r\n    <s:sequence>\r\n      <s:element minOccurs=\"1\" maxOccurs=\"1\" name=\"Success\" type=\"s:boolean\" />\r\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"ResponseText\" type=\"s:string\" />\r\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"State\" type=\"s:string\" />\r\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"City\" type=\"s:string\" />\r\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"WeatherStationCity\" type=\"s:string\" />\r\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"ForecastResult\" type=\"tns:ArrayOfForecast\" />\r\n    </s:sequence>\r\n  </s:complexType>\r\n  <s:complexType name=\"ArrayOfForecast\">\r\n    <s:sequence>\r\n      <s:element minOccurs=\"0\" maxOccurs=\"unbounded\" name=\"Forecast\" nillable=\"true\" type=\"tns:Forecast\" />\r\n    </s:sequence>\r\n  </s:complexType>\r\n  <s:complexType name=\"Forecast\">\r\n    <s:sequence>\r\n      <s:element minOccurs=\"1\" maxOccurs=\"1\" name=\"Date\" type=\"s:dateTime\" />\r\n      <s:element minOccurs=\"1\" maxOccurs=\"1\" name=\"WeatherID\" type=\"s:short\" />\r\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"Desciption\" type=\"s:string\" />\r\n      <s:element minOccurs=\"1\" maxOccurs=\"1\" name=\"Temperatures\" type=\"tns:temp\" />\r\n      <s:element minOccurs=\"1\" maxOccurs=\"1\" name=\"ProbabilityOfPrecipiation\" type=\"tns:POP\" />\r\n    </s:sequence>\r\n  </s:complexType>\r\n  <s:complexType name=\"temp\">\r\n    <s:sequence>\r\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"MorningLow\" type=\"s:string\" />\r\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"DaytimeHigh\" type=\"s:string\" />\r\n    </s:sequence>\r\n  </s:complexType>\r\n  <s:complexType name=\"POP\">\r\n    <s:sequence>\r\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"Nighttime\" type=\"s:string\" />\r\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"Daytime\" type=\"s:string\" />\r\n    </s:sequence>\r\n  </s:complexType>\r\n  <s:element name=\"GetCityWeatherByZIP\">\r\n    <s:complexType>\r\n      <s:sequence>\r\n        <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"ZIP\" type=\"s:string\" />\r\n      </s:sequence>\r\n    </s:complexType>\r\n  </s:element>\r\n  <s:element name=\"GetCityWeatherByZIPResponse\">\r\n    <s:complexType>\r\n      <s:sequence>\r\n        <s:element minOccurs=\"1\" maxOccurs=\"1\" name=\"GetCityWeatherByZIPResult\" type=\"tns:WeatherReturn\" />\r\n      </s:sequence>\r\n    </s:complexType>\r\n  </s:element>\r\n  <s:complexType name=\"WeatherReturn\">\r\n    <s:sequence>\r\n      <s:element minOccurs=\"1\" maxOccurs=\"1\" name=\"Success\" type=\"s:boolean\" />\r\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"ResponseText\" type=\"s:string\" />\r\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"State\" type=\"s:string\" />\r\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"City\" type=\"s:string\" />\r\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"WeatherStationCity\" type=\"s:string\" />\r\n      <s:element minOccurs=\"1\" maxOccurs=\"1\" name=\"WeatherID\" type=\"s:short\" />\r\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"Description\" type=\"s:string\" />\r\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"Temperature\" type=\"s:string\" />\r\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"RelativeHumidity\" type=\"s:string\" />\r\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"Wind\" type=\"s:string\" />\r\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"Pressure\" type=\"s:string\" />\r\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"Visibility\" type=\"s:string\" />\r\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"WindChill\" type=\"s:string\" />\r\n      <s:element minOccurs=\"0\" maxOccurs=\"1\" name=\"Remarks\" type=\"s:string\" />\r\n    </s:sequence>\r\n  </s:complexType>\r\n  <s:element name=\"ArrayOfWeatherDescription\" nillable=\"true\" type=\"tns:ArrayOfWeatherDescription\" />\r\n  <s:element name=\"ForecastReturn\" nillable=\"true\" type=\"tns:ForecastReturn\" />\r\n  <s:element name=\"WeatherReturn\" type=\"tns:WeatherReturn\" />\r\n</s:schema>"

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:ApiSchema ec12520d-9d48-4e7b-8f39-698ca2ac63f1 /subscriptions/subid/resourcegroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apis/59d6bb8f1f7fab13dc67ec9b/schemas/ec12520d-9d48-4e7b-8f39-698ca2ac63f1 
```
