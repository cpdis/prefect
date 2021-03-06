---
sidebarDepth: 2
editLink: false
---
# State
---
State is the main currency in the Prefect platform. It is used to represent the current
status of a flow or task.

This module contains all Prefect state classes, all ultimately inheriting from the base State class as follows:

![diagram of state inheritances](/state_inheritance_diagram.svg){.viz-padded}

Every run is initialized with the `Pending` state, meaning that it is waiting for
execution. During execution a run will enter a `Running` state. Finally, runs become `Finished`.
 ## State
 <div class='class-sig' id='prefect-engine-state-state'><p class="prefect-sig">class </p><p class="prefect-class">prefect.engine.state.State</p>(message=None, result=NoResult)<span class="source"><a href="https://github.com/PrefectHQ/prefect/blob/master/src/prefect/engine/state.py#L24">[source]</a></span></div>

Base state class implementing the basic helper methods for checking state.

**Note:** Each state-checking method (e.g., `is_failed()`) will also return `True` for all _subclasses_ of the parent state.  So, for example: 
```python
my_state = TriggerFailed()
my_state.is_failed() # returns True

another_state = Retrying()
another_state.is_pending() # returns True

```

**Args**:     <ul class="args"><li class="args">`message (str or Exception, optional)`: Defaults to `None`. A message about the         state, which could be an `Exception` (or [`Signal`](signals.html)) that caused it.     </li><li class="args">`result (Any, optional)`: Defaults to `None`. A data payload for the state.</li></ul>

|methods: &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
|:----|
 | <div class='method-sig' id='prefect-engine-state-state-deserialize'><p class="prefect-class">prefect.engine.state.State.deserialize</p>(json_blob)<span class="source"><a href="https://github.com/PrefectHQ/prefect/blob/master/src/prefect/engine/state.py#L194">[source]</a></span></div>
<p class="methods">Deserializes the state from a dict.<br><br>**Args**:     <ul class="args"><li class="args">`json_blob (dict)`: the JSON representing the serialized state</li></ul></p>|
 | <div class='method-sig' id='prefect-engine-state-state-is-cached'><p class="prefect-class">prefect.engine.state.State.is_cached</p>()<span class="source"><a href="https://github.com/PrefectHQ/prefect/blob/master/src/prefect/engine/state.py#L113">[source]</a></span></div>
<p class="methods">Checks if the state is currently in a Cached state<br><br>**Returns**:     <ul class="args"><li class="args">`bool`: `True` if the state is Cached, `False` otherwise</li></ul></p>|
 | <div class='method-sig' id='prefect-engine-state-state-is-failed'><p class="prefect-class">prefect.engine.state.State.is_failed</p>()<span class="source"><a href="https://github.com/PrefectHQ/prefect/blob/master/src/prefect/engine/state.py#L167">[source]</a></span></div>
<p class="methods">Checks if the state is currently in a failed state<br><br>**Returns**:     <ul class="args"><li class="args">`bool`: `True` if the state is failed, `False` otherwise</li></ul></p>|
 | <div class='method-sig' id='prefect-engine-state-state-is-finished'><p class="prefect-class">prefect.engine.state.State.is_finished</p>()<span class="source"><a href="https://github.com/PrefectHQ/prefect/blob/master/src/prefect/engine/state.py#L122">[source]</a></span></div>
<p class="methods">Checks if the state is currently in a finished state<br><br>**Returns**:     <ul class="args"><li class="args">`bool`: `True` if the state is finished, `False` otherwise</li></ul></p>|
 | <div class='method-sig' id='prefect-engine-state-state-is-mapped'><p class="prefect-class">prefect.engine.state.State.is_mapped</p>()<span class="source"><a href="https://github.com/PrefectHQ/prefect/blob/master/src/prefect/engine/state.py#L176">[source]</a></span></div>
<p class="methods">Checks if the state is currently in a mapped state<br><br>**Returns**:     <ul class="args"><li class="args">`bool`: `True` if the state is mapped, `False` otherwise</li></ul></p>|
 | <div class='method-sig' id='prefect-engine-state-state-is-meta-state'><p class="prefect-class">prefect.engine.state.State.is_meta_state</p>()<span class="source"><a href="https://github.com/PrefectHQ/prefect/blob/master/src/prefect/engine/state.py#L185">[source]</a></span></div>
