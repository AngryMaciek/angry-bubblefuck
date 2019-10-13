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
* in the worst case bubble sort requires n-1 (number of elements) phases to sort an array; this information is utilised here to perform exactly n-1 phases on any input therefore assuring the correct order of the elements at the end; in each phase two consecutive elements are compared and swapped, if necessary,

Overall description of the algorithm:

    1. (read input)
       start with i=8
       read a character from the input to [i]
       increment [0]
       copy from [i] to [i+1] with the usage of [i+2]
       test if [i+1] is [space] (ASCII==32)
         NO:
           i=i+1 and read the next character
         YES:
           reset [i]
           decrement [0]
       increment [6] (set pivot)
       decrement [0]
    2. (perform n-1 sorting phases)
       test if [0]==0
         NO:
           2A. (start a single sorting phase)
               decrement [0]
               i=9
               until [i]==0:
                 copy [i-1] to [1] and [3]
                 copy [i] to [2] and [4]
                 copy [1] back to [i-1]
                 copy [2] back to [i]
                 increment [1]
                 2A1. (compare two elements and swap if [i-1]>[i])
                      until ([3]==0 OR [4]==0):
                        decrement [3], decrement [4]
                      case [4]==0:
                        copy [i-1] to [i-2]
                        copy [i] to [i-1]
                        copy [i-2] to [i]
                 2A2. (clear markers for the next comparison)
                      decrement [1]
                      reset [3], reset [4]
                      copy [i-1] to [i-2]
                      i=i+1
               k=3
               until i-k==5:
                 copy [i-k] to [i-k+1]
                 k=k+1
               decrement [7], increment [6]
         YES:
           2B. (print the sorted array)
               i=8
               move to [i]
               until [i]==0:
                 print [i], i=i+1, move to [i]

## Repository
This repository contains four files:

| File | Description |
| ------ | ------ |
| README.md | (this file) |
| array.png | Implementation scheme |
| bubblesort.b | Brainfuck source code for the bubble sort |
| LICENSE | The GNU General Public License v3.0 |

## License
GNU General Public License v3.0

