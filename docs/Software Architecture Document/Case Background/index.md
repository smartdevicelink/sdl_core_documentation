## 2.  Case Background

### 2.1. System Context, Mission and Scope

SmartDeviceLink system is developed to serve as a proxy between vehicle Head Unit sub-system and an Application that runs at any of compatible Mobile Devices:

-   A Mobile Device might be connected via USB, Bluetooth or Wi-Fi to the HU;
-   The Application should be the SDL-enabled one.

The Mobile Device might be any of:
-   Smartphone devices
-   Tablet PCs

with operational system:
-   iOS
-   Android.

The SDL system allows Application to:
-   Use vehicle HMI: VR, TTS, buttons (physical and touch-screen), vehicle display, audio system. etc.
-   Retrieve Vehicle Data (seat belt position, transmission shift lever position, airbag status, etc.).

### 2.2. Business Goals

The purpose of the project is to develop component of SmartDeviceLink Core by adding new features required by the SDL Consortium.

### 2.3. Significant Driving Requirements

The requirements are listed in the table below and ordered by descending of their significance from architectural solution point of view.

| \# | **Driving Requirement Description** |
|----|-------------------------------------|
| 1. | System has to be POSIX-compliant to be easily ported on all POSIX standardized OSs. |
| 2. | Transport for communication between Mobile Application and SDL system must be implemented and easily changed, replaced or added if required |
| 3. | APIs for communication between Mobile Application and SDL system described in appropriate documents have to be fully supported by the system. |
| 4. | There has to be relatively easy way to port existing HMI Modules (such as UI, VR, TTS, etc.) to work with SDL system. |
| 5. | APIs for communication between SDL system and HMI Modules have to be fully described in appropriate document and fully supported by SDL system. |
