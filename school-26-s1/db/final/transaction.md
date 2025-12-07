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



