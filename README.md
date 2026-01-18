<p align="center">IMGD 5010 &bull; Assignment 1 &bull; Build Your Own Binary &bull; Todd Stewart</p>

# Twinkle Twinkle Little Code :notes:
a method to visualize music scores in plain text
===

The *TTLC* language attempts to represent a music score in plain text. Similar to Turing&rsquo;s Machine, this &lsquo;Tuning Machine&rsquo; also lets you print symbols on a &ldquo;tape.&rdquo; Unlike Turing&rsquo;s Machine, though, this method cannot go backwards or return to a specific location. It can only go forward, __STEP__ by __STEP__. 

## How to Code: 
* You provide the __PITCH__ and __NOTE__ in the form of two 4-bit binary words. *Such as...*
    * `0111 0000` for  __PITCH G__ with a __WHOLE NOTE__
    * `1011 0011` for  __PITCH LOW C__ with an __EIGHTH NOTE__
* When your program runs, *TTLC* will look at the first set of words and plot their respective *pitch* and *note* in *step one*.
* After plotting the first note, *TTLC* advances to the next set of words -and- the next step along the music score (grid).
* *TTLC* will continue to *step* through each set of binaries until there are no more sets to process.

## How to Simulate: 
1. Draw a 16col x 11row grid in a digital document or on a piece of paper.<br>&nbsp; *- Don&rsquo;t despair. I included my worksheet below. -*
2. Label the x-axis &ldquo;__STEPS__&rdquo; and the y-axis &ldquo;__PITCH__&rdquo;.
3. Read the first set of words in the program.
4. Go to the first STEP (column 1) of your grid. 
5. Select the cell associated with the declared __PITCH__.
6. INSERT the symbol corresponding with the binary code in the __NOTE__ table.
7. Repeat this process by progressing through each set of words as the next steps. 
---
```
SCORE WORKSHEET - 16 col x 11 row (copy & paste into your favorite MONOSPACE DOCUMENT.)
/* code     01  02  03  04  05  06  07  08  09  10  11  12  13  14  15  16 < STEPS    */
/* 0000 */ --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- ---  /* F / fa */
/* 0001 */                                                                  /* E / mi */
/* 0010 */ --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- ---  /* D / re */
/* 0011 */                                                                  /* C / do */
/* 0100 */ --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- ---  /* B / ti */
/* 0101 */                                                                  /* A / la */
/* 0111 */ --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- ---  /* G / so */
/* 1000 */                                                                  /* F / fa */ 
/* 1001 */ --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- ---  /* E / mi */
/* 1010 */                                                                  /* D / re */
/* 1011 */                                                                  /* C / do */
```
> [!IMPORTANT]
> If you use the worksheet, you'll want to highlight and replace the placeholder character with the note symbol to preserve the layout.
---
```
TO DECLARE PITCH:  /* Descending from High F (0000) to Low C (1010) */
0000 = High F (fa)    0100 = B (ti)     1000 = E (mi)         1100 = null
0001 = E (mi)         0101 = A (la)     1001 = D (re)         1101 = null
0010 = D (re)         0110 = G (so)     1010 = Low C (do)     1110 = null
0011 = C (do)         0111 = F (fa)     1011 = null           1111 = null
```
---
```
TO DECLARE NOTE:  /* The duration of the STEP. Whole Notes are 4 beats, half notes are 2 beats, etc. */
0000 = O  (whole)       0100 = d.. (sixteenth)        1000 = }} (eighth rest)
0001 = o  (half)        0101 = R   (whole rest)       1001 = null
0010 = d  (quarter)     0110 = r   (half rest)        1010 = null
0011 = d. (eighth)      0111 = }   (quarter rest)     1111 = null
```
---

### Example 
4 Bars of Twinkle Twinkle Little Star
---
```
Program: 
  1011 0010  1011 0010  0111 0010  0111 0010  0101 0010  0101 0010  0111 0001  1000 0010
  1000 0010  1001 0010  1001 0010  1010 0010  1010 0010  1011 0001  0010 0000  0001 0000
```
```
Result:
/* code     01  02  03  04  05  06  07  08  09  10  11  12  13  14  15  16 < STEPS   */
/* 0000 */ --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- /* F / fa */
/* 0001 */                                                             d.. /* E / mi */
/* 0010 */ --- --- --- --- --- --- --- --- --- --- --- --- --- --- d.. --- /* D / re */
/* 0011 */                                                                 /* C / do */
/* 0100 */ --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- /* B / ti */
/* 0101 */                  d   d                                          /* A / la */
/* 0111 */ --- --- -d- -d- --- --- -o- --- --- --- --- --- --- --- --- --- /* G / so */
/* 1000 */                              d   d                              /* F / fa */ 
/* 1001 */ --- --- --- --- --- --- --- --- --- -d- -d- --- --- --- --- --- /* E / mi */
/* 1010 */                                              d   d              /* D / re */
/* 1011 */  d   d                                               o          /* C / do */
           do  do  so  so  la  la  so  fa  fa  mi  mi  re  re  do  re  mi (*) (**)
```
(*) The last two steps are throwing an error. I have some debugging to do.  
(**) I added the Solfège[^1] *(do-re-mi)* along the bottom.<br>&nbsp;&nbsp;&nbsp;&nbsp; *It's not technically part of the language but you can still add it as you advance through the steps.* 

---
YOUR CHALLENGE
===
| FIRST CHALLENGE | SECOND CHALLENGE |
| --------------- | ---------------- |
| Name My Tune | Name Your Tune |
| Instructions:<br>I provide the program. | Instructions:<br>You provide the program. |
| My tune: (5 notes) | Your tune:  |
| ` 0010 0010  0001 0010  0011 0010  1011 0010  0111 0000 ` |  ` ???? ????                                           ` |
| Answer: `                                 ` | *Try [ABCNotation](https://abcnotation.com/search) for ideas.* |
---

[^1]: [Solfège](https://www.key-notes.com/blog/solfege)
