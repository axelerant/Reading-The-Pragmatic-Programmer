# Pragmatic Paranoia

> You can't write perfect software.

- Accept, Embrace, and celebrate the above fact because perfect software doesn't exist.
- Unless you accept this as a fact, you'll end up wasting time and energy chasing an impossible dream.
- Given this fact, how does a pragmatic programmer turn it into an advantage? This is what we will discus in this chapter.

> _*Everyone knows that they personally are the only good driver on Earth*_

- The rest of the world is out there to get them and generally not living up to our standards. So we drive defensively.
- The analogy with coding is pretty obvious. A lot of times we work on other people's code - code that might not live up to our high standards. Hence, we are taught to code defensively.
- We use assertions to detect bad data & distruct data from potential attackers or trolls.
- We check for consistency, put constraints on database columns, and generally feel pretty good about ourselves.

> _*But Pragmatic programmers take this a step further*_

^^ How??

> Pragmatic Programmers don't trust themselves, either.

> Knowing that fact that no one writes perfect software, including themselves, Pragmatic Programmers build in defenses against their own mistakes.

## Design by Contract

- Dealing with computer system is hard. Dealing with people is even harder.
- One of the best solution for ensuring plain dealing is *contract*

### What is a contract?

A contract defines your rights and responsibilities, as well as those of the other party. In addition, there is an agreement concerning repercurssions if either party fails to abide by the contract.
Example - 
- Employment contract.

Contract is an idea used by the world over - both formally and informally to help humans interact. The same can be used to help software modules interact.

- Bertrand Meyer (Object oriented software construction [Mey97]) developed the concept of *Design by contract* for the language Eiffel.

- Simple yet powerful technique that focuses on documenting the rights and responsibilities of software modules to ensure program correctness.

### What is a correct program?

- One that does no more and no less than it claims to do.
- Documenting and verifying that claim is the heart of Design by contract.

