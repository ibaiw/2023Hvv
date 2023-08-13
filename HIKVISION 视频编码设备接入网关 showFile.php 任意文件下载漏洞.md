```
<?php
          $file_name = $_GET['fileName'];
          $file_path = '../../../log/'.$file_name;
          $fp = fopen($file_path, "r");
          while($line = fgets($fp)){
            $line = nl2br(htmlentities($line, ENT_COMPAT, "utf-8"));
            echo '<span style="font-size:16px">'.$line.'</span>';
          }
          fclose($fp);
?>
```



```
/serverLog/showFile.php?fileName=../web/html/main.php
```

