---
layout: post
title: Intro to AI Breeder Agents
subtitle: Now running on GPU
#gh-repo: daattali/beautiful-jekyll
comments: true
author: Colton G
---

Plant breeding programs are expensive and long-lasting, typically taking 6-14 years to complete. These programs are vital for global productivity in ever-changing markets and climate conditions. Their success hinges on breeders making a series of critical decisions, each with far-reaching consequences that can determine the program's relative success or failure.

To illustrate the complexity of decision-making in breeding programs, let's examine the simplest design a program can follow when aiming to increase the score of a single trait.

Simplest Breeding Program Design:

1. Set a fixed population size for each breeding cycle (e.g., 100 plants)
2. Establish the duration of the breeding program (e.g., 5 cycles, where each cycle represents one generation of plants)
3. Breeder's Decision Process
    a. Score each plant in the population for the trait of interest  
    b. Rank the plants by this score  
    c. Select the top-performing plants as parents (e.g., keep only the highest 5% of individuals)  
    d. Randomly cross the selected parents to create a new population  
    e. Repeat steps a-d until the breeding program ends

Consider the stark difference between selecting the top 3% versus the top 10% of parents in each breeding cycle. Over multiple generations, these seemingly small variations in selection intensity can lead to dramatically different outcomes in the final population's trait values. However, testing every possible combination of parent selection rates in real-world field trials is simply unfeasible.

Breeding simulations perform two main operations:
1) They predict an individual trait score based on its genetic makeup (genotype).
2) They simulate offspring creation by combining genetic information from two parent plants, mimicking natural processes like meiosis and recombination

Understanding genetic variance is key to grasping the dynamics at play in this scenario. Each time we select a subset of individuals as parents, we typically reduce the offspring population genetic variance in exchange for an improved average trait value (phenotype). This delicate balance between maintaining genetic diversity and advancing desired traits is at the heart of breeding strategy – a balance that simulations allow breeders to fine-tune without the constraints of time and budget that real-world experiments impose.
{% raw %}
{% video {{ site.baseurl }}/assets/img/blog_animate_inbreeding.mp4 %}
{% endraw %}
--
![image](https://github.com/cjGO/cjgo.github.io/blob/master/assets/img/blog_animate_inbreeding.mp4)  
![[blog_animate_inbreeding.mp4]]

A quick (in)breeding lesson ;  In this animation 5 distinct breeding programs are simulated where a specified value for the selection intensity is repeated for 100 cycles of selection. Of note:

1) Selection Intensity 0.01 (red) : this represents keeping only the best of the best of our population. It starts out in the lead but almost immediately hits a wall. When you see the column that means the population is completely inbred. There is nothing to select from; dead end. We don't make use of 90% of the remaining cycles.
2) Selection Intensity 0.10 (yellow): this is the next quickest after 0.01. It also burns out and hits a dead end when inbreeding becomes too strong. Again we don't make use of the entire available time because of poor breeding.
3) Selection Intensity 0.50 (green): Despite not improving as quickly as 0.10, it lasts longer, it only reaches intense inbreeding at the very end of our 100 cycle breeding program, making use of every cycle to improve the phenotype.
4) Selection Intensity 0.85 (blue): Slow and steady doesn't win the race if the race isn't a marathon. While our simulation is 100 cycles long, this population is not a column at the end of it and therefore still has variation to improve the phenotype with.
5) Selection Intensity 0.99 (purple): A slight selection. Over 100 cycles its score slightly increases while maintaining high diversity. Given another 900 cycles even this population will also reach critical inbreeding.

This simulation was using the same repeated action throughout the breeding program, as a simple strategy. A professional breeder would take into consideration the state of their current population and breeding program. In complex breeding programs, even the fastest simulations aren't quick enough to model every scenario, there are simply too many.

Agents are models trained with Reinforcement Learning algorithms, which are best known for mastering complex, sequential decision-making in games like Go, Poker, and StarCraft II. Reinforcement Learning models are famous for being data-hungry which pairs well with simulations. The agent begins with no knowledge of the rules or consequences of its actions. Through neural networks compressing this information and a learning algorithm, it effectively stores memories and learns cause-and-effect relationships between its action(the selection intensity the breeder chooses to keep the top % of parents) and reward (the improved trait score of the offspring in the final generation of the breeding program). 

