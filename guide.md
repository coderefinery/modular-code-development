

# Instructor guide

## Why we teach this lesson

Most codes and scripts start very simple, fit into a screen, and do not require
testing, interfaces, modules, encapsulation, or even documentation. But over
time codes grow and what used to be a simple script can become a complicated
and often unmaintainable code that nobody understands anymore.  Many of us have
been in this situation.

We have this lesson mainly to raise awareness about what factors affect code
complexity and how to approach modular code design.


## Learning topics

- Know about pure functions (functions without side effects, functions which
  given same input always return same output).
- Learn why and how to limit side effects of functions.
- Discuss why and how to limit side effects of data. Also discuss when
  mutable data may be preferable.
- The Zen of Python: https://www.python.org/dev/peps/pep-0020/
- Discuss why single-purpose functions are often preferred over
  multi-purpose functions.


## Intended learning outcomes

By the end of this lesson, learners should:
- Know the concepts of side effects, state, and purity
- Be able to motivate the use of pure functions
- Be able to visualize their code in form of a call tree (note that this is
  currently not in the material)
- Know where in the call tree to locate "impurity" (state, side effects,
  input/output) and which part of the call tree to keep pure
- Be able to recognize when to divide a code portion into a function
- Be able to recognize when to divide a function into functions
- Understand the advantages (and disadvantages) of encapsulation
- Be aware that code complexity might limit reuse and introduce bugs
- Know that implementation choices are often a balance between efficiency in
  terms of human time, CPU time, memory, disk, ...


## Challenge and format

We got once this very fitting feedback: "This is a lesson that everybody needs
but you need experience to appreciate the value of it. But if you have the
experience to appreciate this lesson, you probably already know this."

In other words this lesson may not be convincing for participants who have
never written longer scripts/code than, say, one screen-size and may have never
used functions to portion their codes.

I believe this lesson has value for those who are a bit more experienced but we
probably need to rethink this lesson to make it more approachable and
interesting for all participants.

In this lesson we have iterated between showing and discussing explicit
examples, which can be boring for those who are not familiar with the language
of the example, and a general overview (current version), where the feedback
can be that this is not explicit enough. To accommodate the many languages we
have chosen to maximize group work where code complexity, modular design, and
side effects are discussed in the context of a particular programming language.

We have tried various formats:
- Slides and discussion (this repository in the past)
- Fewer slides, group work, and discussion (this reposistory now)
- Demo with discussions and suggestions via collaborative notes (https://github.com/coderefinery/modular-type-along)


## Timing

We have tried this lesson with 1-1.5 hours but perhaps this is too short.

It is difficult to not become too abstract or too specific on one language.

Perhaps we should give this lesson more time and perhaps we should try a "bring
your own script/code" format where we improve our projects in a group work
setting?


## How to teach this lesson in this version

We start with a 15-20 minute presentation and discussion in class where
we discuss the slides and encourage questions and discussion. The slides
are meant as food for thought and not as dogmatic "truth". Disagreement
and different views are encouraged by the presenter.

After we have discussed the slides, we give instructions for group work and
point the participants to a shared [HackMD](https://hackmd.io) document.  We
form groups of 5-6 persons according to their preferred programming languages.
Typically we arrive at 4 groups. Make sure each group has a scribe (to write
notes) and chair (to encourage equal participation).

We give groups 30 minutes to discuss the following questions:
- What best practices can you recommend to arrive at well structured, modular
  code in your favourite programming language?
- What would you recommend your colleague who starts in the same programming language?
- How do you deal with code complexity in your projects?

As instructor/helper visit the groups after 15 minutes or so and encourage that
ideas are written down (some groups have great discussions but forget to write
bullet point ideas down) and also after 25 minutes to check whether groups
would like more time and to make them aware that we should reconvene to discuss
the results.

Finally we spend 20 minutes to discuss the findings of each groups. Hopefully
this sparks more questions and discussion and hopefully we see common trends
crystallize across programming languages.