<p class="methods">Checks if the state is a meta state that wraps another state<br><br>**Returns**:     <ul class="args"><li class="args">`bool`: `True` if the state is a meta state, `False` otherwise</li></ul></p>|
 | <div class='method-sig' id='prefect-engine-state-state-is-pending'><p class="prefect-class">prefect.engine.state.State.is_pending</p>()<span class="source"><a href="https://github.com/PrefectHQ/prefect/blob/master/src/prefect/engine/state.py#L84">[source]</a></span></div>
<p class="methods">Checks if the state is currently in a pending state<br><br>**Returns**:     <ul class="args"><li class="args">`bool`: `True` if the state is pending, `False` otherwise</li></ul></p>|
 | <div class='method-sig' id='prefect-engine-state-state-is-retrying'><p class="prefect-class">prefect.engine.state.State.is_retrying</p>()<span class="source"><a href="https://github.com/PrefectHQ/prefect/blob/master/src/prefect/engine/state.py#L94">[source]</a></span></div>
<p class="methods">Checks if the state is currently in a retrying state<br><br>**Returns**:     <ul class="args"><li class="args">`bool`: `True` if the state is retrying, `False` otherwise</li></ul></p>|
 | <div class='method-sig' id='prefect-engine-state-state-is-running'><p class="prefect-class">prefect.engine.state.State.is_running</p>()<span class="source"><a href="https://github.com/PrefectHQ/prefect/blob/master/src/prefect/engine/state.py#L104">[source]</a></span></div>
<p class="methods">Checks if the state is currently in a running state<br><br>**Returns**:     <ul class="args"><li class="args">`bool`: `True` if the state is running, `False` otherwise</li></ul></p>|
 | <div class='method-sig' id='prefect-engine-state-state-is-scheduled'><p class="prefect-class">prefect.engine.state.State.is_scheduled</p>()<span class="source"><a href="https://github.com/PrefectHQ/prefect/blob/master/src/prefect/engine/state.py#L131">[source]</a></span></div>
<p class="methods">Checks if the state is currently in a scheduled state, which includes retrying.<br><br>**Returns**:     <ul class="args"><li class="args">`bool`: `True` if the state is skipped, `False` otherwise</li></ul></p>|
 | <div class='method-sig' id='prefect-engine-state-state-is-skipped'><p class="prefect-class">prefect.engine.state.State.is_skipped</p>()<span class="source"><a href="https://github.com/PrefectHQ/prefect/blob/master/src/prefect/engine/state.py#L149">[source]</a></span></div>
<p class="methods">Checks if the state is currently in a skipped state<br><br>**Returns**:     <ul class="args"><li class="args">`bool`: `True` if the state is skipped, `False` otherwise</li></ul></p>|
 | <div class='method-sig' id='prefect-engine-state-state-is-submitted'><p class="prefect-class">prefect.engine.state.State.is_submitted</p>()<span class="source"><a href="https://github.com/PrefectHQ/prefect/blob/master/src/prefect/engine/state.py#L140">[source]</a></span></div>
<p class="methods">Checks if the state is currently in a submitted state.<br><br>**Returns**:     <ul class="args"><li class="args">`bool`: `True` if the state is submitted, `False` otherwise</li></ul></p>|
 | <div class='method-sig' id='prefect-engine-state-state-is-successful'><p class="prefect-class">prefect.engine.state.State.is_successful</p>()<span class="source"><a href="https://github.com/PrefectHQ/prefect/blob/master/src/prefect/engine/state.py#L158">[source]</a></span></div>
<p class="methods">Checks if the state is currently in a successful state<br><br>**Returns**:     <ul class="args"><li class="args">`bool`: `True` if the state is successful, `False` otherwise</li></ul></p>|
 | <div class='method-sig' id='prefect-engine-state-state-serialize'><p class="prefect-class">prefect.engine.state.State.serialize</p>()<span class="source"><a href="https://github.com/PrefectHQ/prefect/blob/master/src/prefect/engine/state.py#L207">[source]</a></span></div>
<p class="methods">Serializes the state to a dict.<br><br>**Returns**:     <ul class="args"><li class="args">`dict`: a JSON representation of the state</li></ul></p>|

