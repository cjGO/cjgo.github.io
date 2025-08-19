---
layout: post
title: From Genomic Selection to Genomic Design
subtitle: Breeding2RL - Defining the next tool beyond genomic prediction
#gh-repo: daattali/beautiful-jekyll
#gh-badge: [star, fork, follow]
#cover-img: /assets/img/synarabidopsis/ScreenArt.png
tags: [synthetic]
comments: true
---


# From Genomic Prediction to Genomic Design

*Breeding2RL - Defining the next tool beyond genomic selection*  
Posted on August 14, 2025

Every breeder knows this moment: you're staring at your genomic predictions, and Individual A ranks highest for yield. Your models are confident—99th percentile performance. But Individual B carries a rare allele combination that could unlock disease resistance your program desperately needs in five years. Individual A will win you next year's trials. Individual B might save your program.

**Which do you choose?**

Your genomic prediction models can't answer this question. They can only tell you what will happen if you do nothing—**passive observers** of genetic potential. But breeding isn't about observing the future; it's about **actively creating** it through strategic intervention.

This is where we transition from **genomic prediction** to **genomic design**.

## The Evolution: From Prediction to Design

For the past two decades, we've revolutionized breeding through **genomic prediction**. Genomic selection transformed how we evaluate individuals, compressing years of biological feedback into statistical models that can rank a seedling's potential from its DNA alone. This has been transformative—but it's only **half the solution**.

**Genomic prediction** asks: "What will this individual's performance be?"  
**Genomic design** asks: "What should I do to maximize long-term genetic gain?"

The difference isn't subtle—it's the difference between **weather forecasting and climate engineering**. Your genomic models are sophisticated weather forecasts: they tell you what's coming, but they don't tell you how to *change* it.

### Why Genomic Prediction Falls Short

Consider the mate selection problem. You have 200 elite parents and need to choose which crosses to make. Your genomic predictions can rank all 19,900 possible crosses by their expected progeny value. Seems straightforward, right?

But here's what your predictions *can't* tell you:
- How will making Cross A change the allele frequencies available for generation t+3?
- If you make the top 100 crosses by predicted value, will you inadvertently create a **genetic bottleneck**?
- Which seemingly "suboptimal" cross today preserves crucial diversity for a climate challenge you haven't encountered yet?

These aren't prediction problems—they're **sequential decision problems under uncertainty**. Every choice you make reshapes the genetic landscape for all future choices. This is exactly what **genomic design** was conceived to solve.

## The Causal Revolution in Genomic Design

Standard machine learning models, including genomic prediction, excel at **correlation**. They find patterns in data: "Plants with this SNP pattern tend to have higher yield." But correlation isn't causation, and breeding success requires **causal thinking**.

**Genomic Prediction (Observational):** P(high yield | these genotypes)  
**Genomic Design (Interventional):** P(future genetic gain | I select these individuals)

This distinction matters *enormously*. Your genomic predictions assume the population structure remains static—they estimate breeding values as if the genetic background won't change. But every selection decision you make **fundamentally alters** that background.

A genomic design framework learns the **causal chain**: "If I select individuals with this genetic profile, the population's allele frequencies will shift in this direction, which will change the genetic variance available next generation, which affects the potential for future gain in this specific way."

This is **interventional causality**—understanding how your actions change the system, not just predicting what the system will do.

## Beyond Single-Generation Thinking

Perhaps most importantly, genomic design naturally handles the **credit assignment problem** that has plagued breeders for generations. When you make a brilliant cross today, its value might not be realized for five or ten years. How do you learn from such **delayed feedback**?

Traditional breeding relied on generational learning—crude statistical feedback over decades. Genomic selection compressed this to single-generation evaluation. But genomic design can optimize across the **entire temporal horizon**, learning to balance immediate gains against long-term potential.

The genomic design framework learns: "This selection strategy looks suboptimal for the next two generations, but it preserves genetic diversity that becomes *crucial* in generation five when environmental conditions shift."

This is **temporal credit assignment** at the scale breeding actually operates—not predicting next season's winners, but **orchestrating decades** of genetic progress.

## The Strategic Control Problem

Think of breeding as a **control system**. You have:
- **States**: Population genetic structure, allele frequencies, environmental conditions
- **Actions**: Selection decisions, crossing schemes, resource allocation
- **Objectives**: Maximize long-term genetic gain while preserving diversity

Standard prediction models give you **better sensors** for this control system—more accurate estimates of individual breeding values. But they don't give you a **better controller**. They tell you what each lever does, but not which levers to pull, when, and in what sequence.

Genomic design learns the **controller itself**. It discovers multi-generational strategies that balance competing objectives, navigate genetic trade-offs, and adapt to changing conditions—all while maximizing the long-term reward you define.

## Reinforcement Learning: The Natural Solution

