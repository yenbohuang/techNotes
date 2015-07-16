The following contents are copied from manual.

|Name|Aliases|Description|
|----|-------|-----------|
|`bigint`|`int8`|signed eight-byte integer|
|`bigserial`|`serial8`|autoincrement|
|`boolean`|`bool`|logical Boolean (true/false)|
|`bytea`| |binary data (“byte array”)|
|`character varying [(n)]`|`varchar [(n)]`|variable-length character string|
|`character [(n)]`|`char [(n)]`|ﬁxed-length character string|
|`double precision`|`float8`|double precision ﬂoating-point number (8 bytes)|
|`text`||variable-length character string|
|`uuid`||universally unique identiﬁer|
|`timestamp [(p)] with time zone`|`timestamptz`|date and time, including time zone|



|Name|Description (2D only)|Example|
|----|---------------------|-------|
|`lseg`|line segment on a plane|`[ ( x1 , y1 ) , ( x2 , y2 ) ]`|
|`path`|geometric path on a plane|`[ ( x1 , y1 ) , ... , ( xn , yn ) ]` or `( ( x1 , y1 ) , ... , ( xn , yn ) )`. `[]` -> open path, `()` -> closed path|
|`point`|geometric point on a plane|`( x , y )`|
|`polygon`|closed geometric path on a plane|`( ( x1 , y1 ) , ... , ( xn , yn ) )`|
|`circle`|circle on a plane|`< ( x , y ) , r >`|


|Name|Description|
|----|-----------|
|`json`|textual JSON data|
|`xml`|XML data|
|`jsonb`|Binary JSON data (preferred)|