# Network

Network domain allows tracking network activities of the page. It exposes information about http,
file, data and other requests and responses, their headers, bodies, timing, etc.

<a id="module-nodriver.cdp.network"></a>
* [Types]()
* [Commands]()
* [Events]()

## Types

Generally, you do not need to instantiate CDP types
yourself. Instead, the API creates objects for you as return
values from commands, and then you can use those objects as
arguments to other commands.

### *class* ResourceType(\*values)

Resource type as it was perceived by the rendering engine.

#### DOCUMENT *= 'Document'*

#### STYLESHEET *= 'Stylesheet'*

#### IMAGE *= 'Image'*

#### MEDIA *= 'Media'*

#### FONT *= 'Font'*

#### SCRIPT *= 'Script'*

#### TEXT_TRACK *= 'TextTrack'*

#### XHR *= 'XHR'*

#### FETCH *= 'Fetch'*

#### PREFETCH *= 'Prefetch'*

#### EVENT_SOURCE *= 'EventSource'*

#### WEB_SOCKET *= 'WebSocket'*

#### MANIFEST *= 'Manifest'*

#### SIGNED_EXCHANGE *= 'SignedExchange'*

#### PING *= 'Ping'*

#### CSP_VIOLATION_REPORT *= 'CSPViolationReport'*

#### PREFLIGHT *= 'Preflight'*

#### FED_CM *= 'FedCM'*

#### OTHER *= 'Other'*

### *class* LoaderId

Unique loader identifier.

### *class* RequestId

Unique network request identifier.
Note that this does not identify individual HTTP requests that are part of
a network request.

### *class* InterceptionId

Unique intercepted request identifier.

### *class* ErrorReason(\*values)

Network level fetch failure reason.

#### FAILED *= 'Failed'*

#### ABORTED *= 'Aborted'*

#### TIMED_OUT *= 'TimedOut'*

#### ACCESS_DENIED *= 'AccessDenied'*

#### CONNECTION_CLOSED *= 'ConnectionClosed'*

#### CONNECTION_RESET *= 'ConnectionReset'*

#### CONNECTION_REFUSED *= 'ConnectionRefused'*

#### CONNECTION_ABORTED *= 'ConnectionAborted'*

#### CONNECTION_FAILED *= 'ConnectionFailed'*

#### NAME_NOT_RESOLVED *= 'NameNotResolved'*

#### INTERNET_DISCONNECTED *= 'InternetDisconnected'*

#### ADDRESS_UNREACHABLE *= 'AddressUnreachable'*

#### BLOCKED_BY_CLIENT *= 'BlockedByClient'*

#### BLOCKED_BY_RESPONSE *= 'BlockedByResponse'*

### *class* TimeSinceEpoch(x=0,)

UTC time in seconds, counted from January 1, 1970.

### *class* MonotonicTime(x=0,)

Monotonically increasing time in seconds since an arbitrary point in the past.

### *class* Headers

Request / response headers as keys / values of JSON object.

### *class* ConnectionType(\*values)

The underlying connection technology that the browser is supposedly using.

#### NONE *= 'none'*

#### CELLULAR2G *= 'cellular2g'*

#### CELLULAR3G *= 'cellular3g'*

#### CELLULAR4G *= 'cellular4g'*

#### BLUETOOTH *= 'bluetooth'*

#### ETHERNET *= 'ethernet'*

#### WIFI *= 'wifi'*

#### WIMAX *= 'wimax'*

#### OTHER *= 'other'*

### *class* CookieSameSite(\*values)

Represents the cookie’s ‘SameSite’ status:
[https://tools.ietf.org/html/draft-west-first-party-cookies](https://tools.ietf.org/html/draft-west-first-party-cookies)

#### STRICT *= 'Strict'*

#### LAX *= 'Lax'*

#### NONE *= 'None'*

### *class* CookiePriority(\*values)

Represents the cookie’s ‘Priority’ status:
[https://tools.ietf.org/html/draft-west-cookie-priority-00](https://tools.ietf.org/html/draft-west-cookie-priority-00)

#### LOW *= 'Low'*

#### MEDIUM *= 'Medium'*

#### HIGH *= 'High'*

### *class* CookieSourceScheme(\*values)

Represents the source scheme of the origin that originally set the cookie.
A value of “Unset” allows protocol clients to emulate legacy cookie scope for the scheme.
This is a temporary ability and it will be removed in the future.

#### UNSET *= 'Unset'*

#### NON_SECURE *= 'NonSecure'*

#### SECURE *= 'Secure'*

### *class* ResourceTiming(request_time, proxy_start, proxy_end, dns_start, dns_end, connect_start, connect_end, ssl_start, ssl_end, worker_start, worker_ready, worker_fetch_start, worker_respond_with_settled, send_start, send_end, push_start, push_end, receive_headers_start, receive_headers_end, worker_router_evaluation_start=None, worker_cache_lookup_start=None)

Timing information for the request.

#### request_time *: [float](https://docs.python.org/3/library/functions.html#float)*

Timing’s requestTime is a baseline in seconds, while the other numbers are ticks in
milliseconds relatively to this requestTime.

#### proxy_start *: [float](https://docs.python.org/3/library/functions.html#float)*

Started resolving proxy.

#### proxy_end *: [float](https://docs.python.org/3/library/functions.html#float)*

Finished resolving proxy.

#### dns_start *: [float](https://docs.python.org/3/library/functions.html#float)*

Started DNS address resolve.

#### dns_end *: [float](https://docs.python.org/3/library/functions.html#float)*

Finished DNS address resolve.

#### connect_start *: [float](https://docs.python.org/3/library/functions.html#float)*

Started connecting to the remote host.

#### connect_end *: [float](https://docs.python.org/3/library/functions.html#float)*

Connected to the remote host.

#### ssl_start *: [float](https://docs.python.org/3/library/functions.html#float)*

Started SSL handshake.

#### ssl_end *: [float](https://docs.python.org/3/library/functions.html#float)*

Finished SSL handshake.

#### worker_start *: [float](https://docs.python.org/3/library/functions.html#float)*

Started running ServiceWorker.

#### worker_ready *: [float](https://docs.python.org/3/library/functions.html#float)*

Finished Starting ServiceWorker.

#### worker_fetch_start *: [float](https://docs.python.org/3/library/functions.html#float)*

Started fetch event.

#### worker_respond_with_settled *: [float](https://docs.python.org/3/library/functions.html#float)*

Settled fetch event respondWith promise.

#### send_start *: [float](https://docs.python.org/3/library/functions.html#float)*

Started sending request.

#### send_end *: [float](https://docs.python.org/3/library/functions.html#float)*

Finished sending request.

#### push_start *: [float](https://docs.python.org/3/library/functions.html#float)*

Time the server started pushing request.

#### push_end *: [float](https://docs.python.org/3/library/functions.html#float)*

Time the server finished pushing request.

#### receive_headers_start *: [float](https://docs.python.org/3/library/functions.html#float)*

Started receiving response headers.

#### receive_headers_end *: [float](https://docs.python.org/3/library/functions.html#float)*

Finished receiving response headers.

#### worker_router_evaluation_start *: [float](https://docs.python.org/3/library/functions.html#float) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Started ServiceWorker static routing source evaluation.

#### worker_cache_lookup_start *: [float](https://docs.python.org/3/library/functions.html#float) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Started cache lookup when the source was evaluated to `cache`.

### *class* ResourcePriority(\*values)

Loading priority of a resource request.

#### VERY_LOW *= 'VeryLow'*

#### LOW *= 'Low'*

#### MEDIUM *= 'Medium'*

#### HIGH *= 'High'*

#### VERY_HIGH *= 'VeryHigh'*

### *class* RenderBlockingBehavior(\*values)

The render-blocking behavior of a resource request.

#### BLOCKING *= 'Blocking'*

#### IN_BODY_PARSER_BLOCKING *= 'InBodyParserBlocking'*

#### NON_BLOCKING *= 'NonBlocking'*

#### NON_BLOCKING_DYNAMIC *= 'NonBlockingDynamic'*

#### POTENTIALLY_BLOCKING *= 'PotentiallyBlocking'*

### *class* PostDataEntry(bytes_=None)

Post data entry for HTTP request

#### bytes_ *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

### *class* Request(url, method, headers, initial_priority, referrer_policy, url_fragment=None, post_data=None, has_post_data=None, post_data_entries=None, mixed_content_type=None, is_link_preload=None, trust_token_params=None, is_same_site=None, is_ad_related=None)

HTTP request data.

#### url *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Request URL (without fragment).

#### method *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

HTTP request method.

#### headers *: [Headers](#nodriver.cdp.network.Headers)*

HTTP request headers.

#### initial_priority *: [ResourcePriority](#nodriver.cdp.network.ResourcePriority)*

Priority of the resource request at the time request is sent.

#### referrer_policy *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

//www.w3.org/TR/referrer-policy/

* **Type:**
  The referrer policy of the request, as defined in https

#### url_fragment *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Fragment of the requested URL starting with hash, if present.

#### post_data *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

HTTP POST request data.
Use postDataEntries instead.

#### has_post_data *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

True when the request has POST data. Note that postData might still be omitted when this flag is true when the data is too long.

#### post_data_entries *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[PostDataEntry](#nodriver.cdp.network.PostDataEntry)] | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Request body elements (post data broken into individual entries).

#### mixed_content_type *: [MixedContentType](security.md#nodriver.cdp.security.MixedContentType) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The mixed content type of the request.

#### is_link_preload *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Whether is loaded via link preload.

#### trust_token_params *: [TrustTokenParams](#nodriver.cdp.network.TrustTokenParams) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Set for requests when the TrustToken API is used. Contains the parameters
passed by the developer (e.g. via “fetch”) as understood by the backend.

#### is_same_site *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

True if this resource request is considered to be the ‘same site’ as the
request corresponding to the main frame.

#### is_ad_related *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

True when the resource request is ad-related.

### *class* SignedCertificateTimestamp(status, origin, log_description, log_id, timestamp, hash_algorithm, signature_algorithm, signature_data)

Details of a signed certificate timestamp (SCT).

#### status *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Validation status.

#### origin *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Origin.

#### log_description *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Log name / description.

#### log_id *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Log ID.

#### timestamp *: [float](https://docs.python.org/3/library/functions.html#float)*

Issuance date. Unlike TimeSinceEpoch, this contains the number of
milliseconds since January 1, 1970, UTC, not the number of seconds.

#### hash_algorithm *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Hash algorithm.

#### signature_algorithm *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Signature algorithm.

#### signature_data *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Signature data.

### *class* SecurityDetails(protocol, key_exchange, cipher, certificate_id, subject_name, san_list, issuer, valid_from, valid_to, signed_certificate_timestamp_list, certificate_transparency_compliance, encrypted_client_hello, key_exchange_group=None, mac=None, server_signature_algorithm=None)

Security details about a request.

#### protocol *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Protocol name (e.g. “TLS 1.2” or “QUIC”).

#### key_exchange *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Key Exchange used by the connection, or the empty string if not applicable.

#### cipher *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Cipher name.

#### certificate_id *: [CertificateId](security.md#nodriver.cdp.security.CertificateId)*

Certificate ID value.

#### subject_name *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Certificate subject name.

#### san_list *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[str](https://docs.python.org/3/library/stdtypes.html#str)]*

Subject Alternative Name (SAN) DNS names and IP addresses.

#### issuer *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Name of the issuing CA.

#### valid_from *: [TimeSinceEpoch](#nodriver.cdp.network.TimeSinceEpoch)*

Certificate valid from date.

#### valid_to *: [TimeSinceEpoch](#nodriver.cdp.network.TimeSinceEpoch)*

Certificate valid to (expiration) date

#### signed_certificate_timestamp_list *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[SignedCertificateTimestamp](#nodriver.cdp.network.SignedCertificateTimestamp)]*

List of signed certificate timestamps (SCTs).

#### certificate_transparency_compliance *: [CertificateTransparencyCompliance](#nodriver.cdp.network.CertificateTransparencyCompliance)*

Whether the request complied with Certificate Transparency policy

#### encrypted_client_hello *: [bool](https://docs.python.org/3/library/functions.html#bool)*

Whether the connection used Encrypted ClientHello

#### key_exchange_group *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

(EC)DH group used by the connection, if applicable.

#### mac *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

TLS MAC. Note that AEAD ciphers do not have separate MACs.

#### server_signature_algorithm *: [int](https://docs.python.org/3/library/functions.html#int) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The signature algorithm used by the server in the TLS server signature,
represented as a TLS SignatureScheme code point. Omitted if not
applicable or not known.

### *class* CertificateTransparencyCompliance(\*values)

Whether the request complied with Certificate Transparency policy.

#### UNKNOWN *= 'unknown'*

#### NOT_COMPLIANT *= 'not-compliant'*

#### COMPLIANT *= 'compliant'*

### *class* BlockedReason(\*values)

The reason why request was blocked.

#### OTHER *= 'other'*

#### CSP *= 'csp'*

#### MIXED_CONTENT *= 'mixed-content'*

#### ORIGIN *= 'origin'*

#### INSPECTOR *= 'inspector'*

#### INTEGRITY *= 'integrity'*

#### SUBRESOURCE_FILTER *= 'subresource-filter'*

#### CONTENT_TYPE *= 'content-type'*

#### COEP_FRAME_RESOURCE_NEEDS_COEP_HEADER *= 'coep-frame-resource-needs-coep-header'*

#### COOP_SANDBOXED_IFRAME_CANNOT_NAVIGATE_TO_COOP_PAGE *= 'coop-sandboxed-iframe-cannot-navigate-to-coop-page'*

#### CORP_NOT_SAME_ORIGIN *= 'corp-not-same-origin'*

#### CORP_NOT_SAME_ORIGIN_AFTER_DEFAULTED_TO_SAME_ORIGIN_BY_COEP *= 'corp-not-same-origin-after-defaulted-to-same-origin-by-coep'*

#### CORP_NOT_SAME_ORIGIN_AFTER_DEFAULTED_TO_SAME_ORIGIN_BY_DIP *= 'corp-not-same-origin-after-defaulted-to-same-origin-by-dip'*

#### CORP_NOT_SAME_ORIGIN_AFTER_DEFAULTED_TO_SAME_ORIGIN_BY_COEP_AND_DIP *= 'corp-not-same-origin-after-defaulted-to-same-origin-by-coep-and-dip'*

#### CORP_NOT_SAME_SITE *= 'corp-not-same-site'*

#### SRI_MESSAGE_SIGNATURE_MISMATCH *= 'sri-message-signature-mismatch'*

### *class* CorsError(\*values)

The reason why request was blocked.

#### DISALLOWED_BY_MODE *= 'DisallowedByMode'*

#### INVALID_RESPONSE *= 'InvalidResponse'*

#### WILDCARD_ORIGIN_NOT_ALLOWED *= 'WildcardOriginNotAllowed'*

#### MISSING_ALLOW_ORIGIN_HEADER *= 'MissingAllowOriginHeader'*

#### MULTIPLE_ALLOW_ORIGIN_VALUES *= 'MultipleAllowOriginValues'*

#### INVALID_ALLOW_ORIGIN_VALUE *= 'InvalidAllowOriginValue'*

#### ALLOW_ORIGIN_MISMATCH *= 'AllowOriginMismatch'*

#### INVALID_ALLOW_CREDENTIALS *= 'InvalidAllowCredentials'*

#### CORS_DISABLED_SCHEME *= 'CorsDisabledScheme'*

#### PREFLIGHT_INVALID_STATUS *= 'PreflightInvalidStatus'*

#### PREFLIGHT_DISALLOWED_REDIRECT *= 'PreflightDisallowedRedirect'*

#### PREFLIGHT_WILDCARD_ORIGIN_NOT_ALLOWED *= 'PreflightWildcardOriginNotAllowed'*

#### PREFLIGHT_MISSING_ALLOW_ORIGIN_HEADER *= 'PreflightMissingAllowOriginHeader'*

#### PREFLIGHT_MULTIPLE_ALLOW_ORIGIN_VALUES *= 'PreflightMultipleAllowOriginValues'*

#### PREFLIGHT_INVALID_ALLOW_ORIGIN_VALUE *= 'PreflightInvalidAllowOriginValue'*

#### PREFLIGHT_ALLOW_ORIGIN_MISMATCH *= 'PreflightAllowOriginMismatch'*

#### PREFLIGHT_INVALID_ALLOW_CREDENTIALS *= 'PreflightInvalidAllowCredentials'*

#### PREFLIGHT_MISSING_ALLOW_EXTERNAL *= 'PreflightMissingAllowExternal'*

#### PREFLIGHT_INVALID_ALLOW_EXTERNAL *= 'PreflightInvalidAllowExternal'*

#### INVALID_ALLOW_METHODS_PREFLIGHT_RESPONSE *= 'InvalidAllowMethodsPreflightResponse'*

#### INVALID_ALLOW_HEADERS_PREFLIGHT_RESPONSE *= 'InvalidAllowHeadersPreflightResponse'*

#### METHOD_DISALLOWED_BY_PREFLIGHT_RESPONSE *= 'MethodDisallowedByPreflightResponse'*

#### HEADER_DISALLOWED_BY_PREFLIGHT_RESPONSE *= 'HeaderDisallowedByPreflightResponse'*

#### REDIRECT_CONTAINS_CREDENTIALS *= 'RedirectContainsCredentials'*

#### INSECURE_LOCAL_NETWORK *= 'InsecureLocalNetwork'*

#### INVALID_LOCAL_NETWORK_ACCESS *= 'InvalidLocalNetworkAccess'*

#### NO_CORS_REDIRECT_MODE_NOT_FOLLOW *= 'NoCorsRedirectModeNotFollow'*

#### LOCAL_NETWORK_ACCESS_PERMISSION_DENIED *= 'LocalNetworkAccessPermissionDenied'*

### *class* CorsErrorStatus(cors_error, failed_parameter)

#### cors_error *: [CorsError](#nodriver.cdp.network.CorsError)*

#### failed_parameter *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

### *class* ServiceWorkerResponseSource(\*values)

Source of serviceworker response.

#### CACHE_STORAGE *= 'cache-storage'*

#### HTTP_CACHE *= 'http-cache'*

#### FALLBACK_CODE *= 'fallback-code'*

#### NETWORK *= 'network'*

### *class* TrustTokenParams(operation, refresh_policy, issuers=None)

Determines what type of Trust Token operation is executed and
depending on the type, some additional parameters. The values
are specified in third_party/blink/renderer/core/fetch/trust_token.idl.

#### operation *: [TrustTokenOperationType](#nodriver.cdp.network.TrustTokenOperationType)*

#### refresh_policy *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Only set for “token-redemption” operation and determine whether
to request a fresh SRR or use a still valid cached SRR.

#### issuers *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[str](https://docs.python.org/3/library/stdtypes.html#str)] | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Origins of issuers from whom to request tokens or redemption
records.

### *class* TrustTokenOperationType(\*values)

#### ISSUANCE *= 'Issuance'*

#### REDEMPTION *= 'Redemption'*

#### SIGNING *= 'Signing'*

### *class* AlternateProtocolUsage(\*values)

The reason why Chrome uses a specific transport protocol for HTTP semantics.

#### ALTERNATIVE_JOB_WON_WITHOUT_RACE *= 'alternativeJobWonWithoutRace'*

#### ALTERNATIVE_JOB_WON_RACE *= 'alternativeJobWonRace'*

#### MAIN_JOB_WON_RACE *= 'mainJobWonRace'*

#### MAPPING_MISSING *= 'mappingMissing'*

#### BROKEN *= 'broken'*

#### DNS_ALPN_H3_JOB_WON_WITHOUT_RACE *= 'dnsAlpnH3JobWonWithoutRace'*

#### DNS_ALPN_H3_JOB_WON_RACE *= 'dnsAlpnH3JobWonRace'*

#### UNSPECIFIED_REASON *= 'unspecifiedReason'*

### *class* ServiceWorkerRouterSource(\*values)

Source of service worker router.

#### NETWORK *= 'network'*

#### CACHE *= 'cache'*

#### FETCH_EVENT *= 'fetch-event'*

#### RACE_NETWORK_AND_FETCH_HANDLER *= 'race-network-and-fetch-handler'*

#### RACE_NETWORK_AND_CACHE *= 'race-network-and-cache'*

### *class* ServiceWorkerRouterInfo(rule_id_matched=None, matched_source_type=None, actual_source_type=None)

#### rule_id_matched *: [int](https://docs.python.org/3/library/functions.html#int) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

ID of the rule matched. If there is a matched rule, this field will
be set, otherwiser no value will be set.

#### matched_source_type *: [ServiceWorkerRouterSource](#nodriver.cdp.network.ServiceWorkerRouterSource) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The router source of the matched rule. If there is a matched rule, this
field will be set, otherwise no value will be set.

#### actual_source_type *: [ServiceWorkerRouterSource](#nodriver.cdp.network.ServiceWorkerRouterSource) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The actual router source used.

### *class* Response(url, status, status_text, headers, mime_type, charset, connection_reused, connection_id, encoded_data_length, security_state, headers_text=None, request_headers=None, request_headers_text=None, remote_ip_address=None, remote_port=None, from_disk_cache=None, from_service_worker=None, from_prefetch_cache=None, from_early_hints=None, service_worker_router_info=None, timing=None, service_worker_response_source=None, response_time=None, cache_storage_cache_name=None, protocol=None, alternate_protocol_usage=None, security_details=None)

HTTP response data.

#### url *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Response URL. This URL can be different from CachedResource.url in case of redirect.

#### status *: [int](https://docs.python.org/3/library/functions.html#int)*

HTTP response status code.

#### status_text *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

HTTP response status text.

#### headers *: [Headers](#nodriver.cdp.network.Headers)*

HTTP response headers.

#### mime_type *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Resource mimeType as determined by the browser.

#### charset *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Resource charset as determined by the browser (if applicable).

#### connection_reused *: [bool](https://docs.python.org/3/library/functions.html#bool)*

Specifies whether physical connection was actually reused for this request.

#### connection_id *: [float](https://docs.python.org/3/library/functions.html#float)*

Physical connection id that was actually used for this request.

#### encoded_data_length *: [float](https://docs.python.org/3/library/functions.html#float)*

Total number of bytes received for this request so far.

#### security_state *: [SecurityState](security.md#nodriver.cdp.security.SecurityState)*

Security state of the request resource.

#### headers_text *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

HTTP response headers text. This has been replaced by the headers in Network.responseReceivedExtraInfo.

#### request_headers *: [Headers](#nodriver.cdp.network.Headers) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Refined HTTP request headers that were actually transmitted over the network.

#### request_headers_text *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

HTTP request headers text. This has been replaced by the headers in Network.requestWillBeSentExtraInfo.

#### remote_ip_address *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Remote IP address.

#### remote_port *: [int](https://docs.python.org/3/library/functions.html#int) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Remote port.

#### from_disk_cache *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Specifies that the request was served from the disk cache.

#### from_service_worker *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Specifies that the request was served from the ServiceWorker.

#### from_prefetch_cache *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Specifies that the request was served from the prefetch cache.

#### from_early_hints *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Specifies that the request was served from the prefetch cache.

#### service_worker_router_info *: [ServiceWorkerRouterInfo](#nodriver.cdp.network.ServiceWorkerRouterInfo) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Information about how ServiceWorker Static Router API was used. If this
field is set with `matchedSourceType` field, a matching rule is found.
If this field is set without `matchedSource`, no matching rule is found.
Otherwise, the API is not used.

#### timing *: [ResourceTiming](#nodriver.cdp.network.ResourceTiming) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Timing information for the given request.

#### service_worker_response_source *: [ServiceWorkerResponseSource](#nodriver.cdp.network.ServiceWorkerResponseSource) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Response source of response from ServiceWorker.

#### response_time *: [TimeSinceEpoch](#nodriver.cdp.network.TimeSinceEpoch) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The time at which the returned response was generated.

#### cache_storage_cache_name *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Cache Storage Cache Name.

#### protocol *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Protocol used to fetch this request.

#### alternate_protocol_usage *: [AlternateProtocolUsage](#nodriver.cdp.network.AlternateProtocolUsage) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The reason why Chrome uses a specific transport protocol for HTTP semantics.

#### security_details *: [SecurityDetails](#nodriver.cdp.network.SecurityDetails) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Security details for the request.

### *class* WebSocketRequest(headers)

WebSocket request data.

#### headers *: [Headers](#nodriver.cdp.network.Headers)*

HTTP request headers.

### *class* WebSocketResponse(status, status_text, headers, headers_text=None, request_headers=None, request_headers_text=None)

WebSocket response data.

#### status *: [int](https://docs.python.org/3/library/functions.html#int)*

HTTP response status code.

#### status_text *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

HTTP response status text.

#### headers *: [Headers](#nodriver.cdp.network.Headers)*

HTTP response headers.

#### headers_text *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

HTTP response headers text.

#### request_headers *: [Headers](#nodriver.cdp.network.Headers) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

HTTP request headers.

#### request_headers_text *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

HTTP request headers text.

### *class* WebSocketFrame(opcode, mask, payload_data)

WebSocket message data. This represents an entire WebSocket message, not just a fragmented frame as the name suggests.

#### opcode *: [float](https://docs.python.org/3/library/functions.html#float)*

WebSocket message opcode.

#### mask *: [bool](https://docs.python.org/3/library/functions.html#bool)*

WebSocket message mask.

#### payload_data *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

WebSocket message payload data.
If the opcode is 1, this is a text message and payloadData is a UTF-8 string.
If the opcode isn’t 1, then payloadData is a base64 encoded string representing binary data.

### *class* CachedResource(url, type_, body_size, response=None)

Information about the cached resource.

#### url *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Resource URL. This is the url of the original network request.

#### type_ *: [ResourceType](#nodriver.cdp.network.ResourceType)*

Type of this resource.

#### body_size *: [float](https://docs.python.org/3/library/functions.html#float)*

Cached response body size.

#### response *: [Response](#nodriver.cdp.network.Response) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Cached response data.

### *class* Initiator(type_, stack=None, url=None, line_number=None, column_number=None, request_id=None)

Information about the request initiator.

#### type_ *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Type of this initiator.

#### stack *: [StackTrace](runtime.md#nodriver.cdp.runtime.StackTrace) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Initiator JavaScript stack trace, set for Script only.
Requires the Debugger domain to be enabled.

#### url *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Initiator URL, set for Parser type or for Script type (when script is importing module) or for SignedExchange type.

#### line_number *: [float](https://docs.python.org/3/library/functions.html#float) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Initiator line number, set for Parser type or for Script type (when script is importing
module) (0-based).

#### column_number *: [float](https://docs.python.org/3/library/functions.html#float) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Initiator column number, set for Parser type or for Script type (when script is importing
module) (0-based).

