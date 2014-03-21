Too Big To Succeed

I spent 3 full days, including 2 nights of homework trying to learn simple, repeatable approaches to design.

Now I'm going to share that with you in 25 minutes

TBTS

There's no way for me to do this, so I'm going to offer 3 paths:

- A super-condensed, likely baffling design demo now
- A git repository where we can collaborate on simple design problems
- A group for reading and discussing foundational books of OOD design

I'll cover the last two at the end, let's jump into the crazy live coding.

Coding script:

  - Here's our problem. We're showing the lyrics to this nursery rhyme as part of building a nursery rhyme site.
  - We've been provided an acceptance test. Let's get this to pass.
  - [paste in heredoc]
  - Done!
  - Will this succeed?
  - Well, mabye. Assuming nothing ever changes, sure.
  - Transparent, Reasonable, Usable, Exemplary
    - I understand what this does, so I find it transparent
    - Reasonable? Not really. This is hard to extend.
    - Usable? Maybe. As long as nothing changes.
    - Exemplary? No. I certainly wouldn't want this pattern spread throughtout my entire code base.
  - So, we don't think this is great. What should we do?
  - Rewrite it!
  - To what?
    - This is not a trivial question. Refactoring is a lot of work, and if we pick wrong, it's a lot of work we'll have to do twice. At least.
  - I have thoughts on places this code could go, but I don't know. I have no other requirements, so I could just leave it as is. But I on't want anyone else on my team to see this and think it's a good idea.
  - I want to push this code to a better place, but since I don't know my final destination, I need to take tiny steps.
  - Refactor Under Green
    - My tests pass, they are my safety net. From this point on, I want them to never fail. 
    - Failure means I've made too big of a leap.
    - And since I don't know where I'm leaping, that means I've probably gone too far.
  - Find things that are almost identical
  - Make them more identical
  - When they are identical, remove the duplication
  - Every stanza has this extra newline. Like a pause between stanzas. It's an easy extraction point.
    - Write pause method.
    - Run test.
    - Implement.
    - Run test.
    - Show final result.
  - Ok. I'm willing to admit that's dumb. It certainly doesn't look like a huge improvement.
  - But it isolates a repetitive aspect of our code and gives it a domain specific name. It lets us talk about it.
  - Isolate enough concepts and you'll start to see how they can be grouped.
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
  - Then we get a call, 
    - "Can we display the lines in a random order?"
    - And you can say, "Yes, no problem"
      - Show implementation
        print Rhyme.new(phrases.shuffle).say
    - But what if the customer asks for the song to always end in "That jack built"
    - You can say, "Yes, no problem"
      - Show implementation
        phrases = PHRASES.dup
        first_element = phrases.shift
        phrases = phrases.shuffle
        phrases.unshift(first_element)
        print Rhyme.new(phrases).say
  - And then they say
        - "We want to shuffle the actors (cat, malt, etc) separately from their actions (killed, lay in, etc)
      - And you say...
        - "Well,..."

Next Steps

  - And that's what we do next. Refactor what we have until we can implement the next feature without further altering the class. Continue to do this and you'll have code that is Open to extension, but closed to modification. You'll have code that you don't hate working with. It will no longer be Too Big To Succeed. It'll be too small to fail. It will be well designed.

Design with Me
  
  Fork this repository, each directory has a problem and a README. Follow the directions in the README and send me a pull request when your code works. Then we'll discuss and refactor.

Read Slowly with Me

I'm starting to think about a small reading group that will, very slowly, read some of the foundational books of design. Gang of Four, refactoring, etc. It'd require a time commitment, probably on weekends or maybe some week night. Read a chapter, get together every couple of weeks, discuss deeply.


