# Laptop_to_Cluster
Basic HPC cluster using Ansilbe,Vagrant and OpenHPC
# How to run
1.Install Vagrant https://www.vagrantup.com/ (note that you might need to install virtual box or another VM provider )
2.Clone this repository
3.Generate ssh keys for your machines by running the gensshkeys.sh
4.Run Vagrant with the command vagrant up, this will also launch the ansible playbook which will set up our cluster.Note that it may take a long time to set up your cluster in the first run.
5.You can now run the command vagrant ssh head to log in to the head node or vagrant ssh fe1 to log in to the frontend
6.Run sinfo in the head or frontend to see the state of your node , you might need to wake them up in case they're down.
7.You can now start using your cluster to run jobs using srun --mpi=pmi2