---
<br>

 ## Pending
 <div class='class-sig' id='prefect-engine-state-pending'><p class="prefect-sig">class </p><p class="prefect-class">prefect.engine.state.Pending</p>(message=None, result=NoResult, cached_inputs=None)<span class="source"><a href="https://github.com/PrefectHQ/prefect/blob/master/src/prefect/engine/state.py#L225">[source]</a></span></div>

Base Pending state; default state for new tasks.

**Args**:     <ul class="args"><li class="args">`message (str or Exception, optional)`: Defaults to `None`. A message about the         state, which could be an `Exception` (or [`Signal`](signals.html)) that caused it.     </li><li class="args">`result (Any, optional)`: Defaults to `None`. A data payload for the state.     </li><li class="args">`cached_inputs (dict)`: Defaults to `None`. A dictionary of input         keys to fully hydrated `Result`s.  Used / set if the Task requires Retries.</li></ul>


---
<br>

 ## Paused
 <div class='class-sig' id='prefect-engine-state-paused'><p class="prefect-sig">class </p><p class="prefect-class">prefect.engine.state.Paused</p>(message=None, result=NoResult, cached_inputs=None)<span class="source"><a href="https://github.com/PrefectHQ/prefect/blob/master/src/prefect/engine/state.py#L249">[source]</a></span></div>

Paused state for tasks which require manual execution.

**Args**:     <ul class="args"><li class="args">`message (str or Exception, optional)`: Defaults to `None`. A message about the         state, which could be an `Exception` (or [`Signal`](signals.html)) that caused it.     </li><li class="args">`result (Any, optional)`: Defaults to `None`. A data payload for the state.     </li><li class="args">`cached_inputs (dict)`: Defaults to `None`. A dictionary of input         keys to fully hydrated `Result`s.  Used / set if the Task requires Retries.</li></ul>


---
<br>

 ## Scheduled
 <div class='class-sig' id='prefect-engine-state-scheduled'><p class="prefect-sig">class </p><p class="prefect-class">prefect.engine.state.Scheduled</p>(message=None, result=NoResult, start_time=None, cached_inputs=None)<span class="source"><a href="https://github.com/PrefectHQ/prefect/blob/master/src/prefect/engine/state.py#L264">[source]</a></span></div>

Pending state indicating the object has been scheduled to run.

Scheduled states have a `start_time` which indicates when they are scheduled to run. Only scheduled states have this property; this is important because non-Python systems identify scheduled states by the presence of this property.

**Args**:     <ul class="args"><li class="args">`message (str or Exception, optional)`: Defaults to `None`. A message about the         state, which could be an `Exception` (or [`Signal`](signals.html)) that caused it.     </li><li class="args">`result (Any, optional)`: Defaults to `None`. A data payload for the state.     </li><li class="args">`start_time (datetime)`: time at which the task is scheduled to run     </li><li class="args">`cached_inputs (dict)`: Defaults to `None`. A dictionary of input         keys to fully hydrated `Result`s.  Used / set if the Task requires Retries.</li></ul>


---
<br>

 ## Resume
 <div class='class-sig' id='prefect-engine-state-resume'><p class="prefect-sig">class </p><p class="prefect-class">prefect.engine.state.Resume</p>(message=None, result=NoResult, start_time=None, cached_inputs=None)<span class="source"><a href="https://github.com/PrefectHQ/prefect/blob/master/src/prefect/engine/state.py#L383">[source]</a></span></div>

Resume state indicating the object can resume execution (presumably from a `Paused` state).

**Args**:     <ul class="args"><li class="args">`message (str or Exception, optional)`: Defaults to `None`. A message about the         state, which could be an `Exception` (or [`Signal`](signals.html)) that caused it.     </li><li class="args">`result (Any, optional)`: Defaults to `None`. A data payload for the state.     </li><li class="args">`start_time (datetime)`: time at which the task is scheduled to run     </li><li class="args">`cached_inputs (dict)`: Defaults to `None`. A dictionary of input         keys to fully hydrated `Result`s.  Used / set if the Task requires Retries.</li></ul>


