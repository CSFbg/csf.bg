# CSF.BG Content Update Guide

This document contains instructions for researching and updating each section of csf.bg. Use it to create deep research tasks with AI tools, then compare findings against the current site content.

---

## General Principles

- **All page content is inline HTML** (no external JSON/API calls for lichnosti, organizacii, sabitia). Data must be embedded directly in the HTML for SEO.
- **kompanii.html and sertifikacii.html** use inline JavaScript arrays (`const COMPANIES = [...]`, `const CERTS = [...]`).
- **Alphabetical order**: lichnosti.html entries are sorted A-Z by Bulgarian first name. kompanii.html is grouped by category (Products, Bulgarian Services, International Services, Distribution, Training).
- **LinkedIn is the primary source** for people data. Always verify current role before adding/updating.
- **papagal.bg** is used for linking organizations without websites to their Bulgarian commercial registry (ЕИК). URL format: `https://papagal.bg/eik/{EIK_NUMBER}/{SUFFIX}` — the suffix varies per entity, find it by searching on papagal.bg.

---

## 1. Личности (lichnosti.html)

**What it contains**: 105+ cybersecurity leaders, CISOs, experts, organizers, and public servants in Bulgaria.

**Suggested update cadence**: Every 2-3 months

### How to research

1. **LinkedIn search for Bulgarian cybersecurity professionals**:
   - Search URL: `https://www.linkedin.com/search/results/people/?keywords=cybersecurity&origin=FACETED_SEARCH&geoUrn=%5B%22105333783%22%5D`
   - Also search for: CISO, information security, penetration tester, SOC, incident response
   - Filter by Bulgaria location

2. **Favikon influencer ranking**:
   - URL: `https://creator.favikon.com/ranking/it-tech/cybersecurity/linkedin/bulgaria/`
   - Cross-reference against current list, add missing people who are genuinely contributing (not just random profiles)

3. **Event speaker lists**:
   - BSides Sofia speakers: check `https://securitybsides.bg/` program archives
   - CyberSecurityTalks Bulgaria: check `https://cybersecuritytalks.bg/` past events
   - ISACA Sofia events: check `https://isaca-sofia.org`
   - OWASP Sofia: check `https://owasp.bg`
   - InfoSec SEE conference: check `https://www.infosec-conference.com/`

4. **Organization boards**:
   - Check each organization in organizacii.html for their management/board members
   - ISACA Sofia Chapter board: find on their website
   - Bulgarian Cybersecurity Association (BCSA): check `https://cybersecbg.org`
   - Women4Cyber Bulgaria: check `https://women4cyber.bg/нашият-екип/`

5. **CISO directory research**:
   - Search LinkedIn for "CISO Bulgaria", "Head of Information Security Bulgaria", "Information Security Officer Bulgaria"
   - Check major Bulgarian companies: banks (Fibank, DSK, UBB, Postbank, tbi bank, Nexo, myPOS), telcos (Yettel, A1, Vivacom), tech companies (SAP, Paysafe, DXC, MentorMate), media (bTV), gaming (Amusnet)
   - Government: Ministry of e-Government, GDBOP, CERT Bulgaria, DANS

### Inclusion criteria

Only add people who meet at least one of:
- Management board member of a cybersecurity organization
- CISO, Head of InfoSec, or equivalent leadership role
- Event organizer or regular conference speaker
- Significant community contributor (open-source, education, mentoring)
- Government official with cybersecurity responsibilities

### Data structure per person (inline HTML)

Each entry needs:
- `data-role`: Лидер, Експерт, Организатор, or Държавен
- `data-name`: lowercase Bulgarian name for search
- `data-search`: lowercase concatenation of name + title + association
- Name linked to LinkedIn profile
- Title / Role (current position)
- Association (company and/or organization)
- Role badge
- LinkedIn link in last column

### Verification checklist

- [ ] Is the person's LinkedIn profile still active?
- [ ] Is the listed role/company still current? (People change jobs frequently)
- [ ] Are there new CISOs at major Bulgarian companies not yet listed?
- [ ] Have any listed people left Bulgaria or changed careers?
- [ ] Are there new event organizers for recurring events?

---

## 2. Компании (kompanii.html)

**What it contains**: 55+ cybersecurity companies operating in Bulgaria with service tags (SOC, MSSP, Pentest, ISO).

**Suggested update cadence**: Every 3-4 months

### How to research

1. **Clutch.co Bulgaria cybersecurity**:
   - Search: `https://clutch.co/bg/it-services/cyber-security`
   - Filter by Bulgaria location
   - Check company profiles for services, size, focus

2. **LinkedIn company search**:
   - Search for cybersecurity companies in Bulgaria
   - Check company pages for employee count, services offered

3. **Papagal.bg for company registry data**:
   - Search by company name to find ЕИК
   - URL format: `https://papagal.bg/eik/{EIK}/{suffix}`
   - Useful for verifying company is still active

