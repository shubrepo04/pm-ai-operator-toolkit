# PRD: Pollen Calendar & Safety Map
**Feature request submitted:** 2026-03-20
**PM:** Shubham Shukla
**Status:** Draft

---

## PROBLEM STATEMENT

Travellers and allergy sufferers planning trips across Europe have no reliable, real-time way to understand where and when pollen levels will be dangerous for them. Pollen types vary by region, season, and elevation — tree pollen peaks in spring, grass pollen in summer, weed pollen in autumn — and a traveller allergic to birch pollen in Germany may have no reaction in southern Spain at the same time of year.

Today, users either rely on generic national weather forecasts that don't surface pollen data prominently, or they search across fragmented third-party allergy sites that aren't integrated into their travel planning workflow.

**Who has this problem:** Allergy sufferers (estimated 40% of Europeans have seasonal allergic rhinitis) who travel within or to Europe and want to plan around pollen exposure. This includes leisure travellers, business travellers, and families travelling with children who have allergies.

**How often:** Every trip planned during pollen season (March–October). For frequent travellers, this is a recurring weekly or monthly decision.

**What happens if we don't solve it:** Users with pollen allergies continue to have poor travel experiences — unexpected allergy attacks, emergency pharmacy visits, cancelled outdoor activities — and associate those experiences with poor trip planning, not with our product's absence. Worse, a competitor weather or travel app adds this feature first and becomes the default for a high-value, high-loyalty user segment.

---

## SUCCESS METRICS

**1. Pollen Map feature adoption rate**
- *What we measure:* % of active users who open the Pollen Map at least once per session during pollen season (March–October)
- *Baseline:* 0% (new feature)
- *Target:* 15% of active users within 90 days of launch

**2. Return visit rate for pollen map users**
- *What we measure:* % of users who view the Pollen Map more than once within a 7-day period
- *Baseline:* N/A
- *Target:* 40% of pollen map users return within 7 days — indicating the map is being used for ongoing trip planning, not just casual discovery

**3. Session duration uplift for pollen map users vs. non-users**
- *What we measure:* Average session length for users who engage with the Pollen Map vs. those who don't
- *Baseline:* Current average session duration (to be pulled from analytics before launch)
- *Target:* Pollen map users show ≥20% longer average session duration within 60 days of launch

**4. Pollen-related support complaints during pollen season**
- *What we measure:* Volume of user feedback or support tickets citing inaccurate or missing pollen information
- *Baseline:* Current complaint volume (pull from support logs)
- *Target:* <5 pollen-related complaints per 10,000 active users per month — indicating data accuracy is trusted

---

## USER STORIES

**1.** As a **traveller with a grass pollen allergy planning a summer road trip across Europe**, I want to **see a map showing which regions have high, medium, or low grass pollen levels on the dates I'm travelling**, so that **I can route my trip through lower-risk areas and avoid allergy attacks**.

**2.** As a **parent travelling with an allergic child**, I want to **check pollen forecasts for my destination city up to 7 days ahead**, so that **I can pack the right medication and plan indoor vs. outdoor activities accordingly**.

**3.** As a **business traveller flying into a new European city**, I want to **get a pollen alert for my destination as part of my weather briefing**, so that **I'm not caught off guard by a high-pollen environment I wasn't expecting**.

**4.** As a **user who checks the weather app daily**, I want to **see pollen type and severity alongside the standard weather forecast**, so that **pollen becomes part of my daily routine check, not a separate search**.

**5.** As a **user with multiple pollen allergies (e.g., birch AND grass)**, I want to **filter the map by pollen type**, so that **I see only the allergens that are relevant to me, not a generic combined index**.

---

## SOLUTION OVERVIEW

We are building a **Pollen Calendar and Safety Map** — an interactive, map-based view within the existing weather app that shows pollen activity levels across Europe by region, filterable by pollen type and date.

**What the user experiences:**

1. A new **"Pollen"** entry point appears in the app's navigation (tab or card on the home screen during pollen season, March–October).
2. The user lands on a **Europe-wide map** with colour-coded regions (green = low, amber = moderate, red = high, grey = no data) showing current pollen levels.
3. The user can **filter by pollen type**: Tree (birch, alder, hazel, oak), Grass, Weed (mugwort, ragweed). Default view shows combined index.
4. The user can **advance the date** up to 7 days forward to see forecast pollen levels — enabling pre-trip planning.
5. Tapping a region opens a **detail card**: pollen type breakdown, severity today vs. next 3 days, and a short plain-English summary ("Birch pollen is peaking in this area this week. If you're sensitive, consider an antihistamine before outdoor activities.").
6. Users can **save a location** to receive a pollen alert notification if levels are forecast to rise to High before or during their trip.

**What it deliberately does not do (v1):**
- Does not provide personalised medical advice or dosage recommendations
- Does not integrate with calendar or travel booking apps
- Does not cover regions outside Europe
- Does not include real-time air quality or pollution data (separate feature)

---

## SCOPE

**IN SCOPE — v1:**
- Interactive pollen map covering Europe (EU + UK + Switzerland + Norway)
- Pollen types: Tree (combined), Grass, Weed (combined) — not species-level granularity in v1
- 3-level severity scale: Low / Moderate / High
- 7-day forecast view with date selector
- Region detail card with type breakdown and plain-English summary
- Filter by pollen type (single selection)
- Save location + push notification when pollen rises to High (opt-in)
- Seasonal availability: map is surfaced March–October; off-season the entry point shows "Pollen season starts in [X weeks]"

