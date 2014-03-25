Too Big To Succeed

I spent 3 full days trying to learn simple, repeatable approaches to design. I barely scratched the surface.

Now I'm going to share that with you in 25 minutes

Obviously, this talk is too big to succeed.

So I'm going to offer 3 paths:

- A super-condensed, likely baffling design demo now
- A git repository where we can collaborate on simple design problems
- A group for reading and discussing foundational books of OOD design

I'll cover the last two at the end, let's jump into the code.

Coding script:

  - Here's our problem. The customer wants us to print the lyrics to this nursery rhyme.
  - We've been provided an acceptance test. Let's get this to pass.
  - [paste in heredoc]
  - Done!
  - Does this work?
    - Yes. By the definition of the test.
  - Is it well designed?
    - Well, what does that mean?
  - Transparent, Reasonable, Usable, Exemplary
    - Transparent: It is easy for me to see what this does and the effect of a change.
      - Sure. I'd call this transparent.
    - Reasonable: A change takes effort reasonable for its complexity.
      - No. If I wanted to change "Jack" to "Jill" that's a bunch of changes.
    - Usable: This can be used in other contexts.
      - No, not at all. Imagine someone asking us to output a song about the Helipcopter that Jill Flew. None of this could be reused.
    - Exemplary: You want others copying this style.
      - Nope.
  - Another way to think of this (also Sandi Metz)
    - The code needs to work today, just once. And it needs to be easy to change forever.
    - We've met the first goal, nowhere near the 2nd.
    - Too Big to Succeed
  - So, what do we do?
  - Rewrite it!
  - To what?
    - This is not a trivial question. Refactoring is a lot of work, and if we pick wrong, it's a lot of work we'll have to do twice. At least.
  - I have thoughts on places this code could go, but I don't know. 
    - I have no other requirements, so I could just leave it as is. 
    - But I don't want anyone else on my team to see this and think it's a good idea.
    - And I've programmed long enough to know there are more requirements coming, even if I don't know what they are.
  - I want to push this code to a better place, but since I don't know my final destination, I need to take tiny steps.
  - Refactor Under Green
    - My tests pass, they are my safety net. From this point on, I want them to never fail.
    - Failure means I've made too big of a leap.
    - And since I don't know where I'm leaping, that means I've probably gone too far.
  - I can't demonstrate this techinque to you, and I certainly can't convince you of its usefullness.
    - You just have to do it. Really do it. 
    - But here's a quick overview:
      - Find things that are almost identical
      - Make them more identical
      - When they are identical, remove the duplication
  - Let's live code this a bit.
  - Every stanza has this extra newline. Like a pause between stanzas. It's an easy extraction point.
    - Write pause method.
    - Run test.
    - Implement.
    - Run test.
    - Show final result.
  - Ok. I'm willing to admit that's dumb. It certainly doesn't look like a huge improvement.
  - But it isolates a repetitive aspect of our code and gives it a domain specific name. It lets us talk about it.
    - Isolate enough concepts and you'll start to see how they can be grouped.
    - Grouping of concepts is design
  - Let's take the next duplication. We can look at this and see that phrases are repeated in each line. Let's start removing that.
    - Write phrases method with just ["house that Jack built"]
    - Run tests.
    - Implement.
    - Run tests.
    - Show final result.
  - And we can see where this is going, right? Let's fast forward.
  - The structure, the algorithm of rhyme consruction, is becoming more clear. There's some ugly repetition in there that is easier to see now. Let's remove that.
    - Write preamble
    - Run test
    - Implement
    - Run test
  - And, though we certainly could have noticed this earlier, our refactoring has shown us some concepts and the rhyme-construction algorithm.
    - A preamble followed by a, for lack of a better word, Rhyme Part. The rhyme part just concatenates "the" and whatever phrase we care about.
  - We see a behavior that we're repeating. Repeated behavior is an object. This is a talk on OOD, so we should have an object.
    - Write RhymePart
    - Run test
    - Implement
    - Run test
  - That's a single RhymePart, but we can see a bigger algorithm as well, there's a RhymeLine that has a preamble, puts out the correct phrases and then pauses.
  - Move to RhymeLine
  - And a further structure appears, the Rhyme
    - Implement Rhyme
  - And now...I think we can stop.
    - There's some stuff in here I don't love, but I think we can call this "Good Enough"
    - TRUE
    - The classes are small. The responsibilities are reasonably clear. Our tests still pass.
  - Then we get a call from the customer,
    - "Can we display the lines in a random order?"
    - And you can say, "Yes, no problem"
      - Show implementation
        print Rhyme.new(phrases.shuffle).say
    - "Can each verse always end with 'the house that Jack built'?"
    - You can say, "Yes, no problem"
      - Show implementation
        phrases = PHRASES.dup
        first_element = phrases.shift
        phrases = phrases.shuffle
        phrases.unshift(first_element)
        print Rhyme.new(phrases).say
  - "Can we shuffle it so we get verses like 'the cat that Jack built'?"
      - And you say...
        - "Well,..."

Next Steps

  - And that's what we do next. Refactor what we have until we can implement the next feature without further altering the class. Continue to do this and you'll have code that is Open to extension, but Closed to modification. You'll have code that you don't hate working with. It will no longer be Too Big To Succeed. It'll be too small to fail. It will be well designed.

Design with Me

  Fork this repository, each directory has a problem and a README. Follow the directions in the README and send me a pull request when your code works. Then we'll discuss and refactor.

Read Slowly with Me

I'm starting to think about a small reading group that will, very slowly, read some of the foundational books of design. Gang of Four, refactoring, etc. It'd require a time commitment, probably on weekends or maybe some week night. Read a chapter, get together every couple of weeks, discuss deeply. If you're interested, let me know.
