file: t.php
```
<?php
error_reporting(E_ALL^E_NOTICE);
function _exception_handler($e)
{
	var_dump($e);exit(1);
}
set_exception_handler('_exception_handler'); 
spl_autoload_register(function($className) {
	$php = $className . ".php";
	$ret = require_once $php;
	return true;
});
spl_autoload_register(function($className) {
        $php = "namespace\\" . $className . ".php";
        $ret = require_once $php;
        echo $e->getMessage();
        return true;
});
new mytest();
```
file: mytest.php
```
<?php
class mytest {
	fdsaf;//parse error
}
```
