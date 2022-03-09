---
id: litvis

narrative-schemas:
  - ../../narrative-schemas/teaching.yml
---

@import "../../css/datavis.less"

<!-- Everything above this line should probably be left untouched. -->

# Coding Gym 3 : Parameterising and Transforming Lists

_These exercises are designed to help you build confidence programming with Elm. They assume no prior experience of coding in any language other than that arising from previous weeks of this module. This document is designed to be viewed in VSCode with litvis so you can add your own code blocks to answer each question._

## 3.1. Functions with Parameters

The functions you have created in the previous gyms return the same value every time they are called. You can customise what they return by providing input _parameters_ that are used to generate the output. Parameters are indicated in a type annotation, naming their type and separating each of them and the output with a `->` symbol. For example:

```elm {l}
add : Float -> Float -> Float
add firstNum secondNum =
    firstNum + secondNum


greeting : String -> String
greeting name =
    "Good evening " ++ name
```

Parameterised functions can be _called_ by providing values for each of the parameters after the function name. For example:

```elm {l raw}
summary : Float
summary =
    add 120 84
```

```elm {l raw}
welcomeMessage : String
welcomeMessage =
    greeting "Ada Lovelace"
```

{(task|}

Create separate parameterised functions, each in their own code block, that do the following. Each code block should have the header `elm {l}`. To see the result, you should create separate code blocks with the header `elm {l raw}` and than call the functions you have created providing values for the parameters. See the examples `summary` and `welcomeMessage` above if you are unsure. If created successfully, you should see the evaluation of these functions appear in the preview window.

- A function that given two words as `String` parameters returns a single string with the words separated by an 'and'.
- A function that given a single `String` parameter representing a colour, returns "My favourite colour is ", naming the colour provided.
- A function to multiply three numbers provided as parameters.
- A function that creates a list of integers from 1 to a number provided as a parameter.
- A function that given two `Float` parameters, provides the square root of the sum of their squares.

{|task)}

```elm {l}
twoWords : String -> String -> String
twoWords firstWord secondWord =
    firstWord ++ " and " ++secondWord

favC : String -> String
favC colour =
    "My favourite colour is "++colour

mut3 : Float ->  Float -> Float -> Float
mut3 x y z =
    x*y*z

listOfInt : Int -> List Int
listOfInt x =
    List.range 1 x

sumOfSquares : Float -> Float -> Float
sumOfSquares x y=
    sqrt((x^2)+(y^2))


```

```elm {l raw}
test1 : String
test1 = twoWords "tobs" "I"
```

```elm {l raw}
test2 : String
test2= favC "BLue"
```

```elm {l raw}
test3 : Float
test3= mut3 20 1 2
```

```elm {l raw}
test4 : List Int
test4= listOfInt 20
```

```elm {l raw}
test5 : Float
test5= sumOfSquares 20 25
```

## 3.2. Transforming Lists

Just as we applied operators to individual items, we can apply them to all the items in a list. This is commonly achieved with the in-built function [List.map](https://package.elm-lang.org/packages/elm/core/latest/List#map). This function takes two parameters: the first is the function that will be applied to each item in the list and the second is the list itself. For example to increment all the values in a list by 1 we could do the following:

```elm {l}
incByOne : List Int -> List Int
incByOne myList =
    let
        inc num =
            num + 1
    in
    List.map inc myList
```

```elm {l raw}
newList : List Int
newList =
    incByOne [ 10, 20, 30, 40 ]
```

{(task|}

Create separate parameterised functions, each in their own code block, that do the following. Each code block should have the header `elm {l}`. Test them by creating separate functions that supply the list as a parameter (like `newList` above)

- A function that given a list of words, adds the word "potato" to each of them.
- A function that adds 12 to all the items in a list of numbers.
- A function that doubles each item in a list of numbers
- A function that finds the sum of the squares of all numbers in a list (_Hint: You may find the function [List.sum](https://package.elm-lang.org/packages/elm/core/latest/List#sum) helpful here_).
- A function that given an integer, creates a list of even numbers from 2 to that integer.

{|task)}

```elm {l}
addPotato : List String -> List String
addPotato myList=
    let
        inc index =
            index ++ " Potato"
    in
    List.map inc myList

add12 : List Int -> List Int
add12 myList=
    let
        inc index =
            index + 12
    in
    List.map inc myList

addX2 : List Int -> List Int
addX2 myList=
    let
        inc index =
            index *2
    in
    List.map inc myList



-- helper
sumOfSquaresL : List Int -> List Int
sumOfSquaresL myList=
    let
        inc index =
            index ^2
    in
    List.map inc myList

sumOfSquaresL2: List Int -> Int
sumOfSquaresL2 myList =
    List.sum (sumOfSquaresL myList)


-- helper
listOfInts : Int -> List Int
listOfInts x =
    List.range 2 x





--helper
isEven : Int -> Bool
isEven n =
   ((modBy 2 n)==0)

-- what is mod function and how to drop value in a list
evenL : Int -> List Int
evenL x=
    let
        inc index = if ((modBy 2 index)==0) then index else 0
    in
    List.map inc (listOfInts x)

-- need something that can find all 0's and drop them
remove : List Int -> List Int
remove k =
    List.filter isEven k

```

```elm {l raw}
testing1 : List String
testing1 =
    addPotato ["ok" ,"okll" ,"od"]

testing2 : List Int
testing2 =
    add12 [1,2,3]

testing3 : List Int
testing3 =
    addX2 [1,2,3]

testing4 : Int
testing4 =
    sumOfSquaresL2 [1,2,3]

-- to compare how the list has changed to get the answer of testing51
testing5 : List Int
testing5 = listOfInts 10

testing51 : List Int
testing51 = remove (evenL 10)
```
