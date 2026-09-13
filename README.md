# Contribution README

## Large Issue: LibrePhotos #544

**Issue:** [Allow copy photo to clipboard #544](https://github.com/LibrePhotos/librephotos/issues/544)

### Problem Summary

LibrePhotos currently creates a blank 0-byte `.webp` file when a user tries to copy a photo from the timeline to the clipboard. The issue is to add functionality that allows users to copy a photo in a compatible format, such as JPG, and paste it directly into another application. This could be implemented through a "Copy to Clipboard" menu option, a copy icon, or a keyboard shortcut.

---

## Medium Issue: Agent Tools MCP Hub #101

**Issue:** [Add Fear and Greed Crypto Sentiment Index Tool (Python) #101](https://github.com/tarunjandra/agent-tools-mcp-hub/issues/101)

### Problem Summary

The project needs a new Python tool that retrieves the daily Crypto Fear and Greed Index and historical sentiment data from the public Alternative.me API. The tool should accept a `days` parameter from 1 to 30, return the current sentiment score, classification, and multi-day trend history, and include the required `tool.py`, `metadata.json`, `requirements.txt`, and `README.md` files. It must also pass the project's tool validation script.

---

## Small Issue: DrumBeatRepo #511

**Issue:** [UI: Add a SVG icon for the crash cymbal #511](https://github.com/Babali42/DrumBeatRepo/issues/511)

### Problem Summary

The Rock Variation Pattern in DrumBeatRepo is missing an icon for the crash cymbal even though MIDI note 49 is correctly configured. The issue requires adding an appropriate SVG crash cymbal icon to the UI and ensuring it is correctly associated with the existing drum pattern configuration and UI tests.






## Phase II: Reproduce & Plan

### Reproduction Process

#### Environment Setup

I forked the LibrePhotos repository and set up the project locally following the project's development instructions. I created a working branch named `clipboard` for Issue #544 so that the reproduction and planned changes can be isolated from the main branch.

#### Steps to Reproduce

1. Start the LibrePhotos application in the local development environment.
2. Navigate to the photo timeline.
3. Select a photo.
4. Open the available photo actions.
5. Attempt to copy the selected photo to the clipboard.
6. Paste the copied content into another application that supports image data.
7. Observe the resulting clipboard content.
8. Repeat the process to confirm that the behavior is consistent.

**Expected:** The selected photo should be copied to the clipboard as usable image data so that it can be pasted directly into another application.

**Actual:** LibrePhotos currently produces a blank 0-byte `.webp` file instead of providing usable image data through the clipboard.

### Reproduction Evidence

**Working Branch:** https://github.com/shanker-codepath/librephotos/tree/clipboard

---

## Solution Approach

### Implementation Plan

**Understand:**

LibrePhotos currently does not provide a working way to copy a photo directly to the clipboard. The goal is to allow a selected photo to be copied as image data rather than creating an empty file.

**Match:**

I will investigate the existing photo actions, including Download, Favorite, and Delete, to understand how actions on selected photos are implemented. I will specifically examine `SelectionActions.tsx` and the existing download functionality, including `DownloadPhotoMutation`, to determine how the application currently retrieves and handles photo data.

**Plan:**

1. Locate the existing photo selection actions.
2. Inspect `SelectionActions.tsx` to determine where a Copy action should be added.
3. Determine how LibrePhotos retrieves the actual photo/image data.
4. Investigate whether the existing download functionality or related utilities can be reused to obtain the image data.
5. Add a Copy button/action to the appropriate photo selection interface.
6. Implement clipboard functionality that copies the actual image data rather than an empty file.
7. Determine the appropriate behavior when one or multiple photos are selected.
8. Add or update tests for the Copy functionality where appropriate.
9. Repeat the reproduction steps and verify that the image can be pasted successfully into another application.

**Implement:**

Implementation will be completed during Phase III.

**Review:**

I will review the changes against LibrePhotos' contribution guidelines and existing patterns for photo actions before creating a pull request.

**Evaluate:**

I will verify that the Copy action places usable image data on the clipboard and that the original 0-byte `.webp` behavior no longer occurs. I will also run the relevant tests and repeat the manual reproduction steps.
