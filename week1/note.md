## Editing with *vi*
vim -- vi improved
Running in Vi compatible mode: vim will run in a mode that is closer tohte normal behavior of vi rahter than the enhanced behavior of vim.

### Moving the cursor
hjkl -- 
0 zero -- to the beginning of th current line
^ -- first non-whitespace character on the current line
$ -- end of current line
w
W
b
B
#G numberG -- to the line #
G to the last line of file

### delete 
x
3x
dd -- delete whole line
5dd -- delete line and next 4 line


### Search and replace
:%s/old/new/g

### Command Line
use `:` to enter the command mode
:q - quit
:q! -- quit without saving
:wq -- write and quit

: set number
### Insert Edit Mode
 `esc + i`

 # Shell Scripts
 A shell script is a file containing a series of commands.

Shell scripts and functions are both interpreted, they are not compiled.

### Why?
standardize and automate the performance of administrative chores.

* case sensitive
  
need *escaped* 

`#!/bin/bash` -- tell what shell are used
`#` comments

no data type in shell script
no space between value and equal sign =
 
 # DevOps
 devops is more about philosophy and cultural changes. Paradigm shifts in the way you think, the way you approach your problem

## Infrastructure as Code
infrastructure is provisioned using manual process.

All infrastructre provisioning "code" and environment configuration must be stored in version management system such as Git

Same programming best practices must apply to the infrastructure code as applied to application code

continuous integration, continuous delivery

### Automation
 
 Monitoring

 feedback is critical. Feedback comes from logs, monitoring, alerting and auditing infrastructure 

 Security

 # Site Reliability Engineering (SRE)


"Hope is not strategy"
#### Conflicts
dev teams want to launch new features and see them adopted by users as quickly as possible, the ope teams watn to make sure the service doesn't braek while they are holding the pager. 
The two teams' goals are fundamentally in tension.

SRE is a discipline that incorporates aspects of SE and applies that to operations whose goals are to create ultra-scalable and highly reliable software systems.

DevOps is a supreset of SRE, SRE focus narrower on DevOps.

Eliminating Toil
Toil is the kind of work tied to running a production service taht tends to be manual, repretitive, automatble, tactical, devoid of enduring value, and that scales linearly as a service grows

Error Budget

#### Time-based availability
over the period of a year, calculate the acceptable number of minutes of downtime to reach a given number of nines of availability.

`availability = uptime / (uptime + downtime)`

#### Aggredate Availability
`availability = successful requests / total requests`


### service level objectives - terminology

#### indicators - service level indicator SLI
a creafully defined quantitative measure of some aspect of the level of service that is provided.

#### objectives - service level objective SLO

#### agreements - SLA: 

"May the queries flow, and the pager stay silent"

(事后剖析)Postmortem: a written record of an incident, its impact, the actions taken to mitigate or resolve it, the root causes, and the follow-up actions to prevent the incident from recurring.