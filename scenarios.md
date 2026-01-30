# 1) Test Scenarios (High-level)

## S1. Unboxing & basic hardware readiness (from a software point of view)
- Robot powers on and reaches a setup-ready state
- Dock power is detected and charging state is correctly reported

## S2. Mobile app onboarding & account flow
- First app launch and basic permissions
- Login or signup flow
- User can reach and stay in the “add device” flow without getting stuck

## S3. Pairing & network provisioning
- Device discovery and pairing (e.g. BLE)
- Standard 2.4GHz Wi-Fi provisioning happy path
- Common real world failures: wrong password, unsupported band, hidden SSID, weak signal, captive portal
- IP assignment, internet reachability, and cloud connectivity confirmed

## S4. Firmware check/update during setup
- No-update-required path
- Update available path (download, apply, reboot)
- Update blocked when battery is too low

## S5. Basic configuration
- Region, language, and timezone are saved correctly
- Reasonable default cleaning settings are applied

## S6. First cleaning run
- User can start the first run successfully
- Map creation begins and completes
- Cleaning finishes or returns to dock
- Run summary is generated and stored

## S7. Recovery and “things going wrong”
- App is killed or backgrounded during setup
- Network drops at bad timing (especially during binding)
- Robot reboots during provisioning or firmware update
- Two phones try to set up the same robot at the same time

## S8. Safety-related software warnings during setup
- Missing bin, brush jam, cliff sensor trigger, robot lifted (if supported)



