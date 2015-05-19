<p>
	An important part of any program is the ability to make decisions based upon a set of conditions.  This is aptly named 'conditional logic'.  Unless you are writing a static set of HTML pages, you will almost certainly need to evaluate conditions.  In conditional logic, all conditions tested must evaluate to a Boolean, either true or false.  As you learned in the variables section of this training, ColdFusion is a dynamically typed language.  This does not mean that ColdFusion is not typed, but rather that ColdFusion can switch from type to type dynamically while the application is executing.  This is a great feature when using conditional logic as you do not need to explicitly define the Boolean such as <span class="code">myVar == true</span>, but for simple variables you can allow ColdFusion to evaluate the value of the variable and convert it dynamically to a Boolean value.  Keep this in mind, and we will revisit this in a bit.
</p>

<p>
	ColdFusion has both <span class="code">if/then/else</span> tags as well as <span class="code">switch/case</span> logic.  We will look at <span class="code">if/then/else</span> logic first.  There are three tags that are important when evaluating conditions: <span class="code">cfif</span>, <span class="code">cfelseif</span>, and <span class="code">cfelse</span>.
</p>

<p>
	<span class="code">cfif</span> is used to start a decision block.  As with any properly formed tag block, being XHTML compliant, a <span class="code">cfif</span> block is terminated with </cfif>. Inside the conditional block you will place either code to execute or markup to output.  A simple case looks like this:
</p>
<pre>
&lt;cfif expression>
	..Markup..
&lt;/cfif>
</pre>
<p>
	The decision block above says that if the expression evaluates to <span class="code">true</span>, then execute the tag contents.  If the expression evaluates to <span class="code">false</span>, do nothing.  However, if we want it to do something if the expression evaluates to false, we use the <span class="code">cfelse</span> tag like this:
</p>
<pre>
&lt;cfif expression>
	..Markup..
&lt;cfelse>
	..More Markup..
&lt;/cfif>
</pre>
<p>
	If you need to compare several conditions in succession, use <span class="code">cfelseif</span>:
</p>
<pre>
&lt;cfif expression>
	..Markup..
&lt;cfelseif another_expression>
	..More Markup..
&lt;cfelse>
	..More Markup..
&lt;/cfif>
</pre>
<p>
	For review, an expression is any value that will evaluate to a Boolean (<span class="code">true</span> or <span class="code">false</span>).  You can provide a string value that will evaluate to a Boolean such as a number.  Any positive number will evaluate to <span class="code">true</span>; 0 evaluates to <span class="code">false</span>.  Negative numbers evaluate to <span class="code">false</span> as well.  You may also call a function that returns a Boolean or numeric value like these:
</p>

<pre>
len(myStringVar); // returns a number
isNull(mySimpleVar); // returns a Boolean
arrayLen(myArray); // returns a number
</pre>

<p>
	Sometimes you will need to perform a values comparison.  ColdFusion includes many decision operators, all of the following being case-insensitive.
</p>

<table>
	<thead>
		<tr>
			<th>
				CFML and CFScript Operators
			</th>
			<th>
				CF8+ CFScript Only
			</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>
				IS, EQUAL, EQ   
			</td>
			<td>
				==
			</td>
		</tr>
		<tr>
			<td>
				IS NOT, NOT EQUAL, NEQ   
			</td>
			<td>
				!=
			</td>
		</tr>
		<tr>
			<td>
				GT, GREATER THAN, LT, LESS THAN, GTE, LTE
			</td>
			<td>
				>,<,>=,<=
			</td>
		</tr>
		<tr>
			<td>
				CONTAINS
			</td>
			<td>
				N/A
			</td>
		</tr>
		<tr>
			<td>
				DOES NOT CONTAIN
			</td>
			<td>
				N/A
			</td>
		</tr>
	</tbody>
</table>

<p>
	These operators allow you to compare a set of values.  An example in action is:
</p>
<pre>
&lt;cfif myValue EQ 'ColdFusion'>
	..code…
&lt;/cfif>
</pre>

<p>
	Below is a fully formed example of a script based <span class="code">if/then/else</span> block.  Since ColdFusion is ECMAScript compliant, it should look very familiar:
</p>

<pre>
if (myValue == 'ColdFusion') {
	..code..
} else if (myValue != '.NET') {
	x = 277;
} else {
	..code..
}
</pre>
<p>
	There are also times you will want to compare more than one expression.  ColdFusion provides a series of Boolean operators to permit join and negation operations:
</p>

<p>
AND   /   &&<br />
OR   /   ||<br />
NOT   /   !<br />
XOR, EQV<br />
IMP - implication<br />
</p>

