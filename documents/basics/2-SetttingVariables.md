# Setting Variables.

Programming is all about doing stuff to things. Generally, the stuff is the execution of a process or algorithm and the things are information or data.

An algorithm is just a fancy name for a series of steps, like tying your shoelaces. Information or data is just values. Your name is a piece of information and so is your birth date. Since it's shorter, in this chapter we'll use the word data to describe a piece of information.

In Lucee, data is held in variables. Think of a variable like a mailbox. You can stuff things like letters and packages into a mailbox and get them out later to do stuff. Lucee makes storing information very easy because it's a loosely typed Language. That means you can stick any kind of data into a Lucee variable without having to tell Lucee what kind of data it is.

## A simple example to start with

Here's the simplest code to set a variable:

<:set thisIs="fun" />

Now, any time I refer to thisIs in my Lucee code, it'll hold the data "fun". You can look at the contents of a variable in Lucee by using the :dump tag.

<:dump var="#thisIs#" label="This is my first ever variable dump" />

or 

<:dump var=thisIs label="This is my first ever variable dump" />

See how the variable contains the string "fun"? But this :dump output actually even tells you that the content of your thisIs variable is a string. How does that fit in with what we said above about Lucee being loosely typed? Without wanting to go into too much detail, Lucee can figure out of which type the content of a variable is. That doesn't mean that your variable is forever limited to this type of content though.

A few other things to note. Examine the statement again:

<:set thisIs="fun" />

The part of the statement to the left of the equals sign (thisIs) is the variable name. The part of the statement to the right of the equals sign ("fun") is the value to assign to the variable.

Now, in the first version of the :dump statement, you’ll note we surrounded the variable name with pound # or hash symbols. The pound sign tells Lucee to evaluate the contents of whatever is in the tag's attribute. In the below example, the pound sign will tell Lucee to replace the thisIs string with the contents of the previously defined variable thisIs.

<:dump var="#thisIs#" label="This is my first ever variable dump" />

Here’s another way to look at pound sign use. Examine the below three statements. Can you guess what will happen in each case?

<:dump var="1 + 2" /><br />
<:dump var="#1 + 2#" /><br />
<:dump var="1 + 2 IS #1 + 2#" /><br />

In the first statement, our math problem is surrounded by the Double Quote character. This tells Lucee to treat the statement as a string and do no evaluations on it.

In the second statement, we also surrounded the math problem with the pound sign. Lucee executes the statement and performs our calculation for us.

In the third statement, notice we’ve mixed strings and evaluations through the correct use of the pound sign and the double quotes.

## The Left Side Of The Statement: <cfset thisIs

The left side of the statement is the variable name. You can have numbers as part of the variable name, but the variable name must start with a letter. You must not have any spaces in your variable names. If you need to use more words for your variable name, you can simply write the variable with CamelCase letters, or use Under_Scores to separate each word if you want. The choice is one of style; there are no right answers. Also, most special characters are not allowed in variable names. A good rule to follow is variable names should be descriptive and help provide context to what is being done.

For example, the word variable is a bad naming choice because the name adds no context to why the variable exists:

<:set variable = "12/26/1975" />

The variable name UserBirthdate is a good naming choice because it adds context to why the variable exists:

<:set UserBirthdate = "12/26/1975" />

Pro Tip: You'll understand the most about WHY your program is written a certain way as you are writing it. Take advantage of that hard-earned understanding and leave yourself (or others) as many clues and as much context as possible. Later on, after you've forgotten some of the details, it'll be much easier to piece together why the program was written a certain way and it'll be quicker to make good updates to your program.
The Right Side Of The Statement: "fun" />

The right side of the statement contains the value for the variable. Simple strings are enclosed in single or double quotes, with double quotes being the most common.

The right side of the statement is an execution zone. This means ColdFusion will attempt to evaluate items on the right side of the statement.

Examples

Here are a few examples that will help you understand setting ColdFusion variables:

Print Out the Current Date:

<cfset DateToday = now() />
<cfdump var = "#DateToday#" />
If you were to run the code example you would see how the ColdFusion function now(), which gets the servers current date and time, was evaluated and the contents placed in the variable DateToday? Anything not specifically in quotes (double or single) will be evaluated. It is possible to evaluate items in quotes, if you use the # sign. Keep this in mind as you develop ColdFusion. Novices have a tendency to overuse the pound sign.

Alternate Method: Print Out the Current Date:

This code will evaluate to the same thing in the previous step.

<cfset DateToday = "#now()#" />
<cfdump var = "#DateToday#" /> 
However, unless there are strings in the quotes, it's generally preferred to use the previous method.

To mix execution and strings, do this:

Mix Execution and Strings

<cfset DateToday = "Today is: #now()#" />
<cfdump var = "#DateToday#" /> 
Concatenation

You could also concatenate the strings using the & operator. This example is functionally equal to the previous example:

<cfset DateToday = "Today is: " & now() />
<cfdump var = "#DateToday#" /> 
So is this one:

<cfset DateToday = "Today is: " />
<cfset DateToday = DateToday & now() />
<cfdump var = "#DateToday#" /> 
See how we added DateToday to another evaluation and replaced the DateToday variable name with the new contents?

Outputting a Variable

You will often need to output the contents of the variables you create. One reason is to display the contents of a variable to the user, perhaps to display the username on a web page. Another reason is to verify the contents of a variable while you are in the process of writing or debugging your program.

About cfoutput

To display the contents of a variable to a user, use cfoutput. The variable reference must be a simple value that can be displayed as text. This includes Strings, Numbers, Dates, Times, and so on. Complex variables, such as Structs, Arrays, Queries, Functions, and so on, can not be displayed with the cfoutput command because they are not displayable as text.

Example of cfoutput Usage

<cfset DateToday = "Today is: #now()#" />
    
<cfoutput>#DateToday#</cfoutput>
The variable will be evaluated, and the variable contents will be added to the current end of the response buffer. i.e. it will be displayed to the user.

About cfdump

To inspect or verify the contents of a variable while writing or debugging your program, use cfdump. ColdFusion makes it very easy to see the contents of ANY variable by using the cfdump command. cfdump will convert the variable contents to a string representation and format it for easy viewing. The cfdump command can be used to help debug your program.

Example of cfdump Usage

<cfset DateToday = "Today is: #now()#" />
    
<cfdump var = "#DateToday#" />
    
<cfset DateArray = [dateFormat(now(), "short"), dateFormat(dateadd('d',1,now()), "short"), dateFormat(dateadd('d',2,now()), "short")] />
    
<cfdump var = "#DateArray#" />
    
<cfset DateStruct = { today=dateFormat(now(), "short"), tomorrow=dateFormat(dateadd('d',1,now()), "short"), later=dateFormat(dateadd('d',2,now()), "short") } />
    
<cfdump var = "#DateStruct#" />