---
<br>

 ## Retrying
 <div class='class-sig' id='prefect-engine-state-retrying'><p class="prefect-sig">class </p><p class="prefect-class">prefect.engine.state.Retrying</p>(message=None, result=NoResult, start_time=None, cached_inputs=None, run_count=None)<span class="source"><a href="https://github.com/PrefectHQ/prefect/blob/master/src/prefect/engine/state.py#L399">[source]</a></span></div>

Pending state indicating the object has been scheduled to be retried.

**Args**:     <ul class="args"><li class="args">`message (str or Exception, optional)`: Defaults to `None`. A message about the         state, which could be an `Exception` (or [`Signal`](signals.html)) that caused it.     </li><li class="args">`result (Any, optional)`: Defaults to `None`. A data payload for the state.     </li><li class="args">`start_time (datetime)`: time at which the task is scheduled to be retried     </li><li class="args">`cached_inputs (dict)`: Defaults to `None`. A dictionary of input         keys to fully hydrated `Result`s.  Used / set if the Task requires Retries.     </li><li class="args">`run_count (int)`: The number of runs that had been attempted at the time of this         Retry. Defaults to the value stored in context under "task_run_count" or 1,         if that value isn't found.</li></ul>


---
<br>

 ## Submitted
 <div class='class-sig' id='prefect-engine-state-submitted'><p class="prefect-sig">class </p><p class="prefect-class">prefect.engine.state.Submitted</p>(message=None, result=NoResult, state=None)<span class="source"><a href="https://github.com/PrefectHQ/prefect/blob/master/src/prefect/engine/state.py#L331">[source]</a></span></div>

The `Submitted` state is used to indicate that another state, usually a `Scheduled` state, has been handled. For example, if a task is in a `Retrying` state, then at the appropriate time it may be put into a `Submitted` state referencing the `Retrying` state. This communicates to the system that the retry has been handled, without losing the information contained in the `Retry` state.

The `Submitted` state should be initialized with another state, which it wraps. The wrapped state is extracted at the beginning of a task run.

**Args**:     <ul class="args"><li class="args">`message (string)`: a message for the state.     </li><li class="args">`result (Any, optional)`: Defaults to `None`.     </li><li class="args">`state (State)`: the `State` state that has been marked as         "submitted".</li></ul>


---
<br>

 ## Queued
 <div class='class-sig' id='prefect-engine-state-queued'><p class="prefect-sig">class </p><p class="prefect-class">prefect.engine.state.Queued</p>(message=None, result=NoResult, state=None, start_time=None)<span class="source"><a href="https://github.com/PrefectHQ/prefect/blob/master/src/prefect/engine/state.py#L353">[source]</a></span></div>

The `Queued` state is used to indicate that another state could not transition to a `Running` state for some reason, often a lack of available resources.

The `Queued` state should be initialized with another state, which it wraps. The wrapped state is extracted at the beginning of a task run.

**Args**:     <ul class="args"><li class="args">`message (string)`: a message for the state.     </li><li class="args">`result (Any, optional)`: Defaults to `None`.     </li><li class="args">`state (State)`: the `State` state that has been marked as         "queued".     </li><li class="args">`start_time (datetime)`: a time the state is queued until. Defaults to `now`.</li></ul>


---
<br>

 ## ClientFailed
 <div class='class-sig' id='prefect-engine-state-clientfailed'><p class="prefect-sig">class </p><p class="prefect-class">prefect.engine.state.ClientFailed</p>(message=None, result=NoResult, state=None)<span class="source"><a href="https://github.com/PrefectHQ/prefect/blob/master/src/prefect/engine/state.py#L311">[source]</a></span></div>

The `ClientFailed` state is used to indicate that the Prefect Client failed to set a task run state, and thus this task run should exit, without triggering any downstream task runs.

The `ClientFailed` state should be initialized with another state, which it wraps. The wrapped state is the state which the client attempted to set in the database, but failed to for some reason.

**Args**:     <ul class="args"><li class="args">`message (string)`: a message for the state.     </li><li class="args">`result (Any, optional)`: Defaults to `None`.     </li><li class="args">`state (State)`: the `State` state that the task run ended in</li></ul>


