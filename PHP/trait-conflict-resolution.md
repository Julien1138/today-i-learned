# Trait method conflict and how to resolve it

If two Traits insert a method with the same name, a fatal error is produced, if the conflict is not explicitly resolved. To resolve, the `insteadof` operator needs to be used as follow :
```php
trait A {
    public function talk() {
        echo 'a';
    }
}

trait B {
    public function talk() {
        echo 'b';
    }
}

class Talker {
    use A, B {
        B::talk insteadof A;
    }
}
```
In this example, the method `talk()` of `Trait B` will be used everywhere in this class, and the method `talk()` of `Trait A` will be ignored.

[more info](https://www.php.net/manual/en/language.oop5.traits.php)