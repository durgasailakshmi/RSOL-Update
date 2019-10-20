<?php  
include 'vendor/autoload.php';
  use \Mailjet\Resources;
$host = 'localhost';  
$user = 'root';  
$pass = '';  
$dbname = 'recycle'; 
session_start();

$conn = mysqli_connect($host, $user, $pass,$dbname);  
if(!$conn){  
  die('Could not connect: '.mysqli_connect_error());  
}  
echo 'Connected successfully<br/>';  
$user1=$_SESSION['username'];
$buyer=$_SESSION['username1']; 
$locality=$_SESSION['location3'];
$address1=$_SESSION['address2'];
$timing=$_SESSION['time2'];
$sql = "INSERT INTO userbuyer(user,buyer,location,address,time) VALUES ('$user1', '$buyer','$locality','$address1','$timing')";
if(mysqli_query($conn, $sql)){  
 echo "successfully Sent"; 
 
  $mj = new \Mailjet\Client('2bd4f6458d847848d7a1cc2da33b169d','fc16058c3265516e1f1caccfd9cedc74',true,['version' => 'v3.1']);
    $email = $_SESSION['email1'];
  $body = [
    'Messages' => [
      [
        'From' => [
          'Email' => "saigrace2000@gmail.com",
          'Name' => "Durga Sai Lakshmi"
        ],
        'To' => [
          [
            'Email' => $email,
            'Name' => "Durga"
          ]
        ],
        'Subject' => "This is From rsol",
        'TextPart' => "My first Mailjet email",
        'HTMLPart' => "The customer Named ".$user1." has some recycling items in address ".$address1." The Timing the user is available is ".$timing,
        'CustomID' => "AppGettingStartedTest"
      ]
    ]
  ];
  $response = $mj->post(Resources::$Email, ['body' => $body]);
  $response->success() && var_dump($response->getData());
}else{  
echo "Not able to send it: ". mysqli_error($conn);  
}  
mysqli_close($conn);  
?>  