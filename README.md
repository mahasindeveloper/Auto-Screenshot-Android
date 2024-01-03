<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Auto Screenshot Android App - PHP Backend</title>
  <style>
    /* Add some basic styling for better readability */
    body {
      font-family: Arial, sans-serif;
      line-height: 1.6;
      margin: 20px;
    }
    h1 {
      text-align: center;
    }
    .code {
      background-color: #f4f4f4;
      padding: 10px;
      margin-bottom: 20px;
    }
  </style>
</head>
<body>
  <h1>Auto Screenshot Android App - PHP Backend</h1>
  
  <h2>About</h2>
  <p>
    This project includes PHP backend scripts for an Android app that automates screenshot capturing and uploading to a server.
  </p>
  
  <h2>connection.php</h2>
  <div class="code">
<?php  
$con = mysqli_connect('localhost', 'id19231404_root', 'Mahasin@786', 'id19231404_smsbot');
 if (mysqli_connect_errno()){  
   echo "Connection Faild <br> " . mysqli_connect_error();  
 } else {  
   echo "Database Connected";  
 }  
 ?>
  </div>
  
  <h2>upload_img.php</h2>
  <div class="code">
   <?php  
$con = mysqli_connect('localhost', 'id19231404_root', 'Mahasin@786', 'id19231404_smsbot');
if (mysqli_connect_errno()){  
   echo "Connection Faild <br> " . mysqli_connect_error();  
 } else {  
   echo "Database Connected";  
 }  
 
 if(isset($_POST['images'])){  
     
   $target_path = "Images/";  
   $image = $_POST['images'];  
   $imageStore = rand()."_".time().".jpeg";  
   $target_path = $target_path."/".$imageStore;  
   file_put_contents($target_path, base64_decode($image));  
   
   $result=array();
   $select = "INSERT INTO usersData (images) VALUES ('$imageStore')";  
   $response = mysqli_query($con,$select);  
   
   if($response){  
     echo "Image Upload";  
     mysqli_close($con);  
   } else{  
     echo "Something Wrong";  
   }  
 }  
 ?>  
  </div>
  
  <!-- You can add an app screenshot by using the <img> tag and specifying the image URL -->
  <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcREsLKdgR4JPQ8B6LjeoCnlF8XBYwgh4OwXYg&usqp=CAU" alt="Auto Screenshot Android App Screenshot" style="max-width: 100%; height: auto; display: block; margin: 20px auto;">
</body>
</html>