This is precisely the problem that reinforcement learning was designed to solve. RL is fundamentally about learning optimal behavior through interaction with an environment—and breeding programs are textbook examples of sequential decision problems under uncertainty.

Consider how perfectly the RL framework maps to breeding:

***Environment***: Your breeding population with its genetic architecture, environmental challenges, and market constraints.

***Agent***: The breeding program making selection and crossing decisions.

***Actions***: Choose which individuals to select, which crosses to make, how to allocate resources across traits.

***States***: Current population genetic structure, allele frequencies, environmental conditions, available genetic diversity.

***Rewards***: Genetic gain, trait improvements, maintained diversity—whatever long-term objectives you define.

The power of RL becomes clear when you see how it naturally handles breeding's core challenges:

**Temporal Credit Assignment**: RL algorithms like TD-learning are specifically designed to propagate rewards backward through time. When a cross made in generation 1 produces breakthrough performance in generation 5, RL learns to credit the original decision appropriately. This is exactly the delayed feedback problem that has made breeding so difficult to optimize systematically.

**Exploration vs. Exploitation**: The classic RL dilemma mirrors breeding perfectly. Do you exploit your current best genetic material (Individual A with high predicted yield) or explore genetic diversity that might pay off later (Individual B with rare alleles)? RL algorithms like upper confidence bound methods learn optimal exploration strategies that balance immediate gains against long-term potential.

**Multi-Objective Optimization**: Modern RL can handle complex reward structures. Your breeding program doesn't just want yield—you want yield plus disease resistance plus environmental adaptation plus genetic diversity preservation. RL learns to navigate these trade-offs automatically, discovering strategies that optimize the full objective function over time.

**Non-Stationary Environments**: As climate changes, markets shift, and new diseases emerge, your breeding environment changes. RL algorithms are designed to adapt continuously, learning new strategies as conditions evolve rather than being locked into static optimization.

The AlphaGo example is instructive: nobody taught AlphaGo specific Go strategies. It learned by playing millions of games against itself, discovering strategies that human masters had never conceived. Similarly, an RL breeding agent could discover crossing and selection strategies that emerge from the complex interactions of quantitative genetics—strategies too sophisticated for any human breeder to design manually.

In breeding simulation, we already have the perfect training environment. Your genetic simulators become the "game" where the RL agent learns optimal breeding strategies through millions of simulated generations, then deploys those strategies in real breeding programs.



## Why This Matters Now

The **genomic prediction revolution** in breeding has reached diminishing returns. We have incredibly sophisticated genomic models, but genetic gain in most crops has **plateaued**. Why? Because having better predictions doesn't automatically translate to **better decisions**.

You can predict individual performance with near-perfect accuracy, but still make suboptimal strategic choices about:
- Which genetic diversity to *preserve vs. exploit*
- How to balance multiple traits with *complex trade-offs*
- When to prioritize *short-term gains vs. long-term potential*
- How to adapt breeding strategies as environments and markets *change*

These are inherently strategic, multi-objective, multi-generational optimization problems. They require moving beyond prediction to **strategic control** through genomic design.

## The Simulation Advantage

Here's what makes this particularly exciting: breeding research has naturally evolved toward simulation-based approaches that are *perfectly suited* for genomic design. Just as we train self-driving cars in simulation before deploying them on real roads, we can train breeding strategies *in silico* before deploying them in real programs.

Your breeding simulators already embed a century of quantitative genetics theory. They model recombination, selection, genetic drift, environmental variation—all the biological "physics" a genomic design system needs to learn optimal strategies.

But simulations alone aren't enough. For decades, we've used them to test a handful of human-designed strategies. **Genomic design** lets the machine discover strategies that might be *far beyond* what any human could conceive or systematically explore.

## From Prediction to Design

The fundamental paradigm shift is this: **genomic prediction** made us incredibly good at evaluating the genetic space we already have. **Genomic design** makes us good at creating the genetic space we *need*.

Your genomic models rank candidates within the current population structure. Genomic design *architects* the population structures of the future. It learns not just which individuals are best, but which selection strategies create the conditions for **sustained genetic progress** over decades.

This isn't about replacing genomic prediction—it's about **unleashing its full potential**. Genomic design uses genomic predictions as inputs to a higher-level strategic optimization that your current tools simply **cannot perform**.

## The Path Forward

The technology exists *today*. Modern breeding programs have the simulation frameworks, genomic tools, and computational resources needed to begin this transition. What's needed is the translation: turning these ideas into practical tools that breeding programs can deploy and benefit from.

The question isn't whether computational breeding strategies will emerge—it's whether our industry will **shape their development** or simply adapt to solutions designed elsewhere.

The conversation starts with understanding this fundamental distinction: we've mastered the art of **predicting genetic potential**. Now it's time to master the science of **realizing it** through strategic intervention.

**The future of breeding isn't about better predictions. It's about better decisions through genomic design.*****The future of breeding isn't about better predictions. It's about better decisions through genomic design.***
