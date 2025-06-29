---
layout: post
title: If you’re not using pipelines, you’re not doing it right.
date: 2025-06-28 11:00:00
description: workflows - from scripts to scale
tags: workflows nextflow
categories: personal-perspective
featured: true
---

## At the beginning...

> [!WARNING]
> If you’re not using pipelines, you’re not doing it right.

I still remember the moment it all shifted, the moment I realized I needed more than just a tangle of scripts to make sense of my work.     

It was 2016. My folders were a graveyard of .sh files — some reused, some renamed, some... unrecognizable. I had directories each holding outputs from hours of computation. No logs. No checkpoints. No version control. Just layers of pure chaos.        
At the time, I was collaborating with Leiden University Medical Centre (LUMC). We were building a genome analysis pipeline together, and for the first time, I wasn’t working alone. Suddenly, my improvised workflows weren’t enough. I couldn’t hand over a pile of scripts and hope others would follow the logic I barely remembered.     
So we did something different.     

We designed a real workflow. It had structure. It had checkpoints. It had version control. And more importantly, it could be reused, shared, and executed reliably across systems and users.     
That collaboration was my turning point. I stopped thinking of computational analysis as a loose collection of steps. I began to see it as something engineered — something built, not just hacked together. It was the beginning of a shift in how I approached bioinformatics altogether.     

## 🧰 :bulb: My first workflow in GNU Make

My first workflows were developed in GNU Make, which was widely employed but not officially for workflows. Make was created in 1976 as part of the Unix ecosystem. 
Its purpose was simple: to automate the building of programs by describing how files depend on one another and what commands are needed to update them.

The GNU version, GNU Make, is part of the GNU Project, and remains widely used in open-source development today. It’s what you run when you type make in countless software packages to compile code, install dependencies, or manage complex build systems.
But its power extends far beyond software compilation.
In essence, Make is a rule-based execution engine:
You define targets, their dependencies, and the commands to produce them. Then, make it automatically run only what's needed and skip everything that's already up to date.
This makes it surprisingly useful in bioinformatics, especially for reproducible data processing pipelines, managing intermediate files and dependencies, and automating multi-step analyses across projects

It's minimalist, elegant, and brutally efficient, the grandfather of all scientific workflow tools.

## :snake: Enter Snakemake: workflows with Python structure

Soon after, I met Snakemake, the workflow manager that changed everything for me.
For those unfamiliar: Snakemake is a workflow system modelled on Makefiles but powered by Python, designed by Johannes Köster. 
It lets you define your analysis as a set of rules, with clear input/output relationships, and automatically determines what needs to be (re)run.

Snakemake was able to define rules that map input files to output files and use wildcards to handle variable filenames automatically, similar to Make, but it had more than this. 
It was also able to specify resources (e.g., threads, memory, runtime) per rule and integrate cluster schedulers. Furthermore enables the user to run containers or Conda environments per rule for reproducibility which was the real gamechanger.

My appreciation for Snakemake deepened not just in academia, but when I transitioned to a project in the private sector. 
I was tasked with building and maintaining a workflow to process genome assemblies for multiple samples per week. Each dataset needed to be handled with precision and complete reproducibility. This is where Snakemake truly proved itself.

I didn’t just learn Snakemake as a tool. I learned to think in pipelines, spending a considerable amount of hours learning efficient pipeline structures. Additionally, I began to understand the beauty of abstraction, the value of modularity, and the quiet power of a system that runs without needing to be babysat. 
I learned to anticipate bottlenecks, handle exceptions, and build in documentation as part of the process, not as an afterthought. That experience taught me to appreciate well-crafted workflows, working together with collaborators on the project,  not just as a means to an end, but as a scientific and engineering discipline in their own right.
Good pipelines aren’t just functional. They’re elegant. They scale, they document thinking, and they make processes more reliable.

Snakemake gave me my first real taste of that elegance — and it set the bar for everything that came next.
The pipeline is still very popular today, widely applicable to many workflows. 

## 🔄 Scaling up with Nextflow

As my projects grew in complexity, spanning hundreds of genomes and datasets across teams at the Centre for Crop and Disease Management, I eventually reached the limits of what Snakemake. 
While it had been the perfect companion for flexible, readable workflows, I needed something built from the ground up for large-scale, distributed computing. That’s when I turned to Nextflow.
That’s when I turned to Nextflow.

Nextflow is a data-driven workflow manager developed by Paolo Di Tommaso. It was designed specifically for scalable, reproducible workflows in bioinformatics, and it has become one of the most powerful and widely adopted tools for HPC and cloud-based analysis.
Unlike other workflow engines, Nextflow combines a scripting language (based on Groovy) with native support for parallel execution across local, HPC, and cloud environments. It allows to use of containers (Docker, Singularity, Podman) and Conda environments. 
The pipelines have full pipeline portability and sharing via GitHub. 
And most importantly, I could do it all without changing my core logic. The workflow was infrastructure-agnostic. I could develop locally, run on HPC, or deploy to AWS with minimal reconfiguration.

## :loudspeaker: :pushpin: Summary & Final Thoughts

What began as a way to clean up my folders became something much deeper:
An adoption of engineering science, where code isn’t just functional but elegant and shareable. 
If you're still running analyses manually, copying files, rewriting scripts, and tracking steps by memory, it’s time to stop.
Because good science deserves clarity, structure, and reproducibility, all of which can be achieved through pipelines.

> [!TIP]
> If you’re not using pipelines, you’re not doing it right.

## 🔗 Further Reading & Useful Links

- 🧰 **GNU Make**  
  [https://www.gnu.org/software/make/](https://www.gnu.org/software/make/)  
  Official documentation for GNU Make — a foundational tool for automation and dependency management.

- 🐍 **Snakemake**  
  [https://snakemake.readthedocs.io](https://snakemake.readthedocs.io)  
  Comprehensive documentation, tutorials, and examples for writing reproducible workflows with Snakemake.

- 🔄 **Nextflow**  
  [https://www.nextflow.io](https://www.nextflow.io)  
  Main Nextflow website with guides, documentation, and getting started materials.
