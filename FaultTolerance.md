# Fault Tolerance
Fault Tolerance is criteria of a system that defines the ability of the system to work or function as expected when there is any failure. 
Failure can be system component, service, network connectivity, unavailability of resource. 

Fault tolerant system ensure high-availability of the system by preventing disruptions arising from a single point of failure.

**Components of a Fault-tolerance System**\
Diversity:\
If a system’s main electricity supply fails, potentially due to a storm that causes a power outage or affects a power station, it will not be possible to access alternative electricity sources. In this event, fault tolerance can be sourced through diversity, which provides electricity from sources like backup generators that take over when a main power failure occurs.

Redundancy:\ 
Fault-tolerant systems use redundancy to remove the single point of failure. The system is equipped with one or more power supply units (PSUs), which do not need to power the system when the primary PSU functions as normal. In the event the primary PSU fails or suffers a fault, it can be removed from service and replaced by a redundant PSU, which takes over system function and performance. 
Alternatively, redundancy can be imposed at a system level, which means an entire alternate computer system is in place in case a failure occurs.

Replication:\
Replication is a more complex approach to achieving fault tolerance. It involves using multiple identical versions of systems and subsystems and ensuring their functions always provide identical results. If the results are not identical, then a democratic procedure is used to identify the faulty system. Alternatively, a procedure can be used to check for a system that shows a different result, which indicates it is faulty. 

Replication can either take place at the component level, which involves multiple processors running simultaneously, or at the system level, which involves identical computer systems running simultaneously.

**Elements of Fault-tolerant Systems**\
Hardware Systems:\
Hardware systems can be backed up by systems that are identical or equivalent to them. A typical example is a server made fault-tolerant by deploying an identical server that runs in parallel to it and mirrors all its operations, such as the redundant array of inexpensive disks (RAID), which combines physical disk components to achieve redundancy and improved performance.

Software Systems:\
Software systems can be made fault-tolerant by backing them up with other software. A common example is backing up a database that contains customer data to ensure it can continuously replicate onto another machine. As a result, in the event that a primary database fails, normal operations will continue because they are automatically replicated and redirected onto the backup database.

There are two fault-tolerant approaches:
- **fault-removal** – This can be either forward error recovery or backward error recovery.
- **fault-masking** – when the presence of one defect hides the presence of another defect in the system.

For fault tolerance with zero downtime (constantly active), a "hot" failover(instantly transfers workloads to a working backup system) 
needs to be implemented. If maintaining a constantly-active standby system is not required, a "warm" or "cold" failover system can 
be implemented where a backup system loads and starts running workloads. The speed of a warm/cold failover is slower because of the 
loading times.

Fault-tolerant computing offers little protection against software failure, which is a major cause of downtime and data center outages for most organizations.

**Forward and Backward error recovery**\
Forward error recovery involves identifying the error and, based on this knowledge, correcting the system state containing the error. Exception handling in high-level languages like Ada and PL/1 provides a system structure that supports forward recovery.

Backward error recovery corrects the system state by restoring the system to a stable state that existed prior to the manifestation of the fault.

**Advantages of fault-tolerant systems**\
The key purpose of creating fault tolerance is to avoid (or at least minimize as much as possible) a situation where the functionality of the system becomes unavailable due to a fault in one or more of its components.

Fault tolerance is necessary for systems that are used to protect people’s safety (such as air traffic control hardware and software systems) and in systems that security, data protection, data integrity, and high-value transactions all depend on.

Fault-tolerant systems provide an excellent safeguard against equipment failure, but they can be extraordinarily expensive to implement because they require a fully redundant set of hardware that needs to be linked to the primary system.
