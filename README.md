**This PHP Class is used for PHP MySQL connections using PHP PDO**
https://github.com/craftpitch/phppdo.git
	Generally we have forms and we have to do various operations on those forms like:
	Read, Ascending or Desending
	Write
	Update
	Delete
	Search
	Count rows and more

This class take form input as an array, unless specified.

**Contruct will over ride the above variables use contruct as below if you donot want to override.**

	private dbname=YOUR_DB_NAME;
	function __construct() {
	  try {
	    $this->dbh = new PDO("mysql:host=$this->hostname;dbname=$this->dbname", $this->username, $this->password);
              }
	  catch(PDOException $e)
	     {
		echo $e->getMessage();
		exit();
	      }
	} 

	 *the way contruct is written so that this class will work with multiple databases and can be extended*

## Example 1 Insert Record into table name client

		include 'CP_DB_PDO.php';
		$cp=new CpPdo(); //Create an object of class CpPdo
		$tablename="client";
		//names in form must match the column names of MYSQL db. 
		//You must unset input names which does not match column names such as submit input types.
		$in_param = $_POST; 
		$myvar=$cp->cpInsert($tablename, $in_param);

## Example 2 Insert Record into table name client and get last insert id

		include 'CP_DB_PDO.php';
		$cp=new CpPdo(); //Create an object of class CpPdo
		$tablename="client";
		//names in form must match the column names of MYSQL db. 
		//You must unset input names which does not match column names such as submit input types.
		$in_param = $_POST; 
		// Let us suppose our column name is "id" and we want to get last insert id.
		$myvar=$cp->cpInsert($tablename, $in_param, "id");
		Now $myvar will hold the last insert id

## Example 3 Update Record into table name client

		include 'CP_DB_PDO.php';
		$cp=new CpPdo(); //Create an object of class CpPdo
		$tablename="client";
		//names in form must match the column names of MYSQL db. 
		//You must unset input names which does not match column names such as submit input types.
		$up_param = $_POST; 
		$u_id['id']= $id // we have to get id or unique name such as email or phone as an update id.
		// id in $u_id['id'] represent column name of DB
		$myvar=$cp->cpUpdate($tablename,$u_id,$up_param);

## Example 4  Select Record from table name client

		include 'CP_DB_PDO.php';
		$cp=new CpPdo(); //Create an object of class CpPdo
		$tablename="client";

		$myvar=$cp->cpSelect($tablename);
		$myvar will return all results in table as an associative array

## Example 5  Delete Record from table name client

		include 'CP_DB_PDO.php';
		$cp=new CpPdo(); //Create an object of class CpPdo
		$tablename="client";
		$d_id['id']=$id // id you want to delete
		$myvar=$cp->cpDelete($tablename, $d_id);

I hope this will be helpfull.
Please give me feedback at craftpitch@gmail.com

