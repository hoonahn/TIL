## Runtime error with Navigation Stack
- - -
#### Error catching during Ionic2 framework project - 2017/04/05

Got an error after navigation, such as Signup, Signin.

Error looks like this;

<pre><code>Runtime Error
Uncaught (in promise): false
Stack
Error: Uncaught (in promise): false
    at v (http://localhost:8100/build/polyfills.js:3:4864)
    at s (http://localhost:8100/build/polyfills.js:3:4289)
    at s (http://localhost:8100/build/polyfills.js:3:4112)
    at http://localhost:8100/build/polyfills.js:3:4652
    at t.invokeTask (http://localhost:8100/build/polyfills.js:3:10284)
    at Object.onInvokeTask (http://localhost:8100/build/main.js:37676:37)
    at t.invokeTask (http://localhost:8100/build/polyfills.js:3:10220)
    at e.runTask (http://localhost:8100/build/polyfills.js:3:7637)
    at i (http://localhost:8100/build/polyfills.js:3:3707)</code></pre>

I thought that this error was related to Ionic2 ```NavController``` and tried to solve it.
But additionally there was one thing more, ```LoadingController```.

There were two situation causing error above.

##### 1. After calling ```NavController.setRoot()``` method.

This case was about setting a view( or a page ) as a Root which is pushed by ```NavController.push``` from other view setted as Root.
So I just changed ```NavController.setRoot``` to ```NavController.pop``` and the problem was solved.

##### 2. Handling ```LoadingController``` with ```LoadingController.dismiss()``` method.

 This case is not solved clearly, but the error didn't appear.
 When the LoadingController is created, ```dismissOnPageChange: true``` field was set as true. However I saw some people arguing about LoadingController, and that ```dismissOnPageChange``` field doesn't works well. Therefore I turned ```dismissOnPageChange: false``` and manually dismissed the LoadingController after page is changed using ```LoadingController.dismiss()```. Then the error disappeared. But I don't think this is the optimal solution. I will update after figuring it out.