4. **Google search queries**:
   - `"cybersecurity" OR "киберсигурност" site:linkedin.com/company Bulgaria`
   - `"penetration testing" OR "пентест" company Bulgaria`
   - `"SOC" OR "MSSP" Bulgaria cybersecurity`
   - `"ISO 27001" consulting Bulgaria`

5. **Existing company websites**:
   - Visit each listed company's website to verify they're still operational
   - Check for new service offerings (SOC, MSSP flags may need updating)
   - Verify URL still works (companies rebrand/change domains)

### Data structure per company

```javascript
{
  name: 'Company Name',
  size: 'Малка|Средна|Голяма',        // Small/Medium/Large
  category: 'Услуги|Продукт|Дистрибуция|Обучения',
  origin: 'Българска|Международна',
  focus: 'Bulgarian description of services',
  url: 'https://company-website.com/',
  soc: 0|1,      // Operates a SOC
  mssp: 0|1,     // Managed Security Service Provider
  pentest: 0|1,  // Offers penetration testing
  iso: 0|1       // ISO 27001 consulting/certification
}
```

### Service tag definitions

- **SOC**: Company operates or offers Security Operations Center services (monitoring, alerting, L1-L3 analysis)
- **MSSP**: Managed Security Service Provider — provides outsourced security monitoring and management
- **Pentest**: Offers penetration testing, vulnerability assessment, red team services
- **ISO**: Provides ISO 27001 consulting, implementation, auditing, or certification support

### Verification checklist

- [ ] Are all company websites still active?
- [ ] Have any companies been acquired, merged, or shut down?
- [ ] Are there new cybersecurity companies not yet listed? (Check Clutch, LinkedIn, event sponsors)
- [ ] Do service tags (SOC/MSSP/Pentest/ISO) still reflect current offerings?
- [ ] Are company sizes still accurate?

---

## 3. Организации (organizacii.html)

**What it contains**: Associations, foundations, communities, initiatives, government institutions, and European organizations related to cybersecurity in Bulgaria.

**Suggested update cadence**: Every 4-6 months

### How to research

1. **Check each organization's website** for:
   - Updated leadership/board members
   - New initiatives or programmes
   - Changed URLs or branding

2. **LinkedIn organization pages**:
   - Search for new cybersecurity organizations in Bulgaria
   - Check existing org pages for leadership changes

3. **Papagal.bg registry**:
   - For organizations without websites, link to their ЕИК page
   - Verify organizations are still registered and active

4. **Government sources**:
   - Ministry of e-Government: `https://egov.government.bg`
   - CERT Bulgaria: `https://www.govcert.bg`
   - NCC (National Coordination Centre): `https://ncc.egov.bg`

5. **European organizations with Bulgarian chapters**:
   - ENISA: check for new Bulgarian involvement
   - ECSO: European Cyber Security Organisation
   - Women4Cyber: check for new chapters or initiatives

### People linked to organizations

Each organization card can have an `org-people` section linking key people to their LinkedIn profiles. When updating organizations, also verify:
- Are the linked people still in leadership roles?
- Are there new board members or chairs?
- Cross-reference with lichnosti.html (people should appear in both)

### Verification checklist

- [ ] Are all organization websites still active?
- [ ] Have any organizations been dissolved or merged?
- [ ] Are linked people still in their listed roles?
- [ ] Are there new cybersecurity organizations or chapters in Bulgaria?
- [ ] Have government institutions changed structure or responsibilities?

---

## 4. Събития (sabitia.html)

**What it contains**: Recurring conferences, meetups, and events in Bulgaria with linked organizers.

**Suggested update cadence**: Every 1-2 months (events change frequently)

### How to research

1. **Event discovery platforms**:
   - Meetup.com: `https://www.meetup.com/find/?keywords=cybersecurity&location=bg--sofia`
   - Luma (lu.ma): search for cybersecurity Bulgaria
   - Eventbrite: `https://www.eventbrite.com/d/bulgaria--sofia/cybersecurity/`
   - LinkedIn Events: search for cybersecurity Bulgaria

2. **Known recurring events to track**:
   - BSides Sofia (Annual, Spring): `https://securitybsides.bg/`
   - CyberSecurityTalks (Monthly): `https://cybersecuritytalks.bg/`
   - OWASP Sofia (Bi-monthly): `https://owasp.bg`
   - ISACA Sofia meetings (Monthly): `https://isaca-sofia.org`
   - CyberCLUB Community Day (Annual): `https://cyberclub.bg`
   - DigiPay Forum (Annual, October): `https://digipay.bg`
   - CyberChristmas (Annual, December)
   - InfoSec SEE (Annual, Spring): `https://www.infosec-conference.com/`

