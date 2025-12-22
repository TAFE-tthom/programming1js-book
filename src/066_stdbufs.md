# Standard Input, Output and Error

**Work In Progress**

We get to discuss some topics from **chapter 2** within this section.

With other programming language like C#, you have used `Console.ReadLine` and `Console.WriteLine` or some variation to interact with input and output from a program.

In JS we need construct functions that can be used by JS event-loop system and retrieve data from buffers attached to the process.

## Standard IO

We have seen and heard the term Input and Output and to apply **Standard** before them is to imply that there is one way that all processes interact with the IO system.

Whenever we launch a program and it turns into a process, each process has access to 3 buffers.

* Input
* Output
* Error

Whenever you call `ReadLine` in C#, it is your process going to sleep until the IO system wakes it up to process the data present there. 



### Readling Lines

A typical pattern we can use is using the `await` keyword within a for loop along with an `of` operator that will use the `SymbolIterator` type associated with the object.

```ts
import readline from 'node:readline';
import { stdin } from 'node:process';

async function RunProgram() {
    const rl = readline.createInterface({input: stdin });
    for await(const line of rl) {
        console.log(line + '!');
    }c
    return;
}
RunProgram();

```


## Files

Files are a familiar IO construct and one we use to create these very slides and also write code in. Programs will interact with files by using them to save data or read them.

A file is a logical map to a range (or many ranges) of memory. We can have files mapped to the hard disk, mapped to ram or mapped over a network.


*How do we read a file with javascript?*


Remember the code from before? Lets now adapt it.

```ts
import readline from 'node:readline';
import fs from 'node:fs';

async function RunProgram() {
    const fstream = fs.createReadStream('some_file.txt');
    const rl = readline.createInterface({input: fstream });

    for await(const line of rl) {
        console.log(line + '!');
    }
    return;
}
RunProgram();

```


# Pipes and Sockets

We also have other files, more special in this case.

Within Unix and Unix-Derivative operating systems exist pipes. These are memory mapped files and act similarly as standard input and output for a program but that we can read and write to them from anywhere.

Unix Sockets operate similarly but provide the ability to have two-way communication. 
