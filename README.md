<!DOCTYPE HTML>  
<html>
<head>
<style>
.error {color: #FF0008;}
</style>
</head>
<body>  

<?php

$nameErr = $emailErr = $genderErr = $martialstatusErr = $phonenumberErr = $addressErr = $icnumberErr = $hiredateErr = $departmentErr = "";

$name = $email = $gender = $martialstatus = $phonenumber = $address = $icnumber = $hiredate = $department = "";



if ($_SERVER["REQUEST_METHOD"] == "POST") {
  if (empty($_POST["name"])) {
    $nameErr = "Name is required";
  } else {
    $name = test_input($_POST["name"]);
    
    if (!preg_match("/^[a-zA-Z-' ]*$/",$name)) {
      $nameErr = "Only letters and white space allowed";
    }
  }
  
  if (empty($_POST["email"])) {
    $emailErr = "Email is required";
  } else {
    $email = test_input($_POST["email"]);
    if (!filter_var($email, FILTER_VALIDATE_EMAIL)) {
      $emailErr = "Invalid email format";
    }
    
  }

  if (empty($_POST["gender"])) {
    $genderErr = "Gender is required";
  } else {
    $gender = test_input($_POST["gender"]);
  }
  
   }
  
  if (empty($_POST["martial status"])) {
    $martialstatusErr = "Need to be fill";
  } else {
    $martialstatus = test_input($_POST["martial status"]);
    if (!filter_var($martialstatus, FILTER_VALIDATE_martialstatus)) {
      $martialstatusErr = "Invalid format";
    }
    
     }
  
  if (empty($_POST["phone number"])) {
    $phonenumberErr = "phone number is required";
  } else {
    $phonenumber = test_input($_POST["phone number"]);
    if (!filter_var($phonenumber, FILTER_VALIDATE_phonenumber)) {
      $phonenumberErr = "Invalid format";
    }
  
}

function test_input($data) {
  $data = trim($data);
  $data = stripslashes($data);
  $data = htmlspecialchars($data);
  return $data;
}
?>

<h2>NEW EPMLOYEE</h2>
<p><span class="error">* required field</span></p>
<form method="post" action="<?php echo htmlspecialchars($_SERVER["PHP_SELF"]);?>"> 

  Name: <input type="text" name="name" value="<?php echo $name;?>">
  <span class="error">* <?php echo $nameErr;?></span>
  <br><br>
  
  E-mail: <input type="text" name="email" value="<?php echo $email;?>">
  <span class="error">* <?php echo $emailErr;?></span>
  <br><br>
  
  Gender:
  <input type="radio" name="gender" <?php if (isset($gender) && $gender=="female") echo "checked";?> value="female">Female
  <input type="radio" name="gender" <?php if (isset($gender) && $gender=="male") echo "checked";?> value="male">Male
  <input type="radio" name="gender" <?php if (isset($gender) && $gender=="other") echo "checked";?> value="other">Other  
  <span class="error">* <?php echo $genderErr;?></span>  
  <br><br>
  
  Martial Status: 
  <input type="text" name="Martial Status" value="<?php echo $martialstatus;?>">
  <span class="error">* <?php echo $martialstatusErr;?></span>
  <br><br>
  
  Phone Number: 
  <input type="int" name="Phone Number" value="<?php echo $phonenumber;?>">
  <span class="error">* <?php echo $phonenumberErr;?></span>
  <br><br>
  
  Address: 
  <input type="char" name="Address" value="<?php echo $address;?>">
  <span class="error">* <?php echo $addressErr;?></span>
  <br><br>
  
  IC Number: 
  <input type="int" name="IC Number" value="<?php echo $icnumber;?>">
  <span class="error">* <?php echo $icnumberErr;?></span>
  <br><br>
  
  Hire Date: 
  <input type="int" name="Hire Date" value="<?php echo $hiredate;?>">
  <span class="error">* <?php echo $hidedateErr;?></span>
  <br><br>
  
  Martial Status: 
  <input type="text" name="Martial Status" value="<?php echo $martialstatus;?>">
  <span class="error">* <?php echo $martialstatusErr;?></span>
  <br><br>
  
  Department: 
  <input type="text" name="Department" value="<?php echo $department;?>">
  <span class="error">* <?php echo $departmentErr;?></span>
  <br><br>
  
 </form>
  
 
<?php
echo $name;
echo "<br>";
echo $email;
echo "<br>";
echo $gender;
echo "<br>";
echo $martialstatus;
echo "<br>";
echo $phonenumber;
echo "<br>";
echo $address;
echo "<br>";
echo $icnumber;
echo "<br>";
echo $hiredate;
echo "<br>";
echo $department;
echo "<br>"
?>

</body>
</html>
