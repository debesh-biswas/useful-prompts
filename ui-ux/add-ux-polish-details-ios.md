# Add UX Polish Details: iOS

**Use when:** you want an AI coding agent to check your native iOS app (SwiftUI or UIKit) against 15 proven UX details and build the ones you approve
**Inputs:** none. Run it from inside your project.
**Works with:** coding agents that can read and edit your code (Claude Code, Cursor, Codex). For other platforms use the [web](add-ux-polish-details-web.md), [Android](add-ux-polish-details-android.md) or [React Native](add-ux-polish-details-react-native.md) version.

## Prompt

```
Check my iOS app against the 15 UX details below.

Before you start: work out the stack (SwiftUI or UIKit, minimum iOS version, data/networking/image libraries) and how to build and test it (xcodebuild scheme, tests, SwiftLint if present). Tell me in a few lines.

Then report on all 15 first, each marked:
- Already done: where it is.
- Missing: what you'd change, and which files.
- Doesn't fit: why (no such screen, below the minimum iOS version, or it needs backend work you can't do from here).

Build only the ones I approve, one at a time, and build and run the tests after each. Fix what breaks before moving on.

While you build:
- Use what the project already has before you add a package, and match the existing code style. If a detail truly needs a new dependency, say which and why before adding it.
- Every animation respects Reduce Motion.
- Keep everything usable with VoiceOver and Dynamic Type.
- Respect the minimum iOS version; gate newer APIs with availability checks.
- Don't commit unless I ask.

For each one you build, tell me what changed, which files, and how I can see it working.

The 15:

Loading & speed (Doherty Threshold: respond in under 0.4s, or look like you did)
1. Skeleton loaders. Use .redacted(reason: .placeholder) on the real view with sample data while content loads, so nothing jumps. Only show it if loading takes longer than about 300ms.
2. Stale-while-revalidate. Show cached data instantly and refresh in the background, again when the app returns to the foreground (scenePhase) or the network comes back (NWPathMonitor). Not for balances, stock counts, or anything where old data costs money.
3. BlurHash placeholders. Store a BlurHash or ThumbHash with each uploaded image and show the decoded blur at the image's exact size while the real one loads.

Feedback & safety (Feedback Loops: every action gets a visible response)
4. Optimistic updates. Small actions like likes, toggles and renames update the UI right away and roll back with an error if the request fails. Never for payments.
5. Undo instead of confirm. For anything reversible, like delete or archive, drop the confirmation alert. Do it right away and show an Undo banner for 5 to 10 seconds, with a soft delete or a delayed request behind it. Register it with UndoManager where it fits, and announce it to VoiceOver.
6. Idempotency keys. Make a UUID when the user starts a payment or anything that creates a record, send it as the Idempotency-Key on every retry of that action, and have my own API honour it (same key = return the first result). Disable the button while the request runs.

Navigation & input (Hick's Law, Recognition over Recall)
7. Keyboard shortcuts. If the app runs on iPad or Mac, add .keyboardShortcut to main actions in .commands menus (or UIKeyCommand in UIKit) so they show in the iPad menu bar (iPadOS 26+) and the hold-⌘ overlay (iPadOS 18 and earlier). Skip for iPhone-only apps.

Motion (Jakob's Law: feel like the platform people already know)
8. Sheets. Use .sheet with .presentationDetents (or UISheetPresentationController) so sheets follow the finger and dismiss with a swipe. Keep a close button too.
9. Interruptible animations. Use spring animations (withAnimation(.spring), UIViewPropertyAnimator in UIKit) that turn around from their current position and speed when interrupted. Never block touches while something animates.
10. Zoom transitions. On iOS 18+, use .navigationTransition(.zoom(sourceID:in:)) with .matchedTransitionSource so a thumbnail grows into its detail screen. Fall back to the default push below iOS 18.

Touch & device (Fitts's Law: big, close targets are easier to hit)
11. Touch targets. Every tap target is at least 44 by 44 points, even when the icon is smaller, using .frame(minWidth: 44, minHeight: 44) with .contentShape(Rectangle()) or padding, without overlapping its neighbours.
12. Safe areas. Nothing tappable sits under the Dynamic Island, notch or home indicator. Only backgrounds use .ignoresSafeArea; use .safeAreaInset for custom bars.
13. One-time-code autofill. .textContentType(.oneTimeCode) with .keyboardType(.numberPad), and the text message ends with a line like "@yourdomain.com #123456".

Typography & shape (Visual Hierarchy, Aesthetic-Usability Effect)
14. Tabular numbers. .monospacedDigit() on timers, prices, counters and table columns.
15. Continuous corners. RoundedRectangle(cornerRadius:style: .continuous) in SwiftUI and layer.cornerCurve = .continuous in UIKit.
```
