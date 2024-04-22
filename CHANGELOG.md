# Change Log

## 3.1.0 (2024-04-19)

### Features

- New [Likelihood to Convert](https://developers.kameleoon.com/feature-management-and-experimentation/using-visit-history-in-feature-flags-and-experiments/#predefined-targeting-conditions) targeting condition.
- [`getRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#getremotevisitordata) method now accepts new boolean parameter `isUniqueIdentifier` to obtain all linked visitors data when working with [Cross-device experimentation](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#cross-device-experimentation)
- Miscellaneous [Cross-device experimentation](https://developers.kameleoon.com/core-concepts/cross-device-experimentation) improvements

### Patch Changes

- Improved visits data collection logic
- Fixed the issue with when `_` variable was transformed to duplicate identifier `a` causing `TypeError`
- Kameleoon network request headers are now properly used
- `Browser` condition could throw an error when the browser version wasn't specified on Kameleoon Platform
- `Geolocation` condition is now case insensitive
- SDK Core version is no more sent with tracking
- Updated dependencies
  - @kameleoon/javascript-sdk-core@4.1.0

## 3.0.1 (2024-02-21)

### Patch Changes

- Added support for additional Data API servers across the world for even faster network requests
- Updated dependencies
  - @kameleoon/javascript-sdk-core@4.0.1

## 3.0.0 (2024-02-16)

### Breaking Changes

- Previously deprecated `KameleoonUtils.getVisitorCode()` was removed

### Features

- Added [External Dependencies](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#external-dependencies) capabilities

### Patch Changes

- Updated dependencies:
  - @kameleoon/javascript-sdk-core@4.0.0

## 2.5.2 (2024-02-07)

### Bug fixes

- Tracking wasn't sent if consent is required

## 2.5.1 (2024-01-29)

### Bug fixes

- Context binding in [setLegalConsent](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#setlegalconsent) method

## 2.5.0 (2024-01-18)

### Bug fixes

- SDK threw an error reading storage when migrating from older SDK versions

### Features

- Added new SDK `configuration` parameter [`requestTimeout`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk/#1-initializing-the-kameleoon-client), which defines maximum time in _milliseconds_ after which any SDK network request will fail

## 2.4.1 (2023-12-15)

### Bug fixes

- Fix nonce for `Conversion` data

## 2.4.0 (2023-12-12)

### Features

- Updated the [getFeatureFlagVariable](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#getfeatureflagvariable) method to return an object of type `FeatureFlagVariableType`
- Enhanced the [getFeatureFlagVariables](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#getfeatureflagvariables) method to include the `key` field in its return value.

### Bug fixes

- Custom Data mapping identifier wasn't tracked correctly

## 2.3.0 (2023-12-11)

### Features

- [flush](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#flush) and [trackConversion](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#trackConversion) methods now have a new optional parameter `isUniqueIdentifier` used for extra [Kameleoon Cross-device Experimentation](https://developers.kameleoon.com/core-concepts/cross-device-experimentation) capabilities
- [getVisitorCode](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#getvisitorcode) and [setLegalConsent](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#setlegalconsent) methods now have an overload allowing methods to be used without parameters (instead of providing and empty object `{}`)

### Bug fixes

- Targeting data cleanup caused `TypeError`

## 2.2.1 (2023-12-04)

### Bug fixes

- Client cookie is now set properly

## 2.2.0 (2023-11-30)

### Features

- [CustomData session merging](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#using-custom-data-for-session-merging) abilities for [Kameleoon Cross-device Experimentation](https://developers.kameleoon.com/core-concepts/cross-device-experimentation)

## 2.1.0 (2023-11-24)

### Features

- Added `setLegalConsent` method to determine the types data Kameleoon includes in tracking requests. This helps you adhere to legal and regulatory requirements while responsibly managing visitor data. You can find more information in the [Consent management policy](https://help.kameleoon.com/consent-management-policy).

## 2.0.0 (2023-11-16)

### Breaking change

- SDK stopped the support of the following methods were:
  - `getExperiments`
  - `getVisitorExperiments`
  - `triggerExperiment`
- Previously deprecated `flushData` method was removed
- [`KameleoonClient`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#arguments) parameters are now an object with type [`SDKParameters`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#arguments)
- [`getRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#getremotevisitordata) method parameters were changed to an object with type [`RemoteVisitorDataParamsType`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#parameters-11) that has a new `filters` field

### Features

- New method for retrieving multiple feature flag variables - [`getFeatureFlagVariables`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#getfeatureflagvariables)
- [`getRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#getremotevisitordata) is now capable of retrieving information from up to 25 visits along with some additional visit information configured by new `filters` field
- [`PageView`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#pageview) data items are now stored by unique URL with timestamps of visits - each visitor can have several `PageView` URLs stored
- [`Conversion`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#conversion) data items are now stored as a list of conversion for each visitor
- [Cross Device Synchronization](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#synchronizing-custom-data-across-devices) was improved - [`CustomData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#customdata) with `Visitor` scope is always re-sent with tracking calls allowing seamless synchronization using [`getRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#getremotevisitordata)
- [New targeting conditions](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#list-of-supported-targeting-conditions) are now available (some of them may require [`getRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#getremotevisitordata) pre-loaded data)
  - `Browser Cookie`
  - `Application Version`
  - `Operating System`
  - `IP Geolocation`
  - `Segment`
  - `Target Feature Flag`
  - `Previous Page`
  - `Number of Page Views`
  - `Time since First Visit`
  - `Time since Last Visit`
  - `Number of Visits Today`
  - `Total Number of Visits`
  - `New or Returning Visitor`
- New Kameleoon Data types were introduced:
  - [`ApplicationVersion`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#applicationversion)
  - [`Cookie`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#cookie)
  - [`OperatingSystem`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#operatingsystem)
  - [`GeolocationData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#geolocationdata)

### Bug fixes

- `SDKParameters` type is now correctly exported from SDK
- SDK Polling re-tries mechanism was optimized - SDK will now try to obtain configuration again during the next poll after 3 failed configuration loading attempts
- [`onConfigurationUpdate`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#onconfigurationupdate) callback now fires on successful configuration update in storage (previously fired after network configuration retrieval)

## 1.8.1 (2023-10-20)

### Bug fixes

- Fix previous version deploy issue

## 1.8.0 (2023-10-20)

### Features

- Added new method [`getVisitorWarehouseAudience`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#getvisitorwarehouseaudience)

## 1.7.4 (2023-10-11)

### Bug fixes

- Storage data parse overhead optimization

## 1.7.3 (2023-09-05)

### Bug fixes

- `UserAgent` was not exported from SDK

## 1.7.2 (2023-08-31)

### Bug fixes

- `Custom Data Condition` now handles index `0` properly

## 1.7.1 (2023-08-25)

### Bug fixes

- Multiple `Real Time Update` connections are no longer created
- `Custom Data Condition` now handles all exceptions properly

## 1.7.0 (2023-08-11)

### Bug fixes

- Empty Custom Data is now sending activity tracking event

### Features

- Added [Cross Device Custom Data Synchronization](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#cross-device-custom-data-synchronization) capabilities

## 1.6.1 (2023-07-26)

### Bug fixes

- [`flush`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#flush) now sends offline tracking requests even if there's no new data to track.
- Timestamps for offline requests are set correctly.

## 1.6.0 (2023-07-21)

### Features

- `flushData` has been deprecated in favor of [`flush`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#flush).
- [`flush`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#flush) sends failed tracking requests that were stored locally during the offline mode at first and then proceeds with the latest request.

## 1.5.2 (2023-07-17)

### Bug fixes

- Typescript `.d.ts` files have proper relative path resolution.
- Unused tracking parameters are no longer sent.
- Real-time update events now get the latest configuration.

### Features

- When the client is initialized in offline mode, in case of network issues failed tracking requests made by [`flushData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk/#flushdata), [`trackConversion`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk/#trackconversion), [`triggerExperiment`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk/#triggerexperiment), [`getFeatureFlagVariationKey`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk/#getfeatureflagvariationkey) or [`getFeatureFlagVariable`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk/#getfeatureflagvariable) will be sent anew once the client is back online.
- Minor optimization for checking [targeting conditions](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#list-of-supported-targeting-conditions) of a segment.

## 1.5.1 (2023-06-30)

### Bug fixes

- Tracking data duplications

## 1.5.0 (2023-06-28)

### Bug fixes

- Improve error handling for [`getRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#obtain-custom-data-from-kameleoon-data-api)
- Visitor code is now validated correctly in every method that uses it.
- Result bundle is now compatible with systems not using `ESM` and `CommonJS`. It's minimized and uses code splitting for `crypto-js` `sha256` function.
- Parameter `revenue` for [`Conversion`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#conversion) is now optional.
- Each visitor can now only have one type of associated [`Kameleoon Data Type`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#data-types), except for [`CustomData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#customdata), that a visitor can have one per `customDataIndex`.

### Features

- New conditions are now supported: `Device`, `Browser`, `SDKLanguage`, `Page Title`, `Page View`, `Visitor Code`, `Conversion`. See the [full list of supported conditions](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#list-of-supported-targeting-conditions).
- [`Browser`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#browser) now has new optional parameter `version`.
- [`flushData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#flush-tracking-data) `visitorCode` parameter is now optional.
- Custom data that is marked as `local only` on Kameleoon Platform is now only used for targeting (not flushed with tracking requests).
- JavaScript SDK is now available as a single file from the static server, see the [details](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#installation)

## 1.4.4 (2023-06-01)

### Bug fixes

- Empty visitor code is no more allowed
- Incorrect tracking body upon triggering an experiment

## 1.4.3 (2023-05-24)

### Bug fixes

- Fixed issue for sending unique `Nonce` parameter on tracking requests

## 1.4.2 (2023-05-21)

### Bug fixes

- [`getRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#obtain-custom-data-from-kameleoon-data-api) current visits not being up-to-date

## 1.4.1 (2023-05-20)

### Bug fixes

- [`getRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#obtain-custom-data-from-kameleoon-data-api) data parse error

## 1.4.0 (2023-05-19)

### Features

- Added method [`getRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#obtain-custom-data-from-kameleoon-data-api)
- Added offline mode for [`initialize`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#initialize-kameleoon-client) method.

## 1.3.3 (2023-05-16)

### Bug fixes

- Initialization throws error

## 1.3.2 (2023-04-24)

### Bug fixes

- Tracking feature flag rule with variation `off` wasn't displayed on result page

## 1.3.1 (2023-04-22)

### Bug fixes

- core dependency fix

## 1.3.0 (2023-04-21)

### Features

- Added method [`getEngineTrackingCode`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#sending-exposure-events-to-external-tools)

## 1.2.0 (2023-04-14)

### Features

- Added method [`getExperimentVariationData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#get-experiment-variation-data)
- Targeting data cleanup interval is now [`optional`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#1-initializing-the-kameleoon-client) and not set by default
- [`getFeatureFlagVariationKey`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#get-variation-key-for-a-certain-feature-flag), [`getFeatureFlagVariable`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#get-a-variable-of-a-certain-feature-flag), [`isFeatureFlagActive`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#check-if-the-feature-is-active-for-visitor) methods do not check previously allocated variation, rather recalculate it each time. Same methods now send tracking request for any rule type (previously only for `Experementation` rule)

### Bug fixes

- `variationId` is undefined when using feature flag related methods

## 1.1.1 (2023-04-05)

### Bug fixes

- Internal bug fixes

## 1.1.0 (2023-03-22)

### Features

- License changed from `GPL3.0` to `ISC`

## 1.0.0 (2023-03-21)

### Features

- Initial Release
