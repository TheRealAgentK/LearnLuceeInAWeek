<p>
	ColdFusion has been designed to allow the use of ColdFusion tags and ColdFusion script. Functionally, both will be interpreted equally and will achieve the same result. The use of ColdFusion Tags and ColdFusion Script is up to personal or team preference. One or two ColdFusion operations are currently Tag only, as of this tutorial, but these will be made available in ColdFusion script in future releases.
</p>
<p>
Some developers write all ColdFusion code in Tags. Some developers write all ColdFusion code in Script. Some write the view portions of their ColdFusion code in Tags and the business layer portion in Script. As long as you stay consistent, all approaches are valid. The overarching rule should be legibility and consistency.
</p>
<p>
Let's look at some statements and compare the differences:
</p>
<h3>
Setting a Variable:
</h3>
<pre class="prettyprint">
&lt;cfset variable = "value" /&gt;
&lt;cfscript&gt;
    variable = "value";
&lt;/cfscript&gt;
</pre>
<h3>
Looping Over an Array:
</h3>
<pre class="prettyprint">
&lt;cfset FruitArray = ["apple", "banana", "cherry"] /&gt;
&lt;cfloop from="1" to="#arrayLen( FruitArray)#" index="i"&gt;
    &lt;cfoutput&gt;#FruitArray[i]#&lt;/cfoutput&gt;
&lt;/cfloop&gt;

&lt;cfscript&gt;
    FruitArray = ["apple", "banana", "cherry"];
    for( i=1; i <= arrayLen(FruitArray); i++){
        writeOutput(FruitArray[i]);
    }
&lt;/cfscript&gt;
</pre>
<p>
Some developers find the ColdFusion Script syntax to resemble other familiar programming languages. ColdFusion is designed to provide a welcoming and productive developer experience. Try both styles to see which you prefer. The ColdFusion documentation has several good pages on ColdFusion script. <a href="http://help.adobe.com/en_US/ColdFusion/10.0/Developing/WSc3ff6d0ea77859461172e0811cbec22c24-7feb.html" target="_new">http://help.adobe.com/en_US/ColdFusion/10.0/Developing/WSc3ff6d0ea77859461172e0811cbec22c24-7feb.html</a>
</p>