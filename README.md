# schedulers
Some tournament schedulers written in Haskell for funsies.

**This is a work in progress.**

## The Idea

For the new SIG-Game Arena, it would be nice to be able to write
schedulers in any language. In particular, Haskell seems like an
appropriate language to use, since we're concerned about correctness
of the schedules.

Also, it sounds like a fun combinatorial problem to fiddle around
with.

## Input

All schedulers are stateless. Instead of holding onto state, they
receive state over `stdin`. The rest of the Arena can handle all of
the distributed business and decide when more scheduling needs to
occur (i.e., the task queue is low or empty).

Schedulers receive a JSON object over `stdin` with the following:

* The previous tournament state
* A list of games that have been scheduled/completed since the last
  scheduling

## Output

Schedulers output a JSON object with the following over `stdout`:

* The new tournament state
* A list of games to add to the job queue

When we are ready to reschedule, we pass the new tournament state to
the next scheduler to produce an even newer state. These states could
even be made available to admins, who can watch the state of the
tournament progress.

<!--  LocalWords:  Haskell SIG
 -->
