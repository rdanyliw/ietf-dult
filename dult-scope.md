# Synthesis of IETF 117 DULT BoF

The following is a synthesis of [feedback](https://notes.ietf.org/notes-ietf-117-dult) captured during the [IETF 117 DULT BoF](https://datatracker.ietf.org/meeting/117/session/dult) and the subsequent threads on the [mailing list](https://mailarchive.ietf.org/arch/browse/unwanted-trackers/).  This summary is an attempt to aggregate and cluster similar feedback so that it is easier the revisit in future discussions.  If your feedback was forgotten, please send me email (<rdd - at - cert.org>) or file a PR.

## Consensus

Consensus found during the BoF included:

* Support for the IETF working in "this area"
* Support for continued IETF efforts to refine a charter that addresses the problem(s) discussed during the BoF, but with a broader scope than defined in [charter-ietf-dult-00-00](https://datatracker.ietf.org/doc/charter-ietf-dult/)

There was also a robust number of reviewers and implementers volunteering to participate in a potential WG.

## Feedback on the Problem Statement

1. Three use cases for trackers were mentioned: (a) finding lost items; (b) finding a stolen item; and (c) unwanted tracking.  
   - Is the proposed scope of work aimed exclusively at (c)-unwanted tracking?
   - Is it acceptable for a solution for use case-(c) be designed without consideration for (b)?  (i.e., the solution for use-case-(c) may make use-case-(b) less tenable)?

2. The discussed solution space seemed to be largely around a device with Bluetooth LE and an internet connection.
   - Is that an acceptable baseline?
   - Does a solution need to be created for user communities that don't have such technologies?

## Reference Architecture

While a [notional DULT architecture](https://datatracker.ietf.org/meeting/117/materials/slides-117-dult-detecting-unwanted-location-trackers-rev-e-00) was formally presented at at the BoF, additional and more specific protocol mechanisms described in [draft-detecting-unwanted-location-trackers-00](https://datatracker.ietf.org/doc/html/draft-detecting-unwanted-location-trackers-00) were also discussed.  To contextualize this discussion, a more expansive reference architecture including input from both sources (and the charter text) is depicted and compared below.

### DULT Architecture
![](https://github.com/rdanyliw/ietf-dult/blob/b3cd784970ced33c9c7de1870bd2de5824df2672/dult-architecture.jpg)

### Comparing the Architecture Description across Sources
The differences in how this architecture is referenced in [charter-00-00](https://datatracker.ietf.org/doc/charter-ietf-dult/), the [architecture presentation at the BOF](https://datatracker.ietf.org/meeting/117/materials/slides-117-dult-detecting-unwanted-location-trackers-rev-e-00), and [draft-detecting-unwanted-location-trackers-00](https://datatracker.ietf.org/doc/html/draft-detecting-unwanted-location-trackers-00) is summarized below.

| State                                    | Charter                                                                                                                                                                                  | BoF Slides   | Draft             |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------|-------------------|
| (1) Enroll in Tracking Network           |     Out of scope are   “Mechanisms for detecting whether a tracking accessory implements the   protocol or allowing a tracking accessory to attest that it implements the   protocol”    | Slide 15     | [Section 3.15](https://datatracker.ietf.org/doc/html/draft-detecting-unwanted-location-trackers-00#section-3.15)      |
| (2) Broadcast Presence                   | “Allow a tracking accessory to identify & advertise its presence when in a detectable mode”                                                                                              | Slide 12     | [Section 3.4](https://datatracker.ietf.org/doc/html/draft-detecting-unwanted-location-trackers-00#section-3.4) – [3.5](https://datatracker.ietf.org/doc/html/draft-detecting-unwanted-location-trackers-00#section-3.5) |
| (3) Determine unwanted tracking occurred | Not mentioned                                                                                                                                                                            | Slide 12     |                   |
| (4) Non-Owner Interface                  | “Allow a nearby device to trigger behavior on an unwanted tracking accessory to aid in determining its physical location”                                                                | Slide 12     | [Section 3.12](https://datatracker.ietf.org/doc/html/draft-detecting-unwanted-location-trackers-00#section-3.12)      |
| (5) Perform Action                       | “Allow a nearby device to trigger behavior on an unwanted tracking accessory to aid in determining its physical location”                                                                | Slide 12     |                   |
| (6) Disablement Info Interface           | “Allow nearby devices to fetch additional information about a tracker accessory”                                                                                                         | Slide 12, 19 | [Section 3.13](https://datatracker.ietf.org/doc/html/draft-detecting-unwanted-location-trackers-00#section-3.13)      |
| (7) Owner Lookup Interface               | “Allow nearby devices to fetch additional information about a tracker accessory”                                                                                                         |              | [Section 3.15](https://datatracker.ietf.org/doc/html/draft-detecting-unwanted-location-trackers-00#section-3.15)      |
| (8) Disable Tracker                      | Not mentioned                                                                                                                                                                            | Slide 19     | [Section 3.13](https://datatracker.ietf.org/doc/html/draft-detecting-unwanted-location-trackers-00#section-3.13)      |
| Report location                          | Not mentioned                                                                                                                                                                            | Slide 12     | Not mentioned     |
| Query location                           | Not mentioned                                                                                                                                                                            | Slide 12     | Not mentioned     |                                                                                                                                                                                   |            |              |

## Feedback on the Scope

1. “Opaque blob” (i.e., “Proprietary company payload data” in Section 3.4.2 of draft-detecting-unwanted-location-trackers-00 and in steps #2, 6? And 7? of the architecture)
   - It needs to be in-scope for IETF work
   - Further definition of the privacy properties is needed

2. “Pairing registry” (i.e, #7 in the architecture)

   - Further definition of privacy implications of engaging it in the architecture

3. “Disabling the tracker” (i.e., per #5 in the architecture)

   - Should physical access be the only way to disable the tracker?

4. (charter text) “Minimize hardware changes needed in tracking accessories to implement this protocol”

   - Should the charter scope be restricted to capabilities of current trackers?
   - How to deal with current deployment of the current-generation, non-conformant-to-this-proposed work trackers? 

5. (charter text) Out of scope are “[m]echanisms for detecting whether a tracking accessory implements the protocol or allowing a tracking accessory to attest that it implements the protocol”

   - Should this be reconsidered to mitigate interoperable, but non-conformant-to-this-proposed work, trackers trying to participate in the tracker network?

6. Additional Security and Privacy Considerations

   - Clarifying privacy protections of the tag owner in the charter
   - Clarifying whether there are physical security considerations

7. What interoperability is being sought?

   - Allow application developer-X to detect an unwanted-tracker-made-by-vendor-A via support from tracking-network-run-by-vendor-A
   - Allow application developer-X to detect an unwanted-tracker-made-by-vendor-A via support from tracking-network-run-by-vendor-B 

8. Concerns about the terms of the [IPR filed against draft-detecting-unwanted-location-trackers](https://datatracker.ietf.org/ipr/search/?submit=draft&id=draft-detecting-unwanted-location-trackers)
