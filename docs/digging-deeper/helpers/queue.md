---
title: queue
sidebar_title: queue
---


Description
-----------

Helper function to send a job to a queue or dispatch a job.

Usage
-----

    <?php

    use Codefy\Framework\Queue\NodeQueue;

    use function Codefy\Framework\Helpers\queue;
    
    function queue(ShouldQueue $queue): NodeQueue;

## Examples

Send a job to the queue:

    <?php
    
    return queue(
        queue: new \App\Infrastructure\Services\NewEmailSignup(
            request: new \Qubus\Http\ServerRequest()
        )
    )->createItem();
    // returns the last inserted id (ULID)

Dispatch a queued job:

    <?php
    
    return queue(queue: $queue)->dispatch();
    // returns bool; $queue is the object that is plucked out of the queue

Parameters
----------

**$queue** (`Codefy\Framework\Queue\ShouldQueue`) (required) A job to queue or dispatch.