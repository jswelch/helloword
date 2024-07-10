bjobs

Displays and filters information about LSF jobs. Specify one or more job
IDs (and, optionally, an array index list) to display information about
specific jobs (and job arrays).

Synopsis\
bjobs \[options\] \[job_ID \| "job_ID\[index_list\]" ... \]\
bjobs -h\[elp\] \[all\] \[description\] \[category_name ...\]
\[-option_name ...\]\
bjobs -V\
Categories and options\
Use the keyword all to display all options and the keyword description
to display a detailed description of the bjobs command. For more details
on specific categories and options, specify bjobs -h with the name of
the categories and options.

Filter specific types of jobs: -A, -aff, -app, -aps, -bucket, -data,
-env, -fwd, -g, -G, -J, -Jd, -Lp, -m, -N, -P, -plan, -prio, -psum, -q,
-rusage, -script, -sla, -ss, -u.\
Control the bjobs display format: -aff, -cname, -hostfile, -l, -N,
-noheader, -o, -psum, -sum, -UF, -w, -W, -WF, -WL, -WP, -X.\
Display specific job states: -a, -d, -N, -p, -pe, -pei, -pi, -psum, -r,
-s, -sum, -x.

Description\
By default, displays information about your own pending, running, and
suspended jobs.

List of options for the bjobs command.\

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

-A\
Displays summarized information about job arrays.

Categories\
filter

Synopsis\
bjobs -A\
Description\
If you specify job arrays with the job array ID, and also specify -A, do
not include the index list with the job array ID.

You can use -w to show the full array specification, if necessary.

-a\
Displays information about jobs in all states, including jobs that
finished recently.

Categories\
state

Synopsis\
bjobs -a\
Description\
The finished jobs that -a displays are those that finished within an
interval specified by CLEAN_PERIOD in lsb.params (the default period is
1 hour).

Use -a with -x option to display all jobs that have triggered a job
exception (overrun, underrun, idle).

Examples\
bjobs -u all -a

Displays all jobs of all users.

-aff\
Displays information about jobs with CPU and memory affinity resource
requirements for each task in the job.

Categories\
filter, format

Synopsis\
bjobs -l \| -UF \[-aff\]\
Conflicting options\
Use only with the -l or -UF option.

Description\
If the job is pending, the requested affinity resources are displayed.
For running jobs, the effective and combined affinity resource
allocation decision made by LSF is also displayed, along with a table
headed AFFINITY that shows detailed memory and CPU binding information
for each task, one line for each allocated processor unit. For finished
jobs (EXIT or DONE state), the affinity requirements for the job, and
the effective and combined affinity resource requirement details are
displayed.

Use bhist -l -aff to show the actual affinity resource allocation for
finished jobs.

-app\
Displays information about jobs submitted to the specified application
profile.

Categories\
filter

Synopsis\
bjobs -app application_profile_name\
Description\
You must specify an existing application profile.

Examples\
bjobs -app fluent

Displays all jobs belonging to the application profile fluent.

-aps\
Displays absolute priority scheduling (APS) information for pending jobs
in a queue with APS_PRIORITY enabled.

Categories\
format

Synopsis\
bjobs -aps\
Description\
The APS value is calculated based on the current scheduling cycle, so
jobs are not guaranteed to be dispatched in this order.

Pending jobs are ordered by APS value. Jobs with system APS values are
listed first, from highest to lowest APS value. Jobs with calculated APS
values are listed next ordered from high to low value. Finally, jobs not
in an APS queue are listed. Jobs with equal APS values are listed in
order of submission time. APS values of jobs not in an APS queue are
shown with a dash (-).

If queues are configured with the same priority, bjobs -aps may not show
jobs in the correct expected dispatch order. Jobs may be dispatched in
the order the queues are configured in lsb.queues. You should avoid
configuring queues with the same priority.

For resizable jobs, -aps displays the latest APS information for running
jobs with active resize allocation requests. LSF handles the dynamic
priority for running jobs with active resize requests. The displayed job
priority can change from time to time.

