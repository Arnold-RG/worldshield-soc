# WorldShield SOC report

- Report generated: 2026-11-28T14:15:11Z (rule-based analyst).
- Snapshot generated: 2026-11-28T14:15:02Z.
- Label: Near-real-time cached threat activity from public feeds.
- This is a near-real-time cached snapshot built by the fetch job. It is not a live attack stream.

## Executive summary

WorldShield SOC refreshed its public-feed cache at 2026-11-28T14:15:02Z. 7 of 9 feeds returned data. Figures below are counts from those cached parses, not a live detection stream.
The parse includes 5 Feodo Tracker C2 addresses; 1,727 Spamhaus DROP networks; 481 ASN-DROP listings; 164,868 DShield source addresses (615,579,147 sensor reports, about the last 30 days); 1,808 CISA KEV catalog entries.
The highest DShield source-address counts, by country of the source and not of a victim, are United States of America (39,998 source addresses), People's Republic of China (25,358 source addresses), Canada (6,967 source addresses), Pakistan (5,714 source addresses), Russia (5,456 source addresses).
The most frequently tagged malware families in this cache are QakBot (4), Emotet (1).
The newest CISA KEV entry in this cache is CVE-2026-120705 (OSGeo GeoServer XML Injection Vulnerability), added 2026-11-27. 1 of the listed recent entries are tagged for known ransomware use.
Feeds that did not return usable data in this run: abuse.ch URLhaus, abuse.ch ThreatFox. Treat those panels as stale.
No fetched feed publishes a victim or target country, so this report does not rank target countries or draw attack paths.

## Trends

Each bar counts timestamps carried by the feeds during that hour of this cache window. An empty bar means those feeds had no timestamp then, not that an attack did not happen.
No feed timestamps fell inside this 24-hour cache window, so the timeline is empty. That is a property of the stamps, not evidence that nothing happened.
Threat-type counts over the full parse, not only the 24-hour window: drop-listing (1,727), phishing (300), sensor-source (100), QakBot (4), Emotet (1).

## Top threats

**Source countries (DShield source addresses, about 30 days of sensor reports):**
- United States of America (US): 39,998 — DShield source addresses located in this country.
- People's Republic of China (CN): 25,358 — DShield source addresses located in this country.
- Canada (CA): 6,967 — DShield source addresses located in this country.
- Pakistan (PK): 5,714 — DShield source addresses located in this country.
- Russia (RU): 5,456 — DShield source addresses located in this country.
- United Kingdom (GB): 5,176 — DShield source addresses located in this country.
- Brazil (BR): 4,627 — DShield source addresses located in this country.
- Ukraine (UA): 4,513 — DShield source addresses located in this country.
**Malware families (from tags the feeds themselves published):**
- QakBot: 4 indicators in the full parse.
- Emotet: 1 indicators in the full parse.
**Autonomous systems (from feed-published ASN fields and Spamhaus ASN-DROP):**
- AS14061 (DIGITALOCEAN-ASN, country US): 2 listings or indicators.
- AS14618 (AMAZON-AES, country US): 2 listings or indicators.
- AS9370 (SAKURA-B SAKURA Internet Inc., country JP): 1 listings or indicators.
- AS245 (PRC-AS, country US): 1 listings or indicators.
- AS2601 (RADIOLINK-AS, country UA): 1 listings or indicators.
- AS2702 (INTERSERVE, country US): 1 listings or indicators.
- AS3507 (IPSWAT_TEAM, country US): 1 listings or indicators.
- AS3563 (PILOT-ASN, country US): 1 listings or indicators.
- AS5060 (DE-KAT, country NL): 1 listings or indicators.
- AS5061 (DRH-RND, country NL): 1 listings or indicators.
**Local triage severity on parsed events:** high 1,732, medium 319, low 81. See the method section for how these labels are assigned.
**Recent CISA Known Exploited Vulnerabilities (catalog dates, not exploit timestamps):**
- CVE-2026-120705: OSGeo GeoServer XML Injection Vulnerability (OSGeo GeoServer), added 2026-11-27, ransomware campaign use: Unknown.
- CVE-2026-129243: OSGeo GeoServer Incorrect Authorization Vulnerability (OSGeo GeoServer), added 2026-11-27, ransomware campaign use: Unknown.
- CVE-2026-136716: Drupal Core Improper Check for Unusual or Exceptional Conditions Vulnerability (Drupal Core), added 2026-11-27, ransomware campaign use: Unknown.
- CVE-2026-103406: Hewlett Packard Enterprise (HPE) Juniper Session Smart Conductor and Session Smart Router OS Command Injection Vulnerability (Hewlett Packard Enterprise (HPE) Juniper Session Smart Conductor and Session Smart Router), added 2026-11-25, ransomware campaign use: Unknown.
- CVE-2026-133469: Vates Xen Orchestra Improper Validation of Specified Type of Input Vulnerability (Vates Xen Orchestra), added 2026-11-25, ransomware campaign use: Unknown.
- CVE-2025-41450: Danfoss AK-SM 800A Series Improper Authentication Vulnerability (Danfoss AK-SM 800A Series), added 2026-11-25, ransomware campaign use: Unknown.
- CVE-2023-25914: Danfoss AK-SM 800A Series Path Traversal Vulnerability (Danfoss AK-SM 800A Series), added 2026-11-25, ransomware campaign use: Unknown.
- CVE-2023-25915: Danfoss AK-SM 800A Series Improper Input Validation Vulnerability (Danfoss AK-SM 800A Series), added 2026-11-25, ransomware campaign use: Unknown.

