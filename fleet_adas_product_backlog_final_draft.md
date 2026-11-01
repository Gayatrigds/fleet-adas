# Fleet Management Application — ADAS Product Backlog

**Document status:** Final draft — pending validation  
**Version:** 5.1  
**Purpose:** Consolidated product backlog for adding the agreed ADAS screens and capabilities to the existing fleet management application, with Vehicles available as a separate menu within the ADAS section.

## 1. Product context and scope

The existing fleet management application is already available. This work extends that application with the six screen areas identified in the supplied Cautio reference:

1. Dashboard
2. ADAS > Vehicles — a separate menu for vehicle and ADAS information
3. Live Tracking
4. Video Playback
5. Incident Alert
6. Fleet Movement History

The ADAS device, camera and event information is supplied by an external ADAS provider (for example, TurboHive) and displayed in the existing fleet management application. The application must not invent provider data or infer statuses that the provider has not supplied.

This backlog is limited to the six areas above. Live Tracking, Video Playback, Incident Alert and Fleet Movement History should retain the layout and functionality shown in the reference. Any item not yet confirmed against the reference or provider capability is explicitly marked **Approved**.

**User-story wording:** All stories use “As a fleet user”.

## 2. Status definitions

- **Approved:** Explicitly approved by the user during backlog review.
- **To be checked:** Draft requirement or unresolved detail that needs validation against the Cautio reference, existing application behavior, or ADAS provider capability.

## 3. Review status summary

| Feature area | Story status |
|---|---|
| Dashboard | DASH-01 to DASH-04 approved |
| ADAS > Vehicles | VEH-01 to VEH-04 approved |
| Live Tracking | LIVE-01 and LIVE-02 approved; LIVE-03 to be checked |
| Video Playback | VID-01 to VID-07 approved |
| Incident Alert | INC-01 to INC-03 approved |
| Fleet Movement History | HIST-01 to HIST-03 and HIST-05 to HIST-06 approved; HIST-04 display order to be checked |

---

# Epic 1 — Dashboard

**Objective:** Provide a consolidated view of fleet operations and relevant ADAS information, using the Cautio dashboard reference.

| ID / User Story | Feature Details | Acceptance Criteria | Status |
|---|---|---|---|
| **DASH-01 — View fleet summary metrics and vehicle status distribution.** As a fleet user, I want to view fleet summary metrics so that I can understand the overall fleet status. | Display the fleet summary metrics identified during review: **Total Vehicles, In-Trip, Idle, Stopped, Low Network, Offline, Offline for more than 48 hours, and Live Alerts**. Each metric displays a count. The vehicle status distribution is included within these summary metrics rather than maintained as a separate story. | 1. Display the eight agreed summary metrics. 2. Show the corresponding count for each metric. 3. Counts reflect the user's authorized fleet data. 4. The “Offline for more than 48 hours” count follows the agreed offline-duration rule. 5. Selecting a metric opens the corresponding filtered vehicle or alert list where supported by the existing application. | **Approved** |
| **DASH-02 — View vehicles on the map.** As a fleet user, I want to view vehicle locations on a map so that I can monitor fleet distribution. | Display vehicle locations using map markers. Markers represent vehicle status. Selecting a marker displays vehicle information. Support map zoom and pan. | 1. Display available vehicle locations. 2. Markers indicate vehicle status. 3. Selecting a marker displays the associated vehicle details. 4. The map reflects the latest available location data. 5. Users can zoom and pan the map. 6. Display the last-updated time. 7. Identify multiple vehicles in a clustered area using cluster functionality. 8. A selected marker shows vehicle registration number, vehicle name, current status, location, speed, last reported time, assigned driver and current trip information where available. | **Approved** |
| **DASH-03 — View ADAS storage and data pack information.** As a fleet user, I want to view ADAS device storage and data pack information so that I can understand available storage and data usage across my fleet. | Display provider-supplied storage information for ADAS devices, such as total capacity, used storage and available storage, and data pack information, such as plan allowance, data used and remaining allowance. Keep device storage and mobile data pack usage clearly distinct. Show validity or reset period when supplied. | 1. Display storage and data pack information separately for the correct vehicle/device. 2. Show total, used and available storage only where supplied by the provider, with clear units. 3. Show data pack allowance, data used and remaining allowance only where supplied, with clear units. 4. Show the data pack validity or reset period when supplied. 5. Use the latest available provider data and display its update time where available. 6. Show Not Available for missing values and do not calculate or infer provider-owned values. 7. Reflect only vehicles within the user's authorized fleet scope. | **Approved** |
| **DASH-04 — View ADAS event summaries.** As a fleet user, I want to view ADAS event summaries so that I can get an overview of safety events. | Display ADAS event information such as **Total Events, Critical Events, High-Severity Events, and Events by Category**. Categories may include Forward Collision Warning, Lane Departure Warning and other event types supported by the provider. | 1. Display the total ADAS event count. 2. Display critical and high-severity counts only where severity data is supplied. 3. Group events by provider-supported category. 4. Reflect the selected reporting period where applicable. 5. Base counts on events received from the integrated ADAS provider. 6. The application must not independently assign severity levels. | **Approved** |

