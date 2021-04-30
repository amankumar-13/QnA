# QnA
<!doctype html>
<html lang="en">
  <head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">

    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-eOJMYsd53ii+scO/bJGFsiCZc+5NDVN2yr8+0RDqr0Ql0h+rP48ckxlpbzKgwra6" crossorigin="anonymous">

    <title>Search Questions</title>
	
	<style>
* {
  box-sizing: border-box;
}

body {
  font: 16px Arial;  
}

/*the container must be positioned relative:*/
.autocomplete {
  position: relative;
  display: inline-block;
}

input {
  border: 1px solid transparent;
  background-color: #f1f1f1;
  padding: 10px;
  font-size: 16px;
}

input[type=text] {
  background-color: #f1f1f1;
  width: 100%;
}

input[type=submit] {
  background-color: DodgerBlue;
  color: #fff;
  cursor: pointer;
}

.autocomplete-items {
  position: absolute;
  border: 1px solid #d4d4d4;
  border-bottom: none;
  border-top: none;
  z-index: 99;
  /*position the autocomplete items to be the same width as the container:*/
  top: 100%;
  left: 0;
  right: 0;
}
#myDIV {
  width: 300px;
  height: 100px;
  padding: 50px;  
  display: none;
  text-align: center;
  font-size: 30px;
}

#myANS {
  width: 1000px;
  height: 100px;
  padding: 50px;  
  display: none;
  text-align: center;
  font-size: 30px;
}

#tableDiv{
 display:block;
}
.autocomplete-items div {
  padding: 10px;
  cursor: pointer;
  background-color: #fff; 
  border-bottom: 1px solid #d4d4d4; 
}

/*when hovering an item:*/
.autocomplete-items div:hover {
  background-color: #e9e9e9; 
}

/*when navigating through the items using the arrow keys:*/
.autocomplete-active {
  background-color: DodgerBlue !important; 
  color: #ffffff; 
}
</style>
	
  </head>
  <body>
    <div class="container">
        <div class="row">
            <div class="col-md-12 mt-4">
                <div class="card">
                    <div class="card-header">
                        <h4 class="card-title">How to Search question</h4>
                    </div>
					<input type="text" id="keyword" placeholder="Type a Question" onkeyup="accesingKeyword()">

		          
	<div id="tableDiv">
      <table class="table" id = "myTable">
                            <thead class="thead-dark">
                              <tr>
                                <th style="font-size: 30px;" scope="col">Most Recent Questions</th>
                                <!-- <th scope="col">Answer</th> -->
                              </tr>
                            </thead>
							
                            <tbody>
                              <tr>
                                <td> <a href= "javascript:onInput(1);">
                                    What is HTML
                                    </a>
                                </td>
                                <!-- <td>HTML is Hyper Text Markup Language</td> -->
                              </tr>
                              <tr>
                                <td><a href= "javascript:onInput(2);">
                                    What is sql
                                    </a></td>
                                <!-- <td>Thornton</td> -->
                              </tr>
                              <tr>
                                <td><a href= "javascript:onInput(3);">
                                    What is Javascript
                                    </a></td>
                                <!-- <td>the Bird</td> -->
                              </tr>
                              <tr>
                                <td><a href= "javascript:onInput(4);">
                                    What are we using in this project
                                    </a></td>
                                <!-- <td>the Bird</td> -->
                              </tr>
                              <tr>
                                <td><a href= "javascript:onInput(5);">
                                    What database is used in this project.
                                    </a></td>
                                <!-- <td>the Bird</td> -->
                              </tr>
                              <tr>
                                <td> <a href= "javascript:onInput(6);" >
                                    What is your hobby
                                    </a>
                                </td>
                                <!-- <td>HTML is Hyper Text Markup Language</td> -->
                              </tr>
                            </tbody>
                          </table>
                        </div>
                    </div>
                </div>
            </div>
        </div>
		
		<div id="myDIV">
	
</div>
	<div id="myANS">

	</div>

    <script>
	function onInput(value){
	
			var x = document.getElementById("tableDiv");
			var y = document.getElementById("myDIV");
			var z = document.getElementById("myANS");
		  if (x.style.display === "none") {
			x.style.display = "block";
			y.style.display = "none";
			z.style.display = "none";
		  } else {
			x.style.display = "none";
			y.style.display = "block";
			z.style.display = "block";
		  }
			var answer="";
			 var text = '{"myJson":[' +
					'{"question":"What is HTML","answer":"HTML is Hyper Text Markup Language","id":1 },' +
					'{"question":"What is SQL","answer":"sql is structured query language","id":2 },' +
					'{"question":"What is Javascript","answer":"Javascript is client side programming language.","id":3 },'+
					'{"question":"What are we using in this project","answer":"Javascript and HTML are used in my project.","id":4 },'+
					'{"question":"What database is used in this project.","answer":"SQL database is used in my project.","id":5 },'+
					'{"question":"What is your hobby","answer":"Watching TV is my hobby","id":6 }]}';
					obj = JSON.parse(text);
			        alert(obj.myJson[value-1].question);
					document.getElementById("myANS").innerHTML = obj.myJson[value-1].question +"<br>"+obj.myJson[value-1].answer;

	}
	
function accesingKeyword() {
            // alert("coming");
            var key = document.getElementById("keyword");
            var filter = key.value.toUpperCase();
            var table = document.getElementById("myTable"); 
            // console.log(table);
            var tr = table.getElementsByTagName("tr");
            // console.log(tr);
            for (i = 0; i < tr.length; i++) {
                var td = tr[i].getElementsByTagName("td")[0];
                var ans = tr[i].getElementsByTagName("td")[1];
                console.log(td);
                console.log(ans);
                if (td) {
                    var txtValue = td.textContent || td.innerText;
                    if (txtValue.toUpperCase().indexOf(filter) > -1) {
                        tr[i].style.display = "";
                    } else {
                        tr[i].style.display = "none";
                    }
                }
                else if (ans) {
                    var txtValue1 = ans.textContent || ans.innerText;
                    if (txtValue1.toUpperCase().indexOf(filter) > -1) {
                        tr[i].style.display = "";
                    } else {
                        tr[i].style.display = "none";
                    }  
                }
            }
        }
</script>
    <!-- Optional JavaScript; choose one of the two! -->

    <!-- Option 1: Bootstrap Bundle with Popper -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta3/dist/js/bootstrap.bundle.min.js" integrity="sha384-JEW9xMcG8R+pH31jmWH6WWP0WintQrMb4s7ZOdauHnUtxwoG2vI5DkLtS3qm9Ekf" crossorigin="anonymous"></script>

    <!-- Option 2: Separate Popper and Bootstrap JS -->
    <!--
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.9.1/dist/umd/popper.min.js" integrity="sha384-SR1sx49pcuLnqZUnnPwx6FCym0wLsk5JZuNx2bPPENzswTNFaQU1RDvt3wT4gWFG" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta3/dist/js/bootstrap.min.js" integrity="sha384-j0CNLUeiqtyaRmlzUHCPZ+Gy5fQu0dQ6eZ/xAww941Ai1SxSY+0EQqNXNE6DZiVc" crossorigin="anonymous"></script>
    -->
  </body>
</html>
