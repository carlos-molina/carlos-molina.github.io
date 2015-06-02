---
layout: page
title: GitHub 
permalink: /github/
---
This section discusses GitHub projects related to my research. 

<section>
<h1>mirage/mirage-decks</h1>
     <p>
      This project demonstrates the use of mirage as a selfhosting unikernel: in this
      demo, mirage is compiled with a set of slide presentation to produce a server of 
      slide presentations. It was developed by the OCaml Lab and the source code is avaliable
      from <a href="https://github.com/mirage/mirage-decks">mirage-decks</a>.
      <!-- from [https://github.com/mirage/mirage-decks](mirage-decks) NOK -->
      </p>

      <p>
      I needed to alter some of the
      slides which involved forking of the Git repository 
      <a href="https://github.com/carlos-molina/mirage-decks">(see)</a> and 
      recompilation of the sources. 

      Here is a summary of the compilation procedure that 
      I followed on my MacBook Air running OS X 10.9.5 and deployed with all the
      OCaml tools and libraries involved in this project. 
      </p>

   <ol>
      <li>  
        <pre>
         1) Let us say you have the source files in a local folder 
         
         bash-3.2$ pwd
         /Users/carlosmolina/local/git/mirage-decks

         2) The folder includes the following
         
         bash-3.2$ ls
         LICENSE         README.md       log             slides/
         Makefile        assets/         pdf/            src/

         3) Run make configure

         bash-3.2$ make configure

         mirage configure src/config.ml --unix
         Mirage      Using specified config file: src/config.ml
         Mirage      Compiling for target: Unix
         ...

         4) Change directory to src.

         sh-3.2$ pwd
         /Users/carlosmolina/local/git/mirage-decks/src

         bash-3.2$ ls -l
         total 120
         -rw-r--r--   1 carlosmolina  staff   1062  5 Feb 12:05 Makefile
         drwxr-xr-x  14 carlosmolina  staff    476  5 Feb 12:05 _build/
         -rw-r--r--   1 carlosmolina  staff   1747  4 Feb 20:14 config.ml
         -rw-r--r--   1 carlosmolina  staff   1098  4 Feb 20:14 deck.ml
         -rwxr-xr-x   1 carlosmolina  staff   1284  5 Feb 12:05 decks.xe*
         ...


         5) Run make build to produce the seflcontained unikernel. It is stored
         as 'mir-decks;.
 
         bash-3.2$ make build
         ocamlbuild -classic-display -use-ocamlfind -pkgs lwt.syntax,conduit.mirage, ...

         6) mir-decks can be executed as a unix process. It works as an http
         server that respondes to http://localhost         

         7) Execute the mir-decks under 'sudo' privileges.

         bash-3.2$ sudo mir-decks
         Password:              /* provide the root passwords of your computer */
         Manager: connect
         Manager: configuring
         Manager: socket config currently ignored (TODO) /* server is ready */
                         
         8) The "Manager: socket config currently ignored (TODO)" line
         indicates that the http server is running and ready to accept
         requests.
         Open your browser and point it to http://localhost
         You will see something like in the following figure.

         9) You can alter the source code and recompile again.

         </pre>
        <img src="/images/mirage-decks-output.png" atl="Mirage-decks first output screen."
                 align= "middle" style="width:604px;height:428px;"/>

      </li>
   </ol>

</section>




<!-- <img src="pic_mountain.jpg" alt="Mountain View" style="width:304px;height:228px;">  -->

<!-- Instead of using < and > to enclose HTML tags in the code snippet -->
<!-- that you want to display, use &lt; and &gt;. For example, to display -->
<!-- the <b>. . .</b> tags that you would use to get bold text, type:     -->
<!--    &lt;b&gt; . . .&lt;/b&gt; -->

