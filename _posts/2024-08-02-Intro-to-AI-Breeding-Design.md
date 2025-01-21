---
layout: post
title: 001-Intro to AI Breeder Agents
subtitle: Now running on GPU
#gh-repo: daattali/beautiful-jekyll
comments: true
author: Colton G
---

Plant breeding programs are expensive and long-lasting, typically taking 6-14 years to complete. These programs are vital for global productivity in ever-changing markets and climate conditions. Their success hinges on breeders making a series of critical decisions, each with far-reaching consequences that can determine the program's relative success or failure.

To illustrate the complexity of decision-making in breeding programs, let's examine the simplest design a program can follow when aiming to increase the score of a single trait.

**Simplest Breeding Program Design:**
1. Set a fixed population size for each breeding cycle (e.g., 100 plants)
2. Establish the duration of the breeding program (e.g., 5 cycles, where each cycle represents one generation of plants)
3. Breeder's Decision Process
   
    a. Score each plant in the population for the trait of interest
   
    b. Rank the plants by this score
   
    c. Select the top-performing plants as parents (e.g., keep only the highest 5% of individuals)
   
    d. Randomly cross the selected parents to create a new population
   
    e. Repeat steps a-d until the breeding program ends

Consider the difference between selecting the *top 3% versus the top 10%* of parents in each breeding cycle. Over multiple generations, these seemingly small variations in selection intensity can lead to **dramatically different** outcomes in the final population's trait values. However, testing every possible combination of parents in the real-world is simply impossible.


---

Breeding simulations perform two main operations:

1) They predict an individual's trait score based on its genetic makeup (genotype)

2) They simulate offspring creation by combining genetic information from two parent plants, mimicking natural processes like meiosis

Understanding genetic variance is key to grasping the dynamics at play in this scenario. Each time we select a subset of individuals as parents, we typically reduce the offspring population genetic variance in exchange for an improved average trait value (phenotype). This delicate balance between maintaining genetic diversity and advancing desired traits is at the heart of breeding strategy – a balance that simulations allow breeders to fine-tune without the constraints of time and budget that real-world experiments impose.

--

<video width="100%" height="auto" controls>
  <source src="{{ site.baseurl }}/assets/img/blog_animate_inbreeding.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

A quick (in)breeding lesson; In this animation each frame shows the trait values for a population of 5 distinct breeding simulations where a specified selection intensity is repeated for 100 cycles of selection. Of note:

# Inbreeding Simulation Analysis: Effect of Selection Intensity

Each frame shows trait values for 5 distinct breeding simulations across 100 selection cycles.

## Key Observations:

**Selection Intensity 0.01 (Red)**
- Represents selecting only the *elite* performers
- Initially leads but rapidly plateaus
- Population becomes fully inbred (visible as a column)
- Wastes ~90% of available breeding cycles

**Selection Intensity 0.10 (Yellow)**
- Second fastest initial progress
- Also reaches inbreeding dead-end
- Fails to utilize full breeding timeline
- Progress halts due to loss of diversity

**Selection Intensity 0.50 (Green)** 
- Slower initial improvement than 0.10
- Maintains progress for longer duration
- Reaches intense inbreeding only at cycle 100
- *Maximizes use of available breeding cycles*

**Selection Intensity 0.85 (Blue)**
- Slower but more sustainable progress
- Maintains genetic variation through cycle 100
- Population avoids column formation
- *Retains potential for further improvement*

**Selection Intensity 0.99 (Purple)**
- Minimal selection pressure applied
- Gradual score increase over 100 cycles
- *Preserves highest genetic diversity*
- Would reach critical inbreeding after ~1000 cycles
  
This simulation was using the same repeated action throughout the breeding program, as a simple strategy. A professional breeder would adjust their actions taking into consideration the state of the current population profile. In complex breeding programs, even the fastest simulations aren't quick enough to model every scenario, there are simply too many combinations combined with random chance.

*Agents* are models trained with Reinforcement Learning algorithms, which are best known for mastering complex, sequential decision-making in games like Go, Poker, and StarCraft II. Reinforcement Learning models are famous for being data-hungry which pairs well with simulations. The agent begins with no knowledge of the rules or consequences of its actions. Through neural networks compressing this information and a learning algorithm, it effectively stores memories and learns cause-and-effect relationships between its action(the selection intensity the breeder chooses to keep the top % of parents) and reward (the improved trait score of the offspring in the final generation of the breeding program). 

