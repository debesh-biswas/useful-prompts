# Add UX Polish Details: Web

**Use when:** you want an AI coding agent to check your web app against 19 proven UX details and build the ones you approve
**Inputs:** none. Run it from inside your project.
**Works with:** coding agents that can read and edit your code (Claude Code, Cursor, Codex). For native apps use the [iOS](add-ux-polish-details-ios.md), [Android](add-ux-polish-details-android.md) or [React Native](add-ux-polish-details-react-native.md) version.

## Prompt

```
Check my web app against the 19 UX details below.

Before you start: work out the stack (framework, router, styling, UI/animation/data libraries) and the project's check commands (lint, typecheck, test, build). Tell me in a few lines.

Then report on all 19 first, each marked:
- Already done: where it is.
- Missing: what you'd change, and which files.
- Doesn't fit: why (no such screen, or it needs backend work you can't do from here).

Build only the ones I approve, one at a time, and run the project's checks after each. Fix what breaks before moving on.

While you build:
- Use what the project already has before you add a library, and match the existing code style. If a detail truly needs a new dependency, say which and why before installing it.
- Every animation respects prefers-reduced-motion.
- Keep everything usable by keyboard and screen reader (focus moves into and back out of menus and sheets).
- Don't commit unless I ask.

For each one you build, tell me what changed, which files, and how I can see it working.

The 19:

Loading & speed (Doherty Threshold: respond in under 0.4s, or look like you did)
1. Skeleton loaders. Gray blocks in the shape of the real layout while content loads, made from the same component as the loaded state so nothing jumps. Only show them if loading takes longer than about 300ms.
2. Stale-while-revalidate. Show cached data instantly and refetch in the background, again when the window regains focus or the network comes back. Not for balances, stock counts, or anything where old data costs money.
3. Prerendering. Speculation rules with eagerness "moderate" for same-site links, leaving out logout and any link that changes data. Check what the router already prefetches first.
4. BlurHash placeholders. Store a BlurHash or ThumbHash with each uploaded image and show the blur at the image's exact size while the real one loads.

Feedback & safety (Feedback Loops: every action gets a visible response)
5. Optimistic updates. Small actions like likes, checkboxes and renames update the screen right away and roll back with an error if the request fails (useOptimistic in React 19, or the data library's optimistic update). Never for payments.
6. Undo toasts. For anything reversible, like delete or archive, drop the confirm dialog. Do it right away and show an Undo toast for 5 to 10 seconds, with a soft delete or a delayed request behind it. The toast has role="status".
7. Idempotency keys. Make a UUID when the user starts a payment or anything that creates a record, send it as the Idempotency-Key on every retry of that action, and have my own API honour it (same key = return the first result). Disable the button while the request runs.

Navigation & input (Hick's Law, Recognition over Recall)
8. Command menu. Cmd+K or Ctrl+K opens a search of every page and action that works with the keyboard alone. Only in apps people use every day.
9. Shortcut hints. Show each action's keyboard shortcut in menus, tooltips and the command menu, with ⌘ on Mac and Ctrl elsewhere. Shortcuts don't fire while someone is typing in a field.
10. Safe triangle. Hover menus with submenus don't switch while the cursor moves diagonally toward the open submenu (safePolygon in Floating UI, or the menu library's own version).

Motion (Jakob's Law: feel like the platform people already know)
11. View transitions. document.startViewTransition for changes on one page, @view-transition { navigation: auto; } between pages, and the same view-transition-name on elements that move between them. Under 300ms.
12. Swipe-to-dismiss sheets. On touch screens, bottom sheets follow the finger and close on distance or a quick flick (Vaul or the UI library's own sheet). Keep a close button too.
13. Interruptible animations. Springs or transitions that turn around from their current position when interrupted. No CSS keyframes on anything a user can interrupt, and never block input while something animates.

Touch & device (Fitts's Law: big, close targets are easier to hit)
14. Touch targets. On touch screens every tap target is at least 44 by 44 CSS pixels, even when the icon is smaller, using padding or a pseudo-element, without overlapping its neighbours.
15. Safe-area insets. viewport-fit=cover and env(safe-area-inset-*) so nothing tappable sits under the notch, the Dynamic Island or the home indicator on phones.
16. One-time-code autofill. One input with autocomplete="one-time-code" and inputmode="numeric", and the text message ends with a line like "@yourdomain.com #123456".

Typography & shape (Visual Hierarchy, Aesthetic-Usability Effect)
17. Tabular numbers. font-variant-numeric: tabular-nums on timers, prices, counters and table columns.
18. Balanced headlines. text-wrap: balance on headings and short titles, text-wrap: pretty on paragraphs.
19. Continuous corners. corner-shape: squircle next to the existing border-radius, which only Chromium browsers draw and everything else ignores.
```

## What each one is

1. **Skeleton loaders:** the page shape appears first, so it feels faster and nothing jumps.
2. **Stale-while-revalidate:** going back to a screen never shows a spinner.
3. **Prerendering:** the next page loads while you hover, and browsers without support ignore it.
4. **BlurHash:** a 20–30 character string decodes into a blurry preview, so the right colours show from the first frame.
5. **Optimistic updates:** the heart fills in instantly and rolls back only if the request fails.
6. **Undo toasts:** act now, offer Undo. People click through confirm dialogs without reading them anyway.
7. **Idempotency keys:** a retried "Pay" tap returns the first result instead of charging twice.
8. **Command menu:** Cmd+K finds any page or action, so nobody has to remember which menu it's in.
9. **Shortcut hints:** people learn shortcuts just by seeing them next to actions.
10. **Safe triangle:** moving the cursor diagonally toward a submenu doesn't switch it.
11. **View transitions:** the browser animates between pages (thumbnail → full photo) with a few lines of CSS.
12. **Swipe-to-dismiss sheets:** drag or flick a bottom sheet away.
13. **Interruptible animations:** grab something mid-motion and it turns around from where it is.
14. **Touch targets:** the touch area is bigger than the visible icon.
15. **Safe-area insets:** keeps UI clear of the notch, the Dynamic Island and the home bar.
16. **One-time-code autofill:** the SMS code appears above the keyboard and fills in with one tap.
17. **Tabular numbers:** every digit has the same width, so changing numbers stop wiggling.
18. **Balanced headlines:** no single word left alone on the last line.
19. **Continuous corners:** Apple-style smooth squircle corners.
