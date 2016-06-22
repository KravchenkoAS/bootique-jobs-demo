[![Build Status](https://travis-ci.org/bootique-examples/bootique-jobs-demo.svg)](https://travis-ci.org/bootique-examples/bootique-jobs-demo)

# bootique-jobs-demo

An example that explains how to write jobs on Bootique platform. Jobs can be run individually from command line, or scheduled with internal scheduler.

*For additional help/questions about this example send a message to
[Bootique forum](https://groups.google.com/forum/#!forum/bootique-user).*

Prerequisites:

* Java 1.8 or newer.
* Apache Maven.

Here is how to build it:

	git clone git@github.com:bootique-examples/bootique-jobs-demo.git
	cd bootique-jobs-demo
	mvn package

Now you can check the options available in your app:

	java -jar target/bootique-jobs-demo-1.0-SNAPSHOT.jar

	Option                    Description
    ------                    -----------
    --config <yaml_location>  Specifies YAML config location, which
                                can be a file path or a URL.
    --exec                    Executes one or more jobs. Jobs are
                                specified with '--job' options
    --help                    Prints this message.
    --job <job_name>          Specifies the name of the job to run
                                with '--exec'. Available job names
                                can be viewed using '--list' command.
    --list                    Lists all jobs available in the app
    --schedule                Schedules and executes jobs according
                                to configuration. Waits indefinitely
                                on the foreground.

One of the options is ```--list``` that tells you what jobs are available:

    java -jar target/bootique-jobs-demo-1.0-SNAPSHOT.jar --list

    Available jobs:
         - simple

From here you have two options - run one or more jobs once from the command line, or start the app as a daemon and let the jobs run on a defined schedule. First option is great for testing/debugging or when you have an external scheduler (such as UNIX cron). So let's run both jobs at once:

    java -jar target/bootique-jobs-demo-1.0-SNAPSHOT.jar --exec --job=simple --job=job2

Now let's schedule jobs. Scheduling information is provided in ```run.yml```:

    java -jar target/bootique-jobs-demo-1.0-SNAPSHOT.jar --schedule --config=run.yml