If you are already familiar with the standard files and directories manipulation, here are some more advanced Unix tools.
You can find the Unix guide on the wiki: https://wiki.flatironinstitute.org/Public/UnixIntroduction

In the following, lines that you should put in your prompts start with the $ sign (aka you can copy-paste what comes after)

# Text manipulation
Inside data/input, you will find a file named animals.txt It is used as the input file for the following examples:

## grep
grep <pattern> is a command that shows you the lines that match a pattern in a file or a string. This pattern can be a full-fledged regular expression.
### Try the following:
$ grep cat animals.txt
$ grep -i cat animals.txt

### And some more advanced functionality:
When dealing with large files, using grep -n will show you the line numbers that have matched the search pattern.
It is often useful to know the context around the line you are looking for, in this case you can use the -C<N> flag, which will show N lines per match (including the lines leading to the matching line, and the ones after).
On the other hand, sometimes you do not want certain lines (eg: in log files) in this case use grep -v <pattern_to_reject>
Finally, you can use regular expressions using grep -E <regular_expression>

## sed
The sed command is used to edit a text quickly, especially to replace one string with another, using the syntax:
sed 's/<string1>/<string2>/' <filename>
# Try:
$ sed 's/cat/bear/' animals.txt

## tr
The tr command is used to delete or replace characters.
$ echo "tata" | tr a o

# Exercise: awk + wget
## awk
When data is stored in a formatted text file, awk is used to parse and output it. By default, it assumes that the data is organized by rows and columns, where rows are lines, and columns are separated with spaces or tabs (this is configurable). In this case, if for instance we want to print the first and third columns of each row, we can use:
awk '{print $1 $3}' <filename>
Each column is identified by $<N> where N refers to the Nth column. $0 is the complete line.

## wget
wget <url> is used to download files from the internet, to the current directory. This works for both HTTP and FTP.

## The exercise
In data/in/input you will find a file called download_metadata.csv
It is a comma-separated value, where each line contains a URL, a file name, a folder.

GOAL: use awk to parse it, then generate wget lines that will download the different files into their proper locations, under the proper name.

TIP: use man awk (and Google!) to know what FS does! Likewise, wget -O might be useful...

A solution will be posted in the #sciware Slack channel on Friday June 2nd!
