# About these files

The files in this directory are stub files which include the file
`/_includes/cli.md`, which parses YAML files generated from the
[`docker/docker`](https://github.com/moby/moby) repository. The YAML files
are parsed into output files like
[https://docs.docker.com/engine/reference/commandline/build/](https://docs.docker.com/engine/reference/commandline/build/).

## How the output is generated

The output files are composed from two sources:

- The **Description** and **Usage** sections comes directly from
  the CLI source code in that repository.

- The **Extended Description** and **Examples** sections are pulled into the
  YAML from the files in [https://github.com/moby/moby/tree/master/docs/reference/commandline](https://github.com/moby/moby/tree/master/docs/reference/commandline)
  Specifically, the Markdown inside the `## Description` and `## Examples`
  headings are parsed. Please submit corrections to the text in that repository.

# Updating the YAML files

The process for generating the YAML files is still in flux. Check with
@thajestah or @frenchben. Be sure to generate the YAML files with the correct
branch of `docker/docker` checked out (probably not `master`).

After generating the YAML files, replace the YAML files in
[https://github.com/docker/docker.github.io/tree/master/_data/engine-cli](https://github.com/docker/docker.github.io/tree/master/_data/engine-cli)
with the newly-generated files. Submit a pull request.
