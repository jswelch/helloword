List of options for the bjobs command.

-A\
Displays summarized information about job arrays.\
-a\
Displays information about jobs in all states, including jobs that
finished recently.\
-aff\
Displays information about jobs with CPU and memory affinity resource
requirements for each task in the job.\
-app\
Displays information about jobs submitted to the specified application
profile.\
-aps\
Displays absolute priority scheduling (APS) information for pending jobs
in a queue with APS_PRIORITY enabled.\
-cname\
In IBM® Spectrum LSF Advanced Edition, includes the cluster name for
execution cluster hosts in the output.\
-d\
Displays information about jobs that finished recently.\
-data\
Displays the data file requirements for the job. The -data option acts
as a filter to show only jobs with data requirements. For example, the
option lists jobs that are submitted with -data. The option also lists
files or data requirement tags that are requested by the job.\
-env\
Displays the environment variables in the job submission environment for
the specified job.\
-fwd\
In LSF multicluster capability job forwarding mode, filters output to
display information on forwarded jobs.\
-G\
Displays jobs associated with the specified user group.\
-g\
Displays information about jobs attached to the specified job group.\
-gpu\
bjobs -l -gpu shows the following information on GPU job allocation:\
-hms\
Displays times in the customized output in hh:mm:ss format.\
-hostfile\
Displays information about a job submitted with a user-specified host
file.\
-J\
Displays information about jobs or job arrays with the specified job
name.\
-Jd\
Displays information about jobs with the specified job description.\
-json\
Displays the customized output in JSON format.\
-Lp\
Displays jobs that belong to the specified LSF License Scheduler
project.\
-l\
Long format. Displays detailed information for each job in a multi-line
format.\
-m\
Displays jobs dispatched to the specified hosts.\
-N\
Displays information about done and exited jobs, also displays the
normalized CPU time consumed by the job.\
-noheader\
Removes the column headings from the output.\
-o\
Sets the customized output format.\
-P\
Displays jobs that belong to the specified project.\
-p\
Displays pending jobs, together with the pending reasons that caused
each job not to be dispatched during the last dispatch turn.\
-pe\
Displays pending jobs that are eligible for scheduling.\
-pei\
Displays pending jobs divided into lists of jobs that are eligible for
scheduling and ineligible for scheduling.\
-pi\
Displays pending jobs that are ineligible for scheduling.\
-plan\
Filter for the PEND jobs that have an allocation plan. See
ALLOCATION_PLANNER (lsb.params).\
-prio\
Displays the detailed absolute priority scheduling (APS) factor values
for all pending jobs.\
-psum\
Displays a summarized version of reasons for pending jobs.\
-q\
Displays jobs in the specified queue.\
-r\
Displays running jobs.\
-rusage\
Displays jobs requesting the resources specified by the filter.\
-s\
Displays suspended jobs, together with the suspending reason that caused
each job to become suspended.\
-script\
Displays the job script for the specified job from the LSF info
directory.\
-sla\
Displays jobs belonging to the specified service class.\
-ss\
Displays summary information for LSF Session Scheduler tasks.\
-sum\
Displays summary information about unfinished jobs.\
-U\
Displays jobs that are associated with the specified advance
reservation.\
-UF\
Displays unformatted job detail information.\
-u\
Displays jobs that were submitted by the specified users or user
groups.\
-W\
Provides resource usage information for: PROJ_NAME, CPU_USED, MEM, SWAP,
PIDS, START_TIME, FINISH_TIME.\
-WF\
Displays an estimated finish time for running or pending jobs. For done
or exited jobs, displays the actual finish time.\
-WL\
Displays the estimated remaining run time of jobs.\
-WP\
Displays the current estimated completion percentage of jobs.\
-w\
Wide format. Displays job information without truncating fields.\
-X\
Displays noncondensed output for host groups and compute units.\
-x\
Displays unfinished jobs that have triggered a job exception (overrun,
underrun, idle, runtime_est_exceeded).\
job_id\
Specifies the jobs or job arrays that bjobs displays.\
-h\
Displays a description of the specified category, command option, or
sub-option to stderr and exits.\
-V\
Prints LSF release version to stderr and exits.
