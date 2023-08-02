## Work log 

A PHP 

Regex 

------


## Problem

Search ip with * 


## How it solved?

``` php
$search_txt_reg = $search_txt;
$search_txt_reg = str_replace('*', '[0-9]{1,3}', $search_txt_reg);
$search_txt_reg = str_replace('.', '\.', $search_txt_reg);
$search_ip_pattern = "{$search_txt_reg}";


and add it to query
$sql_search = "AND {$colname} REGEXP ('{$search_ip_pattern}') ";

```


