Proximus - Proximity Oracle for M&A Deal Rooms and Verical Index Scores
by Smartmarkets.ai · a SmartScale.co product

Proximus already knew the answer.

Proximus is a precomputed proximity oracle. It answers questions about proximate residents, catchment netowks, and competitive footprint for every US location address — instantly, from federal data, with 100% census coverage and no modeling assumptions.

Not a map. Not a dashboard. Not a search engine.
It is an oracle: you ask, it answers from precomputed truth.

What Proximus Does
Given any US address, coordinate, or Bank Holding Company (BHC) group ID, Proximus returns:

Who lives nearest to a location or branch network (proximate residents catchment)

Competitive footprint - how your catchment fits, like a puzzle, with every competitor's

Accretion score - how an acquisition target's catchment is accretive to your footprint

Example Index score: Bypass burden - for hospital access, the extra miles a resident travels past rural care to reach urban care

Every answer traces to public federal sources: FDIC Sites and Summary of Deposits, US Census, CMS hospital data.

text
answer_source: precomputed_not_generated
Live Demo
Try the 7110 oracle — nearest hospital from any US coordinate, 100% coverage:

bash
curl "https://proximustools.com/oracles/7110/distance_to_nearest_hospital\
?lat=29.888611&lon=-96.491111&key=free-demo"
New Ulm, TX result:

json
{
  "nearest_rural_hospital": "Fayette Medical Center — 12.2 miles",
  "nearest_urban_hospital": "Memorial Hermann Katy — 43.1 miles",
  "distance_gap_miles": 30.9,
  "answer_source": "precomputed_not_generated"
}
Any US address. Any coordinate. Answered instantly.

Verticals
Vertical	Series	Status
Hospital Access & Rural Bypass	7110	✅ Live — free demo
Proximate Residents Catchment	7140	✅ Live — API key required
Hospital Competitive Catchment (M&A)	7160	✅ Live — Enterprise
Banking Deposit Catchment (M&A)	8140	🔜 Coming soon
How to Use Proximus
Option 1 — Perplexity Computer (recommended for M&A teams)
Proximus is designed as a Computer-native oracle. The recommended entry point:

Get access to Perplexity Computer

Open a new session and enter:

text
Open smartmarkets.ai/proximus and help me understand
my BHC's competitive footprint.
Computer reads the oracle orientation page, forms the correct URLs, fetches your data, and narrates the answers in deal-room language. No SQL. No GIS. No dashboard to learn.

Option 2 — Direct API (for technical teams)
bash
# Free demo — 7110 hospital access, any US coordinate
curl "https://proximustools.com/oracles/7110/distance_to_nearest_hospital\
?lat={LAT}&lon={LON}&key=free-demo"

# Paid — BHC competitive catchment
curl "https://proximustools.com/oracles/7160/catchment_hospitals/050093\
?key={YOUR_API_KEY}"
Option 3 — MCP (coming soon)
Proximus will be registered as an MCP-native oracle at:

text
proximustools.com/oracles/mcp
Compatible with OpenClaw and any MCP-compliant agent.

Oracle Surface
All callable endpoints live at:

text
https://proximustools.com/oracles/{series}/{operation}
URL	What it answers
URL	What it answers
/oracles/7110/distance_to_nearest_hospital	Nearest rural + urban hospital, bypass burden
/oracles/7140/proximate_residents_catchment	Who lives nearest to a site or network
/oracles/7160/catchment_hospitals/{group_id}	Hospital M&A competitive overlap
/oracles/{series}/docs	Plain-language endpoint docs (free tier)
/oracles/{series}/methodology	Full methodology in markdown (paid tier)
Orientation pages for humans and agents:

smartmarkets.ai/proximus — M&A catchment vertical

smartmarkets.ai/proxindex — scored index vertical

API Keys
Key	Access	How to get
free-demo	7110 only, rate-limited	No signup — use now
Paid key	All series, higher limits	smartmarkets.ai/proximus → $_ prompt
Enterprise key	Deal-room tier, private subdomain	neo@smartmarkets.ai
Data Provenance
Source	Used for
FDIC Summary of Deposits	Branch locations, deposit volumes, BHC group IDs
US Census (TIGER, ACS)	Population, geography, H3-7 binning
CMS Provider of Services	Hospital locations, bed counts, rural/urban classification
Dartmouth Atlas (HRR)	Hospital referral region boundaries
All data is precomputed. No real-time modeling. No proprietary assumptions.
Results are reproducible and auditable from public sources.

Architecture
text
smartmarkets.ai          — human entry point (Vercel / Next.js)
  /proximus              — M&A oracle orientation page
  /proxindex             — scored index orientation page
  /research/{slug}       — white paper series

proximustools.com        — oracle surface (Railway / FastAPI)
  /oracles/{series}/...  — all callable endpoints
  /oracles/{series}/docs — endpoint documentation (markdown)
Held by SmartScale.co LLC · Inquiries: neo@smartmarkets.ai

Status
Pre-client. Actively developed. Banking M&A vertical (8140) in build.
White paper series launching Q2 2026 — scoring past BHC acquisitions
against Proximus catchment data.

If you are a VP of M&A, Corporate Development, or Strategy at a bank
or hospital system — start here.
