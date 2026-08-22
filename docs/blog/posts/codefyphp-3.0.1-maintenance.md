---
title: CodefyPHP 3.0.1 Maintenance Release
description: Review the CodefyPHP 3.0.1 maintenance fixes for configurable authentication cookies, shared UserAuth services, and conditional logic.
summary: Review the CodefyPHP 3.0.1 maintenance fixes for configurable authentication cookies, shared UserAuth services, and conditional logic.
keywords: codefyphp-3.0.1,maintenance-release,bug-fixes
date:
  created: 2025-10-18 13:10:00
authors: [nomadicjosh]
---

# CodefyPHP 3.0.1 Maintenance Release

This is a very small maintenance release. In the `App\Infrastructure\Services\UserAuth` class (located in skeleton), 
`USERSESSID` was hardcoded instead of using the user specified cookie name from `./config/auth.php`. It also has been 
added as a shared instance in `App\Infrastructure\Providers\RbacServiceProvider`.

Another bug that was fixed, was an extra semicolon after an `if` statement. The bug did not cause any adverse reactions, 
but deemed it necessary to take care of.
