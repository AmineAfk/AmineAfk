# Atrium — clinic operations prototype

[Back to profile](../README.md)

**Focus:** Supabase/PostgreSQL, enquiry data, prioritisation, deduplication, audit logging and workflow metrics.

## Problem

Incoming administrative enquiries need a clear queue, a status and a record of what happened. A receptionist should be able to identify outstanding work and review previous actions without relying on memory.

## My contribution

- Built a responsive French-language receptionist inbox with queue and detail views.
- Implemented message ingestion, phone-based contact deduplication and idempotency using external message identifiers.
- Added status and urgency controls, internal reply notes and queue metrics.
- Logged workflow changes in an audit trail.
- Implemented loading, empty and error states and deployed the prototype to Vercel.

## Data flow

Manual/test message → contact and enquiry records → receptionist inbox → human action → audit log and metrics.

Supabase/PostgreSQL stores the workflow data. The interface groups incoming work into a queue and shows the selected enquiry's details and notes.

## Design trade-off and current scope

Idempotent ingestion avoids creating duplicate work when an external message is retried. Contact deduplication keeps related enquiries connected, while audit logging makes status changes inspectable.

The current implementation uses manual or simulated input. WhatsApp integration, authentication and LLM-based structuring are not part of this prototype. It handles administrative workflow and makes no diagnostic or treatment decisions. No clinic adoption or patient outcome is claimed.
