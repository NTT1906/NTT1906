is_null() emits a WARNING if variable is not set, but isset() and empty() don't.

$a - variable with not null value (e.g. TRUE)
$b - variable with null value. `$b = null;`
$c - not declared variable
$d - variable with value that cast to FALSE (e.g. empty string, FALSE or empty array)
$e - variable declared, but without any value assigned
$a->a - declared, but not assigned object property. (`public $a;`)
A::$a - declared, but not assigned static class property.

         |   $a  |   $b  |   $c  |   $d  |   $e  | $a->a | A::$a |
---------+-------+-------+-------+-------+-------+-------+-------+
is_null()| FALSE | TRUE  |TRUE*W | FALSE | TRUE*W| TRUE  | TRUE  |
---------+-------+-------+-------+-------+-------+-------+-------+
isset()  | TRUE  | FALSE | FALSE | TRUE  | FALSE | FALSE | FALSE |
---------+-------+-------+-------+-------+-------+-------+-------+
empty()  | FALSE | TRUE  | TRUE  | TRUE  | TRUE  | TRUE  | TRUE  |
---------+-------+-------+-------+-------+-------+-------+-------+
null === | FALSE | TRUE  |TRUE*W | FALSE | TRUE*W| TRUE  | TRUE  |
---------+-------+-------+-------+-------+-------+-------+-------+
null ==  | FALSE | TRUE  |TRUE*W | TRUE  | TRUE*W| TRUE  | TRUE  |
---------+-------+-------+-------+-------+-------+-------+-------+

TRUE*W - function return TRUE, but same time emits WARNING.
