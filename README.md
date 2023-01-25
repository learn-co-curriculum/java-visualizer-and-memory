# Java Visualizer and Memory

## Learning Goals

- Discuss what memory is and introduce the stack.
- Show memory in terms of storing variables using the Java Visualizer.

## Introduction

In Java, objects live in **memory**. When we start the JVM, some memory from the
operating system (OS) will be allocated to the JVM. Once the memory is allocated,
we can use that memory to run our Java program. Memory is an important concept
because it helps us create new objects and remove them.

When talking about memory in programming languages, we will often talk about the
**stack** and the **heap**. In this lesson, we will focus solely on the stack,
or sometimes referred to as the call stack.

## The Stack

The **stack** is an area of memory that stores variables during runtime. Let's
look at what this looks like using the Java Visualizer plugin that we installed
earlier. We can also use the browser version of the Java Visualizer. In this
lesson, we will walk you through using both to get you used to using the plugin
and to seeing the browser view.

### Using the Java Visualizer

Fork and clone this repository. In it, you should see a program that looks like
this:

```java
package org.example;

public class Main {
    public static void main(String[] args) {
        int x = 1;
        int y = 2;
        int z = 3;
    }
}
```

Comprehension check! What do we think this program would output if we were to
run it?

<details>
    <summary>Comprehension check! What do we think this program would output if we were to run it?</summary>

  <p>Answer: Nothing! This program does not contain a <code>System.out.println()</code> statement.</p>

</details>

To utilize the Java Visualizer Program we need to run this program in debug.
When we run the debugger, it will run just like it would if we were to run the
program with the run command. The only exception is we can tell the debugger to
stop on specific lines of code and pause the execution of the program. The lines
it stops on are lines that we define. These are called **breakpoints** and can
be specified anywhere in the source code.

When a debugger comes across a breakpoint, it will stop and give you control
over the execution of the subsequent lines of code.

Let's set a breakpoint in our program on line 5. We can do this by clicking in
the open space to the right of the line number in the editor window - a red dot
will appear to indicate that you successfully set a breakpoint on that line:

