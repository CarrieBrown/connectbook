[title]: - "Changes between FSurf 2.x and 1.x"


## Overview
This document describes the differences between the 1.x versions of Fsurf and
the current 2.x versions of Fsurf. The differences between the two are primarily
in submitting scans for processing. 

## Inputs for submission

FSurf 2.0 added support for two new workflow types (multiple input and custom).
Since Fsurf 1.x only supports the standard workflow, it uses different options
for inputs. The input file is derived from the subject name and doesn't
necessarily need to be specified.  E.g. if the subject is `MRN_1` then Fsurf 1.x
would look for a mgz file called `MRN_1_defaced.mgz`.  If the file is in the
current directory, Fsurf 1.x would look for that file by default.  Therefore,
you could run a workflow on the `MRN_1` subject by running 

    `fsurf --subject MRN_1`
    
If the file was in another directory, you would need to specify this
using the `--dir` option:

    `fsurf --subject MRN_1 --dir /path/to/scans`.

## Output 

Fsurf 2.x and Fsurf 1.x also vary slightly in the output generated.  The only
place where this varies significantly is when displaying information about
workflows.  FSurf 1.x does not show the number of total tasks and completed tasks
when the `list` command is used.  In addition, Fsurf 1.x only gives the workflow
status when the `status` command is used.  Fsurf 2.x provides a more complete
summary of the workflow status and some details about resources that the
workflow used.

## Workflow status

Fsurf 1.x also used slightly differnt terms to indicate the status of a workflow.
Fsurf 1.x uses `UPLOADED` when a workflow has been created instead of `QUEUED`.
Similarly, Fsurf 1.x uses `PROCESSING` instead of `RUNNING` when a workflow has
been started.
