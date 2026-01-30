# Robot Vacuum Setup Test Design

This repo contains test scenarios and detailed test cases for the initial setup of a robot vacuum cleaner, starting from unboxing and ending with the first cleaning run.

This was done as part of an interview assignment. The focus here is not on guessing exact product behavior, but on showing how I would think through setup testing and automation when details are limited.

---

## What’s covered

The setup flow I’m testing includes:

- Powering on the robot and basic hardware readiness
- Dock detection and charging
- App onboarding and login
- Device discovery and pairing
- WiFi provisioning
- Firmware updates during setup
- Basic configuration
- First cleaning run, including map creation and run history

---

## Repo structure

- `scenarios.md`  
  High level scenarios that outline what areas of setup should be tested.

- `test_cases.csv`  
  The main deliverable.  
  This contains detailed test cases with step by step actions, expected results, and validation signals describing how each result could be checked by automation.

- `edge_cases.md`  
  A set of setup edge cases that tend to cause real issues in the wild, especially when the robot, app, network, and backend get out of sync.

- `prioritization.md`  
  Notes on which test cases I would automate first if time was limited, and why.

- `automation_strategy.md`  
  How I would approach automating this setup flow in practice, including what is hardest to automate and how I would deal with it.

---

## Assumptions

The prompt does not include specific implementation details like APIs, error codes, or telemetry fields.

To keep the test cases concrete and automatable, expected results are written in terms of observable behavior. This could be robot state, app state, or backend outcomes. The names used are illustrative and meant to represent the type of signal an automated test would assert on, not exact production field names.

---

## Intent

This is a test design exercise, not a full automation project.

The goal is to show how I think about setup flows, failure cases, and automation constraints in a realistic way.

