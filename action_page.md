<!DOCTYPE html>
<html>
    <body>
        <?php
            $link=mysqli_connect("localhost","root","","student");
            if($link==false)
            {
                die("ERROR: Could not connect. " . mysqli_connect_error());
            }
            $sname       = mysqli_real_escape_string($link, $_POST['name']);
            $sadmission  = mysqli_real_escape_string($link, $_POST['admission']);
            $DOB        = mysqli_real_escape_string($link, $_POST['DOB']);
            $address    = mysqli_real_escape_string($link, $_POST['address']);
            $program    = mysqli_real_escape_string($link, $_POST['program']);
            $gender     = mysqli_real_escape_string($link, $_POST['gender']);
            $fname      = mysqli_real_escape_string($link, $_POST['fname']);
            $foccu      = mysqli_real_escape_string($link, $_POST['foccu']);
            $mname      = mysqli_real_escape_string($link, $_POST['mname']);
            $moccu      = mysqli_real_escape_string($link, $_POST['moccu']);
            $number     = mysqli_real_escape_string($link, $_POST['number']);
            $email      = mysqli_real_escape_string($link, $_POST['email']);
            $sql="INSERT INTO studententry(SName,AdmissionNo,DOB,SAddress,Program,Gender,FathersName,OccupationF,MothersName,OccupationM,Contact,Email) 
            VALUES ('$sname',$sadmission,'$DOB','$address','$program','$gender','$fname','$foccu','$mname','$moccu','$number','$email')";
            echo "<br>";
            $result=mysqli_query($link,$sql);
            if($result)
            {
                echo "Records inserted successfully.";
            }
            else
            {
                echo "ERROR: Could not able to execute $sql. " . mysqli_error($link);
            }
            echo "<br>";
            echo "<br> LIST OF STUDENTS <br>";
            $sql="SELECT SName,AdmissionNo FROM studententry";
            $result=mysqli_query($link,$sql);
            if($result->num_rows>0)
            {
                while($row=$result->fetch_assoc())
                {
                    echo "<br> Admission Number: ".$row["AdmissionNo"]." - Name: ".$row["SName"]."<br>";
                }
            }
            else
            {
                echo " 0 Results";
            }
            mysqli_close($link);
            
        ?>
    </body>
</html>