-d\
Displays information about jobs that finished recently.

Categories\
state

Synopsis\
bjobs -d\
Description\
The finished jobs that -d displays are those that finished within an
interval specified by CLEAN_PERIOD in lsb.params (the default period is
1 hour).

Examples\
bjobs -d -q short -m hostA -u user1

Displays all the recently finished jobs submitted by user1 to the queue
short, and executed on the host hostA.

-data\
Last Updated: 2024-01-08\
Displays the data file requirements for the job. The -data option acts
as a filter to show only jobs with data requirements. For example, the
option lists jobs that are submitted with -data. The option also lists
files or data requirement tags that are requested by the job.

Categories\
filter

Synopsis\
bjobs -data \[jobID\]\
Conflicting options\
Do not use the -data option with the following options: -A, -sum.

Description\
The following units are displayed for file size:\
nnn B if file size is less than 1 KB\
nnn\[.n\] KB if file size is less than 1 MB\
nnn\[.n\] MB if file size is less than 1 GB\
nnn\[.n\] GB if file size is 1 GB or larger\
nnn\[.n\] EB if file size is 1 EB or larger\
A dash (-) indicates that a size or modification time stamp value is not
available.

For jobs with data requirements that are specified as tags, the -data
option shows the tag names.

Examples\
bjobs -data 1962\
JOBID USER STAT QUEUE FROM_HOST EXEC_HOST JOB_NAME SUBMIT_TIME\
1962 user1 PEND normal hostA \*p 1000000 Sep 20 16:31\
FILE SIZE MODIFIED\
datahost:/proj/user1/input1.dat 500 M Jun 27 16:37:52\
datahost:/proj/user1/input2.dat 100 M Jun 27 16:37:52\
datahost:/proj/user1/input3.dat - -

For jobs with data requirements specified as tags, the -data option
shows the tag names:\
bjobs -data 1962\
JOBID USER STAT QUEUE FROM_HOST EXEC_HOST JOB_NAME SUBMIT_TIME\
1962 user1 PEND normal hostA \*p 1000000 Sep 20 16:31\
TAG\
OUTPUT_FROM_J1\
OUTPUT_FROM_J2

For jobs with a folder as data requirement, the -data shows the folder
name. Individual files in the folder are not shown. For example, for the
following data requirement\
bsub -data "/home/user/folder1/" myjob

the -data option shows the folder name /home/user/folder1/:\
bjobs -data 44843\
JOBID USER STAT QUEUE FROM_HOST EXEC_HOST JOB_NAME SUBMIT_TIME\
44843 user1 PEND normal hosta myjob May 10 14:42

FILE SIZE MODIFIED\
hosta:/home/user1/folder1/ 4 KB May 9 09:53

-env\
Last Updated: 2024-01-08\
Displays the environment variables in the job submission environment for
the specified job.

Categories\
filter

Synopsis\
bjobs -env\
Conflicting options\
Do not use with any other bjobs command options.

Description\
You must specify a single job ID or job array element ID when using the
-env command option. Multiple job IDs are not supported.

When using the LSF multicluster capability and a lease job contains
application-specific environment variables, the -env command option
cannot display these application-specific environment variables when
issued from the remote cluster.

-fwd\
In LSF multicluster capability job forwarding mode, filters output to
display information on forwarded jobs.

Categories\
filter

Synopsis\
bjobs -fwd\
Conflicting options\
Do not use with the following options: -A, -d, -sla, -ss, -x.

Description\
In LSF multicluster capability job forwarding mode, filters output to
display information on forwarded jobs, including the forwarded time and
the name of the cluster to which the job was forwarded. -fwd can be used
with other options to further filter the results. For example, bjobs
-fwd -r displays only forwarded running jobs.

To use -x to see exceptions on the execution cluster, use bjobs -m
execution_cluster -x.

Examples\
% bjobs -fwd\
JOBID USER STAT QUEUE EXEC_HOST JOB_NAME CLUSTER FORWARD_TIME\
123 lsfuser RUN queue1 hostC sleep 1234 cluster3 Nov 29 14:08