#### request_id *: [RequestId](#nodriver.cdp.network.RequestId) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Set if another request triggered this request (e.g. preflight).

### *class* CookiePartitionKey(top_level_site, has_cross_site_ancestor)

cookiePartitionKey object
The representation of the components of the key that are created by the cookiePartitionKey class contained in net/cookies/cookie_partition_key.h.

#### top_level_site *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

The site of the top-level URL the browser was visiting at the start
of the request to the endpoint that set the cookie.

#### has_cross_site_ancestor *: [bool](https://docs.python.org/3/library/functions.html#bool)*

Indicates if the cookie has any ancestors that are cross-site to the topLevelSite.

### *class* Cookie(name, value, domain, path, size, http_only, secure, session, priority, same_party, source_scheme, source_port, expires=None, same_site=None, partition_key=None, partition_key_opaque=None)

Cookie object

#### name *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Cookie name.

#### value *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Cookie value.

#### domain *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Cookie domain.

#### path *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Cookie path.

#### size *: [int](https://docs.python.org/3/library/functions.html#int)*

Cookie size.

#### http_only *: [bool](https://docs.python.org/3/library/functions.html#bool)*

True if cookie is http-only.

#### secure *: [bool](https://docs.python.org/3/library/functions.html#bool)*

True if cookie is secure.

#### session *: [bool](https://docs.python.org/3/library/functions.html#bool)*

True in case of session cookie.

#### priority *: [CookiePriority](#nodriver.cdp.network.CookiePriority)*

Cookie Priority

#### same_party *: [bool](https://docs.python.org/3/library/functions.html#bool)*

True if cookie is SameParty.

#### source_scheme *: [CookieSourceScheme](#nodriver.cdp.network.CookieSourceScheme)*

Cookie source scheme type.

#### source_port *: [int](https://docs.python.org/3/library/functions.html#int)*

Cookie source port. Valid values are {-1, [1, 65535]}, -1 indicates an unspecified port.
An unspecified port value allows protocol clients to emulate legacy cookie scope for the port.
This is a temporary ability and it will be removed in the future.

#### expires *: [float](https://docs.python.org/3/library/functions.html#float) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Cookie expiration date as the number of seconds since the UNIX epoch.
The value is set to -1 if the expiry date is not set.
The value can be null for values that cannot be represented in
JSON (±Inf).

#### same_site *: [CookieSameSite](#nodriver.cdp.network.CookieSameSite) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Cookie SameSite type.

#### partition_key *: [CookiePartitionKey](#nodriver.cdp.network.CookiePartitionKey) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Cookie partition key.

#### partition_key_opaque *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

True if cookie partition key is opaque.

### *class* SetCookieBlockedReason(\*values)

Types of reasons why a cookie may not be stored from a response.

#### SECURE_ONLY *= 'SecureOnly'*

#### SAME_SITE_STRICT *= 'SameSiteStrict'*

#### SAME_SITE_LAX *= 'SameSiteLax'*

#### SAME_SITE_UNSPECIFIED_TREATED_AS_LAX *= 'SameSiteUnspecifiedTreatedAsLax'*

#### SAME_SITE_NONE_INSECURE *= 'SameSiteNoneInsecure'*

#### USER_PREFERENCES *= 'UserPreferences'*

#### THIRD_PARTY_PHASEOUT *= 'ThirdPartyPhaseout'*

#### THIRD_PARTY_BLOCKED_IN_FIRST_PARTY_SET *= 'ThirdPartyBlockedInFirstPartySet'*

#### SYNTAX_ERROR *= 'SyntaxError'*

#### SCHEME_NOT_SUPPORTED *= 'SchemeNotSupported'*

#### OVERWRITE_SECURE *= 'OverwriteSecure'*

#### INVALID_DOMAIN *= 'InvalidDomain'*

#### INVALID_PREFIX *= 'InvalidPrefix'*

#### UNKNOWN_ERROR *= 'UnknownError'*

#### SCHEMEFUL_SAME_SITE_STRICT *= 'SchemefulSameSiteStrict'*

#### SCHEMEFUL_SAME_SITE_LAX *= 'SchemefulSameSiteLax'*

