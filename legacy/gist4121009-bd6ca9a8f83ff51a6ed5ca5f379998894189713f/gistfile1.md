<p>
Programming is all about doing stuff to things. Generally, the stuff is the execution of a process or algorithm and the things are information or data.
</p>
<p>
An algorithm is just a fancy name for a series of steps, like tying your shoelaces. Information or data is just values. Your name is a piece of information and so is your birth date. Since it's shorter, in this chapter we'll use the word data to describe a piece of information.
</p>
<p>
In ColdFusion, data is held in variables. Think of a variable like a mailbox. You can stuff things like letters and packages into a mailbox and get them out later to do stuff. ColdFusion makes storing information very easy because it's a loosely typed Language. You can stick any kind of data into a ColdFusion variable without having to tell ColdFusion what kind of data it is.
</p>
<h3>
Here's the simplest code to set a variable:
</h3>
<pre class="prettyprint">
&lt;cfset ThisIs = "fun" /&gt;
</pre>

<p>
Now, any time I refer to <strong>ThisIs</strong> in my ColdFusion code, it'll hold the data "fun". You can look at the contents of a variable in ColdFusion by using the <span class="code">cfdump</span> tag.
</p>

<pre class="prettyprint">
&lt;cfdump var = "#ThisIs#" /&gt;
</pre>

<p>
See how the variable contains the string <strong>"fun"</strong>?
</p>
<p>
<strong>A few things to note.</strong> Examine the statement again:
</p>

<pre class="prettyprint">
&lt;cfset ThisIs = "fun" /&gt;
</pre>

<p>
The part of the statement to the left of the equals sign (<strong>ThisIs</strong>) is the variable name. The part of the statement to the right of the equals sign (<strong>"fun"</strong>) is the value to assign to the variable.
</p>
<p>
	Now, in the second statement, you’ll note we surrounded the variable name with pound # or hash symbols.  The pound sign tells ColdFusion to evaluate the contents. In the below example, the pound sign will tell ColdFusion to replace the ThisIs string with the contents of the previously defined variable ThisIs.
</p>
<pre class="prettyprint">
&lt;cfdump var = "#ThisIs#" /&gt;
</pre>
<p>
	Here’s another way to look at pound sign use. Examine the below three statements. Can you guess what will happen in each case?
</p>
<pre class="prettyprint">
&lt;cfdump var = "1 + 2" /&gt;&lt;br /&gt;
&lt;cfdump var = "#1 + 2#" /&gt;&lt;br /&gt;
&lt;cfdump var = "1 + 2 IS #1 + 2#" /&gt;&lt;br /&gt;
</pre>
<p>
	In the first statement, our math problem is surrounded by the Double Quote character. This tells ColdFusion to treat the statement as a string and do no evaluations on it.
</p>
<p>
	In the second statement, we also surrounded the math problem with the pound sign. ColdFusion executes the statement and performs our calculation for us.
</p>
<p>
In the third statement, notice we’ve mixed strings and evaluations through the correct use of the pound sign and the double quotes.
</p>

<h2>
The Left Side Of The Statement: &lt;cfset ThisIs
</h2>
<p>
The left side of the statement is the variable name. You can have numbers as part of the variable name, but the variable name must start with a letter. You must not have any spaces in your variable names. If you need to use more words for your variable name, you can simply write the variable with <strong>CamelCase</strong> letters, or use Under_Scores to separate each word if you want. The choice is one of style; there are no right answers. Also, most special characters are not allowed in variable names. A good rule to follow is variable names should be descriptive and help provide context to what is being done.
</p>
<p>
For example, the word <strong>variable</strong> is a bad naming choice because the name adds no context to why the variable exists:
</p>

<pre class="prettyprint">
&lt;cfset variable = "12/26/1975" /&gt;
</pre>
<p>
The variable name <strong>UserBirthdate</strong> is a good naming choice because it adds context to why the variable exists:
</p>

<pre class="prettyprint">
&lt;cfset UserBirthdate = "12/26/1975" /&gt;
</pre>
<blockquote>
<strong>Pro Tip:</strong> You'll understand the most about WHY your program is written a certain way as you are writing it. Take advantage of that hard-earned understanding and leave yourself (or others) as many clues and as much context as possible. Later on, after you've forgotten some of the details, it'll be much easier to piece together why the program was written a certain way and it'll be quicker to make good updates to your program.
</blockquote>
<h2>
	The Right Side Of The Statement: "fun" /&gt;
</h2>

