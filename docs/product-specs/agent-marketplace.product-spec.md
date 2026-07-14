---
spec_format_version: "0.1"
title: "Agent Marketplace"
artifact_type: "prd"
spec_revision: 1
lifecycle_status: in_review
author: "ProductSpec.io"
created_at: "2026-07-09T00:00:00Z"
updated_at: "2026-07-09T00:00:00Z"
---

## Problem

Automotive dealerships already using Spyne Console who want to improve vehicle merchandising but don't know which AI capability to adopt first.

These users face three major problems:

1. They are unaware of what individual AI agents can do for their inventory.
2. Existing workflows require manual effort, multiple tools, or support from CSMs.
3. They cannot experience an agent before purchasing it, making adoption risky.

As a result, dealers hesitate to install or pay for AI-powered merchandising features, even when those features could immediately improve their inventory quality and listing performance.

## Hypothesis

If dealerships can instantly experience an AI agent using their own inventory before purchasing, they will better understand its value, trust the output, and be significantly more likely to activate and pay for the agent.

Instead of explaining product capabilities through documentation or demos, the marketplace lets users experience the outcome directly.

Expected behavioral changes:

More users click "Try it Free"
Higher demo completion rate
More saved outputs
Higher conversion from demo → paid activation
Increased adoption of single-purpose AI agents

## Customer Truth

Dealerships don't buy AI because it sounds intelligent.

They buy solutions that immediately improve their inventory without increasing operational effort.

Users want to answer simple questions:

What will this do to my inventory?
Will it work with my cars?
How many clicks does it take?
Can I trust the output?
Is the quality worth paying for?

Every additional step before users experience value increases drop-off.

The fastest way to build confidence is allowing users to generate real outputs using their own inventory.

## Solution

The Agent Marketplace introduces installable, single-purpose AI agents inside the Spyne Console.

Each agent focuses on solving one merchandising problem exceptionally well (for example, Custom Car Backgrounds, Text Overlay Generator, Window Sticker Generator).

Every agent follows the same reusable experience:

Open Agent
Try it Free
Inventory detection (IMS / VIN / Website URL)
Guided walkthrough
AI generates output
User saves up to three outputs
Activation prompt
Payment
Agent becomes permanently available

The reusable onboarding shell remains identical across agents, while only the AI workflow changes.

This creates a scalable platform where future agents can be launched with minimal UX redesign.

## Scope

```productspec-scope
in:
  - Agent Marketplace listing and Agent Detail page
  - Detect IMS integration status
  - Auto-fetch inventory for IMS-connected dealerships
  - Manual VIN entry for non-IMS dealerships
  - Website URL submission for inventory scraping
  - Inventory selection (single VIN at a time)
  - Guided interactive product walkthrough with coach marks
  - Live demo using dealership inventory
  - AI-generated output preview
  - Save generated outputs (maximum 3 free saves)
  - Activation prompt before/after free usage limit
  - Payment redirection
  - Agent activation after successful payment
  - Consistent reusable onboarding shell for all marketplace agents
  - Exit and resume flows at every stage
  - Reusable onboarding framework that supports future single-purpose AI agents with minimal UX changes.
out:
  - Team-level or enterprise-wide agent management
  - Agent recommendations based on user behavior
  - Agent ratings and reviews
  - Marketplace search and advanced filtering
  - Usage analytics dashboard
  - Subscription management
  - Invoice history
  - Multiple VIN demo generation
  - Batch inventory processing
  - Sharing generated assets
  - Agent version management
  - Admin approval workflows
cut:
  - Cross-agent workflows
  - Collaboration between dealership users
  - Usage-based billing
  - Agent comparison page
  - Custom onboarding paths per agent
```

## User Experience

https://claude.ai/design/p/9c810c11-147c-4227-8241-93ac093e7623?file=Canvas.dc.html&via=share

## Acceptance Criteria

