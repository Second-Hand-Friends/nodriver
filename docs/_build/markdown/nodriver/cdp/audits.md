# Audits

Audits domain allows investigation of page violations and possible improvements.

*This CDP domain is experimental.*

<a id="module-nodriver.cdp.audits"></a>
* [Types]()
* [Commands]()
* [Events]()

## Types

Generally, you do not need to instantiate CDP types
yourself. Instead, the API creates objects for you as return
values from commands, and then you can use those objects as
arguments to other commands.

### *class* AffectedCookie(name, path, domain)

Information about a cookie that is affected by an inspector issue.

#### name *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

The following three properties uniquely identify a cookie

#### path *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### domain *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

### *class* AffectedRequest(url, request_id=None)

Information about a request that is affected by an inspector issue.

#### url *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### request_id *: [RequestId](network.md#nodriver.cdp.network.RequestId) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The unique request id.

### *class* AffectedFrame(frame_id)

Information about the frame affected by an inspector issue.

#### frame_id *: [FrameId](page.md#nodriver.cdp.page.FrameId)*

### *class* CookieExclusionReason(\*values)

#### EXCLUDE_SAME_SITE_UNSPECIFIED_TREATED_AS_LAX *= 'ExcludeSameSiteUnspecifiedTreatedAsLax'*

#### EXCLUDE_SAME_SITE_NONE_INSECURE *= 'ExcludeSameSiteNoneInsecure'*

#### EXCLUDE_SAME_SITE_LAX *= 'ExcludeSameSiteLax'*

#### EXCLUDE_SAME_SITE_STRICT *= 'ExcludeSameSiteStrict'*

#### EXCLUDE_DOMAIN_NON_ASCII *= 'ExcludeDomainNonASCII'*

#### EXCLUDE_THIRD_PARTY_COOKIE_BLOCKED_IN_FIRST_PARTY_SET *= 'ExcludeThirdPartyCookieBlockedInFirstPartySet'*

#### EXCLUDE_THIRD_PARTY_PHASEOUT *= 'ExcludeThirdPartyPhaseout'*

#### EXCLUDE_PORT_MISMATCH *= 'ExcludePortMismatch'*

#### EXCLUDE_SCHEME_MISMATCH *= 'ExcludeSchemeMismatch'*

### *class* CookieWarningReason(\*values)

#### WARN_SAME_SITE_UNSPECIFIED_CROSS_SITE_CONTEXT *= 'WarnSameSiteUnspecifiedCrossSiteContext'*

#### WARN_SAME_SITE_NONE_INSECURE *= 'WarnSameSiteNoneInsecure'*

#### WARN_SAME_SITE_UNSPECIFIED_LAX_ALLOW_UNSAFE *= 'WarnSameSiteUnspecifiedLaxAllowUnsafe'*

#### WARN_SAME_SITE_STRICT_LAX_DOWNGRADE_STRICT *= 'WarnSameSiteStrictLaxDowngradeStrict'*

#### WARN_SAME_SITE_STRICT_CROSS_DOWNGRADE_STRICT *= 'WarnSameSiteStrictCrossDowngradeStrict'*

#### WARN_SAME_SITE_STRICT_CROSS_DOWNGRADE_LAX *= 'WarnSameSiteStrictCrossDowngradeLax'*

#### WARN_SAME_SITE_LAX_CROSS_DOWNGRADE_STRICT *= 'WarnSameSiteLaxCrossDowngradeStrict'*

#### WARN_SAME_SITE_LAX_CROSS_DOWNGRADE_LAX *= 'WarnSameSiteLaxCrossDowngradeLax'*

#### WARN_ATTRIBUTE_VALUE_EXCEEDS_MAX_SIZE *= 'WarnAttributeValueExceedsMaxSize'*

#### WARN_DOMAIN_NON_ASCII *= 'WarnDomainNonASCII'*

#### WARN_THIRD_PARTY_PHASEOUT *= 'WarnThirdPartyPhaseout'*

#### WARN_CROSS_SITE_REDIRECT_DOWNGRADE_CHANGES_INCLUSION *= 'WarnCrossSiteRedirectDowngradeChangesInclusion'*

#### WARN_DEPRECATION_TRIAL_METADATA *= 'WarnDeprecationTrialMetadata'*

#### WARN_THIRD_PARTY_COOKIE_HEURISTIC *= 'WarnThirdPartyCookieHeuristic'*

### *class* CookieOperation(\*values)

#### SET_COOKIE *= 'SetCookie'*

#### READ_COOKIE *= 'ReadCookie'*

### *class* InsightType(\*values)

Represents the category of insight that a cookie issue falls under.

#### GIT_HUB_RESOURCE *= 'GitHubResource'*

#### GRACE_PERIOD *= 'GracePeriod'*

#### HEURISTICS *= 'Heuristics'*

### *class* CookieIssueInsight(type_, table_entry_url=None)

Information about the suggested solution to a cookie issue.

#### type_ *: [InsightType](#nodriver.cdp.audits.InsightType)*

#### table_entry_url *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Link to table entry in third-party cookie migration readiness list.

### *class* CookieIssueDetails(cookie_warning_reasons, cookie_exclusion_reasons, operation, cookie=None, raw_cookie_line=None, site_for_cookies=None, cookie_url=None, request=None, insight=None)

This information is currently necessary, as the front-end has a difficult
time finding a specific cookie. With this, we can convey specific error
information without the cookie.

#### cookie_warning_reasons *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[CookieWarningReason](#nodriver.cdp.audits.CookieWarningReason)]*

#### cookie_exclusion_reasons *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[CookieExclusionReason](#nodriver.cdp.audits.CookieExclusionReason)]*

#### operation *: [CookieOperation](#nodriver.cdp.audits.CookieOperation)*

Optionally identifies the site-for-cookies and the cookie url, which
may be used by the front-end as additional context.

#### cookie *: [AffectedCookie](#nodriver.cdp.audits.AffectedCookie) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

If AffectedCookie is not set then rawCookieLine contains the raw
Set-Cookie header string. This hints at a problem where the
cookie line is syntactically or semantically malformed in a way
that no valid cookie could be created.

#### raw_cookie_line *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### site_for_cookies *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### cookie_url *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### request *: [AffectedRequest](#nodriver.cdp.audits.AffectedRequest) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### insight *: [CookieIssueInsight](#nodriver.cdp.audits.CookieIssueInsight) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The recommended solution to the issue.

### *class* PerformanceIssueType(\*values)

#### DOCUMENT_COOKIE *= 'DocumentCookie'*

### *class* PerformanceIssueDetails(performance_issue_type, source_code_location=None)

Details for a performance issue.

#### performance_issue_type *: [PerformanceIssueType](#nodriver.cdp.audits.PerformanceIssueType)*

#### source_code_location *: [SourceCodeLocation](#nodriver.cdp.audits.SourceCodeLocation) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

### *class* MixedContentResolutionStatus(\*values)

#### MIXED_CONTENT_BLOCKED *= 'MixedContentBlocked'*

#### MIXED_CONTENT_AUTOMATICALLY_UPGRADED *= 'MixedContentAutomaticallyUpgraded'*

#### MIXED_CONTENT_WARNING *= 'MixedContentWarning'*

### *class* MixedContentResourceType(\*values)

#### ATTRIBUTION_SRC *= 'AttributionSrc'*

#### AUDIO *= 'Audio'*

#### BEACON *= 'Beacon'*

#### CSP_REPORT *= 'CSPReport'*

#### DOWNLOAD *= 'Download'*

#### EVENT_SOURCE *= 'EventSource'*

#### FAVICON *= 'Favicon'*

#### FONT *= 'Font'*

#### FORM *= 'Form'*

