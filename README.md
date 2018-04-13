

## CA Mobile SDK for Xamarin

The Mobile SDK for Xamarin provides simple and secure access to CA Mobile API Gateway (MAG) services. 

## Documentation
- [Mobile SDK for Xamarin Android Guide](https://github.com/CAAPIM/Xamarin-MAS-Foundation/blob/DocEdits/Guides/Android/ANDROID_GUIDES.md)
- [Mobile SDK for Xamarin iOS Guide](https://github.com/CAAPIM/Xamarin-MAS-Foundation/blob/DocEdits/Guides/iOS/IOS_GUIDES.md)
- [Mobile SDK for Xamarin Android API Reference](http://mas.ca.com//xamarin-android/1.7.00/sdk/)
- [Mobile SDK for Xamarin iOS API Reference](http://mas.ca.com//xamarin-ios/1.7.00/sdk/)


## What's in this Release

In this release, you get **MASFoundation**, the core library that handles the communication and authentication layer. With MASFoundation you can quickly build secure Xamarin apps using these features:
 
- Authentication and authorization, limited to:  
  - Device Registration
  - User log in and client credentials
  - Fingerprint session lock
  - Single Sign-on 
- Secure access to APIs
- Send HTTP Requests to external APIs

The SDK contains:
- MASFoundation llibrary for iOS and Android with the above features 
- A sample app so you can test basic authentication flows with a CA Mobile API Gateway (MAG)
- iOS and Android guides and API reference documentation  
    
::: alert info
**Note**:  You'll need your own UI framework for a fit and finished app.
:::

## Requirements

### CA Mobile API Gateway

To test your app with the MAG server, you need:
   - CA API Gateway 9.3 
   - OTK 4.2
   - CA Mobile API Gateway 4.1 

#### App configuration file   

**If you have an Administrator...**
Easy. Just tell your Admin which Mobile SDK libraries that you need for your app. Then, ask your Admin for the app configuration file (called msso_config.json), which handles communication between the Mobile SDK and MAGs. (You'll add it to your project in later steps.)

**If you ARE the Administrator...**

Complete these tasks: 
- Install and configure the [CA Mobile API Gateway (MAG)](https://docops.ca.com/mag) server and [OAuth Toolkit](https://docops.ca.com/otk)
- [Prepare devices and apps for developers](https://docops.ca.com/mag)
- [Export MAG Configuration from OAuth Manager](https://docops.ca.com/mag)

**Sample msso_config.json file**

This a valid msso_config.json file exported from a MAG.

```json
{
    "server":
    {
        "hostname": "gatewayhostname.example.com",
        "port": 8443,
        "prefix": "",
        "server_certs":
        [
            [
                "-----BEGIN CERTIFICATE-----","MIIDADCCAeigAwIBAgIIW3j/9QFwgk8wDQYJKoZIhvcNAQEMBQAwHjEcMBoGA1UEAxMTbWF0LWRl","=","-----END CERTIFICATE-----"
            ]
        ]
    },
    
    "mag":
    {
        "system_endpoints":
        {
            "device_register_endpoint_path": "/connect/device/register",
            "device_remove_endpoint_path": "/connect/device/remove",
            "client_credential_init_endpoint_path": "/connect/client/initialize"
        },
        
        "oauth_protected_endpoints":
        {
            "enterprise_browser_endpoint_path": "/connect/enterprise/browser",
            "device_list_endpoint_path": "/connect/device/list"
        },
        
        "mobile_sdk":
        {
            "sso_enabled": true,
            "location_enabled": true,
            "location_provider": "network",
            "msisdn_enabled": true,
            "enable_public_key_pinning": false,
            "trusted_public_pki":false,
            "trusted_cert_pinned_public_key_hashes" :[],
            "client_cert_rsa_keybits": 1024
        },
        
        "ble":
        {
            "msso_ble_service_uuid":"980c2f36-bde3-11e4-8dfc-aa07a5b089db",
            "msso_ble_characteristic_uuid":"980c34cc-bde3-11r6-8dfc-aa07a5b093db",
            "msso_ble_rssi": -35
        }
    },
    
    "oauth":
    {
        "client":
        {
            "organization": "Example Organization Inc.",
            "description": "Example App",
            "client_name": "ExampleApp",
            "client_type": "confidential",
            "registered_by": "ExampleUser",
            "client_ids":
            [
                {
                    "client_id": "819455f6-9a7e-4ee0-b159-f85b25758112",
                    "client_secret":"",
                    "scope": "openid msso phone profile address email",
                    "redirect_uri": "https://ios.ssosdk.ca.com/ios",
                    "environment": "iOS",
                    "status": "ENABLED",
                    "registered_by": "ExampleUser"
                }
            ]
        },
        
        "system_endpoints":
        {
            "authorization_endpoint_path": "/auth/oauth/v2/authorize",
            "token_endpoint_path": "/auth/oauth/v2/token",
            "token_revocation_endpoint_path": "/auth/oauth/v2/token/revoke",
            "usersession_logout_endpoint_path": "/connect/session/logout",
            "usersession_status_endpoint_path": "/connect/session/status"
        },
        
        "oauth_protected_endpoints":
        {
            "userinfo_endpoint_path": "/openid/connect/v1/userinfo"
        }
    },

    "custom":
    {
        "oauth_demo_protected_api_endpoint_path":"/oauth/v2/protectedapi/foo",
        "mag_demo_products_endpoint_path":"/protected/resource/products"
    }
}

```
                                                 
## Get Started Documentation

The best way to get the lastest Xamarin Mobile SDK libraries is to use the NuGet dependency manager, which is embedded in Visual Studio. To get started with your app:

- [Mobile SDK for Xamarin Android Guide](https://github.com/CAAPIM/Xamarin-MAS-Foundation/blob/DocEdits/Guides/Android/ANDROID_GUIDES.md)
- [Mobile SDK for Xamarin iOS Guide](https://github.com/CAAPIM/Xamarin-MAS-Foundation/blob/DocEdits/Guides/iOS/IOS_GUIDES.md)

If you do not have Visual Studio, go to: [Get MASFoundation for Xamarin on NuGet](https://www.nuget.org/packages), and search for: **MASFoundation.Xamarin**.

## API Reference 
- [Mobile SDK for Xamarin Android API Reference](http://mas.ca.com//xamarin-android/1.7.00/sdk/)
- [Mobile SDK for Xamarin iOS API Reference](http://mas.ca.com//xamarin-ios/1.7.00/sdk/)

## License

Copyright (c) 2016 CA. All rights reserved.

This software may be modified and distributed under the terms
of the MIT license. See the [LICENSE][license-link] file for details.

 [license-link]: /LICENSE
 [mag]: https://docops.ca.com/mag
 [mas.ca.com]: http://mas.ca.com/
 [docs]: http://mas.ca.com/docs/
 [StackOverflow]: http://stackoverflow.com/questions/tagged/massdk
 [download]: https://github.com/CAAPIM/iOS-MAS-Foundation/archive/master.zip
 [contributing]: /CONTRIBUTING
 [license-link]: /LICENSE
 [prerequisites]: http://mas.ca.com/docs/ios/1.6.10/guides/#prerequisites
 [agreement-link]: /CA-Beta-Pre-Release-Agreement
