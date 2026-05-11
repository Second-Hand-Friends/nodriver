# Storage

*This CDP domain is experimental.*

<a id="module-nodriver.cdp.storage"></a>
* [Types]()
* [Commands]()
* [Events]()

## Types

Generally, you do not need to instantiate CDP types
yourself. Instead, the API creates objects for you as return
values from commands, and then you can use those objects as
arguments to other commands.

### *class* SerializedStorageKey

### *class* StorageType(\*values)

Enum of possible storage types.

#### COOKIES *= 'cookies'*

#### FILE_SYSTEMS *= 'file_systems'*

#### INDEXEDDB *= 'indexeddb'*

#### LOCAL_STORAGE *= 'local_storage'*

#### SHADER_CACHE *= 'shader_cache'*

#### WEBSQL *= 'websql'*

#### SERVICE_WORKERS *= 'service_workers'*

#### CACHE_STORAGE *= 'cache_storage'*

#### INTEREST_GROUPS *= 'interest_groups'*

#### SHARED_STORAGE *= 'shared_storage'*

#### STORAGE_BUCKETS *= 'storage_buckets'*

#### ALL_ *= 'all'*

#### OTHER *= 'other'*

### *class* UsageForType(storage_type, usage)

Usage for a storage type.

#### storage_type *: [StorageType](#nodriver.cdp.storage.StorageType)*

Name of storage type.

#### usage *: [float](https://docs.python.org/3/library/functions.html#float)*

Storage usage (bytes).

### *class* TrustTokens(issuer_origin, count)

Pair of issuer origin and number of available (signed, but not used) Trust
Tokens from that issuer.

#### issuer_origin *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### count *: [float](https://docs.python.org/3/library/functions.html#float)*

### *class* InterestGroupAuctionId

Protected audience interest group auction identifier.

### *class* InterestGroupAccessType(\*values)

Enum of interest group access types.

#### JOIN *= 'join'*

#### LEAVE *= 'leave'*

#### UPDATE *= 'update'*

#### LOADED *= 'loaded'*

#### BID *= 'bid'*

#### WIN *= 'win'*

#### ADDITIONAL_BID *= 'additionalBid'*

#### ADDITIONAL_BID_WIN *= 'additionalBidWin'*

#### TOP_LEVEL_BID *= 'topLevelBid'*

#### TOP_LEVEL_ADDITIONAL_BID *= 'topLevelAdditionalBid'*

#### CLEAR *= 'clear'*

### *class* InterestGroupAuctionEventType(\*values)

Enum of auction events.

#### STARTED *= 'started'*

#### CONFIG_RESOLVED *= 'configResolved'*

### *class* InterestGroupAuctionFetchType(\*values)

Enum of network fetches auctions can do.

#### BIDDER_JS *= 'bidderJs'*

#### BIDDER_WASM *= 'bidderWasm'*

#### SELLER_JS *= 'sellerJs'*

#### BIDDER_TRUSTED_SIGNALS *= 'bidderTrustedSignals'*

#### SELLER_TRUSTED_SIGNALS *= 'sellerTrustedSignals'*

### *class* SharedStorageAccessScope(\*values)

Enum of shared storage access scopes.

#### WINDOW *= 'window'*

#### SHARED_STORAGE_WORKLET *= 'sharedStorageWorklet'*

#### PROTECTED_AUDIENCE_WORKLET *= 'protectedAudienceWorklet'*

#### HEADER *= 'header'*

### *class* SharedStorageAccessMethod(\*values)

Enum of shared storage access methods.

#### ADD_MODULE *= 'addModule'*

#### CREATE_WORKLET *= 'createWorklet'*

#### SELECT_URL *= 'selectURL'*

#### RUN *= 'run'*

#### BATCH_UPDATE *= 'batchUpdate'*

#### SET_ *= 'set'*

#### APPEND *= 'append'*

#### DELETE *= 'delete'*

