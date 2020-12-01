=====================
Fed4FIRE+ Experiments
=====================

The tutorial gives the detailed steps required to start and run the Fed4FIRE+ experiments and run the asvin image for simulating virtual edge devices with asvin API stack.

Requirements
############
1. jFed Experimenter Toolkit
2. ESpec generator
3. asvin API stack image
4. Grafana json file


Getting Started
###############

1. Starting the Experiment
        To start and monitor the Fed4FIRE experiments we use jFed Experimenter Toolkit. It is a user-friendly tool with simple and self explainatory interface.
        Login to the experimenter tool with Fed4FIRE account. Then experiments can be created and started by utilizing the drag and drop options to form network of nodes. Or the Experiment Specifications (ESpec) can be generated and uploaded in the toolkit to start the experiment.

        .. image:: ../images/Fed4FIRE/jFed_experiment.JPG
                :width: 350pt
                :align: center

        To create the ESpec, ESpec Generator tool is needed. **https://github.ugent.be/jlemaes/generate-espec**. 
        This tool can be used for generated ESpec for only Virtual Wall1 and Wall2 testbeds.
        It includes all the installation scripts of Kubernetes cluster, influx DB and other tools which are required for the stress test of our platform.

        .. image:: ../images/Fed4FIRE/espec_generator.JPG
                :width: 300pt
                :align: center

        Using the generated ESpec, one can start the experiment on Fed4FIRE testbeds. The experiment will have a master node, influxdb node, and all other worker nodes.
        If ESpec is generated for 5 nodes, then the experiment will have a master node, influxdb node, and 5 worker nodes running.

        **To reserver more than 15 nodes in an experiment, it is always good to inform the Fed4FIRE correspondent before initiating**

2. Deploying asvin API stack image

        The example python code running the API stack for simulating the edge device is provided in 

3. Monitoring the Experiment





    



