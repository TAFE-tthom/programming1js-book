# Nested Control Flow

Sometimes we need our programs to make many different decisions where simply just one condition isn't enough. Let's take the following snippet of code as an example.

```js
let temperature = 21;
let raining = true;

if(temperature > 30) {
    console.log("It is very hot today!");
    if(raining == true) {
        console.log(" and it is also humid!");
    }
} else if(temperature <= 30 && temperature >= 22) {
    console.log("It is a little bit warm today");
} else if(temperature == 21) {

    console.log("Perfect beach weather!");
    if(raining == true) {
        console.log(" but it is raining :(");
    }
} else if(temperature < 21 && temperature > 13) {
    console.log("It is a little cool today!");
} else if(temperature <= 13 && temperature > 6) {
    console.log("It is quite cold!");
} else {

    console.log("Absolutely freezing!");
    if(raining == true) {
        console.log(" and it is snowing!");
    }
}
```

Given two variables and a few different ranges we want to check for, we can observe how complicated our nested if statements can be. For each temperature case, there is an additional case for `raining` where it will output in addition to the usual statement.

💻 Experiment with the snippet above and change the `temperature` and `raining` variables. Note down the different combinations you can construct and the different branches the code can go down.


## How many layers can we go?

We are not really limited with how much we can nest control-flow blocks within each other. However it can be difficult to comprehend and likely could be simplified.

It is advised to consider if you **need** that additional loop or if you are overcomplicating it. It is usually advisable to go through a scenario on paper when solving the problem and write down the steps you took 🖊️.


