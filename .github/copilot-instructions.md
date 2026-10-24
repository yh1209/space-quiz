# Space Quiz - Copilot Instructions

## Project Overview

A single-file, no-dependency interactive quiz application featuring 10 Korean-language space exploration questions. The app includes a progress bar, real-time score tracking, animated feedback (green success, red shake on error), and a personalized results screen with emoji reactions. Designed for accessibility with keyboard navigation support and responsive dark/light theme via `prefers-color-scheme`.

## Architecture

The application is a **standalone HTML file** (`index.html`) with embedded CSS and JavaScript. No build process, server, or external dependencies are required.

### Structure
- **HTML**: Semantic markup with language set to Korean (`lang="ko"`)
- **CSS**: CSS Variables for theming, responsive flexbox layout, 500px max-width centered column
- **JavaScript**: Single-file quiz engine with question data, state management, and DOM manipulation

### Key Design Patterns

1. **Quiz State Machine**: Four primary states via `currentQuestion`, `correctCount`, `incorrectCount`, and `answered` flags
   - Initial state → Question display → Answer selection → Feedback → Next question → Results
   
2. **Theme System**: CSS custom properties with `prefers-color-scheme` media query for automatic light/dark mode
   - Light mode: `--bg: #ffffff`, `--text: #1f2937`
   - Dark mode: `--bg: #111827`, `--text: #f3f4f6`

3. **Animation Strategy**: 
   - Entry animations: `.slideIn` (opacity + transform)
   - Feedback animations: `.pulse` (correct) and `.shake` (incorrect)
   - Selected state: `::before` scanline effect, `::after` "LOCKED" indicator with pulsing text

4. **Accessibility First**:
   - All option elements have `tabindex="0"` for keyboard navigation
   - Enter key triggers answer selection via `onkeypress`
   - Semantic HTML5 elements
   - Clear visual feedback for all interactions

## Question Data Format

Questions are stored in a JavaScript array with this structure:

```javascript
{
  question: "String in Korean",
  options: ["Option 1", "Option 2", "Option 3", "Option 4"],
  correct: 0  // Index of correct answer (0-3)
}
```

Currently 10 questions; add more by extending the array. Indices are 0-based.

## Scoring & Feedback

- **Real-time tracking**: Updated after each answer via `updateProgress()`
- **Correct feedback**: "✓ **정답입니다!**" (green background, `feedback.correct` class)
- **Incorrect feedback**: "**❌ 틀렸어요**\n정답: [correct option]" (red background, `feedback.incorrect` class)
- **Results emoji logic**: Scores ≥90% = 🌟, ≥80% = 🚀, ≥70% = 👍, ≥60% = 🤔, else = 😢
- **Score calculation**: `(correctCount / 10) * 100` for percentage display

## Common Tasks

### Adding Questions
1. Locate the `questions` array in the `<script>` section
2. Push a new object with `question`, `options` (4 strings), and `correct` (0-3 index)
3. No restart needed; reload the page to test

### Styling Changes
- Modify CSS variables in `:root` for light mode or `@media (prefers-color-scheme: dark)` for dark mode
- Update class selectors (e.g., `.option`, `.feedback`) to change component appearance
- Animations are defined as `@keyframes` blocks; adjust `duration` or `transform` values to customize feel

### Language Adjustments
- All user-facing text is embedded in the HTML/JS; replace Korean text for other languages
- Update `lang="ko"` attribute in the `<html>` tag if changing language

### Testing
No build or test commands. Manually verify:
1. Open `index.html` in a browser
2. Test correct/incorrect answers on each question
3. Verify score updates and progress bar animation
4. Confirm results screen appears with correct emoji and message
5. Test keyboard navigation (Tab to focus, Enter to select)
6. Toggle system dark mode to verify theme switching

## Performance Notes

- **No external dependencies**: Entire app loads instantly
- **No minification**: Easy to read and modify
- **DOM updates**: Uses `innerHTML` for question rendering; acceptable for a 10-question app
- **Animations**: CSS-based for smooth 60fps performance; JavaScript event handlers are minimal

## Browser Compatibility

Tested and compatible with:
- Modern browsers (Chrome, Firefox, Safari, Edge)
- Mobile browsers with viewport meta tag
- Dark mode detection via `prefers-color-scheme` (supported in all modern browsers)

## Future Enhancement Ideas

- Add difficulty levels (Easy/Medium/Hard) by filtering questions
- Persist scores to localStorage for session tracking
- Add a timer per question
- Shuffle question order or answer options
- Export results as JSON
- Expand question set beyond 10
