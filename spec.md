---
title: club-protocol-v1
description: On-chain protocol for collective identity and curation.
author: Kevin Neaton
status: Draft
---

## Abstract

The Club Protocol v1 provides a modular set of smart contract implementations
for collective management of a shared identity and content with a focus on
curation-based projects. Permissionless and gas-efficient factory contracts are
used to deploy minimal, non-upgradeable, proxies of the provided smart contract
implementations.

This spec is modelled after the [Sound Protocol 2.0 spec][sound-protocol-spec].

## Contracts & interfaces

TODO

## Modules

TODO

### Authority

- Authority modules must implement the `Authority` interface defined in
[solmate/src/auth/Auth.sol][solmate-auth].

#### ClubAuthority.sol

- Target agnostic role-based authority designed to enable flexible management
  of roles and capabilities within a club.
- Based primarily on `RolesAuthority` and `MultiRolesAuthority`.
- Option to grant virtual roles based on token ownership.
- Option to define target-specific capability overrides.
- By default, each club is deployed with a single `ClubAuthority` proxy which
  is used by the club and all of it's deployed contracts.

## Libs

### Auth.sol

[solmate/src/auth/Auth.sol][solmate-auth]

- Modular auth pattern distinct from application logic.
- Every ownable contract in the club-protocol must inherit the solmate
  [Auth.sol][solmate-auth] contract to enable modular auth management.

### RolesAuthority

[solmate/src/auth/authorities/RolesAuthority.sol][solmate-rolesauthority]

- Target aware role-based authority implementation.
- Used as the basis for the `ClubAuthority` above.

### MultiRolesAuthority

[solmate/src/auth/authorities/MultiRolesAuthority.sol][solmate-multirolesauthority]

- Target agnostic role-based authority implementation.
- Used as the basis for the `ClubAuthority` above.

## Secutity model

TODO

[sound-protocol-spec]: https://github.com/soundxyz/sound-protocol/blob/2be55b0e605af6c9b2b744a10fc7199bbe6e1752/spec.md
[solmate-auth]: https://github.com/transmissions11/solmate/blob/main/src/auth/Auth.sol
[solmate-rolesauthority]: https://github.com/transmissions11/solmate/blob/main/src/auth/authorities/RolesAuthority.sol
[solmate-multirolesauthority]: https://github.com/transmissions11/solmate/blob/main/src/auth/authorities/MultiRolesAuthority.sol