3. **People behind events**:
   - Each event card links to organizers via LinkedIn
   - Verify organizer roles haven't changed
   - Add new co-organizers

### Verification checklist

- [ ] Are all event dates/frequencies still accurate?
- [ ] Have any recurring events been discontinued?
- [ ] Are there new recurring cybersecurity events in Bulgaria?
- [ ] Are event websites and links still working?
- [ ] Are linked organizers still active in their roles?

---

## 5. Сертификации (sertifikacii.html)

**What it contains**: 80+ cybersecurity certifications with filters by type, level, vendor, area, and cost.

**Suggested update cadence**: Every 6 months

### How to research

1. **Certification body websites**:
   - CompTIA: `https://www.comptia.org/certifications`
   - (ISC)²: `https://www.isc2.org/certifications`
   - ISACA: `https://www.isaca.org/credentialing`
   - EC-Council: `https://www.eccouncil.org/train-certify/`
   - Offensive Security: `https://www.offsec.com/courses-and-certifications/`
   - GIAC/SANS: `https://www.giac.org/certifications/`
   - Hack The Box: `https://academy.hackthebox.com/preview/certifications`
   - CREST: `https://www.crest-approved.org/`

2. **Paul Jerimy Security Certification Roadmap**:
   - `https://pauljerimy.com/security-certification-roadmap/`
   - Primary reference for comprehensive cert listing

3. **Price verification**:
   - Costs are stored in USD in the data array
   - Displayed in EUR using `USD_TO_EUR = 0.93` conversion
   - Verify exam prices haven't changed (they frequently do)

### Data structure per certification

```javascript
{
  slug: "vendor-certname",
  name: "Full Certification Name",
  abbr: "ABBR",
  body: "Certification Body",
  type: "theoretical|practical",
  level: "beginner|intermediate|advanced",
  cost: 490,  // USD
  areas: ["testing", "networks", "secops", ...],
  description: "English description of what it validates.",
  url: "https://official-cert-page.com/"
}
```

### Valid area tags

`networks`, `secops`, `testing`, `cloud`, `risk`, `management`, `compliance`, `forensics`, `iam`, `architecture`, `software`, `assets`

### Verification checklist

- [ ] Have any certifications been retired or renamed?
- [ ] Are exam prices still accurate?
- [ ] Are there new certifications from existing vendors?
- [ ] Has the `BODY_COLORS` map been updated for any new vendors?
- [ ] Are certification URLs still working?

---

## 6. Регулации (regulacii.html)

**What it contains**: Comprehensive guide to Bulgaria's cybersecurity regulatory framework with interactive assessment tool.

**Suggested update cadence**: Every 6 months (or when new legislation passes)

### How to research

1. **Bulgarian legislation**:
   - Lex.bg for law text: `https://www.lex.bg`
   - National Assembly bills: `https://www.parliament.bg/bg/bills`
   - State Gazette (Държавен вестник): `https://dv.parliament.bg`

2. **EU regulations**:
   - EUR-Lex: `https://eur-lex.europa.eu`
   - Key regulations to track:
     - NIS2: Directive (EU) 2022/2555
     - GDPR: Regulation (EU) 2016/679
     - DORA: Regulation (EU) 2022/2554 + `https://dora.bg`
     - CRA: Regulation (EU) 2024/2847
     - eIDAS 2.0: watch for updates
     - EU AI Act: Regulation (EU) 2024/1689 (may need adding)

3. **Regulatory authority websites**:
   - Ministry of e-Government: `https://egov.government.bg`
   - CERT Bulgaria: `https://www.govcert.bg`
   - CPDP (КЗЛД): `https://cpdp.bg`
   - BNB: `https://www.bnb.bg`
   - FSC (КФН): `https://www.fsc.bg`
   - CRC (КРС): `https://www.crc.bg`
   - DANS: `https://dans.bg`
   - KEVR: `https://www.dker.bg`

4. **National strategies**:
   - Киберустойчива България: `https://cyberbg.eu/`
   - Strategy.bg: `https://www.strategy.bg`
   - MIS Ordinance: `https://e-gov.bg`

### Assessment tool logic

The interactive wizard determines which regulations apply based on:
- **Sector type** (7 categories)
- **Additional traits** (6 multi-select options, shown only for private companies)
- **Size** and **turnover** thresholds

Smart skipping:
- Trust services → instant results (NIS2 + GDPR + eIDAS)
- Finance, telecom, health, energy, public admin → skip traits step (GDPR auto-assumed)
- Private company → full flow including traits

### Verification checklist

- [ ] Has new cybersecurity legislation been adopted in Bulgaria?
- [ ] Have NIS2 implementing acts been published?
- [ ] Are penalty amounts still accurate?
- [ ] Have new sectors been added to NIS2 scope?
- [ ] Have regulatory authority responsibilities changed?
- [ ] Does the assessment tool logic still reflect current law?

