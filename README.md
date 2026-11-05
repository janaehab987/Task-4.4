# Campus Lost & Found — ACL UI/UX Lab

This is a **standalone React demo** for one session of the UI/UX Rescue Challenge. It uses realistic example records stored in this browser; it does not connect to MongoDB or the previous lab API.

## Run

```bash
npm install
npm run dev
```

The terminal prints **one local URL**. Open that link in your normal external browser. The development server will **not** open a browser automatically. Press `Ctrl+C` to stop it.

## Functional brief

Users browse, search and filter item reports, create reports with an optional photo, and edit only their own reports. Uploaded JPEG, PNG, and WebP images are resized and stored with the report in this browser. Reports have lost, found and claimed states. The same title at the same location may not be reported twice. Some found items have been handed to fictional campus collection points; others have only been reported. A reported item is not automatically confirmed as being held by staff.

### Fields from the prior lab

- `title` — Item title: at least two characters
- `status` — Status: lost, found or claimed
- `category` — Category: electronics, clothing, documents, accessories, other
- `location` — Location: optional
- `description` — Description: optional

The demo supports create/edit and stores your updates in browser `localStorage` for this browser. **Reset demo** restores the example records. You can assume the current signed-in user is `You`.

## User scenario for this session

Someone lost an item and wants to find a matching notice. Another student needs to report an item they found. The campus uses designated collection points for handing over and recovering found property, after ownership is verified.

Your redesign should support the scenario above without removing or weakening the existing features.

## UI/UX Rescue Challenge (25–30 minutes)

**Your mission:** use this interface as an end user, find **at least three distinct, meaningful UI/UX problems**, and fix all three with AI assistance.

- Explain the user's goal and why each issue hurts usability.
- Ask AI to suggest alternatives and compare trade-offs before you implement a solution.
- Choose your own changes; there is no prescribed visual redesign.
- Preserve all working behavior and relevant validation.
- Demonstrate the main action, one unsuccessful action, and your three improvements.

**Submit:** the modified React files, before/after screenshots, three brief justifications, and one example of an AI design suggestion you refined or rejected.

**Evaluation:** We assess usability reasoning, design consistency, preserved functionality, and testing. Using AI is allowed and expected. Cosmetic changes alone are not sufficient.

## Rescue redesign notes

### Goal and changes

The user wants to find a likely match for a lost item, or report a found item and understand whether it has actually been handed to campus staff.

1. **Live filtering was paired with a redundant Apply button.** Search and filters already changed the board immediately, while Apply only displayed a count. The count is now continuously visible and the confusing extra step is removed.
2. **An empty result gave no way forward.** “Nothing here yet” did not explain whether a search had failed or what to try next. A no-results state now suggests clearing filters or posting a report.
3. **Found reports did not guide the handover step.** The form now explains that a report alone does not confirm staff custody; found cards distinguish reported-only items from items held at a named point and remind users to verify ownership at pickup. Validation errors also show the actual correction needed.
4. **Status navigation was hard to scan across separate sections.** LOST, FOUND, and CLAIMED are now selectable buttons that show one status at a time; keyword and category search remain available.
5. **Reports had no way to show an item's appearance.** The form now accepts an optional JPEG, PNG, or WebP photo, shows a preview, and displays the saved photo on the report card.

### Alternatives considered

A guided “match finder” could ask about item type and location before showing results, but would add steps and replace the quick noticeboard workflow. The selected improvements keep the existing board and report form, preserving direct browsing while making its state and next actions clearer. The status buttons show one status at a time, while keeping status counts visible to make switching straightforward.

### Demonstration and screenshots

- [Before redesign](./before.png)
- [After redesign](./after.png)
- Main action: search/filter reports, then publish a found-item report with an optional photo.
- Unsuccessful action: submit an invalid or duplicate report and read the specific validation message.
- Suggested change refined: AI suggested a guided match-finder flow; I kept the faster board and instead clarified live search results and recovery actions. Cosmetic changes alone are not sufficient.
