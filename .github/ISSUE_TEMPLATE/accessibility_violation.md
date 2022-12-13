name: Accessibility Violation
description: Document an accessibility violation to be fixed
title: "[A11Y]: "
labels: ["a11y"]
assignees:
  - ''
body:
  - type: markdown
    attributes:
      value: |
        Thanks for taking the time to inform us about this accessiblity issue!
  - type: textarea
    id: short-desc
    attributes:
      label: What happened?
      description: Please tell us briefly what the issue was
      placeholder: Tell us what you see!
      value: "I found an accessiblity issue!"
    validations:
      required: true
  - type: dropdown
    id: impact
    attributes:
      label: Impact
      description: What is the impact of the violation?
      options:
        - BLOCKER (Default)
        - CRITICAL
        - SERIOUS
        - MODERATE
        - MINOR
    validations:
      required: true
  - type: dropdown
    id: successcriteria
    attributes:
      label: Success Criteria
      description: What WCAG Success Criteria best matches this violation?
      options:
        - 1.1.1 Non-text Content
        - 1.2.1 Audio-only and Video-only (Prerecorded)
        - 1.2.2 Captions (Prerecorded)
        - 1.2.3 Audio Description or Media Alternative (Prerecorded)
        - 1.2.4 Captions (Live)
        - 1.2.5 Audio Description (Prerecorded)
        - 1.2.6 Sign Language (Prerecorded)
        - 1.2.7 Extended Audio Description (Prerecorded)
        - 1.2.8 Media Alternative (Prerecorded)
        - 1.2.9 Audio-only (Live)
        - 1.3.1 Info and Relationships
        - 1.3.2 Meaningful Sequence
        - 1.3.3 Sensory Characteristics
        - 1.3.4 Orientation
        - 1.3.5 Identify Input Purpose
        - 1.3.6 Identify Purpose
        - 1.4.1 Use of Color
        - 1.4.2 Audio Control
        - 1.4.3 Contrast (Minimum)
        - 1.4.4 Resize text
        - 1.4.5 Images of Text
        - 1.4.6 Contrast (Enhanced)
        - 1.4.7 Low or No Background Audio
        - 1.4.8 Visual Presentation
        - 1.4.9 Images of Text (No Exception)
        - 1.4.10 Reflow
        - 1.4.11 Non-text Contrast
        - 1.4.12 Text Spacing
        - 1.4.13 Content on Hover or Focus
        - 2.1.1 Keyboard
        - 2.1.2 No Keyboard Trap
        - 2.1.3 Keyboard (No Exception)
        - 2.1.4 Character Key Shortcuts
        - 2.2.1 Timing Adjustable
        - 2.2.2 Pause, Stop, Hide
        - 2.2.3 No Timing
        - 2.2.4 Interruptions
        - 2.2.5 Re-authenticating
        - 2.2.6 Timeouts
        - 2.3.1 Three Flashes or Below Threshold
        - 2.3.2 Three Flashes
        - 2.3.3 Animation from Interactions
        - 2.4.1 Bypass Blocks
        - 2.4.2 Page Titled
        - 2.4.3 Focus Order
        - 2.4.4 Link Purpose (In Context)
        - 2.4.5 Multiple Ways
        - 2.4.6 Headings and Labels
        - 2.4.7 Focus Visible
        - 2.4.8 Location
        - 2.4.9 Link Purpose (Link Only)
        - 2.4.10 Section Headings
        - 2.5.1 Pointer Gestures
        - 2.5.2 Pointer Cancellation
        - 2.5.3 Label in Name
        - 2.5.4 Motion Actuation
        - 2.5.5 Target Size
        - 2.5.6 Concurrent Input Mechanisms
        - 3.1.1 Language of Page
        - 3.1.2 Language of Parts
        - 3.1.3 Unusual Words
        - 3.1.4 Abbreviations
        - 3.1.5 Reading Level
        - 3.1.6 Pronunciation
        - 3.2.1 On Focus
        - 3.2.2 On Input
        - 3.2.3 Consistent Navigation
        - 3.2.4 Consistent Identification
        - 3.2.5 Change on Request
        - 3.3.1 Error Identification
        - 3.3.2 Labels or Instructions
        - 3.3.3 Error Suggestion
        - 3.3.4 Error Prevention (Legal, Financial, Data)
        - 3.3.5 Help
        - 3.3.6 Error Prevention (All)
        - 4.1.1 Parsing
        - 4.1.2 Name, Role, Value
        - 4.1.3 Status Messages
    validations:
      required: true
  - type: textarea
    id: reproduction-steps
    attributes:
      label: How did you find this issue?
      description: Provide clear steps for how to reproduce this issue.
      placeholder: Tell us how you found this issue!
      value: ""
    validations:
      required: true
  - type: textarea
    id: actual-outcome
    attributes:
      label: What was the unexpected behaviour that causes the issue?
      description: Please describe what behaviors are causing the accessbility issue
      placeholder: Tell us what you see!
      value: ""
    validations:
      required: true
  - type: textarea
    id: actual-behiavor
    attributes:
      label: What should have happened instead?
      description: Please provide us with the desired outcome of this issue
      placeholder: Give us help in how to fix this issue!
      value: ""
    validations:
      required: true
  - type: input
    id: auditorid
    attributes:
      label: Auditor Link
      description: If manual issue, provive the link to Auditor Test Run Issue
      placeholder: https://axeauditor.dequecloud.com/
    validations:
      required: false
  - type: textarea
    id: element
    attributes:
      label: Element Source Code
      description: Please copy and paste relevant element source. This will be automatically formatted into code, so no need for backticks.
      render: javascript
    validations:
      required: false
  - type: textarea
    id: screenshots
    attributes:
      label: Links to Screenshots
      description: Please provide links to screnshots
    validations:
      required: false
  - type: checkboxes
    id: extras
    attributes:
      label: 'Additional Context'
      description: 'Mark any and all checkboxes that apply'
      options:
        - label: Found during VPAT
        - label: Found using NVDA
        - label: Found using Chrome Screen Reader
        - label: Found using custom configurations
  - type: checkboxes
    id: terms
    attributes:
      label: Code of Conduct
      description: By submitting this issue, you agree to follow our [Code of Conduct](https://example.com)
      options:
        - label: I agree to follow this project's Code of Conduct
          required: true