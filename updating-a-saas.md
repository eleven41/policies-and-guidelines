# Updating a SaaS

This document describes policies and guidelines for updating a SaaS to version `n`. The purpose of these guidelines is to promote "zero downtime" updates.

## Requirements

### 1. Database Changes

A. All schema changes for sofware version `n` must be compatible with software version `n - 1`.

### 2. Software Changes

A. All software changes must be compatible with data created by version `n - 1`.

## Performing the Update to Version `n`

1. Update the database schema first. Requirement 1A ensures version `n - 1` will continue to function correctly until the software is updated to version `n`.

2. Update any software components that will not promote the creation of new data using schema version `n`.

3. Update non-customer-facing components.

4. Update customer-facing components last.

## Migrating data from one form to another

1. Add new data to database schema
2. Update software to write old and new data to database, read new data, but only use old data
3. Migrate old data to new data for legacy records
4. Update software to use new data, ignoring old data
5. Update software to stop reading and writing old data
6. Remove old data from schema

