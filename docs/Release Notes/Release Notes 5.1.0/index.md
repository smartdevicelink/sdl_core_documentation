# SDL Core 5.1.0 Release Notes

## Supported Specifications
- SDL Mobile RPC Spec: [Version 5.1.0](https://github.com/smartdevicelink/rpc_spec/releases/tag/5.1.0)
- SDL Protocol Spec: [Version 5.2.0](https://github.com/smartdevicelink/protocol_spec/releases/tag/5.2.0)

## Implemented Proposals

### [[SDL 0158] Cloud App Transport Adapter](https://github.com/smartdevicelink/sdl_core/issues/2215)

Allows SDL Core to communicate with SDL-enabled cloud applications over websocket connections.

Cloud apps are configurable via the policy table. To connect your cloud application, you need to specify several fields in the app policies section of the policy table:
```
            "WebAppID12345" : {
                ...
                "endpoint": "wss://fakesdlwebsocketurl.com:8080",
                "enabled" : true,
                "cloud_transport_type": "WSS"
            }
```
The `endpoint` field includes the URL/IP and port which SDL Core can connect to in order to communicate with your cloud application.

The `enabled` field determines whether this cloud app appears on the HMI. When set to true, this cloud app will be included in the HMI RPC "UpdateAppList". Selecting this app when it appears on the HMI will result in Core attempting to connect to the specified endpoint. Upon a successful connection, the app will be registered and brought to the foreground.

The `cloud_transport_type` field is used to specify the type of connection SDL Core will use to connect to your cloud application. Currently SDL Core supports two values for this field (`WS` and `WSS`), but the cloud app transport adapter can be configured to incorporate other transport types as well. The `WS` transport type is intended only for testing and development purposes. Any application in a production environment should use a secured transport type, such as `WSS`.

```
            "WebAppID12345" : {
                ...
                "certificate" : "-----BEGIN CERTIFICATE-----\n" ...,
                "auth_token" : "ABCD12345",
                "hybrid_app_preference": "MOBILE"
            }
```

The `certificate` field is used for opening a secured websocket connection. 

The `auth_token` field is sent to the cloud application in its StartServiceACK, if present in the policy table. This value is meant to be used by the cloud application to determine which user is logged into this vehicle.

The `hybrid_app_preference` field is used to specify the user's preference for using a cloud app that is also available on the user's phone. For example: when the preference is set to `MOBILE` and the user connects a mobile app while using the same cloud app, the cloud app will unregister and the mobile version will be the only app to be displayed on the app list. Possible values for this field are `MOBILE`, `CLOUD`, and `BOTH`.

### [[SDL 0167] App Services - Media Service](https://github.com/smartdevicelink/sdl_core/issues/2806), [Weather Service](https://github.com/smartdevicelink/sdl_core/issues/2805), and [Navigation Service](https://github.com/smartdevicelink/sdl_core/issues/2814)

Allows apps to advertise services which can be used by the HMI and other SDL connected applications.

The following service types were implemented in this release: `MEDIA`, `WEATHER`, and `NAVIGATION`

Services that an application wants to publish must be declared in the app policies section of the policy table:
```
            "SDLSuperApp12345": {
                ...
                "app_services": {
                    "MEDIA": {
                        "service_names": ["SDL Music", "App Music"],
                        "handled_rpcs": [{"function_id": 41}]
                        },
                    "NAVIGATION": {
                        "service_names": ["SDL Navigation", "App Navigation"],
                        "handled_rpcs": [{"function_id": 39}]                    
                    }
                }
            }
```

An app service can be published by sending a `PublishAppService` RPC with one of these declared service types. Both the HMI and other connected applications can then query your service for data using the `GetAppServiceData` RPC, and any updates to this data can be published using the `OnAppServiceData` RPC. 

The `PerformAppServiceInteraction` is a generic RPC which can be sent by an app consumer to request custom actions on your service independent of existing SDL messages. In order to support these custom actions, a predetermined API should be published separately from the SDL project to potential consumers.

In addition, the `handled_rpcs` field can be used to define which RPCs can be handled by your service (such as `SendLocation` for `NAVIGATION` services). If your service is active, such messages will be routed to your application instead of the HMI.

The HMI is able to act as a service provider or consumer through the new `AppService` interface in the HMI_API. This includes the same RPC messages available to mobile applications for app services (`PublishAppService`, `GetAppServiceData`, etc.) as well as several HMI-specific RPCs.

The `AppService.AppServiceActivation` and `AppService.GetAppServiceRecords` RPCs are available to enable the HMI to include a screen where the user can control the active and default services for each service type.

The `AppService.GetActiveServiceConsent` RPC is sent by SDL Core when an application includes `requestServiceActive=true` in a `PerformAppServiceInteraction` request to an app service provider. The HMI is expected to prompt the user to either allow or disallow activation of the service in question, and respond to the RPC according to their choice.

The `BasicCommunication.GetFilePath` RPC is sent by SDL Core when a `GetFile` request is sent by an app service consumer for an embedded provider. The name of the file being retrieved is included in this request, and the HMI is expected to provide the full path to the file in the response to SDL Core. This file name can be provided to the application via the embedded service's `serviceManifest` or `serviceData`, ex. `serviceManifest.serviceIcon`.

## Bug Fixes

- [Genericize vehicle info in hmi_capabilities.json](https://github.com/smartdevicelink/sdl_core/pull/2794)

- [Possible cyclic reference of shared pointers of `Application` class](https://github.com/smartdevicelink/sdl_core/issues/2143)

- [SDL processes Light name values from the default capabilities incorrectly](https://github.com/smartdevicelink/sdl_core/issues/2683)

- [SDL sends UnsubscribeWayPoint request to HMI for App1 when App2 is still subscribed to the WayPoint](https://github.com/smartdevicelink/sdl_core/issues/2862)

- [SDL build fails in case if ENABLE_LOG=OFF or ENABLE_SECURITY=OFF](https://github.com/smartdevicelink/sdl_core/issues/2860)
