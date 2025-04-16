# Part 2 - Reasoning Models

So far, we have been able to use large language models (LLMs) to generate text and establish conversation. But what would happen if we asked these models to solve a logic puzzle or perform a mathematical operation to address a problem? We might get lucky if the model's training data happened to include a solution to a similar problem, but once we attempt to ask clarifying questions or present a problem the model hasn’t been explicitly trained on, it’s unlikely we’ll arrive at an accurate solution. Standard LLMs are not designed to tackle these types of problems. **This is where reasoning models come into play.**

Reasoning models can reach higher levels of performance in domains like math, coding, science, strategy, and logistics. The way these models produces outputs is by explicitly using chain of thought to explore all possible paths before generating an answer. They verify their answers as they produce them which helps them to arrive to better more accurate conclusions. This means that reasoning models may require less context in prompting in order to produce effective results.

Such way of scaling model's performance is referred as inference compute time as it trades performance against higher latency and cost. It contrasts to other approaches that scale through training compute time.

Reasoning models then produce two types of outputs:

- Reasoning completions
- Output completions

Both of these completions count towards content generated from the model and hence, towards the token limits and costs associated with the model. Some models may output the reasoning content, like DeepSeek-R1. Some others, like o1, only outputs the output piece of the completions.

### Reasoning Models Available

- `o3-mini`
- `DeepSeek-R1`



## Interacting with Reasoning Models

1. Navigate to the  **playgrounds** section and select **Try the Chat Playground**

>[!alert] Before you start, click on **Clear Chat** to avoid any context from previous interactions.


2. Select `o3-mini` under the Deployment section.

![Selecting a reasoning model from deployments]()

### **Math**:

1. In the chat text-box, let's try the following prompt:

```
Solve the equation x - 50 = 30
```

2. How about we try something a bit more difficult? Let's see how the model responds to a related rates problem, which requires a word problem to be understood and converted into a mathematical solution. 

Try the following prompt now:

```
Solve the following problem:
A tank of water in the shape of a cone is being filled with water at a rate of 10 m3/sec. The base radius of the tank is 34 meters and the height of the tank is 10 meters. At what rate is the depth of the water in the tank changing when the radius of the top of the water is 10 meters?
```

You will see that not only does the model reach a solution, but it is thoroughly explained and detailed in its analysis. 

3. Lastly let's try a brain-teaser math puzzle:

```
Two 2s can be combined in many ways to express different numbers. Here are some!
2-2=0
2/2 = 1
.2 + 2 = 2.2
(2^2)! = 24 (4! means 4x3x2x1) (2^2 is 2 to the power of 2)

Can you write an expression that has the value of exactly 5, using:
* two, and only two, 2s, and
* any mathematical symbols or operations?

You may not use any other numbers. The symbols used would be known by most high school maths students.
```

What did the model produce for an answer? Note, there is at least two different approaches that correctly solve this puzzle!

### **Logic**:

Next, let's try a logic puzzle:

```
Five people were eating apples, A finished before B, but behind C. D finished before E, but behind B. What was the finishing order?
```

Again, the model is able to reason appropriately and come to the solution accurately. 

### **Code**:

As mentioned before, one of the areas where reasoning models excel is at dealing with code. 

1. We have all run into code that may be a bit hard to understand at first glance. Especially if we do not have context around it. Let's test `o3-mini` out with this piece of uncommented code, with ambiguous variable names:

```
Explain what the following code piece is doing:

A = np.array([2,1,2,3,2,9])
B = np.array([3,4,2,4,5,5])
 
print("A:", A)
print("B:", B)

x = np.dot(A,B)/(norm(A)*norm(B))
print("Result:", x)
```

2. Is the explanation reasonable enough? Try asking the model about scenarios where this code might be used, and to rewrite it for clarity!

```
In what scenario would this code piece be useful? Rewrite it for clarity and ease of understanding in the future.
```

3. What if we had to face code in a programming language we are not familiar with? `o3-mini` and other reasoning models are able to convert a piece of code from one language to another. 

Let's try converting this piece of Go code into C#:

```Go
package main

import "fmt"

type Stack struct {
    items []int
}

func (s *Stack) Push(item int) {
    s.items = append(s.items, item)
}

func (s *Stack) Pop() int {
    if len(s.items) == 0 {
        return -1 // Error: Stack is empty
    }
    lastIndex := len(s.items) - 1
    popped := s.items[lastIndex]
    s.items = s.items[:lastIndex]
    return popped
}

func main() {
    stack := Stack{}
    stack.Push(1)
    stack.Push(2)
    stack.Push(3)
    
    fmt.Println(stack.Pop()) // Outputs: 3
    fmt.Println(stack.Pop()) // Outputs: 2
    fmt.Println(stack.Pop()) // Outputs: 1
}
```

Try converting to other languages too! (Maybe one you are most familiar with, if not C#).

4. Lastly, let's convert our past rate-of-change problem to a program that is able to solve them. 

```
Write a Python program that is able to solve problems such as the following: 
A tank of water in the shape of a cone is being filled with water at a rate of 10 m3/sec. The base radius of the tank is 34 meters and the height of the tank is 10 meters. At what rate is the depth of the water in the tank changing when the radius of the top of the water is 10 meters? 
All values should come in as parameters to the function, such that in any other similar problem the program is still usable.
```

## Next Steps

Congratulations! You have completed the second part of this workshop, and have experimented with reasoning models.

Click **Next** to proceed to the Image Generation section.