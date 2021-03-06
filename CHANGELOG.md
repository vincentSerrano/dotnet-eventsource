# Change log

All notable changes to the LaunchDarkly's EventSource implementation for C# will be documented in this file. This project adheres to [Semantic Versioning](http://semver.org).

## [3.1.5] - 2018-08-29
Duplicate of 3.1.4, created due to a problem in the release process.

## [3.1.4] - 2018-08-29
### Fixed
- Fixed a bug that prevented the event source from reconnecting to the stream if it received an HTTP error status from the server (as opposed to simply losing the connection).

## [3.1.3] - 2018-08-13
### Fixed
- The reconnection attempt counter is no longer shared among all EventSource instances. Previously, if you connected to more than one stream, all but the first would behave as if they were reconnecting and would have a backoff delay.

## [3.1.2] - 2018-08-02
### Changed
- The SDK was referencing some system assemblies via `<PackageReference>`, which could cause dependency conflicts. These have been changed to framework `<Reference>`s. A redundant reference to `System.Runtime` was removed.

### Fixed
- If the stream connection fails, there should be an increasing backoff interval before each reconnect attempt. Previously, it would log a message about waiting some number of milliseconds, but then not actually wait.

## [3.1.1] - 2018-06-28
### Removed
- Removed an unused dependency on Newtonsoft.Json.

## [3.1.0] - 2018-06-01
### Added
- The new class `ConfigurationBuilder` provides a validated fluent builder pattern for `Configuration` instances.
- The HTTP method and request body can now be specified in `ConfigurationBuilder` or in the `Configuration` constructor. The default is still to use `GET` and not send a request body.

## [3.0.0] - 2018-02-23
### Changed
- Logging is now done via `Common.Logging`.

### Added
- `EventSource` now uses the interface `IEventSource`.

## [2.2.1] - 2018-02-05
- Downgrade Microsoft.Extensions.Logging to 1.0.2 to reduce dependencies brought in when building against .NET Framework.

## [2.2.0] - 2018-01-19
### Added
- Exposed `EventSourceServiceCancelledException` as a public class.

### Changed
- Removed unused and transitive dependencies.
- Added a reference to the Apache 2.0 license in `LaunchDarkly.EventSource.csproj`
- Improved logging. Thanks @JeffAshton!

## [2.1.1] - 2017-11-29
### Changed
- Move from .NET Standard 1.6 to 1.4.

## [2.1.0] - 2017-11-16
### Added
- Exposed the `ExponentialBackoffWithDecorrelation` as a public class. This class may be used to calculate exponential backoff with jitter.

### Changed
- Reconnects to EventSource are now handled inline, rather than using [Polly](https://github.com/App-vNext/Polly) for managing retry policies.

## [2.0.0] - 2017-10-11
### Changed
- Removed the `closeOnEndOfStream` property.

## [1.1.0] 2017-10-02
### Added
- `ConnectToEventSourceAsync` now takes in a new boolean parameter, `closeOnEndOfStream`, which, if true, will close the EventSource connection when the end of the stream is reached.

### Changed
- Fixed a bug causing causing read timeouts to never propogate.

## [1.0.1] 2017-09-27
### Added
- Signed EventSource Assembly.

### Changed
- Change dependency on Polly to Polly-Signed.

## [1.0.0] 2017-09-22
Hello world!
