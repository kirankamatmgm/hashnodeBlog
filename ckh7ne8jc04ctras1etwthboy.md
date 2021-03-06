## Regular Expression — A very important tool for data science

<span class="s"></span>

# Regular Expression — A very important tool for data science


June 05, 2020

![Image for post](https://miro.medium.com/max/40/0*pHXaujJmm7T45Eoe?q=20)

<noscript><img alt="Image for post" class="t u v hl aj" src="https://miro.medium.com/max/7680/0*pHXaujJmm7T45Eoe" width="3840" height="5760" srcSet="https://miro.medium.com/max/552/0*pHXaujJmm7T45Eoe 276w, https://miro.medium.com/max/1104/0*pHXaujJmm7T45Eoe 552w, https://miro.medium.com/max/1280/0*pHXaujJmm7T45Eoe 640w, https://miro.medium.com/max/1456/0*pHXaujJmm7T45Eoe 728w, https://miro.medium.com/max/1632/0*pHXaujJmm7T45Eoe 816w, https://miro.medium.com/max/1808/0*pHXaujJmm7T45Eoe 904w, https://miro.medium.com/max/1984/0*pHXaujJmm7T45Eoe 992w, https://miro.medium.com/max/2160/0*pHXaujJmm7T45Eoe 1080w, https://miro.medium.com/max/2700/0*pHXaujJmm7T45Eoe 1350w, https://miro.medium.com/max/3240/0*pHXaujJmm7T45Eoe 1620w, https://miro.medium.com/max/3780/0*pHXaujJmm7T45Eoe 1890w, https://miro.medium.com/max/4320/0*pHXaujJmm7T45Eoe 2160w, https://miro.medium.com/max/4800/0*pHXaujJmm7T45Eoe 2400w" sizes="100vw"/></noscript>

Photo by [Markus Spiske](https://unsplash.com/@markusspiske?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

Inspiration for writing this blog: fastai course( Jeremy says regular expression is an important tool to consider learning. After completing the first part of course, I felt like writing a blog on this, but forgot. I should have written this blog earlier, but remembered about this topic when I was going through fastai v2)

check [fastai v2](https://dev.fast.ai/)

Regular expression is a sequence of characters mainly used to find and replace patterns in a string or file.

Lets discuss problem that can be solved using regular expression. (example is from fastai course)

While solving Deep Learning problems, we have dataset and there may be times when label is stored in file name. So that we will have path and need to extract label from it. Or there may be situation you need to extract information from website. In these or similar situation, regular expression is important tool.

Lets get started with easy example first.

Think that you have document and you want to search names of all people with first name ‘Kiran’ (last name can be anything),
how to do it??
here regular expressions comes into play.

regular expression: ‘ **Kiran\s\w+\s’**

Here \s means a space and \w means character + means 1 or more characters.
This extracts all names with first name Kiran along with last name.

Lets see example where label is in file name path:

`data/oxford-iiit-pet/images/american_bulldog_146.jpg`

`data/oxford-iiit-pet/images/german_shorthaired_137.jpg`

american_bulldog is label of that image.
But how to extract it???

Writing regular expression is similar the way we approach the problem. seeing the example above we can tell that label is found after last forward slash(/) and after label we have number and path is ending with `.jpg` format

Regular expression is **/([^/]+)_\d+.jpg$**

I’ll explain step by step.

**$** means end of text we are interpreting

. **jpg** is make sure that just before end of text we have jpg that is of right format.

**\d** means numeric digits and + means many digits.

**_** is underscore appearing before numbers

**([^/]+)** is for looking a group of characters that do not contain forward slash, and [ ] means character we are interested. ‘**^**’ is negation.

**forward slash** at the beginning is to tell our search ends when we hit forward slash.

**/([^/]+)_\d+.jpg$** gives us label we want i.e `american_bulldog` in our example.

`python code`


```
import re string = 'data/oxford-iiit-pet/images/american_bulldog_146.jpg' 
pat = r'([^/]+)_\d+.jpg/span> 
pat = re.compile(pat) 
print(pat.search(string).group(1))</span> <span id="abd0" class="ed ih ii dg ie b ij in io ip iq ir il s im">>american_bulldog</span>
```


Important Regular expression cheat sheet:


```
^ Start of string 
$ End of string 
\b Word boundary 
* 0 or more 
+ 1 or more 
? 0 or 1 
\s White space 
\S Not white space 
\d Digit 
\D Not digit 
\w Word 
\W Not word 
\ Escape following character 
\n New line 
\t Tab 
. Any character except new line (\n) 
\[a-z] Lower case letter from a to z
\[A-Z] Upper case letter from A to Z
(a|b) a or b 
\[abc] Range (a or b or c) 
\[^abc] Not (a or b or c) 
\[0-7] Digit from 0 to 7</span>
```


I have explained regular expression with just two example but the purpose was to introduce you to regular expression and what it can do. This blog is written to introduce you to power of regular expressions. Regular expression if learnt how to use, can be important tool in your data science toolbox.

Thank you for reading the blog.

<span class="iv ej fm iw ix iy"></span><span class="iv ej fm iw ix iy"></span><span class="iv ej fm iw ix"></span>

_Originally published at_ [_https://kirankamath.netlify.app_](https://kirankamath.netlify.app/blog/regular-expression-a-very-important-tool/)_._