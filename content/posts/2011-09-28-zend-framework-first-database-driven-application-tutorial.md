---
title: Zend Framework – First Database Driven Application – Tutorial
author: Vigas Deep
type: post
date: 2011-09-28T15:37:57+00:00
url: /2011/09/28/zend-framework-first-database-driven-application-tutorial/
dsq_thread_id:
  - 4626540746
categories:
  - Tutorial
  - Ubuntu
  - Zend Framework
tags:
  - Tutorial
  - Ubuntu
  - Zend Framework

---
Hey Everybody, I&#8217;m back with very interesting tutorial, that is a simple Database Driven Application in Zend Framework. Before I begin, I must tell you I am assuming that you are having Ubuntu installed on your system, and you are known to languages HTML and PHP.  
The requirements as under ..  
1) Latest version of PHP, MySql Database and Apache Web Server(httpd) are installed on your system.  
2) **mod_rewrite** extension of Apache must be enabled. To enable, do the following (only for Debian based distros, like Ubuntu) :  
`sudo a2enmod rewrite`  
and don&#8217;t forget to restart Apache.  
`sudo service apache2 restart`  
3) A BIG Cup of Coffee.

Lets Start, First of all, make a directory structure like this, project/ must be placed inside the /var/www/ Directory :

project/  
&#8212;&#8212;-application/  
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;controllers/  
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;forms/  
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;models/  
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;views/  
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-scripts/  
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-error/  
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-index/

Directory &#8220;project/&#8221; is main working directory of the our application. Download Zend Framework minimal package from <a href="http://framework.zend.com/download/latest" target="_blank">http://framework.zend.com/download/latest</a>

Then Extract the Library folder inside the archive to our project/ directory, graphically or use following commands (for UBUNTU)  
Log in to root and extract ->  
`<br />
$ su -i<br />
$ cd /home/your_username_here/Downloads/<br />
$ tar -xf Zend-minimal.tar.gz`  
<span style="color: #ff0000;">NOTE</span> : directory name: Zend-minimal.tar.gz can vary according to the version of Zend, you downloaded.  
Move library directory to project/  
`$ cd Zend-minimal<br />
$ cp library /var/www/project/library`