#### FRAME *= 'Frame'*

#### IMAGE *= 'Image'*

#### IMPORT *= 'Import'*

#### JSON *= 'JSON'*

#### MANIFEST *= 'Manifest'*

#### PING *= 'Ping'*

#### PLUGIN_DATA *= 'PluginData'*

#### PLUGIN_RESOURCE *= 'PluginResource'*

#### PREFETCH *= 'Prefetch'*

#### RESOURCE *= 'Resource'*

#### SCRIPT *= 'Script'*

#### SERVICE_WORKER *= 'ServiceWorker'*

#### SHARED_WORKER *= 'SharedWorker'*

#### SPECULATION_RULES *= 'SpeculationRules'*

#### STYLESHEET *= 'Stylesheet'*

#### TRACK *= 'Track'*

#### VIDEO *= 'Video'*

#### WORKER *= 'Worker'*

#### XML_HTTP_REQUEST *= 'XMLHttpRequest'*

#### XSLT *= 'XSLT'*

### *class* MixedContentIssueDetails(resolution_status, insecure_url, main_resource_url, resource_type=None, request=None, frame=None)

#### resolution_status *: [MixedContentResolutionStatus](#nodriver.cdp.audits.MixedContentResolutionStatus)*

The way the mixed content issue is being resolved.

#### insecure_url *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

The unsafe http url causing the mixed content issue.

#### main_resource_url *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

The url responsible for the call to an unsafe url.

#### resource_type *: [MixedContentResourceType](#nodriver.cdp.audits.MixedContentResourceType) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The type of resource causing the mixed content issue (css, js, iframe,
form,…). Marked as optional because it is mapped to from
blink::mojom::RequestContextType, which will be replaced
by network::mojom::RequestDestination

#### request *: [AffectedRequest](#nodriver.cdp.audits.AffectedRequest) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The mixed content request.
Does not always exist (e.g. for unsafe form submission urls).

#### frame *: [AffectedFrame](#nodriver.cdp.audits.AffectedFrame) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Optional because not every mixed content issue is necessarily linked to a frame.

### *class* BlockedByResponseReason(\*values)

Enum indicating the reason a response has been blocked. These reasons are
refinements of the net error BLOCKED_BY_RESPONSE.

#### COEP_FRAME_RESOURCE_NEEDS_COEP_HEADER *= 'CoepFrameResourceNeedsCoepHeader'*

#### COOP_SANDBOXED_I_FRAME_CANNOT_NAVIGATE_TO_COOP_PAGE *= 'CoopSandboxedIFrameCannotNavigateToCoopPage'*

#### CORP_NOT_SAME_ORIGIN *= 'CorpNotSameOrigin'*

#### CORP_NOT_SAME_ORIGIN_AFTER_DEFAULTED_TO_SAME_ORIGIN_BY_COEP *= 'CorpNotSameOriginAfterDefaultedToSameOriginByCoep'*

#### CORP_NOT_SAME_ORIGIN_AFTER_DEFAULTED_TO_SAME_ORIGIN_BY_DIP *= 'CorpNotSameOriginAfterDefaultedToSameOriginByDip'*

#### CORP_NOT_SAME_ORIGIN_AFTER_DEFAULTED_TO_SAME_ORIGIN_BY_COEP_AND_DIP *= 'CorpNotSameOriginAfterDefaultedToSameOriginByCoepAndDip'*

#### CORP_NOT_SAME_SITE *= 'CorpNotSameSite'*

#### SRI_MESSAGE_SIGNATURE_MISMATCH *= 'SRIMessageSignatureMismatch'*

### *class* BlockedByResponseIssueDetails(request, reason, parent_frame=None, blocked_frame=None)

Details for a request that has been blocked with the BLOCKED_BY_RESPONSE
code. Currently only used for COEP/COOP, but may be extended to include
some CSP errors in the future.

#### request *: [AffectedRequest](#nodriver.cdp.audits.AffectedRequest)*

#### reason *: [BlockedByResponseReason](#nodriver.cdp.audits.BlockedByResponseReason)*

#### parent_frame *: [AffectedFrame](#nodriver.cdp.audits.AffectedFrame) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### blocked_frame *: [AffectedFrame](#nodriver.cdp.audits.AffectedFrame) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

### *class* HeavyAdResolutionStatus(\*values)

#### HEAVY_AD_BLOCKED *= 'HeavyAdBlocked'*

#### HEAVY_AD_WARNING *= 'HeavyAdWarning'*

### *class* HeavyAdReason(\*values)

#### NETWORK_TOTAL_LIMIT *= 'NetworkTotalLimit'*

#### CPU_TOTAL_LIMIT *= 'CpuTotalLimit'*

#### CPU_PEAK_LIMIT *= 'CpuPeakLimit'*

### *class* HeavyAdIssueDetails(resolution, reason, frame)

#### resolution *: [HeavyAdResolutionStatus](#nodriver.cdp.audits.HeavyAdResolutionStatus)*

The resolution status, either blocking the content or warning.

#### reason *: [HeavyAdReason](#nodriver.cdp.audits.HeavyAdReason)*

The reason the ad was blocked, total network or cpu or peak cpu.

#### frame *: [AffectedFrame](#nodriver.cdp.audits.AffectedFrame)*

The frame that was blocked.

### *class* ContentSecurityPolicyViolationType(\*values)

#### K_INLINE_VIOLATION *= 'kInlineViolation'*

#### K_EVAL_VIOLATION *= 'kEvalViolation'*

#### K_URL_VIOLATION *= 'kURLViolation'*

#### K_SRI_VIOLATION *= 'kSRIViolation'*

#### K_TRUSTED_TYPES_SINK_VIOLATION *= 'kTrustedTypesSinkViolation'*

#### K_TRUSTED_TYPES_POLICY_VIOLATION *= 'kTrustedTypesPolicyViolation'*

#### K_WASM_EVAL_VIOLATION *= 'kWasmEvalViolation'*

### *class* SourceCodeLocation(url, line_number, column_number, script_id=None)

#### url *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### line_number *: [int](https://docs.python.org/3/library/functions.html#int)*

#### column_number *: [int](https://docs.python.org/3/library/functions.html#int)*

#### script_id *: [ScriptId](runtime.md#nodriver.cdp.runtime.ScriptId) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

### *class* ContentSecurityPolicyIssueDetails(violated_directive, is_report_only, content_security_policy_violation_type, blocked_url=None, frame_ancestor=None, source_code_location=None, violating_node_id=None)

#### violated_directive *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Specific directive that is violated, causing the CSP issue.

#### is_report_only *: [bool](https://docs.python.org/3/library/functions.html#bool)*

#### content_security_policy_violation_type *: [ContentSecurityPolicyViolationType](#nodriver.cdp.audits.ContentSecurityPolicyViolationType)*

#### blocked_url *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The url not included in allowed sources.

#### frame_ancestor *: [AffectedFrame](#nodriver.cdp.audits.AffectedFrame) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### source_code_location *: [SourceCodeLocation](#nodriver.cdp.audits.SourceCodeLocation) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### violating_node_id *: [BackendNodeId](dom.md#nodriver.cdp.dom.BackendNodeId) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

### *class* SharedArrayBufferIssueType(\*values)

#### TRANSFER_ISSUE *= 'TransferIssue'*

#### CREATION_ISSUE *= 'CreationIssue'*

### *class* SharedArrayBufferIssueDetails(source_code_location, is_warning, type_)

Details for a issue arising from an SAB being instantiated in, or
transferred to a context that is not cross-origin isolated.

#### source_code_location *: [SourceCodeLocation](#nodriver.cdp.audits.SourceCodeLocation)*

#### is_warning *: [bool](https://docs.python.org/3/library/functions.html#bool)*

