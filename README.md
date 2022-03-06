# Regex
Matching a Hex Value with Regex
Intro - Regular expressions (regex) are a series of characters that define a search pattern. Example: /^[a-z0-9_-]{3,16}$/ is the regex for matching a username with 4 parameters. The string can contain lowercase letters a-z, numbers 0-9, _ or -, and must be between 3 and 16 characters long. But how exactly are these parameters being set? We will discuss that as well as matching a hex value below!

Summary
For this section we will be focusing on matching a hex value. Our sample code is: /^#?([a-f0-9]{6}|[a-f0-9]{3})$/ Below I will Identify and define all of the regex components being used in this expression. As well as explain how they are being used in this specific expression.

Table of Contents
Anchors
Quantifiers
Grouping Constructs
Bracket Expressions
The OR Operator
Regex Components
Anchors -
are represented by the characters ^ and $. The ^ anchor signifies a string that begins with the characters that follow it. This can be represented in two formats: 1st) An exact string match, such as ^The, where the strings "The" or "The person" match, but "the" and "the person" do not. This is because a regex is case-sensitive. 2nd) A range of possible matches, displayed using bracket expressions. While the $ anchor signifies a string that ends with the characters that preceded it. Just as with the ^ character, it can be preceded by an exact string or a range of possible matches. Example: /^[a-z0-9_-]{3,16}$/ In this example ^ signifies the begining of the range of matches between the square brackets. While the $ signifies the end of the quantifier between the curly brackets. How it is used in our matching a hex value regex: /^#?([a-f0-9]{6}|[a-f0-9]{3})$/ The ^ character symbolizes the begining of the string, while the $ symbolizes the end of the string.

Quantifiers -
set the limits of the string that your regex matches (or an individual section of the string). Often include an min and max number of characters. The character * matches the pattern zero or more times, + one or more times, ? zero or one time. Curly brackets allow for three different ways to set limits. 1st) { n } matches the pattern n times. 2nd) { n, } matches n or more times. 3rd) { n, x } matches a min of n times and a max of x times. How it is used in our matching a hex value regex: /^#?([a-f0-9]{6}|[a-f0-9]{3})$/ There are two sets of curly brackets in this expression, the first {6} symbolizes that the first subexpression will need to match the pattern 6 times(a.k.a 6 char). The second {3} symbolizes that the second subexpression will need to match the pattern 3 times(a.k.a 3 char). Also there is a ? near the begining of the first subexpression. This character means that the match will be made either zero or one times.

Grouping Constructs -
are used to break up sections of an expression by using parentheses ( ). Each divided section is now known as a subexpression (abc):(xyz). IMPORTANT!!! Grouping constructs have two primary categories: capturing and non-capturing. Understand that capturing groups capture the matched character sequences for possible re-use (including a numbered backreference) while non-capturing groups do not. A grouping construct can be made non-capturing by adding the characters ?: at the beginning of an expression inside the parentheses. How it is used in our matching a hex value regex: /^#?([a-f0-9]{6}|[a-f0-9]{3})$/ This expression is broken up into two subexpressions demonstrated by the two sets of square brackets [].

Bracket Expressions -
(a.k.a positive character groups) are anything inside a set of square brackets []. Example, [abc] will look for a string that includes a or b or c, regardless of the length of the string. How it is used in our matching a hex value regex: /^#?([a-f0-9]{6}|[a-f0-9]{3})$/ Each of the two subexpressions state that the matches will need to be any of the letters from a-f, and any numbers 0-9.

The OR Operator -
allows for the expression to not have to meet all of the requirements. Example: the expression (abc):(xyz) only matches its exact copy of (abc):(xyz). Any variation of this would not match. Now apply the OR operator to the expression, (a|b|c):(x|y|z), any combo of abc and xyz will match. For instance: cab:yzx will work as a match, as well as just a:z. How it is used in our matching a hex value regex: /^#?([a-f0-9]{6}|[a-f0-9]{3})$/ The | character in this case, splits the expression meaning that the left side of the expression is looking for a match as well as the right side.
