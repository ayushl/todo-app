<!DOCTYPE html>
<html>
    <head>
        <style>
             body { background: rgb(49, 49, 49)}
           
            .myTable{
                border-color: rgb(49, 49, 49);
                width: 72%;
                color:white;
  font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
}
.tabb{
    background-color: rgb(49, 49, 49);
}
.but{
    padding: 2px 10px;
      font-size: 24px;
      text-align: center;
      cursor: pointer;
      outline: none;
      transition: 0.3s;
      color: #fff;
      background-color: rgba(83, 99, 119, 0.397);
      border: none;
      border-radius: 15px;
      box-shadow: 0 5px rgb(241, 241, 241);}
      .but:hover {background-color: #3e8e41}
      .but:active {
      background-color: #3e8e41;
      box-shadow: 0 3px rgb(218, 224, 217);
      transform: translateY(2px);
    }
            
            .button {
      padding: 5px 20px;
      font-size: 24px;
      text-align: center;
      cursor: pointer;
      outline: none;
      float: left;
      transition: 0.3s;
      color: #fff;
      background-color: rgba(83, 99, 119, 0.397);
      border: none;
      border-radius: 15px;
      box-shadow: 0 5px rgb(241, 241, 241);}

      .button:hover {background-color: #3e8e41}
    
    .button:active {
      background-color: #3e8e41;
      box-shadow: 0 3px rgb(218, 224, 217);
      transform: translateY(2px);
    }
    .header {
  background-color: #000000;
  padding: 30px 40px;
  color: white;
  text-align: center;
}

.trt{
  color:white;
  font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
}

        </style>
    </head>
    <body>
            <div id="myDiv" class="header">
                    <button onclick="myFunction()" class="button">Add details</button>
                    <button onclick="myDeleteFunction()" class="button">Delete Selected</button>
                    <button onclick="Update()" class="button">Update</button>
                    <br>
                    <br>
            </div>
            <br>
            <br>
            <br>
            <center>
                    <table style="width:70%" class="tabb">
                            <tr class="trt">
                                <th>Check Box</th>
                              <th>Work</th>
                              <th>Description</th> 
                              <th>Days</th>
                              <th>Priority</th>
                            </tr>
                            <tr>
                                <td><input type="checkbox" name="name" onclick="selectall()" id="se"/>Select all</td>
                              <td><input type = "text" id="fname" style="width:95%" onkeypress="dothis()" onkeyup="dothis()" onfocusout="dothis()"></td>
                              <td><input type = "text" id="lname" style="width:95%"></td>
                              <td><input type = "text" id="a" style="width:95%"></td>
                              <td> <select id="drop" name="Priority" style="width:100%" >
                                    <option value="High">High</option>
                                    <option value="Medium">Medium</option>
                                    <option value="Low">Low</option>
                                  </select> </td>
                            </tr>
                           
                          </table>
                          <p id="jj"></p>
                        <p id="demo" ></p>
                        
                     <div id="upd" style="display: none">
                                <button onclick="newval()" class="but">Update values</button>
                                <button onclick="canupdate()" class="but">Cancel Update</button>
                     </div>
                        </center>
            <script>
               

                var arr=[];
                function myFunction(){

                    var flag=0;
  if(document.getElementById("fname").value=="" || document.getElementById("lname").value=="" ||  document.getElementById("a").value=="" ){
    alert("Enter all the feilds!");
    return;
  }
  var name1 = document.getElementById("fname").value;

  for (var i=0;i<arr.length;i++){
    if(arr[i].Work==name1){
        console.log(arr[i].Work);
        flag=1;
    }
  }
    if(flag==0){
    arr.push({
    Work: document.getElementById("fname").value,
    Description: document.getElementById("lname").value,
    Days: document.getElementById("a").value,
    Priority: document.getElementById("drop").value
    });
    display();

                }
                else{
  alert("Employee already exists");
}

document.getElementById("fname").value="";
document.getElementById("lname").value="";
document.getElementById("a").value="";
document.getElementById("drop").value="High"
                
                }
                function display(){
  var text = "<table class='myTable' id='del'><tr><td>Checkbox</td><td>Work</td><td>Description</td><td>Days</td><td>Priority</td></tr>"
                  for (var i=0;i<arr.length;i++){
     text+="<tr><td><input type='checkbox' class='non' id="+i+"/> </td><td>"+arr[i].Work+"</td><td>"+arr[i].Description+"</td><td>"+arr[i].Days+"</td><td>"+arr[i].Priority+"</td></tr>"                                                 
                  }
    text+="</table>";
    //return text;
    document.getElementById("demo").innerHTML=text;
}

function myDeleteFunction(){
    var aObj = document.getElementsByClassName("non");
   // var index;

             for(var i=aObj.length-1;i>=0;i=i-1){
               
               if(aObj[i].checked == true){
                arr.splice(i,1);
               // document.getElementById('del').deleteRow(i);
               }
             }
             display();

}
function dothis(){
  var name1 = document.getElementById("fname").value;
  //var f=0;

for (var i=0;i<arr.length;i++){
  if(arr[i].Work==name1){
      console.log(arr[i].Work);
      document.getElementById("jj").innerHTML="error";
      document.getElementById("fname").focus();
      document.getElementById("fname").style="border-color:red;width:95%";
      return;
  } 
  else{
    document.getElementById("jj").innerHTML="";
      document.getElementById("fname").style="border-color:none;width:95%";
    
  }
} 
}
function selectall(){
    var checkBox = document.getElementById("se");
    var che = document.getElementsByClassName("non");
              if(checkBox.checked == true){
                for(var i=0, n=che.length;i<n;i++) {
    che[i].checked = true}
              }
              else if(checkBox.checked == false){
                for(var i=0, n=che.length;i<n;i++) {
    che[i].checked = false}
            }  
}
function Update(){
   

    var aObj = document.getElementsByClassName("non");
    var f=0;

             for(var i=aObj.length-1;i>=0;i=i-1){
               
               if(aObj[i].checked == true){
                   f=f+1;
               
               if(f!=1){
                   alert("not selected properly!");
                   return;
               }
               if(f==1){
                document.getElementById("fname").value=arr[i].Work;
document.getElementById("lname").value=arr[i].Description;
document.getElementById("a").value=arr[i].Days;
                   
               }
               }
}
if(f==0){
    alert("select something!");
    return;
}
var x = document.getElementById("upd");
  if (x.style.display === "none") {
    x.style.display = "block";
  } 
  document.getElementById("fname").readOnly = true;
}
function newval(){
    var name2 = document.getElementById("fname").value;
   // var f1=1;
    index = arr.findIndex(x => x.Work==name2);
   
  //  console.log(index);
    arr[index].Description=document.getElementById("lname").value
    arr[index].Days=document.getElementById("a").value
    arr[index].Priority=document.getElementById("drop").value
 
  
  var x = document.getElementById("upd");
  if (x.style.display === "block") {
    x.style.display = "none";
  } 
  display();
  document.getElementById("fname").value="";
document.getElementById("lname").value="";
document.getElementById("a").value="";
document.getElementById("fname").readOnly = false;
}
function canupdate(){
    document.getElementById("fname").value="";
document.getElementById("lname").value="";
document.getElementById("a").value="";

var x = document.getElementById("upd");
  if (x.style.display === "block") {
    x.style.display = "none";
  } 
  var aObj = document.getElementsByClassName("non");
  for(var i=aObj.length-1;i>=0;i=i-1){
               
               if(aObj[i].checked == true){

aObj[i].checked = false
               }
  }
  document.getElementById("fname").readOnly = false;

}  
            </script>
    </body>
</html>
