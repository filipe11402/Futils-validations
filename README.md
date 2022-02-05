# Credit Card number validation library

Validate your credit card numbers based on their brand using data anotations

---
## Example
### Create the model you want to perform validation
```cs
public class CreditCardModel
{
    //choose the desired credit card brand
    //in this case MasterCard
    [MasterCard]
    public string CreditCardNumber { get; set; }
}
```
### Check if the data inserted is valid
```cs
public class CreditCardController : Controller
{
    //Use your model as the model that get's the data
    [HttpPost]
    [Route("/")]
    public IActionResult MyRoute([FromBody] CreditCardModel myModel)
    {
        //This will check if the credit card number is valid
        //You can then return an error message to your taste
        if(ModelState.IsValid)
        {
            return StatusCode(StatusCodes.400BadRequest);
        }
        
        //Apply your logic
        //...
        
        return StatusCode(StatusCodes.200OK);
    }
}
```
