# lab-04-queue-table-and-the-duplicate-rule

##Problem- 
I needed to model FIFO job ordering with enqueue and dequeue operations, trace undo and redo stack states across edit steps, and design a rule to prevent duplicate execution when a job retry occurs after a lost acknowledgement.   

##What I built- 
A written design and trace covering FIFO queue states for jobs A, B, and C, a four-step Undo and Redo stack trace for edits X, Y, and Z, and a deduplication rule using a stable identifier and atomic check-and-record logic.   

##How it works- 
Enqueue A, B, and C into the queue and dequeue them in FIFO order (A, then B, then C).Track Undo and Redo stack states (with top on the right) and active edits across Edit(X), Edit(Y), Undo(), and Edit(Z), clearing Redo when a new edit branches history.Assign each job a stable identifier and use an atomic check-and-record rule so a retried job with a lost acknowledgement is executed only once.

##What I learned- 
Queues process items in FIFO order, new edits after an undo clear the redo stack so earlier redo branches are dropped, and idempotent identifiers with atomic check-and-record prevent duplicate side effects during retries.
