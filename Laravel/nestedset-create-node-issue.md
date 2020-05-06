# Creating a new model using the NestedSet NodeTrait fails (not found)
Creating a model as follow would not work and return a "not found" exception :
```php
$data = [
    'name' => 'Some category',
    'parent_id' => '6c5deea0-87ac-11ea-87aa-0d8e79776d7a',
    'document_id' => '6b5d0250-87ac-11ea-83a9-f9f3a62e4dcf',
]

$category = Category::create($data);
```
The reason why it does not work is that my nested set model is scoped on `document_id` and this index was last in the array (or at least after parent_id) passed to `create()`. I do not have a handle on the order of the array elements because they come out of a request.

My solution is then to reorder the array to make sure the scoped index is first (or at least before `parent_id`) before passing it to the `create()` function.

[Issue on GitHub](https://github.com/lazychaser/laravel-nestedset/issues/204)