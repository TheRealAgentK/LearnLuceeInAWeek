<p>
	In this section of the hands on we will switch from tag based code to script based code and create a structure of data. We will then output that on the page.
</p>
<p>
	<strong>Tags Used</strong>: <a href="http://help.adobe.com/en_US/ColdFusion/10.0/CFMLRef/WSc3ff6d0ea77859461172e0811cbec22c24-7ebf.html" target="_new">&lt;cfscript></a>, <a href="http://help.adobe.com/en_US/ColdFusion/10.0/CFMLRef/WSc3ff6d0ea77859461172e0811cbec22c24-7ff6.html" target="_new">&lt;cfoutput></a>
</p>	
<p>
	<ol>
		<li>
			Open up the <span class="code">/www/about.cfm</span> file in your code editor.
		</li>
		<li>
			Locate line 1 and write an opening and closing <span class="code">&lt;cfscript></span> block. Put the closing <span class="code">&lt;/cfscript></span> tag on the second line. Your code should look something like this:
<pre class="prettyprint">
&lt;cfscript&gt;
&lt;/cfscript&gt;
</pre>
		</li>
		<li>
			In between the opening and closing <span class="code">&lt;cfscript></span> tags, create a struct by write the following code:
<pre class="prettyprint">
personalInfo = {name='', dob='', address='', phonenumber='', email='', website='', skype=''};
</pre>			
		</li>
		<li>
			For each variable of the <span class="code">personalInfo</span> struct, provide some information (you do not have to use real information if you prefer not to).
		</li>
		<li>
			Locate the [Name] placeholder text on or around line 116.
		</li>
		<li>
			Replace [Name] with <span class="code">#personalInfo.name#</span>.
		</li>
		<li>
			Replace the other placeholders with their matching variables in the <span class="code">personalInfo</span> struct.
		</li>
		<li>
			Wrap all the <span class="code">&lt;div></span> tags with the class of clr in a <span class="code">&lt;cfoutput></span> tag. Your code should look similar to this:
<pre class="prettyprint">
&lt;cfoutput&gt;
	&lt;div class="clr"&gt;&lt;div class="input-box"&gt;Name &lt;/div&gt;&lt;span&gt;#personalInfo.name#&lt;/span&gt; &lt;/div&gt;
	&lt;div class="clr"&gt;&lt;div class="input-box"&gt;Date of birth &lt;/div&gt;&lt;span&gt; #personalInfo.dob#&lt;/span&gt;&lt;/div&gt;
	&lt;div class="clr"&gt;&lt;div class="input-box"&gt;Address&lt;/div&gt;&lt;span&gt; #personalInfo.address#&lt;/span&gt;&lt;/div&gt;
	&lt;div class="clr"&gt;&lt;div class="input-box"&gt;Phone&lt;/div&gt; &lt;span&gt;#personalInfo.phoneNumber#&lt;/span&gt;  &lt;/div&gt;
	&lt;div class="clr"&gt;&lt;div class="input-box"&gt;E-mail&lt;/div&gt;&lt;span&gt;&lt;a href="#"&gt;#personalInfo.email#&lt;/a&gt;&lt;/span&gt;  &lt;/div&gt;
	&lt;div class="clr"&gt;&lt;div class="input-box"&gt;Website &lt;/div&gt; &lt;span&gt;&lt;a href="#"&gt;#personalInfo.website#&lt;/a&gt;&lt;/span&gt; &lt;/div&gt; 
	&lt;div class="clr"&gt;&lt;div class="box1"&gt;Skype &lt;/div&gt; &lt;span&gt;&lt;a href="#"&gt;#personalInfo.skype#&lt;/a&gt;&lt;/span&gt; &lt;/div&gt; 
&lt;/cfoutput&gt;
</pre>			
		</li>
		<li>
			To test that your changes have taken place, load the <span class="code">/www/about.cfm</span> page in your browser.
		</li>
		<li>
			Notice that you have received a ColdFusion Error. The error states that it has found an Invalid CFML construct. This is due to the single # signs inside the links for email, website, and Skype. ColdFusion uses the # sign to denote variables and it is trying to evaluate everything between the first # sign and the next one. To resolve the error, we must escape the single # signs.
		</li>
		<li>
			Locate the link that wraps around the email output on or around line 121.
		</li>
		<li>
			Update the value of the href attribute to ## rather than #. You're <span class="code">&lt;a></span> tag should look similar to this:
<pre class="prettyprint">
&lt;a href="##"&gt;
</pre>
		</li>
		<li>
			Do this also for the website and Skype links.
		</li>
		<li>
			Refresh the <span class="code">/www/about.cfm</span> page in your browser and confirm that you now see your information being displayed.
		</li>
	</ol>
</p>
<h2>
	Homework
</h2>
<p>
	<ol>
		<li>
			Convert all remaining .html pages to .cfm pages.
		</li>
		<li>
			Update all navigation links to point to the .cfm files rather than the .html files.
		</li>
		<li>
			Create a structure on the Contact page that stores your address, phone number, email, and Skype information; display it on the right hand side under Contact Info.
		</li>
	</ol>
</p>