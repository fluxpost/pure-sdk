## 1.0.63

- Delay starting the connection tracking service until after the user has accepted location permissions.
- Fix a bug that caused events with empty "event" payloads to be sent to the server.
- Fix sending wrong value for adidLimited in device configuration.
- Fixes issue that could cause the config service to fetch more often than necessary.
- Improve battery efficency.
- Fixed an issue that caused the "enableWhenInUse" config flag to have no effect.
- Fixed an issue that caused the GPS to be enabled on app start when it was not needed.
- Fixed EddystoneService using wrong scanning type while in foreground.

- API: connection.timestamp defaults to current date if the last changed timestamp is not available
- API: remember connection change timestamps across restarts for more accurate information
- API: if connection.cellType is not available, do not include instead of including empty string
- API: changed device.powersave default value from "unknown" to false
- API: visit.hacc, eddystone.rssi, beacon.major, and beacon.minor are now not included if they are invalid
- API: fixed sending extra information in beacon.uuid, field is now correctly formatted UUID

## 1.0.62

- Updated internal AFNetworking code to fix 2 data races.
- Audited and fixed CoreData implementation for data races.
- Added locking to prevent concurrent modification to shared dictionaries.
- Fixed a warning in CoreData on iOS 9.

## 1.0.61

- APIClient: Updated default value from "unknown" to "0001-01-01" for the departure date of a visit.
- APIClient: Updated default value from "unknown" to -1 for the batter level.
- APIClient: Fixed wrong version reported in HTTP calls.
- Bitcode enabled on required architecture slices. (armv7 + arm64)
- SDK reports correct version number when not integrated with Cocoapods.
- Public Interface: Added overload for custom event methods. New method allows user to force send events even if SDK is off. Event methods without the overload default to force = NO.
- Include the latest location in the connection event payload.
- Seperate cloud config for when in use and always location tracking for better control of SDK.
- Added ClientID property to Pure.h

#### Known Bitcode Issue
Archiving when integrating through Cocoapods while bitcode is turned on results in the below error. Workaround : Head to project settings, search for "Bitcode" and temporarily disable the "Enable Bitcode" setting. We will provide an update with a fix as soon as possible. This issue does not affect regular compilation, as it only shows up while archiving.

ld: bitcode bundle could not be generated because 'Pods/PureSDK/PureSDK.framework/PureSDK' was built without full bitcode. All frameworks and dylibs for bitcode must be generated from Xcode Archive or Install build file 'Pods/PureSDK/PureSDK.framework/PureSDK' for architecture armv7