### Dashboard items to be checked

- Confirm the storage fields, data pack allowance/usage values, units, validity/reset period and update frequency supplied by each ADAS provider.
- Confirm whether TurboHive supplies event severity classifications and the event categories to be displayed.
- Confirm the reporting-period behavior for ADAS event summaries.
- Confirm the offline-duration rule for “Offline for more than 48 hours” against the existing application behavior.

---

# Epic 2 — ADAS Vehicles Menu

**Objective:** Add a dedicated **Vehicles** menu within the ADAS section of the existing fleet management application. The menu is separate from the existing Vehicles area and presents a vehicle table with five vehicle identification/status columns plus associated ADAS system information.

| ID / User Story | Feature Details | Acceptance Criteria | Status |
|---|---|---|---|
| **VEH-01 — Open Vehicles from the ADAS menu.** As a fleet user, I want to access Vehicles as a separate menu under ADAS so that I can find ADAS-related vehicle information without opening the existing Vehicles area. | Add a distinct **Vehicles** menu entry within the ADAS section/navigation. Selecting it opens the ADAS Vehicles table. | 1. Display Vehicles as a separate selectable menu item under ADAS. 2. Open the ADAS Vehicles table when selected. 3. Keep this menu distinct from the existing Vehicles menu. 4. Show only vehicles the user is authorized to access. | **Approved** |
| **VEH-02 — View ADAS information in the vehicle table.** As a fleet user, I want to view key ADAS system information alongside each vehicle in the ADAS Vehicles table so that I can quickly understand the equipment installed and its current condition. | Show vehicle identification and the associated ADAS information in the table. ADAS fields include the current device status, device model/model number, device manufacturer (the company that produced it), and camera configuration/type such as Single Channel or Dual Channel. Show other channel types only when supported by the provider. | 1. Display each authorized vehicle and associate its ADAS information with the correct vehicle/device. 2. Show the provider-reported current device status; do not infer connectivity or condition. 3. Show the provider-reported device model/model number and manufacturer as separate values. 4. Show provider-reported camera configuration/type, including Single Channel or Dual Channel where supplied. 5. Display Not Available when a value is missing. 6. Use the latest available provider data and display its update time where available. 7. Keep the table readable; any additional fields not named here remain in vehicle details unless confirmed for the table design. | **Approved** |
| **VEH-03 — Find a vehicle in the ADAS Vehicles list.** As a fleet user, I want to search or filter the ADAS vehicle list so that I can quickly locate a specific vehicle. | Support search by available vehicle identifiers, such as registration number or vehicle name. Any additional filters depend on the confirmed reference and existing application capabilities. | 1. Allow search using supported vehicle identifiers. 2. Show vehicles matching the search criteria. 3. Allow the user to clear the search and restore the list. 4. Show a clear empty state when no vehicles match. | **Approved** |
| **VEH-04 — View vehicle information in the ADAS Vehicles table.** As a fleet user, I want to see each vehicle's number, organization, alias, status and ADAS device link in the Vehicles table so that I can identify the vehicle and understand its association with the ADAS system. | Show the five requested vehicle columns in the ADAS Vehicles table: **Vehicle Number, Organization, Alias, Vehicle Status, and Device Linked**. Vehicle Number identifies the vehicle; Organization shows its assigned organization; Alias shows its configured display name; Vehicle Status shows the status from the fleet system; Device Linked indicates whether an ADAS device is associated with the vehicle. | 1. Display all five columns with clear labels: Vehicle Number, Organization, Alias, Vehicle Status and Device Linked. 2. Show each value for the correct vehicle and organization. 3. Use the vehicle status supplied by the fleet system and do not infer a status. 4. Show Device Linked according to the recorded vehicle-to-device association; show Not Available when the association state is unknown. 5. Show Not Available for other missing values rather than inventing data. 6. Restrict rows to vehicles the user is authorized to access. | **Approved** |

