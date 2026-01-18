# Twinkle Twinkle Little Code :notes:
a method to visualize music scores in plain text
===

The *TTLC* language attempts to represent a music score in plain text. Similar to Turing&rsquo;s Machine, this &lsquo;Tuning Machine&rsquo; also lets you print symbols on a &ldquo;tape.&rdquo; Unlike Turing&rsquo;s Machine, though, this method cannot go backwards or return to a specific location. It can only go forward, __STEP__ by __STEP__. 

## How to Code: 
* Provide binary in sets: __PITCH__ and __NOTE__. 
    * `0111 0000` for  __PITCH G__ with a __WHOLE NOTE__
    * `1011 0011` for  __PITCH LOW C__ with an __EIGHTH NOTE__

* When you run *TTLC*, it will take a step forward, plot your note, and repeat until it is out of code.

## How to Simulate:
1. Draw a 16col x 11row grid in a digital document or on a piece of paper.
2. Label the x-axis &ldquo;__STEPS__&rdquo; and the y-axis &ldquo;__PITCH__&rdquo;.
3. Read the first set of words in the program.
4. Go to the first STEP (column 1) of your grid. 
5. Select the cell associated with the declared __PITCH__.
6. INSERT the symbol corresponding with the binary code in the __NOTE__ table.
7. Repeat this process by progressing through each set of words as the next steps. 
---
*I&rsquo;ve included my worksheet as it also includes additional useful labels.*
```
SCORE WORKSHEET - 16 col x 11 row (copy & paste into your favorite MONOSPACE DOCUMENT.)
/* BIN      01  02  03  04  05  06  07  08  09  10  11  12  13  14  15  16 < STEPS   */
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
> If you use the worksheet, you'll want to hightlight and replace the placeholder character to preserve the layout.
---
```
PITCH: Descending from High F (0000) to Low C (1010) 
0000 = High F (fa)    0100 = B (ti)     1000 = E (mi)         1100 = null
0001 = E (mi)         0101 = A (la)     1001 = D (re)         1101 = null
0010 = D (re)         0110 = G (so)     1010 = Low C (do)     1110 = null
0011 = C (do)         0111 = F (fa)     1011 = null           1111 = null
```
---
```
NOTE: This defines the duration of the STEP. Whole Notes are 4 beats.  
0000 = O  (whole)       0100 = d.. (sixteenth)        1000 = }} (eighth rest)
0001 = o  (half)        0101 = R   (whole rest)       1001 = null
0010 = d  (quarter)     0110 = r   (half rest)        1010 = null
0011 = d. (eighth)      0111 = }   (quarter rest)     1111 = null
```
> [!WARNING]
> Dr. Stewart noted a limitation of this language is that it cannot &ldquo;Fa flat.&rdquo;
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
/* BIN      01  02  03  04  05  06  07  08  09  10  11  12  13  14  15  16 < STEPS   */
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
(**) I added the Solfège[^1] *(do-re-mi)* along the bottom. Might add it as a feature later.

---
| FIRST CHALLENGE | SECOND CHALLENGE |
| --------------- | ---------------- |
| Name My Tune | Name Your Tune |
| I provide the program. | You provide the program. |
| I think you can name my tune in 5 notes: | Choose your tune:[^2] |
| ` 0010 0010  0001 0010  0011 0010  1011 0010  0111 0000 ` |  `#### ####` |
---

[^1]: [Solfège](https://www.key-notes.com/blog/solfege)
[^2]: [ABCNotation](https://abcnotation.com/search): An easy place to locate sheet music if you need inspiration. 
