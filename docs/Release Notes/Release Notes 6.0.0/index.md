# SDL Core 6.0.0 Release Notes

## Supported Specifications

- SDL Mobile RPC Spec: [Version 6.0.0](https://github.com/smartdevicelink/rpc_spec/releases/tag/6.0.0)
- SDL Protocol Spec: [Version 5.2.0](https://github.com/smartdevicelink/protocol_spec/releases/tag/5.2.0)

## Completed Features

- [[SDL 0173] Read Generic Network Signal Data](https://github.com/smartdevicelink/sdl_core/issues/2840)

- [[SDL 0211] Service Status Update to HMI](https://github.com/smartdevicelink/sdl_core/issues/2791)

- [[SDL 0207] RPC message protection](https://github.com/smartdevicelink/sdl_core/issues/2816)

- [[SDL 0216] Widget support](https://github.com/smartdevicelink/sdl_core/issues/2918)

- [[SDL 0138] Make 'audioPassThruCapabilities' of HMI an array ](https://github.com/smartdevicelink/sdl_core/issues/2024)

- [[SDL 0179] Pixel density and Scale](https://github.com/smartdevicelink/sdl_core/issues/2319)

- [[SDL 0221] Remote Control - Allow Multiple Modules per Module Type](https://github.com/smartdevicelink/sdl_core/issues/2919)

- [[SDL 0184] Cancel Interaction RPC](https://github.com/smartdevicelink/sdl_core/issues/2533)

- [[SDL 0204] Support running the same app from multiple devices at the same time](https://github.com/smartdevicelink/sdl_core/issues/2763)

- [[SDL 0231] Add Tiles as an Option for Main Menus](https://github.com/smartdevicelink/sdl_core/issues/2925)

- [[SDL 0186] Template Titles](https://github.com/smartdevicelink/sdl_core/issues/2393)

- [[SDL 0177] Alert icon](https://github.com/smartdevicelink/sdl_core/issues/2287)

- [[SDL 0116] Open Menu RPC](https://github.com/smartdevicelink/sdl_core/issues/1937)

- [[SDL 0225] Update Published App Services](https://github.com/smartdevicelink/sdl_core/issues/2911)

- [[SDL 0108] AutoCompleteList](https://github.com/smartdevicelink/sdl_core/issues/1858)

- [[SDL 0224] Navigation Subscription Buttons](https://github.com/smartdevicelink/sdl_core/issues/2917)

- [[SDL 0119] SDL Passenger Mode](https://github.com/smartdevicelink/sdl_core/issues/2134)

- [[SDL 0223] Add Currently Playing Media Image to MediaServiceData](https://github.com/smartdevicelink/sdl_core/issues/2897)

- [[SDL 0115] CloseApplication RPC](https://github.com/smartdevicelink/sdl_core/issues/1931)

- [[SDL 0213] Remote Control - Radio and Climate Parameter Update](https://github.com/smartdevicelink/sdl_core/issues/2793)

- [[SDL 0199] Adding-GPS-Shift-support](https://github.com/smartdevicelink/sdl_core/issues/2639)

- [[SDL 0212] Add Ability to Reuse a SyncFileName for a PutFile](https://github.com/smartdevicelink/sdl_core/issues/2799)

- [[SDL 0246] Add App Services to HMICapabilities](https://github.com/smartdevicelink/sdl_core/issues/2998)

## Completed Bug Fixes/Enhancements

- [Fix/Set mandatory=false for optional response params](https://github.com/smartdevicelink/sdl_core/pull/3052)

- [DialNumber: Update HMI API description to match Mobile API description](https://github.com/smartdevicelink/sdl_core/issues/2408)

- [EmergencyEvent->maximumChangeVelocity data type is incorrect in HMI API](https://github.com/smartdevicelink/sdl_core/issues/2735)

- [SDL crashes while sending OnSystemRequest in case if RPC service is protected](https://github.com/smartdevicelink/sdl_core/issues/2922)

- [Set USB INI Configurations in the .ini](https://github.com/smartdevicelink/sdl_core/issues/2971)

- [Unit test "app_services_commands_test_unity" FAILED](https://github.com/smartdevicelink/sdl_core/issues/2936)

- [Audio Stream cutoff when using pipe streaming](https://github.com/smartdevicelink/sdl_core/issues/2633)

- [Audio stream internal data stream error when using socket streaming](https://github.com/smartdevicelink/sdl_core/issues/2945)

- [Wrong processing of SetDisplayLayout response data](https://github.com/smartdevicelink/sdl_core/issues/1392)

- [Core crash during ignition_off by ATF script execution](https://github.com/smartdevicelink/sdl_core/issues/2859)

- [SDL does not send GENERIC_ERROR in case HMI does NOT respond during <DefaultTimeout>+<RPCs_internal_timeout>](https://github.com/smartdevicelink/sdl_core/issues/1880)

- [Pipe Streaming Thread Blocks Indefinitely](https://github.com/smartdevicelink/sdl_core/issues/3072)

- [SDL is unable to start protected Audio/Video service in multi-transport configuration](https://github.com/smartdevicelink/sdl_core/issues/3059)

- [SDL sends UPDATE_NEEDED even if app is not registered yet](https://github.com/smartdevicelink/sdl_core/issues/2995)

- [Rare SDL Core crash upon termination](https://github.com/smartdevicelink/sdl_core/issues/2787)

- [SDL respond with not supported resultCode = UNSUPPORTED_RESOURCE for ChangeRegistration](https://github.com/smartdevicelink/sdl_core/issues/1694)

- [Remove unused ShowCustomForm HMI RPC](https://github.com/smartdevicelink/sdl_core/issues/2717)

- [ExpectPolicyTableReset unit test is unstable](https://github.com/smartdevicelink/sdl_core/issues/3098)

- [Fix log severity level and various typos](https://github.com/smartdevicelink/sdl_core/issues/2694)

- [Provide operation result to function file_system::CreateDirectory](https://github.com/smartdevicelink/sdl_core/issues/2695)

- [Application does not retrieve subscriptions to app service after resumption ](https://github.com/smartdevicelink/sdl_core/issues/3096)
