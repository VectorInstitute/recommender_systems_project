# Setting up your Environment
Log on to the Vector cluster using the following command on your terminal  
`ssh <USER_ID>@v.vectorinstitute.ai`

Load Python v3.7 <= 3.7.13  
`module load python/3.7.9`

Confirm that the correct module has been loaded  
`which python`

You can use the following command to create the environment in the SSD scratch space  
`python -m venv /scratch/ssd004/scratch/<USER_ID>/<ENV_NAME>`

Activate your environment using the following command  
`source /scratch/ssd004/scratch/<USER_ID>/<ENV_NAME>/bin/activate`

# Running the Tutorial
First install jupyter notebook  
`pip install jupyter`

Next, send a slurm job by first creating a file  
`vim <JOB_NAME>.slrm`

Paste the following contents into the file
```
#!/bin/bash
#SBATCH -p t4v2
#SBATCH --qos=normal
#SBATCH --gres=gpu:1
#SBATCH -c 4
#SBATCH --mem=32G
#SBATCH --job-name=<JOB_NAME>
#SBATCH --output=jupyter_notebook_%j.log

# activate the environment
source /scratch/ssd004/scratch/<USER_ID>/<ENV_NAME>/bin/activate

jupyter notebook --ip 0.0.0.0 --port 2120
```

Make sure you fill in the `<JOB_NAME>`, `<USER_ID>`, `<ENV_NAME>` fields.

Run the job  
`sbatch <JOB_NAME>.slrm`

You can confirm that the job is running  
`squeue -u <USER_ID>`

To cancel a job, run  
`scancel <JOB_ID>`

Open the jupyter_notebook_%j.log file, where j is the JOBID  
`cat jupyter_notebook_%<JOB_ID>.log`

You can find the port and gpu number in the output log
```
[I 17:31:52.310 NotebookApp] Serving notebooks from local directory: /ssd003/home/sheen
[I 17:31:52.310 NotebookApp] Jupyter Notebook 6.4.12 is running at:
[I 17:31:52.310 NotebookApp] http://gpu061.cluster.local:2120/?token=74adbfd9d6295d5cd948c09731062fea6ecc62825a7ab36f
[I 17:31:52.310 NotebookApp]  or http://127.0.0.1:2120/?token=74adbfd9d6295d5cd948c09731062fea6ecc62825a7ab36f
[I 17:31:52.310 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
[W 17:31:52.321 NotebookApp] No web browser found: could not locate runnable browser.
[C 17:31:52.321 NotebookApp] 
    
    To access the notebook, open this file in a browser:
        file:///ssd003/home/sheen/.local/share/jupyter/runtime/nbserver-11478-open.html
    Or copy and paste one of these URLs:
        http://gpu061.cluster.local:2120/?token=74adbfd9d6295d5cd948c09731062fea6ecc62825a7ab36f
     or http://127.0.0.1:2120/?token=74adbfd9d6295d5cd948c09731062fea6ecc62825a7ab36f
```

In the example above, the gpu number is gpu061 amd the port is 2120

Open another terminal and run the following command  
`ssh <USER_ID>@v.vectorinstitute.ai -NL <PORT>:<GPU#>:<PORT>`

Open a browser with the jupyter notebook link found in the log file or run `http://127.0.0.1:port/`

To install the dependencies needed to run the notebook, go to the folder and run  
`pip install -r requirements.txt`
