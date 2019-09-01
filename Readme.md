# Bubblefuck
> If hard things are hard why the easy ones cannot be hard as well?

*Maciej Bak*  
*Swiss Institute of Bioinformatics*

A simple implementation of the bubble sort algorithm in brainfuck langauge. I designed it a few years ago for [Women in Technology](https://womenintechnology.pl/) workshops where I was teaching about esoteric programming languages. I decided to put it out for educational/inspirational purpose :)

## Brainfuck
Brainfuck is one of the best known esoteric programming langauges.  
Excellent description is available at the wikipedia: https://en.wikipedia.org/wiki/Brainfuck  
Even a better one at the esolangs wiki: https://esolangs.org/wiki/Brainfuck

Interpreters:  
* Brainfuck Machine (Windows), the software on which I developed this code. I highly recommend it as it provides much help during the debugging.  
http://www.kacper.kwapisz.eu/index.php?i=19  
* Online tools:  
https://fatiherikli.github.io/brainfuck-visualizer  
https://www.jdoodle.com/execute-brainfuck-online/

The code has been tested successfully on all of the platforms listed above. I do not guarantee it's execution by other interpreters/compilers due to implementation constraints specific to each tool.

## The implementation
As in any brainfuck program all the data are stored in an array (and this is the only data structure available). There are several special purpose addresses reserved for particular operations:

![array.png](https://raw.githubusercontent.com/AngryMaciek/bubblefuck/master/array.png)

    [0] : counts the number of elements in the input array
    [1],[2] : temporary space used for comparing two elements
    [3],[4] : used for comparing two elements
    [5],[6] : pivot that separates the input from the first five cells
    [7] : temporary space required for each phase of the sorting
    [8]...[8+n-1] : the input array
    [8+n],[9+n] : temporary space used while reading input elements

A few notes about this implementation:
* this implementation is far from optimal,
* It works on all alphanumerical characters and some additional ones as well (basically 127>ASCII>32 since [delete] cannot be printed to the output),
* [space] i.e. ASCII=32 is reserved to mark the end of the input; the user is asked to provide a sequence of elements finished with the [space],
* in the worst case bubble sort requires n (number of elements) phases to sort an array; this information is utilized here to perform exactly n phases on any input therefore assuring the correct order of the elements at the end; in each phase two consecutive elements are compared and swapped, if necessary,

## Repository
This repository contains four files:

| File | Description |
| ------ | ------ |
| README.md | (this file) |
| array.png | Implementation scheme |
| bubblesort.b | Brainfuck source code for the bubble sort |
| LICENSE | The GNU General Public License v3.0 |

## License
GNU General Public License