-G\
Last Updated: 2024-01-08\
Displays jobs associated with the specified user group.

Categories\
filter

Synopsis\
bjobs -G user_group\
Conflicting options\
Do not use with the -u option.

Description\
Only displays jobs associated with a user group submitted with bsub -G
for the specified user group. The --G option does not display jobs from
subgroups within the specified user group. Jobs associated with the user
group at submission are displayed, even if they are later switched to a
different user group.

You can only specify a user group name. The keyword all is not supported
for -G.

-g\
Last Updated: 2024-01-08\
Displays information about jobs attached to the specified job group.

Categories\
filter

Synopsis\
bjobs -g job_group_name\
Description\
Use -g with -sla to display job groups attached to a time-based service
class. Once a job group is attached to a time-based service class, all
jobs submitted to that group are subject to the SLA.

bjobs -l with -g displays the full path to the group to which a job is
attached.

Examples\
bjobs -g /risk_group\
JOBID USER STAT QUEUE FROM_HOST EXEC_HOST JOB_NAME SUBMIT_TIME\
113 user1 PEND normal hostA myjob Jun 17 16:15\
111 user2 RUN normal hostA hostA myjob Jun 14 15:13\
110 user1 RUN normal hostB hostA myjob Jun 12 05:03\
104 user3 RUN normal hostA hostC myjob Jun 11 13:18

To display the full path to the group to which a job is attached, run
bjobs -l -g:

bjobs -l -g /risk_group\
Job \<101\>, User `<user1>`{=html}, Project

<default>

, Job Group `</risk_group>`{=html},\
Status `<RUN>`{=html}, Queue `<normal>`{=html}, Command
`<myjob>`{=html}\
Tue Jun 17 16:21:49 2009: Submitted from host `<hostA>`{=html}, CWD
`</home/user1;
Tue Jun 17 16:22:01 2009: Started on <hostA>`{=html};\
...

-gpu\
bjobs -l -gpu shows the following information on GPU job allocation:

Categories\
filter

Synopsis\
bjobs -l \| -UF \[-gpu\]\
Conflicting options\
Use only with the -l or -UF option.

Description\
Host Name\
The name of the host.\
GPU IDs on the host\
Each GPU is shown as a separate line.\
TASK and ID\
List of job tasks and IDs using the GPU (separated by comma if used by
multiple tasks)\
MODEL\
Contains the GPU brand name and model type name.\
MTOTAL\
The total GPU memory size.\
GPU Compute Capability\
MRSV\
GPU memory reserved by the job\
SOCKET\
socket ID of the GPU located at\
NVLINK\
Indicates if the GPU has NVLink connections with other GPUs allocated
for the job (ranked by GPU ID and including itself). The connection flag
of each GPU is a character separated by "/" with the next GPU:\
A "Y" indicates there is a direct NVLINK connection between two GPUs.\
An "N" shows there is no direct NVLINK connection with that GPU.\
A "-" shows the GPU is itself.\
If the job exited abnormally due to a GPU-related error or warning, the
error or warning message displays. If LSF could not get GPU usage
information from DCGM, a hyphen (-) displays.

-hms\
Displays times in the customized output in hh:mm:ss format.

Categories\
format

Synopsis\
bjobs -o format \[-json\] -hms\
Conflicting options\
Use only with the -o and -o -json options.

Description\
When specified, bjobs displays any times (but not time stamps) in the
customized output in hh:mm:ss format.

The cpu_used field normally uses one decimal place in the bjobs output,
but if you specify -hms, bjobs rounds up this field to the next second.
For example, if the cpu_used field is 0.2 seconds, specifying -hms
rounds this number up to 00:00:01.

