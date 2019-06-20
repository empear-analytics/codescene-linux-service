# CodeScene Linux Service

This repository contains a systemd configuration for running a CodeScene instance on Linux as a service.
With CodeScene as a Linux service, systemd will take care of:

* Automatic restart after server reboot.
* Automatic restart if the CodeScene service is killed.

## Mandatory Configuration

To use this script, make sure you create a codescene user and specify that system user in the `User` field.

Note that the system user you creates needs to have SSH credentials in their home directory.

## Optional Configuration

Depending on your environment, you might want to change the following options in the script:

* `ExecStart`: This command is used to launch your CodeScene instance. You might have to use an absolute path for
  the `codescene-enterprise-edition.standalone.jar` JAR file. If you analyse large applications with deep history, then
  you might also want to increase the default `-Xmx8g` JVM memory option to specify a larger maximum heap size.
* `StartLimitIntervalSec=0`: This option means that systemd will attempt to restart the CodeScene service forever. If you
  remove this option, systemd will give up after 5 failed attempts.

## About CodeScene

![codescene_screenshot](codescene-screenshot.png).

CodeScene was created as a reaction and complement to traditional static code analysis tools.
The main difference between CodeScene’s behavioral code analysis and traditional code scanning techniques is that
static tools work on a snapshot of the codebase while CodeScene considers the temporal dimension and evolution of the whole system.

This makes it possible for CodeScene to prioritize technical debt and code quality issues based on how the organization actually
works with the code. Hence, CodeScene limits the results to information that is relevant, actionable, and translates directly into business value.

Read more about CodeScene [here](https://empear.com/).