#### CLEAR *= 'clear'*

#### GET *= 'get'*

#### KEYS *= 'keys'*

#### VALUES *= 'values'*

#### ENTRIES *= 'entries'*

#### LENGTH *= 'length'*

#### REMAINING_BUDGET *= 'remainingBudget'*

### *class* SharedStorageEntry(key, value)

Struct for a single key-value pair in an origin’s shared storage.

#### key *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### value *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

### *class* SharedStorageMetadata(creation_time, length, remaining_budget, bytes_used)

Details for an origin’s shared storage.

#### creation_time *: [TimeSinceEpoch](network.md#nodriver.cdp.network.TimeSinceEpoch)*

Time when the origin’s shared storage was last created.

#### length *: [int](https://docs.python.org/3/library/functions.html#int)*

Number of key-value pairs stored in origin’s shared storage.

#### remaining_budget *: [float](https://docs.python.org/3/library/functions.html#float)*

Current amount of bits of entropy remaining in the navigation budget.

#### bytes_used *: [int](https://docs.python.org/3/library/functions.html#int)*

Total number of bytes stored as key-value pairs in origin’s shared
storage.

### *class* SharedStoragePrivateAggregationConfig(filtering_id_max_bytes, aggregation_coordinator_origin=None, context_id=None, max_contributions=None)

Represents a dictionary object passed in as privateAggregationConfig to
run or selectURL.

#### filtering_id_max_bytes *: [int](https://docs.python.org/3/library/functions.html#int)*

Configures the maximum size allowed for filtering IDs.

#### aggregation_coordinator_origin *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The chosen aggregation service deployment.

#### context_id *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The context ID provided.

#### max_contributions *: [int](https://docs.python.org/3/library/functions.html#int) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The limit on the number of contributions in the final report.

### *class* SharedStorageReportingMetadata(event_type, reporting_url)

Pair of reporting metadata details for a candidate URL for `selectURL()`.

#### event_type *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### reporting_url *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

### *class* SharedStorageUrlWithMetadata(url, reporting_metadata)

Bundles a candidate URL with its reporting metadata.

#### url *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Spec of candidate URL.

#### reporting_metadata *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[SharedStorageReportingMetadata](#nodriver.cdp.storage.SharedStorageReportingMetadata)]*

Any associated reporting metadata.

### *class* SharedStorageAccessParams(script_source_url=None, data_origin=None, operation_name=None, operation_id=None, keep_alive=None, private_aggregation_config=None, serialized_data=None, urls_with_metadata=None, urn_uuid=None, key=None, value=None, ignore_if_present=None, worklet_ordinal=None, worklet_target_id=None, with_lock=None, batch_update_id=None, batch_size=None)

Bundles the parameters for shared storage access events whose
presence/absence can vary according to SharedStorageAccessType.

#### script_source_url *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Spec of the module script URL.
Present only for SharedStorageAccessMethods: addModule and
createWorklet.

#### data_origin *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

String denoting “context-origin”, “script-origin”, or a custom
origin to be used as the worklet’s data origin.
Present only for SharedStorageAccessMethod: createWorklet.

#### operation_name *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Name of the registered operation to be run.
Present only for SharedStorageAccessMethods: run and selectURL.

#### operation_id *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

ID of the operation call.
Present only for SharedStorageAccessMethods: run and selectURL.

#### keep_alive *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Whether or not to keep the worket alive for future run or selectURL
calls.
Present only for SharedStorageAccessMethods: run and selectURL.

#### private_aggregation_config *: [SharedStoragePrivateAggregationConfig](#nodriver.cdp.storage.SharedStoragePrivateAggregationConfig) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Configures the private aggregation options.
Present only for SharedStorageAccessMethods: run and selectURL.

#### serialized_data *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The operation’s serialized data in bytes (converted to a string).
Present only for SharedStorageAccessMethods: run and selectURL.
TODO(crbug.com/401011862): Consider updating this parameter to binary.

