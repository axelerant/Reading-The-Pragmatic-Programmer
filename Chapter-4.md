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

### DBC

- Every function and method in a software does something. It has some expectations and based upon that it delivers some output.

- Meyer describes these expectations and claims as follows - 

### Preconditions

- What must be true in order for the routine to be called: the routines's requirements. A routines should never get called when its preconditions would be violated. It is the caller's responsibility to pass good data.

### Postconditions

- What routine is gauranteed to do; the state of the worls when routine is done. The fact that the routine has a postcondition implies that it will conclude: infinite loops aren't allowed.

### Class invariants

- Class ensures that this condition is always true from the perspective of a caller. During internal processing of a routine, the invariant may not hold, but by the time routine exits and control returns to the caller, the invariant must be true.

* The contract between a routine and any potential caller can thus be read as :

> If all the routines's preconditions are met by the caller, the routine shall gaurantee that all postconditions and invariants will be true when it completes.

If either party fails to live up to the terms of the contract, then a remedy is invoked - maybe an exception is raised, or the program terminates.

> Whatever happens, make no mistake that failure to live up to the contract is a "BUG".

