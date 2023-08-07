# Skellitnizer
Define a SekellFile (.skl)

# Tags
[!KEY:VALUE0:VALUE1]
- ":" can be excaped with a "\\" (single slash)
    - Ex [!KEY:SOME\:VAL] -> Key = "SOME:VAL"

## Defined Tags

|Key|Use|Args|
|---|---|---|
|STR_DEFS|Defines all string varables used in this skl file|No Args|
|FILE|Defines a new file to be added to the resault|[0] FileName

# String Defs

- All definitions must exist in the DEFS tag, there may only be one DEFS tag in the skl file 
- Varables must start and end with "__"
- String Constants in Varable Definitions must start with `"_$"` and end with `"$_"`
- `__` , `_$` , `$_` may be excaped with normal C style excaping `'\'`
- `<FORMATTER_TAG>` may be used to format strings

## Formatters

### Use
Formaters are applied when using a varable, The format goes before the varables closing `__`

#### Example
`__SOMEVAR<CC>__`

### Avalable
Input str for table "This is Some string"
|Tag|Resault|Notes|
|---|---|---|
|SC|this_is_some_string| Snake Case, all lowercase replace space with '_'
|CC|ThisIsSomeString| Cammel Case, First Letter After Space To Upper, all else lower, Remove Spaces
|NS|ThisisSomestring| No Spaces, Just blindly remove all spaces



# Defs

``` skl
[!STR_DEFS]
__PROGRAM_NAME__=Some Program Name


[!FILE:./FileA.sh]
#!/bin/bash
echo Hello world from file A

[!FILE:./src/__PROGRAM_NAME<SC>__.c] #File = ./src/some_program_name.c
void main(void){

}
```