## Recommended actions

1. Prioritize patching of the newest CISA KEV entries in this cache (CVE-2026-120705, CVE-2026-129243, CVE-2026-136716, CVE-2026-103406, CVE-2026-133469, CVE-2025-41450). Confirm exposure against local inventory before treating a CVE as relevant.
2. Give earlier attention to KEV items with known ransomware campaign use: CVE-2024-10441.
3. Block Feodo Tracker C2 addresses at the perimeter and review outbound traffic to those hosts. The Feodo country field is the location of the C2 address, not a victim country.
4. Apply Spamhaus DROP and ASN-DROP listings only under Spamhaus terms, and only as a network-control input. Do not republish the raw lists.
5. Hunt in local telemetry for the malware families that appear most often in this cache: QakBot, Emotet. Family names are the ones the feeds published.
6. Treat DShield country totals as sensor-reported source volume over about 30 days, not as a live attack count and not as attribution of a campaign to a government.
7. Investigate the failed feed fetch(es) (urlhaus, threatfox) and do not make operational decisions from empty panels for those sources.
8. Correlate every indicator with local logs before blocking or escalating. This cache is a near-real-time public-feed snapshot, not a substitute for internal detection.
9. Do not draw source-to-target attack paths from this data: the fetched feeds do not name a target country.

## Method and caveats

This report was produced by a deterministic rule-based analyst that reads only the cached snapshot.
It does not invent events, countries, malware families, ASNs, or source-to-target arcs.
This is a near-real-time cached snapshot built by the fetch job. It is not a live attack stream.
No fetched feed publishes a target country. DShield's target field counts destination addresses worldwide for sources located in a country, so it is not ranked here as a target country.
No arcs are drawn. A feed would have to name a source country and a target country on the same report. These feeds do not.
Severity is a local triage heuristic derived from published feed fields (for example ThreatFox confidence, Feodo C2 role, or CISA ransomware use). It is not a vendor-assigned score.
The indicator table keeps the newest rows from each feed, up to a cap. Country totals, malware-family totals, ASN totals, and the unfiltered 24 hour chart use the full parse.
IP countries that a feed does not already publish come from DB-IP Country Lite (CC BY 4.0), which is a country locator, not a street address and not a victim.
An optional LLM enrichment, when enabled, is appended in a separate section and must not override these facts.
