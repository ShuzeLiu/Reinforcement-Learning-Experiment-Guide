# Reinforcement Learning Experiment Guide

## Get familiar with PyTorch

* [Official Guide](https://pytorch.org/tutorials/)
* [Quick Recap](https://www.cs.princeton.edu/courses/archive/fall19/cos484/lectures/pytorch.pdf)

##  Get familiar with Weights & Biases
* [Official Guide](https://wandb.ai/site/tutorials)
* Understand how to generate figures, manage data tables, use filter and group tools, and download data using wandb API.

## Run Python in Anaconda on UVA CS server
* Be sure to run Python in a specialized virtual environment. Otherwise, dependencies will be easily messed up. 
* [Anaconda Guide](https://www.anaconda.com/)
* [UVA CS server Guide](https://www.cs.virginia.edu/wiki/doku.php?id=start)
  

## Run Python on the server using Slurm
* [Slurm Guide](https://slurm.schedmd.com/documentation.html)
* [Example from Stanford](https://rcpedia.stanford.edu/topicGuides/jobArrayPythonExample.html)
* Reference script
```
#!/bin/bash

# Example of running Python script with a job array

#SBATCH --job-name=stswyuhu
#SBATCH --exclude=adriatic[01-04],cheetah01,cheetah02,cheetah03,jaguar01,jaguar02,jaguar04,jaguar05,jaguar06,lotus,lynx[01-02] # This line exludes high-performance GPUs. Because we do not use GPU on most tasks, we leave them to other people.
#SBATCH --partition=nolim,main,gnolim,gpu
#SBATCH --gpus-per-node=0                # 0 GPU per task. Use GPU only when you have more than 10^5 data to intensively parallel compute.
#SBATCH --cpus-per-task=4                # 4 CPU cores per task
#SBATCH --mem=4G   #Adjust based on demands.
#SBATCH --time=4-00:00:00
#SBATCH --output hello.out            
#SBATCH --ntasks 1                   

srun wandb agent rl_research/grid_ROA/stswyuhu
```


## Be able to run multiple tasks at the same time on the server with different parameters.
* Achieve this with wandb and Slurm.
* Be sure to leave enough computational power (especially GPUs) to others. The above script has "--exclude" to leave high-performance GPUs as RL experiments we conduct usually do not need GPUs.

## Reference Code Repo
* [CleanRL](https://github.com/vwxyzjn/cleanrl): Excellent and systematic guide to start RL programming.
 
