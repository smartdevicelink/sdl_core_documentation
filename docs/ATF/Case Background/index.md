## 2.  Case Background

### 2.1. System Context, Mission and Scope

ATF is a C++/Lua framework for SDL automated black-box testing.
It provides high- and low-level API for mobile applications and/or HMIs emulation.

ATF *core* lua-scripts provides API for SDL easy manipulation:
  - Start and stop SDL
  - Emulates websocket HMI conection, HMI interfaces registration and subscription
  - Emulates establishing a TCP mobile connection and SDL protocol session
  - Expectation HMI and mobile RPC from SDL
  - Expectation extensions with setting up timeouts, call-chains and fields validation
  - SDL messages auto-validation 

### 2.2. Business Goals

ATF system allows to automatize SDL regression testing and decreasing functional end regression costs.
ATF with a smoke tests scripts suite provide [Continuous testing](https://en.wikipedia.org/wiki/Continuous_testing) and [Continuous delivery](https://en.wikipedia.org/wiki/Continuous_delivery) for SDL open-source developers and integrators.

### 2.3. Significant Driving Requirements

The requirements are listed in the table below and ordered by descending of their significance from architectural solution point of view.

| \# | **Driving Requirement Description** |
|----|-------------------------------------|
| 1. | ATF has to be POSIX-compliant to be easily ported on all POSIX standardized OSs. |
| 2. | Script language need to be used as a main-tool for simplification. |
| 3. | ATF shall provide a High-level API for SDL manipulation. |