#### urls_with_metadata *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[SharedStorageUrlWithMetadata](#nodriver.cdp.storage.SharedStorageUrlWithMetadata)] | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Array of candidate URLs’ specs, along with any associated metadata.
Present only for SharedStorageAccessMethod: selectURL.

#### urn_uuid *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

UUID generated for a selectURL call.
Present only for SharedStorageAccessMethod: selectURL.

* **Type:**
  Spec of the URN

#### key *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Key for a specific entry in an origin’s shared storage.
Present only for SharedStorageAccessMethods: set, append, delete, and
get.

#### value *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Value for a specific entry in an origin’s shared storage.
Present only for SharedStorageAccessMethods: set and append.

#### ignore_if_present *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Whether or not to set an entry for a key if that key is already present.
Present only for SharedStorageAccessMethod: set.

#### worklet_ordinal *: [int](https://docs.python.org/3/library/functions.html#int) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

A number denoting the (0-based) order of the worklet’s
creation relative to all other shared storage worklets created by
documents using the current storage partition.
Present only for SharedStorageAccessMethods: addModule, createWorklet.

#### worklet_target_id *: [TargetID](target.md#nodriver.cdp.target.TargetID) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Hex representation of the DevTools token used as the TargetID for the
associated shared storage worklet.
Present only for SharedStorageAccessMethods: addModule, createWorklet,
run, selectURL, and any other SharedStorageAccessMethod when the
SharedStorageAccessScope is sharedStorageWorklet.

#### with_lock *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Name of the lock to be acquired, if present.
Optionally present only for SharedStorageAccessMethods: batchUpdate,
set, append, delete, and clear.

#### batch_update_id *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

If the method has been called as part of a batchUpdate, then this
number identifies the batch to which it belongs.
Optionally present only for SharedStorageAccessMethods:
batchUpdate (required), set, append, delete, and clear.

#### batch_size *: [int](https://docs.python.org/3/library/functions.html#int) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Number of modifier methods sent in batch.
Present only for SharedStorageAccessMethod: batchUpdate.

### *class* StorageBucketsDurability(\*values)

#### RELAXED *= 'relaxed'*

#### STRICT *= 'strict'*

### *class* StorageBucket(storage_key, name=None)

#### storage_key *: [SerializedStorageKey](#nodriver.cdp.storage.SerializedStorageKey)*

#### name *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

If not specified, it is the default bucket of the storageKey.

### *class* StorageBucketInfo(bucket, id_, expiration, quota, persistent, durability)

#### bucket *: [StorageBucket](#nodriver.cdp.storage.StorageBucket)*

#### id_ *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### expiration *: [TimeSinceEpoch](network.md#nodriver.cdp.network.TimeSinceEpoch)*

#### quota *: [float](https://docs.python.org/3/library/functions.html#float)*

Storage quota (bytes).

#### persistent *: [bool](https://docs.python.org/3/library/functions.html#bool)*

#### durability *: [StorageBucketsDurability](#nodriver.cdp.storage.StorageBucketsDurability)*

### *class* RelatedWebsiteSet(primary_sites, associated_sites, service_sites)

A single Related Website Set object.

#### primary_sites *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[str](https://docs.python.org/3/library/stdtypes.html#str)]*

The primary site of this set, along with the ccTLDs if there is any.

#### associated_sites *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[str](https://docs.python.org/3/library/stdtypes.html#str)]*

The associated sites of this set, along with the ccTLDs if there is any.

#### service_sites *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[str](https://docs.python.org/3/library/stdtypes.html#str)]*

The service sites of this set, along with the ccTLDs if there is any.

## Commands

