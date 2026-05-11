# Target

Supports additional targets discovery and allows to attach to them.

<a id="module-nodriver.cdp.target"></a>
* [Types]()
* [Commands]()
* [Events]()

## Types

Generally, you do not need to instantiate CDP types
yourself. Instead, the API creates objects for you as return
values from commands, and then you can use those objects as
arguments to other commands.

### *class* TargetID

### *class* SessionID

Unique identifier of attached debugging session.

### *class* TargetInfo(target_id, type_, title, url, attached, can_access_opener, parent_id=None, opener_id=None, opener_frame_id=None, parent_frame_id=None, browser_context_id=None, subtype=None)

#### target_id *: [TargetID](#nodriver.cdp.target.TargetID)*

#### type_ *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

//source.chromium.org/chromium/chromium/src/+/main:content/browser/devtools/devtools_agent_host_impl.cc?ss=chromium&q=f:devtools%20-f:out%20%22::kTypeTab%5B%5D%22

* **Type:**
  List of types
* **Type:**
  https

#### title *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### url *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### attached *: [bool](https://docs.python.org/3/library/functions.html#bool)*

Whether the target has an attached client.

#### can_access_opener *: [bool](https://docs.python.org/3/library/functions.html#bool)*

Whether the target has access to the originating window.

#### parent_id *: [TargetID](#nodriver.cdp.target.TargetID) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Id of the parent target, if any. For example, “iframe” target may have a “page” parent.

#### opener_id *: [TargetID](#nodriver.cdp.target.TargetID) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Opener target Id

#### opener_frame_id *: [FrameId](page.md#nodriver.cdp.page.FrameId) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Frame id of originating window (is only set if target has an opener).

#### parent_frame_id *: [FrameId](page.md#nodriver.cdp.page.FrameId) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Id of the parent frame, present for “iframe” and “worker” targets. For nested workers,
this is the “ancestor” frame that created the first worker in the nested chain.

#### browser_context_id *: [BrowserContextID](browser.md#nodriver.cdp.browser.BrowserContextID) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### subtype *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Provides additional details for specific target types. For example, for
the type of “page”, this may be set to “prerender”.

### *class* FilterEntry(exclude=None, type_=None)

A filter used by target query/discovery/auto-attach operations.

#### exclude *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

If set, causes exclusion of matching targets from the list.

#### type_ *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

If not present, matches any type.

### *class* TargetFilter(iterable=(),)

The entries in TargetFilter are matched sequentially against targets and
the first entry that matches determines if the target is included or not,
depending on the value of `exclude` field in the entry.
If filter is not specified, the one assumed is
[{type: “browser”, exclude: true}, {type: “tab”, exclude: true}, {}]
(i.e. include everything but `browser` and `tab`).

### *class* RemoteLocation(host, port)

#### host *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### port *: [int](https://docs.python.org/3/library/functions.html#int)*

### *class* WindowState(\*values)

The state of the target window.

#### NORMAL *= 'normal'*

#### MINIMIZED *= 'minimized'*

#### MAXIMIZED *= 'maximized'*

#### FULLSCREEN *= 'fullscreen'*

## Commands

