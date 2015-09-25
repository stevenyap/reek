## Introduction

Classes should use their private methods otherwise this is dead
code, which is confusing, error-prone and bad for maintenance. 

## Example

Given:

```Ruby
class Car
  private
  def self.start_the_engine; end
  def drive; end
end
```

`Reek` would emit the following warning:

```
2 warnings:
  [1]:Car has the unused private class method `start_the_engine` (UnusedPrivateMethod)
  [1]:Car has the unused private instance method `drive` (UnusedPrivateMethod)
```

As you can see above, `Unused Private Method` does differentiate between class
and instance methods. Private methods that are called via `dynamic dispatch`
will trigger a false alarm since detecting something like this is far out of
scope for `Reek`.

## Configuration

`Unused Private Method` offers the [Basic Smell Options](Basic-Smell-Options.md).
