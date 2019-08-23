# FarStudio
### AUTHOR : FARID PERMANA

Datetime Converter

link : [http://www.nuget.org/packages/FarStudio.Utility.Parser/1.0.1](http://www.nuget.org/packages/FarStudio.Utility.Parser/1.0.1)

## Formating for property of DTO (data transfer object) Class.

Requirement : 
 -  Newtonsoft.Json 12.0.0


## Example class :

    using FarDatetimeConverter.Converter;
    using Newtonsoft.Json;

    namespace Core.Manager
    {
        public class ExampleDTO
        {
            public ExampleDTO()
            {
            }

            [JsonProperty("exampleId")]
            public long CustomerId { get; set; }

            [JsonProperty("code")]
            public string Code { get; set; }

            [JsonConverter(typeof(FDateTimeConverter), "dd MMM yyyy HH:mm")]
            [JsonProperty("createdDate")]
            public System.DateTime CreatedDate { get; set; }
        }
    }

**EXPLAIN**
> **[JsonConverter()]** : this base for us include our converter.  
> **typeof(FDateTimeConverter)** : add our converter.  
> **"dd MMM yyyy HH:mm"** : this is one of example our custom format date, you can add another format whatever you want.  
> if you don't take any custome format like **[JsonConverter(typeof(FDateTimeConverter)]** as default we make format **yyyyMMdd**.
   
