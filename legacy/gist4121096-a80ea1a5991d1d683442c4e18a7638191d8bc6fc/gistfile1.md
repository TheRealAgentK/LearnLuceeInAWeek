<p>
	In this hands on, you are going to validate the form data that was submitted and output any problems that might have occurred. We will access data from the form scope.
</p>
<p>
	<strong>Tags Used</strong>: <a href="http://help.adobe.com/en_US/ColdFusion/10.0/CFMLRef/WSc3ff6d0ea77859461172e0811cbec22c24-7ffd.html" target="_new">&lt;cfset></a>, <a href="http://help.adobe.com/en_US/ColdFusion/10.0/CFMLRef/WSc3ff6d0ea77859461172e0811cbec22c24-7fe8.html" target="_new">&lt;cfif></a> 
</p>	
<p>
	<strong>Functions Used</strong>: <a href="http://help.adobe.com/en_US/ColdFusion/10.0/CFMLRef/WSc3ff6d0ea77859461172e0811cbec22c24-7f38.html" target="_new">len</a>
</p>	
<p>
	<ol>
		<li>
			Locate the comment that says <span class="code">Message Output</span> in the <span class="code">/www/contact.cfm</span> file and remove all the code that is inside the <span class="code">&lt;cfif></span> tag just below it.
		</li>
		<li>
			Inside the <span class="code">&lt;cfif></span> tag create a variable called <span class="code">OK</span> and set it to true.
		</li>
		<li>
			Below the <span class="code">&lt;cfset></span>, create a <span class="code">&lt;cfif></span> statement that checks if the length of the value of <span class="code">form.contactname</span> is equal to 0. To do that, use a function called <span class="code">len()</span> which will return the number of characters in the provided string. Your code should look similar to this:
			
<pre class="prettyprint">
&lt;cfset ok = true /&gt;
					
&lt;cfif len(form.contactname) eq 0&gt;

&lt;/cfif&gt;
</pre>
		</li>
		<li>
			Inside the <span class="code">&lt;cfif></span> statement, set the <span class="code">OK</span> variable to false.
		</li>
		<li>
			You should end up with code similar to this:
<pre class="prettyprint">
&lt;cfset ok = true /&gt;
					
&lt;cfif len(form.contactname) eq 0&gt;
	&lt;cfset ok = false /&gt;
&lt;/cfif&gt;
</pre>
		</li>
		<li>
			Create <span class="code">&lt;cfif></span> statements for the email and message fields in the form.
		</li>
		<li>
			After the last <span class="code">&lt;cfif></span> statement, create a new <span class="code">&lt;cfif></span> statement that checks if the <span class="code">OK</span> value is equal to false. If it is equal to false, output the following:
<pre class="prettyprint">
&lt;p&gt;You did not provide all the required information!&lt;/p&gt;
</pre>	
		</li>
		<li>
			Your final block of code should look similar to this:
<pre class="prettyprint">
&lt;cfif form.submitted&gt;
	&lt;cfset ok = true /&gt;
					
	&lt;cfif len(form.contactname) eq 0&gt;
		&lt;cfset ok = false /&gt;
	&lt;/cfif&gt;	
					
	&lt;cfif len(form.email) eq 0&gt;
		&lt;cfset ok = false /&gt;
	&lt;/cfif&gt;	
					
	&lt;cfif len(form.message) eq 0&gt;
		&lt;cfset ok = false /&gt;
	&lt;/cfif&gt;	
					
	&lt;cfif ok eq false&gt;
		&lt;p&gt;You did not provide all the required information!&lt;/p&gt;
	&lt;/cfif&gt;	
&lt;/cfif&gt;
</pre>
		</li>
		<li>
			Reload the <span class="code">contact.cfm</span> page in your browser and click 'submit'. You should see the message "You did not provide all the required information!" displayed.
		</li>
		<li>
			Fill in all the fields in the form and click 'submit'. You will notice that the message does not display.
		</li>
	</ol>
</p>