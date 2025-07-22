What you submitted
Case number: 751402627302207
Title
Race Condition in WhatsApp Polls Leads to Negative Vote Count
Vuln Type
Other
Product Area
Android
Description/Impact
Summary:
A race condition exists in the WhatsApp mobile application's polling feature that allows a user to generate a negative vote count (-1) on a poll option. The bug is triggered when an admin rapidly switches their vote between two options within a poll posted in a WhatsApp Channel.

Device & Environment Details:

Device: Samsung M21 (SM-M215F/DS)

Operating System: Android 12

WhatsApp Version: 2.25.19.83

Environment: A WhatsApp Channel


Expected Result:
The vote count for any option should always be a non-negative integer (0 or greater). The final vote should correctly reflect the last option selected by the user.

Actual Result:
The vote count for the option that was last "un-voted" decrements past zero and displays as −1.

The direct security or privacy risk from this finding appears to be minimal to none. The bug does not seem to leak user data, bypass privacy settings, or allow for any malicious actions against other users.

The primary impact is on the integrity and reliability of the user interface:

Data Integrity: It corrupts the visual representation of the poll's data by displaying a logically impossible state (a -1 vote count).

User Experience: The bug creates a confusing and broken user experience, which could reduce user trust in the reliability of the WhatsApp polling feature.

Application Logic: It highlights a race condition in the application's state management. While this specific instance only affects the UI, such logic flaws can sometimes have other, more subtle implications for application stability.
Repro Steps
Mobile app version: 2.25.19.83

Users: A single user (User A) who is an admin of a WhatsApp Channel.

Environment: A WhatsApp Channel where User A is an admin with permission to create polls.

Browser: n/a (This is a mobile application bug.)

OS: Android 12

1. Open WhatsApp on your Android device and navigate to a Channel where you are an admin.

2. As the admin, create and post a new poll with at least two distinct options (e.g., "Option A" and "Option B").

3. Cast an initial vote for "Option A." Observe that its count becomes 1.

4. Rapidly and repeatedly tap to switch your vote between "Option A" and "Option B" in quick succession (approximately 5-10 taps within a 2-3 second interval).

5. Cease tapping and observe the poll's vote counts to see the bug appear.
