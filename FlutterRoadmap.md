# Flutter Developer Roadmap 2026

This roadmap is a structured checklist from fundamentals through shipping production Flutter apps. Use official docs as source of truth; treat third-party packages as tools with maintenance costs.

## Contents

- [0. How to use this roadmap](#0-how-to-use-this-roadmap)
- [1. Developer foundations](#1-developer-foundations)
- [2. Dart language](#2-dart-language)
- [3. Flutter fundamentals](#3-flutter-fundamentals)
- [4. UI, layout, and adaptive design](#4-ui-layout-and-adaptive-design)
- [5. Navigation and routing](#5-navigation-and-routing)
- [6. State management](#6-state-management)
- [7. Networking and API integration](#7-networking-and-api-integration)
- [8. Local persistence](#8-local-persistence)
- [9. Architecture](#9-architecture)
- [10. Testing](#10-testing)
- [11. Platform integration](#11-platform-integration)
- [12. Performance and DevTools](#12-performance-and-devtools)
- [13. Security](#13-security)
- [14. CI/CD and automation](#14-cicd-and-automation)
- [15. Analytics and monitoring](#15-analytics-and-monitoring)
- [16. Store release and compliance](#16-store-release-and-compliance)
- [17. AI-assisted Flutter development](#17-ai-assisted-flutter-development)
- [18. Advanced Flutter](#18-advanced-flutter)
- [19. Learning path by level](#19-learning-path-by-level)
- [20. Recommended resources](#20-recommended-resources)

---

## 0. How to use this roadmap

| Audience | How to use |
| --- | --- |
| **Beginner** | Complete §1–§4 in order. Build one small app per month (todo → weather → chat UI mock). Skim §17.1–§17.2 so you adopt safe habits early. |
| **Junior** | Assumes §1–§4 done. Focus §5–§8 + §10 basics + §12 skim. Ship one app with login + API + persistence. Read §17 to accelerate—but never skip tests/analyzer. |
| **Middle** | Deep §9–§11 + §13–§14 + §16. Own CI pipeline and release checklist on a real codebase. Use §17.7–§17.10 for systematic refactors and incidents. |
| **Senior** | §9–§16 across teams: standards, modularization, security reviews, observability, store strategy. Drive §17 Level 4–5 workflows (MCP + shared prompts + PR/MR hygiene). |

### Roadmap habits

- Check items off as you can **explain and apply**, not merely watch.
- Prefer **small shipped increments** over passive tutorials.
- Pair every AI acceleration step with **analyzer + tests + human diff review**.

---

## 1. Developer foundations

### Foundations skills

- [ ] **Computer science basics**: complexity intuition (big‑O at a practical level), data structures (list/map/set/tree graphs basics), algorithms that appear daily (sort/search).
- [ ] **Git with GitHub or GitLab**: branching, merge/rebase hygiene, pull/merge request reviews, `.gitignore`, signing commits if your org requires it.
- [ ] **GitLab collaboration** *(when your team uses GitLab)*: repositories; merge requests and code review; issues & boards; branching strategy aligned with release cadence; protected branches; basic **project settings** (visibility, merge method, approvals); **permissions** (roles, guest/reporter/developer/maintainer)—GitLab is a first‑class alternative to GitHub for team delivery on the same Git mental model.
- [ ] **Terminal basics**: env vars, PATH, scripting basics, reading logs.
- [ ] **HTTP/REST basics**: verbs, status codes, headers, idempotency, pagination patterns.
- [ ] **JSON**: encoding/decoding mental model; validation vs trusting raw maps.
- [ ] **APIs**: REST contracts; optional GraphQL/WebSocket awareness (deep‑dive later).
- [ ] **Debugging mindset**: reproduce → isolate → smallest change → prove with test.
- [ ] **Clean code basics**: naming, small functions, avoiding duplication without abstraction overload.
- [ ] **SOLID basics**: practical mapping to Dart services/repositories—not textbook memorization.
- [ ] **Package management basics**: semver intuition, lockfiles, transitive deps, supply‑chain awareness.

### Official starter links

| Topic | Resource |
| --- | --- |
| Git | [Git documentation](https://git-scm.com/doc) |
| GitHub flows | [GitHub Flow](https://docs.github.com/en/get-started/using-github/github-flow) |
| GitLab docs hub | [GitLab documentation](https://docs.gitlab.com/) |
| GitLab repository | [Repositories](https://docs.gitlab.com/user/project/repository/) |
| GitLab merge requests | [Merge requests](https://docs.gitlab.com/user/project/merge_requests/) |
| GitLab issues | [Issues](https://docs.gitlab.com/user/project/issues/) |
| GitLab protected branches | [Protected branches](https://docs.gitlab.com/user/project/protected_branches/) |
| HTTP | [MDN HTTP overview](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview) |

### Hands-on — foundations

- [ ] Automate one repetitive task with a **shell script** or Git alias.
- [ ] Review three **pull or merge requests** focusing only on **readability and edge cases**.

---

## 2. Dart language

### Core topics

| Topic | What “good enough” looks like |
| --- | --- |
| Syntax & types | Reads idiomatically; avoids dynamic unless justified |
| Functions | Named params, arrow syntax, tear‑offs |
| Classes | Fields, getters, `abstract`, interfaces via implicit typing |
| Constructors | Default, named, factory, const constructors |
| Null safety | Flow analysis, `?`, `!`, late with discipline |
| Collections | List/Map/Set, spreads, collection `if`/`for` |
| Generics | Variance intuition for collections and APIs |
| Extensions | Domain‑friendly APIs without wrapper explosion |
| Mixins | Composition where inheritance fights you |
| Enums / enhanced enums | Exhaustive switches |
| Records | Lightweight aggregates ([Records](https://dart.dev/language/records)) |
| Patterns | Destructuring & flow typing ([Patterns](https://dart.dev/language/patterns)) |
| Sealed classes | Algebraic types + exhaustive handling |
| Async | `async`/`await`, cancellation awareness |
| Future / Stream | Error propagation, stream transformers basics |
| Isolates | When UI thread bottlenecks; compute/`Isolate.run` basics |
| Error handling | Typed errors, never swallowing failures silently |
| Tooling | Formatter, analyzer, fixes ([Analysis](https://dart.dev/tools/analysis)) |

### Official Dart references

- [Dart language](https://dart.dev/language)
- [Effective Dart](https://dart.dev/effective-dart)
- [Dart analyzer & static analysis](https://dart.dev/tools/analysis)
- [Records](https://dart.dev/language/records)
- [Patterns](https://dart.dev/language/patterns)
- [Class modifiers](https://dart.dev/language/class-modifiers)

### Hands-on — Dart

- [ ] Enable **`analysis_options.yaml`** with team rules; fix all `info` you agree matters.
- [ ] Implement one **sealed** feature state with exhaustive `switch`.

---

## 3. Flutter fundamentals

### Flutter essentials checklist

- [ ] **Widget tree**: composition over inheritance; rebuilding implications.
- [ ] **`StatelessWidget` vs `StatefulWidget`**: when state belongs in widgets vs elsewhere.
- [ ] **`BuildContext`**: lookup limits; don’t store contexts incorrectly.
- [ ] **Element tree**: relationship between `Widget` ↔ `Element` ↔ `RenderObject` (conceptual).
- [ ] **`RenderObject` basics**: why layout/paint happens; debug overflows.
- [ ] **State lifecycle**: `initState`, `dispose`, `didChangeDependencies`.
- [ ] **Keys**: `ValueKey`, `ObjectKey`, when lists need keys.
- [ ] **`InheritedWidget` basics**: dependency injection of theme/localizations.
- [ ] **Assets**: `pubspec.yaml`, resolution variants, caching.
- [ ] **Themes**: `ThemeData`, text styles, component themes.
- [ ] **Material 3**: Material You concepts; component defaults.
- [ ] **Cupertino basics**: when targeting iOS‑feel surfaces.
- [ ] **Forms**: `Form`, `TextFormField`, validators.
- [ ] **Images & icons**: raster vs vector; caching; accessibility labels.
- [ ] **Localization basics**: `AppLocalizations`, arb files.

### Official Flutter references

- [Flutter documentation](https://docs.flutter.dev/)
- [UI introduction](https://docs.flutter.dev/ui)
- [Widget catalog](https://docs.flutter.dev/ui/widgets)
- [Architectural overview](https://docs.flutter.dev/resources/architectural-overview)

### Hands-on — Flutter fundamentals

- [ ] Build a **theme toggle** (light/dark) with persistent preference (preview §8).
- [ ] Localize **three strings** end‑to‑end (`gen-l10n` workflow).

---

## 4. UI, layout, and adaptive design

### Layout & adaptive checklist

- [ ] **Row / Column / Stack**: alignment, `MainAxisAlignment`, `CrossAxisAlignment`.
- [ ] **Flex**: flex values, `FlexFit`.
- [ ] **`Expanded` / `Flexible`**: difference and overflow pitfalls.
- [ ] **`ListView` / `GridView`**: builders for performance.
- [ ] **`CustomScrollView` & slivers**: headers, collapsing bars.
- [ ] **Constraints**: min/max width/height mental model; “constraints go down, sizes go up”.
- [ ] **`MediaQuery`**: padding, text scaler accessibility.
- [ ] **`LayoutBuilder`**: responsive breakpoints.
- [ ] **`SafeArea`**: notches & system UI padding.
- [ ] **Responsive & adaptive**: phone/tablet/desktop layouts; foldables awareness.
- [ ] **Material Design**: components & motion guidelines — [Material Design](https://m3.material.io/)
- [ ] **Human Interface Guidelines** — [Apple HIG](https://developer.apple.com/design/human-interface-guidelines/)
- [ ] **Animations**: implicit vs explicit; `AnimationController` lifecycle.
- [ ] **`CustomPainter` basics**: custom visuals vs maintainability cost.

### Hands-on — layout & adaptive

- [ ] Implement one screen with **three breakpoints** without duplicating business logic.
- [ ] Fix a **real overflow** using DevTools Layout Explorer.

---

## 5. Navigation and routing

### Navigation checklist

- [ ] **Navigator 1.0**: imperative stack; when still appropriate.
- [ ] **Navigator 2.0 concept**: declarative routes (know strengths/costs).
- [ ] **`go_router`**: routes, redirects, nested navigation — [package](https://pub.dev/packages/go_router)
- [ ] **Deep / App / Universal links**: platform configuration surfaces.
- [ ] **Shell routes**: persistent scaffolding (tabs, drawers).
- [ ] **Nested navigation**: independent stacks.
- [ ] **Auth‑based routing**: guards via redirects / refresh listenables.
- [ ] **Route guards**: unauthenticated vs stale permission handling.
- [ ] **Error routes**: unknown paths and crashes UX.
- [ ] **Web URL strategy**: paths vs hashes where relevant.

### Navigation references

- [Navigation overview](https://docs.flutter.dev/ui/navigation)

### Hands-on — navigation

- [ ] Add **email‑link style deep link** handling with a mocked backend contract.

---

## 6. State management

### State management checklist

- [ ] **`setState`**: local ephemeral UI state only.
- [ ] **`ValueNotifier` / `ValueListenableBuilder`**: simple observable values.
- [ ] **`ChangeNotifier`**: model notifications + disposal discipline.
- [ ] **Provider**: DI + listenable wiring — [package](https://pub.dev/packages/provider)
- [ ] **Riverpod**: compile‑safe providers, overrides, testing hooks — [site](https://riverpod.dev/)
- [ ] **Bloc / Cubit**: explicit events/states for complex domains — [package](https://pub.dev/packages/flutter_bloc)
- [ ] **`InheritedWidget`**: framework‑level dependency propagation.
- [ ] **State restoration**: saving navigation + form state where applicable.
- [ ] **Local UI vs app state**: boundary rules per feature.
- [ ] **Async state**: loading/error/data surfaces; cancellation.
- [ ] **Feature‑scoped state**: avoid global singleton soup.

### Selection criteria (practical)

| Factor | Lean toward |
| --- | --- |
| Small app / protos | `setState`, `ValueNotifier`, Provider |
| Growing codebase | Riverpod or Bloc (pick **one** primary pattern per repo) |
| Heavy forms + transitions | Bloc/Cubit explicit states |
| Highly dynamic DI graphs | Riverpod overrides / scopes |

### Official guidance

- [State management options](https://docs.flutter.dev/data-and-backend/state-mgmt/options)

### Hands-on — state management

- [ ] Refactor one screen so **no business logic** remains inside `build()`.

---

## 7. Networking and API integration

### Networking checklist

- [ ] **HTTP basics**: timeouts, retries policy, cancelling calls.
- [ ] **REST**: resources, versioning, error payloads.
- [ ] **GraphQL basics**: queries/mutations vs REST trade‑offs (pick deep‑dive later).
- [ ] **WebSocket basics**: reconnect strategies; stream hygiene.
- [ ] **`dio`**: interceptors, adaptors — [package](https://pub.dev/packages/dio)
- [ ] **Interceptors**: auth headers, logging (non‑prod), metrics.
- [ ] **Authentication**: token storage (see §13), refresh flows.
- [ ] **Token refresh**: single‑flight pattern; avoid storms.
- [ ] **Error handling**: typed failures vs generic exceptions.
- [ ] **Retry logic**: idempotent vs non‑idempotent endpoints.
- [ ] **Pagination**: cursor vs offset; dedupe & staleness.
- [ ] **Upload/download**: multipart, progress, cancellation.
- [ ] **API logging**: redaction rules for secrets.
- [ ] **DTOs**: wire vs domain separation.
- [ ] **Serialization**: `json_serializable`, codegen discipline — [package](https://pub.dev/packages/json_serializable)
- [ ] **Immutable models**: `freezed` or hand‑rolled sealed unions — [package](https://pub.dev/packages/freezed)

### Hands-on — networking

- [ ] Implement **token refresh** with a single in‑flight future shared across requests.

---

## 8. Local persistence

### Persistence checklist

- [ ] **`shared_preferences`**: tiny flags / last‑seen strings — [package](https://pub.dev/packages/shared_preferences)
- [ ] **Secure storage**: Keychain/Keystore wrappers — [package](https://pub.dev/packages/flutter_secure_storage)
- [ ] **SQLite**: relational local data — [package](https://pub.dev/packages/sqflite)
- [ ] **Drift**: typed SQL layer — [site](https://drift.simonbinder.eu/)
- [ ] **Hive / Isar / ObjectBox**: document/object stores — evaluate maintenance & migrations ([Hive](https://pub.dev/packages/hive), [Isar](https://pub.dev/packages/isar))
- [ ] **Caching strategy**: TTL, stale‑while‑revalidate, eviction.
- [ ] **Offline‑first basics**: queue mutations; conflict awareness at domain level.
- [ ] **Data sync**: idempotency keys; backoff.
- [ ] **Migrations**: schema versioning discipline.

### Hands-on — persistence

- [ ] Write a **migration test** that proves old DB versions upgrade cleanly.

---

## 9. Architecture

### Architecture checklist

- [ ] **Feature‑first structure**: screens/widgets/use‑cases/data per feature.
- [ ] **Layered architecture**: presentation / domain / data separation when complexity warrants.
- [ ] **Clean Architecture**: boundaries & dependency rule (pragmatic, not dogmatic).
- [ ] **MVVM**: ViewModel as testable coordinator (Flutter-friendly variants).
- [ ] **Repository pattern**: single gateway per aggregate root.
- [ ] **Dependency injection**: constructor injection first; service locator sparingly (`get_it`, `injectable`).
- [ ] **Use cases**: app‑specific verbs encapsulating orchestration.
- [ ] **DTO vs Entity vs Model**: naming discipline across layers.
- [ ] **Error strategy**: failure types crossing layers intentionally.
- [ ] **Result / Either pattern**: explicit errors vs throwing soup (`dartz`, `fpdart`, hand‑rolled Result).
- [ ] **Modularization**: packages/modules with clear public APIs.
- [ ] **Monorepo basics**: shared tooling & versioning alignment.
- [ ] **Melos**: multi‑package scripts — [pub.dev package](https://pub.dev/packages/melos)
- [ ] **ADRs**: Architecture Decision Records when choices affect teams.

### Architecture references

- [App architecture recommendations](https://docs.flutter.dev/app-architecture/recommendations)

### Hands-on — architecture

- [ ] Write **one ADR** capturing a state‑management choice with trade‑offs.

---

## 10. Testing

### Testing checklist

- [ ] **Unit tests**: pure logic, repositories with fakes.
- [ ] **Widget tests**: pump widgets; finder hygiene.
- [ ] **Integration tests**: `integration_test` driving real harness — [docs](https://docs.flutter.dev/testing/integration-tests)
- [ ] **Golden tests**: pixel‑perfect guards with sane thresholds.
- [ ] **Mocking**: `mocktail` / manual fakes; prefer **fakes** where behavior matters.
- [ ] **Test data builders**: factories reducing brittle literals.
- [ ] **Repository tests**: simulate disk/network edges.
- [ ] **Bloc/Riverpod tests**: provider overrides / bloc harness patterns.
- [ ] **CI pipeline**: merge‑blocking `flutter test` + analyzer on default branch protection rules.
- [ ] **Coverage**: track trends; avoid gaming percentages blindly.
- [ ] **Naming**: Arrange‑Act‑Assert readability; descriptive test names.

### Testing references

- [Testing overview](https://docs.flutter.dev/testing)

### Hands-on — testing

- [ ] Convert last production bug into a **regression test** before closing ticket.

---

## 11. Platform integration

### Platform integration checklist

- [ ] **Android / iOS setup**: Xcode/Android toolchain hygiene; signing basics awareness.
- [ ] **Permissions**: runtime prompts; minimal scopes — platform docs.
- [ ] **`MethodChannel` / `EventChannel`**: native bridge contracts.
- [ ] **Platform views**: embedding native UI (cost/benefit).
- [ ] **Background execution basics**: platform constraints (don’t promise impossible tasks).
- [ ] **Push notifications**: FCM/APNs wiring — [Firebase Cloud Messaging](https://firebase.google.com/docs/cloud-messaging)
- [ ] **Local notifications**: schedules & permission nuances.
- [ ] **Camera / Photo picker**: permission & lifecycle pitfalls.
- [ ] **Location**: accuracy vs battery trade‑offs.
- [ ] **Biometrics**: `local_auth` patterns — [package](https://pub.dev/packages/local_auth)
- [ ] **Files / SAF / scoped storage awareness** (especially Android).
- [ ] **Native SDK integration**: CocoaPods/Gradle vendor SDK constraints.
- [ ] **App lifecycle**: foreground/background transitions & state restoration interplay.

### Hands-on — platform integration

- [ ] Prototype **biometric‑gated** secret retrieval with secure failure UX.

---

## 12. Performance and DevTools

### Performance checklist

- [ ] **Flutter DevTools**: CPU/memory/network tooling.
- [ ] **Performance overlay / timeline**: identify jank frames.
- [ ] **Memory**: leaks (`dispose`, listeners, streams), image caches.
- [ ] **CPU profiler**: hotspots in Dart vs layout/paint.
- [ ] **Rebuild optimization**: `const`, granular selectors, unnecessary parent rebuilds.
- [ ] **List performance**: builders, cache extents.
- [ ] **Image optimization**: resolution‑aware assets, decoding bounds.
- [ ] **Shader compilation / warmup**: first‑frame strategies where needed.
- [ ] **Impeller**: rendering backend awareness — [Impeller](https://docs.flutter.dev/perf/impeller)
- [ ] **App size**: deferred loading considerations; tree‑shake icons/fonts.
- [ ] **Performance checklist**: periodic audits before releases.

### Performance references

- [Performance profiling](https://docs.flutter.dev/tools/devtools/performance)
- [Performance overview](https://docs.flutter.dev/perf)
- [Impeller](https://docs.flutter.dev/perf/impeller)

### Hands-on — performance

- [ ] Record DevTools timeline for worst screen; remove **≥16 ms** spikes where feasible.

---

## 13. Security

### Security checklist

- [ ] **Secure storage** for tokens/keys; never `shared_preferences` for secrets.
- [ ] **Token hygiene**: short‑lived access + rotation; revoke paths.
- [ ] **Certificate pinning**: threat model clarity—know operational costs.
- [ ] **Secrets management**: CI secrets, `--dart-define`, avoiding checked‑in keys.
- [ ] **Obfuscation**: release symbols handling; know limits vs reversing.
- [ ] **Jailbreak/root detection basics**: risk signaling—not sole defense ([OWASP guidance context](https://owasp.org/www-project-mobile-app-security/)).
- [ ] **API authorization**: server‑side enforcement assumption.
- [ ] **Input validation**: trust boundaries at serialization edges.
- [ ] **Privacy**: data minimization, consent flows, analytics disclosure.
- [ ] **OWASP MASVS**: baseline checklist — [OWASP MASVS](https://owasp.org/www-project-mobile-app-security/)
- [ ] **Permission minimization**: declare only what you use.

### Hands-on — security

- [ ] Threat‑model **one feature** (STRIDE lite): assets, adversaries, mitigations.

---

## 14. CI/CD and automation

### CI/CD checklist

- [ ] **GitHub Actions**: workflows caching Flutter/SDK artifacts — [docs](https://docs.github.com/en/actions)
- [ ] **GitLab CI/CD**: `.gitlab-ci.yml` pipelines with **stages** and **jobs**; **runners** (shared or self‑managed); CI/CD **variables** (incl. protected/masked secrets); **caching**; **artifacts**; **manual** jobs; **scheduled** pipelines; **merge request pipelines** for shift‑left checks; Flutter **`analyze`** / **`test`** jobs; release/build jobs for **APK/AAB/IPA** per flavor; align **environment‑specific** configs without committing secrets — [CI/CD overview](https://docs.gitlab.com/ci/), [`.gitlab-ci.yml` reference](https://docs.gitlab.com/ci/yaml/), [Pipelines](https://docs.gitlab.com/ci/pipelines/), [Runner](https://docs.gitlab.com/runner/), [Variables](https://docs.gitlab.com/ci/variables/), [Caching](https://docs.gitlab.com/ci/caching/), [Job artifacts](https://docs.gitlab.com/ci/jobs/job_artifacts/)
- [ ] **Fastlane**: lanes for screenshots, beta, store uploads — [site](https://fastlane.tools/)
- [ ] **Codemagic**: Flutter‑centric hosted CI — [site](https://codemagic.io/start/)
- [ ] **Shorebird**: over‑the‑air patching basics — [docs](https://docs.shorebird.dev/)
- [ ] **Flavors / schemes**: dev/stage/prod separation.
- [ ] **Environments**: config injection patterns without embedding secrets.
- [ ] **Versioning**: semver + build numbers per store rules.
- [ ] **Signing**: Android keystores, iOS certs/profiles rotation calendars.
- [ ] **Automated tests on CI**: unit/widget/integration staged appropriately.
- [ ] **Release notes automation**: changelog generation discipline.
- [ ] **Static analysis**: `flutter analyze`, formatter checks.
- [ ] **Dependency audits**: `dart pub outdated`, Renovate or similar automation (PRs on GitHub, **MRs** on GitLab).

### Starter example: minimal Flutter pipeline (GitLab CI)

Below is a **starting point only**: adjust image tags, runner tags, signing, and caching for your org. The Flutter image is a common community choice; verify it meets your security/supply‑chain policy.

```yaml
stages:
  - analyze
  - test
  - build

flutter_analyze:
  stage: analyze
  image: ghcr.io/cirruslabs/flutter:stable
  script:
    - flutter pub get
    - flutter analyze

flutter_test:
  stage: test
  image: ghcr.io/cirruslabs/flutter:stable
  script:
    - flutter pub get
    - flutter test

build_android:
  stage: build
  image: ghcr.io/cirruslabs/flutter:stable
  script:
    - flutter pub get
    - flutter build apk --release
  artifacts:
    paths:
      - build/app/outputs/flutter-apk/*.apk
```

### Hands-on — CI/CD

- [ ] Make **`flutter analyze` non‑zero exit** block merges (GitHub branch protection, GitLab merge request approvals, or equivalent).

---

## 15. Analytics and monitoring

### Analytics checklist

- [ ] **Firebase Analytics** — [docs](https://firebase.google.com/docs/analytics)
- [ ] **Firebase Crashlytics** — [docs](https://firebase.google.com/docs/crashlytics)
- [ ] **Firebase Performance Monitoring** — [docs](https://firebase.google.com/docs/perf-mon)
- [ ] **Sentry**: breadcrumbs, tracing — [Flutter SDK](https://docs.sentry.io/platforms/flutter/)
- [ ] **Attribution tools** (AppsFlyer/Branch/etc.) when growth mandates—evaluate privacy impact per region.
- [ ] **Event naming taxonomy**: consistent snake_case/camelCase per org.
- [ ] **Funnels**: define success metrics before instrumenting.
- [ ] **Remote Config / A/B basics**: guardrails + rollback stories.
- [ ] **Crash triage**: symbolicated stacks, ownership routing.
- [ ] **Privacy‑aware analytics**: consent, opt‑out, data retention policies.

### Hands-on — analytics

- [ ] Create **dashboard + alert** for crash‑free sessions dip threshold.

---

## 16. Store release and compliance

### Store release checklist

- [ ] **App Store Connect** workflows — [Apple overview](https://developer.apple.com/app-store-connect/)
- [ ] **Google Play Console** tracks — [Play Console](https://play.google.com/console/about/)
- [ ] **Review notes**: reproduc steps for reviewers (especially gated flows).
- [ ] **Privacy policy**: hosted, accurate, linked in‑app & stores.
- [ ] **Data safety / nutrition labels**: disclosures aligned with actual SDK behaviors.
- [ ] **Permission declarations**: matching manifest plist realities.
- [ ] **Demo/test accounts** provisioning without leaking prod data.
- [ ] **Screenshots / preview assets**: localized readiness.
- [ ] **Release notes**: user‑readable deltas vs internal jargon.
- [ ] **Phased rollout**: monitoring gates before full blast.
- [ ] **Production monitoring**: crash budgets & rollback triggers.
- [ ] **Rollback strategy**: staged percentages; hotfix path awareness.

### Official policy references

- [App Review Guidelines](https://developer.apple.com/app-store/review/guidelines/)
- [Google Play Developer Policy](https://play.google.com/about/developer-content-policy/)

### Hands-on — store release

- [ ] Draft **store reviewer script** for login‑gated features before submission.

---

## 17. AI-assisted Flutter development

Modern Flutter teams increasingly pair human judgment with AI tooling. Treat AI as **acceleration with accountability**, not as an excuse to skip architecture or safety checks.

### 17.1 AI mindset for developers

| Principle | Practice |
| --- | --- |
| Assistant, not replacement | You own architecture, security, UX commitments. |
| Human review mandatory | Especially routing, auth, persistence, concurrency. |
| Verify outputs | Cross‑check against docs & runtime behavior. |
| Guardrails | Formatter, analyzer (`flutter analyze`), CI tests gate merges. |
| Small scopes | Single concern PRs/MRs; easier reviews catch hallucinations. |
| Plan first | Short written plan for multi‑file edits reduces churn. |

### 17.2 Prompt engineering for Flutter

Use the pattern blocks below as reusable templates. Replace placeholders with **paths, versions, logs**, and **constraints**.

#### Bug fixing

| Field | Guidance |
| --- | --- |
| Context | Flutter/Dart version; failing stack trace; minimal reproduction repo snippet |
| Goal | Identify root cause + smallest safe patch |
| Constraints | Preserve public APIs; avoid unrelated refactors |
| Expected output | Patch sketch + reasoning + tests to add |
| Validation | `flutter analyze`; reproduce steps pass/fail |

#### Refactoring

| Field | Guidance |
| --- | --- |
| Context | Module map; coupling hotspots |
| Goal | Reduce coupling / improve naming without behavior change |
| Constraints | No semantic drift; maintain backwards compatibility unless flagged |
| Expected output | Stepwise commits suggestions + impacted tests |
| Validation | Tests green; behavior snapshots/goldens if UI‑critical |

#### Architecture analysis

| Field | Guidance |
| --- | --- |
| Context | Feature boundaries; dependency diagram excerpt |
| Goal | Highlight layering violations & risky edges |
| Constraints | Align with chosen state mgmt + navigation solution |
| Expected output | Prioritized risk list + migration milestones |
| Validation | Team review; ADR update if accepted |

#### UI implementation

| Field | Guidance |
| --- | --- |
| Context | Design specs + accessibility requirements |
| Goal | Compose widgets idiomatically with theme hooks |
| Constraints | Support dynamic text scaling; avoid fixed magic numbers |
| Expected output | Widget tree outline + theming notes |
| Validation | Widget/golden tests; VoiceOver/TalkBack spot checks |

#### Test generation

| Field | Guidance |
| --- | --- |
| Context | Class API + edge cases + failure modes |
| Goal | Cover happy path + identified corner cases |
| Constraints | Deterministic tests (no real network) |
| Expected output | Unit/widget tests with builders/fakes |
| Validation | `flutter test` locally & CI |

#### Code review

| Field | Guidance |
| --- | --- |
| Context | Diff summary + risk areas |
| Goal | Security/perf/architecture findings ranked |
| Constraints | Reference official docs when asserting correctness |
| Expected output | Comment‑style review checklist |
| Validation | Human reviewer adjudicates disagreements |

#### Performance optimization

| Field | Guidance |
| --- | --- |
| Context | DevTools traces; problematic widgets |
| Goal | Concrete hotspots & mitigation |
| Constraints | Measure before/after; avoid premature micro‑opts |
| Expected output | Change list + expected frame budget impact |
| Validation | Timeline replay on low‑end device/emulator |

#### Store review / release notes

| Field | Guidance |
| --- | --- |
| Context | Changes since tag; permissions touched |
| Goal | Plain‑language notes & reviewer instructions |
| Constraints | Avoid revealing unreleased security notes publicly |
| Expected output | Store‑formatted text blocks |
| Validation | PM/legal review where applicable |

#### Documentation

| Field | Guidance |
| --- | --- |
| Context | Audience (dev/on‑call/support); repo conventions |
| Goal | Update README/module docs without fluff |
| Constraints | Link official docs; avoid speculative claims |
| Expected output | Patch‑style markdown suggestions |
| Validation | Doc lint/links checked |

### 17.3 AI coding tools

| Tool | Useful for | Where it fits | Limitations | Safety notes |
| --- | --- | --- | --- | --- |
| **ChatGPT** | Broad reasoning, planning, doc summaries | Spike answers, release note drafts | No repo awareness unless wired | Redact secrets; verify citations |
| **GitHub Copilot** | Inline completion | Boilerplate, tests | May propose stale APIs | Enable org policies; review diffs |
| **Cursor** | Agentic edits across files | Refactors, migrations | Powerful → risky if unchecked | Branch isolation; rules files—see §17.4 |
| **Gemini CLI / cloud assistants** | Scripting help, multi‑modal prompts | Docs parsing | Policy differs by workspace | Treat uploads as sensitive |
| **Claude** *(Anthropic: Claude.ai / API / IDE tooling)* | Long‑context planning & reviews | Architecture spikes, large‑diff summaries | Same hallucination risk as other frontier LLMs | Data‑handling policy per tenant; never paste keystores |
| **Claude Code** *(Anthropic agent product)* | Terminal/agent workflows alongside repo context | Batch edits guided by CLAUDE.md‑style conventions—mirror `AGENTS.md`, `flutter analyze`, and tests discipline | Capability varies by integration—still requires human merge authority | Treat tokens/secrets like CI secrets—scoped tokens only |
| **CodeRabbit‑style PR bots** | Diff‑scoped feedback | PR hygiene | False positives/negatives | Humans merge authority |
| **Figma AI / design‑to‑code** | Exploring layouts | Early prototyping | Rarely production‑ready | Designers validate fidelity |

Official Claude / Anthropic docs *(landing URLs may redirect as providers consolidate domains)*:

- [Anthropic documentation](https://docs.anthropic.com/)
- [Claude Code documentation](https://code.claude.com/docs/en/overview)

### 17.4 Cursor workflow

| Topic | Guidance |
| --- | --- |
| Agent | Use for scoped tasks with explicit file boundaries |
| Rules | Encode non‑negotiable standards ([Rules docs](https://cursor.com/docs/rules)) |
| `AGENTS.md` | Repo‑level guidance for autonomous agents—permissions & workflows |
| Planning | Short plan before multi‑step edits; avoids destructive churn |
| Diff review | Never merge unseen AI diff chunks |
| Terminal approvals | Vet destructive commands (`rm`, `dart pub cache`, DB ops) |
| Analyzer/tests | Run `flutter analyze` & targeted tests post‑change |
| Repo‑wide refactors | Prefer incremental PRs with mechanical commits |
| Documentation | Ask AI to align headings/links with existing structure |

Links:

- [Cursor Docs](https://cursor.com/docs)
- [Rules](https://cursor.com/docs/rules)
- [MCP in Cursor](https://cursor.com/docs/mcp)
- [CLI usage](https://cursor.com/docs/cli/using)
- [Agent best practices](https://cursor.com/blog/agent-best-practices)

### 17.5 MCP — Model Context Protocol

**What MCP is**: an open protocol for connecting AI clients to external **tools**, **resources**, and **prompt templates** with explicit capability negotiation—think structured plugins instead of blind copy‑paste context.

| Concept | Meaning |
| --- | --- |
| MCP client | Host application embedding AI (e.g., IDE agent) |
| MCP server | Bridge exposing capabilities over MCP |
| Tools | Callable actions (query ticket, fetch schema) |
| Resources | Read‑mostly contextual payloads (files, slices of dashboards) |
| Prompts | Pre‑structured prompt workflows |

Flutter‑oriented use cases:

- GitHub issues/PR context without noisy HTML scraping.
- GitLab issues/MRs and pipeline logs as grounded context—apply the same redaction rules as GitHub tokens.
- Local `dartdoc` / internal wiki ingestion with citations.
- Figma frame metadata for implementation parity checks.
- Jira/Linear ticket grounding for acceptance criteria.
- Supabase/Postgres schema snapshots for API modeling sanity (read‑only).
- Internal REST/OpenAPI specs for codegen alignment.

#### MCP safety

- Prefer **read‑only** integrations first.
- Never expose **production secrets** to MCP servers or prompts.
- Avoid connecting **production databases** without strict IAM & auditing.
- Disallow **destructive tools** (drop tables, mass deletes) by default.
- Periodically **review tool scopes** & OAuth grants.
- Use **separate dev sandboxes** for experimentation.

Links *(some URLs redirect to versioned specification pages—bookmark finals after first load)*:

- [MCP introduction](https://modelcontextprotocol.io/docs/getting-started/intro)
- [Architecture overview *(via `/docs/learn/architecture`)*](https://modelcontextprotocol.io/docs/concepts/architecture)
- [Tools concept *(may redirect to latest specification)*](https://modelcontextprotocol.io/docs/concepts/tools)
- [Resources concept](https://modelcontextprotocol.io/docs/concepts/resources)
- [Prompts concept](https://modelcontextprotocol.io/docs/concepts/prompts)
- [GitHub Copilot + MCP concepts](https://docs.github.com/en/copilot/concepts/context/mcp)

### 17.6 AI project documentation

| Artifact | Purpose | AI leverage |
| --- | --- | --- |
| `README.md` | Quick onboarding | Agents infer constraints & setup commands |
| `AGENTS.md` | Automation guardrails | Standardizes safe autonomy boundaries |
| `PLAN.md` | Short‑lived implementation plans | Reduces ambiguous edits mid‑task |
| `REPORTS.md` | Human changelog for docs edits | Helps future prompts avoid regressions |
| `CHANGELOG.md` | Release history | Ground release assistants |
| ADRs | Decision memory | Prevents re‑litigating architecture |
| Prompt/task templates | Repeatable workflows | Speed without forgetting constraints |
| Bug templates | Consistent repro data | Better automated triage |
| PR checklist | Merge quality | Pair with bots + humans |

### 17.7 AI for Flutter architecture

Checklist you can hand an agent:

- [ ] Map current layering vs intended boundaries (presentation/domain/data).
- [ ] Detect global singletons hiding implicit coupling.
- [ ] Propose **feature‑first** folder moves with migration sequencing.
- [ ] Validate **state ownership** between widgets, controllers, and repositories.
- [ ] Audit **navigation + auth** coupling for impossible routes.
- [ ] Evaluate **dependency injection** graph clarity.

### 17.8 AI for testing

- [ ] Generate **unit tests** from pure functions & repositories using fakes.
- [ ] Scaffold **widget tests** given UX acceptance bullets.
- [ ] Outline **`integration_test`** journeys from flows (purchase, login).
- [ ] Propose **golden** coverage where visuals are contractual.
- [ ] Convert bug reports into **regression tests** before merging fixes.
- [ ] Expand factories/builders for complex graphs.

Always require deterministic clocks/network replacements.

### 17.9 AI for debugging

- [ ] Summarize logs into timelines with hypotheses ranked by likelihood.
- [ ] Explain stack traces with symbolicated references when provided.
- [ ] Propose **minimal repro** scripts or test harness stubs.
- [ ] Contrast **actual vs expected** behavior referencing specs.
- [ ] Produce **debugging checklist** (permissions, lifecycle, async gaps).

### 17.10 AI for release engineering

- [ ] Draft **changelog** entries per merged PR labels.
- [ ] Prepare **store reviewer notes** highlighting gated flows.
- [ ] Enumerate **permission manifest changes** vs prior release.
- [ ] Summarize **crash clusters** from Crashlytics/Sentry exports (redacted).
- [ ] Generate **rollout checklist** (monitoring, thresholds, owners).

### 17.11 AI safety checklist

- [ ] Never provide production secrets/API keys to models or MCP tools.
- [ ] Never approve destructive shell/db/git commands without reading rationale.
- [ ] Never allow direct pushes to `main`/protected branches from agents.
- [ ] Never run unreviewed migrations against shared environments.
- [ ] Always review full diffs—even “mechanical” codegen.
- [ ] Always run tests touching impacted surfaces.
- [ ] Always run `flutter analyze` before merge.
- [ ] Always verify package versions against **pub.dev** / trusted release channels.
- [ ] Always scan generated code for **architecture drift**.

### 17.12 AI tools plan by maturity level

| Level | Mode | Use AI for | Required guardrails |
| --- | --- | --- | --- |
| **1 — Manual assistant** | Chat‑only | Explain errors, clarify specs, draft docs | Human verification |
| **2 — IDE assistant** | Inline AI | Completions, quick refactors | Analyzer + spot tests |
| **3 — Agent workflow** | Multi‑file agent | Planned refactors & fixes | Feature branch; scoped tasks; `PLAN.md`; `REPORTS.md`; diff review; CI green |
| **4 — MCP workflow** | Connected context | Repo/issue/design/schema aware answers | Read‑mostly servers; dev sandboxes; secret hygiene; human‑approved writes |
| **5 — Team workflow** | Shared standards | Templates, ADRs, review bots, release automation | Org‑wide policy; training; periodic audits |

---

## 18. Advanced Flutter

- [ ] **Custom `RenderObject`** when framework widgets cannot express constraints efficiently.
- [ ] **Advanced animations**: staggered sequences, physics, nested controllers.
- [ ] **`CustomPainter`** for bespoke visuals at performance cost bounds.
- [ ] **Advanced platform channels**: background threads, codec performance.
- [ ] **Flutter web**: CanvasKit/HTML renderer trade‑offs; SEO limits.
- [ ] **Desktop**: menu bars, window management, accessibility differences.
- [ ] **Packages & plugins**: federated plugin architecture — [Developing packages](https://docs.flutter.dev/packages-and-plugins/developing-packages)
- [ ] **Monorepo scaling**: shared lint/format; codegen pipelines.
- [ ] **Design systems**: tokenized theming bridging design tooling & code.
- [ ] **White‑label / multi‑flavor**: runtime branding vs compile‑time flavors.
- [ ] **Complex navigation graphs**: multi‑stack shells across nested routers.

---

## 19. Learning path by level

| Level | Focus areas |
| --- | --- |
| **Beginner** | Dart basics · Flutter widgets · Layout · Navigation basics · Simple REST integration |
| **Junior** | State management · Local storage · Forms · Authentication flows · Error handling · Foundational tests |
| **Middle** | Architecture · Advanced state mgmt · CI/CD · Performance tuning · Platform integrations · Store releases |
| **Senior** | System design · Modular architecture · Team standards · Security Programs · Monitoring & SLOs · AI-assisted workflows · Mentorship & review culture |

---

## 20. Recommended resources

Grouped for quick bookmarking. Prefer official docs; ecosystem packages listed when no single canonical doc exists.

### Dart

| Link | Why |
| --- | --- |
| [Dart language](https://dart.dev/language) | Canonical syntax & semantics |
| [Effective Dart](https://dart.dev/effective-dart) | Style & API design guidance |
| [Dart analyzer](https://dart.dev/tools/analysis) | Static analysis configuration |
| [Dart CLI](https://dart.dev/tools/dart-tool) | `dart fix`, `dart compile`, tooling |

### Flutter

| Link | Why |
| --- | --- |
| [Flutter docs home](https://docs.flutter.dev/) | Entry hub |
| [Widgets intro](https://docs.flutter.dev/ui/widgets) | Composition foundations |
| [Architectural overview](https://docs.flutter.dev/resources/architectural-overview) | Framework mental model |
| [Flutter CLI](https://docs.flutter.dev/reference/flutter-cli) | Automation surfaces |

### Architecture & structure

| Link | Why |
| --- | --- |
| [Architecture recommendations](https://docs.flutter.dev/app-architecture/recommendations) | Opinionated baseline |

### State management

| Link | Why |
| --- | --- |
| [State management options](https://docs.flutter.dev/data-and-backend/state-mgmt/options) | Compare approaches |
| [provider](https://pub.dev/packages/provider) | Lightweight inherited wiring |
| [Riverpod](https://riverpod.dev/) | Compile‑safe scoped DI |
| [flutter_bloc](https://pub.dev/packages/flutter_bloc) | Explicit state machines |

### Testing

| Link | Why |
| --- | --- |
| [Testing overview](https://docs.flutter.dev/testing) | Official testing docs |
| [Integration tests](https://docs.flutter.dev/testing/integration-tests) | Device‑level harness |

### Performance

| Link | Why |
| --- | --- |
| [Performance](https://docs.flutter.dev/perf) | Guides & checklists |
| [DevTools performance](https://docs.flutter.dev/tools/devtools/performance) | Profiler workflows |
| [Impeller](https://docs.flutter.dev/perf/impeller) | Rendering backend notes |

### Security

| Link | Why |
| --- | --- |
| [OWASP MASVS](https://owasp.org/www-project-mobile-app-security/) | Mobile security baseline |

### CI/CD & release

| Link | Why |
| --- | --- |
| [GitHub Actions docs](https://docs.github.com/en/actions) | Workflow automation |
| [GitLab CI/CD](https://docs.gitlab.com/ci/) | Built‑in pipelines & runners |
| [GitLab CI YAML reference](https://docs.gitlab.com/ci/yaml/) | `.gitlab-ci.yml` authoring |
| [Fastlane](https://fastlane.tools/) | Mobile release lanes |
| [Codemagic](https://codemagic.io/start/) | Flutter CI/CD |
| [Shorebird docs](https://docs.shorebird.dev/) | OTA patches |

### Collaboration (Git hosts)

| Link | Why |
| --- | --- |
| [GitLab documentation](https://docs.gitlab.com/) | Repositories, MRs, issues, permissions |
| [GitLab merge requests](https://docs.gitlab.com/user/project/merge_requests/) | Review workflow |

### AI tools

| Link | Why |
| --- | --- |
| [Anthropic documentation](https://docs.anthropic.com/) | Claude models & API references |
| [Claude Code documentation](https://code.claude.com/docs/en/overview) | Agentic CLI/tooling guidance |
| [Cursor documentation](https://cursor.com/docs) | IDE agent platform |
| [Cursor Agent best practices](https://cursor.com/blog/agent-best-practices) | Operational guidance |
| [GitHub Copilot](https://docs.github.com/en/copilot) | Org‑managed assistant |

### MCP

| Link | Why |
| --- | --- |
| [MCP introduction](https://modelcontextprotocol.io/docs/getting-started/intro) | Protocol primer |
| [MCP tools concept](https://modelcontextprotocol.io/docs/concepts/tools) | Capability model |

### Learning accelerators (official Flutter media)

| Link | Why |
| --- | --- |
| [Widget of the Week (YouTube)](https://www.youtube.com/playlist?list=PLjxrf2q8roU23XGwz3Km7sQZFTdB996iG) | Rapid widget literacy |
| [Package of the Week (YouTube)](https://www.youtube.com/playlist?list=PLjxrf2q8roU1quF6ny8oFHJ2gBdrYN_AK) | Ecosystem orientation |

---

### Closing cadence for teams

Schedule quarterly passes through §12–§16 plus §17.11 to prevent operational drift as tooling evolves.
