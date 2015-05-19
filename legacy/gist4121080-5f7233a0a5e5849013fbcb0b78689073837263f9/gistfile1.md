<p>
	ColdFusion groups variables together in scopes, or a range in which a variable can be accessed.  Think of a scope as a bucket of memory that can store variables.  Each scope has its own purpose, and each scope has its own lifecycle.
</p>

<p>
	The following table shows major scopes available in a running ColdFusion application:
</p>
<ul>
	<li>
		<strong>Variables</strong>: Default scope available in ColdFusion templates. Variables are available only during the execution of the template.
	</li>
	<li>
		<strong>URL</strong>: All variables in the query string or sent to ColdFusion via an HTTP GET request are available in the URL scope.  URL variables are available for the current request.
	</li>
	<li>
		<strong>Form</strong>: All variables posted from a form (HTTP POST) are available in the Form scope. Form variables are available for the current request.
	</li>
	<li>
		<strong>CGI</strong>: CGI variables sent from the browser are placed into the CGI scope.  CGI variables are available for the current request.
	</li>
	<li>
		<strong>Query (not a true scope)</strong>: Upon execution of a query, the resultset is placed into a named scope as specified by the operator assignment or <span class="code">cfquery</span> tag's <span class="code">name</span> attribute.  The data stored in this pointer is available for the current request.
	</li>
	<li>
		<strong>Server</strong>: Developers may choose to utilize the server scope to share data across application running within the context of the current ColdFusion instance or cluster.  This scope persists across requests, and is available until the server shuts down.
	</li>
	<li>
		<strong>Application</strong>: Application variables are shared amongst all connected clients for the current named application.  This scope is also used for objects instantiated using the singleton pattern.  This scope is available across requests for the life of the application, which may terminate on server shutdown, application malfunction, or application timeout.
	</li>
	<li>
		<strong>Session</strong>: Developers use session variables to store a single visitor's data across requests.  This scope is only available to the current session, and will persist until server or application termination, or session timeout.
	</li>
	<li>
		<strong>Request</strong>: The request scope contains data that is available to all functions, CFCs, templates, and custom tags executed during the context of the current request.  Data in this scope is available during the current request.
	</li>
	<li>
		<strong>Arguments</strong>: The arguments scope contains data passed into a ColdFusion function.  The arguments scope is mutually exclusive with the local function scope, and may not contain the same variable names as the local scope.  This scope is available during the current execution of a function, and is private to the current function context.
	</li>
	<li>
		<strong>Attributes</strong>: This scope contains variables passed in as attributes to a ColdFusion custom tag.  The data in this scope is available during the execution lifespan of a custom tag.  Refer to the ColdFusion Livedocs for additional scopes available to custom tags, as well as how scopes are handled in nested custom tags.
	</li>
	<li>
		<strong>Local (function)</strong>: The Local scope may be referenced explicitly, or defined using the var keyword.  Variables in this scope are private to the current function context.  This scope is mutually exclusive with the arguments scope, and may not contain the same variable names as the arguments scope.
	</li>
</ul>
<blockquote>
	NOTE: The above list is not all-inclusive.  Please reference the Adobe Livedocs documentation for additional and tag specific scopes.
</blockquote>

<p>
	To reference a scoped variable in ColdFusion, we preface the variable pointer with the scope in dot-notation.  To access a variable named <span class="code">myVar</span> in the <span class="code">Application</span> scope, we would write <span class="code">application.myVar</span>. It is considered to be a best practice to scope all variables in your ColdFusion application; however, it is not always necessary.  ColdFusion will attempt to figure out what scope the variable is stored in if you do not explicitly provide one by searching each scope one at a time using scope precedence.  The following list shows the order in which ColdFusion will search for a variable matching the pointer you have provided.
</p>

<ol>
	<li>Arguments</li>
	<li>Local (function-local, UDFs and CFCs only)</li>
	<li>Thread local (inside threads only)</li>
	<li>Query (not a true scope; variables in query loops)</li>
	<li>Thread</li>
	<li>Variables</li>
	<li>CGI</li>
	<li>CFFile</li>
	<li>URL</li>
	<li>Form</li>
	<li>Cookie</li>
	<li>Client</li>
</ol>

<p>
	Note that some scopes are not searched in the precedence above.  Variables within these scopes must ALWAYS be requested in dot notation, prefaced by the scope name.
</p>

<ul>
	<li>
		This (public scope of a ColdFusion component)
	</li>
	<li>
		Request
	</li>
	<li>
		Application
	</li>
	<li>
		Session
	</li>
	<li>
		Server
	</li>
</ul>

<p>
	Even though ColdFusion defines scope precedence, there are a number of reasons to always provide a scope when requesting access to a variable such as readability and maintainability; we will explicitly discuss of these reasons.  The first is that variable names are not exclusive in ColdFusion.  We can store a value in multiple scopes with the same name, and which is especially prevalent across persistent scopes such as the application and session scopes, as well as when you are using reusable or third-party components and custom tags.  A common example would be if our program has a variable in the <span class="code">Variables</span> scope called <span class="code">userID</span> and we posted a form that contains a variable called <span class="code">userID</span>, which can result in a collision.  Based on ColdFusion scope precedence, if we referred to the variable <span class="code">userID</span> without explicitly specifying the scope, ColdFusion would return the data stored in <span class="code">variables.userID</span> instead of <span class="code">form.userID</span>.  This can cause problems if we were trying to use the latter data and makes your code hard to read and maintain.
</p>

<p>
	The second reason to scope variables is that there is a minor performance gain in providing the explicit scope because ColdFusion does not have to locate the variable across a number of scopes.  This performance increase has been essentially relegated to nil in the current versions of ColdFusion, but there is still a negligible improvement when scope is explicitly defined.
</p>

<p>
	There are also times when you might not want to scope variables.  One example is when you are not sure the source of the variable you will be accessing, such as when a variable could come from either the form or URL scopes.  This circumstance is rare and can introduce security risks, so you should generally attempt to find an alternative solution, such as implementing logic using <span class="code">cfparam</span>.
</p>