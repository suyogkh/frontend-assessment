# Frontend Assessment

> Both completed task can be found on their respective folder `exercise-1` and `exercise-2`

## Exercise 1

This task has been completed using the expressJS. I have used basic HTML and SCSS along with the bootstrap-5 (CSS) only to complete the task. Since its a basic HTML, inorder to complile SCSS I have used a node-sass module, which will compile the SCSS and generate the minified version of CSS.

Inorder to run the exercise 1 please navigate to exercise 1's folder using your terminal `cd exercise-1` and once you are in the exercise folder please type `npm i` to install all of the required packages. Once completed please run `npm run dev` to run the dev server, which will be available on `http://localhost:3000` if you want to change the port please update `PORT` value on `/src/pre-start/env/development.env`

## Exercise 2

This task has been completed using the VueJS-3.

Inorder to run the exercise 2 please navigate to exercise 2's folder using your terminal `cd exercise-2` and once you are in the exercise folder please type `npm i` to install all of the required packages. Once completed please run `npm run dev` to run the dev server, which will be available on `http://localhost:5173`.

## Bonus Question

Explain why the result of `('b' + 'a' + + 'a' + 'a').toLowerCase()` is `banana`

**Answer:**
The first b and a added up as ba `('ba' + + 'a' + 'a')`. Now the `+ +` that we can see before the second a, the first one is for the concatenation and second one is to convert string to a number. For example if you run the following code:

```
const a = +"10";
typeof a
```

It will output the type as a `number`. Since the value that we have provided isn't a number, it will return the value as NaN (not a number). After the conversion our code look like this `('ba' + 'NaN' + 'a')` which will concate to a value `baNaNa`. Finally `toLowerCase()` which will lowercased the value into `banana`
