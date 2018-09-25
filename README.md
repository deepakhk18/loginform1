

    
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1">
<title>Jotorres Login Form</title>
</head>
<body>
    <form method="post" action="validate_login.php" >
        <table border="1" >
            <tr>
                <td><label for="users_email">Email</label></td>
                <td><input type="text" 

                  name="users_email" id="users_email"></td>
            </tr>
            <tr>
                <td><label for="users_pass">Password</label></td>
                <td><input name="users_pass" 

                  type="password" id="users_pass"></input></td>
            </tr>
            <tr>
                <td><input type="submit" value="Submit"/>
                <td><input type="reset" value="Reset"/>
            </tr>
        </table>
    </form>
</body>
</html>
<?php

// Grab User submitted information
$username = $_POST["UserName"];
$password = $_POST["Password"];

$con = mysql_connect("localhost","root","");
if($con)
{
echo "connected successfully";
}
if(!$con)
{
    die('Connection Failed'.mysql_error());
}


mysql_select_db("noticeboard",$con);

$result = mysql_query("SELECT UserName,Password FROM Login WHERE UserName = $username");
//$result2 = mysql_query($SELECT UserName,Password FROM Login WHERE UserName = $username) or die($SELECT UserName,Password FROM Login WHERE UserName = $username."<br/><br/>".mysql_error());

$row = mysql_fetch_array($result);

if($row["UserName"]==$username && $row["Password"]==$password)
    echo "You are a validated user.";
else
    echo "Sorry,your credentials are not valid, Please try again.";
?>