#### SCHEMEFUL_SAME_SITE_UNSPECIFIED_TREATED_AS_LAX *= 'SchemefulSameSiteUnspecifiedTreatedAsLax'*

#### NAME_VALUE_PAIR_EXCEEDS_MAX_SIZE *= 'NameValuePairExceedsMaxSize'*

#### DISALLOWED_CHARACTER *= 'DisallowedCharacter'*

#### NO_COOKIE_CONTENT *= 'NoCookieContent'*

### *class* CookieBlockedReason(\*values)

Types of reasons why a cookie may not be sent with a request.

#### SECURE_ONLY *= 'SecureOnly'*

#### NOT_ON_PATH *= 'NotOnPath'*

#### DOMAIN_MISMATCH *= 'DomainMismatch'*

#### SAME_SITE_STRICT *= 'SameSiteStrict'*

#### SAME_SITE_LAX *= 'SameSiteLax'*

#### SAME_SITE_UNSPECIFIED_TREATED_AS_LAX *= 'SameSiteUnspecifiedTreatedAsLax'*

#### SAME_SITE_NONE_INSECURE *= 'SameSiteNoneInsecure'*

#### USER_PREFERENCES *= 'UserPreferences'*

#### THIRD_PARTY_PHASEOUT *= 'ThirdPartyPhaseout'*

#### THIRD_PARTY_BLOCKED_IN_FIRST_PARTY_SET *= 'ThirdPartyBlockedInFirstPartySet'*

#### UNKNOWN_ERROR *= 'UnknownError'*

#### SCHEMEFUL_SAME_SITE_STRICT *= 'SchemefulSameSiteStrict'*

#### SCHEMEFUL_SAME_SITE_LAX *= 'SchemefulSameSiteLax'*

#### SCHEMEFUL_SAME_SITE_UNSPECIFIED_TREATED_AS_LAX *= 'SchemefulSameSiteUnspecifiedTreatedAsLax'*

#### NAME_VALUE_PAIR_EXCEEDS_MAX_SIZE *= 'NameValuePairExceedsMaxSize'*

#### PORT_MISMATCH *= 'PortMismatch'*

#### SCHEME_MISMATCH *= 'SchemeMismatch'*

#### ANONYMOUS_CONTEXT *= 'AnonymousContext'*

### *class* CookieExemptionReason(\*values)

Types of reasons why a cookie should have been blocked by 3PCD but is exempted for the request.

#### NONE *= 'None'*

#### USER_SETTING *= 'UserSetting'*

#### TPCD_METADATA *= 'TPCDMetadata'*

#### TPCD_DEPRECATION_TRIAL *= 'TPCDDeprecationTrial'*

#### TOP_LEVEL_TPCD_DEPRECATION_TRIAL *= 'TopLevelTPCDDeprecationTrial'*

#### TPCD_HEURISTICS *= 'TPCDHeuristics'*

#### ENTERPRISE_POLICY *= 'EnterprisePolicy'*

#### STORAGE_ACCESS *= 'StorageAccess'*

#### TOP_LEVEL_STORAGE_ACCESS *= 'TopLevelStorageAccess'*

#### SCHEME *= 'Scheme'*

#### SAME_SITE_NONE_COOKIES_IN_SANDBOX *= 'SameSiteNoneCookiesInSandbox'*

### *class* BlockedSetCookieWithReason(blocked_reasons, cookie_line, cookie=None)

A cookie which was not stored from a response with the corresponding reason.

#### blocked_reasons *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[SetCookieBlockedReason](#nodriver.cdp.network.SetCookieBlockedReason)]*

The reason(s) this cookie was blocked.

#### cookie_line *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

The string representing this individual cookie as it would appear in the header.
This is not the entire “cookie” or “set-cookie” header which could have multiple cookies.

#### cookie *: [Cookie](#nodriver.cdp.network.Cookie) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The cookie object which represents the cookie which was not stored. It is optional because
sometimes complete cookie information is not available, such as in the case of parsing
errors.

### *class* ExemptedSetCookieWithReason(exemption_reason, cookie_line, cookie)

A cookie should have been blocked by 3PCD but is exempted and stored from a response with the
corresponding reason. A cookie could only have at most one exemption reason.

#### exemption_reason *: [CookieExemptionReason](#nodriver.cdp.network.CookieExemptionReason)*

The reason the cookie was exempted.

#### cookie_line *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

The string representing this individual cookie as it would appear in the header.

#### cookie *: [Cookie](#nodriver.cdp.network.Cookie)*

The cookie object representing the cookie.

### *class* AssociatedCookie(cookie, blocked_reasons, exemption_reason=None)

A cookie associated with the request which may or may not be sent with it.
Includes the cookies itself and reasons for blocking or exemption.

#### cookie *: [Cookie](#nodriver.cdp.network.Cookie)*

The cookie object representing the cookie which was not sent.

#### blocked_reasons *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[CookieBlockedReason](#nodriver.cdp.network.CookieBlockedReason)]*

The reason(s) the cookie was blocked. If empty means the cookie is included.

#### exemption_reason *: [CookieExemptionReason](#nodriver.cdp.network.CookieExemptionReason) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The reason the cookie should have been blocked by 3PCD but is exempted. A cookie could
only have at most one exemption reason.

### *class* CookieParam(name, value, url=None, domain=None, path=None, secure=None, http_only=None, same_site=None, expires=None, priority=None, source_scheme=None, source_port=None, partition_key=None)

Cookie parameter object

#### name *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Cookie name.

#### value *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Cookie value.

#### url *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The request-URI to associate with the setting of the cookie. This value can affect the
default domain, path, source port, and source scheme values of the created cookie.

#### domain *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Cookie domain.

#### path *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Cookie path.

#### secure *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

True if cookie is secure.

#### http_only *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

True if cookie is http-only.

#### same_site *: [CookieSameSite](#nodriver.cdp.network.CookieSameSite) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Cookie SameSite type.

#### expires *: [TimeSinceEpoch](#nodriver.cdp.network.TimeSinceEpoch) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Cookie expiration date, session cookie if not set

#### priority *: [CookiePriority](#nodriver.cdp.network.CookiePriority) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Cookie Priority.

#### source_scheme *: [CookieSourceScheme](#nodriver.cdp.network.CookieSourceScheme) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Cookie source scheme type.

#### source_port *: [int](https://docs.python.org/3/library/functions.html#int) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Cookie source port. Valid values are {-1, [1, 65535]}, -1 indicates an unspecified port.
An unspecified port value allows protocol clients to emulate legacy cookie scope for the port.
This is a temporary ability and it will be removed in the future.

#### partition_key *: [CookiePartitionKey](#nodriver.cdp.network.CookiePartitionKey) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Cookie partition key. If not set, the cookie will be set as not partitioned.

### *class* AuthChallenge(origin, scheme, realm, source=None)

Authorization challenge for HTTP status code 401 or 407.

#### origin *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Origin of the challenger.

#### scheme *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

The authentication scheme used, such as basic or digest

#### realm *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

The realm of the challenge. May be empty.

#### source *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Source of the authentication challenge.

### *class* AuthChallengeResponse(response, username=None, password=None)

Response to an AuthChallenge.

#### response *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

The decision on what to do in response to the authorization challenge.  Default means
deferring to the default behavior of the net stack, which will likely either the Cancel
authentication or display a popup dialog box.

#### username *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The username to provide, possibly empty. Should only be set if response is
ProvideCredentials.

#### password *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The password to provide, possibly empty. Should only be set if response is
ProvideCredentials.

### *class* InterceptionStage(\*values)

Stages of the interception to begin intercepting. Request will intercept before the request is
sent. Response will intercept after the response is received.

#### REQUEST *= 'Request'*

#### HEADERS_RECEIVED *= 'HeadersReceived'*

### *class* RequestPattern(url_pattern=None, resource_type=None, interception_stage=None)

Request pattern for interception.

#### url_pattern *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Wildcards (`'*'` -> zero or more, `'?'` -> exactly one) are allowed. Escape character is
backslash. Omitting is equivalent to `"*"`.

#### resource_type *: [ResourceType](#nodriver.cdp.network.ResourceType) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

If set, only requests for matching resource types will be intercepted.

#### interception_stage *: [InterceptionStage](#nodriver.cdp.network.InterceptionStage) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Stage at which to begin intercepting requests. Default is Request.

### *class* SignedExchangeSignature(label, signature, integrity, validity_url, date, expires, cert_url=None, cert_sha256=None, certificates=None)

