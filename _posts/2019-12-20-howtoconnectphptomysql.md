---
layout: post
title: How to Connect PHP to MySQL
category: 03_Database
tag: [MySql, Connect]
---

 


> It is recommended to use mysqli and PDO_MySQL. In this tutorial, mysqli is used.


----



```
<?php
$conn = mysqli_connect(
  'localhost',
  'root',
  '11111',
  'opentutorials');

$sql = "SELECT * FROM topic";
$result = mysqli_query($conn, $sql);
$list = '';

while($row = mysqli_fetch_array($result)) {
  $escaped_title = htmlspecialchars($row['title']);
  $list = $list."<li><a href=\"index.php?id={$row['id']}\">{$escaped_title}</a></li>";

}

$article = array(
  'title'=>'Welcome',
  'description'=>'Hello, web'
);

if(isset($_GET['id'])) {
  $filtered_id = mysqli_real_escape_string($conn, $_GET['id']);
  $sql = "SELECT * FROM topic WHERE id={$filtered_id}";
  $result = mysqli_query($conn, $sql);
  $row = mysqli_fetch_array($result);
  $article['title'] = htmlspecialchars($row['title']);
  $article['description'] = htmlspecialchars($row['description']);
}

?>

<!doctype html>
<html>a
  <head>
    <meta charset="utf-8">
    <title>WEB</title>
  </head>

  <body>
    <h1><a href="index.php">WEB</a></h1>
    <ol>
      <?=$list?>
    </ol>
    <a href="create.php">create</a>
    <h2><?=$article['title']?></h2>
    <?=$article['description']?>
  </body>
</html> 
```