For the runtimelimit field, if the ABS_RUNLIMIT parameter is defined as
Y in the lsb.params file and you specify -hms, bjobs does not display
the host name. That is, if ABS_RUNLIMIT=Y is defined in the lsb.params
file, bjobs normally displays the host name after the runtime limit (for
example, 3.0/hostA). If you specify -hms, bjobs displays the runtime
limit without the host name (for example, 00:03:00). This also applies
if the ABS_RUNLIMIT parameter is defined as Y in the lsb.applications
file and you specify -hms to a job that is submitted to an application
profile with ABS_RUNLIMIT=Y.

Specifying the -hms option overrides the LSB_HMS_TIME_FORMAT environment
variable, which overrides the LSB_HMS_TIME_FORMAT parameter setting in
the lsf.conf file.

This option applies only to output for the bjobs -o and bjobs -o -json
commands for customized output. This option has no effect when run with
bjobs without the -o option.

-hostfile\
Last Updated: 2024-01-08\
Displays information about a job submitted with a user-specified host
file.

Categories\
format

Synopsis\
bjobs -l \| -UF \[-hostfile\]\
Conflicting options\
Use only with the -l or -UF option.

Description\
If a job was submitted with bsub -hostfile or modified with bmod
-hostfile to point to a user-specified host file, use -hostfile to show
the user-specified host file path as well as the contents of the host
file.

Use -hostfile together with -l or -UF, to view the user specified host
file content as well as the host allocation for a given job.

Example\
Use -l -hostfile to display a user-specified host file that was
submitted with a job or added to a job.

For example:\
bjobs -l -hostfile 2012\
Job \<2012\>, User `<userG>`{=html}, Project `<myproject>`{=html},
Status `<PEND>`{=html}, Queue\
`<normal>`{=html}, Commnad \<sleep 10000\>\
Thu Aug 1 12:43:25: Submitted from host `<host10a>`{=html},\
CWD \<\$HOME\>,Host file `</home/userG/myhostfile>`{=html};

......

USER-SPECIFIED HOST FILE:\
HOST SLOTS\
host01 3\
host02 1\
host01 1\
host02 2\
host03 1

-J\
Displays information about jobs or job arrays with the specified job
name.

Categories\
filter

Synopsis\
bjobs -J job_name\
Description\
Only displays jobs that were submitted by the user running this command.

The job name can be up to 4094 characters long. Job names are not
unique.

The wildcard character (**) can be used anywhere within a job name, but
cannot appear within array indices. For example job** returns jobA and
jobarray\[1\], **AAA**\[1\] returns the first element in all job arrays
with names containing AAA, however job1\[\*\] will not return anything
since the wildcard is within the array index.

-Jd\
Displays information about jobs with the specified job description.

Categories\
filter

Synopsis\
bjobs -Jd job_description\
Description\
Only displays jobs that were submitted by the user running this command.

The job description can be up to 4094 characters long. Job descriptions
are not unique.

The wildcard character (\*) can be used anywhere within a job
description.

-json\
Displays the customized output in JSON format.

Categories\
format

Synopsis\
bjobs -o format -json\
Conflicting options\
Do not use with the -noheader option.

Description\
Note: The -json command is not supported for Microsoft Windows or Apple
OS X operating systems.\
When specified, bjobs -o displays the customized output in the JSON
format.

This option applies only to output for the bjobs -o command for
customized output. This option has no effect when run with bjobs without
the -o option and the LSB_BJOBS_FORMAT environment variable or parameter
are not defined.

-json\
Displays the customized output in JSON format.

Categories\
format

Synopsis\
bjobs -o format -json\
Conflicting options\
Do not use with the -noheader option.

Description\
Note: The -json command is not supported for Microsoft Windows or Apple
OS X operating systems.\
When specified, bjobs -o displays the customized output in the JSON
format.

This option applies only to output for the bjobs -o command for
customized output. This option has no effect when run with bjobs without
the -o option and the LSB_BJOBS_FORMAT environment variable or parameter
are not defined.

-Lp\
Displays jobs that belong to the specified LSF License Scheduler
project.

Categories\
filter

Synopsis\
bjobs -Lp ls_project_name

-l\
Long format. Displays detailed information for each job in a multi-line
format.

Categories\
format

