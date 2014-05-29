---
Description: ""
Keywords:
- Development
- VIM
- plugins
- vim
- Vim (text editor)
Section: post
Slug: vim-plugins-nerd-commenter
Tags:
- plugins
- vim
- Vim (text editor)
Thumbnail: /images/1013_Vim_gloss_128.png-200x200.png
Title: 'Vim Plugins: NERD Commenter'
Topics:
- Development
- VIM
Url: post/vim-plugins-nerd-commenter
date: 2009-11-09
disqus_identifier: 193 http://localhost/~sfrancia/wordpress/?p=193
disqus_title: 'Vim Plugins: NERD Commenter'
disqus_url: http://spf13.com/post/vim-plugins-nerd-commenter/
---

{{% img src="/media/vim_logo.png" class="third right" %}}

The NERD Commenter is an indispensable tool when programming in
[VIM](http://www.vim.org/ "Vim"). It understands like a
zillion different file types and properly comments each. It can handle
single line, multi line, partial line commenting as well as nesting. If
you’re programming in VIM you really should be using it.

It is simple enough to use. Most commands are mapped to ,c[character].
The command you are probably going to use the most is ,c\<space\> which
intelligently toggles a comment on or off.

You can find the plugin at [The NERD
Commenter](http://www.vim.org/scripts/script.php?script_id=1218).

Here are the instructions on usage, courtesy of the documentation file.
With some commentary and examples using php, courtesy of me.

Here is the default block of code we will be working with.

~~~~ {.brush: .php;}
// Change to the location of the folder containing the images
$image_folder = "images/days";

// You do not need to edit below this line
$today = date('l');

if (file_exists($image_folder."/".$today.".gif")) {
  echo "<img src="image_folder/".$today.".gif">";
}else {
  echo "No image was found for $today";
}
~~~~

### ,cc |NERDComComment|

Comments out the current line or text selected in visual mode.

~~~~ {.brush: .php;}
  //// Change to the location of the folder containing the images
  //$image_folder = "images/days";

  //// You do not need to edit below this line
  ///$today = date('l');
~~~~

### ,cn |NERDComNestedComment|

Same as |NERDComComment| but forces nesting.

~~~~ {.brush: .php;}
  //// Change to the location of the folder containing the images
  //$image_folder = "images/days";

  //// You do not need to edit below this line
  ///$today = date('l');
~~~~

### ,c\<space\> |NERDComToggleComment|

Toggles the comment state of the selected line(s). If the topmost
selected<br>
 line is commented, all selected lines are uncommented and vice versa.

~~~~ {.brush: .php;}
  Change to the location of the folder containing the images
  $image_folder = "images/days";

  You do not need to edit below this line
  $today = date('l');
~~~~

Running again on the second half

~~~~ {.brush: .php;}
  //if (file_exists($image_folder."/".$today.".gif")) {
      //echo "<img src="image_folder/".$today.".gif">";
  //} else {
      //echo "No image was found for $today";
  //}
~~~~

### ,cm |NERDComMinimalComment|

Comments the given lines using only one set of multipart delimiters if<br>
 possible.

~~~~ {.brush: .php;}
  /*// Change to the location of the folder containing the images
  $image_folder = "images/days";

  // You do not need to edit below this line
  $today = date('l');*/
~~~~

### ,ci |NERDComInvertComment|

Toggles the comment state of the selected line(s) individually. Each
selected<br>
 line that is commented is uncommented and vice versa.

~~~~ {.brush: .php;}
  Change to the location of the folder containing the images
  //$image_folder = "images/days";

  You do not need to edit below this line
  //$today = date('l');
~~~~

### ,cs |NERDComSexyComment|

Comments out the selected lines “sexily”

~~~~ {.brush: .php;}
  /*
   *if (file_exists($image_folder."/".$today.".gif")) {
   *    echo "<img src="image_folder/".$today.".gif">";
   *} else {
   *    echo "No image was found for $today";
   *}
   */
~~~~

### ,cy |NERDComYankComment|

Same as |NERDComComment| except that the commented line(s) are yanked<br>
 before commenting.

~~~~ {.brush: .php;}
  //// Change to the location of the folder containing the images
  //$image_folder = "images/days";

  //// You do not need to edit below this line
  //$today = date('l');
~~~~

### ,c\$ |NERDComEOLComment|

Comments the current line from the cursor to the end of line.

~~~~ {.brush: .php;}
  $today = /*date('l');*/
~~~~

### ,cA |NERDComAppendComment|

Adds comment delimiters to the end of line and goes into insert mode
between<br>
 them.

~~~~ {.brush: .php;}
  $today = date('l'); /* cursor here */
~~~~

### ,cI |NERDComPrependComment|

Adds comment delimiters to the start of line and goes into insert mode
between<br>
 them.

~~~~ {.brush: .php;}
  /* cursor here */$today = date('l');
~~~~

### ,ca |NERDComAltDelim|

Switches to the alternative set of delimiters.

Switches between // and /\* \*/ for example. Here’s ,cc after applying
this

~~~~ {.brush: .php;}
  /*// Change to the location of the folder containing the images*/
  /*$image_folder = "images/days";*/

  /*// You do not need to edit below this line*/
  /*$today = date('l');*/
~~~~

### ,cl OR ,cr OR ,cb |NERDComAlignedComment|

Same as |NERDComComment| except that the delimiters are aligned down
the<br>
 left side (,cl), the right side (,cr) or both sides<br>
 (,cb).

#### ,cl

~~~~ {.brush: .php;}
  /*if (file_exists($image_folder."/".$today.".gif")) {*/
  /*    echo "<img src="image_folder/".$today.".gif">";*/
  /*} else {*/
  /*    echo "No image was found for $today";*/
  /*}*/
~~~~

#### ,cr

~~~~ {.brush: .php;}
  /*if (file_exists($image_folder."/".$today.".gif")) {    */
      /*echo "<img src="image_folder/".$today.".gif">";*/
  /*} else {                                               */
      /*echo "No image was found for $today";              */
  /*}                                                      */
~~~~

#### ,cb

~~~~ {.brush: .php; .first-line:7;}
  /*if (file_exists($image_folder."/".$today.".gif")) {    */
  /*    echo "<img src="image_folder/".$today.".gif">";*/
  /*} else {                                               */
  /*    echo "No image was found for $today";              */
  /*}                                                      */
~~~~

### ,cu |NERDComUncommentLine|

Uncomments any commented lines in the block (only one level if nested)

~~~~ {.brush: .php;}
  Change to the location of the folder containing the images
  $image_folder = "images/days";

  You do not need to edit below this line
  $today = date('l');
~~~~

## Related articles

-   [Almir: Vim
    features](http://almirkaric.com/2009/07/10/vim-features/)
    (almirkaric.com)
-   [VIM video tutorial](http://www.linuxconfig.org/Vim_Tutorial)
    (linuxconfig.org)

