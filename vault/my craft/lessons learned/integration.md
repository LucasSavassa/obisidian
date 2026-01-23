# always save context
## problem
- wanted to replicate events from one system to another system
- and do the main work in a background thread
- but didn't include all context data in the integration ticket
- so, when the worker thread attempted to execute integration
- the context data would have changed already
- and the worker wasn't able to replicate the event
## example
- event 1: job started
- event 2: job updated
![[lessons learned.integration 2026-01-02 10.44.24.excalidraw]]
## cause
- because the integration is executed in the future
- the context data might change
- and the original context data is lost

- in the example above, the event **job started** is sent with
- the wrong start date, because the operator updated the start date before the event was executed
## solution
- add save all context in the ticket