---
<br>

 ## Running
 <div class='class-sig' id='prefect-engine-state-running'><p class="prefect-sig">class </p><p class="prefect-class">prefect.engine.state.Running</p>(message=None, result=NoResult)<span class="source"><a href="https://github.com/PrefectHQ/prefect/blob/master/src/prefect/engine/state.py#L442">[source]</a></span></div>

Base running state. Indicates that a task is currently running.

**Args**:     <ul class="args"><li class="args">`message (str or Exception, optional)`: Defaults to `None`. A message about the         state, which could be an `Exception` (or [`Signal`](signals.html)) that caused it.     </li><li class="args">`result (Any, optional)`: Defaults to `None`. A data payload for the state.</li></ul>


---
<br>

 ## Finished
 <div class='class-sig' id='prefect-engine-state-finished'><p class="prefect-sig">class </p><p class="prefect-class">prefect.engine.state.Finished</p>(message=None, result=NoResult)<span class="source"><a href="https://github.com/PrefectHQ/prefect/blob/master/src/prefect/engine/state.py#L460">[source]</a></span></div>

Base finished state. Indicates when a class has reached some form of completion.

**Args**:     <ul class="args"><li class="args">`message (str or Exception, optional)`: Defaults to `None`. A message about the         state, which could be an `Exception` (or [`Signal`](signals.html)) that caused it.     </li><li class="args">`result (Any, optional)`: Defaults to `None`. A data payload for the state.</li></ul>


---
<br>

 ## Success
 <div class='class-sig' id='prefect-engine-state-success'><p class="prefect-sig">class </p><p class="prefect-class">prefect.engine.state.Success</p>(message=None, result=NoResult)<span class="source"><a href="https://github.com/PrefectHQ/prefect/blob/master/src/prefect/engine/state.py#L473">[source]</a></span></div>

Finished state indicating success.

**Args**:     <ul class="args"><li class="args">`message (str or Exception, optional)`: Defaults to `None`. A message about the         state, which could be an `Exception` (or [`Signal`](signals.html)) that caused it.     </li><li class="args">`result (Any, optional)`: Defaults to `None`. A data payload for the state.</li></ul>


---
<br>

 ## Cached
 <div class='class-sig' id='prefect-engine-state-cached'><p class="prefect-sig">class </p><p class="prefect-class">prefect.engine.state.Cached</p>(message=None, result=NoResult, cached_inputs=None, cached_parameters=None, cached_result_expiration=None)<span class="source"><a href="https://github.com/PrefectHQ/prefect/blob/master/src/prefect/engine/state.py#L486">[source]</a></span></div>

Cached, which represents a Task whose outputs have been cached.

**Args**:     <ul class="args"><li class="args">`message (str or Exception, optional)`: Defaults to `None`. A message about the         state, which could be an `Exception` (or [`Signal`](signals.html)) that caused it.     </li><li class="args">`result (Any, optional)`: Defaults to `None`. A data payload for the         state, which will be cached.     </li><li class="args">`cached_inputs (dict)`: Defaults to `None`. A dictionary of input         keys to fully hydrated `Result`s.  Used / set if the Task requires Retries.     </li><li class="args">`cached_parameters (dict)`: Defaults to `None`     </li><li class="args">`cached_result_expiration (datetime)`: The time at which this cache         expires and can no longer be used. Defaults to `None`</li></ul>


---
<br>

 ## Mapped
 <div class='class-sig' id='prefect-engine-state-mapped'><p class="prefect-sig">class </p><p class="prefect-class">prefect.engine.state.Mapped</p>(message=None, result=NoResult, map_states=None)<span class="source"><a href="https://github.com/PrefectHQ/prefect/blob/master/src/prefect/engine/state.py#L522">[source]</a></span></div>

State indicated this task was mapped over, and all mapped tasks were _submitted_ successfully. Note that this does _not_ imply the individual mapped tasks were successful, just that they have been submitted.

You can not set the `result` of a Mapped state; it is determined by the results of its children states.

**Args**:     <ul class="args"><li class="args">`message (str or Exception, optional)`: Defaults to `None`. A message about the         state, which could be an `Exception` (or [`Signal`](signals.html)) that caused it.     </li><li class="args">`result (Any, optional)`: Defaults to `[]`. A data payload for the state.     </li><li class="args">`map_states (List)`: A list containing the states of any "children" of this task. When         a task enters a Mapped state, it indicates that it has dynamically created copies         of itself to map its operation over its inputs. Those copies are the children.</li></ul>


