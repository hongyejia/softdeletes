<h1 align="center"> softDeletes </h1>

<p align="center"> laravel softDeletes change.</p>


## 前言
Laravel 内置的软删除功能是一个非常方便的功能，但是这个功能有个很大的缺点：使用了软删功能会导致不能给字段增加唯一索引（unique）。因为一旦给数据表增加了唯一索引，那么被软删的数据很容易就与未删除的正常数据产生冲突，在绝大多数业务中这种情况都是不允许发生的！比如用户表的手机号，邮箱等。

Laravel 软删除的的默认值是 NULL， mysql 中如果联合索引中字段值为null,将会使联合索引的唯一约束失效。

所以如果你的数据表中的字段有需要保持唯一性的需求，一旦使用 Laravel 内置的软软删除功能，那就需要靠程序逻辑去保证字段的唯一性，这会给日常开发带来很多不必要的麻烦，增加不必要的开销！大大降低了程序的的性能。

Laravel 内置的软删除功能的另外一个不足就是被软删除的数据一般都是很少用到的，所以跟正常数据放在同一张数据表对性能也会有所影响。


## Installing

```shell
$ composer require hongyejia/softDeletes 
```

## Usage

```angular2html
<?php


namespace App\Http\Model;


use Hongyejia\SoftDeletes\laravelSoftDeletes;
use Illuminate\Database\Eloquent\Model;

class BaseModel extends Model
{
    use laravelSoftDeletes;
   
}
```

软删除的详细操作，详见官方文档

### database
```angular2html
`deleted_at` int(10) unsigned NOT NULL DEFAULT '0' COMMENT '删除时间';
```

## Contributing

You can contribute in one of three ways:

1. File bug reports using the [issue tracker](https://github.com/hongyejia/softDeletes/issues).
2. Answer questions or fix bugs on the [issue tracker](https://github.com/hongyejia/softDeletes/issues).
3. Contribute new features or update the wiki.

_The code contribution process is not very formal. You just need to make sure that you follow the PSR-0, PSR-1, and PSR-2 coding guidelines. Any new code contributions must be accompanied by unit tests where applicable._

## License

MIT