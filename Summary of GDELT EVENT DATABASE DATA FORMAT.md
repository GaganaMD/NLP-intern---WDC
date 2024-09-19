# GDELT Event File Format

GDELT 2.0 is an expanded version of the dyadic CAMEO format, capturing events between two actors. It provides detailed information on the event, including:

## Actor Information
- **Actor1 and Actor2 Attributes**:
  - **Actor1Name**: The actual name of Actor 1.
  - **Actor1CountryCode**: The country affiliation of Actor 1.
  - **Actor1KnownGroupCode**: The CAMEO code for the organization Actor 1 belongs to.
  - **Actor1EthnicCode**: The ethnic affiliation of Actor 1, if specified.
  - **Actor1Religion1Code**: The primary religious affiliation of Actor 1, if specified.
  - **Actor1Religion2Code**: The secondary religious affiliation of Actor 1, if specified.
  - **Actor1Type1Code**: The primary role or type of Actor 1, if specified.
  - **Actor1Type2Code**: The secondary role or type of Actor 1, if specified.
  - **Actor2Name**: The actual name of Actor 2.
  - **Actor2CountryCode**: The country affiliation of Actor 2.
  - **Actor2KnownGroupCode**: The CAMEO code for the organization Actor 2 belongs to.
  - **Actor2EthnicCode**: The ethnic affiliation of Actor 2, if specified.
  - **Actor2Religion1Code**: The primary religious affiliation of Actor 2, if specified.
  - **Actor2Religion2Code**: The secondary religious affiliation of Actor 2, if specified.
  - **Actor2Type1Code**: The primary role or type of Actor 2, if specified.
  - **Actor2Type2Code**: The secondary role or type of Actor 2, if specified.
  - **Actor2Type3Code**: The tertiary role or type of Actor 2, if specified.

**Notes:**
- Actor attributes are primarily derived from the TABARI ACTORS dictionary and may not always align perfectly with information in the text.
- The CountryCode field reflects a combination of information from the TABARI ACTORS dictionary and text, with the dictionary taking precedence.
- One of the actor fields may be blank in certain situations, like single-actor events or when information is minimal.
- GDELT uses the CAMEO version 1.1b3 taxonomy. For more details on specific codes, refer to the CAMEO User Manual or the GDELT website.

## Event Details
- **IsRootEvent**: Indicates if the event was mentioned in the lead paragraph of the first news report.
- **EventCode**: The raw CAMEO action code.
- **EventBaseCode**: The CAMEO event code at level two.
- **EventRootCode**: The CAMEO event code at level one.
- **QuadClass**: The primary classification of the event (Verbal Cooperation, Material Cooperation, Verbal Conflict, Material Conflict).
- **GoldsteinScale**: The theoretical potential impact of the event on country stability.
- **NumMentions**: The number of mentions related to the event.
- **NumSources**: The number of sources related to the event.
- **NumArticles**: The number of articles mentioning the event.
- **AvgTone**: The average tone of documents mentioning the event.

**Notes:**
- The fields related to event coverage are included for legacy purposes and the Mentions table should be used for more precise information.
- The GoldsteinScale is based on the event type, not the specific details.
- The AvgTone provides a basic tonal assessment and can be combined with the Mentions and Global Knowledge Graph tables for more detailed emotional analysis.

## Geographic Information
- **Actor1Geo_Type, Actor2Geo_Type, ActionGeo_Type**: The geographic resolution of the match (country, state, city, landmark).
- **Actor1Geo_Fullname, Actor2Geo_Fullname, ActionGeo_Fullname**: The human-readable name of the matched location.
- **Actor1Geo_CountryCode, Actor2Geo_CountryCode, ActionGeo_CountryCode**: The FIPS10-4 country code of the location.
- **Actor1Geo_ADM1Code, Actor2Geo_ADM1Code, ActionGeo_ADM1Code**: The FIPS10-4 ADM1 code of the location.
- **Actor1Geo_ADM2Code, Actor2Geo_ADM2Code, ActionGeo_ADM2Code**: The GAUL ADM2 code or FIPS10-4 county code of the location.
- **Actor1Geo_Lat, Actor2Geo_Lat, ActionGeo_Lat**: The latitude of the location.
- **Actor1Geo_Long, Actor2Geo_Long, ActionGeo_Long**: The longitude of the location.
- **Actor1Geo_FeatureID, Actor2Geo_FeatureID, ActionGeo_FeatureID**: The GNS or GNIS FeatureID of the location.

**Notes:**
- The georeferenced location may not always match the Actor1_CountryCode or Actor2_CountryCode.
- The Action fields capture the location closest to the action statement.
- Use the Geo_FeatureID column for filtering by specific locations.
- For events in or relating to a specific country, consider both Actor_CountryCode and Geo_CountryCode.
- The ActorGeo_CountryCode can capture situations like a country criticizing another country's actions.
- The Geo_Type field indicates the geographic resolution of the match.
- The Geo_Fullname field reflects the name used in the text.
- The Geo_FeatureID column provides a unique GNS or GNIS identifier.

## Mentions Table
The Mentions table in GDELT 2.0 tracks each mention of an event, providing insights into the event's trajectory and network structure within the global media system.

### Key Fields:
- **GlobalEventID**: The ID of the event mentioned.
- **EventTimeDate**: The timestamp when the event was first recorded.
- **MentionTimeDate**: The timestamp of the current mention.
- **MentionType**: The source collection of the document (WEB, CITATIONONLY, CORE, DTIC, JSTOR, NONTEXTUALSOURCE).
- **MentionSourceName**: A human-friendly identifier of the source.
- **MentionIdentifier**: The unique document or article identifier.
- **SentenceID**: The sentence where the event appears in the article.
- **Actor1CharOffset, Actor2CharOffset, ActionCharOffset**: The character offsets within the article for Actor1, Actor2, and the action.
- **InRawText**: Indicates whether the event was found in the original raw text or required NLP algorithms.
- **Confidence**: GDELT's confidence in extracting the event from the article.
- **MentionDocLen**: The length of the source document.
- **MentionDocTone**: The tone of the document mention.
- **MentionDocTranslationInfo**: Information about the source language and translation system used for machine-translated documents.

**Additional Features:**
- Tracks event mentions over time: Records mentions of past events, even if they occurred years ago.
- Records multiple mentions: Each mention of an event in a document is recorded separately.
- Provides confidence scores: Allows filtering based on GDELT's confidence in event extraction.
- Includes source information: Provides details about the source document, including type, name, identifier, and URL.
- Captures location information: Includes character offsets for Actor1, Actor2, and the action.
- Records translation information: Indicates the source language and translation system for machine-translated documents.
