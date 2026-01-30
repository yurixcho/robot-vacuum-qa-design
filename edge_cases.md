# 2) Critical Edge Case Challenge

These are edge cases that tend to cause real problems during setup because parts of the system succeed while others fail. They usually involve the robot, the app, the network, and the backend getting out of sync.

## EC-1: Network drops during account binding

In this case, local pairing and WiFi setup succeed, but the network drops before the device is fully bound to the user account.

The main risk here is ending up with a half-registered or duplicate device. When the user retries setup after the network comes back, the app should recover cleanly and finish binding. After recovery, there should only be a single device associated with the account and the robot should be fully usable.

## EC-2: Robot reboots during provisioning because of a firmware update

Here the robot starts provisioning, but a firmware update triggers a reboot before setup finishes. This can interrupt credential transfer and cause the app to lose its session with the robot.

The expected behavior is that the app clearly transitions into an updating or waiting state instead of failing silently. After the reboot, the robot should return to a predictable setup state and allow the user to continue setup without requiring a factory reset.

## EC-3: Two phones try to set up the same robot at the same time

This can happen in a real household when more than one person tries to help with setup.

The robot should allow only one active setup flow at a time. If a second phone attempts setup, it should be blocked with a clear message indicating setup is already in progress. Once the first setup finishes, is cancelled, or times out, the second phone should be able to proceed. At no point should duplicate device records be created.

## EC-4: WiFi network connects but has no internet access

Some networks appear connected locally but block internet access, such as captive portals.

In this case, the robot may successfully join the WiFi network but still be unable to reach backend services. The app should detect this and stop setup from proceeding further. The user should be given clear guidance to switch networks or complete the required network steps before continuing.

