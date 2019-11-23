# 2019-BigData_NPPs
Big Data for NPPs Workshop, The Ohio State University Columbus, OH - Dec. 10-11, 2019

Put "framework/CodeInterfaces/Serpent" directory to your raven installation directory. 

Installation: Just follow the instructions given in the user manual or website of Raven. 


Issue-1: There is a bug in the latest Raven version when running an input file on a cluster. 
Solved: Modify your job file in the following way:

from "aprun -n 1 -d 32 raven_framework <input_file>"
to "aprun -n 1 -d 32 /bin/bash raven_framework <input_file>"

Issue-2: When summiting a job using job.pbs file,following error is emerging

(    1.02 sec) DATABASE HDF5            : Message         -> Database is located at: /mnt/c/scratch/sciteam/turkmen/raven/projects/DatabaseStorage/hdf5_database.h5
(    1.03 sec) SIMULATION               : Message         -> -- Beginning step feedbackCalc of type: MultiRun                    --
(    1.04 sec) STEP MULTIRUN            : Message         -> ***  Beginning initialization ***
(    1.06 sec) Grid                     : Message         -> No restart for Grid
(    1.06 sec) GRID ENTITY              : Message         -> Starting initialization of grid 
(    1.06 sec) GRID ENTITY              : Message         -> Grid initialized...
(    1.07 sec) Code                     : Message         -> job "1" submitted!
(    1.07 sec) STEP MULTIRUN            : Message         -> ***    Initialization done    ***
(    1.07 sec) STEP MULTIRUN            : Message         -> ***       Beginning run       ***
Execution Command: [('parallel', 'aprun -n 1 -d 1   /projects/sciteam/bahg/serpent30/src/sss2  msr_channel_design_feedback.inp  ')]
(    1.08 sec) Code                     : Message         -> Execution command submitted: aprun -n 1 -d 1   /projects/sciteam/bahg/serpent30/src/sss2  msr_channel_design_feedback.inp    
(  283.58 sec) Code                     : Message         ->  Process Failed aprun -n 1 -d 1   /projects/sciteam/bahg/serpent30/src/sss2  msr_channel_design_feedback.inp     returnCode 1
(  283.58 sec) Code                     : Message         -> 'socket_connect_unix failed: 15137
socket_connect_unix failed: 15137
socket_connect_unix failed: 15137
qstat: cannot connect to server (null) (errno=15137) could not connect to trqauthd
qstat: Error (15137 - could not connect to trqauthd) 
craylog: WARNING: log tmp dir /var/spool/cray/llm is not writable
aprun: Unable to contact apsys
aprun: Exiting due to errors. Application aborted
getBatchJobId: error opening /ufs/alps_shared/reservations, errno No such file or directory
craylog: ERROR: discarding log message: <150>1 2019-11-22T20:54:53.620160-06:00 c14-4c2s4n3 aprun 13472 p0-20190705t150933 [alps_msgs@34] apid=none, Error, user=59011, batch_id=unknown, Unable to contact apsys
'
(  283.58 sec) Job Handler              : Message         ->  Process Failed <Runners.SharedMemoryRunner.SharedMemoryRunner object at 0x2aaabc574250> internal returnCode -1
(  283.58 sec) Code                     : Message         -> job "2" submitted!
Application 82238497 exit codes: 139
Application 82238497 resources: utime ~22s, stime ~13s, Rss ~141124, inblocks ~317359, outblocks ~6853