#### type_ *: [SharedArrayBufferIssueType](#nodriver.cdp.audits.SharedArrayBufferIssueType)*

### *class* CorsIssueDetails(cors_error_status, is_warning, request, location=None, initiator_origin=None, resource_ip_address_space=None, client_security_state=None)

Details for a CORS related issue, e.g. a warning or error related to
CORS RFC1918 enforcement.

#### cors_error_status *: [CorsErrorStatus](network.md#nodriver.cdp.network.CorsErrorStatus)*

#### is_warning *: [bool](https://docs.python.org/3/library/functions.html#bool)*

#### request *: [AffectedRequest](#nodriver.cdp.audits.AffectedRequest)*

#### location *: [SourceCodeLocation](#nodriver.cdp.audits.SourceCodeLocation) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### initiator_origin *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### resource_ip_address_space *: [IPAddressSpace](network.md#nodriver.cdp.network.IPAddressSpace) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### client_security_state *: [ClientSecurityState](network.md#nodriver.cdp.network.ClientSecurityState) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

### *class* AttributionReportingIssueType(\*values)

#### PERMISSION_POLICY_DISABLED *= 'PermissionPolicyDisabled'*

#### UNTRUSTWORTHY_REPORTING_ORIGIN *= 'UntrustworthyReportingOrigin'*

#### INSECURE_CONTEXT *= 'InsecureContext'*

#### INVALID_HEADER *= 'InvalidHeader'*

#### INVALID_REGISTER_TRIGGER_HEADER *= 'InvalidRegisterTriggerHeader'*

#### SOURCE_AND_TRIGGER_HEADERS *= 'SourceAndTriggerHeaders'*

#### SOURCE_IGNORED *= 'SourceIgnored'*

#### TRIGGER_IGNORED *= 'TriggerIgnored'*

#### OS_SOURCE_IGNORED *= 'OsSourceIgnored'*

#### OS_TRIGGER_IGNORED *= 'OsTriggerIgnored'*

#### INVALID_REGISTER_OS_SOURCE_HEADER *= 'InvalidRegisterOsSourceHeader'*

#### INVALID_REGISTER_OS_TRIGGER_HEADER *= 'InvalidRegisterOsTriggerHeader'*

#### WEB_AND_OS_HEADERS *= 'WebAndOsHeaders'*

#### NO_WEB_OR_OS_SUPPORT *= 'NoWebOrOsSupport'*

#### NAVIGATION_REGISTRATION_WITHOUT_TRANSIENT_USER_ACTIVATION *= 'NavigationRegistrationWithoutTransientUserActivation'*

#### INVALID_INFO_HEADER *= 'InvalidInfoHeader'*

#### NO_REGISTER_SOURCE_HEADER *= 'NoRegisterSourceHeader'*

#### NO_REGISTER_TRIGGER_HEADER *= 'NoRegisterTriggerHeader'*

#### NO_REGISTER_OS_SOURCE_HEADER *= 'NoRegisterOsSourceHeader'*

#### NO_REGISTER_OS_TRIGGER_HEADER *= 'NoRegisterOsTriggerHeader'*

#### NAVIGATION_REGISTRATION_UNIQUE_SCOPE_ALREADY_SET *= 'NavigationRegistrationUniqueScopeAlreadySet'*

### *class* SharedDictionaryError(\*values)

#### USE_ERROR_CROSS_ORIGIN_NO_CORS_REQUEST *= 'UseErrorCrossOriginNoCorsRequest'*

#### USE_ERROR_DICTIONARY_LOAD_FAILURE *= 'UseErrorDictionaryLoadFailure'*

#### USE_ERROR_MATCHING_DICTIONARY_NOT_USED *= 'UseErrorMatchingDictionaryNotUsed'*

#### USE_ERROR_UNEXPECTED_CONTENT_DICTIONARY_HEADER *= 'UseErrorUnexpectedContentDictionaryHeader'*

#### WRITE_ERROR_COSS_ORIGIN_NO_CORS_REQUEST *= 'WriteErrorCossOriginNoCorsRequest'*

#### WRITE_ERROR_DISALLOWED_BY_SETTINGS *= 'WriteErrorDisallowedBySettings'*

#### WRITE_ERROR_EXPIRED_RESPONSE *= 'WriteErrorExpiredResponse'*

#### WRITE_ERROR_FEATURE_DISABLED *= 'WriteErrorFeatureDisabled'*

#### WRITE_ERROR_INSUFFICIENT_RESOURCES *= 'WriteErrorInsufficientResources'*

#### WRITE_ERROR_INVALID_MATCH_FIELD *= 'WriteErrorInvalidMatchField'*

#### WRITE_ERROR_INVALID_STRUCTURED_HEADER *= 'WriteErrorInvalidStructuredHeader'*

#### WRITE_ERROR_INVALID_TTL_FIELD *= 'WriteErrorInvalidTTLField'*

#### WRITE_ERROR_NAVIGATION_REQUEST *= 'WriteErrorNavigationRequest'*

#### WRITE_ERROR_NO_MATCH_FIELD *= 'WriteErrorNoMatchField'*

#### WRITE_ERROR_NON_INTEGER_TTL_FIELD *= 'WriteErrorNonIntegerTTLField'*

#### WRITE_ERROR_NON_LIST_MATCH_DEST_FIELD *= 'WriteErrorNonListMatchDestField'*

#### WRITE_ERROR_NON_SECURE_CONTEXT *= 'WriteErrorNonSecureContext'*

#### WRITE_ERROR_NON_STRING_ID_FIELD *= 'WriteErrorNonStringIdField'*

#### WRITE_ERROR_NON_STRING_IN_MATCH_DEST_LIST *= 'WriteErrorNonStringInMatchDestList'*

#### WRITE_ERROR_NON_STRING_MATCH_FIELD *= 'WriteErrorNonStringMatchField'*

#### WRITE_ERROR_NON_TOKEN_TYPE_FIELD *= 'WriteErrorNonTokenTypeField'*

#### WRITE_ERROR_REQUEST_ABORTED *= 'WriteErrorRequestAborted'*

#### WRITE_ERROR_SHUTTING_DOWN *= 'WriteErrorShuttingDown'*

#### WRITE_ERROR_TOO_LONG_ID_FIELD *= 'WriteErrorTooLongIdField'*

#### WRITE_ERROR_UNSUPPORTED_TYPE *= 'WriteErrorUnsupportedType'*

### *class* SRIMessageSignatureError(\*values)

#### MISSING_SIGNATURE_HEADER *= 'MissingSignatureHeader'*

#### MISSING_SIGNATURE_INPUT_HEADER *= 'MissingSignatureInputHeader'*

#### INVALID_SIGNATURE_HEADER *= 'InvalidSignatureHeader'*

#### INVALID_SIGNATURE_INPUT_HEADER *= 'InvalidSignatureInputHeader'*

#### SIGNATURE_HEADER_VALUE_IS_NOT_BYTE_SEQUENCE *= 'SignatureHeaderValueIsNotByteSequence'*

#### SIGNATURE_HEADER_VALUE_IS_PARAMETERIZED *= 'SignatureHeaderValueIsParameterized'*

#### SIGNATURE_HEADER_VALUE_IS_INCORRECT_LENGTH *= 'SignatureHeaderValueIsIncorrectLength'*

#### SIGNATURE_INPUT_HEADER_MISSING_LABEL *= 'SignatureInputHeaderMissingLabel'*

#### SIGNATURE_INPUT_HEADER_VALUE_NOT_INNER_LIST *= 'SignatureInputHeaderValueNotInnerList'*