<p>
	An example of a compound expression looks like this:
</p>

<pre>
&lt;cfif structKeyExists(myStruct, 'age') AND myStruct.age LTE 7>
	..code..
&lt;/cfif>
</pre>

<p>
	The important thing to know about compound expressions is that ColdFusion will move from left to right when processing joined expressions.  The example above first checks to make sure the <span class="code">age</span> key exists in the structure called <span class="code">myStruct</span> before performing further operations on it.  If we check the value of the key and the key is not defined, ColdFusion will throw an error.  Since ColdFusion works from left to right, ColdFusion would first see that <span class="code">age</span> does not exist as a key in <span class="code">myStruct</span> (<span class="code">structKeyExists</span> will return <span class="code">false</span>) and it will not perform the second operation.  This is not the case for <span class="code">OR</span> operations.  Look at the following example:
</p>

<pre>
&lt;cfif myVar EQ 1 OR myVar EQ 10>
	..code..
&lt;/cfif>
</pre>

<p>
	ColdFusion would look first at <span class="code">myVar EQ 1</span>.  If it returned <span class="code">false</span>, it would simply move on to evaluate the second expression.  In this case, if our variable was equal to 1 or 10, the code inside the <span class="code">cfif</span> block would be evaluated.
</p>

<p>
	In the example above, we are checking if a variable is equal to a set value.  When programming, <span class="code">if/then/else</span> logic can become cumbersome when you need to perform an action based on a variable's value.  Programming languages use the <span class="code">switch/case</span> construct for this type of conditional logic. ColdFusion uses 3 tags to define <span class="code">switch/case</span> statement: <span class="code">cfswitch</span>, <span class="code">cfcase</span>, and <span class="code">cfdefaultcase</span>.  Look at the sample code below:
</p>

<pre>
&lt;cfswitch expression="#myVar#">
	&lt;cfcase value="1">
		..code..
	&lt;/cfcase>
	&lt;cfcase value="9,10" >
		..code..
	&lt;/cfcase>
	&lt;cfdefaultcase>
		..finally..
	&lt;/cfdefaultcase>
&lt;/cfswitch>
</pre>

<p>
	The code above defines a switch block based on the expression of the value of <span class="code">myVar</span>.  Note that we are using hash marks (<span class="code">#</span>) here as the <span class="code">expression</span> attribute, taking a string value, and comparing it to a set of possible matching values.  The possible values are each defined in their own <span class="code">cfcase</span> block.  <span class="code">cfcase</span> takes a string attribute named <span class="code">value</span>, and if it matches the current value, it will execute the code contained inside of the <span class="code">cfcase</span> block.  A value may only be declared once within the entire switch block or ColdFusion will throw an error.  <span class="code">cfswitch</span> will work from top to bottom to find the first matching value.  If it cannot find a matching value, it will execute the code contained inside of the <span class="code">cfdefaultcase</span> block.  It is not required to have a <span class="code">cfdefaultcase</span> block defined, but your logic will dictate if it is present.
</p>

<p>
	The second <span class="code">cfcase</span> declaration above lists more than one value.  If the expression is either <span class="code">9 OR 10</span>, the code will execute.  The default delimiter is '<span class="code">,</span>'.  If the value contains a comma, it is automatically treated as a list.  If you want the value to include a comma in the string, simply specify an alternate delimiter using the <span class="code">delimiters</span> attribute like this:
</p>

<pre>
&lt;cfcase value="9,10" delimiters="|">
	..code..
&lt;/cfcase>
</pre>

<p>
	This will allow the comparison value to be a string of 4 characters "<span class="code">9,10</span>".
</p>

<p>
	Astute programmers may have noticed we have not had to define a break for each case.  This is true in tag based CFML <span class="code">switch/case</span> statements.  In <span class="code">cfscript</span>, you will need to use the break statement as with any other programming language.  Here is an example of a switch case construct in <span class="code">cfscript</span>:
</p>
<pre>
switch (myVar) {
	case 1:
		writeOutput('Value was 1');
		break;
	case 9:
		writeOutput('Value was 9');
		break;
	default:
		writeOutput('Value was not 1 or 9');
}
</pre>

<p>
	ColdFusion also offers ternary operations.  A ternary operation is a construct that acts as a shorthand assignment operation given a comparison with exactly two possible outputs.  Here is an example in <span class="code">cfscript</span>:
</p>

<pre>
x = (myVar == 1) ? 1 : 277;
</pre>

<p>
	The above is equivalent to saying:
</p>

<pre>
if (myVar == 1) {
	x = 1;
} else {
	x = 277;
}
</pre>