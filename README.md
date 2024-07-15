<h1>Rainbow Table Lab</h1>

<h2>Description</h2>
Experimenting with creating and using a rainbow table for hash algorithm cracking.
<br />

<h2>Utilities Used</h2>
<ul>
  <li><b>RainbowCrack Version 1.8 (http://project-rainbowcrack.com/)</b></li>
  <li><b>md5 Hash Generator (https://www.miraclesalad.com/webtools/md5.php)</b></li>
</ul>

<h2>Environments Used </h2>
<ul>
  <li><b>Windows 10</b></li>
</ul>

<h2>Program walk-through:</h2>
<ol>
  <li>
    I began by loading the RainbowCrack tool suite. Once navigating to the containing directory, the “rgen” command prints basic syntax and functionality for generating a table.
    <br />
    <img src="https://github.com/jonzilinsky/pictures/blob/main/rainbow1.png?raw=true" width="600px" alt="Step 1">
  </li>
 <br />
  <li>
    Initially I tried creating a SHA256 algorithm cracker, but it was very resource intensive due to the 32 byte chain size, therefore I moved to MD5 (16 bytes). I specified up to 8 character lengths of lower case alpha numeric text, as I originally wanted to crack a hash of the word “password”.
    <br />
    <img src="https://github.com/jonzilinsky/pictures/blob/main/rainbow2-1-edited.png?raw=true" width="600px" alt="Step 2">
  </li>
<br />
 <li>
    The execution spiked my CPU to 100% usage immediately which was fun to watch. I kept an eye on the core temperature which remained comfortably at around 67° C. The generation of the rainbow table took about an hour to finish. I sorted it using the built-in “rtsort” feature of RainbowCrack.
    <br />
    <img src="https://github.com/jonzilinsky/pictures/blob/main/rainbow-3-edited-1.png?raw=true" width="600px" alt="Step 3a">
    <br />
    <img src="https://github.com/jonzilinsky/pictures/blob/main/rainbow4-1-edited.png?raw=true" width="600px" alt="Step 3b">
  </li>
 <br />
  <li>
    Now it was time to test out the table. I used an online MD5 hash generator to create some hashes for testing.  
    <br /> 
   For example, the plaintext “pass1” generates the MD5 hash:
    a722c63db8ec8625af6cf71cb8c2d939
     <br /> 
    <br />
    <img src="https://github.com/jonzilinsky/pictures/blob/main/rainbow5-copy-1-edited.png?raw=true" width="600px" alt="Step 4">
  </li>
 <br />
  <li>
    I used the “rcrack” command on the directory containing the table, input the hash value “-h a722…” and was rewarded with the plaintext of “pass1”.
    <br />
    It was able to decipher any hash value that I threw at it for up to 5 characters of plain text.
     <br /> 
    <img src="https://github.com/jonzilinsky/pictures/blob/main/rainbow5-edited-1.png?raw=true" width="600px" alt="Step 5">
  </li>
<br />
  <li>
    The variance seemed too great from 6 to 8 characters, and the hash for “password” was not cracked. To remedy this I may try to use table_index values 1 through 6 to change the reduction function and generate a more complete set of tables. I could also increase the chain_len and chain_num using a more powerful machine.
     <br /> For now I am happy at this proof of concept and my experiment with creating a rainbow table.
    <br />
    <img src="https://github.com/jonzilinsky/pictures/blob/main/rainbow6.png?raw=true" width="600px" alt="Step 6">
  </li>
</ol>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
