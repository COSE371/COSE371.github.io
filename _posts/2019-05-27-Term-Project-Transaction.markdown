---
layout: post
title: "Term Project: Transaction 기능 구현 예시 (2차 Final Term Project 참고사항)"
categories: term-project
math: true
permalink: tpfinal-transaction
---

```php
<?
include 'config.php';
include "util.php";

$conn = dbconnect($host,$dbid,$dbpass,$dbname);

$music_no = $_POST['music_no'];
$music_name = $_POST['music_name'];
$artist_name = $_POST['artist_name'];
$genre_id = $_POST['genre_id'];
$year = $_POST['year'];
$album = $_POST['album'];
$lyrics = $_POST['lyrics'];

mysqli_query($conn, "set autocommit = 0");	// autocommit 해제
mysqli_query($conn, "set transation isolation level serializable");	// isolation level 설정
mysqli_query($conn, "begin");	// begins a transation

$query = "select artist_name from artist where artist_name='$artist_name'";
$res = mysqli_query($conn, $query);

if(!$res) {
	alert_message('Query Error : '.mysqli_error($conn));
}
$row = mysqli_fetch_array($res);

if($row['artist_name']!=$artist_name){
//	echo"unequal";
	$ret = mysqli_query($conn, "insert into artist set artist_name=\"$artist_name\"");
	if($ret){	// insert new artist successful
	}
	else{	// insert new artist fail
		mysqli_query($conn, "rollback"); // 아티스트 등록 query 수행 실패. 수행 전으로 rollback
		alert_message('Query Error : '.mysqli_error($conn));
	}
}
else {
//	echo"equal";
}
$ret2 = mysqli_query($conn, "insert into music set music_name = \"$music_name\", artist_name = \"$artist_name\", genre_id = \"$genre_id\", album = \"$album\", year = \"$year\", lyrics= \"$lyrics\"");
if(!$ret2){
	mysqli_query($conn, "rollback"); // 음악 등록 query 수행 실패. 수행 전으로 rollback
	alert_message('Query Error : '.mysqli_error($conn));
}
else{
	$music_no = mysqli_insert_id($conn);
	mysqli_query($conn, "commit"); // 음악 등록 query 수행 성공. 수행 내역 commit
	simple_message ('성공적으로 입력 되었습니다');
	echo "<meta http-equiv='refresh' content='0;url=music_detail.php?music_no=$music_no'>";
}

?>
```