# Proposal

This note is a proposal for a policy about OpenAddresses data.
At time of first writing it is one project member's thoughts; some opinions are far from consensus.
This proposal needs review by someone with expertise in licensing and other IP legal matters.
If this proposal becomes consensus then this notice should be removed.

## License Principles

OpenAddresses (OA) collects and publishes a collection of address points that are freely usable for any purpose.
We explicitly do not want to prevent commercial use nor compel OA users to contribute back to our database.
In many cases the data we collect is already in the public domain or otherwise available under very liberal terms.

OA will collect any data whose license allows redistribution.
Some source data has restrictions such as required attribution, non-commercial use only, or a viral licensing requirement on derived works.
We will focus our efforts on collecting data that has few or no restrictions.
But in principle anything redistributable could go in to OpenAddresses.
<br>*(This statement is a change. Currently we don't include some data with significant requirements on derived works.)*

The primary publication of OA is the output address CSV files. This collection itself is licensed by [CC0](https://creativecommons.org/about/cc0).
However the constituent databases in our publication have their own licenses and we cannot simply alter those license terms.
Because OA lacks the legal expertise to clear every single license we cannot guarantee any OA data user's right to use the data we have collected.
Instead we will do our best to annotate all data with records indicating the source's license of that data.
<br>*(Have we already made this decision about CC0?
Also I would dearly love legal clarification on the copyright status of our collection.
See also [this case](https://en.wikipedia.org/wiki/Feist_Publications,_Inc.,_v._Rural_Telephone_Service_Co.).)*

OpenAddresses also creates its own intellectual property: source code, the collection of source JSON files, and other assets.
The license for any code we produce is the [BSD 3 Clause license](http://opensource.org/licenses/BSD-3-Clause).
Other assets should generally be licensed [CC-BY](https://creativecommons.org/licenses/by/4.0/).
At such time as OpenAddresses gets a formal corporation or other entity, individual contributers should sign copyright assignments for their code to OA.
<br>*(CC-BY and copyright assignments are a change I'm proposing. Also do we want BSD 3 clause? That requires attribution.)*

## Implementation Guidance

* Every source specification should include information about the data license in metadata.
We should cache copies of the license at time of download.

* Every address record should be linked to its source record and, therefore, its license.

* Ignorance sometimes feels like bliss when dealing with data licensing.
OA should only include data that we believe we have the right to redistribute.
But to the extent there is ambiguity about the terms of reuse of any data, we should include it and then inform data users about the underlying license.
Ultimately responsibility for license clearance lies with our users, not us.
We may need contractual language to enforce this, in which case CC0 will not be sufficient.

* While we will accept any data that allows redistribution, we should focus our collection effort on data that has the most liberal licenses.

* The ODbL allows redistribution and is therefore explicitly in the scope of OA.
However the ODbL also places restrictions on derived works that are awkward.
Perhaps we can finesse that by publishing the ODbL-derived data as a separate collection.

* We should consider grouping data by general license type.
Pure public domain / CC0, requires attribution, non-commercial, and ODbL are four possible groupings.

* OpenAddresses really needs some legal structure.
Either its own corporation or becoming hosted by a larger one.
We don't need non-profit tax status (although it'd be nice).
We do need limited liability and a corporate entity to own the copyright on things.
