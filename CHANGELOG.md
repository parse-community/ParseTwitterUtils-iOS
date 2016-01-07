# Change Log
All notable changes to this project will be documented in this file.

---

## [ParseTwitterUtils 1.10.0](https://github.com/ParsePlatform/ParseTwitterUtils-iOS/releases/tag/1.10.0) (01/07/2016)

#### New
- ParseTwitterUtils now requires Xcode 7.0+.  
  [#16](https://github.com/ParsePlatform/ParseTwitterUtils-iOS/pull/16),
  [#17](https://github.com/ParsePlatform/ParseTwitterUtils-iOS/pull/17),
  [#20](https://github.com/ParsePlatform/ParseTwitterUtils-iOS/pull/20)
  by [Nikita Lutsenko](https://github.com/nlutsenko)

#### Improved
- Cleaned up and improved documentation.  
  [#15](https://github.com/ParsePlatform/ParseTwitterUtils-iOS/pull/15)
  by [Nikita Lutsenko](https://github.com/nlutsenko)

## [ParseTwitterUtils 1.9.1](https://github.com/ParsePlatform/ParseTwitterUtils-iOS/releases/tag/1.9.1) (11/17/2015)

#### New
- ParseTwitterUtils now supports Xcode 7.1+. #6

#### Improved
- Added safeguard assertion for initialization of PFTwitterUtils before Parse is initialized. #4
- Removed all custom nullability annotation macros. #8
- Improved localized strings generation. #2

#### Fixed
- Fixed potential warnings in PFOAuth1FlowDialog. #10

## [ParseTwitterUtils 1.9.0](https://github.com/ParsePlatform/ParseTwitterUtils-iOS/releases/tag/1.9.0) (10/08/2015)

Hello, open source!

#### Fixed
- Fixed initialization potentially blocking the main thread for a continuous amount of time.
- Fixed parameter URL Encoding when signing requests with Twitter.