### ADAS Vehicles implementation details to be checked

- Confirm that each ADAS provider supplies the VEH-02 fields: current device status, model/model number, manufacturer and camera configuration/type, and identify the supported values.
- Confirm the source and display format for all five VEH-04 columns: Vehicle Number, Organization, Alias, Vehicle Status and Device Linked. Define the displayed states for a linked, unlinked or unknown device association.
- Confirm which vehicle identifiers VEH-03 search supports and whether any filters are supported.


---
# Epic 3 — Live Tracking

**Objective:** Retain the Live Tracking screen's layout and functionality as shown in the Cautio reference, including vehicle live view, operating details and driver contact action.

| ID / User Story | Feature Details | Acceptance Criteria | Status |
|---|---|---|---|
| **LIVE-01 — View a selected vehicle's live camera channels.** As a fleet user, I want to select a vehicle and view or switch between its available live camera channels so that I can monitor the vehicle's surroundings. | Provide vehicle selection, display the selected vehicle's available camera channels and live feeds, and allow switching between channels. Retain the reference screen layout. | 1. Display available vehicles for selection. 2. Load only camera channels and feeds associated with the selected vehicle. 3. Identify each available channel clearly and allow switching between them. 4. Indicate when a channel or live feed is unavailable. 5. Allow switching to another vehicle and display only its corresponding channels and feeds. | **Approved** |
| **LIVE-02 — View vehicle live-tracking details and contact the driver.** As a fleet user, I want to view a vehicle's speed, channel running status and vehicle running status, and call its driver from Live Tracking so that I can understand its current operation and contact the driver when needed. | Show the selected vehicle's speed, running status and each camera channel's running status as provided by the fleet/ADAS service and shown in the reference. Provide a Call Driver action associated with the selected vehicle's assigned driver. | 1. Show speed and vehicle running status for the selected vehicle when supplied. 2. Show running status for each supported camera channel. 3. Associate all displayed details and the driver contact action with the selected vehicle. 4. Show Unavailable when a status or value is not supplied; do not infer running or connectivity status. 5. Allow the fleet user to initiate a call to the assigned driver's available contact number using the application's supported calling behavior. 6. Indicate when driver contact information or calling is unavailable. | **Approved** |
| **LIVE-03 — Use live monitoring controls.** As a fleet user, I want to use the live monitoring controls so that I can manage the camera viewing experience. | Provide the live monitoring controls displayed in the Cautio Live Tracking reference screen. Potential examples discussed include full-screen, play/pause, audio and snapshot, but these are illustrative only and are not confirmed requirements. | 1. Display only controls confirmed in the reference. 2. Each confirmed control performs its intended action. 3. Controls operate on the currently selected vehicle and camera channel where applicable. 4. Reflect the correct state when a control is activated. 5. Do not introduce controls absent from the reference. | **To be checked** |

