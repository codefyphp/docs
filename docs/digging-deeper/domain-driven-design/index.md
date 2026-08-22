---
title: Aggregates
sidebar_title: Aggregates
summary: Build rich event-sourced PHP aggregates with CodefyPHP using domain events, value objects, invariant protection, state changes, and aggregate roots.
keywords: php-aggregates,domain-driven-design,event-sourcing
weight: 0
---

## Installation

```shell
composer require codefyphp/domain-driven-core
```

## Introduction

Aggregates are the most important part of Domain-Driven Design. They are not just plain old PHP objects (POPO), but 
rich models that help with the complexity of business rules and invariants.

Throughout the aggregates section, you will learn how to build a domain rich eventsourced aggregate. Here is an example 
of an eventsourced `Post` aggregate:

```php
<?php

declare(strict_types=1);

use Codefy\Domain\Aggregate\AggregateRoot;
use Codefy\Domain\Aggregate\EventSourcedAggregate;
use Domain\Post\Event\ContentWasChanged;
use Domain\Post\Event\PostWasCreated;
use Domain\Post\Event\TitleWasChanged;
use Domain\Post\Exception\TitleWasNullException;
use Domain\Post\ValueObject\PostId;
use Domain\Post\ValueObject\Title;
use Domain\Post\ValueObject\Content;
use Qubus\Exception\Data\TypeException;

use function Qubus\Inheritance\Helpers\tap;

final class Post extends EventSourcedAggregate implements AggregateRoot
{
    private PostId $postId;

    private Title $title;

    private Content $content;

    /**
     * @throws TitleWasNullException
     */
    public static function createPostWithoutTap(PostId $postId, Title $title, Content $content): Post
    {
        if ($title->isEmpty()) {
            throw new TitleWasNullException(message: 'Title cannot be null.');
        }

        $post = self::root(aggregateId: $postId);

        $post->recordApplyAndPublishThat(
            event: PostWasCreated::withData($postId, $title, $content)
        );

        return $post;
    }

    /**
     * @throws TitleWasNullException
     */
    public static function createPostWithTap(PostId $postId, Title $title, Content $content): Post
    {
        if ($title->isEmpty()) {
            throw new TitleWasNullException(message: 'Title cannot be null.');
        }

        return tap(
            value: self::root($postId),
            callback: fn($post) => $post->recordApplyAndPublishThat(
                PostWasCreated::withData(postId: $postId, title: $title, content: $content)
            )
        );
    }

    public static function fromNative(PostId $postId): Post
    {
        return self::root(aggregateId: $postId);
    }

    /**S
     * @throws TitleWasNullException
     */
    public function changeTitle(Title $title): void
    {
        if ($title->isEmpty()) {
            throw new TitleWasNullException(message: 'Title cannot be null.');
        }
        if ($title->__toString() === $this->title->__toString()) {
            return;
        }
        $this->recordApplyAndPublishThat(
            event: TitleWasChanged::withData(postId: $this->postId, title: $title)
        );
    }
    
    public function changeContent(Content $content): void
    {
        if ($content->equals($this->content)) {
            return;
        }
        $this->recordApplyAndPublishThat(
            event: ContentWasChanged::withData(postId: $this->postId, content: $content)
        );
    }

    public function title(): Title
    {
        return $this->title;
    }

    public function content(): Content
    {
        return $this->content;
    }

    /**
     * @throws TypeException
     */
    protected function whenPostWasCreated(PostWasCreated $event): void
    {
        $this->postId = $event->aggregateId();
        $this->title = $event->title();
        $this->content = $event->content();
    }

    /**
     * @throws TypeException
     */
    protected function whenTitleWasChanged(TitleWasChanged $event): void
    {
        $this->postId = $event->aggregateId();
        $this->title = $event->title();
    }
    
    /**
     * @throws TypeException
     */
    protected function whenContentWasChanged(ContentWasChanged $event): void
    {
        $this->postId = $event->aggregateId();
        $this->content = $event->content();
    }
}
```
        
There is a lot to unpack in the Post aggregate, but as you go through the rest of this section, you will begin to 
understand its parts as it's broken down and explained.
