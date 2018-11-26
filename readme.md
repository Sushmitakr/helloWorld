


<HTML>
<HEAD>
	<TITLE> Add/Remove dynamic rows in HTML table </TITLE>
	<SCRIPT language="javascript">
		function addRow(tableID) {

			var table = document.getElementById(tableID);

			var rowCount = table.rows.length;
			var row = table.insertRow(rowCount);

			var colCount = table.rows[0].cells.length;

			for(var i=0; i<colCount; i++) {

				var newcell	= row.insertCell(i);

				newcell.innerHTML = table.rows[0].cells[i].innerHTML;
				//alert(newcell.childNodes);
				switch(newcell.childNodes[0].type) {
					case "text":
							newcell.childNodes[0].value = "";
							break;
					case "checkbox":
							newcell.childNodes[0].checked = false;
							break;
					case "select-one":
							newcell.childNodes[0].selectedIndex = 0;
							break;
				}
			}
		}

		function deleteRow(tableID) {
			try {
			var table = document.getElementById(tableID);
			var rowCount = table.rows.length;

			for(var i=0; i<rowCount; i++) {
				var row = table.rows[i];
				var chkbox = row.cells[0].childNodes[0];
				if(null != chkbox && true == chkbox.checked) {
					if(rowCount <= 1) {
						alert("Cannot delete all the rows.");
						break;
					}
					table.deleteRow(i);
					rowCount--;
					i--;
				}


			}
			}catch(e) {
				alert(e);
			}
		}

	</SCRIPT>
	<style>
		.topnav {
  overflow: hidden;
  float:right;
  position: fixed;
  top:0;
   width: 100%;
 
}

.topnav a {
  color: navy;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
  font-size: 17px;
}

.header {
  margin-top:30px;
  padding: 10px;
  text-align: center;
  background:blue;
  color: white;
  font-size: 30px;
}

	</style>
</HEAD>
<BODY>
	<div class="topnav">
		<a class="active" href="#home">Home</a>
		<a href="#news">News</a>
		<a href="#contact">Contact</a>
		<a href="#about">About</a>
	</div>

	<div class="header">
		<h1>Demo</h1>
	</div>
	<br/>
	<div>
		<div style="float: right">
	ADD: <INPUT type="button" value="Add Row" onclick="addRow('dataTable')" />

	<INPUT type="button" value="Delete Row" onclick="deleteRow('dataTable')" />
	</div>
	<br/>
	<div>
	<TABLE id="dataTable" width="350px" border="1">
		<TR>
			<TD><INPUT type="checkbox" name="chk"/></TD>
			
			<TD>
				<SELECT name="country">
					<OPTION value="in">Name</OPTION>
					<OPTION value="de">Category</OPTION>
					<OPTION value="fr">In Stock</OPTION>
					<OPTION value="us">Price</OPTION>
					<OPTION value="ch">Identifier</OPTION>
				</SELECT>
			</TD>
			
			<TD><INPUT type="text" name="txt"/></TD>
		</TR>
	</TABLE>
	</div>
	</div>
</BODY>
</HTML>
