<p>
In our last Section, we talked about variables, data, and how to transport data around in your application. Different data types serve different purposes.
</p>
<h2>
	Strings/Numbers
</h2>
<p>
	
<strong>Is Simple:</strong> Yes
</p>
<p>
Strings and numbers are very easy to work with. To set a string or a number, use the <span class="code">cfset</span> command. To append strings and numbers to each other, use the & operator:
</p>

<pre class="prettyprint">
&lt;cfset aString = "hi" /&gt;
&lt;cfset aNumber = 42 /&gt;
&lt;cfset aStringAndANumber = aString & aNumber /&gt;	

aString: &lt;cfoutput&gt;#aString#&lt;/cfoutput&gt;
aNumber: &lt;cfoutput&gt;#aNumber#&lt;/cfoutput&gt;
aStringAndANumber: &lt;cfoutput&gt;#aStringAndANumber#&lt;/cfoutput&gt;
</pre>
<p>
If you have a big block of strings to set, you can use the <span class="code">cfsavecontent</span> command.
</p>
<pre class="prettyprint">
&lt;cfsavecontent variable="EmailContent"&gt;
    Hi 

    We want to send you a hoverboard.
    Let us know if you will accept this free offer.

    -Us
&lt;/cfsavecontent&gt;

&lt;cfoutput&gt;#EmailContent#&lt;/cfoutput&gt;
</pre>
<h2>
	Dates
</h2>
	
<p>
<strong>Is Simple:</strong> Kind of
</p>
<p>
Dates are also very easy to work with in ColdFusion. You can use built in functions like <span class="code">now()</span> to make a date, or you can type the date into the variable assignment like this:
</p>

<pre class="prettyprint">
&lt;cfset DateToday = now() /&gt;
&lt;cfset NewYearDay = "1/1/2013" /&gt;
</pre>
<p>
You can use built-in functions to work with dates. To show how many days it has been since the turn of the century:
</p>

<pre class="prettyprint">
&lt;cfset DaysSinceTurnOfCentury = DateDiff("d", "1/1/2000", now() ) /&gt;
&lt;cfoutput&gt;#DaysSinceTurnOfCentury#&lt;/cfoutput&gt;
</pre>
<p>
Or suppose you want to know what the date will be 42 days from now:
</p>

<pre class="prettyprint">
&lt;cfset FortyTwoDaysFromNow = DateAdd("d", now(), 42 ) /&gt;
</pre>
<p>
ColdFusion provides many useful functions to work with dates and times. You can compare dates, find out how far two dates are apart, reformat a date, and more. See the ColdFusion Date/Time documentation for a full listing: <a href="http://help.adobe.com/en_US/ColdFusion/10.0/CFMLRef/WSc3ff6d0ea77859461172e0811cbec1a60c-7ffc.html#WSc3ff6d0ea77859461172e0811cbec22c24-6986" target="_new">http://help.adobe.com/en_US/ColdFusion/10.0/CFMLRef/WSc3ff6d0ea77859461172e0811cbec1a60c-7ffc.html#WSc3ff6d0ea77859461172e0811cbec22c24-6986</a>
</p>
<h2>
	Arrays
</h2>
	
<p>
<strong>Is Simple:</strong> No
</p>
<p>
Arrays are an ordered series of data. Here's an example of a one dimensional array:
</p>
<h3>
Array Creation
</h3>
<pre class="prettyprint">
&lt;cfset ThingsILike = ["Warm Sandy Beaches", "Tropical Drinks", 42] /&gt;
&lt;cfdump var = "#ThingsILike#" /&gt;
</pre>
<h3>
	Alternate Method: Array Creation
</h3>

<p>
Here's another way to create an array, along with a couple of different ways to add data to an array:
</p>
<pre class="prettyprint">
&lt;cfset ThingsILike = arrayNew(1) /&gt;
</pre>
<h3>
	Adding Items to an Array
</h3>
	
<p>
You can add things by a specific position. Note: Arrays in ColdFusion start at 1, not 0.
</p>
<pre class="prettyprint">
&lt;cfset ThingsILike[1]  = "Warm Sandy Beaches" /&gt;
</pre>
<h3>
	Alternate Method: Adding Items to an Array
</h3>	

