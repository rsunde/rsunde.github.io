# Background / Queue

A brief comparison and understanding of different background job and queue managers.

## Introduction

### Hangfire
Hangfire provides a job queue, the jobs gets stored in a database or in memory, the jobs are stored with an action or task name and its arguments, these jobs then gets executed right away (background job) or later (scheduled job), all these jobs can run any where you want, locally in the main app or in the cloud as different services consume the jobs.

jobs can be chained by providing the "parent" jobid to another job.

the jobs are very isolated and doesnt return the result, if you need to provide the results of the job, you need to another way of doing this, SignalR for example from inside the job itself.

*Example:*
```csharp
public static Task<Config> Test(Config config)
{
    // Call some services, massage the data

    //and then return...
    return Task.FromResult(config);
}

// Some code somewhere
var jobid = Hangfire.BackgroundJob.Enqueue(() => Test(new Config()));
```

As you can see, the Test task takes a config as argument and then returns a config, maybe in this instance we needed to do something with the config which takes 1 hour, so send the task off to a service somewhere and let it work.

As you can see the task returns the config but adding the job to hangfire only returns the jobid, so there is no way to actually deal with the result.

*Example:*
```csharp
public static void Test(Config config)
{
    // Call some services, massage the data

    // Broadcast SignalR about the updated config
}

// Some code somewhere
var jobid = Hangfire.BackgroundJob.Enqueue(() => Test(new Config()));
```

This is suppsedly the only way to return data, unless you poll the database or another service for some kind of change.

### Brighter


