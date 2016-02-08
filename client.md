## Here is a helper to call Template helper functions inside jasmine tests:

callHelper = (template, helperName, context, args) ->
  context = context or {}
  args = args or []
  Template[template].__helpers[' ' + helperName].apply(context, args)

There is no way to access collection methods directly as to spy on them