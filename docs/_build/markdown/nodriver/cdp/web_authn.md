# WebAuthn

This domain allows configuring virtual authenticators to test the WebAuthn
API.

*This CDP domain is experimental.*

<a id="module-nodriver.cdp.web_authn"></a>
* [Types]()
* [Commands]()
* [Events]()

## Types

Generally, you do not need to instantiate CDP types
yourself. Instead, the API creates objects for you as return
values from commands, and then you can use those objects as
arguments to other commands.

### *class* AuthenticatorId

### *class* AuthenticatorProtocol(\*values)

#### U2F *= 'u2f'*

#### CTAP2 *= 'ctap2'*

### *class* Ctap2Version(\*values)

#### CTAP2_0 *= 'ctap2_0'*

#### CTAP2_1 *= 'ctap2_1'*

#### CTAP2_2 *= 'ctap2_2'*

### *class* AuthenticatorTransport(\*values)

#### USB *= 'usb'*

#### NFC *= 'nfc'*

#### BLE *= 'ble'*

#### CABLE *= 'cable'*

#### INTERNAL *= 'internal'*

### *class* VirtualAuthenticatorOptions(protocol, transport, ctap2_version=None, has_resident_key=None, has_user_verification=None, has_large_blob=None, has_cred_blob=None, has_min_pin_length=None, has_prf=None, has_hmac_secret=None, has_hmac_secret_mc=None, automatic_presence_simulation=None, is_user_verified=None, default_backup_eligibility=None, default_backup_state=None)

#### protocol *: [AuthenticatorProtocol](#nodriver.cdp.web_authn.AuthenticatorProtocol)*

#### transport *: [AuthenticatorTransport](#nodriver.cdp.web_authn.AuthenticatorTransport)*

#### ctap2_version *: [Ctap2Version](#nodriver.cdp.web_authn.Ctap2Version) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Defaults to ctap2_0. Ignored if `protocol` == u2f.

#### has_resident_key *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Defaults to false.

#### has_user_verification *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Defaults to false.

#### has_large_blob *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