This is a relatively underexplored area in the breeding sciences; there is a handful of publications on this topic today. 

---


# Breeding Program Analysis: Effects of Selection Intensity Over 10 Cycles

## Program Parameters:
- **Duration**: 10 breeding cycles
- **Population Size**: 500 individuals per cycle
- **Variable**: Selection intensity (compared against constant baseline)

## Figure Analysis:

### *Top Chart: Phenotype Improvement*
- Each line represents a different selection intensity strategy
- **Purple lines**: Conservative parent selection (fewer parents)
- **Green lines**: Liberal parent selection (more parents)
- *Key observation*: Darkest purple (highest intensity) plateaus before program completion due to inbreeding

### *Middle Chart: Genetic Variance*
- Measures distribution width of trait values
- Non-zero values indicate potential for further improvement
- *Critical for understanding breeding potential*

### *Bottom Chart: Maximum Phenotype*
- Alternative performance metric
- **Dashed line**: Represents optimal constant action baseline
- Enables comparison between strategies

*Note: Visual representation available in referenced figure showing progression across all three metrics over the 10 breeding cycles.*


![image](https://github.com/cjGO/cjgo.github.io/blob/master/assets/img/breeder_agent_01.png?raw=true)  

The breeder agent will now use the same simulation to come up with its own solution to this problem. Instead of being forced to pick a constant action, we allow the agent to pick any number between 0.01 and 0.99 at each cycle. We know that if it simply repeats 0.11, it will reach a high score; however, the agent has no prior knowledge of quantitative genetics or breeding. Instead, it must play the game by making random decisions until it learns to find a consistent reward.

In addition, we provide the agent with information about the current state of the breeding program. This could include anything from images, budgets, genotypes, phenotypes, pedigrees, or more. Keeping this example simple, we will give the agent the following pieces of information:

1. The remaining number of cycles in the program
2. The genetic variance of the current population (width of scores distribution)
3. The average selection intensities the agent has used so far in this attempt

These three pieces of information were found to consistently reach a similar score to our constant action baselines. In the figure below, we can see the average scores during the agent training. Light blue represents the beginning of the program, while the dark purple line represents the final cycle. The dashed red line is the baseline from our constant action strategy. The x-axis shows the number of training steps the agent has taken so far.


![image](https://github.com/cjGO/cjgo.github.io/blob/master/assets/img/breeder_agent_02.png?raw=true)  

The agent successfully leverages the simulation software to explore strategies, finding a relatively unique solution compared to our naive baseline of repeating the same action every cycle. The agent takes a series of decreasing steps, at or below the best constant action we found (seen on the bottom chart). Given the simplicity of this example, it's likely both the agent and naive baseline are finding near-optimal solutions. Showing that the agent can learn this trivial example is a crucial first step to build support for these algorithms.


Breeding programs face complex challenges, including budget constraints, multiple trait selection, and intricate mating schemes. While various lab protocols (e.g. gene editing) can enhance program success, their integration requires validation through simulations. The optimization of these programs is highly sensitive to fluctuating costs and unforeseen events. An AI agent, trained on simulations, can rapidly adapt strategies in response to financial changes, breeding setbacks, or environmental factors, potentially outperforming human breeders who might make short-sighted decisions. This adaptive approach ensures continuous population improvement despite dynamic conditions, making AI-assisted breeding programs more resilient and efficient.

These algorithms, combined with well-designed simulations, have the potential to either automate or serve as sophisticated decision-support systems for breeders across a wide range of scenarios and species (from the nearly extinct populations of the Hawaiian tree snails to designer pigs or food like rice, cattle, or mangoes). By carefully controlling the agent's inputs and actions, we can flexibly model diverse real-world situations. Most excitingly, these agents may discover innovative strategies that even experienced professional breeders might not consider, pushing the boundaries of what's possible in breeding program optimization and potentially leveling the playing field for smaller or less well-funded programs.

**Key takeaways:**

1. Breeding programs are long-term, costly investments requiring strategic planning.
2. Their success hinges on a series of adaptive decisions in response to changing conditions.
3. The synergy of simulations and AI agents can provide powerful decision support systems for breeders, potentially revolutionizing the field.
