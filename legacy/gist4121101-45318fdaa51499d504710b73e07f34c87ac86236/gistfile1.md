<p>
	In this hands on, you are going to update our code to provide a better user experience to your users as well as improve the form validation.
</p>
<p>
	<strong>Tags Used</strong>: <a href="http://help.adobe.com/en_US/ColdFusion/10.0/CFMLRef/WSc3ff6d0ea77859461172e0811cbec22c24-7faf.html" target="_new">&lt;cfparam></a>, <a href="http://help.adobe.com/en_US/ColdFusion/10.0/CFMLRef/WSc3ff6d0ea77859461172e0811cbec22c24-7ff6.html" target="_new">&lt;cfoutout></a>
</p>	
<p>
	<strong>Functions Used</strong>: <a href="http://help.adobe.com/en_US/ColdFusion/10.0/CFMLRef/WSc3ff6d0ea77859461172e0811cbec22c24-7f38.html" target="_new">len</a>, <a href="http://help.adobe.com/en_US/ColdFusion/10.0/CFMLRef/WSc3ff6d0ea77859461172e0811cbec22c24-7b61.html" target="_new">trim</a>
</p>	

<p>
	<ol>
		<li>
			Locate the <span class="code">&lt;cfparam></span> tag at the top of the <span class="code">/www/contact.cfm</span> file.
		</li>
		<li>
			Below the <span class="code">&lt;cfparam></span> tag, create another one for contactname, email, and message. Leave the default attribute as empty. Your code should look similar to this:
<pre class="prettyprint">
&lt;cfparam name="form.contactname" default="" /&gt;
&lt;cfparam name="form.email" default="" /&gt;
&lt;cfparam name="form.message" default="" /&gt;
</pre>
		</li>
		<li>
			Locate the <span class="code">contactname</span> form input on or around line 132 and add a <span class="code">value</span> attribute with a value of <span class="code">#form.contactname#</span>.
		</li>
		<li>
			Locate the <span class="code">email</span> form input on or around line 136 and add a <span class="code">value</span> attribute with the value of <span class="code">#form.email#</span>.
		</li>
		<li>
			Locate the <span class="code">message</span> textarea on or around line 140 and place the value <span class="code">#form.message#</span> between the open and close tags.
		</li>
		<li>
			Confirm your code looks similar to this: 
<pre class="prettyprint">
&lt;div&gt;
	&lt;label&gt;Name &lt;span class="font-11"&gt;(required)&lt;/span&gt;&lt;/label&gt;
	&lt;input name="contactname" type="text" class="required" value="#form.contactname#"/&gt;
&lt;/div&gt;


&lt;div&gt;
	&lt;label&gt;E-mail &lt;span class="font-11"&gt;(required)&lt;/span&gt;&lt;/label&gt;				
	&lt;input name="email" type="text" class="required email" value="#form.email#"/&gt;		
&lt;/div&gt;


&lt;div class="textarea"&gt;
	&lt;label&gt;Message &lt;span class="font-11"&gt;(required)&lt;/span&gt;&lt;/label&gt;				
	&lt;textarea name="message" rows="6" cols="60" class="required"&gt;#form.message#&lt;/textarea&gt;		
&lt;/div&gt;
</pre>
		</li>
		<li>
			Locate the open <span class="code">&lt;form></span> tag on or around line 129 and put on open <span class="code">&lt;cfoutput></span> tag before the form tag.
		</li>
		<li>
			Locate the closing <span class="code">&lt;/form></span> tag on or around line 146 and put a closing <span class="code">&lt;/cfoutput></span> tag after the form tag.
		</li>
		<li>
			Reload the <span class="code">contact.cfm</span> page in your browser; fill in 2 of the 3 inputs of the form and click 'submit'.
		</li>
		<li>
			Notice that the form is now pre-populated with the values you submitted, but you still receive the message "You did not provide all the required information!"
		</li>
		<li>
			Reload the <span class="code">contact.cfm</span> page in your browser.
		</li>
		<li>
			Add a space in all form fields and click submit.
		</li>
		<li>
			Notice that the message does not display on the page. This is due to the fact that the form fields do have a length, even though it is just a space.
		</li>
		<li>
			Locate the <span class="code">&lt;cfif></span> statement that checks the length of <span class="code">form.contactname</span> on or around line 108.
		</li>
		<li>
			Wrap the <span class="code">form.contactname</span> variable in a <span class="code">trim()</span> function. This will remove all whitespace at the beginning and end of the variable.
		</li>
		<li>
			Your code should look similar to this:
<pre class="prettyprint">
&lt;cfif len(trim(form.contactname)) eq 0&gt;
</pre>			
		</li>
		<li>
			Add the <span class="code">trim</span> function to the <span class="code">form.email</span> and <span class="code">form.message</span> <span class="code">&lt;cfif></span> statements.
		</li>
		<li>
			Reload the <span class="code">contact.cfm</span> page in your browser and add spaces to all 3 form fields. Notice that the message is displayed.
		</li>
	</ol>
</p>