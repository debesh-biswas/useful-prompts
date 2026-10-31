# Add UX Polish Details: React Native

**Use when:** you want an AI coding agent to check your React Native or Expo app against 14 proven UX details and build the ones you approve
**Inputs:** none. Run it from inside your project.
**Works with:** coding agents that can read and edit your code (Claude Code, Cursor, Codex). For other platforms use the [web](add-ux-polish-details-web.md), [iOS](add-ux-polish-details-ios.md) or [Android](add-ux-polish-details-android.md) version.

## Prompt

```
Check my React Native app against the 14 UX details below.

Before you start: work out the stack (Expo or bare React Native, version, navigation, data fetching, animation and image libraries) and the project's check commands (lint, typecheck, test). Tell me in a few lines.

Then report on all 14 first, each marked:
- Already done: where it is.
- Missing: what you'd change, and which files.
- Doesn't fit: why (no such screen, or it needs backend work you can't do from here).

Build only the ones I approve, one at a time, and run the project's checks after each. Fix what breaks before moving on.

While you build:
- Use what the project already has before you add a library, and match the existing code style. If a detail truly needs a new dependency, say which and why before installing it.
- Every animation respects the system reduce-motion setting.
- Keep everything usable with VoiceOver and TalkBack (accessibilityLabel, accessibilityRole).
- Check behaviour on both iOS and Android.
- Don't commit unless I ask.

For each one you build, tell me what changed, which files, and how I can see it working.

The 14:

Loading & speed (Doherty Threshold: respond in under 0.4s, or look like you did)
1. Skeleton loaders. Gray blocks in the shape of the real layout while content loads, made from the same component as the loaded state so nothing jumps. Only show them if loading takes longer than about 300ms.
2. Stale-while-revalidate. Show cached data instantly and refetch in the background, again when the app returns to the foreground (AppState) or the network comes back (NetInfo). Wire these into the data library if it supports it. Not for balances, stock counts, or anything where old data costs money.
3. BlurHash placeholders. Store a BlurHash or ThumbHash with each uploaded image and show the blur at the image's exact size while the real one loads (expo-image supports both as a placeholder).

Feedback & safety (Feedback Loops: every action gets a visible response)
4. Optimistic updates. Small actions like likes, toggles and renames update the UI right away and roll back with an error if the request fails (useOptimistic in React 19, or the data library's optimistic update). Never for payments.
5. Undo toasts. For anything reversible, like delete or archive, drop the confirm alert. Do it right away and show an Undo toast for 5 to 10 seconds, with a soft delete or a delayed request behind it. Announce it with AccessibilityInfo.announceForAccessibility.
6. Idempotency keys. Make a UUID when the user starts a payment or anything that creates a record, send it as the Idempotency-Key on every retry of that action, and have my own API honour it (same key = return the first result). Disable the button while the request runs.

Motion (Jakob's Law: feel like the platform people already know)
7. Bottom sheets. Use @gorhom/bottom-sheet (or the existing sheet library) so sheets follow the finger and close on distance or a quick flick. Keep a close button too.
8. Interruptible animations. Use springs (Reanimated withSpring, or Animated.spring) that turn around from their current position and velocity when interrupted. Never block touches while something animates.
9. Predictive back (Android). Apps targeting Android 16 get predictive back by default, and onBackPressed and KEYCODE_BACK are no longer called, so BackHandler and the navigation library can stop receiving back and the app closes instead. Check whether the installed React Native and navigation versions support it and test the back swipe. If they don't, opt out for now with android:enableOnBackInvokedCallback="false" in AndroidManifest.xml.

Touch & device (Fitts's Law: big, close targets are easier to hit)
10. Hit slop. Every tap target is at least 44 by 44 points on iOS and 48 by 48 dp on Android, even when the icon is smaller, using hitSlop or padding, without overlapping its neighbours.
11. Safe areas. Use react-native-safe-area-context (SafeAreaView or useSafeAreaInsets) so nothing tappable sits under the notch, the Dynamic Island, the status bar or the home indicator.
12. One-time-code autofill. textContentType="oneTimeCode" for iOS, autoComplete="sms-otp" for Android, keyboardType="number-pad", and the text message ends with a line like "@yourdomain.com #123456".

Typography & shape (Visual Hierarchy, Aesthetic-Usability Effect)
13. Tabular numbers. fontVariant: ['tabular-nums'] on timers, prices, counters and table columns.
14. Continuous corners. borderCurve: 'continuous' next to borderRadius (iOS only; Android ignores it).
```
