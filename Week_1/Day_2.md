### Summary of Day 2
&nbsp;


#### `Git`

* What's Git?<br> Version Control, Back up copy on Github, keeps a history of the code by commiting and help work better as a team.<br>
* each folder should have only one git repository
* `git commands?` <br> `git add . / git log / git status / git remote -v and etc / git reset --hard <gitaddress>` (Delete updated git) <br>
&nbsp;


#### `How to approach problem solving?`
1. state the hypothesis
2. verify the hypothesis
3. make changes <br>

* Divide problems into step by step -> regular case and edge case, work on regular case first (Happy Path) -> console.log as many as possible to check the process. (`console.log("Args:, arg`))<br>

&nbsp;


#### `return vs process.exit()`

* process.exit() has meaning of our intention to exit the code when return doesn't have any specific meaning in it.

#### `Pseudocode`
* Pseudocode can be especially helpful while not fluent or proficient in the given programming language.

* It allows the writer to detach from the syntax of the language and focus solely on the logic itself.

#### `function` <br>
1. Benefits of functon : reusable, has name which gives us clear idea of what it does.
2. how to name of function : follow the conventions.
3. function should focus on a single task.
4. Data should be passed into as parameter/arguments(local scope)
5. 2 types of function : function expression & function declaration 



#### `global scope vs local scope` <br>
global scope is avaiable anywhere whereas local scope is avaiable only where it's defined.



#### `stack trace`

#### `type coercion` <br>

* 자료형을 다른형태로 해주는것. 마치 숫자0이 상황에 따라 falshy값이 되는것처럼.

* JavaScript will perform a `type conversion with the double equals(==)` and we might get an unexpected result. That's why most of the time we should use the triple equals (===) because it makes the comparison more predictable.

#### `truthy value vs falshy value` <br>
* most of them are truthy except `0, false, "", null, undefined, NaN`. <br>
* when do we use? truthy values are a fast and easy way to check conditions in our code. `if(!shoppingList.length){}`


#### `New Vocabularies` 

* typecast
* modulo operator %
* pseudocode (almost code)
* double equal operators ==
* triple equal operators ===
