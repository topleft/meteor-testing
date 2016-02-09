
Testing helpers

Keys for client side integration testing:

* create data/instances in before each statement or inside of it statement, do not rely on seeded data. This ensures that you know exactly what you are testing against and do not have to change your tests if seed data changes.

```coffee
# Good
customer = new POS.Customer {
    name: 'Bo Jangle'
    ...
  }

# Bad
customer = POS.Customers.find({})[0]

```

* Isolate pieces of code as much as possible. Ideally your test is looking for one function to do its job properly. This means that functions inside of the function being tested should be stubbed or spied and forced to return the value you would expect. (You can test that the internal function do there job in a separate test.)

```coffee

item.anotherFunction = function()
util.amazingFunction = function()

someFunction = (item) ->

  value = item.anotherFunction()

  result = util.amazingFunction(value)

  result

```

```coffee
popcorn = {
  value: 500,
  kernel: 6
}

describe 'someFunction', ->
  it "should do exactly one thing", ->
    spyOn('item', anotherFunction).and.returnValue(500)
    spyOn('util', amazingFunction).andReturnValue(true)

    result = someFunction(popcorn)

    expect(item.anotherFunction).toHaveBeenCalled()
    expect(util.amazingFunction).toHaveBeenCalled()
    expect(result).toBe 1.5
```

This tests the purpose of someFunction(): to call two other functions and return a value of 1.5 if anotherFunction returns `500` and amazingFunction returns `true`.


## Here is a helper to call Template helper functions inside jasmine tests:

```coffee
callHelper = (template, helperName, context, args) ->
  context = context or {}
  args = args or []
  Template[template].__helpers[' ' + helperName].apply(context, args)
```

There is no way to access collection methods directly as to spy on them