<p>
The right side of the statement contains the value for the variable. Simple strings are enclosed in single or double quotes, with double quotes being the most common.
</p>
<p>
The right side of the statement is an execution zone. This means ColdFusion will attempt to evaluate items on the right side of the statement.
</p>
<h2>
	Examples
</h2>
<p>
	Here are a few examples that will help you understand setting ColdFusion variables:
</p>
<h3>
Print Out the Current Date:
</h3>
<pre class="prettyprint">
&lt;cfset DateToday = now() /&gt;
&lt;cfdump var = "#DateToday#" /&gt;
</pre>
<p>
If you were to run the code example you would see how the ColdFusion function <span class="code">now()</span>, which gets the servers current date and time, was evaluated and the contents placed in the variable DateToday? Anything not specifically in quotes (double or single) will be evaluated. It is possible to evaluate items in quotes, if you use the # sign. Keep this in mind as you develop ColdFusion. Novices have a tendency to overuse the pound sign.
</p>
<h3>
Alternate Method: Print Out the Current Date:
</h3>
<p>
This code will evaluate to the same thing in the previous step.
</p>

<pre class="prettyprint">
&lt;cfset DateToday = "#now()#" /&gt;
&lt;cfdump var = "#DateToday#" /&gt; 
</pre>
<p>
However, unless there are strings in the quotes, it's generally preferred to use the previous method.
</p>
<p>
	To mix execution and strings, do this:
</p>
<h3>
	Mix Execution and Strings
</h3>
<pre class="prettyprint">
&lt;cfset DateToday = "Today is: #now()#" /&gt;
&lt;cfdump var = "#DateToday#" /&gt; 
</pre>
<h3>
Concatenation
</h3>

<p>
You could also concatenate the strings using the & operator. This example is functionally equal to the previous example:
</p>
<pre class="prettyprint">
&lt;cfset DateToday = "Today is: " & now() /&gt;
&lt;cfdump var = "#DateToday#" /&gt; 
</pre>
<p>
<strong>So is this one:</strong>
</p>
<pre class="prettyprint">
&lt;cfset DateToday = "Today is: " /&gt;
&lt;cfset DateToday = DateToday & now() /&gt;
&lt;cfdump var = "#DateToday#" /&gt; 
</pre>
<p>
See how we added DateToday to another evaluation and replaced the DateToday variable name with the new contents?
</p>
<h2>
	Outputting a Variable
</h2>

<p>
You will often need to output the contents of the variables you create. One reason is to display the contents of a variable to the user, perhaps to display the username on a web page. Another reason is to verify the contents of a variable while you are in the process of writing or debugging your program.
</p>
<h4>
	About cfoutput 
</h4>

<p>
To display the contents of a variable to a user, use <span class="code">cfoutput</span>. The variable reference must be a simple value that can be displayed as text. This includes Strings, Numbers, Dates, Times, and so on. Complex variables, such as Structs, Arrays, Queries, Functions, and so on, can not be displayed with the <span class="code">cfoutput</span> command because they are not displayable as text.
</p>
<h4>
Example of cfoutput Usage
</h4>
<pre class="prettyprint">
&lt;cfset DateToday = "Today is: #now()#" /&gt;
	
&lt;cfoutput&gt;#DateToday#&lt;/cfoutput&gt;
</pre>
<p>
The variable will be evaluated, and the variable contents will be added to the current end of the response buffer. i.e. it will be displayed to the user.
</p>
<h4>
	About cfdump
</h4>

<p>
To inspect or verify the contents of a variable while writing or debugging your program, use <span class="code">cfdump</span>. ColdFusion makes it very easy to see the contents of ANY variable by using the <span class="code">cfdump</span> command. <span class="code">cfdump</span> will convert the variable contents to a string representation and format it for easy viewing. The <span class="code">cfdump</span> command can be used to help debug your program.
</p>
<h4>
Example of cfdump Usage
</h4>
<pre class="prettyprint">
&lt;cfset DateToday = "Today is: #now()#" /&gt;
	
&lt;cfdump var = "#DateToday#" /&gt;
	
&lt;cfset DateArray = [dateFormat(now(), "short"), dateFormat(dateadd('d',1,now()), "short"), dateFormat(dateadd('d',2,now()), "short")] /&gt;
	
&lt;cfdump var = "#DateArray#" /&gt;
	
&lt;cfset DateStruct = { today=dateFormat(now(), "short"), tomorrow=dateFormat(dateadd('d',1,now()), "short"), later=dateFormat(dateadd('d',2,now()), "short") } /&gt;
	
&lt;cfdump var = "#DateStruct#" /&gt;
</pre>