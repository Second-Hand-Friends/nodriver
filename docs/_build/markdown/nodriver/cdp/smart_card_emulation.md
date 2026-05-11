# SmartCardEmulation

*This CDP domain is experimental.*

<a id="module-nodriver.cdp.smart_card_emulation"></a>
* [Types]()
* [Commands]()
* [Events]()

## Types

Generally, you do not need to instantiate CDP types
yourself. Instead, the API creates objects for you as return
values from commands, and then you can use those objects as
arguments to other commands.

### *class* ResultCode(\*values)

Indicates the PC/SC error code.

This maps to:
PC/SC Lite: [https://pcsclite.apdu.fr/api/group_\_ErrorCodes.html](https://pcsclite.apdu.fr/api/group__ErrorCodes.html)
Microsoft: [https://learn.microsoft.com/en-us/windows/win32/secauthn/authentication-return-values](https://learn.microsoft.com/en-us/windows/win32/secauthn/authentication-return-values)

#### SUCCESS *= 'success'*

#### REMOVED_CARD *= 'removed-card'*

#### RESET_CARD *= 'reset-card'*

#### UNPOWERED_CARD *= 'unpowered-card'*

#### UNRESPONSIVE_CARD *= 'unresponsive-card'*

#### UNSUPPORTED_CARD *= 'unsupported-card'*

#### READER_UNAVAILABLE *= 'reader-unavailable'*

#### SHARING_VIOLATION *= 'sharing-violation'*

#### NOT_TRANSACTED *= 'not-transacted'*

#### NO_SMARTCARD *= 'no-smartcard'*

#### PROTO_MISMATCH *= 'proto-mismatch'*

#### SYSTEM_CANCELLED *= 'system-cancelled'*

#### NOT_READY *= 'not-ready'*

#### CANCELLED *= 'cancelled'*

#### INSUFFICIENT_BUFFER *= 'insufficient-buffer'*

#### INVALID_HANDLE *= 'invalid-handle'*

#### INVALID_PARAMETER *= 'invalid-parameter'*

#### INVALID_VALUE *= 'invalid-value'*

#### NO_MEMORY *= 'no-memory'*

#### TIMEOUT *= 'timeout'*

#### UNKNOWN_READER *= 'unknown-reader'*

#### UNSUPPORTED_FEATURE *= 'unsupported-feature'*

#### NO_READERS_AVAILABLE *= 'no-readers-available'*

#### SERVICE_STOPPED *= 'service-stopped'*

#### NO_SERVICE *= 'no-service'*

#### COMM_ERROR *= 'comm-error'*

#### INTERNAL_ERROR *= 'internal-error'*

#### SERVER_TOO_BUSY *= 'server-too-busy'*

#### UNEXPECTED *= 'unexpected'*

#### SHUTDOWN *= 'shutdown'*

#### UNKNOWN_CARD *= 'unknown-card'*

#### UNKNOWN *= 'unknown'*

### *class* ShareMode(\*values)

Maps to the `SCARD_SHARE_*` values.

#### SHARED *= 'shared'*

#### EXCLUSIVE *= 'exclusive'*

#### DIRECT *= 'direct'*

### *class* Disposition(\*values)

Indicates what the reader should do with the card.

#### LEAVE_CARD *= 'leave-card'*

#### RESET_CARD *= 'reset-card'*

#### UNPOWER_CARD *= 'unpower-card'*

#### EJECT_CARD *= 'eject-card'*

### *class* ConnectionState(\*values)

Maps to `SCARD_*` connection state values.

#### ABSENT *= 'absent'*

#### PRESENT *= 'present'*

#### SWALLOWED *= 'swallowed'*

#### POWERED *= 'powered'*

#### NEGOTIABLE *= 'negotiable'*

#### SPECIFIC *= 'specific'*

### *class* ReaderStateFlags(unaware=None, ignore=None, changed=None, unknown=None, unavailable=None, empty=None, present=None, exclusive=None, inuse=None, mute=None, unpowered=None)

Maps to the `SCARD_STATE_*` flags.

#### unaware *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### ignore *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### changed *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### unknown *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### unavailable *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### empty *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### present *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### exclusive *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### inuse *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### mute *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### unpowered *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

### *class* ProtocolSet(t0=None, t1=None, raw=None)

Maps to the `SCARD_PROTOCOL_*` flags.

#### t0 *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### t1 *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### raw *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

### *class* Protocol(\*values)

Maps to the `SCARD_PROTOCOL_*` values.

#### T0 *= 't0'*

#### T1 *= 't1'*

#### RAW *= 'raw'*

### *class* ReaderStateIn(reader, current_state, current_insertion_count)

#### reader *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### current_state *: [ReaderStateFlags](#nodriver.cdp.smart_card_emulation.ReaderStateFlags)*

#### current_insertion_count *: [int](https://docs.python.org/3/library/functions.html#int)*

### *class* ReaderStateOut(reader, event_state, event_count, atr)

#### reader *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### event_state *: [ReaderStateFlags](#nodriver.cdp.smart_card_emulation.ReaderStateFlags)*

#### event_count *: [int](https://docs.python.org/3/library/functions.html#int)*

#### atr *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

## Commands

Each command is a generator function. The return
type `Generator[x, y, z]` indicates that the generator
*yields* arguments of type `x`, it must be resumed with
an argument of type `y`, and it returns type `z`. In
this library, types `x` and `y` are the same for all
commands, and `z` is the return type you should pay attention
to. For more information, see
[Getting Started: Commands](../../readme.md#getting-started-commands).

### disable()

Disables the `SmartCardEmulation` domain.

* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### enable()

Enables the `SmartCardEmulation` domain.

* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### report_begin_transaction_result(request_id, handle)

Reports the result of a `SCardBeginTransaction` call.
On success, this creates a new transaction object.

This maps to:
PC/SC Lite: [https://pcsclite.apdu.fr/api/group_\_API.html#gaddb835dce01a0da1d6ca02d33ee7d861](https://pcsclite.apdu.fr/api/group__API.html#gaddb835dce01a0da1d6ca02d33ee7d861)
Microsoft: [https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardbegintransaction](https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardbegintransaction)

* **Parameters:**
  * **request_id** ([`str`](https://docs.python.org/3/library/stdtypes.html#str))
  * **handle** ([`int`](https://docs.python.org/3/library/functions.html#int))
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### report_connect_result(request_id, handle, active_protocol=None)

Reports the successful result of a `SCardConnect` call.

This maps to:
PC/SC Lite: [https://pcsclite.apdu.fr/api/group_\_API.html#ga4e515829752e0a8dbc4d630696a8d6a5](https://pcsclite.apdu.fr/api/group__API.html#ga4e515829752e0a8dbc4d630696a8d6a5)
Microsoft: [https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardconnecta](https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardconnecta)

* **Parameters:**
  * **request_id** ([`str`](https://docs.python.org/3/library/stdtypes.html#str))
  * **handle** ([`int`](https://docs.python.org/3/library/functions.html#int))
  * **active_protocol** ([`Protocol`](#nodriver.cdp.smart_card_emulation.Protocol) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)*
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### report_data_result(request_id, data)

Reports the successful result of a call that sends back data on success.
Used for `SCardTransmit`, `SCardControl`, and `SCardGetAttrib`.

This maps to:
1. SCardTransmit

> PC/SC Lite: [https://pcsclite.apdu.fr/api/group_\_API.html#ga9a2d77242a271310269065e64633ab99](https://pcsclite.apdu.fr/api/group__API.html#ga9a2d77242a271310269065e64633ab99)
> Microsoft: [https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardtransmit](https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardtransmit)
1. SCardControl
   PC/SC Lite: [https://pcsclite.apdu.fr/api/group_\_API.html#gac3454d4657110fd7f753b2d3d8f4e32f](https://pcsclite.apdu.fr/api/group__API.html#gac3454d4657110fd7f753b2d3d8f4e32f)
   Microsoft: [https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardcontrol](https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardcontrol)
2. SCardGetAttrib
   PC/SC Lite: [https://pcsclite.apdu.fr/api/group_\_API.html#gaacfec51917255b7a25b94c5104961602](https://pcsclite.apdu.fr/api/group__API.html#gaacfec51917255b7a25b94c5104961602)
   Microsoft: [https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardgetattrib](https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardgetattrib)

* **Parameters:**
  * **request_id** ([`str`](https://docs.python.org/3/library/stdtypes.html#str))
  * **data** ([`str`](https://docs.python.org/3/library/stdtypes.html#str))
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### report_error(request_id, result_code)

Reports an error result for the given request.

* **Parameters:**
  * **request_id** ([`str`](https://docs.python.org/3/library/stdtypes.html#str))
  * **result_code** ([`ResultCode`](#nodriver.cdp.smart_card_emulation.ResultCode))
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### report_establish_context_result(request_id, context_id)

Reports the successful result of a `SCardEstablishContext` call.

This maps to:
PC/SC Lite: [https://pcsclite.apdu.fr/api/group_\_API.html#gaa1b8970169fd4883a6dc4a8f43f19b67](https://pcsclite.apdu.fr/api/group__API.html#gaa1b8970169fd4883a6dc4a8f43f19b67)
Microsoft: [https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardestablishcontext](https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardestablishcontext)

* **Parameters:**
  * **request_id** ([`str`](https://docs.python.org/3/library/stdtypes.html#str))
  * **context_id** ([`int`](https://docs.python.org/3/library/functions.html#int))
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### report_get_status_change_result(request_id, reader_states)

Reports the successful result of a `SCardGetStatusChange` call.

This maps to:
PC/SC Lite: [https://pcsclite.apdu.fr/api/group_\_API.html#ga33247d5d1257d59e55647c3bb717db24](https://pcsclite.apdu.fr/api/group__API.html#ga33247d5d1257d59e55647c3bb717db24)
Microsoft: [https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardgetstatuschangea](https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardgetstatuschangea)

* **Parameters:**
  * **request_id** ([`str`](https://docs.python.org/3/library/stdtypes.html#str))
  * **reader_states** ([`List`](https://docs.python.org/3/library/typing.html#typing.List)[[`ReaderStateOut`](#nodriver.cdp.smart_card_emulation.ReaderStateOut)])
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### report_list_readers_result(request_id, readers)

Reports the successful result of a `SCardListReaders` call.

This maps to:
PC/SC Lite: [https://pcsclite.apdu.fr/api/group_\_API.html#ga93b07815789b3cf2629d439ecf20f0d9](https://pcsclite.apdu.fr/api/group__API.html#ga93b07815789b3cf2629d439ecf20f0d9)
Microsoft: [https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardlistreadersa](https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardlistreadersa)

* **Parameters:**
  * **request_id** ([`str`](https://docs.python.org/3/library/stdtypes.html#str))
  * **readers** ([`List`](https://docs.python.org/3/library/typing.html#typing.List)[[`str`](https://docs.python.org/3/library/stdtypes.html#str)])
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### report_plain_result(request_id)

Reports the successful result of a call that returns only a result code.
Used for: `SCardCancel`, `SCardDisconnect`, `SCardSetAttrib`, `SCardEndTransaction`.

This maps to:
1. SCardCancel

> PC/SC Lite: [https://pcsclite.apdu.fr/api/group_\_API.html#gaacbbc0c6d6c0cbbeb4f4debf6fbeeee6](https://pcsclite.apdu.fr/api/group__API.html#gaacbbc0c6d6c0cbbeb4f4debf6fbeeee6)
> Microsoft: [https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardcancel](https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardcancel)
1. SCardDisconnect
   PC/SC Lite: [https://pcsclite.apdu.fr/api/group_\_API.html#ga4be198045c73ec0deb79e66c0ca1738a](https://pcsclite.apdu.fr/api/group__API.html#ga4be198045c73ec0deb79e66c0ca1738a)
   Microsoft: [https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scarddisconnect](https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scarddisconnect)
2. SCardSetAttrib
   PC/SC Lite: [https://pcsclite.apdu.fr/api/group_\_API.html#ga060f0038a4ddfd5dd2b8fadf3c3a2e4f](https://pcsclite.apdu.fr/api/group__API.html#ga060f0038a4ddfd5dd2b8fadf3c3a2e4f)
   Microsoft: [https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardsetattrib](https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardsetattrib)
3. SCardEndTransaction
   PC/SC Lite: [https://pcsclite.apdu.fr/api/group_\_API.html#gae8742473b404363e5c587f570d7e2f3b](https://pcsclite.apdu.fr/api/group__API.html#gae8742473b404363e5c587f570d7e2f3b)
   Microsoft: [https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardendtransaction](https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardendtransaction)

* **Parameters:**
  **request_id** ([`str`](https://docs.python.org/3/library/stdtypes.html#str))
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### report_release_context_result(request_id)

Reports the successful result of a `SCardReleaseContext` call.

This maps to:
PC/SC Lite: [https://pcsclite.apdu.fr/api/group_\_API.html#ga6aabcba7744c5c9419fdd6404f73a934](https://pcsclite.apdu.fr/api/group__API.html#ga6aabcba7744c5c9419fdd6404f73a934)
Microsoft: [https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardreleasecontext](https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardreleasecontext)

* **Parameters:**
  **request_id** ([`str`](https://docs.python.org/3/library/stdtypes.html#str))
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### report_status_result(request_id, reader_name, state, atr, protocol=None)

Reports the successful result of a `SCardStatus` call.

This maps to:
PC/SC Lite: [https://pcsclite.apdu.fr/api/group_\_API.html#gae49c3c894ad7ac12a5b896bde70d0382](https://pcsclite.apdu.fr/api/group__API.html#gae49c3c894ad7ac12a5b896bde70d0382)
Microsoft: [https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardstatusa](https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardstatusa)

* **Parameters:**
  * **request_id** ([`str`](https://docs.python.org/3/library/stdtypes.html#str))
  * **reader_name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str))
  * **state** ([`ConnectionState`](#nodriver.cdp.smart_card_emulation.ConnectionState))
  * **atr** ([`str`](https://docs.python.org/3/library/stdtypes.html#str))
  * **protocol** ([`Protocol`](#nodriver.cdp.smart_card_emulation.Protocol) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)*
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

## Events

Generally, you do not need to instantiate CDP events
yourself. Instead, the API creates events for you and then
you use the event’s attributes.

### *class* EstablishContextRequested(request_id)

Fired when `SCardEstablishContext` is called.

This maps to:
PC/SC Lite: [https://pcsclite.apdu.fr/api/group_\_API.html#gaa1b8970169fd4883a6dc4a8f43f19b67](https://pcsclite.apdu.fr/api/group__API.html#gaa1b8970169fd4883a6dc4a8f43f19b67)
Microsoft: [https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardestablishcontext](https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardestablishcontext)

#### request_id *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

### *class* ReleaseContextRequested(request_id, context_id)

Fired when `SCardReleaseContext` is called.

This maps to:
PC/SC Lite: [https://pcsclite.apdu.fr/api/group_\_API.html#ga6aabcba7744c5c9419fdd6404f73a934](https://pcsclite.apdu.fr/api/group__API.html#ga6aabcba7744c5c9419fdd6404f73a934)
Microsoft: [https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardreleasecontext](https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardreleasecontext)

#### request_id *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### context_id *: [int](https://docs.python.org/3/library/functions.html#int)*

### *class* ListReadersRequested(request_id, context_id)

Fired when `SCardListReaders` is called.

This maps to:
PC/SC Lite: [https://pcsclite.apdu.fr/api/group_\_API.html#ga93b07815789b3cf2629d439ecf20f0d9](https://pcsclite.apdu.fr/api/group__API.html#ga93b07815789b3cf2629d439ecf20f0d9)
Microsoft: [https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardlistreadersa](https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardlistreadersa)

#### request_id *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### context_id *: [int](https://docs.python.org/3/library/functions.html#int)*

### *class* GetStatusChangeRequested(request_id, context_id, reader_states, timeout)

Fired when `SCardGetStatusChange` is called. Timeout is specified in milliseconds.

This maps to:
PC/SC Lite: [https://pcsclite.apdu.fr/api/group_\_API.html#ga33247d5d1257d59e55647c3bb717db24](https://pcsclite.apdu.fr/api/group__API.html#ga33247d5d1257d59e55647c3bb717db24)
Microsoft: [https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardgetstatuschangea](https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardgetstatuschangea)

#### request_id *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### context_id *: [int](https://docs.python.org/3/library/functions.html#int)*

#### reader_states *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[ReaderStateIn](#nodriver.cdp.smart_card_emulation.ReaderStateIn)]*

#### timeout *: [int](https://docs.python.org/3/library/functions.html#int) | [None](https://docs.python.org/3/library/constants.html#None)*

in milliseconds, if absent, it means “infinite”

### *class* CancelRequested(request_id, context_id)

Fired when `SCardCancel` is called.

This maps to:
PC/SC Lite: [https://pcsclite.apdu.fr/api/group_\_API.html#gaacbbc0c6d6c0cbbeb4f4debf6fbeeee6](https://pcsclite.apdu.fr/api/group__API.html#gaacbbc0c6d6c0cbbeb4f4debf6fbeeee6)
Microsoft: [https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardcancel](https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardcancel)

#### request_id *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### context_id *: [int](https://docs.python.org/3/library/functions.html#int)*

### *class* ConnectRequested(request_id, context_id, reader, share_mode, preferred_protocols)

Fired when `SCardConnect` is called.

This maps to:
PC/SC Lite: [https://pcsclite.apdu.fr/api/group_\_API.html#ga4e515829752e0a8dbc4d630696a8d6a5](https://pcsclite.apdu.fr/api/group__API.html#ga4e515829752e0a8dbc4d630696a8d6a5)
Microsoft: [https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardconnecta](https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardconnecta)

#### request_id *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### context_id *: [int](https://docs.python.org/3/library/functions.html#int)*

#### reader *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### share_mode *: [ShareMode](#nodriver.cdp.smart_card_emulation.ShareMode)*

#### preferred_protocols *: [ProtocolSet](#nodriver.cdp.smart_card_emulation.ProtocolSet)*

### *class* DisconnectRequested(request_id, handle, disposition)

Fired when `SCardDisconnect` is called.

This maps to:
PC/SC Lite: [https://pcsclite.apdu.fr/api/group_\_API.html#ga4be198045c73ec0deb79e66c0ca1738a](https://pcsclite.apdu.fr/api/group__API.html#ga4be198045c73ec0deb79e66c0ca1738a)
Microsoft: [https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scarddisconnect](https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scarddisconnect)

#### request_id *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### handle *: [int](https://docs.python.org/3/library/functions.html#int)*

#### disposition *: [Disposition](#nodriver.cdp.smart_card_emulation.Disposition)*

### *class* TransmitRequested(request_id, handle, data, protocol)

Fired when `SCardTransmit` is called.

This maps to:
PC/SC Lite: [https://pcsclite.apdu.fr/api/group_\_API.html#ga9a2d77242a271310269065e64633ab99](https://pcsclite.apdu.fr/api/group__API.html#ga9a2d77242a271310269065e64633ab99)
Microsoft: [https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardtransmit](https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardtransmit)

#### request_id *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### handle *: [int](https://docs.python.org/3/library/functions.html#int)*

#### data *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### protocol *: [Protocol](#nodriver.cdp.smart_card_emulation.Protocol) | [None](https://docs.python.org/3/library/constants.html#None)*

### *class* ControlRequested(request_id, handle, control_code, data)

Fired when `SCardControl` is called.

This maps to:
PC/SC Lite: [https://pcsclite.apdu.fr/api/group_\_API.html#gac3454d4657110fd7f753b2d3d8f4e32f](https://pcsclite.apdu.fr/api/group__API.html#gac3454d4657110fd7f753b2d3d8f4e32f)
Microsoft: [https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardcontrol](https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardcontrol)

#### request_id *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### handle *: [int](https://docs.python.org/3/library/functions.html#int)*

#### control_code *: [int](https://docs.python.org/3/library/functions.html#int)*

#### data *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

### *class* GetAttribRequested(request_id, handle, attrib_id)

Fired when `SCardGetAttrib` is called.

This maps to:
PC/SC Lite: [https://pcsclite.apdu.fr/api/group_\_API.html#gaacfec51917255b7a25b94c5104961602](https://pcsclite.apdu.fr/api/group__API.html#gaacfec51917255b7a25b94c5104961602)
Microsoft: [https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardgetattrib](https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardgetattrib)

#### request_id *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### handle *: [int](https://docs.python.org/3/library/functions.html#int)*

#### attrib_id *: [int](https://docs.python.org/3/library/functions.html#int)*

### *class* SetAttribRequested(request_id, handle, attrib_id, data)

Fired when `SCardSetAttrib` is called.

This maps to:
PC/SC Lite: [https://pcsclite.apdu.fr/api/group_\_API.html#ga060f0038a4ddfd5dd2b8fadf3c3a2e4f](https://pcsclite.apdu.fr/api/group__API.html#ga060f0038a4ddfd5dd2b8fadf3c3a2e4f)
Microsoft: [https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardsetattrib](https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardsetattrib)

#### request_id *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### handle *: [int](https://docs.python.org/3/library/functions.html#int)*

#### attrib_id *: [int](https://docs.python.org/3/library/functions.html#int)*

#### data *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

### *class* StatusRequested(request_id, handle)

Fired when `SCardStatus` is called.

This maps to:
PC/SC Lite: [https://pcsclite.apdu.fr/api/group_\_API.html#gae49c3c894ad7ac12a5b896bde70d0382](https://pcsclite.apdu.fr/api/group__API.html#gae49c3c894ad7ac12a5b896bde70d0382)
Microsoft: [https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardstatusa](https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardstatusa)

#### request_id *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### handle *: [int](https://docs.python.org/3/library/functions.html#int)*

### *class* BeginTransactionRequested(request_id, handle)

Fired when `SCardBeginTransaction` is called.

This maps to:
PC/SC Lite: [https://pcsclite.apdu.fr/api/group_\_API.html#gaddb835dce01a0da1d6ca02d33ee7d861](https://pcsclite.apdu.fr/api/group__API.html#gaddb835dce01a0da1d6ca02d33ee7d861)
Microsoft: [https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardbegintransaction](https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardbegintransaction)

#### request_id *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### handle *: [int](https://docs.python.org/3/library/functions.html#int)*

### *class* EndTransactionRequested(request_id, handle, disposition)

Fired when `SCardEndTransaction` is called.

This maps to:
PC/SC Lite: [https://pcsclite.apdu.fr/api/group_\_API.html#gae8742473b404363e5c587f570d7e2f3b](https://pcsclite.apdu.fr/api/group__API.html#gae8742473b404363e5c587f570d7e2f3b)
Microsoft: [https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardendtransaction](https://learn.microsoft.com/en-us/windows/win32/api/winscard/nf-winscard-scardendtransaction)

#### request_id *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### handle *: [int](https://docs.python.org/3/library/functions.html#int)*

#### disposition *: [Disposition](#nodriver.cdp.smart_card_emulation.Disposition)*
