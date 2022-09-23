---
layout: post
title:      "Pour Me A Drink"
date:       2022-09-22 17:22:26 -0400
permalink:  pour_me_a_drink
---

This project has taken me years to complete. When I started this software engineering course, I expected to finish it in less than a year. I got off to a great start in April 2019. Since starting this course over 3 years ago, I have had 4 different jobs, lived in 3 different places, planned a funeral, fought for my life, questioned all of my beliefs, and eventually met the love of my life. And if that isn't enough, I did it all during a global pandemic. 

To say I'm proud to finally finish this little project is an understatement.  

Over the past few years, I've had to relearn React multiple times. Flatiron went through a complete makeover during that time as well, so I've gotten to learn it in multiple ways. You'd think I'd be an expert by now, but of course, there is always more to learn.  

The project I created is a single page app for helping a user store unique drink recipes and browse new ones. With the help of the free cocktail database API, I was able to load their data into my app and provide the user with many recipes to browse. Because it is a free API, there were limits to how many recipes I could fetch at a time and to how I fetched those recipes. For that reason, the user can browse recipes by the starting letter in the drink title. In future versions of this app, users would hopefully be able to search by name or ingredients.

![](https://imgur.com/FIXXsHu)

The app contains a dynamic form that is used for adding new recipes, as well as editing recipes that have already been added. There were plenty of resources for creating a blank dynamic form online, but I ran into issues when it came time to use the same form to update a recipe that already existed in the database.

First, for some context, this is how the ingredients and measurements were structured in the free Cocktail Database API. 

```
"strIngredient1": "Gin",
"strIngredient2": "Creme de Cacao",
"strIngredient3": "Light cream",
"strIngredient4": "Nutmeg",
```

```
"strMeasure1": "1/2 oz ",
"strMeasure2": "1/2 oz white ",
"strMeasure3": "2 oz ",
```

In order to make my React components more versatile, it felt necessary to structure the user's recipes in the same way in the backend. For a blank recipe form, that meant my code looked like this: 

State: 
```
const [ingredientFields, setIngredientFields] = useState([
      {ingredient: "", measurement: ''}
    ])
```

Creating blank inputs: 

```
function mapIngredientFields(){
      return ingredientFields.map((field, index) => {
            return (
                  <div key={`${field.ingredient}${index}`}>
                  <input type="text" placeholder={`Ingredient ${index + 1}`} name={`strIngredient${index+1}`} onChange={handleChange} key={`${index}Ingredient`} defaultValue={''} />
                  <input type="text" placeholder={`Measurement ${index + 1}`} name={`strMeasure${index+1}`} onChange={handleChange} key={`${index}Measurement`} defaultValue={''} />
                  <button key={index} onClick={e => removeIngredientField(e, index)}>X</button><br />
                  </div>

            )
      })
```

When any changes were made in the form: 

```
function handleChange(e){
        return setFormData({...formData, [e.target.name]: e.target.value}) 
    }
```

So notice that the name attribute for the input was based on how many times the user hit the "Add Ingredient" button and added an input to the array of inputs in state. That made it fairly simple to add ingredients and measurements. If a user needed to remove an input, they would click the X and this function would run: 

```
function removeIngredientField(e, index){
            e.preventDefault()
            let fields = [...ingredientFields]
            fields.splice(index, 1)
            return setIngredientFields(fields)
      }
```

This changed the indexes of the inputs and kept everything in the correct order. 

Once I started using the form to edit, it got more complicated. Upon rendering the form, I used the `useEffect` hook to check if the params contained a cocktail Id and if it did, it would search through the recipes and filter out the matching cocktail. Then it would populate the fields based on the information contained in that object in the database.  

For things like the title, this was easy. The input looked like this: 
```
<label>Drink Name</label><br />
<input type="text" placeholder="Drink Name" name="strDrink" onChange={handleChange} defaultValue={cocktail ? cocktail.strDrink : ''} />
```

If there was a cocktail the default value was simply the Title of the drink. But for each cocktail, there was a different number of ingredients and I had to find a way to iterate over them and create fields for each ingredient and measurement. If the ingredients and measurements were contained in an array in the backend, then it would be a simple matter of using the `.map` method to iterate and create ingredient fields. However, it was not that simple. 

In the end, this is how I did it.  I created a method to add the cocktail ingredient fields to the `ingredientFields` array in state. That method looked like this:  

```
  function addCocktailIngredients(){
        if(cocktail){
            let count = 1
            let allFields = []
            while(cocktail[`strIngredient${count}`]){
                allFields.push({
                    ingredient: cocktail[`strIngredient${count}`], measurement: cocktail[`strMeasure${count}`]
                })
                count++
            }
            setIngredientFields([...allFields, {
                ingredient: '', measurement: ''
            }])
        }
    }
```

This method was called in the `useEffect` hook so as soon as the form rendered the ingredient fields were populated. This worked wonderfully, but the next challenge came when trying to make any changes to those ingredient fields. Simply clicking the  "X" to remove the field didn't change the formData or the backend. I had to change the `removeIngredientField` method to look like this: 

```
 function removeIngredientField(e, index){
        if(!cocktail){
            e.preventDefault()
            let fields = [...ingredientFields]
            fields.splice(index, 1)
            return setIngredientFields(fields)
        }else{
            e.preventDefault()
            let fields = [...ingredientFields]
            fields.splice(index, 1)
            let data = {...formData}
            for(let i = 0; i < fields.length; i++){
                data[`strIngredient${i+1}`] = fields[i].ingredient
                data[`strMeasure${i+1}`] = fields[i].measurement
            }
            setFormData(data)
            return setIngredientFields(fields)
        }
    }
```

When there is a cocktail present in state and a user clicks on the "X" to remove the ingredient, it updates the fields as it did previously, but it also changes the field data. I had to learn a lot about how the spread operator and setting state works to make this function correctly. I so badly wanted to make the `data` variable an array of ingredients but that added a new key to the `formData` object that pointed to a value of an array and then that didn't succesfully change the backend. Once I got the `data` variable right, I was able to change the `formData` object much more easily and then successfully update the backend when hitting submit. 

I had to do a lot of trial and error to get this to work. I spent days trying to solve this problem and I'm so proud of the final result. The app is simple and may not be impressive to some, but it symbolizes so much for me. I'm  proud of this accomplishment and with it's completion, I can now officially recieve the certificate to show I completed the Flatiron course. There was a long time where I didn't think that would happen. 

I'm a software engineer and I deserve a drink to celebrate! Good thing I have a whole app to help me find my new favorite!

Cheers,
Jo
