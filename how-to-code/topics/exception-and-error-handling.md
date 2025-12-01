# Exception and Error Handling

“Error handling is important, but if it obscures logic, it’s wrong.” [1](#cite01)

> Low level methods should throw exceptions and high level method who consume them should
> handle (catch) those exceptions. Said that high level methods could also throw exceptions if they 
> called by other methods as well.

## [ERR1] Catch must leave the program in good state, whatever happens in try.

## [ERR2] Throw exceptions 
Do not clutter your code with a giant try catch. If this is case most probably your function or 
method is not cohesive. Break them up into small functions, methods and make sure these methods
throws exceptions. Have a main method who call these functions with try catch block.

> Remember generally low level methods throws exceptions and high level methods handles them.

"Each exception that you throw should provide enough context to determine the source and location of an error." [1](#cite01)

_For example:_

```javascript
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
  * @throws Claim does not exists exception.
  */
 getClaim(claimId) {
    ...
    throw new Error('Claim does not exists, id: ', claimId); 
 }
 
 /**
  *
  * @throws User not found exception.
  */
 getUser(customerId) {
    ...
    throw new Error('User does not exists, id: ', claimId); 
 }
 ...
}
```

## [ERR3] Extract try and catch blocks out into functions of their own.

Your intent will be clear as well as your code.

_For example:_

```javascript
try {
    deleteUserReferences(userId);
}
catch (e) {
    ...
}
```

## [ERR4] Use good, understandable error messages avoid using error codes.

"Create informative error messages and pass them along with your exceptions. 
Mention the operation that failed and the type of failure. 
If you are logging in your application, pass along enough information to be able 
to log the error in your catch." [1](#cite01)

Your error messages should be understandable, and help the developer to isolate the issue. Avoid using 
generic and cryptic messages.

`Error 3487dE` is not very helpful, avoid using error codes.

`There is a problem, contact system admin.` is not helpful either, actually it makes it worse.

## References
1. <a id="cite01"></a>Clean Code by Robert C. Martin, Functions, Error Handling

---

[Back to Code Review](../code-review.md)