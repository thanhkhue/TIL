- **Optimistic Concurrency Control (OCC)**, assumes multiple transactions can completed without intefer each other (frequently used in low data contention).
- In **OCC**, while running, transactions uses data resources without accquiring the locks in theses data resources. 

- Phases of OCC:
  + Begin: assign timestamp at the beginning of transaction
  + Modify: transaction read the data of record, and does computations.
  + Verify: transaction check the state of the data resources to see whether any change made by other transactions during the time (from begin step to current).
  + Commit/Rollback: If there is no conflict, commit all the changes. If having, solve it, by aborting the transaction or resolve conflicts.
  
