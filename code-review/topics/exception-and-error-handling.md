# Exception and Error Handling

“Error handling is important, but if it obscures logic, it’s wrong.” [1](#cite01)

> Low level methods should throw exceptions and high level method who consume them should
> handle those exceptions. Said that high level methods could also throw exceptions if they 
> called by other methods as well.

## [ERR1] Throw exceptions 
Do not clutter your code with a giant try catch. If this is case most probably your function or 
method is not cohesive. Break them up into small functions, methods and make sure these methods
throws exceptions. Have a main method who call these functions with try catch block.

> Remember generally low level methods throws exceptions and high level methods handles them.

_For example:_

```
class Insurance {
 processClaim(claimId, customerId) {
    try {
        let claim = getClaim(claimId);
        let user = getUser(customerId);
        submitClaim(claim, user);
    } 
    catch(e) {
        ExceptionHandler.handleException(e);
        console.log('Cannot proccess claim ', e);
    }
 }
 
 /**
  *
  * @throws Claim does not exists exception
  */
 getClaim(claimId) {
    ...
    throw new Error('Claim does not exists, id: ', claimId); 
 }
 
 /**
  *
  * @throws User not found exception
  */
 getUser(customerId) {
    ...
    throw new Error('User does not exists, id: ', claimId); 
 }
 ...
}
```

## [ERR2] Use good, understandable error messages avoid using error codes.

Your error message should be understandable, and the developer to isolate the issue. Avoid using 
generic messages.

`Error 3487dE` is not very helpful, avoid using error codes.

## References
1. <a id="cite01"></a>Clean Code by Robert C. Martin, Functions, Error Handling

---

[Back to Code Review](../code-review.md)