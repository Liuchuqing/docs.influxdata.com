---
title: toString() function
description: The toString() function converts a value to a string.
aliases:
  - /flux/v0.50/functions/transformations/type-conversions/tostring
  - /flux/v0.50/functions/built-in/transformations/type-conversions/tostring/
menu:
  flux_0_50:
    name: toString
    parent: built-in-type-conversions
    weight: 1
---

The `toString()` function converts a value to a string.

_**Function type:** Type conversion_  
_**Output data type:** String_

```js
toString()
```

{{% note %}}
To convert values in a column other than `_value`, define a custom function
patterned after the [function definition](#function-definition),
but replace `_value` with your desired column.
{{% /note %}}

## Examples
```js
from(bucket: "telegraf")
  |> filter(fn:(r) =>
    r._measurement == "mem" and
    r._field == "used"
  )
  |> toString()
```

## Function definition
```js
toString = (tables=<-) =>
  tables
    |> map(fn:(r) => ({ r with _value: string(v: r._value) }))
```
