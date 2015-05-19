<p>
	In this hands on, we are going to refactor our code and take out any unnecessary logic we might have.
</p>
<p>
	<strong>Tags Used</strong>: <a href="http://help.adobe.com/en_US/ColdFusion/10.0/CFMLRef/WSc3ff6d0ea77859461172e0811cbec22c24-7fe8.html" target="_new">&lt;cfif></a>, <a href="http://help.adobe.com/en_US/ColdFusion/10.0/CFMLRef/WSc3ff6d0ea77859461172e0811cbec22c24-7fe6.html" target="_new">&lt;cfelse></a>
</p>	
<p>
	<ol>
		<li>
			Open up the <span class="code">/www/contact.cfm</span> file in your code editor and locate the <span class="code">&lt;cfif></span> statement that checks the <span class="code">form.contactname</span> variable. Remove the <span class="code">eq 0</span> part of the expression; as any number greater than 0 is treated as true, and the number 0 is treated as false, we do not need this additional part of the <span class="code">&lt;cfif></span> statement. Because we only want to run the code when there is NO value passed we must negate the value by putting the word NOT before it. 
		</li>
		<li>
			Remove the <span class="code">eq 0</span> part of the <span class="code">form.email</span> and <span class="code">form.message</span> <span class="code">&lt;cfif></span> statements and add NOT before the <span class="code">len</span> function call.
		</li>
		<li>
			Locate the <span class="code">&lt;cfif></span> statements that checks the variable <span class="code">OK</span> on or around line 120.
		</li>
		<li>
			Remove the <span class="code">eq false</span> part of the expression. As a <span class="code">&lt;cfif></span> tag is looking for a true or false value, we do not need to check the value of the variable as it is already going to be a true or false value. As we are checking if the variable is false then we need to put the ! symbol before the variable.  ! is the same as NOT.
		</li>
		<li>
			Before the closing <span class="code">&lt;/cfif></span> tag of the expression that checks the <span class="code">OK</span> variable, insert a <span class="code">&lt;cfelse></span> tag.
		</li>
		<li>
			Between the <span class="code">&lt;cfelse></span> tag and the closing <span class="code">&lt;/cfif></span> tag add the following code: &lt;p>Form submitted successfully!&lt;/p>
		</li>
		<li>
			Your final code block should look similar to this:
<pre class="prettyprint">
&lt;cfif form.submitted&gt;
	&lt;cfset ok = true /&gt;
	
	&lt;cfif NOT len(trim(form.contactname))&gt;
		&lt;cfset ok = false /&gt;
	&lt;/cfif&gt;	
	
	&lt;cfif NOT len(trim(form.email))&gt;
		&lt;cfset ok = false /&gt;
	&lt;/cfif&gt;	
	
	&lt;cfif NOT len(trim(form.message))&gt;
		&lt;cfset ok = false /&gt;
	&lt;/cfif&gt;	
	
	&lt;cfif !ok&gt;
		&lt;p&gt;You did not provide all the required information!&lt;/p&gt;
	&lt;cfelse&gt;
		&lt;p&gt;Form submitted successfully!&lt;/p&gt;	
	&lt;/cfif&gt;	
&lt;/cfif&gt;
</pre>	
		</li>
		<li>
			Reload the <span class="code">contact.cfm</span> page in your browser and enter spaces in all form fields.
		</li>
		<li>
			Click 'submit' and notice that the message "You did not provide all the required information!" message is displayed.
		</li>
		<li>
			Provide information for all the form fields and click 'submit'.
		</li>
		<li>
			Notice that the message "Form submitted successfully!" is displayed.
		</li>
	
	</ol>
</p>