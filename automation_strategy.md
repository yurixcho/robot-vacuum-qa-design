# 4) Automation Strategy

## Hardest parts to automate

The most difficult parts of this setup flow to automate are the ones that depend on real world conditions rather than pure software logic.

WiFi provisioning is the biggest challenge. It involves Bluetooth or AP handoff, timing issues, and real network variability that is hard to reproduce consistently.

Firmware updates are another risky area, especially when reboots happen in the middle of setup. These timing issues can leave the system in awkward intermediate states that are difficult to recover from.

Physical interactions are also hard to automate. Things like placing the robot on the dock, removing the bin, or lifting the robot usually require hardware involvement or indirect signals.

## Approach

In practice, I would use a layered approach and avoid relying too heavily on full end to end tests.

At the bottom layer, I would focus on API or SDK level tests to validate the setup state machine. These tests are fast, stable, and good for covering error handling and edge cases without needing real hardware.

On top of that, I would rely on a robot simulator or hardware in the loop setup to exercise provisioning states, firmware update behavior, and reboot scenarios. This makes it possible to reproduce timing related issues in a controlled way.

Finally, I would keep a small set of end to end tests running on real robots. These would act as smoke tests to catch major regressions, but I would avoid scaling this too much since hardware tests are slow and expensive to maintain.

## Network related testing

To make network failures reproducible, I would use a controlled access point setup where network conditions can be changed intentionally. This makes it possible to test scenarios like unsupported networks, weak signal, dropped connections, or captive portals in a repeatable way.

Adding artificial latency or packet loss during provisioning is also useful for exposing timing issues that are otherwise hard to hit reliably.

## Physical signals and observability

Wherever possible, I would avoid relying on camera or vision based checks. These tend to be fragile and slow. Instead, I would prefer using robot telemetry and software signals to confirm physical states, such as whether the robot believes it is docked or charging.

Good observability is critical for automation. Each major setup step should produce a clear and consistent signal that indicates success or failure. Without this, even well written automated tests will become flaky very quickly.

