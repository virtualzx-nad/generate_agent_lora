# generate_agent_lora
A set of script to generate agent interactions for training LoRAs.

Data generation and formatting into commands should be separated so that we can quickly move to a different command syntax when needed.
We should also directly include reasoning information whenever possible for every type of interaction.

Focus areas
==========
We will focus the interaction generation in the following areas, subject to addtion over time

* Correctly utilize commands.  Given a list of commands it should only choose from the list, use the right syntax and pick the right command.
* Utilize knowledge.  Agent should use its knowledge when it is reliable, and reasoning should include why knowledge instead of grounding should be used certain topics.
* Search and read.  In some areas it is better to search the internet and read about to gain new information.
* Chain of thought.  Some problems require verbal chains of thought to correctly tackle
* Planning.  Complex problems that should be divided into sensible steps that can be potentially dependent on each other
* Storage and retrieve of information.
* Reflection and verification.
* Address user intention instead of literal meaning
* Tool utilization.   Given a new command and some explanation it should properly utilize the command.
* Coding.  Designing, composing, debugging and deploying code


Method
======
Generally we use these two approaches

* Progressive questioning 
   For simpler topics such as knowledge utilization and search, read and chain of thought we simply as GPT4 to come up with areas and topics, then ask for explations, instead of letting it actually perform the task (which usually it will not behave correctly)
* For more complex tasks like planning we use agents to perform tasks and observe if they succeed.  When they do we store the interaction sequence.
