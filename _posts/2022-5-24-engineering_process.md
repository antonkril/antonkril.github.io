---
layout: post
title: Engineering Process
---

## Dev Environments

1. Local development environment SHOULD be as close as possible to production environment
1. Every service MUST be containerized. Dockerfile should be stored in service repository

## Repositories

1. Every service SHOULD live in a separate repository
1. Every repository MUST have a README.md describing
   - Code purpose
   - Usage examples
   - Configuration options
   - For repositories contaning services - installation steps
1. Every repository containing a service should have Dockerfile recreating the production environment for the service
1. Libraries should only be extracted to separate repositories if they are used by more than one service

## Migrations

1. Every significant refactoring that requires a whole-system migration MUST start with a design document shared with the team.
1. Every code migration should start by adding a rule/lint that forces all new code to be written in the new way

## Artifacts

1. Vision document describes the desired state of the system. It includes
   - the goal of the system
   - intended customers and their needs
   - supported scenarios
   - non-functional requirements
1. Strategy document describes how the vision should be implemented