![set-breakpoint](https://curriculum-content.s3.amazonaws.com/java-mod-1/java-visualizer-and-memory/set-breakpoint.png)

Now that we have set a breakpoint, let's run this program in debug mode. To do
so, click the little green bug next to the run button in the upper right of the
IntelliJ window:

![debug-button](https://curriculum-content.s3.amazonaws.com/java-mod-1/java-visualizer-and-memory/debug-button.png)

The program will begin executing but then stop on line 5, where we set the
breakpoint. Below, a **debug console** will appear. This will allow us to
control what happens when we set a breakpoint. In the debug console, click the
"Java Visualizer" to show that instead of the console:

![java-visualizer-debug window](https://curriculum-content.s3.amazonaws.com/java-mod-1/java-visualizer-and-memory/java-visualizer-debug-window.png)

The other buttons to the right of the Java Visualizer tab that re highlighted in
the screenshot above show how to proceed with the execution of the program. We
will highlight each of those buttons in a later lesson. For now, click the
step over
(![step-over](https://curriculum-content.s3.amazonaws.com/java-mod-3/debugger/step-over.png))
button.

When we click the step over button, notice what happens in the Java Visualizer
window:

![call-stack-x](https://curriculum-content.s3.amazonaws.com/java-mod-1/java-visualizer-and-memory/call-stack-x.png)

The execution of the program has moved onto line 6, but our stack now has the
`x` variable along with the value we initialized it to, `1`. This is showing how
the variables are being stored by Java! If we click the step over button again,
we should see that the variable `y` and its value, `2`, is now also stored on
the stack.

![call-stack-xy](https://curriculum-content.s3.amazonaws.com/java-mod-1/java-visualizer-and-memory/call-stack-xy.png)

If we click the step over button one more time, we will see all three of our
variables, `x`, `y`, and `z` stored on the stack inside of memory.

![call-stack-xyz](https://curriculum-content.s3.amazonaws.com/java-mod-1/java-visualizer-and-memory/call-stack-xyz.png)

### Using the Brower Java Visualizer

We could also copy and paste this code into the Java Visualizer. The browser
based Java Visualizer can be found here:

[Java Visualizer for Variables and Call Stack Lesson](https://pythontutor.com/visualize.html#code=public%20class%20Main%20%7B%0A%20%20%20%20public%20static%20void%20main%28String%5B%5D%20args%29%20%7B%0A%20%20%20%20%20%20%20%20int%20x%20%3D%201%3B%0A%20%20%20%20%20%20%20%20int%20y%20%3D%202%3B%0A%20%20%20%20%20%20%20%20int%20z%20%3D%203%3B%0A%20%20%20%20%7D%0A%7D&cumulative=false&curInstr=1&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=java&rawInputLstJSON=%5B%5D&textReferences=false)

For convenience, we have also embedded the Java Visualizer you would see on a
browser here:

<iframe width="800" height="500" frameborder="0" src="https://pythontutor.com/iframe-embed.html#code=public%20class%20Main%20%7B%0A%20%20%20%20public%20static%20void%20main%28String%5B%5D%20args%29%20%7B%0A%20%20%20%20%20%20%20%20int%20x%20%3D%201%3B%0A%20%20%20%20%20%20%20%20int%20y%20%3D%202%3B%0A%20%20%20%20%20%20%20%20int%20z%20%3D%203%3B%0A%20%20%20%20%7D%0A%7D&codeDivHeight=400&codeDivWidth=350&cumulative=false&curInstr=1&heapPrimitives=nevernest&origin=opt-frontend.js&py=java&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe>

Click "Next" as you would with the step over button in IntelliJ to watch the
variables be stored on the stack inside of memory.

## Re-assigning Variables

Now that we know how to use the Java Visualizer tool, modify the code in the
`Main` class to the following:

```java
package org.example;

public class Main {
    public static void main(String[] args) {
        int x = 1;
        int y = 2;
        int z = 3;
        
        x = y;
        z = 4;
    }
}
```

Let's put a breakpoint on line 9 and run the program in the debugger to see
what happens with memory when we re-assign the variables `x` and `z`:

![call-stack-xyz](https://curriculum-content.s3.amazonaws.com/java-mod-1/java-visualizer-and-memory/call-stack-xyz-again.png)

If we click the step over button, it will move the execution to the next line.
If you'd rather use the browser Java Visualizer, feel free to click on this link
[here](https://pythontutor.com/visualize.html#code=public%20class%20Main%20%7B%0A%20%20%20%20public%20static%20void%20main%28String%5B%5D%20args%29%20%7B%0A%20%20%20%20%20%20%20%20int%20x%20%3D%201%3B%0A%20%20%20%20%20%20%20%20int%20y%20%3D%202%3B%0A%20%20%20%20%20%20%20%20int%20z%20%3D%203%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20x%20%3D%20y%3B%0A%20%20%20%20%20%20%20%20z%20%3D%204%3B%0A%20%20%20%20%7D%0A%7D&cumulative=false&curInstr=5&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=java&rawInputLstJSON=%5B%5D&textReferences=false).

![call-stack-xyz-x-reassigned](https://curriculum-content.s3.amazonaws.com/java-mod-1/java-visualizer-and-memory/call-stack-xyz-x-reassigned.png)

Notice that the value of `x` changed to the value of `y` once we re-assigned
`x = y;` When we initialize and assign variables to another variable, the
variable being initialized will then be assigned to the value in the other
variable; as we saw with `x = y`.

We can also re-assign variables to a completely new value. Let's see what
happens in memory when we execute the line `z = 4;`

![call-stack-xyz-z-reassigned](https://curriculum-content.s3.amazonaws.com/java-mod-1/java-visualizer-and-memory/call-stack-xyz-z-reassigned.png)

Notice the value of `z` has been changed from `3` to `4` in memory on the call
stack.

## Conclusion

As we saw, memory is how we can run our Java program, define, store, and
initialize variables during runtime. The stack is an area of memory that stores
variables during runtime. We can use the Java Visualizer tool to show us what is
in memory and help us learn more about Java behind the scenes.

## Resources

- [Learning Java, 5th Edition](https://learning.oreilly.com/library/view/learning-java-5th/9781492056263/ch01.html#learnjava5-CHP-1-SECT-4.3)
- [Head First Java, 3rd Edition](https://learning.oreilly.com/library/view/head-first-java/9781492091646/ch09.html#the_stack_and_the_heap_where_things_live)
