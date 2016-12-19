- normal characters match themselves
- `.` matches anything (except newlines)
- brackets create groups:
  - `[abcd]` matches ‘a’ or ‘b’ or ‘c’ or ‘d.
  - can also be written `[a-d]`.
- Some are really common, so they have shortcuts:
  - `[a-zA-Z0-9_]` matches alphanumerics and _ (the chars allowed in python variables). it can be written `\w`.
  - `[0-9]` can be written `\d`


1. Write a regex that matches any year in the 2000s. It should match 2000, 2001, 2182, but not 1999 or 123 or 18222. Test with
`echo '2000 2001 2182 1999 123 18222' | tr ' ' '\n' | grep '(your regex here)'`

Aside: shell commands and pipes are incredibly useful. This one says:
```
echo '2000 2001 2182 1999 123 18222' | # Prepare input for the next command
tr ' ' '\n' | # translate spaces into newlines
grep '(regex)' # filter the lines, requiring that they match the regex
```
There's a great story about shell scripts at http://www.leancrew.com/all-this/2011/12/more-shell-less-egg/

2. Write a regex to match any iso8601-formatted dates that occur during November of any year. (Those look like ‘2012-08-13’, ‘2016-09-08’, ‘YYYY-MM-DD’.) Test with `echo '2014-01-12 2016-11-01 2010-03-11 2011-12-11 2003-11-18' | tr ' ' '\n' | grep '(your regex here)'`


The special characters `^` and `$` represent the start and end of a word.


3. Write a regex that matches ‘pear’ or ‘peer’, but no other words. Test with `echo pear peer pare spaghetti pearls peerless | tr ' ' '\n' | grep '(your regex here)'`

4. Write a regex to match any line, as long as it ends with a period. It shouldn't count lines that merely *include* a period. Test with `curl https://raw.githubusercontent.com/bgschiller/regex-tutorial/master/sentences | grep '(your regex here)'`

Crossword puzzle helper! Use  https://raw.githubusercontent.com/bgschiller/regex-tutorial/master//words for your words list, or /usr/share/dict/words if you're on mac or linux.

5. `ad_r_` to decorate
6. `_l_c__` calm, unexcitable
7. `n__ir` Towards earth, for the ISS

To repeat a pattern, you can use curly braces with the number of times you want it:

- `abc{3}` will match 'abccc', but not 'abc' or 'abcc'
- `\w{4,}` will match four or more letters in `\w`.
- `co{2,}l` will match 'cool', 'coooool', or  'cooooooooooooooool', but not 'col'

Note: I found that I needed to use `grep`s `-E` flag in order for the repeat-pattern regexes to work. This looks like `< words grep -E 'abc{3}`

8. Find a word with three dotted letters in a row. Credit to The Simpsons for the [inspiration for this problem](bartofwar10.mp3).
9. Make a list of words composed only of vowels (consider 'y' to be a vowel for this problem).

To negate a set, use ^. so [^a-d] will match anything *but* a,b,c,d.

10. Find a word with five consonants in a row.
