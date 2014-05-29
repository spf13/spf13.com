---
Description: How to go about creating better backups through replication and snapshots
  and how to ensure that your infrastructure has a solid disaster recovery plan.
Keywords:
- Architecture
- Development
- MongoDB
- Systems
- backup
- backups
- better backups
- computer data
- computer storage
- computing
- data
- data loss
- data management
- Database
- database management systems
- disaster recovery
- disaster recovery plan
- infrastructure
- mongodb
- raid
- recovery
- recovery plan
- replication
- snapshot
Section: post
Slug: backups-replication-and-disaster-recovery
Tags:
- backup
- backups
- better backups
- computer data
- computer storage
- computing
- data
- data loss
- data management
- Database
- database management systems
- disaster recovery
- disaster recovery plan
- infrastructure
- mongodb
- raid
- recovery
- recovery plan
- replication
- snapshot
Thumbnail: /images/1702_header_412_disaster_day_of_crisis1.jpg-200x200.jpg
Title: Backup, Replication and Disaster Recovery
Topics:
- Architecture
- Development
- MongoDB
- Systems
Url: post/backups-replication-and-disaster-recovery
date: 2012-01-11
disqus_identifier: 1699 http://spf13.com/?p=1699
disqus_title: Backup, Replication, and Disaster Recovery
disqus_url: http://spf13.com/post/backups-replication-and-disaster-recovery/
---

{{% img src="/media/disaster_day_of_crisis.jpg" alt="crisis" %}}

One of the most common concerns people have is how to ensure that their
application is safe, secure and available in the event of an emergency.
Often I have found that people are mistakenly believe that they are
protected when in fact they often have ignored potential scenarios.

The principles explained apply equally well in RDBMSs, MongoDB and other
databases.

Potential scenarios to protect against
--------------------------------------

1.  ### Drive failure

2.  ### Machine failure

3.  ### Switch failure

4.  ### Power circuit failure

5.  ### Data center failure

6.  ### Intrusion

7.  ### Fat fingers

8.  ### Programmer error

Raid
----

To prevent drive failure use multiple drives in a single machine for
high availability. RAID 10 provides the best performance with high
availability. RAID 10 consists of a minimum of 4 disks which are split
into mirrored pairs. The raid controller stripes across the pairs.

Replication
-----------

Replication is the act of mirroring the data from one server onto
another. It will protect against any failure of one (or more) of
machines. Commonly two or more machines are used. If properly configured
it can also protect against most of the failures identified above. I
will present a few different configurations and what they protect
against.

### Replica Sets

In addition to standard Master Slave replication MongoDB provides an
additional replication configuration called replica sets. Replica sets
are similar to master slave, but they are set aware with automatic
failover and recovery. Replica sets are a minimum of 3 nodes. 3 nodes
can be 3 database nodes, or 2 database nodes + 1 arbiter. The arbiter
doesn’t handle queries or store data, but is around to provide a third
perspective to cast a vote when determining the status of the set. In
master slave you can have the same setup but it requires you to
participate as the arbiter.

### Configuration 1 :

**2 nodes + 1 arbiter (or 3 nodes) on same rack (same switch and power
circuit).**

-   Protects against single drive failure (if not using RAID 0 or 10).
-   Protects against single node failure.

### Configuration 2 :

**2 nodes + 1 arbiter on 3 different racks (different switch and power
circuit).**

-   Protects against the above + failure of switch or power circuit.

### Configuration 3 :

**4 nodes + 1 arbiter on 3 different racks (different switch and power
circuit).**

-   Protects against the above + two nodes failing or a node failure at
    the same time as a switch or power failure.

### Configuration 4 :

**4 nodes + 1 arbiter in 3 different data centers.**

-   Protects against all the above + data center failure.

### Configuration 5 :

**Any combination of the above but swap out the arbiter for a delayed
secondary with priority 0 (hidden).**

Some Protection against data loss in the event of Intrusion, Fat finger
(sysadmin / DBA accidentally deleting / changing something), programmer
error.

Only partial protection as any data written during the delay window will
be lost. If not caught during the window (or windows) provides no
protection.

Backups
-------

A backup consists of a dump of the data ideally stored in a remote
secure location. It’s important to ensure that the backup format used
has an easy and consistent import mechanism. Any scripts you use to
backup should have a counterpart restore written along with them. The
worst possible time to discover issues with your backup is when you are
trying to restore them. Make sure restoration is rock solid.

For permanent disaster recovery and for compliance with a variety of
industry regulations it’s important to keep (offsite) backups. Depending
on your data size, business and type of data you may want to take
backups more or less regularly. A solid backup plan is the only way to
ensure that the bulk of your data is never lost in the event of a
disaster. It is often not enough to have replication be your sole form
of backup as it doesn’t protect against intrusion, fat finger (sysadmin
/ DBA accidentally deleting / changing something) or programmer error
outside of the delay window and not at all without a delayed replicant.

Conclusion
----------

It’s important to understand the pitfalls and how to prevent them. Also
recognize that there’s a balance that must be struck. Multiple data
centers add additional complexity and bring a number of challenges along
with their additional protection.

Lastly, Replication != backup. Please backup your data. If someone
accidentally or intentionally maliciously performs a drop operation that
same operation will be replicated across all of your machines. The only
safety net is a good backup strategy.
