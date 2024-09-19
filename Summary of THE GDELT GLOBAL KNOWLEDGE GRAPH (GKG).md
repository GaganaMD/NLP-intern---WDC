# GDELT Event File Format

The GDELT Event File Format is designed to provide detailed information about global news events. The format has undergone significant updates, particularly in GKG 2.1. This document summarizes the key features, differences between versions, and the structure of the GKG 2.1 format.

## Key Features of GKG 2.1

GKG 2.1 introduces several enhancements over the previous version:

- **Expanded Data**:
  - **Emotions and Themes**: Real-time measurement of 2,300 emotions and themes across 15 languages.
  - **Translation**: Real-time translation into English from 65 languages.
  - **Multimedia**: Extraction of relevant images, videos, and social media embeds.
  - **Quotes, Names, and Amounts**: Extraction of quotes, proper names, and numerical data.
  - **Date Mentions**: Tracking of specific dates mentioned.

- **Contextual Information**:
  - **Proximity Context**: Associates entities based on their proximity within articles.

- **New Data Types**:
  - **Enhanced Themes**: Over 100 new themes covering various topics.
  - **Extensible XML Block**: For storing specialized data types.
  - **Unique Record Identifiers**: Each record has a unique identifier.
  - **Single Data File**: Merges previous separate "Counts" and full dataset files.

- **Production Status**:
  - **Stable Release**: GKG 2.1 is now a stable production release.

## Differences Between GKG 2.0 and GKG 2.1

### Document Clustering

- **GKG 2.0**: Clusters documents with similar metadata.
- **GKG 2.1**: Processes each document independently, allowing for more granular analysis.

### Inclusion Criteria

- **GKG 2.0**: Required at least one geocoded location.
- **GKG 2.1**: Includes any extracted information, regardless of geographic mentions.

### Data Format

- **GKG 2.1**: Introduces additional fields and changes field ordering compared to GKG 2.0.
  - New fields include `V2EXTRASXML`, `V2GCAM`, and others.
  - Changes in field ordering and new data types.

### Compatibility

- **GKG 2.0**: Compatibility feed is not available.
- **GKG 2.1**: Only GKG 1.0 and GKG 2.1 formats are supported.

## Summary of Core Fields in GKG 2.1

- **GKGRECORDID**: Unique identifier for each record.
- **V2.1DATE**: Publication date of the news media document.
- **V2SOURCECOLLECTIONIDENTIFIER**: Source collection identifier (e.g., WEB, CORE).
- **V2SOURCECOMMONNAME**: Human-friendly identifier of the source.
- **V2DOCUMENTIDENTIFIER**: Unique external identifier for the source document.
- **V1COUNTS**: List of counts extracted from the document.
  - Includes count type, number, object type, location information, and offset.
- **V2ENHANCEDTHEMES**: List of themes with character offsets.
- **V1LOCATIONS**: List of locations with various details.
- **V2ENHANCEDLOCATIONS**: Enhanced location details with character offsets.
- **V1PERSONS**: List of person names.
- **V2ENHANCEDPERSONS**: Enhanced list of person names with character offsets.
- **V1ORGANIZATIONS**: List of organization names.
- **V2ENHANCEDORGANIZATIONS**: Enhanced list of organization names with character offsets.
- **V1.5TONE**: Six core emotional dimensions.
  - Includes Tone, Positive Score, Negative Score, Polarity, Activity Reference Density, and Self/Group Reference Density.
- **V2.1ENHANCEDDATES**: List of date references with details and character offsets.
- **V2GCAM**: Results from various content analysis systems.
- **V2.1SHARINGIMAGE**: URL of the sharing image.
- **V2.1RELATEDIMAGES**: List of URLs for relevant images.
- **V2.1SOCIALIMAGEEMBEDS**: URLs for embedded image-based social media posts.
- **V2.1SOCIALVIDEOEMBEDS**: URLs for embedded videos.

## Summary of Additional Fields in GKG 2.1

### V2.1QUOTATIONS

- **Fields**: Offset, Length, Verb, Actual Text.

### V2.1ALLNAMES

- **Fields**: All proper names with character offsets.

### V2.1AMOUNTS

- **Fields**: Numeric amounts with values, objects, and offsets.

### V2.1TRANSLATIONINFO

- **Fields**: Information about the source language and translation system.

## Summary of V2EXTRASXML Field in GKG 2.1

- **Purpose**: Reserved for storing specialized data types.
- **Format**: XML-formatted, customized for different data types.
- **CITEDREFERENCESLIST Block**: Contains citation details from academic journal articles.
  - **Fields**: Authors, Title, BookTitle, Date, Journal, Volume, Issue, Pages, Institution, Publisher, Location, Marker.

## Key Differences in Counts Fields

- **V1COUNTS**: Includes ADM2 support, lacks character offset.
- **V2.1COUNTS**: Adds character offset, does not include ADM2 support.

## Summary of Location Fields

- **V1LOCATIONS**: Detailed location information.
- **V2ENHANCEDLOCATIONS**: Adds ADM2Code and character offset fields.

## People and Organizations

- **V1PERSONS**: List of person names.
- **V2ENHANCEDPERSONS**: Enhanced list with character offsets.
- **V1ORGANIZATIONS**: List of organization names.
- **V2ENHANCEDORGANIZATIONS**: Enhanced list with character offsets.

## Tone

- **V1.5TONE**: Six core emotional dimensions.

## Dates

- **V2.1ENHANCEDDATES**: Detailed date references with offsets.

## Additional Notes

- **Use FeatureID**: For determining if two location names refer to the same place.
- **Error Notices**: Country code error from February 19th, 2015 to March 1st, 2015.

For detailed documentation and further information, refer to the [GDELT Documentation](https://www.gdelt.org/data.html).