We have placed the required Zend Framework Files, more interesting thing is the next.  
create index.php file inside the project/ directory and write the following code also readout the comments given in the code.  
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;  
<?php  
define(&#8216;ROOT\_DIR&#8217;, dirname(\\_\_FILE\_\_));

//including the MVC (Model-View-Controller) directories and Zend library

set\_include\_path(&#8216;.&#8217;  
. PATH\_SEPARATOR . ROOT\_DIR . &#8216;/library&#8217;  
. PATH\_SEPARATOR . ROOT\_DIR . &#8216;/application/models&#8217;  
. PATH\_SEPARATOR . ROOT\_DIR . &#8216;/application/forms&#8217;  
. PATH\_SEPARATOR . get\_include_path()  
);

//Autoloading the zend

require_once &#8220;Zend/Loader/Autoloader.php&#8221;;  
$autoloader = Zend\_Loader\_Autoloader::getInstance();  
$autoloader->setFallbackAutoloader(true)

$frontController = Zend\_Controller\_Front::getInstance();

$frontController->throwExceptions(true);

$frontController->setControllerDirectory(ROOT_DIR.&#8217;/application/controllers&#8217;);  
$frontController->dispatch();  
?>  
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;  
So this was the index.php file, When we will open this file, Zend will lookout for IndexController.php inside the controllers/ directory which we have defined in the index.php file, therefore create the IndexController.php inside project/application/controllers/ and write the following code in it.

<span style="color: #ff0000;">NOTE</span>: Be careful about the case of files and codes, all are case-sensitive.  
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;  
<!--?php <br ?--> // setting up the controller here..

  
<?php

class IndexController extends Zend\_Controller\_Action  
{  
public function indexAction()  
{  
}}

?>  
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;  
and now the inside the IndexController.php we created the class with the same name, and indexAction() is created. indexAction() will look for index.phtml inside the project/application/views/scripts/index/ so just create it, whatever you will write in this file, directly comes to your view. Similarly create error.phtml in project/application/views/scripts/error/ and write anything that will identify you, whenever you faced the error.  
Next, create .htacess file in project/ folder and write following code in it  
`<br />
RewriteEngine On<br />
RewriteCond %{REQUEST_FILENAME} -s [OR]<br />
RewriteCond %{REQUEST_FILENAME} -l [OR]<br />
RewriteCond %{REQUEST_FILENAME} -d<br />
RewriteRule ^.*$ - [NC,L]<br />
RewriteRule ^.*$ index.php [NC,L]<br />
`  
This is the file where mod_rewrite extension of Apache Web Server(httpd) is used to rewrite the URLs, as I will not discuss this now.  
Now, I must tell you that we are creating database application to store the basic information of the user into the database and view it. So firstly I&#8217;m going to setup the view page. To do so we must create a database and a table inside it  
Create a Database and note down the name you created. Create table by executing the following query :  
``<br />
CREATE TABLE IF NOT EXISTS `users` (<br />
`id` int(11) NOT NULL AUTO_INCREMENT,<br />
`name` varchar(75) NOT NULL,<br />
`pname` varchar(75) NOT NULL,<br />
`address` varchar(100) NOT NULL,<br />
`contact` varchar(15) NOT NULL,<br />
`hobbies` text NOT NULL,<br />
PRIMARY KEY (`id`)<br />
) ENGINE=InnoDB DEFAULT CHARSET=latin1 AUTO_INCREMENT=10 ;<br />
``  
Upto now, the database and table are created, now configure the database settings. Create a file config.ini inside the /project/application/ directory, write the following code, fill in your details and save the file.  
`<br />
[general]<br />
db.adapter = "PDO_MYSQL"<br />
db.params.host = "localhost"<br />
db.params.username = "root"<br />
db.params.password = ""<br />
db.params.dbname = "project"<br />
`  
We have created the Database configuration file, now add the following lines to index.php  
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;  
$config = new Zend\_Config\_Ini(ROOT_DIR.&#8217;/application/config.ini&#8217;, &#8216;general&#8217;);  
$db = Zend_Db::factory($config->db);  
Zend\_Db\_Table::setDefaultAdapter($db);  
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;  
now it should look like ..  
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;  
<?php  
define(&#8216;ROOT\_DIR&#8217;, dirname(\\_\_FILE\_\_));

set\_include\_path(&#8216;.&#8217;  
. PATH\_SEPARATOR . ROOT\_DIR . &#8216;/library&#8217;  
. PATH\_SEPARATOR . ROOT\_DIR . &#8216;/application/models&#8217;  
. PATH\_SEPARATOR . ROOT\_DIR . &#8216;/application/forms&#8217;  
. PATH\_SEPARATOR . get\_include_path()  
);

require_once &#8220;Zend/Loader/Autoloader.php&#8221;;  
$autoloader = Zend\_Loader\_Autoloader::getInstance();  
$autoloader->setFallbackAutoloader(true);

//database configs initialized

$config = new Zend\_Config\_Ini(ROOT_DIR.&#8217;/application/config.ini&#8217;, &#8216;general&#8217;);  
$db = Zend_Db::factory($config->db);  
Zend\_Db\_Table::setDefaultAdapter($db);

$frontController = Zend\_Controller\_Front::getInstance();

$frontController->throwExceptions(true);

$frontController->setControllerDirectory(ROOT_DIR.&#8217;/application/controllers&#8217;);  
$frontController->dispatch();  
?>  
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;  
I&#8217;ve also added a form to view the data in specific defined order as desired by the viewer, So create a file named SortForm.php inside /project/application/forms directory and write following code.  
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;  
<?php  
class SortForm extends Zend_Form  
{  
public function init()  
{

$this->setMethod(&#8216;post&#8217;);  
$this->addElement(&#8216;radio&#8217;, &#8216;sortby&#8217;, array(  
&#8216;label&#8217; => &#8216;Sort by Column:&#8217;,  
&#8216;multioptions&#8217; => array(  
&#8216;name&#8217; => &#8216;Name&#8217;,  
&#8216;pname&#8217; => &#8216;Parent\&#8217;s Name&#8217;,  
&#8216;address&#8217; => &#8216;Address&#8217;,  
&#8216;contact&#8217; => &#8216;Contact&#8217;,  
&#8216;hobbies&#8217; => &#8216;hobbies&#8217;  
),

));

$this->addElement(&#8216;radio&#8217;, &#8216;sorttype&#8217;, array(  
&#8216;label&#8217; => &#8216;Sort Type:&#8217;,  
&#8216;multioptions&#8217; => array(  
&#8216;ASC&#8217; => &#8216;Aescending&#8217;,  
&#8216;DESC&#8217; => &#8216;Descending&#8217;  
),

));  
$this->addElement(&#8216;text&#8217;,&#8217;search&#8217;,array(  
&#8216;label&#8217;=>&#8217;search name&#8217;));  
$this->addElement(&#8216;submit&#8217;,&#8217;sortdata&#8217;,array(  
&#8216;label&#8217;=>&#8217;Sort Data&#8217;));

}  
}  
?>  
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;  
so We also update the IndexController.php and so as the index.phtml, the respective updated codes are embedded below.  
IndexController.php  
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;  
<?php  
class IndexController extends Zend\_Controller\_Action  
{  
public function indexAction()  
{

//loading Users model, ans SortForm  
$users = new Users();  
$form = new SortForm();  
$this->view->form = $form;

//searching and sorting logic  
if ($this->getRequest()->isPost()) {  
$sortData = $this->_request->getPost();

}  
if((empty($sortData[&#8216;search&#8217;])==0)){

if(isset($sortData[&#8216;sortby&#8217;]) && isset($sortData[&#8216;sorttype&#8217;]))  
{

$data=$users->fetchAll($users->select()->order($sortData[&#8216;sortby&#8217;].&#8221; &#8220;.$sortData[&#8216;sorttype&#8217;])->where(&#8216;name = ?&#8217;, $sortData[&#8216;search&#8217;]));  
}  
else  
{

$data=$users->fetchAll($users->select()->where(&#8216;name = ?&#8217;, $sortData[&#8216;search&#8217;]));  
}

}

elseif(isset($sortData[&#8216;sortby&#8217;]) && isset($sortData[&#8216;sorttype&#8217;])){

$data=$users->fetchAll($users->select()->order($sortData[&#8216;sortby&#8217;].&#8221; &#8220;.$sortData[&#8216;sorttype&#8217;]));  
}

else {

$data = $users->fetchAll($users->select());

}

$this->view->data = $data;  
}

}

?>  
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;  
index.phtml  
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;  
<h3>All Added Entries</h4>

<?php

echo $this->form;  
?>

<table border=&#8221;1&#8221;>

<tr>  
<th>Name</th>  
<th>Father&#8217;s Name</th>  
<th>Address</th>  
<th>Contact</th>  
<th>Hobbies</th>  
</tr>

<?php foreach ($this->data as $d) {?>  
<tr>  
<td><?php echo $d[&#8216;name&#8217;];?></td>  
<td><?php echo $d[&#8216;pname&#8217;];?></td>  
<td><?php echo $d[&#8216;address&#8217;];?></td>  
<td><?php echo $d[&#8216;contact&#8217;];?></td>  
<td><?php echo $d[&#8216;hobbies&#8217;];?></td>  
</tr>  
<?php }?>

</table>  
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;  
We have to setup a model for the Database table which we are using, which is also used in indexAction() of IndexController.php file so, create a file Users.php which resides in /project/application/models/ directory and write the corresponding code.  
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;

<?php class Users extends Zend\_Db\_Table {    protected $_name = &#8220;users&#8221;; } ?>

&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;  
also create ErrorController.php inside project/application/controllers/ and write the code, which we are using to display errors if any occurs.  
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;  
<?php

class ErrorController extends Zend\_Controller\_Action {

public function errorAction() {  
$errors = $this->\_getParam(&#8216;error\_handler&#8217;);  
$exception = $errors->exception;

echo $exception->getMessage();  
echo &#8220;<br /><pre>&#8221;;  
echo $exception->getTraceAsString();  
}  
}  
?>  
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;  
<span style="color: #ff0000;">NOTE</span>: If you are a beginner with PHP application or you&#8217;re facing problems in understanding, you must take a break here, try reading next after sometime.  
Next is the Data Entry form for user, create a form named CustomForm.php inside project/application/forms/ directory and write the following code to create a form for Data Entry.  
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;  
<?php  
class CustomForm extends Zend_Form  
{  
public function init()  
{  
$this->setMethod(&#8216;post&#8217;);

$id = $this->createElement(&#8216;hidden&#8217;,&#8217;id&#8217;);  
$name = $this->createElement(&#8216;text&#8217;,&#8217;name&#8217;);  
$name->setLabel(&#8216;Name:&#8217;)  
->setAttrib(&#8216;maxlength&#8217;,75);  
$pname = $this->createElement(&#8216;text&#8217;,&#8217;pname&#8217;);  
$pname->setLabel(&#8216;Father\&#8217;s Name&#8217;)  
->setAttrib(&#8216;maxlength&#8217;,75);  
$address = $this->createElement(&#8216;text&#8217;,&#8217;address&#8217;);  
$address->setLabel(&#8216;Address:&#8217;)  
->setAttrib(&#8216;maxlength&#8217;,100)  
->setAttrib(&#8216;size&#8217;,75);  
$contact = $this->createElement(&#8216;text&#8217;,&#8217;contact&#8217;);  
$contact->setLabel(&#8216;Contact:&#8217;)  
->setAttrib(&#8216;maxlength&#8217;,15)  
->setAttrib(&#8216;size&#8217;,15);

$hobbies = $this->createElement(&#8216;textarea&#8217;,&#8217;hobbies&#8217;);  
$hobbies->setLabel(&#8216;Hobbies (seprate with coma(,)):&#8217;)  
->setAttrib(&#8216;size&#8217;,255)  
->setAttrib(&#8216;rows&#8217;,10)  
->setAttrib(&#8216;cols&#8217;,40);  
$addentry = $this->createElement(&#8216;submit&#8217;,&#8217;addentry&#8217;);  
$addentry->setLabel(&#8220;Add Entry&#8221;)  
->setIgnore(true);

$this->addElements(array(  
$name,  
$pname,  
$address,  
$contact,  
$hobbies,  
$id,  
$addentry  
));  
}  
}  
?>  
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;  
also we have to create an addAction in IndexController to make the data entry work, updates version of IndexController.php is following, please make corresponding changes.  
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;  
<?php  
class IndexController extends Zend\_Controller\_Action  
{  
public function indexAction()  
{  
$users = new Users();  
$form = new SortForm();  
$this->view->form = $form;  
if ($this->getRequest()->isPost()) {  
$sortData = $this->_request->getPost();

}  
if((empty($sortData[&#8216;search&#8217;])==0)){

if(isset($sortData[&#8216;sortby&#8217;]) && isset($sortData[&#8216;sorttype&#8217;]))  
{

$data=$users->fetchAll($users->select()->order($sortData[&#8216;sortby&#8217;].&#8221; &#8220;.$sortData[&#8216;sorttype&#8217;])->where(&#8216;name = ?&#8217;, $sortData[&#8216;search&#8217;]));  
}  
else  
{

$data=$users->fetchAll($users->select()->where(&#8216;name = ?&#8217;, $sortData[&#8216;search&#8217;]));  
}

}

elseif(isset($sortData[&#8216;sortby&#8217;]) && isset($sortData[&#8216;sorttype&#8217;])){

$data=$users->fetchAll($users->select()->order($sortData[&#8216;sortby&#8217;].&#8221; &#8220;.$sortData[&#8216;sorttype&#8217;]));  
}

else {

$data = $users->fetchAll($users->select());

}

$this->view->data = $data;  
}

//add action

public function addAction()  
{  
$users = new Users();  
$form = new CustomForm();  
$this->view->form = $form;

if ($this->getRequest()->isPost()) {  
$formData = $this->_request->getPost();  
if ($form->isValid($formData)) {  
unset($formData[&#8216;addentry&#8217;]);  
$users->insert($formData);  
echo &#8220;Data Successfully stored&#8221;;  
}  
}  
}

}  
?>  
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;  
<span class="Apple-style-span" style="font-family: 'Helvetica Neue', Helvetica, Arial, Geneva, sans-serif; font-size: 13px; line-height: 18px; white-space: normal;">The only thing left is, create add.phtml file in project/application/views/scripts/index/ and write the following code in it.</span>

&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;  
<h3>Add User</h3>  
<?php  
if ($this->errorMsg) {  
echo $this->errorMsg;  
}  
?>  
<?php

echo $this->form;  
?>  
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;  
Now we are done with all the coding. You must try running your application now at  
Viewing the Entries :<a href="http://localhost/project/index" target="_blank">http://localhost/project/index</a>  
Adding Entries :<a href="http://localhost/project/index/add" target="_blank">http://localhost/project/index/add</a>  
While looking at the links you me seem that how http://localhost/project/index/add will run, you have created to add/ Directory inside the index/ Directory, then I must tell you that, It is the Magic of Rewrite_mod.  
Try running your application, if your face any error, just make sure following things are right again ->  
1) Rewrite_mod is enabled  
2) your directories and files are readable to you.  
3) Re-check the braces, most of the times Errors are with the braces.  
4) check your configuration paths in index.php.  
5) Also, Try refilling your cup of coffee.

Being Lazy ? huh ? Download the <a href="https://wp.vigasdeep.com/Zend_Task/task.tar.gz" target="_blank">Source</a>  
I hope I have not missed something.  
Good Luck.

System.out.print(&#8220;Vigas Deep&#8221;);