```productspec-acceptance-criteria
- id: AC-1
  criterion: Agent Discovery: Given a user is logged into the Spyne Console, when they open the Agent Marketplace, then they should be able to discover and open an Agent Detail page.
- id: AC-2
  criterion: Demo Entry: Given the user is on an Agent Detail page, when they click "Try it Free", then the interactive demo should launch without navigating away from the Console.
- id: AC-3
  criterion: IMS Detection: Given the demo starts, when the system checks the dealership configuration, then it should automatically detect whether an IMS integration exists and route the user to the appropriate onboarding flow.
- id: AC-4
  criterion: Inventory Selection: Given the dealership has an IMS connection, when inventory is fetched successfully, then the user should be able to select exactly one VIN for the demo.
- id: AC-5
  criterion: Manual Input: Given the dealership does not have an IMS connection, when the user enters a valid VIN or submits a website URL, then the system should validate the input before proceeding.
- id: AC-6
  criterion: Guided Walkthrough: Given a valid inventory item is selected, when the demo begins, then the user should be guided through the experience using coach marks without requiring external documentation.
- id: AC-7
  criterion: AI Output: Given the walkthrough is completed, when AI processing finishes, then the generated output should be displayed for preview.
- id: AC-8
  criterion: Save Limit: Given a user generates demo outputs, when they save a design, then the system should allow a maximum of three free saved outputs.
- id: AC-9
  criterion: Activation Gate: Given the user has reached the free save limit, when they attempt another save, then the system should prompt them to activate the agent before continuing.
- id: AC-10
  criterion: Payment Flow: Given the user chooses to activate the agent, when they click "Activate Agent", then they should be redirected to the payment flow.
- id: AC-11
  criterion: Exit & Resume: Given the user exits the demo before completion, when they return later, then the system should either restore the last valid state or restart the demo based on the defined product rules.
- id: AC-12
  criterion: Navigation: Given any screen or modal in the onboarding flow, when the user clicks an ingress or exit action, then the destination should be clearly defined with no dead ends or redundant navigation paths.
```

## Adoption

Success depends on reducing friction between discovery and first value.

The marketplace encourages adoption by:

1. Allowing users to experience the product before purchase
2. Using their own inventory instead of sample assets
3. Providing interactive guided walkthroughs
4. Limiting free saves to create a natural upgrade point
5. Keeping all interactions inside the existing Spyne Console
6. Maintaining a consistent onboarding experience across every future agent

Primary adoption metrics:

Try it Free CTR
Demo completion rate
Output save rate
Activation rate
Conversion to paid installation
Repeat usage after activation

## Success Metrics

```productspec-success-metrics
- id: SM-1
  metric: Try it Free CTR (Users who click Try it Free ÷ Users who visit an Agent Detail page)
  target: "≥ 40%"
  window: Within 30 days of launch
- id: SM-2
  metric: Demo Completion Rate (Users reaching AI-generated output ÷ Users who start the demo)
  target: "≥ 80%"
  window: Within 30 days
- id: SM-3
  metric: First Value Time (Median time from clicking Try it Free to first generated output)
  target: "≤ 2 minutes"
  window: Within 30 days
- id: SM-4
  metric: Save Rate (Users who save at least one generated output ÷ Demo completions)
  target: "≥ 70%"
  window: Within 30 days
- id: SM-5
  metric: Activation Conversion (Users who activate the agent ÷ Users who complete the demo)
  target: "≥ 20%"
  window: Within 60 days
- id: SM-6
  metric: Demo Drop-off Rate (Users abandoning before AI output)
  target: "≤ 20%"
  window: Within 30 days
- id: SM-7
  metric: Repeat Usage (Activated users who use the agent again within 7 days)
  target: "≥ 60%"
  window: Within 90 days
```

## Open Questions

Product:
Should every agent use the same reusable onboarding shell?
Should the free save limit always be three, or vary by agent?
Can multiple agents share a common activation flow?

Technical:
What is the expected inventory fetch time for IMS integrations?
Should website scraping run synchronously or asynchronously?
How should failed VIN validation be handled?
Where should demo outputs be temporarily stored?

Business:
Will agents support monthly, annual, or usage-based pricing?
Can enterprises purchase agents at the dealership-group level?

UX:
How should users switch between VIN-based and inventory-based demos without restarting the flow?