#### SIGNATURE_INPUT_HEADER_VALUE_MISSING_COMPONENTS *= 'SignatureInputHeaderValueMissingComponents'*

#### SIGNATURE_INPUT_HEADER_INVALID_COMPONENT_TYPE *= 'SignatureInputHeaderInvalidComponentType'*

#### SIGNATURE_INPUT_HEADER_INVALID_COMPONENT_NAME *= 'SignatureInputHeaderInvalidComponentName'*

#### SIGNATURE_INPUT_HEADER_INVALID_HEADER_COMPONENT_PARAMETER *= 'SignatureInputHeaderInvalidHeaderComponentParameter'*

#### SIGNATURE_INPUT_HEADER_INVALID_DERIVED_COMPONENT_PARAMETER *= 'SignatureInputHeaderInvalidDerivedComponentParameter'*

#### SIGNATURE_INPUT_HEADER_KEY_ID_LENGTH *= 'SignatureInputHeaderKeyIdLength'*

#### SIGNATURE_INPUT_HEADER_INVALID_PARAMETER *= 'SignatureInputHeaderInvalidParameter'*

#### SIGNATURE_INPUT_HEADER_MISSING_REQUIRED_PARAMETERS *= 'SignatureInputHeaderMissingRequiredParameters'*

#### VALIDATION_FAILED_SIGNATURE_EXPIRED *= 'ValidationFailedSignatureExpired'*

#### VALIDATION_FAILED_INVALID_LENGTH *= 'ValidationFailedInvalidLength'*

#### VALIDATION_FAILED_SIGNATURE_MISMATCH *= 'ValidationFailedSignatureMismatch'*

#### VALIDATION_FAILED_INTEGRITY_MISMATCH *= 'ValidationFailedIntegrityMismatch'*

### *class* UnencodedDigestError(\*values)

#### MALFORMED_DICTIONARY *= 'MalformedDictionary'*

#### UNKNOWN_ALGORITHM *= 'UnknownAlgorithm'*

#### INCORRECT_DIGEST_TYPE *= 'IncorrectDigestType'*

#### INCORRECT_DIGEST_LENGTH *= 'IncorrectDigestLength'*

### *class* ConnectionAllowlistError(\*values)

#### INVALID_HEADER *= 'InvalidHeader'*

#### MORE_THAN_ONE_LIST *= 'MoreThanOneList'*

#### ITEM_NOT_INNER_LIST *= 'ItemNotInnerList'*

#### INVALID_ALLOWLIST_ITEM_TYPE *= 'InvalidAllowlistItemType'*

#### REPORTING_ENDPOINT_NOT_TOKEN *= 'ReportingEndpointNotToken'*

#### INVALID_URL_PATTERN *= 'InvalidUrlPattern'*

### *class* AttributionReportingIssueDetails(violation_type, request=None, violating_node_id=None, invalid_parameter=None)

