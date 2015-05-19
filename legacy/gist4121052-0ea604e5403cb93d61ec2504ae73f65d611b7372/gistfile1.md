<p>
	In the first part of this hands on we are going to convert some pages to .cfm pages. We will then add some variables and output them to the user. Finally, we will add a comment to our code.
</p>
<p>
	<strong>Tags Used</strong>: <a href="http://help.adobe.com/en_US/ColdFusion/10.0/CFMLRef/WSc3ff6d0ea77859461172e0811cbec22c24-7ffd.html" target="_new">&lt;cfset></a>, <a href="http://help.adobe.com/en_US/ColdFusion/10.0/CFMLRef/WSc3ff6d0ea77859461172e0811cbec22c24-7ff6.html" target="_new">&lt;cfoutput></a> 
</p>	
<p>
	<ol>
		<li>
			Rename the <span class="code">/www/index.html</span> file to <span class="code">index.cfm</span>.
		</li>
		<li>
			Confirm that the ColdFusion page displays by going to <span class="code">/www/index.cfm</span> in your browser.
		</li>
		<li>
			Open up the <span class="code">/www/index.cfm</span> file in your code editor.
		</li>
		<li>
			First, let's create some variables that we will display later on in the page. On line 1, write a <span class="code">&lt;cfset></span> tag that sets the variable <span class="code">myName</span> with a value of your name. The tag should look something like this:
<pre class="prettyprint">
&lt;cfset myName="Simon" /&gt;
</pre>
		</li>
		<li>
			On the next line, create another variable called <span class="code">myPosition</span> with a value of 'Developer'. The tag should look something like:
<pre class="prettyprint">
&lt;cfset myPosition="Developer" /&gt;
</pre>
		</li>
		<li>
			Now, let's output these variables. Locate the text [Name] on or around line 80. Replace [Name] with <span class="code">#myName#</span>.
		</li>
		<li>
			Locate the text [position] on or around line 81. Replace [position] with <span class="code">#myPosition#</span>.
		</li>
		<li>
			Refresh the page in your browser and confirm that you now see <span class="code">#myName#</span> and <span class="code">#myPosition#</span> displayed.
		</li>
		<li>
			In your code editor, locate the <span class="code">#myName#</span> variable on or around line 80 and place a <span class="code">&lt;cfoutput></span> tag before it and a <span class="code">&lt;/cfoutput></span> tag after it so that the code looks similar to this:
<pre class="prettyprint">
&lt;cfoutput>#myName#&lt;/cfoutput&gt;	
</pre>
		</li>
		<li>
			Do the same for the <span class="code">myPosition</span> variable on or around line 81.
		</li>
		<li>
			Refresh the browser and confirm that you now see your name and position displayed on the page.
		</li>
		<li>
			Go to line 2 and update the variable <span class="code">myPosition</span> so that it has a value of 'A Developer'. The tag should look similar to this:
<pre class="prettyprint">
&lt;cfset myPosition="A Developer" /&gt;
</pre>
		</li>
		<li>
			Refresh the browser and confirm that you see your change.
		</li>
		<li>
			In your code editor, locate the comment that says <span class="code">Data Output</span>. Add a new line after this tag and write the following text: "This is where the name and position are output".
		</li>
		<li>
			Refresh the browser and confirm that you see this text displayed on the page.
		</li>
		<li>
			Go back to your code editor and add ColdFusion comments around the line of text so that it looks similar to this:
<pre class="prettyprint">
&lt;!--- This is where the name and position are output ---&gt;	
</pre>
		</li>
		<li>
			Refresh the browser and confirm that the text is no longer visible on the page.
		</li>
		<li>
			In your code editor, locate the link to <span class="code">index.html</span> on or around line 52. Change the link so that it points to <span class="code">index.cfm</span>.
		</li>
		<li>
			Now let's update some of the links to point to the new .cfm pages. Locate the link to <span class="code">about.html</span> on or around line 53 and change it to point to <span class="code">about.cfm</span>.
		</li>
		<li>
			Rename the <span class="code">/www/about.html</span> file to <span class="code">about.cfm</span>.
		</li>
		<li>
			Refresh your browser and click on the <span class="code">about</span> link at the top of the page.
		</li>
		<li>
			Confirm that the about page loads.
		</li>
	</ol>
</p>