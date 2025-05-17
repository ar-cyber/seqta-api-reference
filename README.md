
# By using this program, you agree that you will not use these APIs maliciously. We are not responsible for any damages
# SEQTA Learn API Reference
A reference for some undocumented APIs<br>
**Base URL:** `/seqta/student`

## All endpoints need the `JSESSIONID` cookie
## General APIs
### <code style="background-color: orangered">POST</code> `/login`

*__This endpoint requires the `_ga` cookies to be passed__*

Log in to SEQTA. This is the endpoint after you log in and a `JSESSIONID` token is generated.
#### Request
Body is in JSON format. It is required.
##### Sample body
```json
{
  "mode":"normal",
  "redirect_url":"blahblahblah"
}
```
The `redirect_url` parameter can be anything, but it is a required parameter.
#### Response
Response is in JSON format
##### Response format
```js
{
  "payload": {
    "lastAccessedTime": Number,
    "personUUID": String,
    "meta": { "code": Number, "governmentID": Any },
    "clientIP": "user identification",
    "saml": [
      {
        "autologin": Boolean,
        "request": "the output of ms auth",
        "relaystate": "the output of ms auth",
        "method": "POST",
        "signature": "secret b64 key",
        "slo": Boolean,
        "label": String,
        "sigalg": String,
        "url": "the query for ms auth"
      }
    ],
    "userDesc": String,
    "id": Number,
    "type": "student",
    "userName": String,
    "userCode": String,
    "email": String,
    "status": "200"
  },
  "status": "200"
}
```
- SAML might not be present in any query. As no JSON is provided, the simple login cannot be shown here.
- The ID is more important then the usercode. Accessing stuff is dependent on it

### <code style="background-color: orangered">POST</code> `/load/settings`
Load the settings for a user. This might be missing data as it is most of the time different between instances.<br>
*__No request body is needed for this endpoint__*
#### Response
Returns JSON
##### Response format (do not rely on; can be different)
```js
{
    "payload": {
      "global.communications.phone.exit_code": {
        "value": String
      },
      "global.notifications.email.minimumAge": { "value": String },
      "global.ai.api.baseurl": { "value": "https://ai.seqta.com/" },
      "coneqt-s.events.contacts.enabled": { "value": "enabled/disabled" },
      "coneqt-s.synergetic.community.pages.events": { "value": "enabled/disabled" },
      "coneqt-s.messages.students.enabled": { "value": "enabled/disabled" },
      "coneqt-s.events.staff.enabled": { "value": "enabled/disabled" },
      "global.datacube": { "value": "enabled/disabled" },
      "global.folios": { "value": "enabled/disabled" },
      "coneqt-s.synergetic.community.pages.selfassessment": {
        "value": "enabled/disabled"
      },
      "coneqt-s.forum.photos": { "value": "enabled/disabled" },
      "global.ai.lessonplan": { "value": "enabled/disabled" },
      "coneqt-s.page.forums": { "value": "enabled/disabled" },
      "global.myed": { "value": "enabled/disabled" },
      "coneqt-s.page.folios": { "value": "enabled/disabled" },
      "coneqt-s.events.students.enabled": { "value": "enabled/disabled" },
      "coneqt-s.synergetic.community.pages.applications": { "value": "enabled/disabled" },
      "coneqt-s.events.tutors.enabled": { "value": "enabled/disabled" },
      "coneqt-s.page.reports": { "value": "enabled/disabled" },
      "coneqt-s.synergetic.community.pages.timetable": { "value": "enabled/disabled" },
      "coneqt-s.mediaRecorder.enabled": { "value": "enabled/disabled" },
      "coneqt-s.page.goals": { "value": "enabled/disabled" },
      "coneqt-s.synergetic.community.pages.electives": { "value": "enabled/disabled" },
      "coneqt-s.timetable.email": { "value": "enabled/disabled" },
      "global.microsoftTeams.pilot": { "value": "enabled/disabled" },
      "coneqt-s.filesize.limit": { "value": String }, // Allowed filesize in MB
      "coneqt-s.synergetic.community.pages.docs": { "value": "enabled/disabled" },
      "global.ai.credits": { "value": String }, // If the `global.ai.lessonplan is disabled, this parameter is useless
      "coneqt-s.googleAnalytics": {}, // Different for each school
      "url.coneqt-s": { "value": String },
      "global.dashlet.summarised-assessment-feedback": { "value": "enabled/disabled" },
      "global.microsoftTeams.directoryId": {
        "value": String // Secret key
      },
      "global.forums.usePrefName": { "value": "enabled/disabled" },
      "coneqt-s.page.notices": { "value": "enabled/disabled" },
      "attendance.defaults.time_from": { "value": String },
      "coneqt-s.synergetic.community.pages.accommodation": {
        "value": "enabled/disabled"
      },
      "global.ai.client.secret": {
        "value": String // Private key
      },
      "global.url.seqtaresources": {
        "value": String // URL
      },
      "coneqt-s.assessments.customtext": { "value": "enabled/disabled" },
      "global.ai.api.token": { "value": "token" },
      "coneqt-s.forum.greeting": {
        "value": String // Rich text (HTML)
      },
      "global.requestedAbsences": { "value": "enabled/disabled" },
      "coneqt-s.synergetic.community.pages.absences": { "value": "enabled/disabled" },
      "global.datacube.dailyexport": { "value": "enabled/disabled" },
      "global.microsoftTeams.domainName": { "value": String },
      "coneqt-s.timetable.attendance": { "value": "enabled/disabled" },
      "attendance.defaults.time_to": { "value": String },
      "coneqt-s.messages.contacts.enabled": { "value": "enabled/disabled" },
      "global.microsoftTeams.applicationId": {
        "value": String // Secret Key
      },
      "coneqt-s.goals.message": {
        "value": String // Markdown
      },
      "global.email.defaultFrom": { "value": String },
      "global.microsoftTeams.clientSecret": {
        "value": String // Secret Key
      },
      "coneqt-s.page.documents": { "value": "enabled/disabled" },
      "coneqt-s.synergetic.community.pages.results": { "value": "enabled/disabled" },
      "coneqt-s.synergetic.community.pages.excursions": { "value": "enabled/disabled" },
      "global.microsoftTeams.features": { "value": "enabled/disabled" },
      "global.email.feedbackExtra": { "value": String },
      "coneqt-s.courses": { "value": "enabled/disabled" },
      "global.oneDrive.clientId": {
        "value": String // Secret Key
      }
    },
    "status": "200"
  }
  ```
- Schools that do not use shittygenic will have to use other ways; this only covers synergetic-based systems

# Brought to you by SockyCat.net and the BetterSEQTA team!!! 
