# jabberywocky-go
x86 compiler written in Go

# Jabberwocky
## A Go lang to x86 compiler that supports a limited set of instructions.
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/d/d0/Jabberwocky.jpg/800px-Jabberwocky.jpg" width="625" height="938" />

Documenting the struggle of a pretty meh programmer learning Go

References, and major notes found here

Issues page will act as TO DO list and bug tracker


### Texbook from Jay's class website
https://jeapostrophe.github.io/courses/2017/spring/406/notes/book.pdf
### another version of the book with working citations
https://www.sharelatex.com/project/5637a774990f556d48bab667

### Paper book is based on 
http://scheme2006.cs.uchicago.edu/11-ghuloum.pdf





# Basics

#### Steps
[R1] Uniquify -> Flatten [C0] -> Select [x86*] -> Assign -> Fix[x86]

<dl>
  <dt>Uniquify</dt>
  <dd>Remove variable shadowing</dd>
  <dt>Flatten</dt>
  <dd>Remove nested expressions</dd>
  <dt>Select</dt>
  <dd>Generate x86 instructions</dd>
  <dt>Assign</dt>
  <dd>Map variables to stack locations</dd>
  <dt>Fix</dt>
  <dd>Two offsets one instruction</dd>
</dl>



## Intermediary Languages 

### 	R1

<dl>
  <dt>exp 	::==</dt>
  <dd>	int | (read) | (- exp) | (+ exp exp) | var | (let ([var exp]) exp)</dd>
  <dt>R1 	::==</dt>
  <dd>	(program exp)</dd>
</dl>


### 	C0

<dl>
  <dt>arg 	::==</dt>
  <dd>	int |  var </dd>
  <dt>exp 	::==</dt>
  <dd>	arg | (read) | (- arg) | (+ arg arg)</dd>
  <dt>stmt 	::==</dt>
  <dd>	(assign var exp) | (return arg)</dd>
  <dt>C0 	::==</dt>
  <dd>	(program (var*) stmt+)</dd>
</dl>


### 	x86* and x86

<dl>
  ```
  <dt>x86*, arg	::==</dt>
  <dd>		int | var | reg </dd>
  <dt>x86, arg 	::==</dt>
  <dd>		int | reg | (reg, offset) </dd>
  ```
</dl>

#### x86, instr
```
> (popq arg)
> (pushq arg)
> (subq arg arg)
> (addq arg arg)
> (movq arg arg)
> (callq label)
> (negq arg)
> (retq arg)
```

