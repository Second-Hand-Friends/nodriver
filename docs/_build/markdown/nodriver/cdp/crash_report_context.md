# CrashReportContext

This domain exposes the current state of the CrashReportContext API.

*This CDP domain is experimental.*

<a id="module-nodriver.cdp.crash_report_context"></a>
* [Types]()
* [Commands]()
* [Events]()

## Types

Generally, you do not need to instantiate CDP types
yourself. Instead, the API creates objects for you as return
values from commands, and then you can use those objects as
arguments to other commands.

### *class* CrashReportContextEntry(key, value, frame_id)

Key-value pair in CrashReportContext.

#### key *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### value *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### frame_id *: [FrameId](page.md#nodriver.cdp.page.FrameId)*

The ID of the frame where the key-value pair was set.

## Commands

Each command is a generator function. The return
type `Generator[x, y, z]` indicates that the generator
*yields* arguments of type `x`, it must be resumed with
an argument of type `y`, and it returns type `z`. In
this library, types `x` and `y` are the same for all
commands, and `z` is the return type you should pay attention
to. For more information, see
[Getting Started: Commands](../../readme.md#getting-started-commands).

### get_entries()

Returns all entries in the CrashReportContext across all frames in the page.

* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`List`](https://docs.python.org/3/library/typing.html#typing.List)[[`CrashReportContextEntry`](#nodriver.cdp.crash_report_context.CrashReportContextEntry)]]
* **Returns:**

## Events

*There are no events in this module.*