### Live Tracking items to be checked

- Confirm the source and update frequency for vehicle speed, vehicle running status and camera-channel running status.
- Confirm the driver's contact field and supported call behavior, including any required access permissions.
- Identify the exact monitoring controls visible in the Cautio Live Tracking screenshot and confirm their behavior.
- Confirm supported camera channels, simultaneous feed support and unavailable-feed behavior with the reference and ADAS provider.

---
# Epic 4 — Video Playback

**Objective:** Retain the Video Playback screen's layout and functionality as shown in the Cautio reference.

| ID / User Story | Feature Details | Acceptance Criteria | Status |
|---|---|---|---|
| **VID-01 — Select a vehicle.** As a fleet user, I want to select a vehicle in Video Playback so that I can access its recordings. | Provide vehicle selection within Video Playback. Retrieve recordings associated with the selected vehicle. | 1. Display available vehicles. 2. Allow vehicle selection. 3. Retrieve recordings associated with the selected vehicle. 4. Ensure recordings belong to the selected vehicle. 5. Allow selection of another vehicle and display its recordings. | **Approved** |
| **VID-02 — Select date and time range.** As a fleet user, I want to select a date and time range so that I can retrieve recordings for the selected vehicle and period. | Provide date and time selection within Video Playback, following the Cautio reference. | 1. Allow date selection. 2. Allow selection of the required time range. 3. Retrieve recordings for the selected vehicle and period. 4. Prevent invalid date/time ranges. 5. Indicate when no recordings are available. | **Approved** |
| **VID-03 — View video availability timeline.** As a fleet user, I want to view the video availability timeline so that I can identify when recordings are available. | Display a timeline showing recording availability for the selected vehicle, date and time range, following the reference. | 1. Display the timeline for the selected vehicle and period. 2. Distinguish periods with available recordings from periods without recordings. 3. Reflect availability for the selected camera channel where applicable. 4. Update the timeline when vehicle or date/time selection changes. | **Approved** |
| **VID-04 — Filter recordings by camera channel.** As a fleet user, I want to filter recordings by camera channel so that I can view recordings from a specific camera. | Provide camera channel selection within Video Playback. Display recordings corresponding to the selected channel. | 1. Display channels available for the selected vehicle. 2. Allow channel selection. 3. Show recordings associated with the selected channel. 4. Display only channels supported by the selected vehicle's ADAS device. 5. Update the availability timeline based on the selected channel. | **Approved** |
| **VID-05 — View available video clips.** As a fleet user, I want to view available video clips so that I can identify recordings to play. | Display clips based on the selected vehicle, date/time range and camera channel. Show start time, end time, duration and camera channel where available. | 1. Display clips matching the selected vehicle and filters. 2. Show clip start and end time. 3. Display clip duration. 4. Identify the associated camera channel. 5. Indicate when no clips are available. | **Approved** |
| **VID-06 — Play selected video.** As a fleet user, I want to play a selected video clip so that I can review recorded footage. | Allow selection and playback of an available clip for the selected vehicle, date/time range and camera channel, following the reference. | 1. Allow selection of an available clip. 2. Play the recording associated with the selected vehicle and channel. 3. Play footage corresponding to the selected recording and time period. 4. Provide playback controls shown in the reference. 5. Display an appropriate message if the video cannot be played. | **Approved** |
| **VID-07 — Download video clip.** As a fleet user, I want to download an available video clip so that I can save the recording for future reference or investigation. | Allow download of an available clip for the selected vehicle, date/time range and camera channel, subject to provider capabilities and access permissions. | 1. Allow download of an available clip. 2. Download the recording associated with the selected vehicle and channel. 3. Ensure the downloaded clip corresponds to the selected recording and time period. 4. Allow downloads only when supported by the provider and permitted for the fleet user. 5. Display an appropriate message if download fails or is unavailable. | **Approved** |