Synopsis\
bjobs -l\
Description\
The -l option displays the following additional information:\
Project name\
Job command\
Current working directory on the submission host\
Initial checkpoint period\
Checkpoint directory\
Migration threshold\
Predicted job start time\
Pending and suspending reasons\
Job status\
Job kill reason\
Number of resources (or, starting in Fix Pack 14, the assigned resource
names for each job)\
Resource usage\
Resource usage limits information\
Memory and CPU usage information, such as CPU efficiency, CPU peak
usage, and memory efficiency values\
Runtime resource usage information on the execution hosts\
Pending time limits, and eligible pending time limits\
Job description\
Name of any esub or epsub used with the job\
Energy usage (if energy accounting with IBM® Spectrum LSF Explorer is
enabled by setting LSF_QUERY_ES_FUNCTIONS="energy" or "all" in the
lsf.conf file)\
Approximate accumulated job disk usage (I/O) data on IBM Spectrum Scale
(if IBM Spectrum Scale I/O accounting with IBM Spectrum LSF Explorer is
enabled by setting LSF_QUERY_ES_FUNCTIONS="gpfsio" or "all" in the
lsf.conf file)\
Planned start time for jobs with a schedule and reservation plan.\
GPU requirement and allocation information\
Account name for LSF resource connector\
If the job was submitted with the bsub -K command, the -l option
displays Synchronous Execution.

Use the bjobs -A -l command to display detailed information for job
arrays, including job array job limit (% job_limit) if set.

Use the bjobs -ss -l command to display detailed information for session
scheduler jobs.

Use the bjobs -data -l command to display detailed information for jobs
with data requirements (for example, jobs that are submitted with
-data).

The bjobs -pl command displays detailed information about all pending
jobs of the invoker.

If the JOB_IDLE parameter is configured in the queue, use bjobs -l to
display job idle exception information.

If you submitted your job with the -U option to use advance reservations
that are created with the brsvadd command, bjobs -l shows the
reservation ID used by the job.

If the LSF_HPC_EXTENSIONS="SHORT_PIDLIST" parameter is specified in the
lsf.conf file, the output from bjobs is shortened to display only the
first PID and a count of the process group IDs (PGIDs) and process IDs
for the job. Without SHORT_PIDLIST, all of the process IDs (PIDs) for a
job are displayed.

If the LSF_HPC_EXTENSIONS="HOST_RUSAGE" parameter is specified in the
lsf.conf file, the output from the bjobs -l command reports the correct
rusage-based usage and the total rusage that is being charged to the
execution host.

If you submitted a job with multiple resource requirement strings by
using the bsub -R option for the order, same, rusage, and select
sections, bjobs -l displays a single, merged resource requirement string
for those sections, as if they were submitted by using a single -R
option.

If you submitted a job by using the OR (\|\|) expression to specify
alternative resources, this option displays the Execution rusage string
with which the job runs.

Predicted start time for PEND reserve job is not shown with the bjobs -l
command option. LSF does not calculate the predicted start time for PEND
reserve job if no back fill queue is configured in the system. In that
case, resource reservation for PEND jobs works as normal, and no
predicted start time is calculated.

For resizable jobs, the -l option displays active pending resize
allocation requests, and the latest job priority for running jobs with
active pending resize requests.

For jobs with user-based fair share scheduling, displays the charging
SAAP (share attribute account path).

For jobs submitted to an absolute priority scheduling (APS) queue, -l
shows the ADMIN factor value and the system APS value if they are not
set by the administrator for the job.

For jobs submitted with SSH X11 forwarding, displays that the job was
submitted in SSH X11 forwarding mode as well as the SSH command
submitted (set in LSB_SSH_XFORWARD_CMD in lsf.conf).

If the job was auto-attached to a guarantee SLA, -l displays the
auto-attached SLA name.

Specified CWD shows the value of the bsub -cwd option or the value of
LSB_JOB_CWD. The CWD path with pattern values is displayed. CWD is the
submission directory where bsub ran. If specified CWD was not defined,
this field is not shown. The execution CWD with pattern values is always
shown.

