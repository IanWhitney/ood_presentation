Note: All of the below came originally from Sandi Metz and Katrina Owen and their class "Practical Object Oriented Design". I am repurposing their exercise for a couple of presentations that I'm giving.

The presentation text is in script.md. The script is more of a series of speaking triggers for myself, so it's not the easiest thing to follow along with.

The code is in bin/house


Below is Sandi & Katrina's original readme.

# The House that Jack Built

Write the code that will output the text to the nursery rhyme
_The House that Jack Built_.

## Setup

- Checkout repo
- `bundle install`
- `rake` or `bundle exec rake`

## Requirements

- Ruby 1.9.3 up to 2.x should be fine. Haven't tried anything else.

### Test Suite

A failing test suite is provided in `./features/house.feature`.
It can be run with any of the following commands:

```plain
$ cucumber
$ cucumber features
$ rake
```

Your mission, should you choose to accept it, is to make the tests pass.

### Lyrics

```plain
This is the house that Jack built.

This is the malt that lay in the house that Jack built.

This is the rat that ate the malt that lay in the house that Jack built.

This is the cat that killed the rat that ate the malt that lay in the house that Jack built.

This is the dog that worried the cat that killed the rat that ate the malt that lay in the house that Jack built.

This is the cow with the crumpled horn that tossed the dog that worried the cat that killed the rat that ate the malt that lay in the house that Jack built.

This is the maiden all forlorn that milked the cow with the crumpled horn that tossed the dog that worried the cat that killed the rat that ate the malt that lay in the house that Jack built.

This is the man all tattered and torn that kissed the maiden all forlorn that milked the cow with the crumpled horn that tossed the dog that worried the cat that killed the rat that ate the malt that lay in the house that Jack built.

This is the priest all shaven and shorn that married the man all tattered and torn that kissed the maiden all forlorn that milked the cow with the crumpled horn that tossed the dog that worried the cat that killed the rat that ate the malt that lay in the house that Jack built.

This is the rooster that crowed in the morn that woke the priest all shaven and shorn that married the man all tattered and torn that kissed the maiden all forlorn that milked the cow with the crumpled horn that tossed the dog that worried the cat that killed the rat that ate the malt that lay in the house that Jack built.

This is the farmer sowing his corn that kept the rooster that crowed in the morn that woke the priest all shaven and shorn that married the man all tattered and torn that kissed the maiden all forlorn that milked the cow with the crumpled horn that tossed the dog that worried the cat that killed the rat that ate the malt that lay in the house that Jack built.

This is the horse and the hound and the horn that belonged to the farmer sowing his corn that kept the rooster that crowed in the morn that woke the priest all shaven and shorn that married the man all tattered and torn that kissed the maiden all forlorn that milked the cow with the crumpled horn that tossed the dog that worried the cat that killed the rat that ate the malt that lay in the house that Jack built.
```
