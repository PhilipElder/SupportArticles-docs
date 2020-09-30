---
title: Scheduled task may not run upon reboot if machine was off at time of task
description: Helps to solve the issue that a scheduled task may not run upon reboot if the machine is off at the time of the task
ms.date: 09/14/2020
author: Deland-Han
ms.author: delhan 
manager: dscontentpm
audience: itpro
ms.topic: troubleshooting
ms.prod: windows-server
localization_priority: medium
ms.reviewer: kaushika
ms.prod-support-area-path: Task Scheduler
ms.technology: SysManagementComponents
---
# Scheduled task may not run upon reboot if the machine is off at the time of task

This article helps to solve the issue that a scheduled task may not run upon reboot if the machine is off at the time of the task.

_Original product version:_ &nbsp; Windows Server 2012 R2, Windows 7 Service Pack 1  
_Original KB number:_ &nbsp; 2437520

## Symptoms

On a Windows Vista, Windows 7, and Windows Server 2008 or Windows Server 2008 R2 machine, a scheduled task may not run upon reboot if the machine was off at the time of the scheduled task.

## Cause

This issue can occur if the task trigger was set to run One Time when created. It is possible to set a task to "Run as soon as possible after a scheduled start is missed". This will cause the task to rerun after a reboot if the trigger was missed. However, this does not occur if the task is set to run One Time. This behavior is by design.

## Resolution

You can work around this issue by setting a time and date under the Expire option of the task. This option can be reached by opening the Properties of the task, selecting the Triggers tab, and then clicking the Edit button for the trigger in question. If a date and time are set for the Expire option, the task will attempt to refire on reboot if its previous trigger time was missed.