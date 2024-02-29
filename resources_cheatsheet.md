# Resources Cheetsheet #
Quick guide to understanding the resource demands of your slurm scripts. If your script, or its `sbatch` arguments, is borrowed, then it might be worth confirming that the `sbatch` arguments are correct.

A more detailed reference for `sbatch` arguments can be found in the [slurm docs](https://slurm.schedmd.com/sbatch.html)

### Important terms ###
Task: In computer terms, this is a process, not a thread. If those terms are unfamilar, a command that you run in your terminal that takes over the command line is a task (e.g. `sleep 10` or `srun sleep 10`). You can launch multiple tasks at once that would ordinarily take over the terminal (e.g. `srun sleep 10 & srun sleep 12`). If launched this way, the `&` means they will run in parallel, and slurm is mostly concerned with this possibility. If you don't see an `srun` or an `&`, then you probably only need one task.

Node: A computer to connect to. An HPC login node or an AWS instance are both nodes.

### Important CPU Commands ###

`-n`, `--ntasks`: Number of tasks you will launch in parallel.

`-c`, `--cpus-per-task`: Number of CPUs per task you're launching. The total number of CPUS will be `cpus-per-task * ntasks`.

### Important RAM Commands ###

`--mem`: Minimum RAM on each node. If you're consolidating to one instance, multiply this by the number of nodes to get your RAM requirement.

`--mem-per-cpu`: Minimum RAM per CPU allocated. Total RAM will be `mem-per-cpu * cpus-per-task * ntasks`