Details for issues around “Attribution Reporting API” usage.
Explainer: [https://github.com/WICG/attribution-reporting-api](https://github.com/WICG/attribution-reporting-api)

#### violation_type *: [AttributionReportingIssueType](#nodriver.cdp.audits.AttributionReportingIssueType)*

#### request *: [AffectedRequest](#nodriver.cdp.audits.AffectedRequest) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### violating_node_id *: [BackendNodeId](dom.md#nodriver.cdp.dom.BackendNodeId) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### invalid_parameter *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

### *class* QuirksModeIssueDetails(is_limited_quirks_mode, document_node_id, url, frame_id, loader_id)

Details for issues about documents in Quirks Mode
or Limited Quirks Mode that affects page layouting.

#### is_limited_quirks_mode *: [bool](https://docs.python.org/3/library/functions.html#bool)*

If false, it means the document’s mode is “quirks”
instead of “limited-quirks”.

#### document_node_id *: [BackendNodeId](dom.md#nodriver.cdp.dom.BackendNodeId)*

#### url *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### frame_id *: [FrameId](page.md#nodriver.cdp.page.FrameId)*

#### loader_id *: [LoaderId](network.md#nodriver.cdp.network.LoaderId)*

### *class* NavigatorUserAgentIssueDetails(url, location=None)

#### url *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### location *: [SourceCodeLocation](#nodriver.cdp.audits.SourceCodeLocation) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

### *class* SharedDictionaryIssueDetails(shared_dictionary_error, request)

#### shared_dictionary_error *: [SharedDictionaryError](#nodriver.cdp.audits.SharedDictionaryError)*

#### request *: [AffectedRequest](#nodriver.cdp.audits.AffectedRequest)*

### *class* SRIMessageSignatureIssueDetails(error, signature_base, integrity_assertions, request)

#### error *: [SRIMessageSignatureError](#nodriver.cdp.audits.SRIMessageSignatureError)*

#### signature_base *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

#### integrity_assertions *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[str](https://docs.python.org/3/library/stdtypes.html#str)]*

#### request *: [AffectedRequest](#nodriver.cdp.audits.AffectedRequest)*

### *class* UnencodedDigestIssueDetails(error, request)

#### error *: [UnencodedDigestError](#nodriver.cdp.audits.UnencodedDigestError)*

#### request *: [AffectedRequest](#nodriver.cdp.audits.AffectedRequest)*

### *class* ConnectionAllowlistIssueDetails(error, request)

#### error *: [ConnectionAllowlistError](#nodriver.cdp.audits.ConnectionAllowlistError)*

#### request *: [AffectedRequest](#nodriver.cdp.audits.AffectedRequest)*

### *class* GenericIssueErrorType(\*values)

#### FORM_LABEL_FOR_NAME_ERROR *= 'FormLabelForNameError'*

#### FORM_DUPLICATE_ID_FOR_INPUT_ERROR *= 'FormDuplicateIdForInputError'*

#### FORM_INPUT_WITH_NO_LABEL_ERROR *= 'FormInputWithNoLabelError'*

#### FORM_AUTOCOMPLETE_ATTRIBUTE_EMPTY_ERROR *= 'FormAutocompleteAttributeEmptyError'*

#### FORM_EMPTY_ID_AND_NAME_ATTRIBUTES_FOR_INPUT_ERROR *= 'FormEmptyIdAndNameAttributesForInputError'*

#### FORM_ARIA_LABELLED_BY_TO_NON_EXISTING_ID_ERROR *= 'FormAriaLabelledByToNonExistingIdError'*

#### FORM_INPUT_ASSIGNED_AUTOCOMPLETE_VALUE_TO_ID_OR_NAME_ATTRIBUTE_ERROR *= 'FormInputAssignedAutocompleteValueToIdOrNameAttributeError'*

#### FORM_LABEL_HAS_NEITHER_FOR_NOR_NESTED_INPUT_ERROR *= 'FormLabelHasNeitherForNorNestedInputError'*

#### FORM_LABEL_FOR_MATCHES_NON_EXISTING_ID_ERROR *= 'FormLabelForMatchesNonExistingIdError'*

#### FORM_INPUT_HAS_WRONG_BUT_WELL_INTENDED_AUTOCOMPLETE_VALUE_ERROR *= 'FormInputHasWrongButWellIntendedAutocompleteValueError'*

#### RESPONSE_WAS_BLOCKED_BY_ORB *= 'ResponseWasBlockedByORB'*

#### NAVIGATION_ENTRY_MARKED_SKIPPABLE *= 'NavigationEntryMarkedSkippable'*

#### BACK_UI_NAVIGATION_WOULD_SKIP_AD *= 'BackUINavigationWouldSkipAd'*

#### AUTOFILL_AND_MANUAL_TEXT_POLICY_CONTROLLED_FEATURES_INFO *= 'AutofillAndManualTextPolicyControlledFeaturesInfo'*

#### AUTOFILL_POLICY_CONTROLLED_FEATURE_INFO *= 'AutofillPolicyControlledFeatureInfo'*

#### MANUAL_TEXT_POLICY_CONTROLLED_FEATURE_INFO *= 'ManualTextPolicyControlledFeatureInfo'*

#### FORM_MODEL_CONTEXT_PARAMETER_MISSING_TITLE_AND_DESCRIPTION *= 'FormModelContextParameterMissingTitleAndDescription'*

#### FORM_MODEL_CONTEXT_MISSING_TOOL_NAME *= 'FormModelContextMissingToolName'*

#### FORM_MODEL_CONTEXT_MISSING_TOOL_DESCRIPTION *= 'FormModelContextMissingToolDescription'*

#### FORM_MODEL_CONTEXT_REQUIRED_PARAMETER_MISSING_NAME *= 'FormModelContextRequiredParameterMissingName'*

#### FORM_MODEL_CONTEXT_PARAMETER_MISSING_NAME *= 'FormModelContextParameterMissingName'*

### *class* GenericIssueDetails(error_type, frame_id=None, violating_node_id=None, violating_node_attribute=None, request=None)

Depending on the concrete errorType, different properties are set.

#### error_type *: [GenericIssueErrorType](#nodriver.cdp.audits.GenericIssueErrorType)*

Issues with the same errorType are aggregated in the frontend.

#### frame_id *: [FrameId](page.md#nodriver.cdp.page.FrameId) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### violating_node_id *: [BackendNodeId](dom.md#nodriver.cdp.dom.BackendNodeId) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### violating_node_attribute *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### request *: [AffectedRequest](#nodriver.cdp.audits.AffectedRequest) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

### *class* DeprecationIssueDetails(source_code_location, type_, affected_frame=None)

This issue tracks information needed to print a deprecation message.
[https://source.chromium.org/chromium/chromium/src/+/main:third_party/blink/renderer/core/frame/third_party/blink/renderer/core/frame/deprecation/README.md](https://source.chromium.org/chromium/chromium/src/+/main:third_party/blink/renderer/core/frame/third_party/blink/renderer/core/frame/deprecation/README.md)

#### source_code_location *: [SourceCodeLocation](#nodriver.cdp.audits.SourceCodeLocation)*

#### type_ *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

One of the deprecation names from third_party/blink/renderer/core/frame/deprecation/deprecation.json5

#### affected_frame *: [AffectedFrame](#nodriver.cdp.audits.AffectedFrame) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

### *class* BounceTrackingIssueDetails(tracking_sites)

This issue warns about sites in the redirect chain of a finished navigation
that may be flagged as trackers and have their state cleared if they don’t
receive a user interaction. Note that in this context ‘site’ means eTLD+1.
For example, if the URL `https://example.test:80/bounce` was in the
redirect chain, the site reported would be `example.test`.

#### tracking_sites *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[str](https://docs.python.org/3/library/stdtypes.html#str)]*

### *class* CookieDeprecationMetadataIssueDetails(allowed_sites, opt_out_percentage, is_opt_out_top_level, operation)

This issue warns about third-party sites that are accessing cookies on the
current page, and have been permitted due to having a global metadata grant.
Note that in this context ‘site’ means eTLD+1. For example, if the URL
`https://example.test:80/web_page` was accessing cookies, the site reported
would be `example.test`.

#### allowed_sites *: [List](https://docs.python.org/3/library/typing.html#typing.List)[[str](https://docs.python.org/3/library/stdtypes.html#str)]*

#### opt_out_percentage *: [float](https://docs.python.org/3/library/functions.html#float)*

#### is_opt_out_top_level *: [bool](https://docs.python.org/3/library/functions.html#bool)*

#### operation *: [CookieOperation](#nodriver.cdp.audits.CookieOperation)*

### *class* ClientHintIssueReason(\*values)

#### META_TAG_ALLOW_LIST_INVALID_ORIGIN *= 'MetaTagAllowListInvalidOrigin'*

#### META_TAG_MODIFIED_HTML *= 'MetaTagModifiedHTML'*

### *class* FederatedAuthRequestIssueDetails(federated_auth_request_issue_reason)

#### federated_auth_request_issue_reason *: [FederatedAuthRequestIssueReason](#nodriver.cdp.audits.FederatedAuthRequestIssueReason)*

### *class* FederatedAuthRequestIssueReason(\*values)

Represents the failure reason when a federated authentication reason fails.
Should be updated alongside RequestIdTokenStatus in
third_party/blink/public/mojom/devtools/inspector_issue.mojom to include
all cases except for success.

#### SHOULD_EMBARGO *= 'ShouldEmbargo'*

#### TOO_MANY_REQUESTS *= 'TooManyRequests'*

#### WELL_KNOWN_HTTP_NOT_FOUND *= 'WellKnownHttpNotFound'*

#### WELL_KNOWN_NO_RESPONSE *= 'WellKnownNoResponse'*

#### WELL_KNOWN_INVALID_RESPONSE *= 'WellKnownInvalidResponse'*

#### WELL_KNOWN_LIST_EMPTY *= 'WellKnownListEmpty'*

#### WELL_KNOWN_INVALID_CONTENT_TYPE *= 'WellKnownInvalidContentType'*

#### CONFIG_NOT_IN_WELL_KNOWN *= 'ConfigNotInWellKnown'*

#### WELL_KNOWN_TOO_BIG *= 'WellKnownTooBig'*

#### CONFIG_HTTP_NOT_FOUND *= 'ConfigHttpNotFound'*

#### CONFIG_NO_RESPONSE *= 'ConfigNoResponse'*

#### CONFIG_INVALID_RESPONSE *= 'ConfigInvalidResponse'*

#### CONFIG_INVALID_CONTENT_TYPE *= 'ConfigInvalidContentType'*

#### IDP_NOT_POTENTIALLY_TRUSTWORTHY *= 'IdpNotPotentiallyTrustworthy'*

#### DISABLED_IN_SETTINGS *= 'DisabledInSettings'*

#### DISABLED_IN_FLAGS *= 'DisabledInFlags'*

#### ERROR_FETCHING_SIGNIN *= 'ErrorFetchingSignin'*

#### INVALID_SIGNIN_RESPONSE *= 'InvalidSigninResponse'*

#### ACCOUNTS_HTTP_NOT_FOUND *= 'AccountsHttpNotFound'*

#### ACCOUNTS_NO_RESPONSE *= 'AccountsNoResponse'*

#### ACCOUNTS_INVALID_RESPONSE *= 'AccountsInvalidResponse'*

#### ACCOUNTS_LIST_EMPTY *= 'AccountsListEmpty'*

#### ACCOUNTS_INVALID_CONTENT_TYPE *= 'AccountsInvalidContentType'*

#### ID_TOKEN_HTTP_NOT_FOUND *= 'IdTokenHttpNotFound'*

#### ID_TOKEN_NO_RESPONSE *= 'IdTokenNoResponse'*

#### ID_TOKEN_INVALID_RESPONSE *= 'IdTokenInvalidResponse'*

#### ID_TOKEN_IDP_ERROR_RESPONSE *= 'IdTokenIdpErrorResponse'*

#### ID_TOKEN_CROSS_SITE_IDP_ERROR_RESPONSE *= 'IdTokenCrossSiteIdpErrorResponse'*

#### ID_TOKEN_INVALID_REQUEST *= 'IdTokenInvalidRequest'*

#### ID_TOKEN_INVALID_CONTENT_TYPE *= 'IdTokenInvalidContentType'*

#### ERROR_ID_TOKEN *= 'ErrorIdToken'*

#### CANCELED *= 'Canceled'*

#### RP_PAGE_NOT_VISIBLE *= 'RpPageNotVisible'*

#### SILENT_MEDIATION_FAILURE *= 'SilentMediationFailure'*

#### NOT_SIGNED_IN_WITH_IDP *= 'NotSignedInWithIdp'*

#### MISSING_TRANSIENT_USER_ACTIVATION *= 'MissingTransientUserActivation'*

#### REPLACED_BY_ACTIVE_MODE *= 'ReplacedByActiveMode'*

#### RELYING_PARTY_ORIGIN_IS_OPAQUE *= 'RelyingPartyOriginIsOpaque'*

#### TYPE_NOT_MATCHING *= 'TypeNotMatching'*

#### UI_DISMISSED_NO_EMBARGO *= 'UiDismissedNoEmbargo'*

#### CORS_ERROR *= 'CorsError'*

#### SUPPRESSED_BY_SEGMENTATION_PLATFORM *= 'SuppressedBySegmentationPlatform'*

### *class* FederatedAuthUserInfoRequestIssueDetails(federated_auth_user_info_request_issue_reason)

#### federated_auth_user_info_request_issue_reason *: [FederatedAuthUserInfoRequestIssueReason](#nodriver.cdp.audits.FederatedAuthUserInfoRequestIssueReason)*

### *class* FederatedAuthUserInfoRequestIssueReason(\*values)

Represents the failure reason when a getUserInfo() call fails.
Should be updated alongside FederatedAuthUserInfoRequestResult in
third_party/blink/public/mojom/devtools/inspector_issue.mojom.

#### NOT_SAME_ORIGIN *= 'NotSameOrigin'*

#### NOT_IFRAME *= 'NotIframe'*

#### NOT_POTENTIALLY_TRUSTWORTHY *= 'NotPotentiallyTrustworthy'*

#### NO_API_PERMISSION *= 'NoApiPermission'*

#### NOT_SIGNED_IN_WITH_IDP *= 'NotSignedInWithIdp'*

#### NO_ACCOUNT_SHARING_PERMISSION *= 'NoAccountSharingPermission'*

#### INVALID_CONFIG_OR_WELL_KNOWN *= 'InvalidConfigOrWellKnown'*

#### INVALID_ACCOUNTS_RESPONSE *= 'InvalidAccountsResponse'*

#### NO_RETURNING_USER_FROM_FETCHED_ACCOUNTS *= 'NoReturningUserFromFetchedAccounts'*

### *class* ClientHintIssueDetails(source_code_location, client_hint_issue_reason)

This issue tracks client hints related issues. It’s used to deprecate old
features, encourage the use of new ones, and provide general guidance.

#### source_code_location *: [SourceCodeLocation](#nodriver.cdp.audits.SourceCodeLocation)*

#### client_hint_issue_reason *: [ClientHintIssueReason](#nodriver.cdp.audits.ClientHintIssueReason)*

### *class* FailedRequestInfo(url, failure_message, request_id=None)

#### url *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

The URL that failed to load.

#### failure_message *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

The failure message for the failed request.

#### request_id *: [RequestId](network.md#nodriver.cdp.network.RequestId) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

### *class* PartitioningBlobURLInfo(\*values)

#### BLOCKED_CROSS_PARTITION_FETCHING *= 'BlockedCrossPartitionFetching'*

#### ENFORCE_NOOPENER_FOR_NAVIGATION *= 'EnforceNoopenerForNavigation'*

### *class* PartitioningBlobURLIssueDetails(url, partitioning_blob_url_info)

#### url *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

The BlobURL that failed to load.

#### partitioning_blob_url_info *: [PartitioningBlobURLInfo](#nodriver.cdp.audits.PartitioningBlobURLInfo)*

Additional information about the Partitioning Blob URL issue.

### *class* ElementAccessibilityIssueReason(\*values)

#### DISALLOWED_SELECT_CHILD *= 'DisallowedSelectChild'*

#### DISALLOWED_OPT_GROUP_CHILD *= 'DisallowedOptGroupChild'*

#### NON_PHRASING_CONTENT_OPTION_CHILD *= 'NonPhrasingContentOptionChild'*

#### INTERACTIVE_CONTENT_OPTION_CHILD *= 'InteractiveContentOptionChild'*

#### INTERACTIVE_CONTENT_LEGEND_CHILD *= 'InteractiveContentLegendChild'*

#### INTERACTIVE_CONTENT_SUMMARY_DESCENDANT *= 'InteractiveContentSummaryDescendant'*

### *class* ElementAccessibilityIssueDetails(node_id, element_accessibility_issue_reason, has_disallowed_attributes)

This issue warns about errors in the select or summary element content model.

#### node_id *: [BackendNodeId](dom.md#nodriver.cdp.dom.BackendNodeId)*

#### element_accessibility_issue_reason *: [ElementAccessibilityIssueReason](#nodriver.cdp.audits.ElementAccessibilityIssueReason)*

#### has_disallowed_attributes *: [bool](https://docs.python.org/3/library/functions.html#bool)*

### *class* StyleSheetLoadingIssueReason(\*values)

#### LATE_IMPORT_RULE *= 'LateImportRule'*

#### REQUEST_FAILED *= 'RequestFailed'*

### *class* StylesheetLoadingIssueDetails(source_code_location, style_sheet_loading_issue_reason, failed_request_info=None)

This issue warns when a referenced stylesheet couldn’t be loaded.

#### source_code_location *: [SourceCodeLocation](#nodriver.cdp.audits.SourceCodeLocation)*

Source code position that referenced the failing stylesheet.

#### style_sheet_loading_issue_reason *: [StyleSheetLoadingIssueReason](#nodriver.cdp.audits.StyleSheetLoadingIssueReason)*

Reason why the stylesheet couldn’t be loaded.

#### failed_request_info *: [FailedRequestInfo](#nodriver.cdp.audits.FailedRequestInfo) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Contains additional info when the failure was due to a request.

### *class* PropertyRuleIssueReason(\*values)

#### INVALID_SYNTAX *= 'InvalidSyntax'*

#### INVALID_INITIAL_VALUE *= 'InvalidInitialValue'*

#### INVALID_INHERITS *= 'InvalidInherits'*

#### INVALID_NAME *= 'InvalidName'*

### *class* PropertyRuleIssueDetails(source_code_location, property_rule_issue_reason, property_value=None)

This issue warns about errors in property rules that lead to property
registrations being ignored.

#### source_code_location *: [SourceCodeLocation](#nodriver.cdp.audits.SourceCodeLocation)*

Source code position of the property rule.

#### property_rule_issue_reason *: [PropertyRuleIssueReason](#nodriver.cdp.audits.PropertyRuleIssueReason)*

Reason why the property rule was discarded.

#### property_value *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The value of the property rule property that failed to parse

### *class* UserReidentificationIssueType(\*values)

#### BLOCKED_FRAME_NAVIGATION *= 'BlockedFrameNavigation'*

#### BLOCKED_SUBRESOURCE *= 'BlockedSubresource'*

#### NOISED_CANVAS_READBACK *= 'NoisedCanvasReadback'*

### *class* UserReidentificationIssueDetails(type_, request=None, source_code_location=None)

This issue warns about uses of APIs that may be considered misuse to
re-identify users.

#### type_ *: [UserReidentificationIssueType](#nodriver.cdp.audits.UserReidentificationIssueType)*

#### request *: [AffectedRequest](#nodriver.cdp.audits.AffectedRequest) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Applies to BlockedFrameNavigation and BlockedSubresource issue types.

#### source_code_location *: [SourceCodeLocation](#nodriver.cdp.audits.SourceCodeLocation) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Applies to NoisedCanvasReadback issue type.

### *class* PermissionElementIssueType(\*values)

#### INVALID_TYPE *= 'InvalidType'*

#### FENCED_FRAME_DISALLOWED *= 'FencedFrameDisallowed'*

#### CSP_FRAME_ANCESTORS_MISSING *= 'CspFrameAncestorsMissing'*

#### PERMISSIONS_POLICY_BLOCKED *= 'PermissionsPolicyBlocked'*

#### PADDING_RIGHT_UNSUPPORTED *= 'PaddingRightUnsupported'*

#### PADDING_BOTTOM_UNSUPPORTED *= 'PaddingBottomUnsupported'*

#### INSET_BOX_SHADOW_UNSUPPORTED *= 'InsetBoxShadowUnsupported'*

#### REQUEST_IN_PROGRESS *= 'RequestInProgress'*

#### UNTRUSTED_EVENT *= 'UntrustedEvent'*

#### REGISTRATION_FAILED *= 'RegistrationFailed'*

#### TYPE_NOT_SUPPORTED *= 'TypeNotSupported'*

#### INVALID_TYPE_ACTIVATION *= 'InvalidTypeActivation'*

#### SECURITY_CHECKS_FAILED *= 'SecurityChecksFailed'*

#### ACTIVATION_DISABLED *= 'ActivationDisabled'*

#### GEOLOCATION_DEPRECATED *= 'GeolocationDeprecated'*

#### INVALID_DISPLAY_STYLE *= 'InvalidDisplayStyle'*

#### NON_OPAQUE_COLOR *= 'NonOpaqueColor'*

#### LOW_CONTRAST *= 'LowContrast'*

#### FONT_SIZE_TOO_SMALL *= 'FontSizeTooSmall'*

#### FONT_SIZE_TOO_LARGE *= 'FontSizeTooLarge'*

#### INVALID_SIZE_VALUE *= 'InvalidSizeValue'*

### *class* PermissionElementIssueDetails(issue_type, type_=None, node_id=None, is_warning=None, permission_name=None, occluder_node_info=None, occluder_parent_node_info=None, disable_reason=None)

This issue warns about improper usage of the <permission> element.

#### issue_type *: [PermissionElementIssueType](#nodriver.cdp.audits.PermissionElementIssueType)*

#### type_ *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The value of the type attribute.

#### node_id *: [BackendNodeId](dom.md#nodriver.cdp.dom.BackendNodeId) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The node ID of the <permission> element.

#### is_warning *: [bool](https://docs.python.org/3/library/functions.html#bool) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

True if the issue is a warning, false if it is an error.

#### permission_name *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Fields for message construction:
Used for messages that reference a specific permission name

#### occluder_node_info *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Used for messages about occlusion

#### occluder_parent_node_info *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Used for messages about occluder’s parent

#### disable_reason *: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

Used for messages about activation disabled reason

### *class* SelectivePermissionsInterventionIssueDetails(api_name, ad_ancestry, stack_trace=None)

The issue warns about blocked calls to privacy sensitive APIs via the
Selective Permissions Intervention.

#### api_name *: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Which API was intervened on.

#### ad_ancestry *: [AdAncestry](network.md#nodriver.cdp.network.AdAncestry)*

Why the ad script using the API is considered an ad.

#### stack_trace *: [StackTrace](runtime.md#nodriver.cdp.runtime.StackTrace) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

The stack trace at the time of the intervention.

### *class* InspectorIssueCode(\*values)

A unique identifier for the type of issue. Each type may use one of the
optional fields in InspectorIssueDetails to convey more specific
information about the kind of issue.

#### COOKIE_ISSUE *= 'CookieIssue'*

#### MIXED_CONTENT_ISSUE *= 'MixedContentIssue'*

#### BLOCKED_BY_RESPONSE_ISSUE *= 'BlockedByResponseIssue'*

#### HEAVY_AD_ISSUE *= 'HeavyAdIssue'*

#### CONTENT_SECURITY_POLICY_ISSUE *= 'ContentSecurityPolicyIssue'*

#### SHARED_ARRAY_BUFFER_ISSUE *= 'SharedArrayBufferIssue'*

#### CORS_ISSUE *= 'CorsIssue'*

#### ATTRIBUTION_REPORTING_ISSUE *= 'AttributionReportingIssue'*

#### QUIRKS_MODE_ISSUE *= 'QuirksModeIssue'*

#### PARTITIONING_BLOB_URL_ISSUE *= 'PartitioningBlobURLIssue'*

#### NAVIGATOR_USER_AGENT_ISSUE *= 'NavigatorUserAgentIssue'*

#### GENERIC_ISSUE *= 'GenericIssue'*

#### DEPRECATION_ISSUE *= 'DeprecationIssue'*

#### CLIENT_HINT_ISSUE *= 'ClientHintIssue'*

#### FEDERATED_AUTH_REQUEST_ISSUE *= 'FederatedAuthRequestIssue'*

#### BOUNCE_TRACKING_ISSUE *= 'BounceTrackingIssue'*

#### COOKIE_DEPRECATION_METADATA_ISSUE *= 'CookieDeprecationMetadataIssue'*

#### STYLESHEET_LOADING_ISSUE *= 'StylesheetLoadingIssue'*

#### FEDERATED_AUTH_USER_INFO_REQUEST_ISSUE *= 'FederatedAuthUserInfoRequestIssue'*

#### PROPERTY_RULE_ISSUE *= 'PropertyRuleIssue'*

#### SHARED_DICTIONARY_ISSUE *= 'SharedDictionaryIssue'*

#### ELEMENT_ACCESSIBILITY_ISSUE *= 'ElementAccessibilityIssue'*

#### SRI_MESSAGE_SIGNATURE_ISSUE *= 'SRIMessageSignatureIssue'*

#### UNENCODED_DIGEST_ISSUE *= 'UnencodedDigestIssue'*

#### CONNECTION_ALLOWLIST_ISSUE *= 'ConnectionAllowlistIssue'*

#### USER_REIDENTIFICATION_ISSUE *= 'UserReidentificationIssue'*

#### PERMISSION_ELEMENT_ISSUE *= 'PermissionElementIssue'*

#### PERFORMANCE_ISSUE *= 'PerformanceIssue'*

#### SELECTIVE_PERMISSIONS_INTERVENTION_ISSUE *= 'SelectivePermissionsInterventionIssue'*

### *class* InspectorIssueDetails(cookie_issue_details=None, mixed_content_issue_details=None, blocked_by_response_issue_details=None, heavy_ad_issue_details=None, content_security_policy_issue_details=None, shared_array_buffer_issue_details=None, cors_issue_details=None, attribution_reporting_issue_details=None, quirks_mode_issue_details=None, partitioning_blob_url_issue_details=None, navigator_user_agent_issue_details=None, generic_issue_details=None, deprecation_issue_details=None, client_hint_issue_details=None, federated_auth_request_issue_details=None, bounce_tracking_issue_details=None, cookie_deprecation_metadata_issue_details=None, stylesheet_loading_issue_details=None, property_rule_issue_details=None, federated_auth_user_info_request_issue_details=None, shared_dictionary_issue_details=None, element_accessibility_issue_details=None, sri_message_signature_issue_details=None, unencoded_digest_issue_details=None, connection_allowlist_issue_details=None, user_reidentification_issue_details=None, permission_element_issue_details=None, performance_issue_details=None, selective_permissions_intervention_issue_details=None)

This struct holds a list of optional fields with additional information
specific to the kind of issue. When adding a new issue code, please also
add a new optional field to this type.

#### cookie_issue_details *: [CookieIssueDetails](#nodriver.cdp.audits.CookieIssueDetails) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### mixed_content_issue_details *: [MixedContentIssueDetails](#nodriver.cdp.audits.MixedContentIssueDetails) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### blocked_by_response_issue_details *: [BlockedByResponseIssueDetails](#nodriver.cdp.audits.BlockedByResponseIssueDetails) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### heavy_ad_issue_details *: [HeavyAdIssueDetails](#nodriver.cdp.audits.HeavyAdIssueDetails) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### content_security_policy_issue_details *: [ContentSecurityPolicyIssueDetails](#nodriver.cdp.audits.ContentSecurityPolicyIssueDetails) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### shared_array_buffer_issue_details *: [SharedArrayBufferIssueDetails](#nodriver.cdp.audits.SharedArrayBufferIssueDetails) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### cors_issue_details *: [CorsIssueDetails](#nodriver.cdp.audits.CorsIssueDetails) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### attribution_reporting_issue_details *: [AttributionReportingIssueDetails](#nodriver.cdp.audits.AttributionReportingIssueDetails) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### quirks_mode_issue_details *: [QuirksModeIssueDetails](#nodriver.cdp.audits.QuirksModeIssueDetails) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### partitioning_blob_url_issue_details *: [PartitioningBlobURLIssueDetails](#nodriver.cdp.audits.PartitioningBlobURLIssueDetails) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### navigator_user_agent_issue_details *: [NavigatorUserAgentIssueDetails](#nodriver.cdp.audits.NavigatorUserAgentIssueDetails) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### generic_issue_details *: [GenericIssueDetails](#nodriver.cdp.audits.GenericIssueDetails) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### deprecation_issue_details *: [DeprecationIssueDetails](#nodriver.cdp.audits.DeprecationIssueDetails) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### client_hint_issue_details *: [ClientHintIssueDetails](#nodriver.cdp.audits.ClientHintIssueDetails) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### federated_auth_request_issue_details *: [FederatedAuthRequestIssueDetails](#nodriver.cdp.audits.FederatedAuthRequestIssueDetails) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### bounce_tracking_issue_details *: [BounceTrackingIssueDetails](#nodriver.cdp.audits.BounceTrackingIssueDetails) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### cookie_deprecation_metadata_issue_details *: [CookieDeprecationMetadataIssueDetails](#nodriver.cdp.audits.CookieDeprecationMetadataIssueDetails) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### stylesheet_loading_issue_details *: [StylesheetLoadingIssueDetails](#nodriver.cdp.audits.StylesheetLoadingIssueDetails) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### property_rule_issue_details *: [PropertyRuleIssueDetails](#nodriver.cdp.audits.PropertyRuleIssueDetails) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### federated_auth_user_info_request_issue_details *: [FederatedAuthUserInfoRequestIssueDetails](#nodriver.cdp.audits.FederatedAuthUserInfoRequestIssueDetails) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### shared_dictionary_issue_details *: [SharedDictionaryIssueDetails](#nodriver.cdp.audits.SharedDictionaryIssueDetails) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### element_accessibility_issue_details *: [ElementAccessibilityIssueDetails](#nodriver.cdp.audits.ElementAccessibilityIssueDetails) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### sri_message_signature_issue_details *: [SRIMessageSignatureIssueDetails](#nodriver.cdp.audits.SRIMessageSignatureIssueDetails) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### unencoded_digest_issue_details *: [UnencodedDigestIssueDetails](#nodriver.cdp.audits.UnencodedDigestIssueDetails) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### connection_allowlist_issue_details *: [ConnectionAllowlistIssueDetails](#nodriver.cdp.audits.ConnectionAllowlistIssueDetails) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### user_reidentification_issue_details *: [UserReidentificationIssueDetails](#nodriver.cdp.audits.UserReidentificationIssueDetails) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### permission_element_issue_details *: [PermissionElementIssueDetails](#nodriver.cdp.audits.PermissionElementIssueDetails) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### performance_issue_details *: [PerformanceIssueDetails](#nodriver.cdp.audits.PerformanceIssueDetails) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

#### selective_permissions_intervention_issue_details *: [SelectivePermissionsInterventionIssueDetails](#nodriver.cdp.audits.SelectivePermissionsInterventionIssueDetails) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

### *class* IssueId

A unique id for a DevTools inspector issue. Allows other entities (e.g.
exceptions, CDP message, console messages, etc.) to reference an issue.

### *class* InspectorIssue(code, details, issue_id=None)

An inspector issue reported from the back-end.

#### code *: [InspectorIssueCode](#nodriver.cdp.audits.InspectorIssueCode)*

#### details *: [InspectorIssueDetails](#nodriver.cdp.audits.InspectorIssueDetails)*

#### issue_id *: [IssueId](#nodriver.cdp.audits.IssueId) | [None](https://docs.python.org/3/library/constants.html#None)* *= None*

A unique id for this issue. May be omitted if no other entity (e.g.
exception, CDP message, etc.) is referencing this issue.

## Commands

Each command is a generator function. The return
type `Generator[x, y, z]` indicates that the generator
*yields* arguments of type `x`, it must be resumed with
an argument of type `y`, and it returns type `z`. In
this library, types `x` and `y` are the same for all
commands, and `z` is the return type you should pay attention
to. For more information, see
[Getting Started: Commands](../../readme.md#getting-started-commands).

### check_forms_issues()

Runs the form issues check for the target page. Found issues are reported
using Audits.issueAdded event.

* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`List`](https://docs.python.org/3/library/typing.html#typing.List)[[`GenericIssueDetails`](#nodriver.cdp.audits.GenericIssueDetails)]]
* **Returns:**

### disable()

Disables issues domain, prevents further issues from being reported to the client.

* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### enable()

Enables issues domain, sends the issues collected so far to the client by means of the
`issueAdded` event.

* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`None`](https://docs.python.org/3/library/constants.html#None)]

### get_encoded_response(request_id, encoding, quality=None, size_only=None)

Returns the response body and size if it were re-encoded with the specified settings. Only
applies to images.

* **Parameters:**
  * **request_id** ([`RequestId`](network.md#nodriver.cdp.network.RequestId)) – Identifier of the network request to get content for.
  * **encoding** ([`str`](https://docs.python.org/3/library/stdtypes.html#str)) – The encoding to use.
  * **quality** ([`float`](https://docs.python.org/3/library/functions.html#float) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* The quality of the encoding (0-1). (defaults to 1)
  * **size_only** ([`bool`](https://docs.python.org/3/library/functions.html#bool) | [`None`](https://docs.python.org/3/library/constants.html#None)) –  *(Optional)* Whether to only return the size information (defaults to false).
* **Return type:**
  [`Generator`](https://docs.python.org/3/library/typing.html#typing.Generator)[[`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Dict`](https://docs.python.org/3/library/typing.html#typing.Dict)[[`str`](https://docs.python.org/3/library/stdtypes.html#str), [`Any`](https://docs.python.org/3/library/typing.html#typing.Any)], [`Tuple`](https://docs.python.org/3/library/typing.html#typing.Tuple)[[`str`](https://docs.python.org/3/library/stdtypes.html#str) | [`None`](https://docs.python.org/3/library/constants.html#None), [`int`](https://docs.python.org/3/library/functions.html#int), [`int`](https://docs.python.org/3/library/functions.html#int)]]
* **Returns:**
  A tuple with the following items:
  1. **body** -  *(Optional)* The encoded body as a base64 string. Omitted if sizeOnly is true. (Encoded as a base64 string when passed over JSON)
  2. **originalSize** - Size before re-encoding.
  3. **encodedSize** - Size after re-encoding.

## Events

Generally, you do not need to instantiate CDP events
yourself. Instead, the API creates events for you and then
you use the event’s attributes.

### *class* IssueAdded(issue)

#### issue *: [InspectorIssue](#nodriver.cdp.audits.InspectorIssue)*
