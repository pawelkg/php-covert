<h6 align="center">
    <img src="https://github.com/stephenlake/php-covert/blob/master/docs/assets/php-covert-banner.png?v=2" width="300"/>
</h6>

<h6 align="center">
    Execute code as a background system process for Linux, Mac and Windows without relying on any external dependencies.
</h6>

<br>

# PHP Covert
**PHP Covert** makes running inline code as background tasks in PHP a piece of cake without the need to install external software. Plan your operation and execute it instantly as a background process.

Made with ❤️ by [Stephen Lake](http://stephenlake.github.io/)

## Getting Started
Install the package via composer.

    composer require stephenlake/php-covert

Try it!

```php
use Covert\Operation;

$operation = new Operation();
$operation->setLoggingFile('log.txt');
$operation->execute(function() {
     $counter = 0;
     
     while($counter < 120) {
        $counter++;
        sleep(1);
        echo "I have been running in the background for {$counter} seconds!".PHP_EOL;
     }
});
```
That's it. Your task is now running in the background as a process. Get the process ID with `$operation->getProcessID()`. Check out the [documentation](https://stephenlake.github.io/php-covert) for further usage and features.

## Caveats
- Covert runs background tasks as a new separate PHP process for each operation executed, because of this it is not aware of namespaced imports and currently cannot figure out which classes belong to which namespace, therefore when defining the anonymous function, it's important to remember to use classes' fully qualified namespace otherwise the process will fail.  

## License

This library is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.
