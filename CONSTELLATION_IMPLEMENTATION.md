# Unnamed Constellation Atlas — scientific, editorial, interactive web + Android

## Identity and separation

This is a **new** astronomy and constellation experience, not the previously completed Seasify project. Leave brand identity unassigned until the user names it. Do not re-use protected code, design assets or naming from Seasify without explicit permission and license compliance.

## Product hypothesis

Existing planetariums are strong at astronomy simulation. The new project should distinguish itself through approachable constellation-first discovery, excellent interface craft, accurate sky positioning, thoughtful editorial content, and clear pathways from a constellation story to observing the real sky.

## Explicit scope

- Premium, responsive public website.
- Interactive 3D/2.5D-feeling sky explorer with astronomy-appropriate data.
- Individual constellation atlas pages, guided discovery and science facts.
- Accurate coordinate/time/location behavior, not decorative star placement marketed as real data.
- Source-attributed imagery and scientific citations.
- Crawlable content, sitemap, metadata and `robots.txt`.
- Optional webcam/gesture-driven navigation if a reliable prototype passes testing.
- Android companion path evaluated by actual UX, licensing and performance requirements.
- 30–40 genuinely integrated React components, target 36 from `DESIGN_CONSTITUTION.md`.
- No generated generic card-page aesthetic. Design references to be supplied later must be faithfully interpreted.

## Do not build as v1 requirements

- A replacement for all Stellarium catalog or telescope features.
- Synthetic 'live' astronomical data from a general text model.
- An AI chatbot as the homepage's primary feature.
- A mandatory sign-up wall for simple constellation exploration.
- A streaming video service or social network.
- Unverified augmented reality camera overlays.
- A cloud backend merely to host static constellation pages.
- An Android app requiring full duplicate engineering of the web interface without justification.

## Research and astronomy source policy

- IAU constellation list/names/boundaries as a canonical naming reference.
- Astronomical calculations from vetted ephemeris/astronomy libraries.
- NASA or appropriate space agency APIs for imagery/events only where they actually offer the required data.
- Separate fixed-star catalog information from apparent observer-relative placement.
- Distinguish constellation figures/asterisms from official sky-area boundaries.
- Record coordinate systems and reference epochs in data contracts.
- Handle observer latitude, longitude, date, timezone, horizon and daylight saving precisely.
- Check whether apparent/refraction corrections are included in the selected astronomy library.
- Track object magnitude and whether the sky viewer renders this physically or illustratively.
- Record every dataset version, license and attribution.
- Scientific facts must be reviewable to a source; mythological stories must indicate tradition or cultural origin.

## Data candidates

- `Constellation`: id, IAU abbreviation, official name, region, boundary metadata, source.
- `Star`: catalog id, RA, Dec, reference epoch, magnitude, spectral metadata, names.
- `ConstellationMembership`: star ID, constellation ID, link type, source version.
- `AsterismEdge`: pair of star IDs, tradition, source reference.
- `DeepSkyObject`: catalog ID, constellation association, coordinates, object type.
- `EditorialArticle`: slug, title, factual sources, fact-check status, revision date.
- `AstronomyAsset`: file/URL, rights, caption, creator, source, attribution.
- `Observation`: observer position/time, computed altitude/azimuth, visibility conditions.
- `UserBookmark`: constellation ID, local storage key or account identity if implemented.
- `InteractiveLesson`: chapter sequence, question IDs, references and accessibility text.

## Main user journeys

1. Visitor lands on editorial home and sees a compelling, real astronomical hero.
2. Visitor opens constellation atlas and filters by name or region.
3. Visitor chooses Orion and sees its pattern, notable stars, science and stories.
4. Visitor opens the interactive viewer with constellation highlighted.
5. Visitor selects their city manually or grants location permission.
6. Visitor chooses a date/time and sees correct sky orientation and visibility.
7. Visitor taps a star and sees credible data and reference details.
8. Visitor enters a guided visual lesson with accessible narrative.
9. Visitor saves a discovery without mandatory account creation.
10. Visitor returns from a search engine to a standalone constellation page with content fully visible.
11. Mobile visitor uses touch controls and reduced-graphics mode.
12. Optional Android visitor launches the PWA/TWA/native shell and resumes an observing session.

## Architecture candidates to compare

- Next.js or equivalent SSR/SSG for public editorial content; compare build and deployment costs with static generation.
- React + a deliberate visualization engine for the sky; evaluate Canvas/WebGL library portability and accessibility.
- Existing astronomy math library for celestial coordinate conversions, not improvised formulas.
- JSON/content repository for editorial and star catalog data when update needs are modest.
- Client-side bookmarks initially; auth only if a validated cross-device requirement exists.
- Small serverless API only if needed for cache/proxy, rate limiting or licensed external data.
- Android PWA/TWA first if the web renderer performs; native implementation only when camera/GPU/offline UX justifies it.