### Video Playback items to be checked

- Confirm that the ADAS provider supports the proposed recording search, timeline, playback and download capabilities.
- Confirm supported recording retention period, time-range limits, camera channels and download permissions.
- Confirm exact playback and timeline controls against the Cautio reference.

---

# Epic 5 — Incident Alert

**Objective:** Retain the Incident Alert screen's layout and functionality as shown in the Cautio reference, with incident summaries, searchable alerts, a five-column event table and related video evidence.

| ID / User Story | Feature Details | Acceptance Criteria | Status |
|---|---|---|---|
| **INC-01 — View incident summaries.** As a fleet user, I want to view incident counts by severity and event category so that I can understand the types and seriousness of ADAS incidents reported across my fleet. | Display incident summary metrics following the Cautio reference. Show total incidents and, where provider data supports it, counts grouped by severity (for example, Critical, High, Medium and Low) and event category (for example, Forward Collision Warning and Lane Departure Warning). | 1. Display the incident summary metrics included in the agreed design. 2. Show counts for provider-supported severity levels and event categories. 3. Reflect the selected fleet and applicable filters. 4. Use provider-supplied classifications; do not independently assign severity or event category. 5. Handle missing classifications as Unclassified or omit the breakdown where appropriate. | **Approved** |
| **INC-02 — Search and filter incident alerts.** As a fleet user, I want to search and filter incident alerts so that I can find events relevant to a vehicle, alert type, date or status. | Support search and filters for incident alerts using fields available in the design and provider data, such as vehicle number, alert type, event, date range, severity and status. | 1. Allow search by supported fields such as vehicle number and alert type. 2. Allow filtering by criteria included in the agreed design and supplied by the provider. 3. Show records matching the search and applied filters. 4. Allow clearing search and filters. 5. Show a clear message when no matching alerts are found. | **Approved** |
| **INC-03 — View incident alerts in a five-column table.** As a fleet user, I want to view incident alerts in a table with video proof availability so that I can identify what happened and open its captured evidence. | Display five columns: **Vehicle Number, Alert Type, Event, Date & Time, and Proof Captured**. Proof Captured indicates whether video evidence is available for that alert and provides access to the video when available. | 1. Display all five columns with clear labels. 2. Show the correct vehicle number, alert type, event and date/time for each alert. 3. In Proof Captured, clearly indicate whether video evidence is available for the corresponding alert. 4. Allow the user to open or play the associated video when available and permitted. 5. Show Not Available when no video evidence is supplied; do not imply that proof exists. 6. Ensure video evidence corresponds to the selected alert and vehicle. 7. Respect fleet-user access permissions. | **Approved** |

### Incident Alert items to be checked

- Confirm provider-supplied severity levels, event categories and incident statuses.
- Confirm the summary cards, the five incident-table columns (Vehicle Number, Alert Type, Event, Date & Time, Proof Captured), and supported search/filter fields against the Cautio reference.
- Confirm event-related video evidence availability, retrieval and playback behavior.

---
# Epic 6 — Fleet Movement History

**Objective:** Retain the Fleet Movement History screen's layout and functionality as shown in the Cautio reference.

