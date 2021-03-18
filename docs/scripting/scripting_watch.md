---
layout: default
title: Symbol API (Watch)
parent: Scripting
nav_order: 2
---

# `SymbolManager x2c_symbol`

Symbol Control Interface. Variable preinitialised as `ISymbolManager`.


## `String[] getSymbolIdentifiers()`

Returns a list of all known symbol identifiers.

 * **Returns:** Array of symbol identifiers


## `String[] getSymbolIdentifiers(String identifier) throws Exception`

Returns a list of all known sub-element identifier names.<br> Example: symbol identifier = "mystruct", returns "mystruct.a" and "mystruct.b" which can itself be used in all other methods of this interface. <ul> <li>mystruct.a is a value &rarr; use it in other methods as valid identifier</li> <li>mystruct.a is a struct &rarr; use it in this method to get sub-member identifiers</li> </ul>

 * **Parameters:** `identifier` — Symbol identifier
 * **Returns:** Array of symbol identifiers or null if element doesn't contain sub-elements
 * **Exceptions:** `Exception` — if invalid identifier

## `ISymbol getSymbol(String identifier) throws Exception`

Returns Symbol.

 * **Parameters:** `identifier` — Symbol identfier
 * **Returns:** Symbol - reference to a variable
 * **Exceptions:** `Exception` — if invalid symbol identfier

###  Example
```
symbol = x2c_symbol.getSymbol("myStruct.ledOn") # get myStruct.ledOn variable reference
symbol.getScaledValue() #Get the actual value of the variable
```

# `Symbol`

Symbol class. Direct access to variables. getSymbol() return type.

## `String[] getSymbolIdentifiers()`

Returns a list of all known sub-element identifier names.<br> If element is a C structure or array, the <b>full</b> names will be returned. Example:<br> In case of struct: structName.member1, structName.member2<br> In case of an array: arrayName[0], arrayName[1]<br> <br> If the element doesn't contain any sub-elements, null will be returned.

 * **Returns:** Member symbol identifiers or null if element doesn't contain

     sub-elements

## `void updateValue() throws Exception`

Updates (Uploads) value from target.

 * **Exceptions:** `Exception` — if communication problem occurs

## `void setValue(double value) throws Exception`

Sets raw value and downloads it to the target.

 * **Parameters:** `value` — Value
 * **Exceptions:** `Exception` — if a communication problem occurs

## `double getValue()`

Returns current raw value.

 * **Returns:** Raw value

## `void setScaledValue(double value) throws Exception`

Sets scaled value and downloads it to the target.

 * **Parameters:** `value` — Scaled value
 * **Exceptions:** `Exception` — if a communication problem occurs

## `double getScaledValue()`

Returns current scaled value.

 * **Returns:** Scaled value

## `void setScaling(double scaling)`

Sets scaling.

 * **Parameters:** `scaling` — Scaling

## `double getScaling()`

Returns scaling.

 * **Returns:** Scaling

## `void setOffset(double offset)`

Sets offset.

 * **Parameters:** `offset` — Offset

## `double getOffset()`

Returns offset.

 * **Returns:** Offset

## `void setUnit(String unit)`

Sets unit label.

 * **Parameters:** `unit` — Unit label

## `String getUnit()`

Returns unit label.

 * **Returns:** Unit label