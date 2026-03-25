# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm run dev      # Start dev server at http://localhost:5173
npm run build    # Production build
npm run lint     # Run ESLint
npm run preview  # Preview production build
```

## Architecture

This is a React + Vite single-page app with no routing, no state management library, and no backend — all state lives in `src/App.jsx`.

**`src/App.jsx`** is the entire application: one monolithic component holding all state (`transactions`, form fields, filter state), derived values (totals, balance, filtered list), and the full JSX for the summary cards, add-transaction form, and transactions table.

**Known intentional issues (course material):**
- Bug: `amount` is stored as a string, so `.reduce((sum, t) => sum + t.amount, 0)` concatenates instead of summing — totals are wrong.
- Transaction item "Freelance Work" is marked `type: "expense"` but categorized as `"salary"` (data inconsistency).
- UI and code organization are intentionally rough — refactoring into components is part of the course exercises.
