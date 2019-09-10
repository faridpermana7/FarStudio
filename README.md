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
            public long ExampleId { get; set; }

            [JsonProperty("code")]
            public string Code { get; set; }

            [JsonConverter(typeof(FDateTimeConverter), "dd MMM yyyy HH:mm")]
            [JsonProperty("createdDate")]
            public System.DateTime CreatedDate { get; set; }
        }
    }


## MVC :
On mvc that make DateTime Converter work, you must add BaseController on your MVC Controller. You just put **JsonController** and using **FarDatetimeConverter.Mvc**.

    using FarDatetimeConverter.Mvc;
    using System.Web.Mvc;

    namespace FarstWeb.Controllers
    {
        public class ExamplesController : **JsonController**
        {
            // GET: Mahasiswas
            public ActionResult Index(long id)
            {
		             var response = new object();
               // your code
               // your code
               return Json(response, JsonRequestBehavior.AllowGet);
            }
        }
    }


**EXPLAIN**
> **[JsonConverter()]** : this base for us include our converter.  
> **typeof(FDateTimeConverter)** : add our converter.  
> **"dd MMM yyyy HH:mm"** : this is one of example our custom format date, you can add another format whatever you want.  
> if you don't take any custom format like **[JsonConverter(typeof(FDateTimeConverter)]** as default we make format **yyyyMMdd**.
