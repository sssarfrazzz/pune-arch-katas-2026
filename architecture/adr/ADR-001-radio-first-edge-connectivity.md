# ADR-001: Radio-First Edge Connectivity

## Status

Proposed

## Date

2026-09-16

## Context

The estate is large and has patchy Wi-Fi. Operations Intelligence Platform requires low-cost sensing coverage and resilient local operation.

MQTT-capable hardware devices are the application-layer interface: provisioned estate devices and gateways expose MQTT directly or use MQTT-SN bridged at the radio hub or gateway. The interface applies over the selected LoRaWAN transport.

## Decision

Use private LoRaWAN with two overlapping receiver hubs for Operations Intelligence Platform.

## Alternatives Considered

- Extend Wi-Fi across the estate: rejected as the default because the source identifies patchy coverage and cost constraints.
- Use cellular for every device: not selected; cost, coverage, and power evidence is absent.
- Use one hub: rejected because it creates a visibility failure point.

## Consequences

- Positive: broad low-power coverage and local operation.
- Positive: MQTT provides the required publish/subscribe application-layer interface for telemetry and command traffic over the LoRaWAN transport; MQTT-SN bridging supports constrained radio devices.
- Negative: duty-cycle, congestion, survey, power, and backhaul evidence are required.
- Negative: MQTT broker, gateway, and MQTT-SN bridge conformance, buffering, replay, and command-failure behavior require integration evidence.

## Related Requirements

BR-003; NFR-001; NFR-012; SEC-009.
