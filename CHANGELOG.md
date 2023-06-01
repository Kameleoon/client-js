# Change Log

All notable changes to this project will be documented in this file.

[Project Homepage](https://developers.kameleoon.com/javascript-sdk.html)

# 1.4.4 (2023-06-01)


### Bug fixes

* Empty visitor code is no more allowed
* Incorrect tracking body upon triggering an experiment

# 1.4.3 (2023-05-24)


### Bug fixes

* Fixed issue for sending unique `Nonce` parameter on tracking requests

# 1.4.2 (2023-05-21)


### Bug fixes

* [`getRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#obtain-custom-data-from-kameleoon-data-api) current visits not being up-to-date

# 1.4.1 (2023-05-20)


### Bug fixes

* [`getRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#obtain-custom-data-from-kameleoon-data-api) data parse error

# 1.4.0 (2023-05-19)


### Features

* Added method [`getRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#obtain-custom-data-from-kameleoon-data-api)
* Added offline mode for [`initialize`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#initialize-kameleoon-client) method.

# 1.3.3 (2023-05-16)


### Bug fixes

* Initialization throws error

# 1.3.2 (2023-04-24)


### Bug fixes

* Tracking feature flag rule with variation `off` wasn't displayed on result page

# 1.3.1 (2023-04-22)


### Bug fixes

* core dependency fix

# 1.3.0 (2023-04-21)


### Features

* Added method [`getEngineTrackingCode`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#sending-exposure-events-to-external-tools)

# 1.2.0 (2023-04-14)

### Features

* Added method [`getExperimentVariationData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#get-experiment-variation-data)
* Targeting data cleanup interval is now [`optional`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#1-initializing-the-kameleoon-client) and not set by default
* [`getFeatureFlagVariationKey`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#get-variation-key-for-a-certain-feature-flag), [`getFeatureFlagVariable`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#get-a-variable-of-a-certain-feature-flag), [`isFeatureFlagActive`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/js-sdk#check-if-the-feature-is-active-for-visitor) methods do not check previously allocated variation, rather recalculate it each time. Same methods now send tracking request for any rule type (previously only for `Experementation` rule)

### Bug fixes

* `variationId` is undefined when using feature flag related methods

# 1.1.1 (2023-04-05)


### Bug fixes

* Internal bug fixes

# 1.1.0 (2023-03-22)


### Features

- License changed from `GPL3.0` to `ISC`


# 1.0.0 (2023-03-21)


### Features

* Initial Release
