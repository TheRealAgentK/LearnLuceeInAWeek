<p>
In our previous sections we talked about the importance of adding context into your programs. You’ll find you will spend much more time reading programs for the purposes of debugging and enhancing, than you spend writing the program. So take care to write your programs in such a way the program can be read and understood as easily as possible. </p>
<p>
Context is important because our programs express a problem to a computer using a kind of shorthand, in our case ColdFusion programming code. The computer doesn’t much care about the amount of context in the application, as long as the instructions (code) are all properly formed. The program is good enough for the computer if it works well. But this doesn’t necessarily mean the program is good enough for a human. Programs that are good for humans can be efficiently understood, debugged and enhanced by another programer.
</p>
<p>
One way to add context is to use descriptive variable names.
</p>

<h3>
Not Descriptive:
</h3>
<pre class="prettyprint">
&lt;cfset var1 = "42" /&gt;
</pre>
<h3>
Descriptive:
</h3>
<pre class="prettyprint">
&lt;cfset AnswerForEverything = 42 /&gt;
</pre>
<p>
Another way to add context to your program is by writing a descriptive comment. ColdFusion comments resemble HTML comments, only with an extra dash on each end.
</p>
<p>
Any text or programming code inside of a comment is not executed nor displayed. Only a person with access to the source code can see the content inside of a comment.
</p>
<pre class="prettyprint">
HTML Comment
&lt;!-- I am an HTML Comment--&gt;

ColdFusion Comment
&lt;!---  I am a ColdFusion Comment---&gt;

&lt;cfscript>
    // I am a ColdFusion Comment in CFScript for a single line
    /*
        I am a multi-line
        ColdFusion Comment in CFScript
    */
&lt;/cfscript&gt;
</pre>

<h2>
	Example of Good Comments
</h2>
<p>	
You can use comments to describe your intent and give context to a section of your programming code:
</p>
<pre class="prettyprint">
&lt;!--- Always load the hard coded value if specified ---&gt;
&lt;cfif len( trim ( ChartHelperName ) )&gt;
    &lt;cfset ReportPeriod = ChartHelperName /&gt;
&lt;/cfif&gt;

&lt;!--- Load the Chart Helper as defined in the config ---&gt;
&lt;cfset ChartHelper = ChartHelperLoader.load( ReportPeriod, filter, ChartHelperOptionList ) /&gt;

&lt;!--- Add the bits to the helper, shove the helper in the event, then announce the right result ---&gt;
&lt;cfset event.setValue( ChartHelperEventValue, ChartHelper ) /&gt;
</pre>
<p>
Programming code explains the HOW, portion of problem solving. Proper use of comments explain the WHY part of the problem solving. It's much better to make comment notations about your program when you are writing your program because that is when you best understand the problem and how you have chosen to solve it.
</p>

<p>
	Later on, after the program has been written, you will be very happy to have good comments in your program explaining the WHY part of your program, so you can make updates and alterations in the same spirit as when you wrote the initial program.
</p>