Each command is a generator function. The return
type `Generator[x, y, z]` indicates that the generator
*yields* arguments of type `x`, it must be resumed with
an argument of type `y`, and it returns type `z`. In
this library, types `x` and `y` are the same for all
commands, and `z` is the return type you should pay attention
to. For more information, see
[Getting Started: Commands](../../readme.md#getting-started-commands).

### clear_cookies(browser_context_id=None)

Clears cookies.

* **Parameters:**
  **browser_context_id** ([`BrowserContextID`](browser.md#nodriver.cdp.browser.BrowserContextID) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* Browser context to use when called on the browser endpoint.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### clear_data_for_origin(origin, storage_types)

Clears storage for origin.

* **Parameters:**
  * **origin** ([`str`](https://docs.python.org/3/library/stdtypes.html#str)) – Security origin.
  * **storage_types** ([`str`](https://docs.python.org/3/library/stdtypes.html#str)) – Comma separated list of StorageType to clear.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### clear_data_for_storage_key(storage_key, storage_types)

Clears storage for storage key.

* **Parameters:**
  * **storage_key** ([`str`](https://docs.python.org/3/library/stdtypes.html#str)) – Storage key.
  * **storage_types** ([`str`](https://docs.python.org/3/library/stdtypes.html#str)) – Comma separated list of StorageType to clear.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### clear_shared_storage_entries(owner_origin)

Clears all entries for a given origin’s shared storage.

**EXPERIMENTAL**

* **Parameters:**
  **owner_origin** ([`str`](https://docs.python.org/3/library/stdtypes.html#str))
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### clear_trust_tokens(issuer_origin)

Removes all Trust Tokens issued by the provided issuerOrigin.
Leaves other stored data, including the issuer’s Redemption Records, intact.

**EXPERIMENTAL**

* **Parameters:**
  **issuer_origin** ([`str`](https://docs.python.org/3/library/stdtypes.html#str))
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`bool`](https://docs.python.org/3/library/functions.html#bool)]
* **Returns:**
  True if any tokens were deleted, false otherwise.

### delete_shared_storage_entry(owner_origin, key)

Deletes entry for `key` (if it exists) for a given origin’s shared storage.

**EXPERIMENTAL**

* **Parameters:**
  * **owner_origin** ([`str`](https://docs.python.org/3/library/stdtypes.html#str))
  * **key** ([`str`](https://docs.python.org/3/library/stdtypes.html#str))
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### delete_storage_bucket(bucket)

Deletes the Storage Bucket with the given storage key and bucket name.

**EXPERIMENTAL**

* **Parameters:**
  **bucket** ([`StorageBucket`](#nodriver.cdp.storage.StorageBucket))
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### get_cookies(browser_context_id=None)

Returns all browser cookies.

* **Parameters:**
  **browser_context_id** ([`BrowserContextID`](browser.md#nodriver.cdp.browser.BrowserContextID) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* Browser context to use when called on the browser endpoint.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`List`](https://docs.python.org/3/library/typing.html#typing.List)[[`Cookie`](network.md#nodriver.cdp.network.Cookie)]]
* **Returns:**
  Array of cookie objects.

### get_interest_group_details(owner_origin, name)

Gets details for a named interest group.

**EXPERIMENTAL**

* **Parameters:**
  * **owner_origin** ([`str`](https://docs.python.org/3/library/stdtypes.html#str))
  * **name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str))
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`dict`](https://docs.python.org/3/library/stdtypes.html#dict)]
* **Returns:**
  This largely corresponds to: [https://wicg.github.io/turtledove/#dictdef-generatebidinterestgroup](https://wicg.github.io/turtledove/#dictdef-generatebidinterestgroup) but has absolute expirationTime instead of relative lifetimeMs and also adds joiningOrigin.

### get_related_website_sets()

Returns the effective Related Website Sets in use by this profile for the browser
session. The effective Related Website Sets will not change during a browser session.

**EXPERIMENTAL**

* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`List`](https://docs.python.org/3/library/typing.html#typing.List)[[`RelatedWebsiteSet`](#nodriver.cdp.storage.RelatedWebsiteSet)]]
* **Returns:**

### get_shared_storage_entries(owner_origin)

Gets the entries in an given origin’s shared storage.

**EXPERIMENTAL**

* **Parameters:**
  **owner_origin** ([`str`](https://docs.python.org/3/library/stdtypes.html#str))
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`List`](https://docs.python.org/3/library/typing.html#typing.List)[[`SharedStorageEntry`](#nodriver.cdp.storage.SharedStorageEntry)]]
* **Returns:**

### get_shared_storage_metadata(owner_origin)

Gets metadata for an origin’s shared storage.

**EXPERIMENTAL**

* **Parameters:**
  **owner_origin** ([`str`](https://docs.python.org/3/library/stdtypes.html#str))
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`SharedStorageMetadata`](#nodriver.cdp.storage.SharedStorageMetadata)]
* **Returns:**

### get_storage_key(frame_id=None)

Returns storage key for the given frame. If no frame ID is provided,
the storage key of the target executing this command is returned.

**EXPERIMENTAL**

* **Parameters:**
  **frame_id** ([`FrameId`](page.md#nodriver.cdp.page.FrameId) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)*
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`SerializedStorageKey`](#nodriver.cdp.storage.SerializedStorageKey)]
* **Returns:**

### get_storage_key_for_frame(frame_id)

Returns a storage key given a frame id.
Deprecated. Please use Storage.getStorageKey instead.

#### Deprecated
Deprecated since version 1.3.

* **Parameters:**
  **frame_id** ([`FrameId`](page.md#nodriver.cdp.page.FrameId))
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`SerializedStorageKey`](#nodriver.cdp.storage.SerializedStorageKey)]
* **Returns:**

#### Deprecated
Deprecated since version 1.3.

### get_trust_tokens()

Returns the number of stored Trust Tokens per issuer for the
current browsing context.

**EXPERIMENTAL**

* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`List`](https://docs.python.org/3/library/typing.html#typing.List)[[`TrustTokens`](#nodriver.cdp.storage.TrustTokens)]]
* **Returns:**

### get_usage_and_quota(origin)

Returns usage and quota in bytes.

* **Parameters:**
  **origin** ([`str`](https://docs.python.org/3/library/stdtypes.html#str)) – Security origin.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Tuple`](https://docs.python.org/3/library/typing.html#typing.Tuple)[[`float`](https://docs.python.org/3/library/functions.html#float), [`float`](https://docs.python.org/3/library/functions.html#float), [`bool`](https://docs.python.org/3/library/functions.html#bool), [`List`](https://docs.python.org/3/library/typing.html#typing.List)[[`UsageForType`](#nodriver.cdp.storage.UsageForType)]]]
* **Returns:**
  A tuple with the following items:
  1. **usage** - Storage usage (bytes).
  2. **quota** - Storage quota (bytes).
  3. **overrideActive** - Whether or not the origin has an active storage quota override
  4. **usageBreakdown** - Storage usage per type (bytes).

### override_quota_for_origin(origin, quota_size=None)

Override quota for the specified origin

**EXPERIMENTAL**

* **Parameters:**
  * **origin** ([`str`](https://docs.python.org/3/library/stdtypes.html#str)) – Security origin.
  * **quota_size** ([`float`](https://docs.python.org/3/library/functions.html#float) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* The quota size (in bytes) to override the original quota with. If this is called multiple times, the overridden quota will be equal to the quotaSize provided in the final call. If this is called without specifying a quotaSize, the quota will be reset to the default value for the specified origin. If this is called multiple times with different origins, the override will be maintained for each origin until it is disabled (called without a quotaSize).
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### reset_shared_storage_budget(owner_origin)

Resets the budget for `ownerOrigin` by clearing all budget withdrawals.

**EXPERIMENTAL**

* **Parameters:**
  **owner_origin** ([`str`](https://docs.python.org/3/library/stdtypes.html#str))
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### run_bounce_tracking_mitigations()

Deletes state for sites identified as potential bounce trackers, immediately.

**EXPERIMENTAL**

* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`List`](https://docs.python.org/3/library/typing.html#typing.List)[[`str`](https://docs.python.org/3/library/stdtypes.html#str)]]
* **Returns:**

### set_cookies(cookies, browser_context_id=None)

Sets given cookies.

* **Parameters:**
  * **cookies** ([`List`](https://docs.python.org/3/library/typing.html#typing.List)[[`CookieParam`](network.md#nodriver.cdp.network.CookieParam)]) – Cookies to be set.
  * **browser_context_id** ([`BrowserContextID`](browser.md#nodriver.cdp.browser.BrowserContextID) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* Browser context to use when called on the browser endpoint.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### set_interest_group_auction_tracking(enable)

Enables/Disables issuing of interestGroupAuctionEventOccurred and
interestGroupAuctionNetworkRequestCreated.

**EXPERIMENTAL**

* **Parameters:**
  **enable** ([`bool`](https://docs.python.org/3/library/functions.html#bool))
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### set_interest_group_tracking(enable)

Enables/Disables issuing of interestGroupAccessed events.

**EXPERIMENTAL**

* **Parameters:**
  **enable** ([`bool`](https://docs.python.org/3/library/functions.html#bool))
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### set_protected_audience_k_anonymity(owner, name, hashes)

* **Parameters:**
  * **owner** ([`str`](https://docs.python.org/3/library/stdtypes.html#str))
  * **name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str))
  * **hashes** ([`List`](https://docs.python.org/3/library/typing.html#typing.List)[[`str`](https://docs.python.org/3/library/stdtypes.html#str)])
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### set_shared_storage_entry(owner_origin, key, value, ignore_if_present=None)

Sets entry with `key` and `value` for a given origin’s shared storage.

**EXPERIMENTAL**

* **Parameters:**
  * **owner_origin** ([`str`](https://docs.python.org/3/library/stdtypes.html#str))
  * **key** ([`str`](https://docs.python.org/3/library/stdtypes.html#str))
  * **value** ([`str`](https://docs.python.org/3/library/stdtypes.html#str))
  * **ignore_if_present** ([`bool`](https://docs.python.org/3/library/functions.html#bool) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* If ``ignoreIfPresent``` is included and true, then only sets the entry if ```key`` doesn’t already exist.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### set_shared_storage_tracking(enable)

Enables/disables issuing of sharedStorageAccessed events.

**EXPERIMENTAL**

* **Parameters:**
  **enable** ([`bool`](https://docs.python.org/3/library/functions.html#bool))
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### set_storage_bucket_tracking(storage_key, enable)

Set tracking for a storage key’s buckets.

**EXPERIMENTAL**

* **Parameters:**
  * **storage_key** ([`str`](https://docs.python.org/3/library/stdtypes.html#str))
  * **enable** ([`bool`](https://docs.python.org/3/library/functions.html#bool))
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### track_cache_storage_for_origin(origin)

Registers origin to be notified when an update occurs to its cache storage list.

* **Parameters:**
  **origin** ([`str`](https://docs.python.org/3/library/stdtypes.html#str)) – Security origin.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### track_cache_storage_for_storage_key(storage_key)

Registers storage key to be notified when an update occurs to its cache storage list.

* **Parameters:**
  **storage_key** ([`str`](https://docs.python.org/3/library/stdtypes.html#str)) – Storage key.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### track_indexed_db_for_origin(origin)

Registers origin to be notified when an update occurs to its IndexedDB.

* **Parameters:**
  **origin** ([`str`](https://docs.python.org/3/library/stdtypes.html#str)) – Security origin.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### track_indexed_db_for_storage_key(storage_key)

Registers storage key to be notified when an update occurs to its IndexedDB.

* **Parameters:**
  **storage_key** ([`str`](https://docs.python.org/3/library/stdtypes.html#str)) – Storage key.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### untrack_cache_storage_for_origin(origin)

Unregisters origin from receiving notifications for cache storage.

* **Parameters:**
  **origin** ([`str`](https://docs.python.org/3/library/stdtypes.html#str)) – Security origin.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### untrack_cache_storage_for_storage_key(storage_key)

Unregisters storage key from receiving notifications for cache storage.

* **Parameters:**
  **storage_key** ([`str`](https://docs.python.org/3/library/stdtypes.html#str)) – Storage key.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### untrack_indexed_db_for_origin(origin)

Unregisters origin from receiving notifications for IndexedDB.

* **Parameters:**
  **origin** ([`str`](https://docs.python.org/3/library/stdtypes.html#str)) – Security origin.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### untrack_indexed_db_for_storage_key(storage_key)

Unregisters storage key from receiving notifications for IndexedDB.

* **Parameters:**
  **storage_key** ([`str`](https://docs.python.org/3/library/stdtypes.html#str)) – Storage key.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

## Events

Generally, you do not need to instantiate CDP events
yourself. Instead, the API creates events for you and then
you use the event’s attributes.

### *class* CacheStorageContentUpdated(origin, storage_key, bucket_id, cache_name)

A cache’s contents have been modified.

#### origin *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Origin to update.

#### storage_key *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Storage key to update.

#### bucket_id *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Storage bucket to update.

#### cache_name *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Name of cache in origin.

### *class* CacheStorageListUpdated(origin, storage_key, bucket_id)

A cache has been added/deleted.

#### origin *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Origin to update.

#### storage_key *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Storage key to update.

#### bucket_id *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Storage bucket to update.

### *class* IndexedDBContentUpdated(origin, storage_key, bucket_id, database_name, object_store_name)

The origin’s IndexedDB object store has been modified.

#### origin *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Origin to update.

#### storage_key *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Storage key to update.

#### bucket_id *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Storage bucket to update.

#### database_name *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Database to update.

#### object_store_name *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

ObjectStore to update.

### *class* IndexedDBListUpdated(origin, storage_key, bucket_id)

The origin’s IndexedDB database list has been modified.

#### origin *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Origin to update.

#### storage_key *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Storage key to update.

#### bucket_id *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Storage bucket to update.

### *class* InterestGroupAccessed(access_time, type_, owner_origin, name, component_seller_origin, bid, bid_currency, unique_auction_id)

One of the interest groups was accessed. Note that these events are global
to all targets sharing an interest group store.

#### access_time *: [TimeSinceEpoch](network.md#nodriver.cdp.network.TimeSinceEpoch)*

#### type_ *: [InterestGroupAccessType](#nodriver.cdp.storage.InterestGroupAccessType)*

#### owner_origin *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### name *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### component_seller_origin *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)*

For topLevelBid/topLevelAdditionalBid, and when appropriate,
win and additionalBidWin

#### bid *: [float](https://docs.python.org/3/library/functions.html#float) | [None](https://docs.python.org/3/library/constants.html#None)*

For bid or somethingBid event, if done locally and not on a server.

#### bid_currency *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)*

#### unique_auction_id *: [InterestGroupAuctionId](#nodriver.cdp.storage.InterestGroupAuctionId) | [None](https://docs.python.org/3/library/constants.html#None)*

For non-global events — links to interestGroupAuctionEvent

### *class* InterestGroupAuctionEventOccurred(event_time, type_, unique_auction_id, parent_auction_id, auction_config)

An auction involving interest groups is taking place. These events are
target-specific.

#### event_time *: [TimeSinceEpoch](network.md#nodriver.cdp.network.TimeSinceEpoch)*

#### type_ *: [InterestGroupAuctionEventType](#nodriver.cdp.storage.InterestGroupAuctionEventType)*

#### unique_auction_id *: [InterestGroupAuctionId](#nodriver.cdp.storage.InterestGroupAuctionId)*

#### parent_auction_id *: [InterestGroupAuctionId](#nodriver.cdp.storage.InterestGroupAuctionId) | [None](https://docs.python.org/3/library/constants.html#None)*

Set for child auctions.

#### auction_config *: [dict](https://docs.python.org/3/library/stdtypes.html#dict) | [None](https://docs.python.org/3/library/constants.html#None)*

Set for started and configResolved

### *class* InterestGroupAuctionNetworkRequestCreated(type_, request_id, auctions)

Specifies which auctions a particular network fetch may be related to, and
in what role. Note that it is not ordered with respect to
Network.requestWillBeSent (but will happen before loadingFinished
loadingFailed).

#### type_ *: [InterestGroupAuctionFetchType](#nodriver.cdp.storage.InterestGroupAuctionFetchType)*

#### request_id *: [RequestId](network.md#nodriver.cdp.network.RequestId)*

#### auctions *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[InterestGroupAuctionId](#nodriver.cdp.storage.InterestGroupAuctionId)]*

This is the set of the auctions using the worklet that issued this
request.  In the case of trusted signals, it’s possible that only some of
them actually care about the keys being queried.

### *class* SharedStorageAccessed(access_time, scope, method, main_frame_id, owner_origin, owner_site, params)

Shared storage was accessed by the associated page.
The following parameters are included in all events.

#### access_time *: [TimeSinceEpoch](network.md#nodriver.cdp.network.TimeSinceEpoch)*

Time of the access.

#### scope *: [SharedStorageAccessScope](#nodriver.cdp.storage.SharedStorageAccessScope)*

Enum value indicating the access scope.

#### method *: [SharedStorageAccessMethod](#nodriver.cdp.storage.SharedStorageAccessMethod)*

Enum value indicating the Shared Storage API method invoked.

#### main_frame_id *: [FrameId](page.md#nodriver.cdp.page.FrameId)*

DevTools Frame Token for the primary frame tree’s root.

#### owner_origin *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Serialization of the origin owning the Shared Storage data.

#### owner_site *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Serialization of the site owning the Shared Storage data.

#### params *: [SharedStorageAccessParams](#nodriver.cdp.storage.SharedStorageAccessParams)*

The sub-parameters wrapped by `params` are all optional and their
presence/absence depends on `type`.

### *class* SharedStorageWorkletOperationExecutionFinished(finished_time, execution_time, method, operation_id, worklet_target_id, main_frame_id, owner_origin)

A shared storage run or selectURL operation finished its execution.
The following parameters are included in all events.

#### finished_time *: [TimeSinceEpoch](network.md#nodriver.cdp.network.TimeSinceEpoch)*

Time that the operation finished.

#### execution_time *: [int](https://docs.python.org/3/library/functions.html#int)*

Time, in microseconds, from start of shared storage JS API call until
end of operation execution in the worklet.

#### method *: [SharedStorageAccessMethod](#nodriver.cdp.storage.SharedStorageAccessMethod)*

Enum value indicating the Shared Storage API method invoked.

#### operation_id *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

ID of the operation call.

#### worklet_target_id *: [TargetID](target.md#nodriver.cdp.target.TargetID)*

Hex representation of the DevTools token used as the TargetID for the
associated shared storage worklet.

#### main_frame_id *: [FrameId](page.md#nodriver.cdp.page.FrameId)*

DevTools Frame Token for the primary frame tree’s root.

#### owner_origin *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Serialization of the origin owning the Shared Storage data.

### *class* StorageBucketCreatedOrUpdated(bucket_info)

#### bucket_info *: [StorageBucketInfo](#nodriver.cdp.storage.StorageBucketInfo)*

### *class* StorageBucketDeleted(bucket_id)

#### bucket_id *: [str](https://docs.python.org/3/library/stdtypes.html#str)*