**OUT OF SCOPE — v1:**
- Species-level pollen breakdown (e.g., birch vs. oak vs. alder separately) — too granular for v1, evaluate post-launch
- Coverage outside Europe
- Personalised allergy profiles (user inputs their specific allergens) — v2 candidate
- Integration with calendar or flight/hotel booking platforms
- Real-time air quality or particulate matter data
- Medical recommendations or symptom tracking
- Offline access to pollen maps

---

## OPEN QUESTIONS

1. **Data source:** Which pollen data provider are we using — SILAM, Copernicus Atmosphere Monitoring Service (CAMS), or a commercial API like BreezoMeter or Ambee? Data quality, coverage gaps, update frequency, and cost all differ significantly. This must be decided before design begins.

2. **Update frequency:** How often does pollen data refresh — hourly, 6-hourly, daily? This affects both the UX copy ("Updated every 6 hours") and the infrastructure cost. What's the acceptable staleness threshold for the user?

3. **Regional granularity:** Is the map country-level, NUTS-2 region level, or city-level? City-level is more useful to travellers but requires more data density. What does our data provider support at acceptable cost?

4. **Notification opt-in strategy:** Do we ask users to opt into pollen notifications during onboarding, or only when they first open the Pollen Map? Opt-in timing affects notification reach significantly.

5. **Off-season handling:** What does the experience look like for users who open the app in November–February? Do we show historical pollen data, a "season preview" for next year, or simply hide the feature entirely? Hiding it risks losing any SEO or discovery benefit year-round.

---

## RISKS

**Risk 1: Pollen data inaccuracy damages trust**
- *What could go wrong:* Users with serious allergies rely on our map, travel to a region shown as "Low," and experience a severe allergic reaction because the data was stale, incomplete, or at the wrong granularity.
- *Likelihood:* Medium — pollen forecasting is imprecise by nature; no provider is 100% accurate
- *Severity:* High — trust damage and potential liability
- *Mitigation:* Add a clear disclaimer on every map view ("Pollen forecasts are indicative. Always consult a healthcare provider for medical decisions."). Set user expectations on data freshness and coverage gaps upfront. Display "No data" regions clearly rather than defaulting to Low.

**Risk 2: Low adoption outside pollen season makes the feature feel abandoned**
- *What could go wrong:* We build a feature that 15% of users love March–October and no one touches November–February, creating pressure to deprioritise maintenance and updates.
- *Likelihood:* High — pollen is inherently seasonal
- *Severity:* Medium — acceptable if planned for; problematic if it surprises leadership
- *Mitigation:* Set seasonal KPIs from the start, not annual ones. Plan the off-season experience explicitly (historical view or season countdown). Frame this as a seasonal engagement driver, not a year-round daily active feature.

**Risk 3: Data provider dependency creates cost or reliability risk**
- *What could go wrong:* Our chosen pollen data provider increases API costs, degrades coverage, or loses a key regional partner — forcing us to scramble for an alternative mid-season.
- *Likelihood:* Low-Medium
- *Severity:* High — a broken pollen map during peak season is a support and trust crisis
- *Mitigation:* Negotiate SLA terms with the data provider before launch. Evaluate at least two providers during the discovery phase so we have a fallback. Design the data ingestion layer to be provider-agnostic where feasible.

---

## DEPENDENCIES

| Dependency | Owner | Required by |
|-----------|-------|-------------|
| Pollen data API contract and access | Business Dev / Partnerships | End of Discovery phase |
| Map rendering infrastructure (existing or new tile service) | Platform Engineering | Start of Build phase |
| Push notification system (already built for weather alerts?) | Mobile Engineering | Build phase |
| Design system components for map overlays | Design | Start of Build phase |
| Legal review of health-related disclaimer copy | Legal | End of Design phase |
| App store review (iOS/Android) for new feature section | Mobile Engineering | Testing phase |

---

## TIMELINE ESTIMATE

**Phase 1 — Discovery and design: 3 weeks**
- Evaluate and select pollen data provider (Week 1)
- Define regional granularity and data update frequency (Week 1)
- Design map UI, filter interaction, detail card, and notification flow (Weeks 2–3)
- Legal review of disclaimer copy (Week 3)

*Assumption: Pollen data provider evaluation can run in parallel with design. If procurement takes longer than 2 weeks, Phase 1 extends.*

**Phase 2 — Build: 5 weeks**
- Data ingestion pipeline and API integration (Weeks 1–2)
- Map rendering with colour-coded overlay (Weeks 2–3)
- Filter by pollen type + date selector (Week 3)
- Region detail card (Week 4)
- Save location + push notification (Week 5)

*Assumption: Map tile rendering infrastructure already exists from the weather map feature. If not, add 2 weeks.*

**Phase 3 — Testing and launch: 2 weeks**
- QA across iOS and Android, including edge cases (no data regions, off-season state) (Week 1)
- Beta with 500 internal/external users during active pollen season (Week 1)
- App store submission and review (Week 2)
- Staged rollout: 10% → 50% → 100% over 5 days

**Total estimate: 10 weeks from kickoff to full rollout**

*Critical assumption: This timeline assumes launch during pollen season (before June). If the feature misses the March–June window, the next meaningful launch opportunity is March of the following year. Do not slip past May.*

---

## IMPORTANT INSTRUCTIONS FOR PRD GENERATOR

Before writing any PRD, always ask clarifying questions first. Do not assume platform, audience, scope, timeline, or business context. Every assumption made without asking is a risk that shows up later as a wrong PRD.

**Always ask before writing:**
1. What platform is this for? (web, iOS, Android, all?)
2. Who is the primary user — and is there a secondary user?
3. Is there a target launch date or business deadline driving this?
4. Are there known constraints — technical, legal, budget, or team size?
5. Has any discovery or research already been done on this problem?

No filler. No assumptions. Ask first, write second.
