# Queue plugin for CakePHP

[![Build Status](https://travis-ci.org/Oefenweb/cakephp-queue.png?branch=master)](https://travis-ci.org/Oefenweb/cakephp-queue) [![Coverage Status](https://coveralls.io/repos/Oefenweb/cakephp-queue/badge.png)](https://coveralls.io/r/Oefenweb/cakephp-queue)

## Requirements

* CakePHP 2.4.2 or greater.
* PHP 5.3.10 or greater.

## Installation

Clone/Copy the files in this directory into `app/Plugin/Queue`

## Configuration

Ensure the plugin is loaded in `app/Config/bootstrap.php` by calling:

```
CakePlugin::load('Queue');
```

Ensure to configure the following lines in `app/Config/bootstrap.php`:

```
Configure::write('Queue.sleepTime', 10);
Configure::write('Queue.gcprop', 10);
Configure::write('Queue.defaultWorkerTimeout', 2 * MINUTE);
Configure::write('Queue.defaultWorkerRetries', 4);
Configure::write('Queue.workerMaxRuntime', 0);
Configure::write('Queue.cleanupTimeout', DAY);
Configure::write('Queue.exitWhenNothingToDo', false);
```

Load schema:

```
Console/cake schema create;
```

## Usage

### Console

Run from your APP folder:

```
# Tries to call the `add()` function on a task.
Console/cake Queue.queue add <taskname>;
```

```
# Run a queue worker.
Console/cake Queue.queue runworker;
```

```
# Display some general statistics.
Console/cake Queue.queue stats;
```

```
# Manually call cleanup function to delete task data of completed tasks.
Console/cake Queue.queue clean;
```
