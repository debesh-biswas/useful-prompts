# Add UX Polish Details: Android

**Use when:** you want an AI coding agent to check your native Android app (Jetpack Compose or Views) against 16 proven UX details and build the ones you approve
**Inputs:** none. Run it from inside your project.
**Works with:** coding agents that can read and edit your code (Claude Code, Cursor, Codex). For other platforms use the [web](add-ux-polish-details-web.md), [iOS](add-ux-polish-details-ios.md) or [React Native](add-ux-polish-details-react-native.md) version.

## Prompt

```
Check my Android app against the 16 UX details below.

Before you start: work out the stack (Compose or Views, minSdk and targetSdk, data/networking/image libraries) and the project's check commands (Gradle build, lint, unit tests). Tell me in a few lines.

Then report on all 16 first, each marked:
- Already done: where it is.
- Missing: what you'd change, and which files.
- Doesn't fit: why (no such screen, below minSdk, or it needs backend work you can't do from here).

Build only the ones I approve, one at a time, and run the project's checks after each. Fix what breaks before moving on.

While you build:
- Use what the project already has before you add a library, and match the existing code style. If a detail truly needs a new dependency, say which and why before adding it.
- Every animation respects the system "Remove animations" setting.
- Keep everything usable with TalkBack and large font sizes.
- Respect minSdk; gate newer APIs with version checks.
- Don't commit unless I ask.

For each one you build, tell me what changed, which files, and how I can see it working.

The 16:

Loading & speed (Doherty Threshold: respond in under 0.4s, or look like you did)
1. Skeleton loaders. Placeholder shapes in the layout of the real content, built from the same composable or layout so nothing jumps. Only show them if loading takes longer than about 300ms.
2. Stale-while-revalidate. Show cached data instantly (Room, DataStore or the HTTP cache) and refresh in the background, again when the app resumes or the network comes back. Not for balances, stock counts, or anything where old data costs money.
3. BlurHash placeholders. Store a BlurHash or ThumbHash with each uploaded image and show the decoded blur at the image's exact size while the real one loads.

Feedback & safety (Feedback Loops: every action gets a visible response)
4. Optimistic updates. Small actions like likes, toggles and renames update the UI right away and roll back with an error if the request fails. Never for payments.
5. Undo snackbars. For anything reversible, like delete or archive, drop the confirmation dialog. Do it right away and show a Snackbar with an Undo action for 5 to 10 seconds, with a soft delete or a delayed request behind it. Make sure TalkBack announces it.
6. Idempotency keys. Make a UUID when the user starts a payment or anything that creates a record, send it as the Idempotency-Key on every retry of that action, and have my own API honour it (same key = return the first result). Disable the button while the request runs.

Navigation & input (Hick's Law, Recognition over Recall)
7. Keyboard shortcuts. If the app supports tablets, foldables or ChromeOS, handle hardware keyboard shortcuts for main actions and list them with onProvideKeyboardShortcuts so they appear in the system shortcuts helper. Skip for phone-only apps.

Motion (Jakob's Law: feel like the platform people already know)
8. Bottom sheets. Use Material 3 ModalBottomSheet (or BottomSheetDialogFragment) so sheets follow the finger and dismiss on drag. Keep a close button too.
9. Interruptible animations. Use spring-based animations (animate*AsState / Animatable with spring() in Compose, SpringAnimation in Views) that continue from the current value and velocity when interrupted. Never block touches while something animates.
10. Predictive back. Move back handling to OnBackPressedCallback, or BackHandler / PredictiveBackHandler in Compose, and remove onBackPressed overrides, so the back swipe can preview the previous screen. It's on by default when targeting Android 16, where onBackPressed and KEYCODE_BACK are no longer called.
11. Shared element transitions. Use SharedTransitionLayout with Modifier.sharedElement in Compose (or the Navigation/Fragment shared element APIs in Views) so a thumbnail grows into its detail screen. Under 300ms.

Touch & device (Fitts's Law: big, close targets are easier to hit)
12. Touch targets. Every tap target is at least 48 by 48 dp, even when the icon is smaller, using Modifier.minimumInteractiveComponentSize() or padding in Compose and minWidth/minHeight or a TouchDelegate in Views, without overlapping its neighbours.
13. Edge-to-edge insets. Call enableEdgeToEdge() and apply WindowInsets (safeDrawing, systemBars, displayCutout) so nothing tappable sits under the status bar, camera cutout or gesture navigation bar. Edge-to-edge is enforced when targeting Android 15.
14. One-time-code autofill. Use the SMS Retriever API (the message ends with your app's 11-character hash) or the SMS User Consent API, never the READ_SMS permission. Mark the field as a one-time code so autofill can fill it.

Typography (Visual Hierarchy, Aesthetic-Usability Effect)
15. Tabular numbers. fontFeatureSettings = "tnum" on the text style for timers, prices, counters and table columns.
16. Balanced headlines. In Compose, lineBreak = LineBreak.Heading on headings and short titles, LineBreak.Paragraph on body text.
```
