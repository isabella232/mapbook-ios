# Mapbook iOS
This repo is home to the mobile mapbook app, an example application using the [ArcGIS Runtime SDK for iOS](https://developers.arcgis.com/iOS/). Replace the paper maps you use for field work with offline maps.

## Features
- Mobile map packages
- Feature layers
- Identify
- Table of Contents
- Show a legend
- Use a map view callout
- Geocode addresses
- Suggestion search
- Bookmarks
- Sign in to an ArcGIS account

## Best Practices
The project also demonstrates some patterns for building real-world apps around the ArcGIS Runtime SDK.

* Defining a modular, decoupled UI that operates alongside a map view
* Asynchronous service and UI coding patterns
* Internal application communication patterns

## Get Started
You will need [Xcode](https://itunes.apple.com/us/app/xcode/id497799835?mt=12) and the [ArcGIS Runtime SDK for iOS](https://developers.arcgis.com/ios/latest/swift/guide/install.htm) (v100.1 or later) installed locally.

Clone the GitHub repository and open `mapbook-iOS.xcodeproj` in Xcode.

### Configure the app
The app can be run as is, but it's recommended you do some configuration to set up OAuth to be relevant to your users (certainly it should not be deployed without these changes):

1. Register an ArcGIS Portal Application.
2. Configure the Mapbook App project to reference that application.
3. License the app to remove the Developer Mode watermark.

#### 1. Register an Application 
For OAuth configuration, create a new Application in your ArcGIS Portal to obtain a `Client ID` and configure a `Redirect URL`. The **Client ID** configures the ArcGIS Runtime to show your users, during the log in process, that the application was built by you and can be trusted. The **Redirect URL** configures the OAuth process to then return to your app once authentication is complete.

1. Log in to [https://developers.arcgis.com](https://developers.arcgis.com) with either your ArcGIS Organizational Account or an ArcGIS Developer Account.
2. Register a new Application. ![Register new application](/docs/images/create-application.png)
3. In the Authentication tab, note the **Client ID** and add a **Redirect URL**, e.g. `my-mapbook-app://auth`. We will use this URL in the **Configuring the project** section below. ![Configure new application](/docs/images/configure-application.png)

#### 2. Configuring the project
Open the project in Xcode and browse to the `mapbook-iOS` target's `Info` panel and expand the `AGSConfiguration` dictionary (see steps 1-4 in the screenshot below).

1. Set the `ClientID` value to the application's **Client ID** noted above.
2. Set the `AppURLScheme` value to match the **Redirect URL** scheme (the part *before* the `://`, e.g. `my-mapbook-app`) configured in "Register an Application" above. Note how the `AppURLScheme` and `AuthURLPath` combine to construct the **Redirect URL**. ![Configure the App URL Scheme](/docs/images/configure-xcode-target.png)
3. Expand the **URL Types** section and modify the existing entry.
    1. The **Identifier** doesn't matter, but should be unique (e.g. `com.my-org.my-mapbook-app`).
    2. The **URL Scheme** should match the **Redirect URL** scheme (the part *before* the `://`, e.g. `my-mapbook-app`) configured in "Register an Application" above.

#### 3. License the app (Optional)
This step is optional during development, but required for deployment.

To remove the _Licensed for Developer Use Only_ watermark on the map view, set the `LicenseKey` in the `AGSConfiguration` dictionary. Retrieve this value by clicking the `Show my ArcGIS Runtime Lite license key` at the top-right of the [Licensing Your ArcGIS Runtime App](https://developers.arcgis.com/arcgis-runtime/licensing/) page (you must be logged in).

## Learn More
Learn more about the App Architecture and usage here.

## Requirements
* [Xcode](https://itunes.apple.com/us/app/xcode/id497799835?mt=12)
* [ArcGIS Runtime SDK for iOS](https://developers.arcgis.com/ios/)

## Contributing
Anyone and everyone is welcome to [contribute](CONTRIBUTING.md). We do accept pull requests.

1. Get involved
2. Report issues
3. Contribute code
4. Improve documentation

## Licensing
Copyright 2017 Esri

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.

A copy of the license is available in the repository's [LICENSE](LICENSE) file.

For information about licensing your deployed app, see [License your app](https://developers.arcgis.com/ios/latest/swift/guide/license-your-app.htm).