---

## 7. Университети (universiteti.html)

**What it contains**: Accredited cybersecurity degree programmes at Bulgarian universities.

**Suggested update cadence**: Every 6-12 months (academic programmes change yearly)

### How to research

1. **University websites**:
   - Check each listed university for new/changed programmes
   - Look for new cybersecurity specializations

2. **NACID (National Agency for Assessment and Accreditation)**:
   - Check for newly accredited programmes
   - Verify existing programme accreditation status

3. **Key universities to monitor**:
   - Technical University Sofia: `https://tu-sofia.bg`
   - NVU "Vasil Levski": `https://nvu.bg`
   - VVMU Vaptsarov: `https://naval-acad.bg`
   - NBU: `https://nbu.bg`
   - Plovdiv University: `https://uni-plovdiv.bg`
   - Varna Free University: `https://vfu.bg`
   - Military Academy Rakovski: `https://rakovski.bg`
   - UniBIT: `https://unibit.bg`
   - ANIS: `https://anis-bg.org`

### Verification checklist

- [ ] Are all programmes still offered and accredited?
- [ ] Have any universities added new cybersecurity programmes?
- [ ] Are study modes (full-time, part-time, distance) still accurate?
- [ ] Have programme names changed?

---

## 8. Курсове (kursove.html)

**What it contains**: Professional cybersecurity courses and training providers in Bulgaria.

**Suggested update cadence**: Every 3-4 months

### How to research

- Check each provider's website for updated course offerings and prices
- Search for new training providers in Bulgaria
- Key providers: SoftUni, EHU, Pragmatic, Progress Education Centre, New Horizons, Cyber360, NIT, Cyber Academy

### Verification checklist

- [ ] Are course prices still accurate?
- [ ] Have any providers added new courses or discontinued old ones?
- [ ] Are there new training providers in the Bulgarian market?

---

## 9. Инструменти (instrumenti.html)

**What it contains**: Cybersecurity tools grouped by category.

**Suggested update cadence**: Every 6 months

### How to research

- Check for new major tool releases or version changes
- Monitor GitHub trending in security category
- Check OWASP project updates
- Verify tool URLs are still active

---

## 10. Книги (knigi.html)

**What it contains**: Curated cybersecurity books in Bulgarian and English.

**Suggested update cadence**: Every 6-12 months

### How to research

- Check Bulgarian publishers (Softpress, Ciela, Helikon) for new cybersecurity translations
- Monitor Amazon/Goodreads for notable new cybersecurity books
- Check if listed books have new editions

---

## 11. Форуми (forumi.html)

**What it contains**: Forums, Discord servers, Facebook groups, Reddit communities.

**Suggested update cadence**: Every 3-4 months

### How to research

- Verify Discord invite links are still active (they expire)
- Check Facebook groups for activity (dead groups should be noted)
- Look for new Bulgarian cybersecurity communities

---

## Research Output Template

When producing research for comparison, use this format per section:

```markdown
## [Section Name] Research - [Date]

### Currently on site
- [List of current entries with key details]

### Found but missing from site
- [New items to add with all required data fields]

### Needs updating
- [Items where data has changed - specify what changed]

### Should be removed
- [Items no longer relevant - specify why]

### Data quality issues
- [Broken links, outdated info, incorrect data]
```

---

## SEO Maintenance

Every page includes: `<title>`, `<meta description>`, `<meta keywords>`, Open Graph tags, Twitter Cards, canonical URL, favicon, and `title` attributes on navigation links. When adding new pages:

1. Add all SEO meta tags in `<head>`
2. Add the page to `sitemap.xml`
3. Add navigation links with `title` attributes in all other pages (desktop dropdown, mobile menu, footer)
4. Ensure single `<h1>` tag per page
5. All `<img>` tags must have `alt` attributes
6. All external links need `target="_blank" rel="noopener"`

### Large screen responsiveness

All pages use:
- Base max-width: `1440px`
- `@media (min-width: 1600px)`: max-width 1600px, font-size 17px
- `@media (min-width: 1920px)`: max-width 1720px, font-size 18px

---

## Suggested Overall Cadence

| Section | Frequency | Priority | Effort |
|---------|-----------|----------|--------|
| Събития | Monthly | High | Low |
| Личности | Every 2-3 months | High | Medium |
| Компании | Every 3-4 months | High | Medium |
| Форуми | Every 3-4 months | Medium | Low |
| Курсове | Every 3-4 months | Medium | Low |
| Организации | Every 4-6 months | Medium | Medium |
| Сертификации | Every 6 months | Medium | Medium |
| Регулации | Every 6 months | High | High |
| Университети | Every 6-12 months | Low | Low |
| Инструменти | Every 6 months | Low | Low |
| Книги | Every 6-12 months | Low | Low |
| Видео ресурси | Every 6 months | Low | Low |
