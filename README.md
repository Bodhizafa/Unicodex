#𝔗𝔥𝔢 𝔘𝔫𝔦𝔠𝔬𝔡𝔢𝔵
Build strings out of funny characters.
##Output
Click characters (or just type on the keyboard, enter works for newlines too) to add them to the string shown at the top. 
'Backspace' and 'Clear are exactly what they say on the tin.
'Prompt' will bring up a modal which allows you to copy/paste or replace the content. 
Note that if the string contains newlines, prompt will mangle them, and perhaps other characters. Behavior of strings in memory is a lot like the behavior of numbers on restaurant checks for large parties.
##Filter
There is always a current set of codepoints being displayed. 'Reset' sets this to the full set of codepoints in UnicodeData.txt, 
'Narrow' reduces the set to only things that were in the set before, and match the filter. 
'Widen' expands it to be things that were in the set before, plus those that match the filter from the full set.
Filters can happen based on aliases or properties. Searches are a basic substring match and are case-insensitive, but properties and aliases follow pretty strict conventions, so if you don't find what you're looking for, trying the Title_Case version or the ALL CAPS version
You can filter based on properties or based on aliases (the actual name is added to the alias list as well), so for exmple filtering on alias LATIN will bring up most (all?) of the variously modified latin characters.
##Font and Glyph Test
By default, your browser's full font fallback is used. If you type in a specific font or font-family, only that will be used, and remaining characters will be blank rather than falling back to whatever the OS wants. Running the glyph test will iterate over all possible codepoints, render them, and check to see if the resultant box has width. If it does, that character will get the 'Glyph' property, so once the glyph test has completed, you can filter by Property = Glyph and only get characters that you can see. Unfortunately, combining characters that have no width will cause false-negatives. (note this does not work if no font is selected, because it appears to be impossible to add AdobeBlank at the _end_ of the default font fallback list, so fonts with no characters will be rendered as boxes, which have width, and sort of defeats the purpose.)
##Skip/Start
'Next' and 'Prev' page through the current set of codepoints. 'Skip' is how far into the current set is being displayed, and 'Start' is the first codepoint being displayed. Both can be changed by entering a number and pressing enter.

##Motivation
Originally this was built as an auxiliary utility to a hobby project, but turned out to be fun in its own right. Besides that, I was interested in doing a real-world study of javascript performance, and wanted to try to write an app that dealt with a reasonable amount of data and had no dependencies whatsoever. In building it, I deliberately avoided optimizing it at all on the first pass a naive implementation would be. Turns out it's more than usable. Currently it only supports a smallish subset of the actual Unicode Character Database (AFAICT there's no real cohesive way to slurp it all at once into a usable data structure [https://xkcd.com/1726/](https://xkcd.com/1726/), so parsers are being added as I find bits that exist in different parts of it useful)

The Unicode people say I should include this with any copies of their database (which this includes). 

This applies to the directory UCD9 in this project:

Copyright © 1991-2016 Unicode, Inc. All rights reserved.
Distributed under the Terms of Use in http://www.unicode.org/copyright.html.

Permission is hereby granted, free of charge, to any person obtaining
a copy of the Unicode data files and any associated documentation
(the "Data Files") or Unicode software and any associated documentation
(the "Software") to deal in the Data Files or Software
without restriction, including without limitation the rights to use,
copy, modify, merge, publish, distribute, and/or sell copies of
the Data Files or Software, and to permit persons to whom the Data Files
or Software are furnished to do so, provided that either
(a) this copyright and permission notice appear with all copies
of the Data Files or Software, or
(b) this copyright and permission notice appear in associated
Documentation.

THE DATA FILES AND SOFTWARE ARE PROVIDED "AS IS", WITHOUT WARRANTY OF
ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE
WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT OF THIRD PARTY RIGHTS.
IN NO EVENT SHALL THE COPYRIGHT HOLDER OR HOLDERS INCLUDED IN THIS
NOTICE BE LIABLE FOR ANY CLAIM, OR ANY SPECIAL INDIRECT OR CONSEQUENTIAL
DAMAGES, OR ANY DAMAGES WHATSOEVER RESULTING FROM LOSS OF USE,
DATA OR PROFITS, WHETHER IN AN ACTION OF CONTRACT, NEGLIGENCE OR OTHER
TORTIOUS ACTION, ARISING OUT OF OR IN CONNECTION WITH THE USE OR
PERFORMANCE OF THE DATA FILES OR SOFTWARE.

