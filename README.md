# lincs_docker_scripts
##Shell script pipelines using LINCS docker containers

###Summary

The shell scripts are derived from python based pipelines for processing UMI RNAseq data. These scripts now call docker images from Biodepot to ensure reproducibility. 

Three sets of shell scripts have been provided:

####1. dockerScripts_orig
  Re-creates the original python/R pipeline.
####2. dockerScripts_cpp_orig
  The python scripts used in the alignment phase have been rewritten in C++ for greater speed and are now multi-threaded. The analysis phase is the same R pipeline. The results are the same when using this or the dockerScripts_orig.
####3. dockerScripts_cpp
 Various improvements have been made upon the original implementation. Reads are separated by barcodes before alignment  and counting to increase speed, reduce memory requirments and allow for greater parallelism. UMIs can now grouped by mapping position as well as the mapped gene for determining whether the read is artifactual.

In each directory there are 3 scripts:
####1. runAll.sh
  Runs the docker containers. Once docker is installed, the containers will be pulled the first time and run. Parameters, such as file locations and sample ids are provided to this script.
####2. run-alignment-analysis.sh 
  This is from the original pipeline and contains more parameters. It is run inside the container.
####3. myRun.sh
  Provided as an example of the parameters that would be fed to runAll.sh
