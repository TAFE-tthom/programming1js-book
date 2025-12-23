# Standard Input, Output and Error

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


### Reading Lines

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

We can adapt the code where we read from stdin to also be applicable for files. As a generalisation, buffers and files share the same interface with nodejs.

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

### Writing to files

Writing to a file within JS, specifically NodeJS isn't as complicated as reading lines. We will need to create a `WriteStream` which will allow for data to be buffered and eventually flushed.

#### Truncating and Writing

There are two modes to writing to a file. There is truncate and write, this will eliminate the existing data in the file and make it open to writes from the beginning of the file.

```js
import fs from 'node:fs';

async function RunProgram() {
    const fstream = fs.createWriteStream('some_file.txt'. { flags: 'w' });

    fstream.write("Writing a line to a file\n");

    //By closing it, it will 
    fstream.end();
    
    return;
}
RunProgram();
    
```

#### Appending and Writing

The other mode is appending to the end of the file. This is a matter of specifying the mode as `'a'` when opening the stream.


```js
import fs from 'node:fs';

async function RunProgram() {
    const fstream = fs.createWriteStream('some_file.txt'. { flags: 'a' });

    fstream.write("Writing a line to the end of the file\n");

    //By closing it, it will 
    fstream.end();
    
    return;
}
RunProgram();
    
```

# Pipes and Sockets

We also have other files, more special in this case.

Within Unix and Unix-Derivative operating systems exist pipes. These are memory mapped files and act similarly as standard input and output for a program but that we can read and write to them from anywhere.

Unix Sockets operate similarly but provide the ability to have two-way communication. 
