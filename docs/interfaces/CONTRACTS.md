# Preliminary interface sketches (NOT stable APIs)

This file describes semantic contracts, **not** ready-to-compile Rust signatures, manifest schemas, or the final security model.

## JavaScript engine adapter

```text
JsEngineDescriptor { id, version, adapter_api, declared_capabilities }
JsEngineFactory::create(config) -> JsRuntime
JsRuntime::create_realm(origin, host_bindings) -> JsRealm
JsRealm::evaluate(script, source_name) -> Completion
JsRealm::load_module(specifier, resolver) -> ModuleResult
JsRealm::drain_microtasks(budget) -> Progress
JsRealm::close() -> Result
JsDiagnostics::inspect()/console()/debugger_capabilities()
```

`JsValueHandle` lifetimes and GC tracing are unresolved. Capability reports distinguish declared versus tested availability. No swapping a live JS heap between runtimes.

## Storage data management

```text
StorageProvider::describe() -> {id, scopes, capabilities, quotas}
StorageProvider::enumerate(scope, cursor) -> page<RecordMetadata>
StorageProvider::inspect(record_id, privileged_reveal) -> RecordContent
StorageProvider::export(scope, format) -> ExportArtifact
StorageProvider::delete(ids, mode, owner_authorization) -> Outcome
StorageProvider::subscribe(scope) -> StorageEventStream
```

All providers must declare inspect/export/delete ability and honest limitations; owner privileges != plugin privileges. Do not assume all records are textual.

## Workloads / watchers

```text
Collector::discover(source, since/checkpoint) -> ItemBatch
ConditionEvaluator::compare(prior, current) -> Changes
WorkloadRunner::run(id, durable_checkpoint) -> RunOutcome
NotificationService::publish(event_id, status, targets) -> Result
```

Each result includes stable IDs, provenance, timestamps, error/unknown distinctions and idempotency keys. A source's existing releases form a baseline unless user requests history.

## Prompt pack

```yaml
# Illustrative manifest; not yet adopted by a parser.
id: community.github-notification-helper
version: 0.1.0
type: prompt-pack
requires:
  input: [SelectedMail]
  capabilities: [mail.read.selected, ai.analyze, mail.draft.create]
entries:
  - id: summarize-ci
    prompt: prompts/summarize-ci.md
    output_schema: schemas/ci-summary.json
```

Content displayed before release authorization; grant permissions via gateway, never from manifest alone. Support localization and versioned updates.

## Transparent outbound report

```text
DraftReport -> SanitizedReport -> ImmutablePayload(hash)
-> ReviewScreen(exact_content, destination)
-> UserApproval(payload_hash)
-> OutboundTransfer(progress, response)
-> AuditRecord
```

If payload hash/content differs, approval is invalid. Plain transport internals are not necessarily individually presented, but all application data and attachments are.
