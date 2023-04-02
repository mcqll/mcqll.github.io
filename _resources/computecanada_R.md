---
layout: resourcepost
title: Compute Canada tutorial
description: Steps to get set up to fit R models on a cluster
author: Jacob and Connie
date: 26 November 2021
---

_Note: As of April 1 Jan 2022, **Compute Canada** became **Digital Research Alliance of Canada**._

This is a short tutorial to test using Compute Canada (aka Digital Research Alliance of Canada) for R computing with `brms` and `mgcv`. See also [this blog post](https://medium.com/the-nature-of-food/how-to-run-your-r-script-with-compute-canada-c325c0ab2973). For complete information see the extensive [technical documentation](https://docs.alliancecan.ca/wiki/Technical_documentation) on the official wiki.

## 1. Log in and install modules

1. Make sure you have an active account with [CCDB](https://ccdb.computecanada.ca/).

2. SSH in to a Compute Canada login node (with `-Y` for trusted X11 forwarding):
  ```bash
  ssh -Y ${username}@beluga.computecanada.ca
  ```
  where `${username}` is your Compute Canada username (not your CCI).  You could also replace `beluga` with another Compute Canada cluster name, if you're not in Quebec (see [here](https://alliancecan.ca/en/services/advanced-research-computing/accessing-resources/resource-allocation-competition/available-resources)).
  You will be prompted to enter a password. Note: if you have entered your public ssh key on the Alliance's website, you won't need a password (you can generate a key, or if you have a key on your computer already it's probably at `~/.ssh/id_rs.pub`; you can paste the contents of that file on the Compute Canada website at _My Account > Manage SSH Keys_, and press 'Add Key' and then you won't need to use a password to login).

3. Once you're logged into, you will see a welcome message and a bash prompt that looks something like `[username@beluga3 ~]$`.  You now need to load the necessary modules.  Use the following command.  Note: the bioconductor module is necessary for `brms` to work.
  ```bash
module load gcc/9.3.0 r-bundle-bioconductor/3.14 r/4.1.2
```
  You may get messages about modules being replaced/reloaded, which you can ignore.

4. Start an R session
```bash
R
```

5. Once R is started, install the R packages you want to use. 
```R
install.packages(c("tidyverse", "mgcv", "brms"),
                    repos = "https://utstat.toronto.edu/cran/")
```
  You may get a warning message saying `'lib = " ... "' is not writeable`, asking if I want to use a personal library (respond `y`), and then asking if you want to create the personal library directory to install packages into (respond `y` again).
  The packages will install (and take some time, like a half-hour).  If this succeeds, you should get a message like: `The downloaded source packages are in ‘/tmp/.../downloaded_packages’`, and no warnings.

6. Quit R with `q()`. You will return to the bash prompt on the login node.

Now it should be all set.  

Note: *Steps 1-4 you'll use anytime you use the cluster for an R project. You should only have to run step 5 once ever (the packages will remain installed for you for all future sessions on Béluga).  If you need other packages in the future, just open R and `install.packages` as in step 5 to install them too.*

## 2. Test fitting models in R

When you ssh into the cluster, you start out in a "login node" (you'll see the name of the particular node your on at the prompt. It will probably have a name like `beluga3`). 

**Important**: _A login node is just your entry point to the cluster, it is not where you run your code. Fitting models on a login node will be slow (probably not faster your laptop), and more importantly, it can make the login node unusable to other users! Don't be rude!_  To run things, you must do one of the following:

- Run things interactively. This is for data exploration and interactive debugging of a script, for instance. See **Section 2.1** below.
- Use a job script to do batch submission. This is for large computational tasks, like fitting your heavy-duty models. In general, this is the default way Compute Canada expects you'll use the cluster. See **Section 2.2** below.

### 2.1 Running things interactively
(skip this section if you just want to submit jobs to be run)

1. Start in a cluster login node, as above. Then, request an interactive session using the `salloc` command:

   ```bash
   salloc --x11 --time=1:0:0 --ntasks=4 --mem-per-cpu=4GB --account=${ACCOUNT} 
   ```
   this example requests four CPU cores for one hour, with 4GB of RAM per CPU. `${ACCOUNT}` is the name of the account you want to use. 

    - If you misspell or don't specify the account, you'll get a helpful error message telling you what accounts you are a member of. Choose one of them. 

    - The `--x11` flag is necessary only if you want to do interactive plotting. 

   After running the `salloc` command, you'll see some messages like the below. It may take a minute, but once the resources you requested are allocated you, will see a bash prompt, like `[username@blg8610 ~]$`

2. Now you're on a the "compute node".  Start up `R`, where you can interactively run Test 1 and Test 2, below.

3. After running the tests below, `q()` to quit R, and then `exit` to relinquish  the compute node (you'll be returned to the login node).

#### Test 1: using `mgcv`

Let's test fitting a GAM.

```r
library(mgcv)
dat <- gamSim(1,n=400,dist="normal",scale=2)
b <- gam(y~s(x0)+s(x1)+s(x2)+s(x3),data=dat)
summary(b)
```
This should fit the model and print the summary.

and (if you used `-x11` flag to `salloc` when you requested the allocation), test plotting the model, like so

```R
plot(b, select=1)
```

This should use X11 forwarding to show a plot of the fit smooth for `s(x0)`. 

#### Test 2: using `brms`

Let's test fitting a Bayesian regression model with `brm()`

```R
library(brms)
data("kidney")
fit1 <- brm(
  formula = time | cens(censored) ~ age * sex + disease
  + (1 + age|patient),
  data = kidney, family = lognormal(),
  prior = c(set_prior("normal(0,5)", class = "b"),
  set_prior("cauchy(0,2)", class = "sd"),
  set_prior("lkj(2)", class = "cor")),
  warmup = 1000, iter = 2000, chains = 4, cores = 4,
  control = list(adapt_delta = 0.95))
summary(fit1)
```

This should compile the Stan program and fit the model, and print a summary.  Works for me.  Also test plotting with `plot(fit1, select=1)`.  Note that setting `cores=4` tells the `brms` to make use of the multiple cores you requested.

When you're done, you can quit R and exit the compute node (also, be aware that you'll be kicked out automatically after the time you requested has been used up).

### 2.2 Running things in a job script

Start in a login node. 

Let's make an R script that does the same two tests above. Name the script `Rtest.R`, and save it in the user directory of the login node (that'll be accessible from the compute nodes too), by running the following:

```bash
cd;
cat > Rtest.R << EOF
## testing mgcv
library(mgcv)
dat <- gamSim(1,n=400,dist="normal",scale=2)
gam1 <- gam(y~s(x0)+s(x1)+s(x2)+s(x3),data=dat)
summary(gam1)
png(file="Rtest-plots/gam1.png", width=600, height=500)
plot(gam1, select=1)
dev.off()

## testing brms
library(brms)
data("kidney")
fit1 <- brm(
  formula = time | cens(censored) ~ age * sex + disease
  + (1 + age|patient),
  data = kidney, family = lognormal(),
  prior = c(set_prior("normal(0,5)", class = "b"),
  set_prior("cauchy(0,2)", class = "sd"),
  set_prior("lkj(2)", class = "cor")),
  warmup = 1000, iter = 2000, chains = 4, cores = 4,
  control = list(adapt_delta = 0.95))
summary(fit1)
png(file="Rtest-plots/fit1.png", width=600, height=500)
plot(fit1, select=1)
dev.off()
EOF
```

Now make a job script, and save it as `Rtest-job.sh` in the home directory too:

```bash
cd;
cat > Rtest-job.sh << EOF
#!/bin/bash
#SBATCH --account=${ACCOUNT}
#SBATCH --time=00:15:00
#SBATCH --mem-per-cpu=4G
#SBATCH --cpus-per-task=8
#SBATCH --job-name=Rtest
#SBATCH --output=%x-%j.out
#SBATCH --mail-user=${EMAIL}
#SBATCH --mail-type=ALL
module load gcc/9.3.0 r-bundle-bioconductor/3.14 r/4.1.2
Rscript Rtest.R
EOF
```

This requests 15 minutes of time on a compute node with 8 CPUs, and 4GB of RAM per each. `${ACCOUNT}` should be the account name you want to use. Set `${EMAIL}` to your email address to be alerted when the job starts/finishes/fails (optional). The `--output` flag specifies the format for the output file you'll get when your job terminates.  In this case, we're setting it to be `Rtest-jobnumber.out`.

Make a directory for the test plots to be put in:

```bash
mkdir Rtest-plots
```

Submit the job to be scheduled.

```bash
sbatch Rtest-job.sh
```

You'll see something like `Submitted batch job 27701226`.
You can use `squeue` or `sq` to see the list of queued jobs.  Hopefully yours will be run soon.

When finished, the following outputs will be in the home directory

- An out file with a name like `Rtest-27701226.out`, containing the stdout stuff from the R script (and if the job crashed, useful info may be in there).
- Two plots, in the `test-plots/` directory.

## 3. Transferring files

Beyond just running a simple test like above, you'll likely need to transfer datasets and scripts to the cluster before running things.

To  transfer files between your local machine and your home directory on Béluga

- you can use [`scp`](https://linux.die.net/man/1/scp) or [`rsync`](https://linux.die.net/man/1/rsync) to copy files via SSH (or on Windows, equivalent tools). For example, to copy a script from your laptop to your home directory on Béluga, run something like the following (on your local terminal):
  ```bash
  scp /path/to/myscript.R ${username}@beluga.computecanada.ca:/home/${username}/
  ```
  You can use it similarly to copy output files back to your local machine.
- for large/multiple files, the Alliance [recommends the _Globus_ system](https://docs.alliancecan.ca/wiki/Transferring_data).
