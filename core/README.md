> 为 Envision 创建的服务端 PHP 面向对象基类

## Using The Class


### Database Credentials

在 `/config/database.config.php` 中配置数据库的各项信息。

```php
private $db_host = "localhost";  // Change as required
private $db_user = "username";  // Change as required
private $db_pass = "password";  // Change as required
private $db_name = "database";	// Change as required
```

### Test MySQLi


**Select Example**

查找示例。

```php
<?php
include('/core/class.database.php');
$db = new Database();
$db->connect();
$db->select('table_name'); // 表名
$res = $db->getResult();
print_r($res);
```

或者使用更详细的参数来查找：

```php
<?php
include('/core/class.database.php');
$db = new Database();
$db->connect();
$db->select('table_name','id,name','name="Name 1"','id DESC'); // 表名, 字段名, WHERE 条件, ORDER BY 条件
$res = $db->getResult();
print_r($res);
```

**Update Example**

更新数据示例

```php
<?php
include('/core/class.database.php');
$db = new Database();
$db->connect();
$db->update('table_name',array('name'=>"Name 4",'email'=>"name4@email.com"),'id="1" AND name="Name 1"'); // 表名, 字段名和字段值, WHERE 条件
$res = $db->getResult();
print_r($res);
```

**Insert Example**

插入数据示例。

```php
<?php
include('core/class.database.php');
$db = new Database();
$db->connect();
$data = $db->escapeString("name5@email.com"); // 可以借助 escapeString 来将字符串转为小写
$db->insert('table_name',array('name'=>'Name 5','email'=>$data));  // 表名, 字段名 和 字段值 组成的数组
$res = $db->getResult();  
print_r($res);
```

**Delete Example**

删除数据记录示例。

```php
<?php
include('core/class.database.php');
$db = new Database();
$db->connect();
$db->delete('table_name','id=5');  // 表名, WHERE 条件
$res = $db->getResult();  
print_r($res);
```