| ID / User Story | Feature Details | Acceptance Criteria | Status |
|---|---|---|---|
| **HIST-01 — Select a vehicle.** As a fleet user, I want to select a vehicle in Fleet Movement History so that I can view its historical movement. | Provide vehicle selection within Fleet Movement History, following the Cautio reference. Retrieve historical movement information for the selected vehicle. | 1. Display available vehicles. 2. Allow vehicle selection. 3. Retrieve movement history for the selected vehicle. 4. Ensure displayed movement belongs to the selected vehicle. 5. Allow selection of another vehicle and display its movement history. | **Approved** |
| **HIST-02 — Select historical date and time period.** As a fleet user, I want to select a historical date and time period so that I can view vehicle movement during the selected period. | Provide date and time selection within Fleet Movement History, following the Cautio reference. | 1. Allow selection of a historical date. 2. Allow selection of the required time period. 3. Retrieve movement records for the selected vehicle and period. 4. Prevent invalid date/time ranges. 5. Display a message when no movement records are available. | **Approved** |
| **HIST-03 — View historical route on map.** As a fleet user, I want to view the historical route of a selected vehicle on a map so that I can understand its movement during the selected period. | Display the historical route on the map based on the selected vehicle and date/time period, following the Cautio reference. | 1. Display the historical route for the selected vehicle. 2. Show the route for the selected period. 3. Display route points in the movement sequence represented by the reference. 4. Clearly represent the route on the map. 5. Update the route when vehicle or time period changes. | **Approved** |
| **HIST-04 — View route points.** As a fleet user, I want to view individual points along a vehicle's historical route so that I can inspect movement details at specific locations. | Display individual route points on the map. When a fleet user selects a point, show available details such as location, timestamp and speed, following the Cautio reference. | 1. Display route points along the selected vehicle's historical route. 2. Show the timestamp associated with each point. 3. Allow selection of an individual route point. 4. Display available location, timestamp and speed for the selected point. 5. Ensure details correspond to the selected vehicle and historical period. 6. Confirm whether points should be ordered earliest-to-latest or latest-to-earliest against the Cautio reference before finalizing display behavior. | **To be checked — display order** |
| **HIST-05 — View trip information.** As a fleet user, I want to view trip information for a selected vehicle's historical movement so that I can understand journey details. | Display available trip information such as trip start time, end time, duration and distance travelled, following the Cautio reference. | 1. Display available trip information for the selected vehicle and period. 2. Show trip start and end times where available. 3. Show trip duration and distance where available. 4. Ensure trip information corresponds to the selected vehicle and historical route. | **Approved** |
| **HIST-06 — Navigate through historical movement.** As a fleet user, I want to navigate through a vehicle's historical movement so that I can review its journey across the selected period. | Provide the historical movement navigation controls shown in the Cautio reference. Allow navigation through recorded movement and corresponding route information. | 1. Display navigation controls shown in the reference. 2. Allow navigation through historical movement. 3. Keep route and trip information aligned with the selected movement point or segment where applicable. 4. Ensure navigation corresponds to the selected vehicle and historical period. 5. Retain the reference layout and intended behavior. | **Approved** |

### Fleet Movement History items to be checked

- Confirm from the Cautio reference whether route points are displayed earliest-to-latest or latest-to-earliest.
- Confirm the exact navigation controls and behavior shown in the reference.
- Confirm which trip details (start/end time, duration and distance) are available from the existing fleet data/provider.

---

## 4. Consolidated validation checklist

The following items remain open for validation. They do not change the stories already approved; they identify details that must be confirmed before implementation sign-off.

| Area | Item to validate | Validation basis |
|---|---|---|
| Dashboard | Availability and definitions for ADAS device storage and data pack allowance/usage fields | ADAS provider |
| Dashboard | Availability of event severity and event categories; reporting-period behavior | ADAS provider |
| Dashboard | Offline-for-more-than-48-hours calculation | Existing fleet application rule |
| ADAS > Vehicles | Provider availability and supported values for VEH-02 device status, model, manufacturer and camera configuration/type | ADAS provider |
| ADAS > Vehicles | Source and display format for the five VEH-04 columns; linked/unlinked/unknown states; VEH-03 search identifiers and filters | Existing fleet application and ADAS integration |
| Live Tracking | Speed, vehicle and channel running-status data sources; driver contact and call behavior | ADAS provider and existing application |
| Live Tracking | Exact monitoring controls and their actions | Cautio reference screenshot |
| Live Tracking | Simultaneous camera feed support, available channels and unavailable-feed behavior | Cautio reference and ADAS provider |
| Video Playback | Recording retention, search limits, playback, timeline and download capabilities | ADAS provider |
| Incident Alert | Severity, event categories, five event-table columns, search/filters and video evidence availability/playback | Cautio reference and ADAS provider |
| Fleet Movement History | Route-point order (earliest-to-latest or latest-to-earliest) | Cautio reference screenshot |
| Fleet Movement History | Navigation controls and available trip details | Cautio reference and existing fleet data |

