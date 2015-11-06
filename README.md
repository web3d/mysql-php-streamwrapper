# mysql-php-streamwrapper
php stream wrapper mysql lib

用法:

```php
stream_register_wrapper('tcmysqlfs', 'TimeCheer_StreamWrapper_Adapter_MySQL');

$dir_prefix = 'tcmysqlfs://root@localhost/test';

$file_path = $dir_prefix . '/myapp_dir/sub_dir';

mkdir($file_path);

//写入
$file = $file_path . '/' . time() . '.txt';
$fp = fopen($file, 'w');
if (!$fp) {
    echo 'file resource failed.';
}

fwrite($fp, "asdfasdfa_______ttt");
fclose($fp);

//追加
$fp = fopen($file, 'a');
if (!$fp) {
    echo 'file resource failed.';
}

fwrite($fp, "_appended_");
fwrite($fp, "_appended2222_");
fwrite($fp, "_appended3333_");
fclose($fp);

//读取
$fp = fopen($file, 'r');
if (!$fp) {
    echo 'file resource failed.';
}
echo fread($fp, 20000);
            
fclose($fp);
```

开发日志:

2015-11-06

  1. 确定代码基础结构;
  2. 初步完成目录的创建\删除 mkdir rmdir
  3. 初步完成文件的rwa三种操作
  4. DB操作暂时混杂在业务逻辑中,后续优化