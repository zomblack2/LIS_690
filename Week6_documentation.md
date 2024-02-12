# grep

Using scopus.bib file on virtual machine

## Basic Commands

1. grep "Irish Dance" scopus.bib
- looks specifically for any strings that match the string in quotations
2. grep -i "irish dance" scopus.bib
- ignores case with -i
3. grep -vi "irish dance" scopus.bib
- ignores case with -i and searches for anything that does not match the string with -v
4. grep -vi "^irish dance" scopus.bib
- ignores case with -i and searches for all lines that do not match "irish dance" at the beginning of the line because of the ^
5. grep -vi "irish$" scopus.bib
- ignores case with -i and searches for all lines that do not match "irish" at the end of the line because of the $
6. grep -vic "irish$" scopus.bib
- counts the number of matching lines excluding the header
7. grep -Ei "(dance|music)" scopus.bib
- searches for any string that matches dance or music (| is or and called an infix operator) 
8. grep -i "\<dance\>" scopus.bib or grep -wi "dance" scopus.bib
- searches for only whole words with \<word\> or -w

## Advanced Commands

1. grep -i "dance" -A2 scopus.bib
- prints the matching line plus the two lines after with -A2
2. grep -i "dance" -B2 scopus.bib
- prints the matching line plus the two lines before with -B2
3. grep -i -m1 "music" scopus.bib
- returns search for music and stops after the first hit
4. grep -in "music" scopus.bib
- returns the line numbers for each hit
5. grep -Eiw "[a-z]{3}" scopus.bib
- returns any three letter words that contain the characters a-z
6. grep -Eiw "d.{3}s" scopus.bib
- returns any words that start with d and end with s and have three letters in the middle due to the {3}
7. grep -Eio "^dance(A|B)[A-Z]*" scopus.bib | sort | uniq -c
- orders the sort output alphabetically, uniq deduplicates results, and -c counts the number of duplicates

## More Commands
cut - takes results of grep and removes the first column based on the comma as the column delimiter
sed - takes results and replaces sections 
awk - searches files to see if they contain lines that match with the specified patterns and then performs the associated actions
