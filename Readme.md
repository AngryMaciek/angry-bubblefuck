# Bubblefuck
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

