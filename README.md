# NOX
> programming language for linear optimization problems.
![nox logo](https://imgur.com/fbVBC0k.png)

nox is a programming language, intended to deal with linear optimization problems.
for now, nox supports basic language features. and as nox grow we will implement features, specified for LP.

## Tasks
✅
⬜


## Build Nox

## Linux:

 ### install [bison](https://www.gnu.org/software/bison/) & [flex](https://github.com/westes/flex/) & [gcc](https://gcc.gnu.org/) .( you probaly have them installed 😉)
```sh
$ sudo apt-get install bison flex gcc
```
### clone this repository & build
```sh
$ git clone https://github.com/abdullahMosibah/NOX.git
$ cd NOX
$ bison -dv NoxBison.y
$ gcc -c NoxBison.tab.c
$ flex NoxLex.l
$ gcc -c lex.yy.c
$ gcc -o nox lex.yy.o NoxBison.tab.o -lm
```

## Usage example

lets try to wite Fibonacci Series in NOX

or more examples and usage, please refer to the [Wiki][wiki]._

## Development setup

Describe how to install all development dependencies and how to run an automated test-suite of some kind. Potentially do this for multiple platforms.

```sh
make install
npm test
```

## Release History

* 0.2.1
    * CHANGE: Update docs (module code remains unchanged)
* 0.2.0
    * CHANGE: Remove `setDefaultXYZ()`
    * ADD: Add `init()`
* 0.1.1
    * FIX: Crash when calling `baz()` (Thanks @GenerousContributorName!)
* 0.1.0
    * The first proper release
    * CHANGE: Rename `foo()` to `bar()`
* 0.0.1
    * Work in progress

## Meta

Your Name – [@YourTwitter](https://twitter.com/dbader_org) – YourEmail@example.com

Distributed under the XYZ license. See ``LICENSE`` for more information.

[https://github.com/yourname/github-link](https://github.com/dbader/)

## Contributing

1. Fork it (<https://github.com/yourname/yourproject/fork>)
2. Create your feature branch (`git checkout -b feature/fooBar`)
3. Commit your changes (`git commit -am 'Add some fooBar'`)
4. Push to the branch (`git push origin feature/fooBar`)
5. Create a new Pull Request

<!-- Markdown link & img dfn's -->
[npm-image]: https://img.shields.io/npm/v/datadog-metrics.svg?style=flat-square
[npm-url]: https://npmjs.org/package/datadog-metrics
[npm-downloads]: https://img.shields.io/npm/dm/datadog-metrics.svg?style=flat-square
[travis-image]: https://img.shields.io/travis/dbader/node-datadog-metrics/master.svg?style=flat-square
[travis-url]: https://travis-ci.org/dbader/node-datadog-metrics
[wiki]: https://github.com/yourname/yourproject/wiki






















------------------------------------
 NOX l
-------------------------------------
- nox is intended to be a lanugage for linear programming problems
	- but why ?, im trying to learn math for fun, and im intersted in compilers,
	  so i though it would be fun if could combine those to create AMPL-like language ( needs further editing)


steps:-
1. add variable declaration, flow control statements and basic language features.
2. learn about solvers and GLPK. 
3. learn about linear programming segments, and try to implement those in nox. 

B. add floating point, data type.
	- start implementing from flex. 
	
SCANNER ( generated by flex) 
--------------------------------------






STACK VIRTUAL MACHINE info
--------------------------------------
- the runtine system(virtual machine) is capable of executing the
code and a data area in which values assigned to variables are accessed
through an offset into the data area.
- the implemented virtual machine consists of	
	- data area ( the association between variables and values)
	- program area (manipulate the data area)

#machine orgnization:- 
	the *S-machine*  consists of two stores
	C > Program store( orgnized as an array Read-only) 
	S > Data Store(orgnized as a stack)
	
	registers:-
	IR > instructions register(contains the instruction which is being interpreted
	T > stack top register (contain the address of the top element of the stack )
	PC > program address register(contains the address of the next instruction of be fetched for interpretation) 
	AR > current activation record register(contains the base address of the activation record of the procedure which is being interpreted) 

	* each location of C is capalbe of holding an instruction
	* each location of S is capalble of holding an addressof an integer
	* each instruction consists of three fields
		- opreration code 
		- two parameters

instruction set :-
	the S-codes are the machine language of the S-machines.
	they occupy four bytes each.
	
	1st byte > operation code(op-code)	
	* there are 9 basics instruction each with diffrent op-code

	2nd byte > contains either 0 or 
					1- lexical level  offset
					2-condition code for the conditional jump offset
	
	last 2 bytes > taken as 16-bit integer form an oprand which is a literal value or 
		1- variable offset from a base in stack( what we currently using (?))
		2- S-code instruction locatoin
		3- operation number 
		4- special routine number 

* data access and storage instructions requires and offset within
the activation record 	

S-machine S-code instructions:-
	1. ADD - Addition
	2. SUB - Subtraction
	3. MULT- Multiplication
	4. DIV- Division
	5. PWR - Power 
	6. EQ - test equality 
	7. LT - test less that  
	8. GT - test greater than
	9. LD_INT - load literal value onto stack  (?) 
	10. LD_VAR - load value of variable at level offset (?)
	11. STORE - store value on top of stack into variable location a	t level offset (?)
	12. DATA - ADD NN to stack pointer (?) 
	13. GOTO - JUMP
	14. JMP_FALSE - JUMP if (?)
	15. READ_INT - read integer from user (?) 
	16. WRITE_INT - write integer as an output (?)
	17. HALT - end program (?) 

Memory;-
	saperated into two segments
	1. code segment ( code array ) 
	2. run-time data, expression stack (stack array)
	