## Website route map

- `/` — editorial landing, immediate explorer entry, curated highlights.
- `/atlas` — all constellations, filters and discovery paths.
- `/constellations/[slug]` — crawlable individual profile with history/science/observation.
- `/sky` — full interactive sky explorer.
- `/observe` — observing guidance and date/location controls.
- `/stories` — curated science and mythology guides.
- `/stories/[slug]` — long-form illustrated discovery journey.
- `/events` — factual astronomy event list when source available.
- `/about` — purpose, data methodology and accuracy limitations.
- `/sources` — science/asset provenance, licenses and credits.
- `/privacy` — location/camera/storage disclosure if used.
- `/sitemap.xml` and `/robots.txt` — crawl configuration.

## Visual exploration engine

- Define celestial coordinate inputs and conversions explicitly.
- Determine projection (spherical, stereographic, equirectangular or selected view) before drawing.
- Render points in physically consistent orientation for selected location/time.
- Separate star brightness, horizon, atmospheric illustration and constellation lines into layers.
- Implement smooth drag-to-pan and zoom with stable pointer handling.
- Support touch gestures and keyboard shortcuts for essential navigation.
- Maintain selected object as stable state through viewport movement.
- Avoid representing viewport position as geolocation/astronomy state.
- Provide coordinate and scale information in observer mode.
- Recompute only required transforms when time/location changes.
- Use frame-rate budgeting and lower-detail mode for mobile hardware.
- Support browser/device pixel ratio without blurry labels.
- Test numeric precision and cross-hemisphere orientation.
- Show error or unavailability state if astronomical dataset has not loaded.
- Provide static canvas fallback and textual atlas when WebGL is unsupported.

## Webcam and gesture-control research spike

- Treat camera as opt-in and off by default.
- Never process/upload video without clear disclosure and permission.
- Prototype limited actions: pan left/right, zoom and reset.
- Evaluate false positives, poor lighting, camera absence, accessibility and fatigue.
- Show explicit gesture calibration and live camera status.
- Require a visible pause/stop control.
- Provide mouse/touch/keyboard parity.
- Test performance on modest laptop webcams and mobile devices.
- Remove from v1 if it compromises astronomy accuracy, battery, latency or user trust.

## Content engine

- Create a structured template for each constellation page while ensuring each page provides materially unique information.
- Include official name, abbreviation, location in celestial sphere and major identifiable stars.
- Include one accurately drawn pattern diagram and one relevant, licensed hero image where possible.
- Separate 'how to locate' instructions by hemisphere/season and verify against an ephemeris.
- Include individual science facts with sources and dates when volatile.
- Include mythology only with named tradition and neutral framing.
- Include links to neighboring constellations and relevant deep-sky objects.
- Avoid AI-generated filler paragraphs or scientifically unverified superlatives.
- Initial target: 12–20 substantive pages before scaling to all 88 constellations.
- Add review queue for remaining pages; prioritize high-interest, observably distinctive ones.
- Use editorial checklists for accuracy, citations, imagery rights and clarity.

## SEO and crawlability

- Public pages must have server-rendered or statically generated title/description and meaningful text.
- Each constellation gets canonical slug and unique title.
- Include structured internal links between atlas, guide, story and sky view.
- Generate `sitemap.xml` from published routes; exclude drafts and internal endpoints.
- Set `robots.txt` to permit crawlable public pages while excluding unnecessary private/technical paths.
- Do not treat `robots.txt` as an index/noindex guarantee.
- Use canonical links for duplicate parameterized URLs.
- Use stable route structure and avoid thousands of thin autogenerated pages.
- Optimize Core Web Vitals by lazy-loading 3D client code and images.
- Ensure editorial text is usable if JavaScript fails or canvas cannot initialize.
- Provide real alt text, figure captions and descriptive headings.
- Include an accurate sources page and transparent data update methodology.

## Content and space API validation

- Confirm API availability, authentication, quotas and CORS behavior before implementation.
- Distinguish live image APIs from numerical ephemeris services.
- Use rate-limited caching and fallback when a live service is unavailable.
- Label when last refreshed; never display fabricated fresh status.
- Build client tests with recorded, permission-compatible fixtures.
- Validate date-based API results across timezones.
- Consider astronomy dataset download licensing and bandwidth before bundling on Android.
- Avoid exposing private API keys in public browser bundles.