<p>
You can append an item to the end of the array:
</p>
<pre class="prettyprint">
&lt;cfset ArrayAppend( ThingsILike,  "Tropical Drinks") /&gt;
&lt;cfset ArrayAppend( ThingsILike,  42) /&gt;
&lt;cfdump var="#ThingsILike#" /&gt;
</pre>
<p>
See how I defined the strings in my array with quotes, and non-strings without? Each element in the array is an execution zone also, so if you need ColdFusion to evaluate something, just add it in:
</p>
<pre class="prettyprint">
&lt;cfset ImportantDates = ["12/26/1975", now() ] /&gt;
&lt;cfdump var = "#ImportantDates#" /&gt;
</pre>
<h3>
	Displaying the Contents of an Array
</h3>

<p>
You can not use the <span class="code">cfoutput</span> command on an array because complex data types such as arrays are not displayable as a string. You can loop over the array, however, and output the strings to the page:
</p>
<pre class="prettyprint">
&lt;cfset ThingsILike = ["Warm Sandy Beaches", "Tropical Drinks", 42] /&gt;
&lt;cfloop array="#ThingsILike#" index="thing"&gt;
    &lt;cfoutput&gt;#thing#&lt;/cfoutput&gt;
&lt;/cfloop>
</pre>
<p>
ColdFusion provides many useful functions to work with arrays. You can search the contents of an array for a value, perform mathematical functions such Sum or Average, sort the contents of an array, and more. See the ColdFusion Array function documentation for a full listing: <a href="http://help.adobe.com/en_US/ColdFusion/10.0/CFMLRef/WSc3ff6d0ea77859461172e0811cbec1a60c-7ffc.html#WSc3ff6d0ea77859461172e0811cbec22c24-6a66" target="_new">http://help.adobe.com/en_US/ColdFusion/10.0/CFMLRef/WSc3ff6d0ea77859461172e0811cbec1a60c-7ffc.html#WSc3ff6d0ea77859461172e0811cbec22c24-6a66</a>
</p>

<h2>
	Structs
</h2>
	
<p>
<strong>Is Simple:</strong> No
</p>
<p>
Structs, aka Structures, are a collection of data, stored by a key, or name. Suppose for example, you wanted to store several kinds of fruit and also whether you like it or not. Structs provide a way to organize like name/value pairs and let you refer to them as a single collection.
</p>
<h3>
	Struct Creation
</h3>
<pre class="prettyprint">
&lt;cfset FruitBasket = structNew() /&gt;
</pre>
<h3>
	Alternate Method: Struct Creation
</h3>
<pre class="prettyprint">
&lt;cfset FruitBasket = {} /&gt;
</pre>
<h3>
	Adding Items to a Struct: Bracket Notation
</h3>
<pre class="prettyprint">
&lt;cfset FruitBasket = {} /&gt;
&lt;cfset FruitBasket["Apple"] = "Like" /&gt;
&lt;cfset FruitBasket["Banana"] = "Like" /&gt;
&lt;cfset FruitBasket["Cherry"] = "Dislike" /&gt;

&lt;cfdump var = "#FruitBasket#" /&gt;
</pre>
<h3>
	Adding Items to a Struct Dot Notation
</h3>
<pre class="prettyprint">
&lt;cfset FruitBasket = {} /&gt;
&lt;cfset FruitBasket.Apple = "Like" /&gt;
&lt;cfset FruitBasket.Banana = "Like" /&gt;
&lt;cfset FruitBasket.Cherry = "Dislike" /&gt;

&lt;cfdump var = "#FruitBasket#" /&gt;
</pre>
<h3>
	Struct Creation and Population in One Statement
</h3>
<pre class="prettyprint">
&lt;cfset fruitBasket = {
    "Apple" = "Like",
    "Banana" = "Like",
    "Cherry" = "Dislike"
} /&gt;
&lt;cfdump var = "#FruitBasket#" /&gt;
</pre>

