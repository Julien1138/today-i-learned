# Return Collection as Resource
Returning a Collection of objects as a JSon resource mays seem easy but there is a little something I did not do at first, and it caused me trouble when a started arranging the collection à passed to the Resource object.

```php
    /**
     * Transform the resource collection into an array.
     *
     * @param  \Illuminate\Http\Request
     * @return array
     */
    public function toArray($request)
    {
        return [
            'data' => $this->collection->map(function ($category) {
                return [
                    'id' => $category->id,
                    'document_id' => $category->document_id,
                    'parent_id' => $category->parent_id,
                    'name' => $category->name,
                    'acronym' => $category->acronym,
                    'order' => (int) $category->order,
                ];
            })->values(),
        ];
    }
```
The thing to not forget is the `->values()` at the end.
