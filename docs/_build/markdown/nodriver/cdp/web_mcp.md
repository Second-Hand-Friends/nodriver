# WebMCP

*This CDP domain is experimental.*

<a id="module-nodriver.cdp.web_mcp"></a>
* [Types]()
* [Commands]()
* [Events]()

## Types

Generally, you do not need to instantiate CDP types
yourself. Instead, the API creates objects for you as return
values from commands, and then you can use those objects as
arguments to other commands.

### *class* Annotation(read_only=None, untrusted_content=None, autosubmit=None)

Tool annotations

#### read_only *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

A hint indicating that the tool does not modify any state.

#### untrusted_content *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

UGC, 3rd party data.

* **Type:**
  A hint indicating that the tool output may contain untrusted content, ex

#### autosubmit *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

If the declarative tool was declared with the autosubmit attribute.

### *class* InvocationStatus(\*values)

Represents the status of a tool invocation.

#### COMPLETED *= 'Completed'*

#### CANCELED *= 'Canceled'*

#### ERROR *= 'Error'*

### *class* Tool(name, description, frame_id, input_schema=None, annotations=None, backend_node_id=None, stack_trace=None)

Definition of a tool that can be invoked.

#### name *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Tool name.

#### description *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Tool description.

#### frame_id *: [FrameId](page.md#nodriver.cdp.page.FrameId)*

Frame identifier associated with the tool registration.

#### input_schema *: [dict](https://docs.python.org/3/library/stdtypes.html#dict) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Schema for the tool’s input parameters.

#### annotations *: [Annotation](#nodriver.cdp.web_mcp.Annotation) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Optional annotations for the tool.

#### backend_node_id *: [BackendNodeId](dom.md#nodriver.cdp.dom.BackendNodeId) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Optional node ID for declarative tools.

#### stack_trace *: [StackTrace](runtime.md#nodriver.cdp.runtime.StackTrace) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The stack trace at the time of the registration.

### *class* RemovedTool(name, frame_id)

Definition of a tool that was removed.

#### name *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Tool name.

#### frame_id *: [FrameId](page.md#nodriver.cdp.page.FrameId)*

Frame identifier associated with the tool registration.

## Commands

Each command is a generator function. The return
type `Generator[x, y, z]` indicates that the generator
*yields* arguments of type `x`, it must be resumed with
an argument of type `y`, and it returns type `z`. In
this library, types `x` and `y` are the same for all
commands, and `z` is the return type you should pay attention
to. For more information, see
[Getting Started: Commands](../../readme.md#getting-started-commands).

### cancel_invocation(invocation_id)

Cancels a pending tool invocation.

* **Parameters:**
  **invocation_id** ([`str`](https://docs.python.org/3/library/stdtypes.html#str)) – Invocation identifier to cancel.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### disable()

Disables the WebMCP domain.

* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### enable()

Enables the WebMCP domain, allowing events to be sent. Enabling the domain will trigger a toolsAdded event for
all currently registered tools.

* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### invoke_tool(frame_id, tool_name, input_)

Invokes a registered tool.

* **Parameters:**
  * **frame_id** ([`FrameId`](page.md#nodriver.cdp.page.FrameId)) – Frame in which to invoke the tool.
  * **tool_name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str)) – Name of the tool to invoke.
  * **input** – Input parameters for the tool, matching the tool’s inputSchema.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`str`](https://docs.python.org/3/library/stdtypes.html#str)]
* **Returns:**
  Unique identifier for this invocation. Response is sent before tool events.

## Events

Generally, you do not need to instantiate CDP events
yourself. Instead, the API creates events for you and then
you use the event’s attributes.

### *class* ToolsAdded(tools)

Event fired when new tools are added.

#### tools *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[Tool](#nodriver.cdp.web_mcp.Tool)]*

Array of tools that were added.

### *class* ToolsRemoved(tools)

Event fired when tools are removed.

#### tools *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[RemovedTool](#nodriver.cdp.web_mcp.RemovedTool)]*

Array of tools that were removed.

### *class* ToolInvoked(tool_name, frame_id, invocation_id, input_)

Event fired when a tool invocation starts.

#### tool_name *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Name of the tool to invoke.

#### frame_id *: [FrameId](page.md#nodriver.cdp.page.FrameId)*

Frame id

#### invocation_id *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Invocation identifier.

#### input_ *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

The input parameters used for the invocation.

### *class* ToolResponded(invocation_id, status, output, error_text, exception)

Event fired when a tool invocation completes or fails.

#### invocation_id *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Invocation identifier.

#### status *: [InvocationStatus](#nodriver.cdp.web_mcp.InvocationStatus)*

Status of the invocation.

#### output *: [Any](https://docs.python.org/3/library/typing.html#typing.Any) | [None](https://docs.python.org/3/library/constants.html#None)*

Output or error delivered as delivered to the agent. Missing if `status` is anything other than Completed.
Note: The output is untrusted and poses a prompt injection risk. Clients should treat this as potentially malicious user input.

#### error_text *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)*

Error text for protocol users.

#### exception *: [RemoteObject](runtime.md#nodriver.cdp.runtime.RemoteObject) | [None](https://docs.python.org/3/library/constants.html#None)*

The exception object, if the javascript tool threw an error>
