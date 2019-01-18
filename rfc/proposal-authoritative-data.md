# Proposal

This note is a proposal for a policy about OpenAddresses data.
At time of first writing it is simply one project member's thoughts.
If this proposal becomes consensus then this notice should be removed.

## Authoritative Data

OpenAddresses (OA) is a collection of *authoritative data* for address locations around the world.
We collect address data from authoritative sources; we do not create our own data. 

As of June 2015 OpenAddresses consists of 125M address records that are mostly (entirely?) republished from authoritative sources.
Our source data comes from regional and national authorities.
These government sources are useful because they tend to be correct and liberally licensed.
That correctness is a valuable property.

Our notion of "authoritative source" is quite different from OpenStreetMap's guiding principle of [verifiability](http://wiki.openstreetmap.org/wiki/Verifiability).
OSM has built a fantastic world map largely from data that was individually mapped or else verified from an import and subsequently edited.
In contrast OA consists of republished data from other sources that we cannot or do not intend to verify.
OA does not currently have user-submitted or hand-edited data.
OpenStreetMap's value is in allowing the OSM community to *create* map data.
OpenAddresses' value is in *collecting* data from authoritative sources.

OpenAddresses collects the best data and gives users a clear chain of authority that connects any particular address point back to the source of that information.
Inevitably some authoritative data will be conflicting, incorrect, or incomplete.
OA does not currently have any tools to allow users to flag or correct incorrect data and no way to communicate improvements back to sources.
We may build such tools in the future, but we will treat any data we collect from individuals as improvements or patches to authoritative sources, not replacements.


## Implementation Guidance

The principle of "authoritative sources" gives us several guidelines for implementing OpenAddresses.

* The source description JSON files are primary, essential records for the OA database.
Sources are not just directives for how to extract data.
Source JSON files also contain information about the source itself, its authority.

* Every single address record should be traceable back to its source.
Conceptually, every single row in our master CSV file should have a "source ID" column.
In practice, grouping many addresses into per-source collections will maintain the link to the source authority.
(Should we timestamp each record as well?)

* The OA database may contain multiple records for a single address.
These records may be identical or contradictory.
OA should republish one record per address per source.

* OA may choose to integrate useful sources that do not have the authority of government data.
For example a layer of OSM address points would be a natural addition to OpenAddresses (license permitting).
As long as each record has a link to its source, users of OA data can make their own decision on authoritativeness.

* The OA database should only manipulate source data in ways that do not degrade the authoritativeness of the data.
Right now we significantly process source data – we join and split addresses into "number" and "street" columns, we rewrite street names and expand abbreviations, we round geographic coordinates.
We should not make lossy edits if they compromise the authority of the source data, or at least consider publishing the verbatim data along with our edited version.

* OA should not delete or update individual data records from sources.
We should not take user-submitted edits to authoritative source data.
We may wish to expand to create our own overriding overlay database of addresses that act as patches to authoritative sources.
In those cases we should publish both our own record and that of the original authority and let OA consumers decide which to believe.

* We may decide to produce one single merged and cleaned data file where we normalize street naming, de-duplicate addresses, overlay our own user submitted corrections, etc.
That value-add file should still contain links to the source authority in every single record.
Any extra data publication should not replace our unedited collection of data from authoritative sources.
