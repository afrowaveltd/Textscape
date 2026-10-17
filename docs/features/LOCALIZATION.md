# Localization and accessibility

**Status:** design requirement from day one.

Textscape documentation and primary planning language are English, while the app is designed for many locales, including Czech. Do not hard-code user-facing English strings in UI components, notifications, error messages, plugin catalogs, prompts or help text.

## Requirements

- Locale-aware resources, placeholders, dates/times, number formatting, plural forms, directionality where supported, collations and input methods.
- Safe placeholder interpolation and validation across translations; translation must not execute template syntax or silently remove required variables.
- Plugin manifests can bundle translated names/descriptions/help with an explicit fallback language; prompt source texts and versions must remain inspectable as actual executed material, not misleading translations.
- User can override language per profile and optionally use text translation plugin, without making network AI translation a runtime dependency.
- Every action has a non-emoji/ASCII path; color alone must not communicate security status; mouse functionality must have keyboard equivalents.
- Design terminal glyph-width fallback for ASCII/Unicode/color emoji; layouts should withstand ambiguous-width glyphs and reduced columns.
- Expose accessible focus order, readable headings, state and error details; test with assistive setups available on supported platforms.

## Testing

String extraction lint, missing-resource checks, placeholder count/names, plural tests for multiple languages, 40/80/120-column layouts, no control characters leaking from untrusted sources, English and Czech smoke tests. Do not claim universal Unicode terminal capability without actual backend measurements.
