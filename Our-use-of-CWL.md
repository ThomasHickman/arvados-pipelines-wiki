These notes are a work in progress! They reflect our use of CWL and other ways of using it may be equally valid.

# Overview
CWL specifies tools which are linked into workflows. A tool is a single step which takes inputs, does some processing, and produces outputs. A workflow is a series of steps. Workflows can be built from sub-workflows. There can be branching and 'scattering' meaning apply the same tool in parallel to a set of inputs.

## Running a script or program in a CWL tool.
The individual steps (tools) run in Docker containers. It is important for reliability and reproducibility that we use well defined containers. Normally for us that means that they are from our own [mercury docker hub](https://hub.docker.com/u/mercury/)

If the tool involves a shell script calling a function from samtools, bcftools or similar and doing some processing, the generic mercury docker image for the correct version of samtools or bcftools can be used, and the script read in as an input file. 

If there are more dependencies, such as R packages or Python packages we create a new docker image that includes the script and all dependencies, and it is automatically uploaded to mercury.

There are examples of both methods in our CWL codebase.

## Handling secondary files 
### Necessary secondary files
Specify these in the CWL file, [docs](http://www.commonwl.org/v1.0/CommandLineTool.html#File)

### Optional secondary files 
(eg input a file, with an index file if one exists)
Specify these in the yaml inputs file

## Writing output to files
### If the script in the tool outputs to stdout
### If the script writes to a file
