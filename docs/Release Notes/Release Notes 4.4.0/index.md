# SDL Core 4.4.0 Release Notes

## Implemented Proposals

[System Capabilities Query](https://github.com/smartdevicelink/sdl_evolution/blob/master/proposals/0055-system_capabilities_query.md) - Implementation of a new RPC which allows an app to query the capabilities of a specific component (i.e. video streaming, remote control) within a given integration of SDL Core.

[Constructed Payloads](https://github.com/smartdevicelink/sdl_evolution/blob/master/proposals/0052-constructed-payloads.md) - Addition of constructed payloads for control (non-RPC type) packets. These payloads allow for control packets to be more descriptive without using the overhead needed by an RPC message. The feature has been implemented using the [BSON standard](http://bsonspec.org/spec.html) through use of the [bson_c_lib](https://github.com/smartdevicelink/bson_c_lib/releases). This includes the introduction of protocol version 5, versions prior to this do not support this feature.

[Control Frame Payloads v1.0.0](https://github.com/smartdevicelink/sdl_evolution/blob/master/proposals/0078-control_frame_payloads_v1_0_0.md) - Introduced specific parameters that will be sent with a control frame's constructed payload. This is part of the introduction of protocol version 5, versions prior to this do not support this feature.

[Support Indian English and Thai](https://github.com/smartdevicelink/sdl_evolution/blob/master/proposals/0060-support-indian-english-thai.md) - Adds the possibility to support languages `English - India` and `Thai - Thailand`.

[Support For Additional Languages](https://github.com/smartdevicelink/sdl_evolution/blob/master/proposals/0076-Support-For-Additional-Languages.md) - Adds the possibility to support 8 new languages. 

[Mobile Projection](https://github.com/smartdevicelink/sdl_evolution/blob/master/proposals/0031-mobile-projection.md) - Defines new AppHMIType `PROJECTION`. This AppHMIType allows an app to use the same video streaming technologies as a navigation app. 

[Gesture Cancellation](https://github.com/smartdevicelink/sdl_evolution/blob/master/proposals/0049-touch-cancellation.md) - Addition of a `CANCEL` element to the TouchType Enum used during an OnTouchEvent RPC. 

[Add Video Streaming Capabilities](https://github.com/smartdevicelink/sdl_evolution/blob/master/proposals/0058-video-streaming-capabilities.md) - Allows core to notify the proxy of the HMI's video streaming capabilities. This addition also includes a video format negotiation procedure that uses a combination of RPC and constructed payload messages. 

[Adding Metadata Types](https://github.com/smartdevicelink/sdl_evolution/blob/master/proposals/0073-Adding-Metadata-Types.md) - Add `metadataTags` parameter to the Show RPC, as well as the new types `MetadataTag` and `MetadataType`. These additions allow for a more detailed description of the main field strings sent during a Show RPC request. 

[Human Interface Device Support](https://github.com/smartdevicelink/sdl_evolution/blob/master/proposals/0075-HID-Support-Plug-in.md) - Implementation of the `SendHapticData` RPC. This RPC sends the HMI an array of rectangle coordinates for focusable elements used during video streaming. 

[Remote Control Baseline](https://github.com/smartdevicelink/sdl_evolution/blob/master/proposals/0071-remote-control-baseline.md) - Implementation of a new core plugin/functional module `RemoteControl`. This feature includes a set of RPCs that the proxy may use to control certain aspects of the HMI's climate and radio modules. Changes also include additions to the `GetSystemCapability` RPC and policy configurations.  

[Update Mobile API Mandatory Flag](https://github.com/smartdevicelink/sdl_evolution/blob/master/proposals/0023-update-mobile-api-mandatory-flag.md) - Update formatting of `MOBILE_API.xml` to include the `mandatory` flag on all parameters. 

## Bug Fixes

### Video Streaming Related
 - [Core still sends out deprecated Service Data ACK frames](https://github.com/smartdevicelink/sdl_core/issues/1768)
 - [Proper Cleanup for the StreamerAdapter class](https://github.com/smartdevicelink/sdl_core/issues/1701)
 - [SDL does not send StopStream/StopAudioStream to HMI after unregistering app during streaming](https://github.com/smartdevicelink/sdl_core/issues/1010)

### Connection Related
 - [TransportManager that incorrectly deletes a connection object within a C++ map iterator loop](https://github.com/smartdevicelink/sdl_core/issues/1663)
 - [Core cannot find App via BT ](https://github.com/smartdevicelink/sdl_core/issues/1753)
 - [Connection List Lock is Not Released](https://github.com/smartdevicelink/sdl_core/issues/1515)
 - [Invalid memory access in websocket_handler](https://github.com/smartdevicelink/sdl_core/issues/1686)

### Policy Related 
 - [SDL does not set "timeout" for OnSystemRequest with url](https://github.com/smartdevicelink/sdl_core/issues/1021)
 - [Policies Manager does not revert the Local Policy Table to the Preload Policy Table upon FACTORY Rese](https://github.com/smartdevicelink/sdl_core/issues/1024)
 - [SDL does not write UserFriendlyMessages to DB](https://github.com/smartdevicelink/sdl_core/issues/1027)
 - [SDL dos not select url from PT for specified appID during GetURLs request.](https://github.com/smartdevicelink/sdl_core/issues/961)
 - [PM should verify that "seconds\_between\_retries" array has maxlength 5](https://github.com/smartdevicelink/sdl_core/issues/962)
 - [SDL does not apply url from PT for specified appID for OnSystemRequest](https://github.com/smartdevicelink/sdl_core/issues/985)
 - [PM doesn't validate the size of section "default" in "endpoints" of Policy Table](https://github.com/smartdevicelink/sdl_core/issues/978)
 - [Policy table can't be loaded when RPCs added in functional_group is greater than 50.](https://github.com/smartdevicelink/sdl_core/issues/968)
 - [PT is considered as valid with no items in "groups" sub-section from "default"](https://github.com/smartdevicelink/sdl_core/issues/973)


### Documentation
 - [README should not reference "v4tester" application](https://github.com/smartdevicelink/sdl_core/issues/1547)
 - [Create an Issue template for sdl_core](https://github.com/smartdevicelink/sdl_core/issues/397)

### General Fixes
 - [media\_manager\_test fails with EXTENDED_MEDIA_MODE=ON](https://github.com/smartdevicelink/sdl_core/issues/1802)
 - [Memory leak in FromMicToFileRecorderThread](https://github.com/smartdevicelink/sdl_core/issues/1682)
 - [Invalid memory access in FromMicToFileRecorderThread](https://github.com/smartdevicelink/sdl_core/issues/1681)
 - [SDL does not reset the default watchdog timeout of GetWayPoints request if HMI sends OnResetTimeout notification for this request](https://github.com/smartdevicelink/sdl_core/issues/991)
 - [SDL sends BC.UpdateDeviceList with out of upper bound size of deviceList](https://github.com/smartdevicelink/sdl_core/issues/1019)
 - [HashID should not be updated on successful single UI.<RPC> if no UI.IsReady response](https://github.com/smartdevicelink/sdl_core/issues/993)
 - [OpenSDL repo still contains old "generate\_test\_certificates.py" script.](https://github.com/smartdevicelink/sdl_core/issues/1005)
 - [SDL does not send VehicleInfo.GetVehicleData in case HMI responds invalid json](https://github.com/smartdevicelink/sdl_core/issues/1015)
 - [SDL print out CN and serialNumber details of certificates in log.](https://github.com/smartdevicelink/sdl_core/issues/1017)
 - [SDL returns IGNORED instead of UNSUPPORTED_RESOURCE for UnsubscribeButton](https://github.com/smartdevicelink/sdl_core/issues/998)
 - [SDL must respond with INVALID_DATA on SystemRequest that uploads a file containing "../" sequences](https://github.com/smartdevicelink/sdl_core/issues/975)
