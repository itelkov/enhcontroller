EnhController
=============

Enhanced controller for Laravel 4


# Usage #


Declare controller class

```
namespace MyNamespace;

use Selket\EnhController;

Class MyController extends EnhController\Controller implements EnhController\ControllerInterface {

	public $map = [
		1 => 'MyNamespace\MyAction1',
		2 => 'MyNamespace\MyAction2',
	];

	function __construct(EnhController\Mapper $mapper)
	{
		parent::__construct($mapper);
	}
}
```

Declare accepted action classes

```
namespace MyNamespace;

use Selket\EnhController;

Class MyAction1 extends EnhController\Action implements EnhController\ActionInterface {

	public function call() {
		return 'Hellow world!';
	}
}

Class MyAction2 extends EnhController\Action implements EnhController\ActionInterface {

	public function call() {
		return $this->controller->call(1); // calls internally action MyNamespace\MyAction1
	}
}
```

Define routing

```
// by action class name
Route::get('foo', 'MyNamespace\MyController@MyNamespace\MyAction1');

// by action numeric key
Route::get('foo', 'MyNamespace\MyController@2');
```
