---
layout: post
title:  "Introduction of OCaml to the University of Guadalajara, Mexico?"
date:   2015-06-02 18:52:37
categories: jekyll update
---
As a preliminary activity within the context of the [Dual Year of UK and Mexico 
2015](http://www.ukmexico.mx/en), I visited the [Centro Universitario de Ciencias 
Exactas e Ingenierías](http://www.cucei.udg.mx) of the [University of
Guadalajara](http://udg.mx/en), Mexico, last April.

I taught an Introductory Tutorial of OCaml (12 hrs). In addition to
OCaml particularities, I discussed with the atendees the differences
between functional and imperative languages. 

The following
code is an extract from a slide that I used to explain side effects
caused by global variables used in imperative languages like C. You 
can find the source of inspiration in
page 76 of this old but excellent text book on concurrency and
operating systems: 
<i>Concurrent Euclid, The Unix System and Tunis, R.C. Holt, Addison-Wesley
Publishing Company, 1983.</i> 

<pre>
        Example of a Side Effect Caused by Global Variables
#include &lt;stdio.h&gt;

int i=1; /* a global var */

int f(int x){ 
   i=2*i;       /* f changes the val of i from  i=1 to i=2 */
   return i*x;  /* f returns 20 when x= 10                 */
} 

main(){
int  j= i + f(10);  
printf("j= %d",j); /* what is the value of j? */
}

/*
  j= 21 if computed as j= i + f(10)= 1 + 20= 21 where the original val of i=1 is used.

 The compiler might optimize computation as j= f(10) + i, then
 j= 22 computed as j= f(10) + i= 20 + 2= 22 where the new val of i=2 from f is used.
 
The result is ambiguous, different compilers produce different results!
*/

</pre> 


Different C compilers will peoduce different results, for
instance, the [online GNU GCC v4.8.3 compiler](http://www.tutorialspoint.com/compile_c_online.php) 
outputs j=22.
 
[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help

<!-- Instead of using < and > to enclose HTML tags in the code snippet        -->
<!-- that you want to display, use &lt; and &gt;. For example, to             -->
<!-- display the <b>. . .</b> tags that you would use to get bold text, type: -->
<!--    &lt;b&gt; . . .&lt;/b&gt;                                             -->
