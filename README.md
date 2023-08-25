# Reinforcement Learning Experiment Guide

## Get familiar with PyTorch

* [Official Guide](https://pytorch.org/tutorials/)
* [Quick Recap](https://www.cs.princeton.edu/courses/archive/fall19/cos484/lectures/pytorch.pdf)

##  Get familiar with Weights & Biases
* [Official Guide](https://wandb.ai/site/tutorials)
* Understand how to generate figures, manage data tables, use filter and group tools, and download data using wandb API.

## Run Python in Anaconda on UVA CS server
* Be sure to run python in a specialized virtual environment. Otherwise, dependencies will be easily messed up. 
* [Anaconda Guide](https://www.anaconda.com/)
* [UVA CS server Guide](https://www.cs.virginia.edu/wiki/doku.php?id=start)
  

## Run python on the server using Slurm
* [Slurm Guide](https://slurm.schedmd.com/documentation.html)
* [Example from Stanford](https://rcpedia.stanford.edu/topicGuides/jobArrayPythonExample.html)
* Reference script
```
#!/bin/bash

# Example of running python script with a job array

#SBATCH --job-name=stswyuhu
#SBATCH --exclude=adriatic[01-04],cheetah01,cheetah02,cheetah03,jaguar01,jaguar02,jaguar04,jaguar05,jaguar06,lotus,lynx[01-02] # This line exludes high-performance GPU. Because we do not use GPU on most tasks, we should courtesy left them to other people.
#SBATCH --partition=nolim,main,gnolim,gpu
#SBATCH --gpus-per-node=0
#SBATCH --cpus-per-task=4                 # 4 CPU core per task
#SBATCH --mem=4G   #Adjust based on demands
#SBATCH --time=4-00:00:00
#SBATCH --output hello.out            
#SBATCH --ntasks 1                   

srun wandb agent rl_research/grid_ROA/stswyuhu
```


## Be able to run distributed training (at least 100 tasks in parallel) on the server.
* Achieve this with wandb and Slurm.
* Be sure to leave enough computational power (especially GPU) to others. Use at most 1600 cores or less depends on the crowdness of the server.

## Reference Code Repo
* [CleanRL](https://github.com/vwxyzjn/cleanrl): Excellent and systematic guide to start RL programming.
 
