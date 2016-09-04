# README - en
This repository holds all interfaces defined by [streamWrapper](http://www.php.net/manual/en/class.streamwrapper.php).

An instance of this class is initialized as soon as a stream function tries to access the protocol it is associated with.

⚠️*Note:*
This is NOT a real class, only a prototype of how a class defining its own protocol should be.

# 关于 - 中文
这个包实现了[streamWrapper](http://php.net/manual/zh/class.streamwrapper.php)中所要求的所有接口

这个接口类的实例将可以注册后使用流的形势访问。

⚠️*️注意：*
这个包的class不是一个实例，而是一个可以规范实例需要完成的方法的接口类。

# Composer
```shell
composer require medz/stream-wrapper-interface
```

# Demo
```php
use Medz\Component\WrapperInterface\WrapperInterface

class DemoStream implements WrapperInterface
{
    /**
     * Enter description here...
     *
     * @param string $path
     * @param string $mode
     * @param int    $options
     * @param string &$opened_path
     *
     * @return bool
     */
    public function stream_open($path, $mode, $options, &$opened_path)
    {
        // TODO
    }
}

```
## Register this object as stream wrapper. 注册这个streamWrapper.
```php
stream_register_wrapper('demo', 'DemoStream');
```

## use the wrapper client. 使用这个注册的自定义流协议。
```php
// get
file_get_contents('demo://test.txt');

// put
file_put_contents('demo://test.txt', 'This is a test content.');
```

## Use vendor package. 使用第三方包

`(symfony/finder)`:
```php
use Symfony\Component\Finder\Finder;

$finder = new Finder();
$finder->files()->in('demo://src');

foreach ($finder as $file)
{
    var_dump($file);
}
```
# Use the package for Aliyun OSS SDK. 使用这个接口的阿里云sdk。
[medz/oss-stream-wrapper](https://packagist.org/packages/medz/oss-stream-wrapper) alias [medz/aliyun-oss](https://packagist.org/packages/medz/aliyun-oss)

# License:
MIT