## Android strategy gate

- Stage 1: installable PWA with mobile UX and offline reading where feasible.
- Stage 2: evaluate Trusted Web Activity packaging if Play Store deployment is desired and web capability suffices.
- Stage 3: evaluate native Android only if performance, gestures, camera/AR, accessibility or offline maps require it.
- If native: use structured shared data contracts, not copy/paste web implementation.
- Determine target Android API level based on current Play requirements.
- Plan package identifier, app icon, signing and release configuration only with user-supplied account control.
- Verify startup, storage, permissions, offline modes, performance, orientation and screen-density handling.
- Do not claim store upload unless actual user authorization and developer console access exist.

## Candidate component contract

The 36-item component inventory lives in `DESIGN_CONSTITUTION.md` and is the authoritative minimum functional map. For each component record:

- Source or original implementation license.
- Route or parent module using it.
- Props and state dependencies.
- Accessibility semantics.
- Responsive behavior and empty/error states.
- Interaction test or visual acceptance check.
- Performance budget where heavy.
- Test coverage and known defects.

A component is **not counted as integrated** merely because its file exists or is imported but never displayed.

## Accessibility and astronomy pedagogy

- Make map exploration optional for users who prefer text.
- Supply keyboard navigation for selection or provide an equivalent list UI.
- Use readable labels and avoid star-dot selection only.
- Explain right ascension and declination with sensible units.
- Avoid confusing apparent proximity with physical proximity.
- Distinguish mythology from astronomy in visual labels.
- Avoid false precision in star distances or observer position.
- Make reduced motion, high contrast and mobile usability first-class.
- Test interface with small screens and slow CPU/GPU emulation.

## Acceptance tests

- STAR-AT-001: static site builds and all published routes resolve.
- STAR-AT-002: atlas search returns a known constellation with correct abbreviation.
- STAR-AT-003: constellation page has factual references and unique editorial content.
- STAR-AT-004: sky canvas loads with selected date/time and valid data.
- STAR-AT-005: time change updates object placement reproducibly.
- STAR-AT-006: latitude/longitude changes produce plausible sky orientation.
- STAR-AT-007: stars can be selected by pointer and via accessible alternative.
- STAR-AT-008: constellation overlay toggles without losing selected star.
- STAR-AT-009: pan/zoom remains smooth on representative hardware.
- STAR-AT-010: unsupported WebGL shows meaningful fallback.
- STAR-AT-011: reduced motion setting eliminates unnecessary effects.
- STAR-AT-012: location permission denial allows manual location selection.
- STAR-AT-013: source/asset credits appear where content is used.
- STAR-AT-014: failed astronomy API request shows truthful offline/fallback state.
- STAR-AT-015: no exposed private API secrets in client assets.
- STAR-AT-016: 12–20 published editorial pages pass fact/source review.
- STAR-AT-017: `/robots.txt` and `/sitemap.xml` return intended content.
- STAR-AT-018: metadata and canonical URLs are correct for published profiles.
- STAR-AT-019: desktop/tablet/mobile screenshots match approved reference criteria.
- STAR-AT-020: 36 target React components have actual usage and acceptance evidence before counting complete.
- STAR-AT-021: optional webcam features do not activate without consent.
- STAR-AT-022: if webcam implemented, stop/pause action and non-webcam controls work.
- STAR-AT-023: PWA manifest/icons/offline behavior are tested before Android packaging.
- STAR-AT-024: Android artifact builds and works on emulator/device if included in release scope.
- STAR-AT-025: clean installation instructions reproduce the demo.

## Red-team cases

- North vs south hemisphere reversed labels.
- Seasonal sky guidance that ignores local time.
- Daylight-saving errors or UTC confusion.
- Star positions calculated with inconsistent reference epoch.
- External imagery endpoint blocked by CORS.
- Bad API quota handling.
- Font/image load causing enormous layout shift.
- Search engine cannot render content because only WebGL exists.
- Camera permissions denied on insecure origin.
- Scientific claim lacks source.
- Third-party constellation art copied without license.
- Component library used decoratively but no real interaction.
- Android WebView performance worse than responsive website.
- Huge asset bundle and unsupported low-end hardware.
- False claim of a live observation when data is static.

## Release evidence

- Site build and functional browser traces.
- Approved screenshots and mobile-responsive audit.
- Astronomy calculation test cases with expected outputs.
- Content source/copyright ledger.
- Component integration inventory with usage/tests.
- SEO generated files and crawl review.
- Android APK/AAB evidence if built; no fictitious store publication.
- Unimplemented camera/native features clearly described.