This is a relatively underexplored area in the breeding sciences; there is about a handful of publications on this topic today. 

---

We will set up a similar scenario as before: a breeding program that lasts 10 cycles, has a fixed population size of 500 at each cycle, and we will use the same constant action to find a good baseline to compare the breeder agent to.

In the figure below, each line represents a breeding program where a specific selection intensity was repeated for each of the 10 cycles. Purple intensity represents a conservative number of parents selected, versus green where more parents are selected.

The top chart shows the improvement of phenotype at each cycle. We see the phenomenon of inbreeding again with the darkest purple line representing the strongest selection intensity, which plateaus at its top value before the program ends.

The middle chart shows the genetic variance, which is the same as saying how wide the distribution is, like in the animation earlier. If it's not zero, then it's possible for selection to still improve the trait in the offspring population.

The bottom chart shows the max phenotype, another metric to see how well they perform. The dashed line shows the optimal constant action.


![image](https://github.com/cjGO/cjgo.github.io/blob/master/assets/img/breeder_agent_01.png?raw=true)  

The breeder agent will now use the same simulation to come up with its own solution to this problem. Instead of being forced to pick a constant action, we allow the agent to pick any number between 0.01 and 0.99 at each cycle. We know that if it simply repeats 0.11, it will reach a high score; however, the agent has no prior knowledge of quantitative genetics or breeding. Instead, it must play the game by making random decisions until it learns to find a consistent reward.

In addition, we provide the agent with information about the current state of the breeding program. This could include anything from images, budgets, genotypes, phenotypes, pedigrees, or more. Keeping this example simple, we will give the agent the following pieces of information:

1. The remaining number of cycles in the program
2. The genetic variance of the current population (width of scores distribution)
3. The average selection intensities the agent has used so far in this attempt

These three pieces of information were found to consistently reach a similar score to our constant action baselines. In the figure below, we can see the average scores during the agent training. Light blue represents the beginning of the program, while the dark purple line represents the final cycle. The dashed red line is the baseline from our constant action strategy. The x-axis shows the number of training steps the agent has taken so far.


![image](https://github.com/cjGO/cjgo.github.io/blob/master/assets/img/breeder_agent_02.png?raw=true)  

The agent successfully leverages the simulation software to explore strategies, finding a relatively unique solution compared to our naive baseline of repeating the same action every cycle. The agent takes a series of decreasing steps, at or below the best constant action we found (seen on the bottom chart). Given the simplicity of this example, it's likely both the agent and naive baseline are finding near-optimal solutions. Showing that the agent can learn this trivial example is a crucial first step to build support for these algorithms.

Breeding programs face complex challenges, including budget constraints, multiple trait selection, and intricate mating schemes. While various lab protocols (e.g., gene editing) can enhance program success, their integration requires validation through simulations. The optimization of these programs is highly sensitive to fluctuating costs and unforeseen events. An AI agent, trained on simulations, can rapidly adapt strategies in response to financial changes, breeding setbacks, or environmental factors, potentially outperforming human breeders who might make short-sighted decisions. This adaptive approach ensures continuous population improvement despite dynamic conditions, making AI-assisted breeding programs more resilient and efficient.

These algorithms, combined with well-designed simulations, have the potential to either automate or serve as sophisticated decision-support systems for breeders across a wide range of scenarios and species (from the nearly extinct populations of the Hawaiian tree snails to designer pigs or food like rice, cattle, or mangoes). By carefully controlling the agent's inputs and actions, we can flexibly model diverse real-world situations. Most excitingly, these agents may discover innovative strategies that even experienced professional breeders might not consider, pushing the boundaries of what's possible in breeding program optimization and potentially leveling the playing field for smaller or less well-funded programs.Key takeaways:

1. Breeding programs are long-term, costly investments requiring strategic planning.
2. Their success hinges on a series of adaptive decisions in response to changing conditions.
3. The synergy of simulations and AI agents can provide powerful decision support systems for breeders, potentially revolutionizing the field.
