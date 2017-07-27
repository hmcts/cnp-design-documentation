# Test-driven Infrastructure Framework

The attempt here is to take an high-level philosophical overview of the business od testing infrastructure code, setting out a vision for what the testing strategy landscape should look like. 

## Test-driven Infrastructure: a Conceptual Framework

Test-driven infrastructure should be based on the MASCOT concept:

- *M*ainstream
- *A*utomated
- *S*ide-effect aware
- *C*ontinuously integrated
- *O*utside-in
- *T*est-first

### TDI should be mainstream

It should not be questioned that developing infrastructure code is done in a test-driven way. 
Although a very strong case can be made for the approach, it will never become mainstream until the barriers to entry are lowered.
Modern language like Ruby, has most comprehensively embraced test-driven engineering. The quality of tooling is very high, with innovation and improvement being seen on regular basis.

In order for testing to become mainstream, it's necessary to agree a set of standards around which to organize. 
When developing infrastructure code in a shared environment, enforcing a house style can be very valuable thing to implement.
It encourages the team to work in a consistent way, and ensures that code is maximally shareable and portable.

### TDI should be automated

In order for testing to become mainstream, and effective, it's essential that it will be automated, especially in the case of long-running, complex integration test.
A workflow (or pipeline) that includes automation of these high-value, labor-intensive tests allows to run tests with a degree of frequency to deliver consistent improvements and a degree of feedback that is noticeable and unignorable.

Infrastructure tests should run automatically, ideally on every commit. Even better is to move to a continuous deployment model, where every commit not only kicks off a test run, but deploys the code
on a test environment, and then traverses a build pipeline, with appropriate yes/no gates, ultimately resulting in an update of the production infrastructure.

### TDI should be side-effect aware

When we write infrastructure code to capture a set of complex requirements, what we’re really doing is commanding one system to take action in a way which has a side effect on another system, 
which in turn impacts other systems, in such a way as to bring the world into a desired state.

Fundamentally, we want to be confident that seemingly trivial changes to our infrastructure don’t have unwanted side-effects. This becomes more of a challenge if our code grows to support complex platforms.

### TDI should be continuously integrated

A key component of constructing a world in which our infrastructure testing is both automated and side-effect aware is that the code we write should be continuously integrated.

Another core practice from eXtreme programming, the idea of continuous integration lies in the recognition that the traditional approach of periodically integrating the code of a number of different people is invariably an error-prone, time-consuming and painful endeavor.

In principle developers should be integrating and committing code very frequently. This avoids diverging or fragmented development efforts, especially where team members are not in direct communication with each other.

If we’re to be serious about developing quality infrastructure code, we need to bring the same practices to bear. This means that our tests need to be run automatically on commits, and the results shared visibly and publicly.

### TDI should be outside in

One of the maxims of BDD is that we take an outside-in approach. 
Imagine a group of people in a room with a programming task to complete, of moderate complexity. 
If you were to watch each person in the room after finishing explaining the task, you’d find that the most natural approach, and the statistically most-likely approach of each person would be to open up their editor of choice and start hacking away. 
You might find some people opening up some kind of interactive REPL, and experimenting. 
Those with a grounding in agile programming approaches might even start writing some basic unit tests. 
This kind of approach is called “inside-out”. Straight away we’re starting to write the code to solve the problem, even if we’re writing tests first.

BDD encourages thinking about the problem a different way. This is the great thing about Cucumber - it allows, and to an extent even forces the developer to step right away from the implementation details and think about how the software should look, feel, behave, act. This is outside-in. We describe a feature that delivers value, as an executable specification. Only once we have this feature described, and failing a test, do we start to think about how to make it pass.

The outside-in approach starts by writing the feature which defines how the piece of infrastructure should behave and the fact that none of our development efforts are worth a thing if they don’t address a specific business value. Test-driven infrastructure means committing to build the right thing, not just build the thing right.

### TDI should be test-first

The final objective of mascot manifesto is that as we write our infrastructure, not only should we be ensuring our code is under test, but that those tests should be written before we write any code. 
This discipline recognizes that the tests we write are actually a development tool in themselves. 

The benefits are clear:
* It focuses attention on precisely what the infrastructure code needs to do.
* It makes it very clear where the development should start.
* There is never any question about the definition of done - the test owns this.
* It encourages a lean and efficient development approach - we build only as much infrastructure as is needed to make the tests pass.
* It makes our code easy to reason about - the target is reproducible, predictable results.
* Dependencies are flushed out early, and their minimization is a core activity.
* It surfaces good design decisions by encouraging the creation of solutions that are simple enough to make the test pass, but no simpler.
* In the event of unexpected failures, the debugging process is targeted.
* It encourages refactoring - as we write code to make our tests pass, so we should identify hints that refactoring is needed.