## 5. Scope and implementation notes

- The existing fleet management application remains the host application. The ADAS section includes a separate Vehicles menu; ADAS vehicle information is not embedded in the existing Vehicles area.
- TurboHive is an example of an external ADAS provider; provider-specific capabilities and data fields must be confirmed.
- Display provider-supplied data faithfully. Do not independently invent device status, severity, event categories or other provider-owned values.
- Missing data should be shown as unavailable or unclassified as appropriate, not treated as a confirmed status.
- Preserve the reference layout and behavior for Live Tracking, Video Playback, Incident Alert and Fleet Movement History.
- The status **Approved** records the user's approval of the story wording during backlog review. It does not mean provider feasibility or every detailed UI behavior has already been technically validated.

## 6. Change log

- **Version 5.1:** Revised Epic 2 to define Vehicles as a separate menu under the ADAS section, distinct from the existing Vehicles area; added user stories for opening the menu, viewing/searching the ADAS vehicle list, and viewing vehicle and device details; made manufacturer and model separate detail fields; updated review summary and validation checklist.
- **Version 5.2:** Consolidated Epic 2 into four stories. Combined key ADAS table fields into VEH-02 (device status, model/model number, manufacturer and camera configuration/type), kept VEH-03 as a standalone vehicle search story, and moved other device information into VEH-04 details.
- **Version 5.3:** Consolidated Epic 3 by combining vehicle selection, live feed viewing, channel display and channel switching into LIVE-01; added LIVE-02 for vehicle speed, channel and vehicle running statuses, and the Call Driver action; retained the reference-control story as LIVE-03 and updated validation items.
- **Version 5.4:** Consolidated Epic 5 into four stories by grouping incident severity and category summaries, combining the event table with search and filters, adding a dedicated event-details and evidence story, and retaining export; updated the review summary and validation checklist.
- **Version 5.5:** Removed the merged vehicle status distribution story and the excluded fleet activity trends story; updated the Dashboard review summary and removed unused Merged/Removed status definitions.
- **Version 5.6:** Renumbered the remaining Dashboard ADAS stories sequentially after removing the merged and excluded stories: DASH-05 to DASH-03 and DASH-06 to DASH-04; updated the review summary.
- **Version 5.7:** Reworked DASH-03 to cover ADAS device storage and data pack information, with acceptance criteria for provider-supplied capacity, usage, remaining allowance, units and update time.
- **Version 5.8:** Marked all Epic 1 stories (DASH-01 through DASH-04) as Approved and updated the Dashboard review summary.
- **Version 5.9:** Removed VEH-04 from Epic 2 and updated the Epic 2 objective, review summary and validation checklist to reflect the remaining stories.
- **Version 6.0:** Added VEH-04 to define the five vehicle columns in the ADAS Vehicles table: Vehicle Number, Organization, Alias, Vehicle Status and Device Linked; updated the Epic 2 objective, review summary and validation checklist.
- **Version 6.1:** Marked all Epic 2 stories, VEH-01 through VEH-04, as Approved and updated the review summary.
- **Version 6.2:** Updated Epic 2 validation notes to match VEH-02 device fields, VEH-03 search behavior and the five VEH-04 vehicle table columns, including device-link states.
- **Version 6.3:** Removed INC-04 (Export incident events) from Epic 5 and updated the review summary and validation notes.
- **Version 6.4:** Added INC-03 for the five incident table columns and video proof availability, moved the incident detail/evidence story to INC-04, and updated the Epic 5 summary and validation checklist.
- **Version 6.5:** Removed INC-04 (View incident event details and evidence) and updated the Epic 5 objective, review summary and validation notes; video evidence access remains covered by INC-03.
