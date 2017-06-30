# Lambda Calculus

### Functions

A function takes inputs (input set / domain) and returns outputs (output set / codomain)

```
f(1) = A
```

1 = input

A = output

#### Referential Transparency

Referential transparency means that given the same input the output should be predicatable.

Invalid:

```
f(1) = A
f(1) = B
```

Valid:

```
f(1) = A
f(2) = A
```   

#### Lambda Terms

* expressions
* variables
* abstractions (functions)

an expression can be a variable or abstraction or combination. An abstraction is a function.

#### Lambda structure

An abstraction / function has 

1. head
2. body
3. dot separates params from the body

```
λx.x
```

The head is everything up to and including the dot. The body is everything after the dot.

This is an anonymous function - given a value it returns the value. It's called the identity function.

Takes a single parameter only which binds any variables with the same name in the body.

When applied the function returns the body.

#### Alpha equivalence

determines if a function is the same as another function based on its terms (params and body)

```
λx.x
λd.d
λz.z
```

Are all the same.

#### Beta reduction

1. substitute the the input for all variables in the body
2. elimitate the head

```
(λx.x) 2
       2
```

returns 2

```
(λx.x+1) 2
         2 + 1
         3
```

returns 3

##### Beta reduction with functions

```
(λx.x)(λy.y)
[x :== (λy.y)]
       λy.y
```

The first x lambda takes the y lambda and returns a y lambda. Use the :== to denote that we are substituting (λy.y) for all instances of x. So we are left with the y lambda.

```
((λx.x)(λy.y) z)
[x :== (λy.y)]
       (λy.y) z
       [y :== z]
              z 
```

Here lambda x takes lambda y and returns lambda y. Lamba y then takes the z and returns it.

#### Free Variables

Any variable in the body which is not part of the head. Alpha equivalence does not apply to free variables.

```
λx.xy
```

y = free variable

```
(λ x.xy) z
(λ[x :== z].xy)
         zy
```

Lambda x takes the z and returns it along with y. The x is substitued for the z everywhere in the body.

#### Multiple arguments

Since a lambda can only define 1 parameter and accept one argument then functions that require multiple arguments have multiple nested heads.

You apply the leftmost head and eliminate and move onto the next head. This is called `currying`

```
λxy.xy
```

is shorthand for two nested lambdas (one for x and one for y)

```
λx.(λy.xy)
```

#### Combinators

A lambda with no free variabled is called a combinator. Every variable in the body is specified in the head.
 

```
λx.x 
```

If there is a free variable in the body not specified in the head then it's not classed as a combinator

```
λx.xa
```

#### Simplification

Beta normal form is when you can't apply lambdas to arguments any more (reduce). 

Given a function (/) when you provide arguments it is said to be saturated - e.g. arguments applied but not yet reduced / evaluated.

``` 2000/1000 ``` is applied but not evaluated

The following has again been applied but not yet evaluated:

```
(10+2)*100/2
```

```600``` is the Beta normal form of the above (it has been reduced as far as it can go)


#### Divergence

This is when Beta reduction (convergence) is not possible. 

```(λx.xx)(λx.xx)``` is a lambda term called omega that diverges. The x in the first lambdas head becomes the second lambda and so after subsituting (λx.xx) for each occurance we come back to where we started and end up in an infinite loop. 