Information about a signed exchange signature.
[https://wicg.github.io/webpackage/draft-yasskin-httpbis-origin-signed-exchanges-impl.html#rfc.section.3.1](https://wicg.github.io/webpackage/draft-yasskin-httpbis-origin-signed-exchanges-impl.html#rfc.section.3.1)

#### label *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Signed exchange signature label.

#### signature *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

The hex string of signed exchange signature.

#### integrity *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Signed exchange signature integrity.

#### validity_url *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Signed exchange signature validity Url.

#### date *: [int](https://docs.python.org/3/library/functions.html#int)*

Signed exchange signature date.

#### expires *: [int](https://docs.python.org/3/library/functions.html#int)*

Signed exchange signature expires.

#### cert_url *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Signed exchange signature cert Url.

#### cert_sha256 *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The hex string of signed exchange signature cert sha256.

#### certificates *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[str](https://docs.python.org/3/library/stdtypes.html#str)] | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The encoded certificates.

### *class* SignedExchangeHeader(request_url, response_code, response_headers, signatures, header_integrity)

Information about a signed exchange header.
[https://wicg.github.io/webpackage/draft-yasskin-httpbis-origin-signed-exchanges-impl.html#cbor-representation](https://wicg.github.io/webpackage/draft-yasskin-httpbis-origin-signed-exchanges-impl.html#cbor-representation)

#### request_url *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Signed exchange request URL.

#### response_code *: [int](https://docs.python.org/3/library/functions.html#int)*

Signed exchange response code.

#### response_headers *: [Headers](#nodriver.cdp.network.Headers)*

Signed exchange response headers.

#### signatures *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[SignedExchangeSignature](#nodriver.cdp.network.SignedExchangeSignature)]*

Signed exchange response signature.

#### header_integrity *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Signed exchange header integrity hash in the form of `sha256-<base64-hash-value>`.

### *class* SignedExchangeErrorField(\*values)

Field type for a signed exchange related error.

#### SIGNATURE_SIG *= 'signatureSig'*

#### SIGNATURE_INTEGRITY *= 'signatureIntegrity'*

#### SIGNATURE_CERT_URL *= 'signatureCertUrl'*

#### SIGNATURE_CERT_SHA256 *= 'signatureCertSha256'*

#### SIGNATURE_VALIDITY_URL *= 'signatureValidityUrl'*

#### SIGNATURE_TIMESTAMPS *= 'signatureTimestamps'*

### *class* SignedExchangeError(message, signature_index=None, error_field=None)

Information about a signed exchange response.

#### message *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Error message.

#### signature_index *: [int](https://docs.python.org/3/library/functions.html#int) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The index of the signature which caused the error.

#### error_field *: [SignedExchangeErrorField](#nodriver.cdp.network.SignedExchangeErrorField) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The field which caused the error.

### *class* SignedExchangeInfo(outer_response, has_extra_info, header=None, security_details=None, errors=None)

Information about a signed exchange response.

#### outer_response *: [Response](#nodriver.cdp.network.Response)*

The outer response of signed HTTP exchange which was received from network.

#### has_extra_info *: [bool](https://docs.python.org/3/library/functions.html#bool)*

Whether network response for the signed exchange was accompanied by
extra headers.

#### header *: [SignedExchangeHeader](#nodriver.cdp.network.SignedExchangeHeader) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Information about the signed exchange header.

#### security_details *: [SecurityDetails](#nodriver.cdp.network.SecurityDetails) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Security details for the signed exchange header.

#### errors *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[SignedExchangeError](#nodriver.cdp.network.SignedExchangeError)] | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Errors occurred while handling the signed exchange.

### *class* ContentEncoding(\*values)

List of content encodings supported by the backend.

#### DEFLATE *= 'deflate'*

#### GZIP *= 'gzip'*

#### BR *= 'br'*

#### ZSTD *= 'zstd'*

### *class* NetworkConditions(url_pattern, latency, download_throughput, upload_throughput, connection_type=None, packet_loss=None, packet_queue_length=None, packet_reordering=None, offline=None)

#### url_pattern *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Only matching requests will be affected by these conditions. Patterns use the URLPattern constructor string
syntax ([https://urlpattern.spec.whatwg.org/](https://urlpattern.spec.whatwg.org/)) and must be absolute. If the pattern is empty, all requests are
matched (including p2p connections).

#### latency *: [float](https://docs.python.org/3/library/functions.html#float)*

Minimum latency from request sent to response headers received (ms).

#### download_throughput *: [float](https://docs.python.org/3/library/functions.html#float)*

Maximal aggregated download throughput (bytes/sec). -1 disables download throttling.

#### upload_throughput *: [float](https://docs.python.org/3/library/functions.html#float)*

Maximal aggregated upload throughput (bytes/sec).  -1 disables upload throttling.

#### connection_type *: [ConnectionType](#nodriver.cdp.network.ConnectionType) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Connection type if known.

#### packet_loss *: [float](https://docs.python.org/3/library/functions.html#float) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

WebRTC packet loss (percent, 0-100). 0 disables packet loss emulation, 100 drops all the packets.

#### packet_queue_length *: [int](https://docs.python.org/3/library/functions.html#int) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

WebRTC packet queue length (packet). 0 removes any queue length limitations.

#### packet_reordering *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

WebRTC packetReordering feature.

#### offline *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

True to emulate internet disconnection.

### *class* BlockPattern(url_pattern, block)

#### url_pattern *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

URL pattern to match. Patterns use the URLPattern constructor string syntax
([https://urlpattern.spec.whatwg.org/](https://urlpattern.spec.whatwg.org/)) and must be absolute. Example: `*://*:*/*.css`.

#### block *: [bool](https://docs.python.org/3/library/functions.html#bool)*

Whether or not to block the pattern. If false, a matching request will not be blocked even if it matches a later
`BlockPattern`.

### *class* DirectSocketDnsQueryType(\*values)

#### IPV4 *= 'ipv4'*

#### IPV6 *= 'ipv6'*

### *class* DirectTCPSocketOptions(no_delay, keep_alive_delay=None, send_buffer_size=None, receive_buffer_size=None, dns_query_type=None)

#### no_delay *: [bool](https://docs.python.org/3/library/functions.html#bool)*

TCP_NODELAY option

#### keep_alive_delay *: [float](https://docs.python.org/3/library/functions.html#float) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Expected to be unsigned integer.

#### send_buffer_size *: [float](https://docs.python.org/3/library/functions.html#float) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Expected to be unsigned integer.

#### receive_buffer_size *: [float](https://docs.python.org/3/library/functions.html#float) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Expected to be unsigned integer.

#### dns_query_type *: [DirectSocketDnsQueryType](#nodriver.cdp.network.DirectSocketDnsQueryType) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

### *class* DirectUDPSocketOptions(remote_addr=None, remote_port=None, local_addr=None, local_port=None, dns_query_type=None, send_buffer_size=None, receive_buffer_size=None, multicast_loopback=None, multicast_time_to_live=None, multicast_allow_address_sharing=None)

#### remote_addr *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### remote_port *: [int](https://docs.python.org/3/library/functions.html#int) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Unsigned int 16.

#### local_addr *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### local_port *: [int](https://docs.python.org/3/library/functions.html#int) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Unsigned int 16.

#### dns_query_type *: [DirectSocketDnsQueryType](#nodriver.cdp.network.DirectSocketDnsQueryType) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### send_buffer_size *: [float](https://docs.python.org/3/library/functions.html#float) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Expected to be unsigned integer.

#### receive_buffer_size *: [float](https://docs.python.org/3/library/functions.html#float) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Expected to be unsigned integer.

#### multicast_loopback *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### multicast_time_to_live *: [int](https://docs.python.org/3/library/functions.html#int) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Unsigned int 8.

#### multicast_allow_address_sharing *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

### *class* DirectUDPMessage(data, remote_addr=None, remote_port=None)

#### data *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### remote_addr *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Null for connected mode.

#### remote_port *: [int](https://docs.python.org/3/library/functions.html#int) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Null for connected mode.
Expected to be unsigned integer.

### *class* LocalNetworkAccessRequestPolicy(\*values)

#### ALLOW *= 'Allow'*

#### BLOCK_FROM_INSECURE_TO_MORE_PRIVATE *= 'BlockFromInsecureToMorePrivate'*

#### WARN_FROM_INSECURE_TO_MORE_PRIVATE *= 'WarnFromInsecureToMorePrivate'*

#### PERMISSION_BLOCK *= 'PermissionBlock'*

#### PERMISSION_WARN *= 'PermissionWarn'*

### *class* IPAddressSpace(\*values)

#### LOOPBACK *= 'Loopback'*

#### LOCAL *= 'Local'*

#### PUBLIC *= 'Public'*

#### UNKNOWN *= 'Unknown'*

### *class* ConnectTiming(request_time)

#### request_time *: [float](https://docs.python.org/3/library/functions.html#float)*

Timing’s requestTime is a baseline in seconds, while the other numbers are ticks in
milliseconds relatively to this requestTime. Matches ResourceTiming’s requestTime for
the same request (but not for redirected requests).

### *class* ClientSecurityState(initiator_is_secure_context, initiator_ip_address_space, local_network_access_request_policy)

#### initiator_is_secure_context *: [bool](https://docs.python.org/3/library/functions.html#bool)*

#### initiator_ip_address_space *: [IPAddressSpace](#nodriver.cdp.network.IPAddressSpace)*

#### local_network_access_request_policy *: [LocalNetworkAccessRequestPolicy](#nodriver.cdp.network.LocalNetworkAccessRequestPolicy)*

### *class* AdScriptIdentifier(script_id, debugger_id, name)

Identifies the script on the stack that caused a resource or element to be
labeled as an ad. For resources, this indicates the context that triggered
the fetch. For elements, this indicates the context that caused the element
to be appended to the DOM.

#### script_id *: [ScriptId](runtime.md#nodriver.cdp.runtime.ScriptId)*

The script’s V8 identifier.

#### debugger_id *: [UniqueDebuggerId](runtime.md#nodriver.cdp.runtime.UniqueDebuggerId)*

V8’s debugging ID for the v8::Context.

#### name *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

The script’s url (or generated name based on id if inline script).

### *class* AdAncestry(ancestry_chain, root_script_filterlist_rule=None)

Encapsulates the script ancestry and the root script filter list rule that
caused the resource or element to be labeled as an ad.

#### ancestry_chain *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[AdScriptIdentifier](#nodriver.cdp.network.AdScriptIdentifier)]*

A chain of `AdScriptIdentifier`’s representing the ancestry of an ad
script that led to the creation of a resource or element. The chain is
ordered from the script itself (lowest level) up to its root ancestor
that was flagged by a filter list.

#### root_script_filterlist_rule *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The filter list rule that caused the root (last) script in
`ancestryChain` to be tagged as an ad.

### *class* AdProvenance(filterlist_rule=None, ad_script_ancestry=None)

Represents the provenance of an ad resource or element. Only one of
`filterlistRule` or `adScriptAncestry` can be set. If `filterlistRule`
is provided, the resource URL directly matches a filter list rule. If
`adScriptAncestry` is provided, an ad script initiated the resource fetch or
appended the element to the DOM. If neither is provided, the entity is
known to be an ad, but provenance tracking information is unavailable.

#### filterlist_rule *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The filterlist rule that matched, if any.

#### ad_script_ancestry *: [AdAncestry](#nodriver.cdp.network.AdAncestry) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The script ancestry that created the ad, if any.

### *class* CrossOriginOpenerPolicyValue(\*values)

#### SAME_ORIGIN *= 'SameOrigin'*

#### SAME_ORIGIN_ALLOW_POPUPS *= 'SameOriginAllowPopups'*

#### RESTRICT_PROPERTIES *= 'RestrictProperties'*

#### UNSAFE_NONE *= 'UnsafeNone'*

#### SAME_ORIGIN_PLUS_COEP *= 'SameOriginPlusCoep'*

#### RESTRICT_PROPERTIES_PLUS_COEP *= 'RestrictPropertiesPlusCoep'*

#### NOOPENER_ALLOW_POPUPS *= 'NoopenerAllowPopups'*

### *class* CrossOriginOpenerPolicyStatus(value, report_only_value, reporting_endpoint=None, report_only_reporting_endpoint=None)

#### value *: [CrossOriginOpenerPolicyValue](#nodriver.cdp.network.CrossOriginOpenerPolicyValue)*

#### report_only_value *: [CrossOriginOpenerPolicyValue](#nodriver.cdp.network.CrossOriginOpenerPolicyValue)*

#### reporting_endpoint *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### report_only_reporting_endpoint *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

### *class* CrossOriginEmbedderPolicyValue(\*values)

#### NONE *= 'None'*

#### CREDENTIALLESS *= 'Credentialless'*

#### REQUIRE_CORP *= 'RequireCorp'*

### *class* CrossOriginEmbedderPolicyStatus(value, report_only_value, reporting_endpoint=None, report_only_reporting_endpoint=None)

#### value *: [CrossOriginEmbedderPolicyValue](#nodriver.cdp.network.CrossOriginEmbedderPolicyValue)*

#### report_only_value *: [CrossOriginEmbedderPolicyValue](#nodriver.cdp.network.CrossOriginEmbedderPolicyValue)*

#### reporting_endpoint *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### report_only_reporting_endpoint *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

### *class* ContentSecurityPolicySource(\*values)

#### HTTP *= 'HTTP'*

#### META *= 'Meta'*

### *class* ContentSecurityPolicyStatus(effective_directives, is_enforced, source)

#### effective_directives *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### is_enforced *: [bool](https://docs.python.org/3/library/functions.html#bool)*

#### source *: [ContentSecurityPolicySource](#nodriver.cdp.network.ContentSecurityPolicySource)*

### *class* SecurityIsolationStatus(coop=None, coep=None, csp=None)

#### coop *: [CrossOriginOpenerPolicyStatus](#nodriver.cdp.network.CrossOriginOpenerPolicyStatus) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### coep *: [CrossOriginEmbedderPolicyStatus](#nodriver.cdp.network.CrossOriginEmbedderPolicyStatus) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### csp *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[ContentSecurityPolicyStatus](#nodriver.cdp.network.ContentSecurityPolicyStatus)] | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

### *class* ReportStatus(\*values)

The status of a Reporting API report.

#### QUEUED *= 'Queued'*

#### PENDING *= 'Pending'*

#### MARKED_FOR_REMOVAL *= 'MarkedForRemoval'*

#### SUCCESS *= 'Success'*

### *class* ReportId

### *class* ReportingApiReport(id_, initiator_url, destination, type_, timestamp, depth, completed_attempts, body, status)

An object representing a report generated by the Reporting API.

#### id_ *: [ReportId](#nodriver.cdp.network.ReportId)*

#### initiator_url *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

The URL of the document that triggered the report.

#### destination *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

The name of the endpoint group that should be used to deliver the report.

#### type_ *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

The type of the report (specifies the set of data that is contained in the report body).

#### timestamp *: [TimeSinceEpoch](#nodriver.cdp.network.TimeSinceEpoch)*

When the report was generated.

#### depth *: [int](https://docs.python.org/3/library/functions.html#int)*

How many uploads deep the related request was.

#### completed_attempts *: [int](https://docs.python.org/3/library/functions.html#int)*

The number of delivery attempts made so far, not including an active attempt.

#### body *: [dict](https://docs.python.org/3/library/stdtypes.html#dict)*

#### status *: [ReportStatus](#nodriver.cdp.network.ReportStatus)*

### *class* ReportingApiEndpoint(url, group_name)

#### url *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

The URL of the endpoint to which reports may be delivered.

#### group_name *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Name of the endpoint group.

### *class* DeviceBoundSessionKey(site, id_)

Unique identifier for a device bound session.

#### site *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

The site the session is set up for.

#### id_ *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

The id of the session.

### *class* DeviceBoundSessionWithUsage(session_key, usage)

How a device bound session was used during a request.

#### session_key *: [DeviceBoundSessionKey](#nodriver.cdp.network.DeviceBoundSessionKey)*

The key for the session.

#### usage *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

How the session was used (or not used).

### *class* DeviceBoundSessionCookieCraving(name, domain, path, secure, http_only, same_site=None)

A device bound session’s cookie craving.

#### name *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

The name of the craving.

#### domain *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

The domain of the craving.

#### path *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

The path of the craving.

#### secure *: [bool](https://docs.python.org/3/library/functions.html#bool)*

The `Secure` attribute of the craving attributes.

#### http_only *: [bool](https://docs.python.org/3/library/functions.html#bool)*

The `HttpOnly` attribute of the craving attributes.

#### same_site *: [CookieSameSite](#nodriver.cdp.network.CookieSameSite) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The `SameSite` attribute of the craving attributes.

### *class* DeviceBoundSessionUrlRule(rule_type, host_pattern, path_prefix)

A device bound session’s inclusion URL rule.

#### rule_type *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

See comments on `net::device_bound_sessions::SessionInclusionRules::UrlRule::rule_type`.

#### host_pattern *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

See comments on `net::device_bound_sessions::SessionInclusionRules::UrlRule::host_pattern`.

#### path_prefix *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

See comments on `net::device_bound_sessions::SessionInclusionRules::UrlRule::path_prefix`.

### *class* DeviceBoundSessionInclusionRules(origin, include_site, url_rules)

A device bound session’s inclusion rules.

#### origin *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

See comments on `net::device_bound_sessions::SessionInclusionRules::origin_`.

#### include_site *: [bool](https://docs.python.org/3/library/functions.html#bool)*

Whether the whole site is included. See comments on
`net::device_bound_sessions::SessionInclusionRules::include_site_` for more
details; this boolean is true if that value is populated.

#### url_rules *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[DeviceBoundSessionUrlRule](#nodriver.cdp.network.DeviceBoundSessionUrlRule)]*

See comments on `net::device_bound_sessions::SessionInclusionRules::url_rules_`.

### *class* DeviceBoundSession(key, refresh_url, inclusion_rules, cookie_cravings, expiry_date, allowed_refresh_initiators, cached_challenge=None)

A device bound session.

#### key *: [DeviceBoundSessionKey](#nodriver.cdp.network.DeviceBoundSessionKey)*

The site and session ID of the session.

#### refresh_url *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

See comments on `net::device_bound_sessions::Session::refresh_url_`.

#### inclusion_rules *: [DeviceBoundSessionInclusionRules](#nodriver.cdp.network.DeviceBoundSessionInclusionRules)*

See comments on `net::device_bound_sessions::Session::inclusion_rules_`.

#### cookie_cravings *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[DeviceBoundSessionCookieCraving](#nodriver.cdp.network.DeviceBoundSessionCookieCraving)]*

See comments on `net::device_bound_sessions::Session::cookie_cravings_`.

#### expiry_date *: [TimeSinceEpoch](#nodriver.cdp.network.TimeSinceEpoch)*

See comments on `net::device_bound_sessions::Session::expiry_date_`.

#### allowed_refresh_initiators *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[str](https://docs.python.org/3/library/stdtypes.html#str)]*

See comments on `net::device_bound_sessions::Session::allowed_refresh_initiators_`.

#### cached_challenge *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

See comments on `net::device_bound_sessions::Session::cached_challenge__`.

### *class* DeviceBoundSessionEventId

A unique identifier for a device bound session event.

### *class* DeviceBoundSessionFetchResult(\*values)

A fetch result for a device bound session creation or refresh.

#### SUCCESS *= 'Success'*

#### KEY_ERROR *= 'KeyError'*

#### SIGNING_ERROR *= 'SigningError'*

#### TRANSIENT_SIGNING_ERROR *= 'TransientSigningError'*

#### SERVER_REQUESTED_TERMINATION *= 'ServerRequestedTermination'*

#### INVALID_SESSION_ID *= 'InvalidSessionId'*

#### INVALID_CHALLENGE *= 'InvalidChallenge'*

#### TOO_MANY_CHALLENGES *= 'TooManyChallenges'*

#### INVALID_FETCHER_URL *= 'InvalidFetcherUrl'*

#### INVALID_REFRESH_URL *= 'InvalidRefreshUrl'*

#### TRANSIENT_HTTP_ERROR *= 'TransientHttpError'*

#### SCOPE_ORIGIN_SAME_SITE_MISMATCH *= 'ScopeOriginSameSiteMismatch'*

#### REFRESH_URL_SAME_SITE_MISMATCH *= 'RefreshUrlSameSiteMismatch'*

#### MISMATCHED_SESSION_ID *= 'MismatchedSessionId'*

#### MISSING_SCOPE *= 'MissingScope'*

#### NO_CREDENTIALS *= 'NoCredentials'*

#### SUBDOMAIN_REGISTRATION_WELL_KNOWN_UNAVAILABLE *= 'SubdomainRegistrationWellKnownUnavailable'*

#### SUBDOMAIN_REGISTRATION_UNAUTHORIZED *= 'SubdomainRegistrationUnauthorized'*

#### SUBDOMAIN_REGISTRATION_WELL_KNOWN_MALFORMED *= 'SubdomainRegistrationWellKnownMalformed'*

#### SESSION_PROVIDER_WELL_KNOWN_UNAVAILABLE *= 'SessionProviderWellKnownUnavailable'*

#### RELYING_PARTY_WELL_KNOWN_UNAVAILABLE *= 'RelyingPartyWellKnownUnavailable'*

#### FEDERATED_KEY_THUMBPRINT_MISMATCH *= 'FederatedKeyThumbprintMismatch'*

#### INVALID_FEDERATED_SESSION_URL *= 'InvalidFederatedSessionUrl'*

#### INVALID_FEDERATED_KEY *= 'InvalidFederatedKey'*

#### TOO_MANY_RELYING_ORIGIN_LABELS *= 'TooManyRelyingOriginLabels'*

#### BOUND_COOKIE_SET_FORBIDDEN *= 'BoundCookieSetForbidden'*

#### NET_ERROR *= 'NetError'*

#### PROXY_ERROR *= 'ProxyError'*

#### EMPTY_SESSION_CONFIG *= 'EmptySessionConfig'*

#### INVALID_CREDENTIALS_CONFIG *= 'InvalidCredentialsConfig'*

#### INVALID_CREDENTIALS_TYPE *= 'InvalidCredentialsType'*

#### INVALID_CREDENTIALS_EMPTY_NAME *= 'InvalidCredentialsEmptyName'*

#### INVALID_CREDENTIALS_COOKIE *= 'InvalidCredentialsCookie'*

#### PERSISTENT_HTTP_ERROR *= 'PersistentHttpError'*

#### REGISTRATION_ATTEMPTED_CHALLENGE *= 'RegistrationAttemptedChallenge'*

#### INVALID_SCOPE_ORIGIN *= 'InvalidScopeOrigin'*

#### SCOPE_ORIGIN_CONTAINS_PATH *= 'ScopeOriginContainsPath'*

#### REFRESH_INITIATOR_NOT_STRING *= 'RefreshInitiatorNotString'*

#### REFRESH_INITIATOR_INVALID_HOST_PATTERN *= 'RefreshInitiatorInvalidHostPattern'*

#### INVALID_SCOPE_SPECIFICATION *= 'InvalidScopeSpecification'*

#### MISSING_SCOPE_SPECIFICATION_TYPE *= 'MissingScopeSpecificationType'*

#### EMPTY_SCOPE_SPECIFICATION_DOMAIN *= 'EmptyScopeSpecificationDomain'*

#### EMPTY_SCOPE_SPECIFICATION_PATH *= 'EmptyScopeSpecificationPath'*

#### INVALID_SCOPE_SPECIFICATION_TYPE *= 'InvalidScopeSpecificationType'*

#### INVALID_SCOPE_INCLUDE_SITE *= 'InvalidScopeIncludeSite'*

#### MISSING_SCOPE_INCLUDE_SITE *= 'MissingScopeIncludeSite'*

#### FEDERATED_NOT_AUTHORIZED_BY_PROVIDER *= 'FederatedNotAuthorizedByProvider'*

#### FEDERATED_NOT_AUTHORIZED_BY_RELYING_PARTY *= 'FederatedNotAuthorizedByRelyingParty'*

#### SESSION_PROVIDER_WELL_KNOWN_MALFORMED *= 'SessionProviderWellKnownMalformed'*

#### SESSION_PROVIDER_WELL_KNOWN_HAS_PROVIDER_ORIGIN *= 'SessionProviderWellKnownHasProviderOrigin'*

#### RELYING_PARTY_WELL_KNOWN_MALFORMED *= 'RelyingPartyWellKnownMalformed'*

#### RELYING_PARTY_WELL_KNOWN_HAS_RELYING_ORIGINS *= 'RelyingPartyWellKnownHasRelyingOrigins'*

#### INVALID_FEDERATED_SESSION_PROVIDER_SESSION_MISSING *= 'InvalidFederatedSessionProviderSessionMissing'*

#### INVALID_FEDERATED_SESSION_WRONG_PROVIDER_ORIGIN *= 'InvalidFederatedSessionWrongProviderOrigin'*

#### INVALID_CREDENTIALS_COOKIE_CREATION_TIME *= 'InvalidCredentialsCookieCreationTime'*

#### INVALID_CREDENTIALS_COOKIE_NAME *= 'InvalidCredentialsCookieName'*

#### INVALID_CREDENTIALS_COOKIE_PARSING *= 'InvalidCredentialsCookieParsing'*

#### INVALID_CREDENTIALS_COOKIE_UNPERMITTED_ATTRIBUTE *= 'InvalidCredentialsCookieUnpermittedAttribute'*

#### INVALID_CREDENTIALS_COOKIE_INVALID_DOMAIN *= 'InvalidCredentialsCookieInvalidDomain'*

#### INVALID_CREDENTIALS_COOKIE_PREFIX *= 'InvalidCredentialsCookiePrefix'*

#### INVALID_SCOPE_RULE_PATH *= 'InvalidScopeRulePath'*

#### INVALID_SCOPE_RULE_HOST_PATTERN *= 'InvalidScopeRuleHostPattern'*

#### SCOPE_RULE_ORIGIN_SCOPED_HOST_PATTERN_MISMATCH *= 'ScopeRuleOriginScopedHostPatternMismatch'*

#### SCOPE_RULE_SITE_SCOPED_HOST_PATTERN_MISMATCH *= 'ScopeRuleSiteScopedHostPatternMismatch'*

#### SIGNING_QUOTA_EXCEEDED *= 'SigningQuotaExceeded'*

#### INVALID_CONFIG_JSON *= 'InvalidConfigJson'*

#### INVALID_FEDERATED_SESSION_PROVIDER_FAILED_TO_RESTORE_KEY *= 'InvalidFederatedSessionProviderFailedToRestoreKey'*

#### FAILED_TO_UNWRAP_KEY *= 'FailedToUnwrapKey'*

#### SESSION_DELETED_DURING_REFRESH *= 'SessionDeletedDuringRefresh'*

### *class* DeviceBoundSessionFailedRequest(request_url, net_error=None, response_error=None, response_error_body=None)

Details about a failed device bound session network request.

#### request_url *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

The failed request URL.

#### net_error *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The net error of the response if it was not OK.

#### response_error *: [int](https://docs.python.org/3/library/functions.html#int) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The response code if the net error was OK and the response code was not
200.

#### response_error_body *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The body of the response if the net error was OK, the response code was
not 200, and the response body was not empty.

### *class* CreationEventDetails(fetch_result, new_session=None, failed_request=None)

Session event details specific to creation.

#### fetch_result *: [DeviceBoundSessionFetchResult](#nodriver.cdp.network.DeviceBoundSessionFetchResult)*

The result of the fetch attempt.

#### new_session *: [DeviceBoundSession](#nodriver.cdp.network.DeviceBoundSession) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The session if there was a newly created session. This is populated for
all successful creation events.

#### failed_request *: [DeviceBoundSessionFailedRequest](#nodriver.cdp.network.DeviceBoundSessionFailedRequest) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Details about a failed device bound session network request if there was
one.

### *class* RefreshEventDetails(refresh_result, was_fully_proactive_refresh, fetch_result=None, new_session=None, failed_request=None)

Session event details specific to refresh.

#### refresh_result *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

The result of a refresh.

#### was_fully_proactive_refresh *: [bool](https://docs.python.org/3/library/functions.html#bool)*

See comments on `net::device_bound_sessions::RefreshEventResult::was_fully_proactive_refresh`.

#### fetch_result *: [DeviceBoundSessionFetchResult](#nodriver.cdp.network.DeviceBoundSessionFetchResult) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

If there was a fetch attempt, the result of that.

#### new_session *: [DeviceBoundSession](#nodriver.cdp.network.DeviceBoundSession) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The session display if there was a newly created session. This is populated
for any refresh event that modifies the session config.

#### failed_request *: [DeviceBoundSessionFailedRequest](#nodriver.cdp.network.DeviceBoundSessionFailedRequest) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Details about a failed device bound session network request if there was
one.

### *class* TerminationEventDetails(deletion_reason)

Session event details specific to termination.

#### deletion_reason *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

The reason for a session being deleted.

### *class* ChallengeEventDetails(challenge_result, challenge)

Session event details specific to challenges.

#### challenge_result *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

The result of a challenge.

#### challenge *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

The challenge set.

### *class* LoadNetworkResourcePageResult(success, net_error=None, net_error_name=None, http_status_code=None, stream=None, headers=None)

An object providing the result of a network resource load.

#### success *: [bool](https://docs.python.org/3/library/functions.html#bool)*

#### net_error *: [float](https://docs.python.org/3/library/functions.html#float) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Optional values used for error reporting.

#### net_error_name *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### http_status_code *: [float](https://docs.python.org/3/library/functions.html#float) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### stream *: [StreamHandle](io.md#nodriver.cdp.io.StreamHandle) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

If successful, one of the following two fields holds the result.

#### headers *: [Headers](#nodriver.cdp.network.Headers) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Response headers.

### *class* LoadNetworkResourceOptions(disable_cache, include_credentials)

An options object that may be extended later to better support CORS,
CORB and streaming.

#### disable_cache *: [bool](https://docs.python.org/3/library/functions.html#bool)*

#### include_credentials *: [bool](https://docs.python.org/3/library/functions.html#bool)*

## Commands

Each command is a generator function. The return
type `Generator[x, y, z]` indicates that the generator
*yields* arguments of type `x`, it must be resumed with
an argument of type `y`, and it returns type `z`. In
this library, types `x` and `y` are the same for all
commands, and `z` is the return type you should pay attention
to. For more information, see
[Getting Started: Commands](../../readme.md#getting-started-commands).

### can_clear_browser_cache()

Tells whether clearing browser cache is supported.

#### Deprecated
Deprecated since version 1.3.

* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`bool`](https://docs.python.org/3/library/functions.html#bool)]
* **Returns:**
  True if browser cache can be cleared.

#### Deprecated
Deprecated since version 1.3.

### can_clear_browser_cookies()

Tells whether clearing browser cookies is supported.

#### Deprecated
Deprecated since version 1.3.

* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`bool`](https://docs.python.org/3/library/functions.html#bool)]
* **Returns:**
  True if browser cookies can be cleared.

#### Deprecated
Deprecated since version 1.3.

### can_emulate_network_conditions()

Tells whether emulation of network conditions is supported.

#### Deprecated
Deprecated since version 1.3.

* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`bool`](https://docs.python.org/3/library/functions.html#bool)]
* **Returns:**
  True if emulation of network conditions is supported.

#### Deprecated
Deprecated since version 1.3.

### clear_accepted_encodings_override()

Clears accepted encodings set by setAcceptedEncodings

**EXPERIMENTAL**

* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### clear_browser_cache()

Clears browser cache.

* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### clear_browser_cookies()

Clears browser cookies.

* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### configure_durable_messages(max_total_buffer_size=None, max_resource_buffer_size=None)

Configures storing response bodies outside of renderer, so that these survive
a cross-process navigation.
If maxTotalBufferSize is not set, durable messages are disabled.

**EXPERIMENTAL**

* **Parameters:**
  * **max_total_buffer_size** ([`int`](https://docs.python.org/3/library/functions.html#int) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* Buffer size in bytes to use when preserving network payloads (XHRs, etc).
  * **max_resource_buffer_size** ([`int`](https://docs.python.org/3/library/functions.html#int) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* Per-resource buffer size in bytes to use when preserving network payloads (XHRs, etc).
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### continue_intercepted_request(interception_id, error_reason=None, raw_response=None, url=None, method=None, post_data=None, headers=None, auth_challenge_response=None)

Response to Network.requestIntercepted which either modifies the request to continue with any
modifications, or blocks it, or completes it with the provided response bytes. If a network
fetch occurs as a result which encounters a redirect an additional Network.requestIntercepted
event will be sent with the same InterceptionId.
Deprecated, use Fetch.continueRequest, Fetch.fulfillRequest and Fetch.failRequest instead.

#### Deprecated
Deprecated since version 1.3.

**EXPERIMENTAL**

* **Parameters:**
  * **interception_id** ([`InterceptionId`](#nodriver.cdp.network.InterceptionId))
  * **error_reason** ([`ErrorReason`](#nodriver.cdp.network.ErrorReason) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* If set this causes the request to fail with the given reason. Passing ``Aborted``` for requests marked with ```isNavigationRequest`` also cancels the navigation. Must not be set in response to an authChallenge.
  * **raw_response** ([`str`](https://docs.python.org/3/library/stdtypes.html#str) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* If set the requests completes using with the provided base64 encoded raw response, including HTTP status line and headers etc… Must not be set in response to an authChallenge. (Encoded as a base64 string when passed over JSON)
  * **url** ([`str`](https://docs.python.org/3/library/stdtypes.html#str) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* If set the request url will be modified in a way that’s not observable by page. Must not be set in response to an authChallenge.
  * **method** ([`str`](https://docs.python.org/3/library/stdtypes.html#str) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* If set this allows the request method to be overridden. Must not be set in response to an authChallenge.
  * **post_data** ([`str`](https://docs.python.org/3/library/stdtypes.html#str) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* If set this allows postData to be set. Must not be set in response to an authChallenge.
  * **headers** ([`Headers`](#nodriver.cdp.network.Headers) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* If set this allows the request headers to be changed. Must not be set in response to an authChallenge.
  * **auth_challenge_response** ([`AuthChallengeResponse`](#nodriver.cdp.network.AuthChallengeResponse) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* Response to a requestIntercepted with an authChallenge. Must not be set otherwise.

#### Deprecated
Deprecated since version 1.3.

* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### delete_cookies(name, url=None, domain=None, path=None, partition_key=None)

Deletes browser cookies with matching name and url or domain/path/partitionKey pair.

* **Parameters:**
  * **name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str)) – Name of the cookies to remove.
  * **url** ([`str`](https://docs.python.org/3/library/stdtypes.html#str) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* If specified, deletes all the cookies with the given name where domain and path match provided URL.
  * **domain** ([`str`](https://docs.python.org/3/library/stdtypes.html#str) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* If specified, deletes only cookies with the exact domain.
  * **path** ([`str`](https://docs.python.org/3/library/stdtypes.html#str) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* If specified, deletes only cookies with the exact path.
  * **partition_key** ([`CookiePartitionKey`](#nodriver.cdp.network.CookiePartitionKey) | [`None`](https://docs.python.org/3/library/constants.html#None)) – **(EXPERIMENTAL)**  *(Optional)* If specified, deletes only cookies with the the given name and partitionKey where all partition key attributes match the cookie partition key attribute.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### delete_device_bound_session(key)

Deletes a device bound session.

**EXPERIMENTAL**

* **Parameters:**
  **key** ([`DeviceBoundSessionKey`](#nodriver.cdp.network.DeviceBoundSessionKey))
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### disable()

Disables network tracking, prevents network events from being sent to the client.

* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### emulate_network_conditions(offline, latency, download_throughput, upload_throughput, connection_type=None, packet_loss=None, packet_queue_length=None, packet_reordering=None)

Activates emulation of network conditions. This command is deprecated in favor of the emulateNetworkConditionsByRule
and overrideNetworkState commands, which can be used together to the same effect.

#### Deprecated
Deprecated since version 1.3.

* **Parameters:**
  * **offline** ([`bool`](https://docs.python.org/3/library/functions.html#bool)) – True to emulate internet disconnection.
  * **latency** ([`float`](https://docs.python.org/3/library/functions.html#float)) – Minimum latency from request sent to response headers received (ms).
  * **download_throughput** ([`float`](https://docs.python.org/3/library/functions.html#float)) – Maximal aggregated download throughput (bytes/sec). -1 disables download throttling.
  * **upload_throughput** ([`float`](https://docs.python.org/3/library/functions.html#float)) – Maximal aggregated upload throughput (bytes/sec).  -1 disables upload throttling.
  * **connection_type** ([`ConnectionType`](#nodriver.cdp.network.ConnectionType) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* Connection type if known.
  * **packet_loss** ([`float`](https://docs.python.org/3/library/functions.html#float) | [`None`](https://docs.python.org/3/library/constants.html#None)) – **(EXPERIMENTAL)**  *(Optional)* WebRTC packet loss (percent, 0-100). 0 disables packet loss emulation, 100 drops all the packets.
  * **packet_queue_length** ([`int`](https://docs.python.org/3/library/functions.html#int) | [`None`](https://docs.python.org/3/library/constants.html#None)) – **(EXPERIMENTAL)**  *(Optional)* WebRTC packet queue length (packet). 0 removes any queue length limitations.
  * **packet_reordering** ([`bool`](https://docs.python.org/3/library/functions.html#bool) | [`None`](https://docs.python.org/3/library/constants.html#None)) – **(EXPERIMENTAL)**  *(Optional)* WebRTC packetReordering feature.

#### Deprecated
Deprecated since version 1.3.

* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### emulate_network_conditions_by_rule(matched_network_conditions, offline=None, emulate_offline_service_worker=None)

Activates emulation of network conditions for individual requests using URL match patterns. Unlike the deprecated
Network.emulateNetworkConditions this method does not affect `navigator` state. Use Network.overrideNetworkState to
explicitly modify `navigator` behavior.

**EXPERIMENTAL**

* **Parameters:**
  * **offline** ([`bool`](https://docs.python.org/3/library/functions.html#bool) | [`None`](https://docs.python.org/3/library/constants.html#None)) – **(DEPRECATED)**  *(Optional)* True to emulate internet disconnection. Deprecated, use the offline property in matchedNetworkConditions or emulateOfflineServiceWorker instead.
  * **emulate_offline_service_worker** ([`bool`](https://docs.python.org/3/library/functions.html#bool) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* True to emulate offline service worker.
  * **matched_network_conditions** ([`List`](https://docs.python.org/3/library/typing.html#typing.List)[[`NetworkConditions`](#nodriver.cdp.network.NetworkConditions)]) – Configure conditions for matching requests. If multiple entries match a request, the first entry wins.  Global conditions can be configured by leaving the urlPattern for the conditions empty. These global conditions are also applied for throttling of p2p connections.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`List`](https://docs.python.org/3/library/typing.html#typing.List)[[`str`](https://docs.python.org/3/library/stdtypes.html#str)]]
* **Returns:**
  An id for each entry in matchedNetworkConditions. The id will be included in the requestWillBeSentExtraInfo for requests affected by a rule.

### enable(max_total_buffer_size=None, max_resource_buffer_size=None, max_post_data_size=None, report_direct_socket_traffic=None, enable_durable_messages=None)

Enables network tracking, network events will now be delivered to the client.

* **Parameters:**
  * **max_total_buffer_size** ([`int`](https://docs.python.org/3/library/functions.html#int) | [`None`](https://docs.python.org/3/library/constants.html#None)) – **(EXPERIMENTAL)**  *(Optional)* Buffer size in bytes to use when preserving network payloads (XHRs, etc). This is the maximum number of bytes that will be collected by this DevTools session.
  * **max_resource_buffer_size** ([`int`](https://docs.python.org/3/library/functions.html#int) | [`None`](https://docs.python.org/3/library/constants.html#None)) – **(EXPERIMENTAL)**  *(Optional)* Per-resource buffer size in bytes to use when preserving network payloads (XHRs, etc).
  * **max_post_data_size** ([`int`](https://docs.python.org/3/library/functions.html#int) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* Longest post body size (in bytes) that would be included in requestWillBeSent notification
  * **report_direct_socket_traffic** ([`bool`](https://docs.python.org/3/library/functions.html#bool) | [`None`](https://docs.python.org/3/library/constants.html#None)) – **(EXPERIMENTAL)**  *(Optional)* Whether DirectSocket chunk send/receive events should be reported.
  * **enable_durable_messages** ([`bool`](https://docs.python.org/3/library/functions.html#bool) | [`None`](https://docs.python.org/3/library/constants.html#None)) – **(EXPERIMENTAL)**  *(Optional)* Enable storing response bodies outside of renderer, so that these survive a cross-process navigation. Requires maxTotalBufferSize to be set. Currently defaults to false. This field is being deprecated in favor of the dedicated configureDurableMessages command, due to the possibility of deadlocks when awaiting Network.enable before issuing Runtime.runIfWaitingForDebugger.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### enable_device_bound_sessions(enable)

Sets up tracking device bound sessions and fetching of initial set of sessions.

**EXPERIMENTAL**

* **Parameters:**
  **enable** ([`bool`](https://docs.python.org/3/library/functions.html#bool)) – Whether to enable or disable events.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### enable_reporting_api(enable)

Enables tracking for the Reporting API, events generated by the Reporting API will now be delivered to the client.
Enabling triggers ‘reportingApiReportAdded’ for all existing reports.

**EXPERIMENTAL**

* **Parameters:**
  **enable** ([`bool`](https://docs.python.org/3/library/functions.html#bool)) – Whether to enable or disable events for the Reporting API
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### fetch_schemeful_site(origin)

Fetches the schemeful site for a specific origin.

**EXPERIMENTAL**

* **Parameters:**
  **origin** ([`str`](https://docs.python.org/3/library/stdtypes.html#str)) – The URL origin.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`str`](https://docs.python.org/3/library/stdtypes.html#str)]
* **Returns:**
  The corresponding schemeful site.

### get_all_cookies()

Returns all browser cookies. Depending on the backend support, will return detailed cookie
information in the `cookies` field.
Deprecated. Use Storage.getCookies instead.

#### Deprecated
Deprecated since version 1.3.

* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`List`](https://docs.python.org/3/library/typing.html#typing.List)[[`Cookie`](#nodriver.cdp.network.Cookie)]]
* **Returns:**
  Array of cookie objects.

#### Deprecated
Deprecated since version 1.3.

### get_certificate(origin)

Returns the DER-encoded certificate.

**EXPERIMENTAL**

* **Parameters:**
  **origin** ([`str`](https://docs.python.org/3/library/stdtypes.html#str)) – Origin to get certificate for.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`List`](https://docs.python.org/3/library/typing.html#typing.List)[[`str`](https://docs.python.org/3/library/stdtypes.html#str)]]
* **Returns:**

### get_cookies(urls=None)

Returns all browser cookies for the current URL. Depending on the backend support, will return
detailed cookie information in the `cookies` field.

* **Parameters:**
  **urls** ([`List`](https://docs.python.org/3/library/typing.html#typing.List)[[`str`](https://docs.python.org/3/library/stdtypes.html#str)] | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* The list of URLs for which applicable cookies will be fetched. If not specified, it’s assumed to be set to the list containing the URLs of the page and all of its subframes.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`List`](https://docs.python.org/3/library/typing.html#typing.List)[[`Cookie`](#nodriver.cdp.network.Cookie)]]
* **Returns:**
  Array of cookie objects.

### get_request_post_data(request_id)

Returns post data sent with the request. Returns an error when no data was sent with the request.

* **Parameters:**
  **request_id** ([`RequestId`](#nodriver.cdp.network.RequestId)) – Identifier of the network request to get content for.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Tuple`](https://docs.python.org/3/library/typing.html#typing.Tuple)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`bool`](https://docs.python.org/3/library/functions.html#bool)]]
* **Returns:**
  A tuple with the following items:
  1. **postData** - Request body string, omitting files from multipart requests
  2. **base64Encoded** - True, if content was sent as base64.

### get_response_body(request_id)

Returns content served for the given request.

* **Parameters:**
  **request_id** ([`RequestId`](#nodriver.cdp.network.RequestId)) – Identifier of the network request to get content for.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Tuple`](https://docs.python.org/3/library/typing.html#typing.Tuple)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`bool`](https://docs.python.org/3/library/functions.html#bool)]]
* **Returns:**
  A tuple with the following items:
  1. **body** - Response body.
  2. **base64Encoded** - True, if content was sent as base64.

### get_response_body_for_interception(interception_id)

Returns content served for the given currently intercepted request.

**EXPERIMENTAL**

* **Parameters:**
  **interception_id** ([`InterceptionId`](#nodriver.cdp.network.InterceptionId)) – Identifier for the intercepted request to get body for.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Tuple`](https://docs.python.org/3/library/typing.html#typing.Tuple)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`bool`](https://docs.python.org/3/library/functions.html#bool)]]
* **Returns:**
  A tuple with the following items:
  1. **body** - Response body.
  2. **base64Encoded** - True, if content was sent as base64.

### get_security_isolation_status(frame_id=None)

Returns information about the COEP/COOP isolation status.

**EXPERIMENTAL**

* **Parameters:**
  **frame_id** ([`FrameId`](page.md#nodriver.cdp.page.FrameId) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* If no frameId is provided, the status of the target is provided.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`SecurityIsolationStatus`](#nodriver.cdp.network.SecurityIsolationStatus)]
* **Returns:**

### load_network_resource(url, options, frame_id=None)

Fetches the resource and returns the content.

**EXPERIMENTAL**

* **Parameters:**
  * **frame_id** ([`FrameId`](page.md#nodriver.cdp.page.FrameId) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* Frame id to get the resource for. Mandatory for frame targets, and should be omitted for worker targets.
  * **url** ([`str`](https://docs.python.org/3/library/stdtypes.html#str)) – URL of the resource to get content for.
  * **options** ([`LoadNetworkResourceOptions`](#nodriver.cdp.network.LoadNetworkResourceOptions)) – Options for the request.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`LoadNetworkResourcePageResult`](#nodriver.cdp.network.LoadNetworkResourcePageResult)]
* **Returns:**

### override_network_state(offline, latency, download_throughput, upload_throughput, connection_type=None)

Override the state of navigator.onLine and navigator.connection.

**EXPERIMENTAL**

* **Parameters:**
  * **offline** ([`bool`](https://docs.python.org/3/library/functions.html#bool)) – True to emulate internet disconnection.
  * **latency** ([`float`](https://docs.python.org/3/library/functions.html#float)) – Minimum latency from request sent to response headers received (ms).
  * **download_throughput** ([`float`](https://docs.python.org/3/library/functions.html#float)) – Maximal aggregated download throughput (bytes/sec). -1 disables download throttling.
  * **upload_throughput** ([`float`](https://docs.python.org/3/library/functions.html#float)) – Maximal aggregated upload throughput (bytes/sec).  -1 disables upload throttling.
  * **connection_type** ([`ConnectionType`](#nodriver.cdp.network.ConnectionType) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* Connection type if known.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### replay_xhr(request_id)

This method sends a new XMLHttpRequest which is identical to the original one. The following
parameters should be identical: method, url, async, request body, extra headers, withCredentials
attribute, user, password.

**EXPERIMENTAL**

* **Parameters:**
  **request_id** ([`RequestId`](#nodriver.cdp.network.RequestId)) – Identifier of XHR to replay.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### search_in_response_body(request_id, query, case_sensitive=None, is_regex=None)

Searches for given string in response content.

**EXPERIMENTAL**

* **Parameters:**
  * **request_id** ([`RequestId`](#nodriver.cdp.network.RequestId)) – Identifier of the network response to search.
  * **query** ([`str`](https://docs.python.org/3/library/stdtypes.html#str)) – String to search for.
  * **case_sensitive** ([`bool`](https://docs.python.org/3/library/functions.html#bool) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* If true, search is case sensitive.
  * **is_regex** ([`bool`](https://docs.python.org/3/library/functions.html#bool) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* If true, treats string parameter as regex.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`List`](https://docs.python.org/3/library/typing.html#typing.List)[[`SearchMatch`](debugger.md#nodriver.cdp.debugger.SearchMatch)]]
* **Returns:**
  List of search matches.

### set_accepted_encodings(encodings)

Sets a list of content encodings that will be accepted. Empty list means no encoding is accepted.

**EXPERIMENTAL**

* **Parameters:**
  **encodings** ([`List`](https://docs.python.org/3/library/typing.html#typing.List)[[`ContentEncoding`](#nodriver.cdp.network.ContentEncoding)]) – List of accepted content encodings.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### set_attach_debug_stack(enabled)

Specifies whether to attach a page script stack id in requests

**EXPERIMENTAL**

* **Parameters:**
  **enabled** ([`bool`](https://docs.python.org/3/library/functions.html#bool)) – Whether to attach a page script stack for debugging purpose.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### set_blocked_ur_ls(url_patterns=None, urls=None)

Blocks URLs from loading.

**EXPERIMENTAL**

* **Parameters:**
  * **url_patterns** ([`List`](https://docs.python.org/3/library/typing.html#typing.List)[[`BlockPattern`](#nodriver.cdp.network.BlockPattern)] | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* Patterns to match in the order in which they are given. These patterns also take precedence over any wildcard patterns defined in ``urls``.
  * **urls** ([`List`](https://docs.python.org/3/library/typing.html#typing.List)[[`str`](https://docs.python.org/3/library/stdtypes.html#str)] | [`None`](https://docs.python.org/3/library/constants.html#None)) – **(DEPRECATED)**  *(Optional)* URL patterns to block. Wildcards (‘\*’) are allowed.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### set_bypass_service_worker(bypass)

Toggles ignoring of service worker for each request.

* **Parameters:**
  **bypass** ([`bool`](https://docs.python.org/3/library/functions.html#bool)) – Bypass service worker and load from network.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### set_cache_disabled(cache_disabled)

Toggles ignoring cache for each request. If `true`, cache will not be used.

* **Parameters:**
  **cache_disabled** ([`bool`](https://docs.python.org/3/library/functions.html#bool)) – Cache disabled state.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### set_cookie(name, value, url=None, domain=None, path=None, secure=None, http_only=None, same_site=None, expires=None, priority=None, source_scheme=None, source_port=None, partition_key=None)

Sets a cookie with the given cookie data; may overwrite equivalent cookies if they exist.

* **Parameters:**
  * **name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str)) – Cookie name.
  * **value** ([`str`](https://docs.python.org/3/library/stdtypes.html#str)) – Cookie value.
  * **url** ([`str`](https://docs.python.org/3/library/stdtypes.html#str) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* The request-URI to associate with the setting of the cookie. This value can affect the default domain, path, source port, and source scheme values of the created cookie.
  * **domain** ([`str`](https://docs.python.org/3/library/stdtypes.html#str) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* Cookie domain.
  * **path** ([`str`](https://docs.python.org/3/library/stdtypes.html#str) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* Cookie path.
  * **secure** ([`bool`](https://docs.python.org/3/library/functions.html#bool) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* True if cookie is secure.
  * **http_only** ([`bool`](https://docs.python.org/3/library/functions.html#bool) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* True if cookie is http-only.
  * **same_site** ([`CookieSameSite`](#nodriver.cdp.network.CookieSameSite) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* Cookie SameSite type.
  * **expires** ([`TimeSinceEpoch`](#nodriver.cdp.network.TimeSinceEpoch) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* Cookie expiration date, session cookie if not set
  * **priority** ([`CookiePriority`](#nodriver.cdp.network.CookiePriority) | [`None`](https://docs.python.org/3/library/constants.html#None)) – **(EXPERIMENTAL)**  *(Optional)* Cookie Priority type.
  * **source_scheme** ([`CookieSourceScheme`](#nodriver.cdp.network.CookieSourceScheme) | [`None`](https://docs.python.org/3/library/constants.html#None)) – **(EXPERIMENTAL)**  *(Optional)* Cookie source scheme type.
  * **source_port** ([`int`](https://docs.python.org/3/library/functions.html#int) | [`None`](https://docs.python.org/3/library/constants.html#None)) – **(EXPERIMENTAL)**  *(Optional)* Cookie source port. Valid values are {-1, [1, 65535]}, -1 indicates an unspecified port. An unspecified port value allows protocol clients to emulate legacy cookie scope for the port. This is a temporary ability and it will be removed in the future.
  * **partition_key** ([`CookiePartitionKey`](#nodriver.cdp.network.CookiePartitionKey) | [`None`](https://docs.python.org/3/library/constants.html#None)) – **(EXPERIMENTAL)**  *(Optional)* Cookie partition key. If not set, the cookie will be set as not partitioned.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`bool`](https://docs.python.org/3/library/functions.html#bool)]
* **Returns:**
  Always set to true. If an error occurs, the response indicates protocol error.

### set_cookie_controls(enable_third_party_cookie_restriction)

Sets Controls for third-party cookie access
Page reload is required before the new cookie behavior will be observed

**EXPERIMENTAL**

* **Parameters:**
  **enable_third_party_cookie_restriction** ([`bool`](https://docs.python.org/3/library/functions.html#bool)) – Whether 3pc restriction is enabled.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### set_cookies(cookies)

Sets given cookies.

* **Parameters:**
  **cookies** ([`List`](https://docs.python.org/3/library/typing.html#typing.List)[[`CookieParam`](#nodriver.cdp.network.CookieParam)]) – Cookies to be set.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### set_extra_http_headers(headers)

Specifies whether to always send extra HTTP headers with the requests from this page.

* **Parameters:**
  **headers** ([`Headers`](#nodriver.cdp.network.Headers)) – Map with extra HTTP headers.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### set_request_interception(patterns)

Sets the requests to intercept that match the provided patterns and optionally resource types.
Deprecated, please use Fetch.enable instead.

#### Deprecated
Deprecated since version 1.3.

**EXPERIMENTAL**

* **Parameters:**
  **patterns** ([`List`](https://docs.python.org/3/library/typing.html#typing.List)[[`RequestPattern`](#nodriver.cdp.network.RequestPattern)]) – Requests matching any of these patterns will be forwarded and wait for the corresponding continueInterceptedRequest call.

#### Deprecated
Deprecated since version 1.3.

* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### set_user_agent_override(user_agent, accept_language=None, platform=None, user_agent_metadata=None)

Allows overriding user agent with the given string.

* **Parameters:**
  * **user_agent** ([`str`](https://docs.python.org/3/library/stdtypes.html#str)) – User agent to use.
  * **accept_language** ([`str`](https://docs.python.org/3/library/stdtypes.html#str) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* Browser language to emulate.
  * **platform** ([`str`](https://docs.python.org/3/library/stdtypes.html#str) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* The platform navigator.platform should return.
  * **user_agent_metadata** ([`UserAgentMetadata`](emulation.md#nodriver.cdp.emulation.UserAgentMetadata) | [`None`](https://docs.python.org/3/library/constants.html#None)) – **(EXPERIMENTAL)**  *(Optional)* To be sent in Sec-CH-UA-\* headers and returned in navigator.userAgentData
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### stream_resource_content(request_id)

Enables streaming of the response for the given requestId.
If enabled, the dataReceived event contains the data that was received during streaming.

**EXPERIMENTAL**

* **Parameters:**
  **request_id** ([`RequestId`](#nodriver.cdp.network.RequestId)) – Identifier of the request to stream.
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`str`](https://docs.python.org/3/library/stdtypes.html#str)]
* **Returns:**
  Data that has been buffered until streaming is enabled. (Encoded as a base64 string when passed over JSON)

### take_response_body_for_interception_as_stream(interception_id)

Returns a handle to the stream representing the response body. Note that after this command,
the intercepted request can’t be continued as is – you either need to cancel it or to provide
the response body. The stream only supports sequential read, IO.read will fail if the position
is specified.

**EXPERIMENTAL**

* **Parameters:**
  **interception_id** ([`InterceptionId`](#nodriver.cdp.network.InterceptionId))
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`StreamHandle`](io.md#nodriver.cdp.io.StreamHandle)]
* **Returns:**

## Events

Generally, you do not need to instantiate CDP events
yourself. Instead, the API creates events for you and then
you use the event’s attributes.

### *class* DataReceived(request_id, timestamp, data_length, encoded_data_length, data)

Fired when data chunk was received over the network.

#### request_id *: [RequestId](#nodriver.cdp.network.RequestId)*

Request identifier.

#### timestamp *: [MonotonicTime](#nodriver.cdp.network.MonotonicTime)*

Timestamp.

#### data_length *: [int](https://docs.python.org/3/library/functions.html#int)*

Data chunk length.

#### encoded_data_length *: [int](https://docs.python.org/3/library/functions.html#int)*

Actual bytes received (might be less than dataLength for compressed encodings).

#### data *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)*

Data that was received. (Encoded as a base64 string when passed over JSON)

### *class* EventSourceMessageReceived(request_id, timestamp, event_name, event_id, data)

Fired when EventSource message is received.

#### request_id *: [RequestId](#nodriver.cdp.network.RequestId)*

Request identifier.

#### timestamp *: [MonotonicTime](#nodriver.cdp.network.MonotonicTime)*

Timestamp.

#### event_name *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Message type.

#### event_id *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Message identifier.

#### data *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Message content.

### *class* LoadingFailed(request_id, timestamp, type_, error_text, canceled, blocked_reason, cors_error_status)

Fired when HTTP request has failed to load.

#### request_id *: [RequestId](#nodriver.cdp.network.RequestId)*

Request identifier.

#### timestamp *: [MonotonicTime](#nodriver.cdp.network.MonotonicTime)*

Timestamp.

#### type_ *: [ResourceType](#nodriver.cdp.network.ResourceType)*

Resource type.

#### error_text *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

//cs.chromium.org/chromium/src/net/base/net_error_list.h

* **Type:**
  Error message. List of network errors
* **Type:**
  https

#### canceled *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)*

True if loading was canceled.

#### blocked_reason *: [BlockedReason](#nodriver.cdp.network.BlockedReason) | [None](https://docs.python.org/3/library/constants.html#None)*

The reason why loading was blocked, if any.

#### cors_error_status *: [CorsErrorStatus](#nodriver.cdp.network.CorsErrorStatus) | [None](https://docs.python.org/3/library/constants.html#None)*

The reason why loading was blocked by CORS, if any.

### *class* LoadingFinished(request_id, timestamp, encoded_data_length)

Fired when HTTP request has finished loading.

#### request_id *: [RequestId](#nodriver.cdp.network.RequestId)*

Request identifier.

#### timestamp *: [MonotonicTime](#nodriver.cdp.network.MonotonicTime)*

Timestamp.

#### encoded_data_length *: [float](https://docs.python.org/3/library/functions.html#float)*

Total number of bytes received for this request.

### *class* RequestIntercepted(interception_id, request, frame_id, resource_type, is_navigation_request, is_download, redirect_url, auth_challenge, response_error_reason, response_status_code, response_headers, request_id)

**EXPERIMENTAL**

Details of an intercepted HTTP request, which must be either allowed, blocked, modified or
mocked.
Deprecated, use Fetch.requestPaused instead.

#### Deprecated
Deprecated since version 1.3.

#### interception_id *: [InterceptionId](#nodriver.cdp.network.InterceptionId)*

Each request the page makes will have a unique id, however if any redirects are encountered
while processing that fetch, they will be reported with the same id as the original fetch.
Likewise if HTTP authentication is needed then the same fetch id will be used.

#### request *: [Request](#nodriver.cdp.network.Request)*

#### frame_id *: [FrameId](page.md#nodriver.cdp.page.FrameId)*

The id of the frame that initiated the request.

#### resource_type *: [ResourceType](#nodriver.cdp.network.ResourceType)*

How the requested resource will be used.

#### is_navigation_request *: [bool](https://docs.python.org/3/library/functions.html#bool)*

Whether this is a navigation request, which can abort the navigation completely.

#### is_download *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)*

Set if the request is a navigation that will result in a download.
Only present after response is received from the server (i.e. HeadersReceived stage).

#### redirect_url *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)*

Redirect location, only sent if a redirect was intercepted.

#### auth_challenge *: [AuthChallenge](#nodriver.cdp.network.AuthChallenge) | [None](https://docs.python.org/3/library/constants.html#None)*

Details of the Authorization Challenge encountered. If this is set then
continueInterceptedRequest must contain an authChallengeResponse.

#### response_error_reason *: [ErrorReason](#nodriver.cdp.network.ErrorReason) | [None](https://docs.python.org/3/library/constants.html#None)*

Response error if intercepted at response stage or if redirect occurred while intercepting
request.

#### response_status_code *: [int](https://docs.python.org/3/library/functions.html#int) | [None](https://docs.python.org/3/library/constants.html#None)*

Response code if intercepted at response stage or if redirect occurred while intercepting
request or auth retry occurred.

#### response_headers *: [Headers](#nodriver.cdp.network.Headers) | [None](https://docs.python.org/3/library/constants.html#None)*

Response headers if intercepted at the response stage or if redirect occurred while
intercepting request or auth retry occurred.

#### request_id *: [RequestId](#nodriver.cdp.network.RequestId) | [None](https://docs.python.org/3/library/constants.html#None)*

If the intercepted request had a corresponding requestWillBeSent event fired for it, then
this requestId will be the same as the requestId present in the requestWillBeSent event.

### *class* RequestServedFromCache(request_id)

Fired if request ended up loading from cache.

#### request_id *: [RequestId](#nodriver.cdp.network.RequestId)*

Request identifier.

### *class* RequestWillBeSent(request_id, loader_id, document_url, request, timestamp, wall_time, initiator, redirect_has_extra_info, redirect_response, type_, frame_id, has_user_gesture, render_blocking_behavior)

Fired when page is about to send HTTP request.

#### request_id *: [RequestId](#nodriver.cdp.network.RequestId)*

Request identifier.

#### loader_id *: [LoaderId](#nodriver.cdp.network.LoaderId)*

Loader identifier. Empty string if the request is fetched from worker.

#### document_url *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

URL of the document this request is loaded for.

#### request *: [Request](#nodriver.cdp.network.Request)*

Request data.

#### timestamp *: [MonotonicTime](#nodriver.cdp.network.MonotonicTime)*

Timestamp.

#### wall_time *: [TimeSinceEpoch](#nodriver.cdp.network.TimeSinceEpoch)*

Timestamp.

#### initiator *: [Initiator](#nodriver.cdp.network.Initiator)*

Request initiator.

#### redirect_has_extra_info *: [bool](https://docs.python.org/3/library/functions.html#bool)*

In the case that redirectResponse is populated, this flag indicates whether
requestWillBeSentExtraInfo and responseReceivedExtraInfo events will be or were emitted
for the request which was just redirected.

#### redirect_response *: [Response](#nodriver.cdp.network.Response) | [None](https://docs.python.org/3/library/constants.html#None)*

Redirect response data.

#### type_ *: [ResourceType](#nodriver.cdp.network.ResourceType) | [None](https://docs.python.org/3/library/constants.html#None)*

Type of this resource.

#### frame_id *: [FrameId](page.md#nodriver.cdp.page.FrameId) | [None](https://docs.python.org/3/library/constants.html#None)*

Frame identifier.

#### has_user_gesture *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)*

Whether the request is initiated by a user gesture. Defaults to false.

#### render_blocking_behavior *: [RenderBlockingBehavior](#nodriver.cdp.network.RenderBlockingBehavior) | [None](https://docs.python.org/3/library/constants.html#None)*

The render-blocking behavior of the request.

### *class* ResourceChangedPriority(request_id, new_priority, timestamp)

**EXPERIMENTAL**

Fired when resource loading priority is changed

#### request_id *: [RequestId](#nodriver.cdp.network.RequestId)*

Request identifier.

#### new_priority *: [ResourcePriority](#nodriver.cdp.network.ResourcePriority)*

New priority

#### timestamp *: [MonotonicTime](#nodriver.cdp.network.MonotonicTime)*

Timestamp.

### *class* SignedExchangeReceived(request_id, info)

**EXPERIMENTAL**

Fired when a signed exchange was received over the network

#### request_id *: [RequestId](#nodriver.cdp.network.RequestId)*

Request identifier.

#### info *: [SignedExchangeInfo](#nodriver.cdp.network.SignedExchangeInfo)*

Information about the signed exchange response.

### *class* ResponseReceived(request_id, loader_id, timestamp, type_, response, has_extra_info, frame_id)

Fired when HTTP response is available.

#### request_id *: [RequestId](#nodriver.cdp.network.RequestId)*

Request identifier.

#### loader_id *: [LoaderId](#nodriver.cdp.network.LoaderId)*

Loader identifier. Empty string if the request is fetched from worker.

#### timestamp *: [MonotonicTime](#nodriver.cdp.network.MonotonicTime)*

Timestamp.

#### type_ *: [ResourceType](#nodriver.cdp.network.ResourceType)*

Resource type.

#### response *: [Response](#nodriver.cdp.network.Response)*

Response data.

#### has_extra_info *: [bool](https://docs.python.org/3/library/functions.html#bool)*

Indicates whether requestWillBeSentExtraInfo and responseReceivedExtraInfo events will be
or were emitted for this request.

#### frame_id *: [FrameId](page.md#nodriver.cdp.page.FrameId) | [None](https://docs.python.org/3/library/constants.html#None)*

Frame identifier.

### *class* WebSocketClosed(request_id, timestamp)

Fired when WebSocket is closed.

#### request_id *: [RequestId](#nodriver.cdp.network.RequestId)*

Request identifier.

#### timestamp *: [MonotonicTime](#nodriver.cdp.network.MonotonicTime)*

Timestamp.

### *class* WebSocketCreated(request_id, url, initiator)

Fired upon WebSocket creation.

#### request_id *: [RequestId](#nodriver.cdp.network.RequestId)*

Request identifier.

#### url *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

WebSocket request URL.

#### initiator *: [Initiator](#nodriver.cdp.network.Initiator) | [None](https://docs.python.org/3/library/constants.html#None)*

Request initiator.

### *class* WebSocketFrameError(request_id, timestamp, error_message)

Fired when WebSocket message error occurs.

#### request_id *: [RequestId](#nodriver.cdp.network.RequestId)*

Request identifier.

#### timestamp *: [MonotonicTime](#nodriver.cdp.network.MonotonicTime)*

Timestamp.

#### error_message *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

WebSocket error message.

### *class* WebSocketFrameReceived(request_id, timestamp, response)

Fired when WebSocket message is received.

#### request_id *: [RequestId](#nodriver.cdp.network.RequestId)*

Request identifier.

#### timestamp *: [MonotonicTime](#nodriver.cdp.network.MonotonicTime)*

Timestamp.

#### response *: [WebSocketFrame](#nodriver.cdp.network.WebSocketFrame)*

WebSocket response data.

### *class* WebSocketFrameSent(request_id, timestamp, response)

Fired when WebSocket message is sent.

#### request_id *: [RequestId](#nodriver.cdp.network.RequestId)*

Request identifier.

#### timestamp *: [MonotonicTime](#nodriver.cdp.network.MonotonicTime)*

Timestamp.

#### response *: [WebSocketFrame](#nodriver.cdp.network.WebSocketFrame)*

WebSocket response data.

### *class* WebSocketHandshakeResponseReceived(request_id, timestamp, response)

Fired when WebSocket handshake response becomes available.

#### request_id *: [RequestId](#nodriver.cdp.network.RequestId)*

Request identifier.

#### timestamp *: [MonotonicTime](#nodriver.cdp.network.MonotonicTime)*

Timestamp.

#### response *: [WebSocketResponse](#nodriver.cdp.network.WebSocketResponse)*

WebSocket response data.

### *class* WebSocketWillSendHandshakeRequest(request_id, timestamp, wall_time, request)

Fired when WebSocket is about to initiate handshake.

#### request_id *: [RequestId](#nodriver.cdp.network.RequestId)*

Request identifier.

#### timestamp *: [MonotonicTime](#nodriver.cdp.network.MonotonicTime)*

Timestamp.

#### wall_time *: [TimeSinceEpoch](#nodriver.cdp.network.TimeSinceEpoch)*

UTC Timestamp.

#### request *: [WebSocketRequest](#nodriver.cdp.network.WebSocketRequest)*

WebSocket request data.

### *class* WebTransportCreated(transport_id, url, timestamp, initiator)

Fired upon WebTransport creation.

#### transport_id *: [RequestId](#nodriver.cdp.network.RequestId)*

WebTransport identifier.

#### url *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

WebTransport request URL.

#### timestamp *: [MonotonicTime](#nodriver.cdp.network.MonotonicTime)*

Timestamp.

#### initiator *: [Initiator](#nodriver.cdp.network.Initiator) | [None](https://docs.python.org/3/library/constants.html#None)*

Request initiator.

### *class* WebTransportConnectionEstablished(transport_id, timestamp)

Fired when WebTransport handshake is finished.

#### transport_id *: [RequestId](#nodriver.cdp.network.RequestId)*

WebTransport identifier.

#### timestamp *: [MonotonicTime](#nodriver.cdp.network.MonotonicTime)*

Timestamp.

### *class* WebTransportClosed(transport_id, timestamp)

Fired when WebTransport is disposed.

#### transport_id *: [RequestId](#nodriver.cdp.network.RequestId)*

WebTransport identifier.

#### timestamp *: [MonotonicTime](#nodriver.cdp.network.MonotonicTime)*

Timestamp.

### *class* DirectTCPSocketCreated(identifier, remote_addr, remote_port, options, timestamp, initiator)

**EXPERIMENTAL**

Fired upon direct_socket.TCPSocket creation.

#### identifier *: [RequestId](#nodriver.cdp.network.RequestId)*

#### remote_addr *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### remote_port *: [int](https://docs.python.org/3/library/functions.html#int)*

Unsigned int 16.

#### options *: [DirectTCPSocketOptions](#nodriver.cdp.network.DirectTCPSocketOptions)*

#### timestamp *: [MonotonicTime](#nodriver.cdp.network.MonotonicTime)*

#### initiator *: [Initiator](#nodriver.cdp.network.Initiator) | [None](https://docs.python.org/3/library/constants.html#None)*

### *class* DirectTCPSocketOpened(identifier, remote_addr, remote_port, timestamp, local_addr, local_port)

**EXPERIMENTAL**

Fired when direct_socket.TCPSocket connection is opened.

#### identifier *: [RequestId](#nodriver.cdp.network.RequestId)*

#### remote_addr *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### remote_port *: [int](https://docs.python.org/3/library/functions.html#int)*

Expected to be unsigned integer.

#### timestamp *: [MonotonicTime](#nodriver.cdp.network.MonotonicTime)*

#### local_addr *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)*

#### local_port *: [int](https://docs.python.org/3/library/functions.html#int) | [None](https://docs.python.org/3/library/constants.html#None)*

Expected to be unsigned integer.

### *class* DirectTCPSocketAborted(identifier, error_message, timestamp)

**EXPERIMENTAL**

Fired when direct_socket.TCPSocket is aborted.

#### identifier *: [RequestId](#nodriver.cdp.network.RequestId)*

#### error_message *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### timestamp *: [MonotonicTime](#nodriver.cdp.network.MonotonicTime)*

### *class* DirectTCPSocketClosed(identifier, timestamp)

**EXPERIMENTAL**

Fired when direct_socket.TCPSocket is closed.

#### identifier *: [RequestId](#nodriver.cdp.network.RequestId)*

#### timestamp *: [MonotonicTime](#nodriver.cdp.network.MonotonicTime)*

### *class* DirectTCPSocketChunkSent(identifier, data, timestamp)

**EXPERIMENTAL**

Fired when data is sent to tcp direct socket stream.

#### identifier *: [RequestId](#nodriver.cdp.network.RequestId)*

#### data *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### timestamp *: [MonotonicTime](#nodriver.cdp.network.MonotonicTime)*

### *class* DirectTCPSocketChunkReceived(identifier, data, timestamp)

**EXPERIMENTAL**

Fired when data is received from tcp direct socket stream.

#### identifier *: [RequestId](#nodriver.cdp.network.RequestId)*

#### data *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### timestamp *: [MonotonicTime](#nodriver.cdp.network.MonotonicTime)*

### *class* DirectUDPSocketJoinedMulticastGroup(identifier, ip_address)

**EXPERIMENTAL**

#### identifier *: [RequestId](#nodriver.cdp.network.RequestId)*

#### ip_address *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

### *class* DirectUDPSocketLeftMulticastGroup(identifier, ip_address)

**EXPERIMENTAL**

#### identifier *: [RequestId](#nodriver.cdp.network.RequestId)*

#### ip_address *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

### *class* DirectUDPSocketCreated(identifier, options, timestamp, initiator)

**EXPERIMENTAL**

Fired upon direct_socket.UDPSocket creation.

#### identifier *: [RequestId](#nodriver.cdp.network.RequestId)*

#### options *: [DirectUDPSocketOptions](#nodriver.cdp.network.DirectUDPSocketOptions)*

#### timestamp *: [MonotonicTime](#nodriver.cdp.network.MonotonicTime)*

#### initiator *: [Initiator](#nodriver.cdp.network.Initiator) | [None](https://docs.python.org/3/library/constants.html#None)*

### *class* DirectUDPSocketOpened(identifier, local_addr, local_port, timestamp, remote_addr, remote_port)

**EXPERIMENTAL**

Fired when direct_socket.UDPSocket connection is opened.

#### identifier *: [RequestId](#nodriver.cdp.network.RequestId)*

#### local_addr *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### local_port *: [int](https://docs.python.org/3/library/functions.html#int)*

Expected to be unsigned integer.

#### timestamp *: [MonotonicTime](#nodriver.cdp.network.MonotonicTime)*

#### remote_addr *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)*

#### remote_port *: [int](https://docs.python.org/3/library/functions.html#int) | [None](https://docs.python.org/3/library/constants.html#None)*

Expected to be unsigned integer.

### *class* DirectUDPSocketAborted(identifier, error_message, timestamp)

**EXPERIMENTAL**

Fired when direct_socket.UDPSocket is aborted.

#### identifier *: [RequestId](#nodriver.cdp.network.RequestId)*

#### error_message *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### timestamp *: [MonotonicTime](#nodriver.cdp.network.MonotonicTime)*

### *class* DirectUDPSocketClosed(identifier, timestamp)

**EXPERIMENTAL**

Fired when direct_socket.UDPSocket is closed.

#### identifier *: [RequestId](#nodriver.cdp.network.RequestId)*

#### timestamp *: [MonotonicTime](#nodriver.cdp.network.MonotonicTime)*

### *class* DirectUDPSocketChunkSent(identifier, message, timestamp)

**EXPERIMENTAL**

Fired when message is sent to udp direct socket stream.

#### identifier *: [RequestId](#nodriver.cdp.network.RequestId)*

#### message *: [DirectUDPMessage](#nodriver.cdp.network.DirectUDPMessage)*

#### timestamp *: [MonotonicTime](#nodriver.cdp.network.MonotonicTime)*

### *class* DirectUDPSocketChunkReceived(identifier, message, timestamp)

**EXPERIMENTAL**

Fired when message is received from udp direct socket stream.

#### identifier *: [RequestId](#nodriver.cdp.network.RequestId)*

#### message *: [DirectUDPMessage](#nodriver.cdp.network.DirectUDPMessage)*

#### timestamp *: [MonotonicTime](#nodriver.cdp.network.MonotonicTime)*

### *class* RequestWillBeSentExtraInfo(request_id, associated_cookies, headers, connect_timing, device_bound_session_usages, client_security_state, site_has_cookie_in_other_partition, applied_network_conditions_id)

**EXPERIMENTAL**

Fired when additional information about a requestWillBeSent event is available from the
network stack. Not every requestWillBeSent event will have an additional
requestWillBeSentExtraInfo fired for it, and there is no guarantee whether requestWillBeSent
or requestWillBeSentExtraInfo will be fired first for the same request.

#### request_id *: [RequestId](#nodriver.cdp.network.RequestId)*

Request identifier. Used to match this information to an existing requestWillBeSent event.

#### associated_cookies *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[AssociatedCookie](#nodriver.cdp.network.AssociatedCookie)]*

A list of cookies potentially associated to the requested URL. This includes both cookies sent with
the request and the ones not sent; the latter are distinguished by having blockedReasons field set.

#### headers *: [Headers](#nodriver.cdp.network.Headers)*

Raw request headers as they will be sent over the wire.

#### connect_timing *: [ConnectTiming](#nodriver.cdp.network.ConnectTiming)*

Connection timing information for the request.

#### device_bound_session_usages *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[DeviceBoundSessionWithUsage](#nodriver.cdp.network.DeviceBoundSessionWithUsage)] | [None](https://docs.python.org/3/library/constants.html#None)*

How the request site’s device bound sessions were used during this request.

#### client_security_state *: [ClientSecurityState](#nodriver.cdp.network.ClientSecurityState) | [None](https://docs.python.org/3/library/constants.html#None)*

The client security state set for the request.

#### site_has_cookie_in_other_partition *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)*

Whether the site has partitioned cookies stored in a partition different than the current one.

#### applied_network_conditions_id *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)*

The network conditions id if this request was affected by network conditions configured via
emulateNetworkConditionsByRule.

### *class* ResponseReceivedExtraInfo(request_id, blocked_cookies, headers, resource_ip_address_space, status_code, headers_text, cookie_partition_key, cookie_partition_key_opaque, exempted_cookies)

**EXPERIMENTAL**

Fired when additional information about a responseReceived event is available from the network
stack. Not every responseReceived event will have an additional responseReceivedExtraInfo for
it, and responseReceivedExtraInfo may be fired before or after responseReceived.

#### request_id *: [RequestId](#nodriver.cdp.network.RequestId)*

Request identifier. Used to match this information to another responseReceived event.

#### blocked_cookies *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[BlockedSetCookieWithReason](#nodriver.cdp.network.BlockedSetCookieWithReason)]*

A list of cookies which were not stored from the response along with the corresponding
reasons for blocking. The cookies here may not be valid due to syntax errors, which
are represented by the invalid cookie line string instead of a proper cookie.

#### headers *: [Headers](#nodriver.cdp.network.Headers)*

Raw response headers as they were received over the wire.
Duplicate headers in the response are represented as a single key with their values
concatentated using `\n` as the separator.
See also `headersText` that contains verbatim text for HTTP/1.\*.

#### resource_ip_address_space *: [IPAddressSpace](#nodriver.cdp.network.IPAddressSpace)*

The IP address space of the resource. The address space can only be determined once the transport
established the connection, so we can’t send it in `requestWillBeSentExtraInfo`.

#### status_code *: [int](https://docs.python.org/3/library/functions.html#int)*

The status code of the response. This is useful in cases the request failed and no responseReceived
event is triggered, which is the case for, e.g., CORS errors. This is also the correct status code
for cached requests, where the status in responseReceived is a 200 and this will be 304.

#### headers_text *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)*

Raw response header text as it was received over the wire. The raw text may not always be
available, such as in the case of HTTP/2 or QUIC.

#### cookie_partition_key *: [CookiePartitionKey](#nodriver.cdp.network.CookiePartitionKey) | [None](https://docs.python.org/3/library/constants.html#None)*

The cookie partition key that will be used to store partitioned cookies set in this response.
Only sent when partitioned cookies are enabled.

#### cookie_partition_key_opaque *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)*

True if partitioned cookies are enabled, but the partition key is not serializable to string.

#### exempted_cookies *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[ExemptedSetCookieWithReason](#nodriver.cdp.network.ExemptedSetCookieWithReason)] | [None](https://docs.python.org/3/library/constants.html#None)*

A list of cookies which should have been blocked by 3PCD but are exempted and stored from
the response with the corresponding reason.

### *class* ResponseReceivedEarlyHints(request_id, headers)

**EXPERIMENTAL**

Fired when 103 Early Hints headers is received in addition to the common response.
Not every responseReceived event will have an responseReceivedEarlyHints fired.
Only one responseReceivedEarlyHints may be fired for eached responseReceived event.

#### request_id *: [RequestId](#nodriver.cdp.network.RequestId)*

Request identifier. Used to match this information to another responseReceived event.

#### headers *: [Headers](#nodriver.cdp.network.Headers)*

Raw response headers as they were received over the wire.
Duplicate headers in the response are represented as a single key with their values
concatentated using `\n` as the separator.
See also `headersText` that contains verbatim text for HTTP/1.\*.

### *class* TrustTokenOperationDone(status, type_, request_id, top_level_origin, issuer_origin, issued_token_count)

**EXPERIMENTAL**

Fired exactly once for each Trust Token operation. Depending on
the type of the operation and whether the operation succeeded or
failed, the event is fired before the corresponding request was sent
or after the response was received.

#### status *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Detailed success or error status of the operation.
‘AlreadyExists’ also signifies a successful operation, as the result
of the operation already exists und thus, the operation was abort
preemptively (e.g. a cache hit).

#### type_ *: [TrustTokenOperationType](#nodriver.cdp.network.TrustTokenOperationType)*

#### request_id *: [RequestId](#nodriver.cdp.network.RequestId)*

#### top_level_origin *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)*

Top level origin. The context in which the operation was attempted.

#### issuer_origin *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)*

Origin of the issuer in case of a “Issuance” or “Redemption” operation.

#### issued_token_count *: [int](https://docs.python.org/3/library/functions.html#int) | [None](https://docs.python.org/3/library/constants.html#None)*

The number of obtained Trust Tokens on a successful “Issuance” operation.

### *class* PolicyUpdated

**EXPERIMENTAL**

Fired once security policy has been updated.

### *class* ReportingApiReportAdded(report)

**EXPERIMENTAL**

Is sent whenever a new report is added.
And after ‘enableReportingApi’ for all existing reports.

#### report *: [ReportingApiReport](#nodriver.cdp.network.ReportingApiReport)*

### *class* ReportingApiReportUpdated(report)

**EXPERIMENTAL**

#### report *: [ReportingApiReport](#nodriver.cdp.network.ReportingApiReport)*

### *class* ReportingApiEndpointsChangedForOrigin(origin, endpoints)

**EXPERIMENTAL**

#### origin *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Origin of the document(s) which configured the endpoints.

#### endpoints *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[ReportingApiEndpoint](#nodriver.cdp.network.ReportingApiEndpoint)]*

### *class* DeviceBoundSessionsAdded(sessions)

**EXPERIMENTAL**

Triggered when the initial set of device bound sessions is added.

#### sessions *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[DeviceBoundSession](#nodriver.cdp.network.DeviceBoundSession)]*

The device bound sessions.

### *class* DeviceBoundSessionEventOccurred(event_id, site, succeeded, session_id, creation_event_details, refresh_event_details, termination_event_details, challenge_event_details)

**EXPERIMENTAL**

Triggered when a device bound session event occurs.

#### event_id *: [DeviceBoundSessionEventId](#nodriver.cdp.network.DeviceBoundSessionEventId)*

A unique identifier for this session event.

#### site *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

The site this session event is associated with.

#### succeeded *: [bool](https://docs.python.org/3/library/functions.html#bool)*

Whether this event was considered successful.

#### session_id *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)*

The session ID this event is associated with. May not be populated for
failed events.

#### creation_event_details *: [CreationEventDetails](#nodriver.cdp.network.CreationEventDetails) | [None](https://docs.python.org/3/library/constants.html#None)*

The below are the different session event type details. Exactly one is populated.

#### refresh_event_details *: [RefreshEventDetails](#nodriver.cdp.network.RefreshEventDetails) | [None](https://docs.python.org/3/library/constants.html#None)*

#### termination_event_details *: [TerminationEventDetails](#nodriver.cdp.network.TerminationEventDetails) | [None](https://docs.python.org/3/library/constants.html#None)*

#### challenge_event_details *: [ChallengeEventDetails](#nodriver.cdp.network.ChallengeEventDetails) | [None](https://docs.python.org/3/library/constants.html#None)*
