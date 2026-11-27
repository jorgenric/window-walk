# Research and references

Supporting research behind the concept: what earlier attempts teach, who to talk to in Portland, data source details, the ShopSmallPDX review and the naming check. Research gathered November 26, 2026.

## Lessons from past attempts

Every earlier local-stock search either faded or became a data feed for Google. The common failure points were getting stock data, attracting traffic, and thin coverage.

| Attempt | What happened | Lesson |
| --- | --- | --- |
| [StepUp.com](https://www.searchenginejournal.com/local-shopping-search-engine-stepupcom-in-beta/762/) (2000s) | Early local shopping search engine; gone | Stores without web presence were hard to onboard |
| Milo | Local product search, bought by eBay in 2010 | Absorbed into a large platform |
| [Elephanti](https://techcrunch.com/?p=934228) | Raised $4.5M seed; gone | Funding didn't solve inventory or traffic |
| [ShopNear.me](https://techcrunch.com/?p=703035) | San Francisco only, about 40 shops | Hyperlocal coverage stayed small |
| [NearSt](https://www.retail-systems.com/rs/Google_NearSt_Partnership_Local_Shopping_Search.php) | Started as a shopper site, became a Google data feed | Shoppers default to Google; standalone search needs another reason to exist |
| [Pointy](https://searchengineland.com/startup-helps-small-retailers-get-local-inventory-data-online-at-pos-313117) | Barcode-scanner device for shop inventory; bought by Google | Data capture is the hard, valuable part |
| [Locally.com](https://retailwire.com/?p=49572) | Still active, 30,000+ retailers | Only works for retailers with a POS system |

Implication for Window Walk: lead with character and the Hometown Shelf, not stock; launch one corridor deeply; rely on local partners and physical presence for reach.

## Portland ecosystem

| Group | What it is | Possible role |
| --- | --- | --- |
| [Prosper Portland / ShopSmallPDX](https://shopsmallpdx.com/small-business-directory) | City-backed directory of 2,000+ small businesses | Seed list, co-promotion, possible host |
| [LocalFirst PDX](https://siliconflorist.com/2026/07/01/portland-loves-local-small-business-localfirst-pdx-makes-them-easier-to-find/) | Shop-local platform launched July 2026 | Partner or overlap; check first |
| [Little Boxes PDX](https://katu.com/news/local/little-boxes-movement-to-shop-local-growing-in-portland) | Shop-local passport, app and discounts | Model for the neighborhood passport; partner |
| [Resourceful PDX](https://www.portland.gov/bps/sustainability/resourcefulpdx/resourceful-pdx-map) | City map of used, repair, lending and donation spots | Overlap for used and repair shops; data-sharing |
| [B Local PDX](https://www.idealist.org/en/nonprofit/09aefa1eae61484ebdbe346727f4279e-b-local-pdx-portland) | Local business nonprofit | Partner, volunteers |
| [Portland Metro Chamber](https://community.portlandmetrochamber.com/list/Search/shopping-and-retail-249448?cid=249372) | Member directory including specialty retail | Outreach to members |
| [Travel Portland shopping guides](https://www.travelportland.com/attractions/shopping/) | Editorial guides to local shops | Curated collection ideas, promotion |
| Markets: [Portland Saturday Market](https://shopsmallpdx.com/small-business-directory), [My People's Market, Slabtown Makers Market](https://melvinmarkcompanies.com/?p=5426) | Maker and vendor markets | Source of market-vendor pages and storefront days |
| [West End Wednesdays](https://traveloregon.com/places-to-go/oregon-attractions/shopping/ultimate-guide-to-portland-shopping-experiences/) | Monthly late-open shop night | Launch event model for a corridor |

## Data source details

| Source | Details | Constraints |
| --- | --- | --- |
| [Oregon Active Businesses (all)](https://catalog.data.gov/dataset/active-businesses-all) | Principal place of business, mailing address, registered agent | No license stated; no business-type tags |
| [Oregon Active Businesses (county)](https://catalog.data.gov/dataset/active-businesses-county-data) | Oregon principal place of business, county from city and ZIP | Same |
| [Oregon New Businesses, last month](https://catalog.data.gov/dataset/new-businesses-registered-last-month) | Monthly feed via data.oregon.gov API in JSON, XML, CSV | Good for spotting openings |
| [OpenStreetMap](https://www.openstreetmap.org/copyright) | Tags: shop=\*, [opening\_hours, check\_date:opening\_hours, source:opening\_hours](https://wiki.openstreetmap.org/Key:opening_hours) | ODbL: attribute, share improvements; facts from a shop's own site are OK, never from aggregators like Google |
| [Google Maps Platform](https://conductatlas.com/platform/google-maps/google-maps-platform-terms-of-service/no-scraping-or-content-extraction/) | Places, geocoding | No scraping or extraction; no use with non-Google maps; lat/lng cache limited to 30 days |

## ShopSmallPDX review

Reviewed November 26, 2026, as a reference for what a richer front end would add.

- 2,000+ listings, filterable by location, category and shopping options, with a map button
- Cards show a logo, a one-line tagline, badges (Delivery, Online Ordering, Gift Cards, Pickup) and "Read more"
- Services (SEO agencies, carpet cleaning, wildlife removal, consulting) mixed in with shops
- Many listings show only "Portland," with no street address or neighborhood
- Broad, overlapping categories: Gifts & Accessories (832), Lifestyle & Personal Care (865), Home & Living (489)
- No storefront or interior photos, owner stories, themes or featured shops

## Naming check

No direct conflicts found in web searches on November 26, 2026.

- **Window Walk:** no service by that name; [Streetify](https://apps.apple.com/app/streetify/id1450938613) (virtual shopping streets with store windows) is conceptually close
- **Hometown Shelf:** no service by that name; "Hometown" is common in shop names
- Still to check: domains, [USPTO trademarks](https://tmsearch.uspto.gov/), [Oregon business registry](https://sos.oregon.gov/business/pages/find.aspx)

## Next actions

Next actions from this research are tracked in the project [to-do list](../../TODO.md): O-01, O-02, O-03, O-05, O-09, O-10, T-01 and T-02.
