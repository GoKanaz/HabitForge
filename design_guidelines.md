# Personal Habit Tracker - Design Guidelines

## Design Approach
**System-Based Approach**: Drawing inspiration from Linear's clean productivity aesthetic, Notion's card organization, and Material Design's progress visualization patterns. This utility-focused productivity tool prioritizes clarity, quick interactions, and motivational feedback.

## Typography System
- **Primary Font**: Inter or SF Pro (via Google Fonts CDN)
- **Headings**: Font weight 600-700, sizes: text-3xl (page titles), text-xl (section headers), text-lg (card titles)
- **Body Text**: Font weight 400-500, text-base for descriptions, text-sm for metadata
- **Streak Numbers**: Font weight 700, text-4xl for emphasis
- **Motivational Messages**: Font weight 500, text-base, italic for personality

## Layout System
**Spacing Primitives**: Use Tailwind units of 2, 4, 6, and 8 primarily (p-2, gap-4, m-6, py-8)
- **Container**: max-w-7xl with px-4 md:px-6 lg:px-8
- **Card Padding**: p-6
- **Section Spacing**: py-8 between major sections
- **Grid Gaps**: gap-4 for tight grouping, gap-6 for breathing room

## Core Layout Structure

### Dashboard Layout
- **Today's Focus Panel**: Full-width section at top with today's date and quick stats (active habits, completion rate)
- **Habit Grid**: 2-column on mobile (grid-cols-1 sm:grid-cols-2 lg:grid-cols-3) for habit cards
- **Quick Add Button**: Fixed position bottom-right (fixed bottom-8 right-8) with z-index

### Habit Card Anatomy
Each card includes (in order):
1. Habit name (text-lg font-semibold)
2. Frequency indicator (text-sm - "Daily" or "Every Monday, Wednesday")
3. Streak display with fire icon (text-2xl, flame emoji + number + "day streak")
4. Progress bar (h-2 rounded-full, shows week/month progress)
5. Completion percentage (text-sm)
6. Check-in button (full-width, prominent)
7. Last completed timestamp (text-xs, muted)

### Calendar View
- Monthly calendar grid (grid-cols-7)
- Each day cell shows completion dots for multiple habits
- Selected habit highlights its completion days
- Navigation arrows for month switching
- Compact on mobile, spacious on desktop

## Component Library

### Navigation
- Top app bar with logo/title on left
- Tab navigation for "Today", "All Habits", "Calendar", "Stats"
- Clean horizontal tabs with underline indicator
- Sticky positioning (sticky top-0)

### Habit Cards
- Rounded corners (rounded-xl)
- Subtle border treatment
- Hover elevation (slight shadow increase)
- Completed state: checkmark overlay, reduced opacity
- Incomplete state: prominent check-in button

### Progress Indicators
- Linear progress bars: h-2 rounded-full with smooth fill animation
- Circular progress: for weekly completion (size: w-16 h-16)
- Streak flame icons: Use Font Awesome via CDN
- Completion checkmarks: Heroicons check-circle

### Motivational Messages
- Rotating messages in header based on performance:
  - Just starting: "Every journey begins with a single step"
  - 3-day streak: "Momentum is building!"
  - 7-day streak: "One week strong! Keep going"
  - 30-day streak: "Incredible dedication!"
- Display in dedicated banner (p-4 rounded-lg) above habit grid
- Animated entrance when message changes

### Forms & Modals
- **Create Habit Modal**: Center overlay with max-w-md
  - Habit name input (text-base, p-3)
  - Frequency selector (radio buttons for daily/weekly, checkboxes for specific days)
  - Goal setting (optional target streak)
  - Save/Cancel buttons
- **Edit Modal**: Same structure as create
- Input fields: Consistent p-3 padding, rounded-lg borders

### Stats Dashboard
- Large stat cards in grid (grid-cols-1 md:grid-cols-3 gap-6)
  - Total active habits
  - Overall completion rate
  - Longest current streak
- Chart area for completion trends (placeholder for Chart.js integration)
- Best performing habits list (top 5)

### Empty States
- Centered content with illustration placeholder (<!-- ILLUSTRATION: Person setting goals -->)
- "No habits yet" message (text-xl font-semibold)
- Prominent "Create Your First Habit" button
- Helpful onboarding text about habit formation

## Interaction Patterns
- **Quick Check-in**: Single tap/click on habit card or dedicated button
- **Undo Action**: Toast notification with undo button appears after completion (3s duration)
- **Streak Recovery**: Visual indicator if habit was missed yesterday with "Start Again" option
- **Batch Operations**: Multi-select mode for editing/deleting multiple habits

## Data Visualization
- Progress bars use smooth CSS transitions (transition-all duration-300)
- Streak numbers count up with brief animation on update
- Completion calendar uses dot indicators (w-2 h-2 rounded-full) per habit
- Week view shows 7 vertical bars for daily completion

## Responsive Behavior
- Mobile: Single column cards, collapsible calendar, bottom sheet for modals
- Tablet: 2-column grid, side panel for calendar
- Desktop: 3-column grid, all panels visible simultaneously, expanded stats

## Accessibility
- All interactive elements have focus states (ring-2 focus visible)
- Progress bars include aria-valuenow attributes
- Streak information announced to screen readers
- Keyboard navigation: Tab through habits, Space to toggle completion
- High contrast between text and backgrounds throughout

## Icons
Use Heroicons via CDN for:
- check-circle (completions)
- plus (add habit)
- calendar (calendar view)
- chart-bar (statistics)
- cog (settings)
- fire emoji (🔥) for streaks (not icon, actual emoji)