# Backup as a Service in Cleura Cloud

!!! warning "Service availability"
    Backup as a Service will become available on 2026-10-12 (in the {{api_region}} region only).

**Backup as a Service (BaaS)** is a mechanism for backing up cloud block storage.
BaaS allows {{brand}} users to create, manage, schedule, and restore volume backups using the OpenStack CLI or the {{gui}}.

??? "Differences to the Recovery service"
    Compared to the [Recovery service](recovery-service.md) {{brand}} offers, BaaS is much more flexible regarding backup scheduling.
    Also, unlike the Recovery service, which is offered *only* via the {{gui}}, BaaS can be managed from either the OpenStack CLI or the {{gui}}.

## Cinder Backup

BaaS is implemented over the **Cinder Backup** service.
Cinder creates full or incremental backups of available or in-use (attached to instances) block volumes.

Cinder Backup also supports encrypted volumes, which it backs up as-is.
Backups of encrypted volumes can be full or incremental.

You can later restore Cinder backups to new or existing volumes.
You can even restore to the *original* volumes the backups were based on.

## Backups in immutable containers

In {{brand}}, you may create volume backups by specifying a special container named `immutable`.

You can still delete any backup in that container.
However, you can recover deleted volume backups from the `immutable` container by raising a [service support request](../howto/support/raise-issues.md) within a specified time period.

## OpenStack Freezer

BaaS uses **Freezer**, an OpenStack project that facilitates automatic backup workflows.
Freezer enables users to define backup jobs and execution schedules.
That way, the backup jobs run automatically, without manual intervention.
