# Top mistakes

1. There are two arrays. The task is do something related to both of them. For example, create a new array with some rules.
Mistake: Write a `for loop` for the first array and make some checks for the second array inside. But if the second array has
unique for first array values then some of values won't be processed.

1. Many very simular operations, like copy-paste with small changes. Mistake: forget to change values for the `last` copy pasted
element. Strange, but it happens extremely often.

1. There is an array of elements. Mistake: Most of the development are concentrated around desting business logic with only one element. Solution: In all tests create at least two elements.

1. Time estimation. Many tiny tasks. Every task cost is around half a hour. But there are 20 tasks. Total brave estimate could be 4 hours, but actually it will be 10 hours `for a such simple bunch of tasks`

1. Compexity growth. There is an existing code. Task is to add a small business workflow. But it is a bit different than existing workflow. As a result, a refactoring is required because if you add a feature `as-is` then overall complexity will be too high. Same rule - for the legacy code.

To be continued...