If the job was submitted with an energy policy, to automatically select
a CPU frequency, -l shows the Combined CPU frequency (the CPU frequency
that is selected for the job based on the energy policy tag, energy
policy, and threshold file). If the job was submitted with a
user-defined CPU frequency (by using bsub -freq), -l shows the Specified
CPU frequency for the job.

For jobs submitted with the default GPU requirements (with the option
~~gpu~~), use the bjobs -l command to see the default job-level resource
requirement without details like \<num=1...\>: Requested GPU.

If the -gpu option specifies GPU requirements (for example, -gpu num=3,
the bjobs -l shows the details as Requested GPU \<num=3\>.

The bjobs -l command displays an output section for GPU jobs that shows
the combined and effective GPU requirements that are specified for the
job. The GPU requirement string is in the format of the GPU_REQ
parameter in the application profile or queue:\
The combined GPU requirement is merged based on the current GPU
requirements in job, queue, application, or default GPU requirement.\
The effective GPU requirement is the one used by a started job. It never
changes after a job is started.\
Jobs that are submitted with an esub (or epsub) by using bsub -a (or
modified by using bmod -a), shows the latest esubs used for execution in
bjobs -l output, first with the default and then user esubs. If a
user-specified esub script is the same as the default esub script, the
duplicate esubs shows as one entry. If a job is submitted with an esub
containing parameters, the esub and its parameters are shown in bjobs -l
as well, and the format of the esub is the same as the esub that is
specified in the job submission. For example:\
bsub -a "test(a,b,c) " sleep 10000

is shown as:\
Job \<1561\>, User `<joes>`{=html}, Project

<default>

, Status `<RUN>`{=html}, Queue `<normal>`{=html},\
Command \<sleep 1000000\>, Share group charged `</joes>`{=html}, Esub
\<test(a,b,c)\>

If enhanced energy accounting with IBM Spectrum LSF Explorer is enabled
(with LSF_ENABLE_BEAT_SERVICE in lsf.conf), output shows the energy
usage in Joule and kWh.

If the lsb.params configuration file is configured with
ALLOCATION_PLANNER = Y, and sets of candidate jobs have been identified
for consideration for an allocation plan, LSF creates a scheduling and
reservation allocation plan.

bjobs --l : displays the planned start time for all jobs with an
allocation plan.\
bjobs --l --plan : filter for jobs with allocation plans, displaying the
planned start time and planned allocation for each job.

-m\
Displays jobs dispatched to the specified hosts.

Categories\
filter

Synopsis\
bjobs -m host_name ... \| -m host_group ... \| -m cluster_name\
Description\
To see the available hosts, use bhosts.

If a host group or compute unit is specified, displays jobs dispatched
to all hosts in the group. To determine the available host groups, use
bmgroup. To determine the available compute units, use bmgroup -cu.

You can specify a single cluster. If a remote cluster name is specified,
you see the remote job ID, even if the execution host belongs to the
local cluster. To determine the available clusters, use bclusters.

Examples\
bjobs -d -q short -m hostA -u user1

Displays all the recently finished jobs submitted by user1 to the queue
short, and executed on the host hostA.

-N\
Displays information about done and exited jobs, also displays the
normalized CPU time consumed by the job.

Categories\
filter, format, state

Synopsis\
bjobs -N host_name \| -N host_model \| -N cpu_factor\
Description\
Normalizes using the CPU factor specified, or the CPU factor of the host
or host model specified.

Use with -p, -r, and -s to show information about pending, running, and
suspended jobs along with done and exited jobs.

-noheader\
Removes the column headings from the output.

Categories\
format

Synopsis\
bjobs -noheader\
Description\
When specified, bjobs displays the values of the fields without
displaying the names of the fields. This is useful for script parsing,
when column headings are not necessary.

This option applies to output for the bjobs command with no options, and
to output for all bjobs options with short form output except for -aff,
-l, -UF, -N, -h, and -V.





