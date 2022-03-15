# reflected-post-xss
HTML &amp;&amp; JavaScript reflected XSS attack


Explanation:

"<body onload="document.forms[0].submit()">" >>> After the page loaded, immediately submit the first form the page (StageXssAttack.html).

"<form action="http://192.168.1.2:4444/challenge/XSS/stage6.php" method="post">" >>>  the form we want to send  and it contains the **target** and **method**.

 "input type="hidden" name="_" value='aaaa" onmouseover="alert(1)'>" >>> for example we want to exploit an input of a form, we need a name attribute (name="_" in this example). the type="hidden" can also be "text" it wom't change the result. Now the real thing happens here, the value is **value='aaaa" onmouseover="alert(1)'>"** because we want change the input's value when we send the form request using our script. The way it works is, when server (target) will see that a post request has been made with an existing parameter in the page it will change the input's value to the new avlue we assigned to it using out post request because we used the same parameter ($_GET['_'], in this example). I used the **onmouseover="alert(1)'** because the specials chars unicoded, and when we are just adding a new attribute it won't be unicoded.