---
<br>

 ## Skipped
 <div class='class-sig' id='prefect-engine-state-skipped'><p class="prefect-sig">class </p><p class="prefect-class">prefect.engine.state.Skipped</p>(message=None, result=NoResult)<span class="source"><a href="https://github.com/PrefectHQ/prefect/blob/master/src/prefect/engine/state.py#L619">[source]</a></span></div>

Finished state indicating success on account of being skipped.

**Args**:     <ul class="args"><li class="args">`message (str or Exception, optional)`: Defaults to `None`. A message about the         state, which could be an `Exception` (or [`Signal`](signals.html)) that caused it.     </li><li class="args">`result (Any, optional)`: Defaults to `None`. A data payload for the state.</li></ul>


---
<br>

 ## Failed
 <div class='class-sig' id='prefect-engine-state-failed'><p class="prefect-sig">class </p><p class="prefect-class">prefect.engine.state.Failed</p>(message=None, result=NoResult)<span class="source"><a href="https://github.com/PrefectHQ/prefect/blob/master/src/prefect/engine/state.py#L556">[source]</a></span></div>

Finished state indicating failure.

**Args**:     <ul class="args"><li class="args">`message (str or Exception, optional)`: Defaults to `None`. A message about the         state, which could be an `Exception` (or [`Signal`](signals.html)) that caused it.     </li><li class="args">`result (Any, optional)`: Defaults to `None`. A data payload for the state.</li></ul>


---
<br>

 ## Aborted
 <div class='class-sig' id='prefect-engine-state-aborted'><p class="prefect-sig">class </p><p class="prefect-class">prefect.engine.state.Aborted</p>(message=None, result=NoResult)<span class="source"><a href="https://github.com/PrefectHQ/prefect/blob/master/src/prefect/engine/state.py#L569">[source]</a></span></div>

Finished state indicating that a user aborted the flow run manually.

**Args**:     <ul class="args"><li class="args">`message (str or Exception, optional)`: Defaults to `None`. A message about the         state, which could be an `Exception` (or [`Signal`](signals.html)) that caused it.     </li><li class="args">`result (Any, optional)`: Defaults to `None`. A data payload for the state.</li></ul>


---
<br>

 ## TriggerFailed
 <div class='class-sig' id='prefect-engine-state-triggerfailed'><p class="prefect-sig">class </p><p class="prefect-class">prefect.engine.state.TriggerFailed</p>(message=None, result=NoResult)<span class="source"><a href="https://github.com/PrefectHQ/prefect/blob/master/src/prefect/engine/state.py#L606">[source]</a></span></div>

Finished state indicating failure due to trigger.

**Args**:     <ul class="args"><li class="args">`message (str or Exception, optional)`: Defaults to `None`. A message about the         state, which could be an `Exception` (or [`Signal`](signals.html)) that caused it.     </li><li class="args">`result (Any, optional)`: Defaults to `None`. A data payload for the state.</li></ul>


---
<br>

 ## TimedOut
 <div class='class-sig' id='prefect-engine-state-timedout'><p class="prefect-sig">class </p><p class="prefect-class">prefect.engine.state.TimedOut</p>(message=None, result=NoResult, cached_inputs=None)<span class="source"><a href="https://github.com/PrefectHQ/prefect/blob/master/src/prefect/engine/state.py#L582">[source]</a></span></div>

Finished state indicating failure due to execution timeout.

**Args**:     <ul class="args"><li class="args">`message (str or Exception, optional)`: Defaults to `None`. A message about the         state, which could be an `Exception` (or [`Signal`](signals.html)) that caused it.     </li><li class="args">`result (Any, optional)`: Defaults to `None`. A data payload for the state.     </li><li class="args">`cached_inputs (dict)`: Defaults to `None`. A dictionary of input         keys to fully hydrated `Result`s.  Used / set if the Task requires Retries.</li></ul>


---
<br>


<p class="auto-gen">This documentation was auto-generated from commit <a href='https://github.com/PrefectHQ/prefect/commit/n/a'>n/a</a> </br>by Prefect 0.5.3 on May 7, 2019 at 20:46 UTC</p>