Each command is a generator function. The return
type `Generator[x, y, z]` indicates that the generator
*yields* arguments of type `x`, it must be resumed with
an argument of type `y`, and it returns type `z`. In
this library, types `x` and `y` are the same for all
commands, and `z` is the return type you should pay attention
to. For more information, see
[Getting Started: Commands](../../readme.md#getting-started-commands).

### activate_target(target_id)

Activates (focuses) the target.

* **Parameters:**
  **target_id** ([`TargetID`](#nodriver.cdp.target.TargetID))
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### attach_to_browser_target()

Attaches to the browser target, only uses flat sessionId mode.

**EXPERIMENTAL**

* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`SessionID`](#nodriver.cdp.target.SessionID)]
* **Returns:**
  Id assigned to the session.

### attach_to_target(target_id, flatten=None)

Attaches to the target with given id.

* **Parameters:**
  * **target_id** ([`TargetID`](#nodriver.cdp.target.TargetID))
  * **flatten** ([`bool`](https://docs.python.org/3/library/functions.html#bool) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* Enables “flat” access to the session via specifying sessionId attribute in the commands. We plan to make this the default, deprecate non-flattened mode, and eventually retire it. See crbug.com/991325.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`SessionID`](#nodriver.cdp.target.SessionID)]
* **Returns:**
  Id assigned to the session.

### auto_attach_related(target_id, wait_for_debugger_on_start, filter_=None)

Adds the specified target to the list of targets that will be monitored for any related target
creation (such as child frames, child workers and new versions of service worker) and reported
through `attachedToTarget`. The specified target is also auto-attached.
This cancels the effect of any previous `setAutoAttach` and is also cancelled by subsequent
`setAutoAttach`. Only available at the Browser target.

**EXPERIMENTAL**

* **Parameters:**
  * **target_id** ([`TargetID`](#nodriver.cdp.target.TargetID))
  * **wait_for_debugger_on_start** ([`bool`](https://docs.python.org/3/library/functions.html#bool)) – Whether to pause new targets when attaching to them. Use ``Runtime.runIfWaitingForDebugger`` to run paused targets.
  * **filter** – **(EXPERIMENTAL)**  *(Optional)* Only targets matching filter will be attached.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### close_target(target_id)

Closes the target. If the target is a page that gets closed too.

* **Parameters:**
  **target_id** ([`TargetID`](#nodriver.cdp.target.TargetID))
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`bool`](https://docs.python.org/3/library/functions.html#bool)]
* **Returns:**
  Always set to true. If an error occurs, the response indicates protocol error.

### create_browser_context(dispose_on_detach=None, proxy_server=None, proxy_bypass_list=None, origins_with_universal_network_access=None)

Creates a new empty BrowserContext. Similar to an incognito profile but you can have more than
one.

* **Parameters:**
  * **dispose_on_detach** ([`bool`](https://docs.python.org/3/library/functions.html#bool) | [`None`](https://docs.python.org/3/library/constants.html#None)) – **(EXPERIMENTAL)**  *(Optional)* If specified, disposes this context when debugging session disconnects.
  * **proxy_server** ([`str`](https://docs.python.org/3/library/stdtypes.html#str) | [`None`](https://docs.python.org/3/library/constants.html#None)) – **(EXPERIMENTAL)**  *(Optional)* Proxy server, similar to the one passed to –proxy-server
  * **proxy_bypass_list** ([`str`](https://docs.python.org/3/library/stdtypes.html#str) | [`None`](https://docs.python.org/3/library/constants.html#None)) – **(EXPERIMENTAL)**  *(Optional)* Proxy bypass list, similar to the one passed to –proxy-bypass-list
  * **origins_with_universal_network_access** ([`List`](https://docs.python.org/3/library/typing.html#typing.List)[[`str`](https://docs.python.org/3/library/stdtypes.html#str)] | [`None`](https://docs.python.org/3/library/constants.html#None)) – **(EXPERIMENTAL)**  *(Optional)* An optional list of origins to grant unlimited cross-origin access to. Parts of the URL other than those constituting origin are ignored.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`BrowserContextID`](browser.md#nodriver.cdp.browser.BrowserContextID)]
* **Returns:**
  The id of the context created.

### create_target(url, left=None, top=None, width=None, height=None, window_state=None, browser_context_id=None, enable_begin_frame_control=None, new_window=None, background=None, for_tab=None, hidden=None, focus=None)

Creates a new page.

* **Parameters:**
  * **url** ([`str`](https://docs.python.org/3/library/stdtypes.html#str)) – The initial URL the page will be navigated to. An empty string indicates [about:blank](about:blank).
  * **left** ([`int`](https://docs.python.org/3/library/functions.html#int) | [`None`](https://docs.python.org/3/library/constants.html#None)) – **(EXPERIMENTAL)**  *(Optional)* Frame left origin in DIP (requires newWindow to be true or headless shell).
  * **top** ([`int`](https://docs.python.org/3/library/functions.html#int) | [`None`](https://docs.python.org/3/library/constants.html#None)) – **(EXPERIMENTAL)**  *(Optional)* Frame top origin in DIP (requires newWindow to be true or headless shell).
  * **width** ([`int`](https://docs.python.org/3/library/functions.html#int) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* Frame width in DIP (requires newWindow to be true or headless shell).
  * **height** ([`int`](https://docs.python.org/3/library/functions.html#int) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* Frame height in DIP (requires newWindow to be true or headless shell).
  * **window_state** ([`WindowState`](#nodriver.cdp.target.WindowState) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* Frame window state (requires newWindow to be true or headless shell). Default is normal.
  * **browser_context_id** ([`BrowserContextID`](browser.md#nodriver.cdp.browser.BrowserContextID) | [`None`](https://docs.python.org/3/library/constants.html#None)) – **(EXPERIMENTAL)**  *(Optional)* The browser context to create the page in.
  * **enable_begin_frame_control** ([`bool`](https://docs.python.org/3/library/functions.html#bool) | [`None`](https://docs.python.org/3/library/constants.html#None)) – **(EXPERIMENTAL)**  *(Optional)* Whether BeginFrames for this target will be controlled via DevTools (headless shell only, not supported on MacOS yet, false by default).
  * **new_window** ([`bool`](https://docs.python.org/3/library/functions.html#bool) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* Whether to create a new Window or Tab (false by default, not supported by headless shell).
  * **background** ([`bool`](https://docs.python.org/3/library/functions.html#bool) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* Whether to create the target in background or foreground (false by default, not supported by headless shell).
  * **for_tab** ([`bool`](https://docs.python.org/3/library/functions.html#bool) | [`None`](https://docs.python.org/3/library/constants.html#None)) – **(EXPERIMENTAL)**  *(Optional)* Whether to create the target of type “tab”.
  * **hidden** ([`bool`](https://docs.python.org/3/library/functions.html#bool) | [`None`](https://docs.python.org/3/library/constants.html#None)) – **(EXPERIMENTAL)**  *(Optional)* Whether to create a hidden target. The hidden target is observable via protocol, but not present in the tab UI strip. Cannot be created with ``forTab: true```, ```newWindow: true``` or ```background: false``. The life-time of the tab is limited to the life-time of the session.
  * **focus** ([`bool`](https://docs.python.org/3/library/functions.html#bool) | [`None`](https://docs.python.org/3/library/constants.html#None)) – **(EXPERIMENTAL)**  *(Optional)* If specified, the option is used to determine if the new target should be focused or not. By default, the focus behavior depends on the value of the background field. For example, background=false and focus=false will result in the target tab being opened but the browser window remain unchanged (if it was in the background, it will remain in the background) and background=false with focus=undefined will result in the window being focused. Using background: true and focus: true is not supported and will result in an error.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`TargetID`](#nodriver.cdp.target.TargetID)]
* **Returns:**
  The id of the page opened.

### detach_from_target(session_id=None, target_id=None)

Detaches session with given id.

* **Parameters:**
  * **session_id** ([`SessionID`](#nodriver.cdp.target.SessionID) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* Session to detach.
  * **target_id** ([`TargetID`](#nodriver.cdp.target.TargetID) | [`None`](https://docs.python.org/3/library/constants.html#None)) – **(DEPRECATED)**  *(Optional)* Deprecated.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### dispose_browser_context(browser_context_id)

Deletes a BrowserContext. All the belonging pages will be closed without calling their
beforeunload hooks.

* **Parameters:**
  **browser_context_id** ([`BrowserContextID`](browser.md#nodriver.cdp.browser.BrowserContextID))
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### expose_dev_tools_protocol(target_id, binding_name=None, inherit_permissions=None)

Inject object to the target’s main frame that provides a communication
channel with browser target.

Injected object will be available as `window[bindingName]`.

The object has the following API:
- `binding.send(json)` - a method to send messages over the remote debugging protocol
- `binding.onmessage = json => handleMessage(json)` - a callback that will be called for the protocol notifications and command responses.

**EXPERIMENTAL**

* **Parameters:**
  * **target_id** ([`TargetID`](#nodriver.cdp.target.TargetID))
  * **binding_name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* Binding name, ‘cdp’ if not specified.
  * **inherit_permissions** ([`bool`](https://docs.python.org/3/library/functions.html#bool) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* If true, inherits the current root session’s permissions (default: false).
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### get_browser_contexts()

Returns all browser contexts created with `Target.createBrowserContext` method.

* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Tuple`](https://docs.python.org/3/library/typing.html#typing.Tuple)[[`List`](https://docs.python.org/3/library/typing.html#typing.List)[[`BrowserContextID`](browser.md#nodriver.cdp.browser.BrowserContextID)], [`BrowserContextID`](browser.md#nodriver.cdp.browser.BrowserContextID) | [`None`](https://docs.python.org/3/library/constants.html#None)]]
* **Returns:**
  A tuple with the following items:
  1. **browserContextIds** - An array of browser context ids.
  2. **defaultBrowserContextId** -  *(Optional)* The id of the default browser context if available.

### get_dev_tools_target(target_id)

Gets the targetId of the DevTools page target opened for the given target
(if any).

**EXPERIMENTAL**

* **Parameters:**
  **target_id** ([`TargetID`](#nodriver.cdp.target.TargetID)) – Page or tab target ID.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`TargetID`](#nodriver.cdp.target.TargetID) | [`None`](https://docs.python.org/3/library/constants.html#None)]
* **Returns:**
   *(Optional)* The targetId of DevTools page target if exists.

### get_target_info(target_id=None)

Returns information about a target.

**EXPERIMENTAL**

* **Parameters:**
  **target_id** ([`TargetID`](#nodriver.cdp.target.TargetID) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)*
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`TargetInfo`](#nodriver.cdp.target.TargetInfo)]
* **Returns:**

### get_targets(filter_=None)

Retrieves a list of available targets.

* **Parameters:**
  **filter** – **(EXPERIMENTAL)**  *(Optional)* Only targets matching filter will be reported. If filter is not specified and target discovery is currently enabled, a filter used for target discovery is used for consistency.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`List`](https://docs.python.org/3/library/typing.html#typing.List)[[`TargetInfo`](#nodriver.cdp.target.TargetInfo)]]
* **Returns:**
  The list of targets.

### open_dev_tools(target_id, panel_id=None)

Opens a DevTools window for the target.

**EXPERIMENTAL**

* **Parameters:**
  * **target_id** ([`TargetID`](#nodriver.cdp.target.TargetID)) – This can be the page or tab target ID.
  * **panel_id** ([`str`](https://docs.python.org/3/library/stdtypes.html#str) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* The id of the panel we want DevTools to open initially. Currently supported panels are elements, console, network, sources, resources and performance.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`TargetID`](#nodriver.cdp.target.TargetID)]
* **Returns:**
  The targetId of DevTools page target.

### send_message_to_target(message, session_id=None, target_id=None)

Sends protocol message over session with given id.
Consider using flat mode instead; see commands attachToTarget, setAutoAttach,
and crbug.com/991325.

#### Deprecated
Deprecated since version 1.3.

* **Parameters:**
  * **message** ([`str`](https://docs.python.org/3/library/stdtypes.html#str))
  * **session_id** ([`SessionID`](#nodriver.cdp.target.SessionID) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* Identifier of the session.
  * **target_id** ([`TargetID`](#nodriver.cdp.target.TargetID) | [`None`](https://docs.python.org/3/library/constants.html#None)) – **(DEPRECATED)**  *(Optional)* Deprecated.

#### Deprecated
Deprecated since version 1.3.

* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### set_auto_attach(auto_attach, wait_for_debugger_on_start, flatten=None, filter_=None)

Controls whether to automatically attach to new targets which are considered
to be directly related to this one (for example, iframes or workers).
When turned on, attaches to all existing related targets as well. When turned off,
automatically detaches from all currently attached targets.
This also clears all targets added by `autoAttachRelated` from the list of targets to watch
for creation of related targets.
You might want to call this recursively for auto-attached targets to attach
to all available targets.

* **Parameters:**
  * **auto_attach** ([`bool`](https://docs.python.org/3/library/functions.html#bool)) – Whether to auto-attach to related targets.
  * **wait_for_debugger_on_start** ([`bool`](https://docs.python.org/3/library/functions.html#bool)) – Whether to pause new targets when attaching to them. Use ``Runtime.runIfWaitingForDebugger`` to run paused targets.
  * **flatten** ([`bool`](https://docs.python.org/3/library/functions.html#bool) | [`None`](https://docs.python.org/3/library/constants.html#None)) – **(EXPERIMENTAL)**  *(Optional)* Enables “flat” access to the session via specifying sessionId attribute in the commands. We plan to make this the default, deprecate non-flattened mode, and eventually retire it. See crbug.com/991325.
  * **filter** – **(EXPERIMENTAL)**  *(Optional)* Only targets matching filter will be attached.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### set_discover_targets(discover, filter_=None)

Controls whether to discover available targets and notify via
`targetCreated/targetInfoChanged/targetDestroyed` events.

* **Parameters:**
  * **discover** ([`bool`](https://docs.python.org/3/library/functions.html#bool)) – Whether to discover available targets.
  * **filter** – **(EXPERIMENTAL)**  *(Optional)* Only targets matching filter will be attached. If ``discover``` is false, ```filter`` must be omitted or empty.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### set_remote_locations(locations)

Enables target discovery for the specified locations, when `setDiscoverTargets` was set to
`true`.

**EXPERIMENTAL**

* **Parameters:**
  **locations** ([`List`](https://docs.python.org/3/library/typing.html#typing.List)[[`RemoteLocation`](#nodriver.cdp.target.RemoteLocation)]) – List of remote locations.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

## Events

Generally, you do not need to instantiate CDP events
yourself. Instead, the API creates events for you and then
you use the event’s attributes.

### *class* AttachedToTarget(session_id, target_info, waiting_for_debugger)

**EXPERIMENTAL**

Issued when attached to target because of auto-attach or `attachToTarget` command.

#### session_id *: [SessionID](#nodriver.cdp.target.SessionID)*

Identifier assigned to the session used to send/receive messages.

#### target_info *: [TargetInfo](#nodriver.cdp.target.TargetInfo)*

#### waiting_for_debugger *: [bool](https://docs.python.org/3/library/functions.html#bool)*

### *class* DetachedFromTarget(session_id, target_id)

**EXPERIMENTAL**

Issued when detached from target for any reason (including `detachFromTarget` command). Can be
issued multiple times per target if multiple sessions have been attached to it.

#### session_id *: [SessionID](#nodriver.cdp.target.SessionID)*

Detached session identifier.

#### target_id *: [TargetID](#nodriver.cdp.target.TargetID) | [None](https://docs.python.org/3/library/constants.html#None)*

Deprecated.

### *class* ReceivedMessageFromTarget(session_id, message, target_id)

Notifies about a new protocol message received from the session (as reported in
`attachedToTarget` event).

#### session_id *: [SessionID](#nodriver.cdp.target.SessionID)*

Identifier of a session which sends a message.

#### message *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### target_id *: [TargetID](#nodriver.cdp.target.TargetID) | [None](https://docs.python.org/3/library/constants.html#None)*

Deprecated.

### *class* TargetCreated(target_info)

Issued when a possible inspection target is created.

#### target_info *: [TargetInfo](#nodriver.cdp.target.TargetInfo)*

### *class* TargetDestroyed(target_id)

Issued when a target is destroyed.

#### target_id *: [TargetID](#nodriver.cdp.target.TargetID)*

### *class* TargetCrashed(target_id, status, error_code)

Issued when a target has crashed.

#### target_id *: [TargetID](#nodriver.cdp.target.TargetID)*

#### status *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Termination status type.

#### error_code *: [int](https://docs.python.org/3/library/functions.html#int)*

Termination error code.

### *class* TargetInfoChanged(target_info)

Issued when some information about a target has changed. This only happens between
`targetCreated` and `targetDestroyed`.

#### target_info *: [TargetInfo](#nodriver.cdp.target.TargetInfo)*