<blockquote>
<strong>Pro Tip:</strong> There are reasons to use one struct notation over another. If you ran some of these examples you would notice that the Bracket Notation preserved the case of the keys and the Dot Notation did not. Sometimes the preservation of case is important, like when passing values to Javascript or other case sensitive languages or formats.  In the Struct Creation and Population in One Statement Example, the case will be preserved as long as they keys are surrounded by quotes. If the keys are not quoted, the case will be converted to upper case. <br /><br />Also, the bracket notation allows for a dynamic key reference. This is helpful when the name of the struct key will come from a runtime operation, such as looping over the struct. Many people find Dot Notation easier to read and use it most of the time, except in cases where Bracket Notation offers a feature Dot Notation does not.
</blockquote>
<h3>
	Displaying the Contents of a Struct
</h3>

<p>
See how your preference was mapped to the kind of fruit? You can't use the <span class="code">cfoutput</span> command on structs either because, once again, they aren't displayable as a string. You can loop over the struct and output the keys and values to the page:
</p>
<pre class="prettyprint">
&lt;cfloop collection="#FruitBasket#" item="fruit"&gt;
    &lt;cfoutput&gt;I #FruitBasket[fruit]# #fruit#&lt;/cfoutput&gt;&lt;br /&gt;
&lt;/cfloop&gt;
</pre>
<p>
ColdFusion provides many functions to work with structs. You can search the contents of struct, make complete and partial copies, retrieve a list of just the keys, and more. See the ColdFusion Struct function documentation for a full listing: <a hef="http://help.adobe.com/en_US/ColdFusion/10.0/CFMLRef/WSc3ff6d0ea77859461172e0811cbec1a60c-7ffc.html#WSc3ff6d0ea77859461172e0811cbec22c24-69b8" target="_new">http://help.adobe.com/en_US/ColdFusion/10.0/CFMLRef/WSc3ff6d0ea77859461172e0811cbec1a60c-7ffc.html#WSc3ff6d0ea77859461172e0811cbec22c24-69b8</a>
</p>

<h2>
	Queries
</h2>

<p>
<strong>Is Simple:</strong> No
</p>
<p>
Queries are recordsets. Recordsets contain a series of columns with 0 or more rows. You can think of a query like a single page of a spreadsheet with the columns across the top and rows down the side.
</p>
<p>
Most ColdFusion programs interact with databases. Database interaction takes the form of a query and ColdFusion makes it very easy to work with the data returned by the database.  Databases will be covered more in more detail later on in the course.
</p>
<pre class="prettyprint">
&lt;cfquery name="FruitQuery" datasource="fruit"&gt;
    SELECT Name, Price
    FROM FruitStore
    WHERE Price &lt; 7
&lt;/cfquery&gt;

&lt;cfloop query="FruitQuery"&gt;
    #FruitQuery.Name# costs #FruitQuery.Price# &lt;br /&gt;
&lt;/cfloop&gt;
</pre>

<p>
Query Objects have a few special properties. You can use these properties to get specific information about the data inside the query.
</p>
<p>
	<ul>
		<li><strong>queryname.recordcount</strong>: How many rows does this query have?</li>
		<li><strong>queryname.columnlist</strong>: What columns does this query have?</li>
		<li><strong>queryname.currentrow</strong>: What row number are we currently on inside a <span class="code">cfoutput</span> or <span class="code">cfloop</span>?</li>
	</ul>
	
</p>




<p>
ColdFusion provides several useful functions to work with query objects. You can create your own query objects in ColdFusion without a database call or even retrieve all the values in a specific column in a list format. See the ColdFusion Query function documentation for a full listing:  <a href="http://help.adobe.com/en_US/ColdFusion/10.0/CFMLRef/WSc3ff6d0ea77859461172e0811cbec1a60c-7ffc.html#WSc3ff6d0ea77859461172e0811cbec22c24-67fe" target="_new">http://help.adobe.com/en_US/ColdFusion/10.0/CFMLRef/WSc3ff6d0ea77859461172e0811cbec1a60c-7ffc.html#WSc3ff6d0ea77859461172e0811cbec22c24-67fe</a>
</p>
<p>
Also, be sure to review the Accessing and Using Data portion of the ColdFusion documentation, which explains a number of key concepts and techniques for working with data, databases and query objects: <a href="http://help.adobe.com/en_US/ColdFusion/10.0/Developing/WS8f0cc78011fffa7168855f811cdb0b0cce-8000.html" target="_new">http://help.adobe.com/en_US/ColdFusion/10.0/Developing/WS8f0cc78011fffa7168855f811cdb0b0cce-8000.html</a>
</p>