# fswatch-cmd

Monitoring and batching filesystem changes into smooth, efficient command executions. For example
can be used for efficiently and live mirroring of a directory.

Mirror a folder directly when the folder's contents changes

    fswatch-cmd  src-folder/   mirror src-folder/ dest-server:dst-folder/

The [mirror](https://github.com/harcokuppens/mirror/) command is a wrapper around rsync to easily do
mirroring.

## Installation

## Documentation

Documentation by giving no arguments to `fswatch-cmd` command:

    $ fswatch-cmd

    NAME

    fswatch-cmd - monitoring and batching filesystem changes into smooth, efficient command executions.
                  For example can be used for efficiently and live mirroring of a directory.

    USAGE

    fswatch-cmd [-e EVENTS] [-x EVENTS] WATCHDIR COMMAND [ARG]..

    DESCRIPTION

    The fswatch-cmd monitors the specified WATCHDIR for filesystem changes. When changes are detected,
    it executes the specified COMMAND (along with any optional arguments).

    While the COMMAND is running, fswatch-cmd continues to collect incoming events. This allows it
    to batch these events and pass them to the COMMAND on the next execution, rather than triggering
    the COMMAND for each individual event.

    All detected events are passed to the COMMAND via the EVENTS environment variable, where
    each event is separated by a newline

    Key Advantages of using fswatch-cmd:

    1. Event Batching: It aggregates filesystem events and passes them to the command at once,
        reducing redundant command executions.
    2. Performance Efficiency: Avoids launching a new process for each event, which can be resource-intensive.
    3. Simplified Event Handling: The COMMAND can handle all collected events in a single execution,
        improving the logic and reducing complexity when handling frequent or high-volume filesystem changes.


    OPTIONS

    -e   comma-separated list of allowed events
    -x   comma-separated list of excluded events

    All events are described in the manpage of fswatch.

    EXAMPLE

    Mirror a folder directly when the folder's contents changes

        fswatch-cmd  src-folder/   mirror src-folder/ dest-server:dst-folder/

    The 'mirror' command is a wrapper around rsync to easily do mirroring.
    See: https://github.com/harcokuppens/mirror/
