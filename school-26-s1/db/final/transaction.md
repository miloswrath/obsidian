## Definition
---
A **transaction** is the logical unit of work of on application that queries a database.
- Apps are usually querying a series of transactions.
- In production these are typically concurrent
- Transforms db from one state to another
**EX**
![[transaction 2025-12-07 12.28.15.excalidraw]]
## Transaction Model
---
*There are two main types of transactions*:
- `COMMIT`
- `ROLLBACK`

Changes are made in local cache before comitting, so other concurrently running workers don't see the changes until they are committed.
*^^ This will lead to concurrency problems*

*Transactions have one of two possible outcomes*
- Success - changes are comitted and DB has new consistent state
- Failure - transaction aborts and database is restored to previous consistent state
	- This is `ROLLBACK`
*Notes*
- Committed transactions can't be rolled back
- Aborted trasactions can be restarted later

*Diagram of Transaction States*
![[Pasted image 20251207123944.png]]

## Transaction Properties
---
> Transactions follow the **ACID** properties

**A**tomicity - a transaction is an indivisible unit that is either fully performed or not at all
**C**onsistency - transactions transform DB from one consistent state to another
**I**solation - Partial effects of one transaction aren't visible to other concurrent workers
**D**urability - Effects of a comitted transaction are permanent and must not be lost due
	to later failure

*Transaction Subsystem Diagram*
![[Pasted image 20251207124822.png]]

## Concurrency Control
---
> Because operations are almost always simultaneous, operations often interfere with each other

- **Concurrency Control** prevents two or more users accessing same data while one is updating - leading to an inconsistent read or write
- Although two transactions may be correct, interleaving operations can lead to incorrect final state

### Problems From Concurrent Transactions
---
*There are three main problems caused by concurrent workers*
1. Lost update problem
2. Uncommitted dependency problem
3. Inconsistent analysis problem

### Lost Update Problem
---
> A successfully completed update is overridden by another user

![[transaction 2025-12-07 12.54.41.excalidraw]]

*Because $T_1$ did not receive the update from $T_2$, this +100 update is Lost
Hence **Lost Update Problem***

### Uncommitted Dependency Problem
---
> When one transaction accesses intermediate results before the first transaction is committed

![[transaction 2025-12-07 13.01.27.excalidraw]]

### Inconsistent Analysis Problem
---
> Transaction reads **several** values but second transaction updates some of them during execution first.

![[transaction 2025-12-07 13.12.06.excalidraw]]


