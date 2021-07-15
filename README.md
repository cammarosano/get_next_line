# get_next_line

Project proposed by [42](https://www.42.fr/).

Consists of a function that returns a line read from a file descriptor (without the '\n'). A very useful tool for the following projects of the common circle, whenever reading from a file or fro standard input.

### Function prototype:  
__int get_next_line(int fd, char **line)__

### Parameters:
- fd: file descriptor for reading
- line: address of char * pointer, that will contain the line read after the function call. *line* will point to a freeable string.

### Return values:
- 1: a line has been read.
- 0: EOF (end of file) has been reached.
- -1: An error has occurred (ex: invalid file descriptor, malloc error, char **line is the NULL pointer, etc)

Clarifying what's been much debated (subject as of december 2020):
- get_next_line returns 0 in the event of a line containing characters followed by EOF (_line_ points, therefore, to a freeable string containing those characters) 
- get_next_line returns 0 in the event of an empty line containing merely the EOF. And _line_ points to a freeable empty string.
- in case of error (return value -1), _line_ does not point to a freeable string.

### Bonus version:

get_next_line is able to manage multiple file descriptors. For example, if the file descriptors 3, 4 and 5 are accessible for reading, then you can call get_next_line once on 3, once on 4, once again on 3 then once on 5 etc. without losing the reading thread on each of the descriptors.