If set to true, the authenticator will support the largeBlob extension.
[https://w3c.github.io/webauthn#largeBlob](https://w3c.github.io/webauthn#largeBlob)
Defaults to false.

#### has_cred_blob *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

If set to true, the authenticator will support the credBlob extension.
[https://fidoalliance.org/specs/fido-v2.1-rd-20201208/fido-client-to-authenticator-protocol-v2.1-rd-20201208.html#sctn-credBlob-extension](https://fidoalliance.org/specs/fido-v2.1-rd-20201208/fido-client-to-authenticator-protocol-v2.1-rd-20201208.html#sctn-credBlob-extension)
Defaults to false.

#### has_min_pin_length *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

If set to true, the authenticator will support the minPinLength extension.
[https://fidoalliance.org/specs/fido-v2.1-ps-20210615/fido-client-to-authenticator-protocol-v2.1-ps-20210615.html#sctn-minpinlength-extension](https://fidoalliance.org/specs/fido-v2.1-ps-20210615/fido-client-to-authenticator-protocol-v2.1-ps-20210615.html#sctn-minpinlength-extension)
Defaults to false.

#### has_prf *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

If set to true, the authenticator will support the prf extension.
[https://w3c.github.io/webauthn/#prf-extension](https://w3c.github.io/webauthn/#prf-extension)
Defaults to false.

#### has_hmac_secret *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

If set to true, the authenticator will support the hmac-secret extension.
[https://fidoalliance.org/specs/fido-v2.1-ps-20210615/fido-client-to-authenticator-protocol-v2.1-ps-20210615.html#sctn-hmac-secret-extension](https://fidoalliance.org/specs/fido-v2.1-ps-20210615/fido-client-to-authenticator-protocol-v2.1-ps-20210615.html#sctn-hmac-secret-extension)
Defaults to false.

#### has_hmac_secret_mc *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

If set to true, the authenticator will support the hmac-secret-mc extension.
[https://fidoalliance.org/specs/fido-v2.2-rd-20241003/fido-client-to-authenticator-protocol-v2.2-rd-20241003.html#sctn-hmac-secret-make-cred-extension](https://fidoalliance.org/specs/fido-v2.2-rd-20241003/fido-client-to-authenticator-protocol-v2.2-rd-20241003.html#sctn-hmac-secret-make-cred-extension)
Defaults to false.

#### automatic_presence_simulation *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

If set to true, tests of user presence will succeed immediately.
Otherwise, they will not be resolved. Defaults to true.

#### is_user_verified *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Sets whether User Verification succeeds or fails for an authenticator.
Defaults to false.

#### default_backup_eligibility *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Credentials created by this authenticator will have the backup
eligibility (BE) flag set to this value. Defaults to false.
[https://w3c.github.io/webauthn/#sctn-credential-backup](https://w3c.github.io/webauthn/#sctn-credential-backup)

#### default_backup_state *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Credentials created by this authenticator will have the backup state
(BS) flag set to this value. Defaults to false.
[https://w3c.github.io/webauthn/#sctn-credential-backup](https://w3c.github.io/webauthn/#sctn-credential-backup)

### *class* Credential(credential_id, is_resident_credential, private_key, sign_count, rp_id=None, user_handle=None, large_blob=None, backup_eligibility=None, backup_state=None, user_name=None, user_display_name=None)

#### credential_id *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### is_resident_credential *: [bool](https://docs.python.org/3/library/functions.html#bool)*

#### private_key *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

The ECDSA P-256 private key in PKCS#8 format. (Encoded as a base64 string when passed over JSON)

#### sign_count *: [int](https://docs.python.org/3/library/functions.html#int)*

Signature counter. This is incremented by one for each successful
assertion.
See [https://w3c.github.io/webauthn/#signature-counter](https://w3c.github.io/webauthn/#signature-counter)

#### rp_id *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Relying Party ID the credential is scoped to. Must be set when adding a
credential.

#### user_handle *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

An opaque byte sequence with a maximum size of 64 bytes mapping the
credential to a specific user. (Encoded as a base64 string when passed over JSON)

#### large_blob *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The large blob associated with the credential.
See [https://w3c.github.io/webauthn/#sctn-large-blob-extension](https://w3c.github.io/webauthn/#sctn-large-blob-extension) (Encoded as a base64 string when passed over JSON)

#### backup_eligibility *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Assertions returned by this credential will have the backup eligibility
(BE) flag set to this value. Defaults to the authenticator’s
defaultBackupEligibility value.

#### backup_state *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Assertions returned by this credential will have the backup state (BS)
flag set to this value. Defaults to the authenticator’s
defaultBackupState value.

#### user_name *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The credential’s user.name property. Equivalent to empty if not set.
[https://w3c.github.io/webauthn/#dom-publickeycredentialentity-name](https://w3c.github.io/webauthn/#dom-publickeycredentialentity-name)

#### user_display_name *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The credential’s user.displayName property. Equivalent to empty if
not set.
[https://w3c.github.io/webauthn/#dom-publickeycredentialuserentity-displayname](https://w3c.github.io/webauthn/#dom-publickeycredentialuserentity-displayname)

## Commands

Each command is a generator function. The return
type `Generator[x, y, z]` indicates that the generator
*yields* arguments of type `x`, it must be resumed with
an argument of type `y`, and it returns type `z`. In
this library, types `x` and `y` are the same for all
commands, and `z` is the return type you should pay attention
to. For more information, see
[Getting Started: Commands](../../readme.md#getting-started-commands).

### add_credential(authenticator_id, credential)

Adds the credential to the specified authenticator.

* **Parameters:**
  * **authenticator_id** ([`AuthenticatorId`](#nodriver.cdp.web_authn.AuthenticatorId))
  * **credential** ([`Credential`](#nodriver.cdp.web_authn.Credential))
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### add_virtual_authenticator(options)

Creates and adds a virtual authenticator.

* **Parameters:**
  **options** ([`VirtualAuthenticatorOptions`](#nodriver.cdp.web_authn.VirtualAuthenticatorOptions))
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`AuthenticatorId`](#nodriver.cdp.web_authn.AuthenticatorId)]
* **Returns:**

### clear_credentials(authenticator_id)

Clears all the credentials from the specified device.

* **Parameters:**
  **authenticator_id** ([`AuthenticatorId`](#nodriver.cdp.web_authn.AuthenticatorId))
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### disable()

Disable the WebAuthn domain.

* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### enable(enable_ui=None)

Enable the WebAuthn domain and start intercepting credential storage and
retrieval with a virtual authenticator.

* **Parameters:**
  **enable_ui** ([`bool`](https://docs.python.org/3/library/functions.html#bool) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* Whether to enable the WebAuthn user interface. Enabling the UI is recommended for debugging and demo purposes, as it is closer to the real experience. Disabling the UI is recommended for automated testing. Supported at the embedder’s discretion if UI is available. Defaults to false.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### get_credential(authenticator_id, credential_id)

Returns a single credential stored in the given virtual authenticator that
matches the credential ID.

* **Parameters:**
  * **authenticator_id** ([`AuthenticatorId`](#nodriver.cdp.web_authn.AuthenticatorId))
  * **credential_id** ([`str`](https://docs.python.org/3/library/stdtypes.html#str))
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Credential`](#nodriver.cdp.web_authn.Credential)]
* **Returns:**

### get_credentials(authenticator_id)

Returns all the credentials stored in the given virtual authenticator.

* **Parameters:**
  **authenticator_id** ([`AuthenticatorId`](#nodriver.cdp.web_authn.AuthenticatorId))
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`List`](https://docs.python.org/3/library/typing.html#typing.List)[[`Credential`](#nodriver.cdp.web_authn.Credential)]]
* **Returns:**

### remove_credential(authenticator_id, credential_id)

Removes a credential from the authenticator.

* **Parameters:**
  * **authenticator_id** ([`AuthenticatorId`](#nodriver.cdp.web_authn.AuthenticatorId))
  * **credential_id** ([`str`](https://docs.python.org/3/library/stdtypes.html#str))
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### remove_virtual_authenticator(authenticator_id)

Removes the given authenticator.

* **Parameters:**
  **authenticator_id** ([`AuthenticatorId`](#nodriver.cdp.web_authn.AuthenticatorId))
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### set_automatic_presence_simulation(authenticator_id, enabled)

Sets whether tests of user presence will succeed immediately (if true) or fail to resolve (if false) for an authenticator.
The default is true.

* **Parameters:**
  * **authenticator_id** ([`AuthenticatorId`](#nodriver.cdp.web_authn.AuthenticatorId))
  * **enabled** ([`bool`](https://docs.python.org/3/library/functions.html#bool))
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### set_credential_properties(authenticator_id, credential_id, backup_eligibility=None, backup_state=None)

Allows setting credential properties.
[https://w3c.github.io/webauthn/#sctn-automation-set-credential-properties](https://w3c.github.io/webauthn/#sctn-automation-set-credential-properties)

* **Parameters:**
  * **authenticator_id** ([`AuthenticatorId`](#nodriver.cdp.web_authn.AuthenticatorId))
  * **credential_id** ([`str`](https://docs.python.org/3/library/stdtypes.html#str))
  * **backup_eligibility** ([`bool`](https://docs.python.org/3/library/functions.html#bool) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)*
  * **backup_state** ([`bool`](https://docs.python.org/3/library/functions.html#bool) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)*
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### set_response_override_bits(authenticator_id, is_bogus_signature=None, is_bad_uv=None, is_bad_up=None)

Resets parameters isBogusSignature, isBadUV, isBadUP to false if they are not present.

* **Parameters:**
  * **authenticator_id** ([`AuthenticatorId`](#nodriver.cdp.web_authn.AuthenticatorId))
  * **is_bogus_signature** ([`bool`](https://docs.python.org/3/library/functions.html#bool) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* If isBogusSignature is set, overrides the signature in the authenticator response to be zero. Defaults to false.
  * **is_bad_uv** ([`bool`](https://docs.python.org/3/library/functions.html#bool) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* If isBadUV is set, overrides the UV bit in the flags in the authenticator response to be zero. Defaults to false.
  * **is_bad_up** ([`bool`](https://docs.python.org/3/library/functions.html#bool) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* If isBadUP is set, overrides the UP bit in the flags in the authenticator response to be zero. Defaults to false.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### set_user_verified(authenticator_id, is_user_verified)

Sets whether User Verification succeeds or fails for an authenticator.
The default is true.

* **Parameters:**
  * **authenticator_id** ([`AuthenticatorId`](#nodriver.cdp.web_authn.AuthenticatorId))
  * **is_user_verified** ([`bool`](https://docs.python.org/3/library/functions.html#bool))
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

## Events

Generally, you do not need to instantiate CDP events
yourself. Instead, the API creates events for you and then
you use the event’s attributes.

### *class* CredentialAdded(authenticator_id, credential)

Triggered when a credential is added to an authenticator.

#### authenticator_id *: [AuthenticatorId](#nodriver.cdp.web_authn.AuthenticatorId)*

#### credential *: [Credential](#nodriver.cdp.web_authn.Credential)*

### *class* CredentialDeleted(authenticator_id, credential_id)

Triggered when a credential is deleted, e.g. through
PublicKeyCredential.signalUnknownCredential().

#### authenticator_id *: [AuthenticatorId](#nodriver.cdp.web_authn.AuthenticatorId)*

#### credential_id *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

### *class* CredentialUpdated(authenticator_id, credential)

Triggered when a credential is updated, e.g. through
PublicKeyCredential.signalCurrentUserDetails().

#### authenticator_id *: [AuthenticatorId](#nodriver.cdp.web_authn.AuthenticatorId)*

#### credential *: [Credential](#nodriver.cdp.web_authn.Credential)*

### *class* CredentialAsserted(authenticator_id, credential)

Triggered when a credential is used in a webauthn assertion.

#### authenticator_id *: [AuthenticatorId](#nodriver.cdp.web_authn.AuthenticatorId)*

#### credential *: [Credential](#nodriver.cdp.web_authn.Credential)*
