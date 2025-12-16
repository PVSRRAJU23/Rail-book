# Indian Railway Ticket Booking Application - Design Guidelines

## Design Approach
**Reference-Based Approach:** Drawing inspiration from IRCTC (Indian Railway Catering and Tourism Corporation) and BookMyShow's seat selection interface. Focus on clear visual hierarchy, intuitive seat maps, and familiar booking flows that Indian users trust.

## Core Design Principles
1. **Visual Clarity:** Clear sectional demarcation (middle/left/right) with instant seat availability recognition
2. **Familiar Patterns:** Leverage IRCTC's trusted UI patterns while modernizing the experience
3. **Status-Driven Design:** Color-coded seat states that are immediately understandable
4. **Progressive Disclosure:** Show complexity only when needed (search → results → seats → booking)

## Typography
- **Primary Font:** Roboto (clean, highly legible for complex booking information)
- **Secondary Font:** Open Sans (for body text and forms)
- **Hierarchy:**
  - H1: 32px/bold (page titles)
  - H2: 24px/semibold (section headers, train names)
  - H3: 18px/semibold (coach numbers, section labels)
  - Body: 16px/regular (general content)
  - Small: 14px/regular (seat numbers, timestamps)
  - Caption: 12px/regular (helper text, disclaimers)

## Color System (User-Specified)
- **Primary:** #FF5722 (Indian Railway orange - CTAs, active states)
- **Secondary:** #1565C0 (railway blue - headers, navigation)
- **Success/Available:** #4CAF50 (green for available seats)
- **Booked/Disabled:** #9E9E9E (grey for booked seats)
- **Background:** #FAFAFA (light grey page background)
- **Text Primary:** #212121 (dark grey for main content)
- **White:** #FFFFFF (cards, seat boxes)

## Layout System
**Spacing Units:** Base-12px system (Tailwind: 3, 4, 6, 8, 12, 16 units)
- Component padding: 4-6 units (16-24px)
- Section spacing: 8-12 units (32-48px)
- Card gaps: 4 units (16px)

**Container Widths:**
- Max content: 1280px
- Search/booking forms: 800px max
- Seat map: Full container width with responsive scaling

## Component Library

### Navigation Bar
- Railway blue (#1565C0) background, white text
- Logo left, user account/login right
- Sticky on scroll with subtle shadow

### Train Search Interface
- White card with shadow
- Multi-column layout: From/To stations | Date | Class dropdown
- Orange CTA button for search
- Auto-complete dropdowns for station names

### Train Results List
- Card-based layout with train details
- Each card shows: Train number/name, departure/arrival times, duration, available classes
- "View Seats" button in orange
- Availability indicators (green text/icons)

### Seat Selection Map (Critical Component)
**Layout Structure:**
- Three distinct sections clearly labeled: LEFT | MIDDLE | RIGHT
- Visual separator lines between sections
- Coach header showing coach number and class (e.g., "S7 - Sleeper")
- Grid-based seat layout (rows × columns appropriate to train class)

**Seat Representation:**
- Individual seat boxes (40px × 40px minimum on desktop)
- Seat number displayed inside box
- Clear visual states:
  - Available: Green background (#4CAF50), white text
  - Booked: Grey background (#9E9E9E), white text, subtle strikethrough
  - Selected: Orange background (#FF5722), white text, bold border
- Hover state: Slight scale and shadow (available seats only)

**Legend/Key:**
- Color-coded legend below seat map
- Shows Available/Booked/Selected states

### Booking Form
- Card-based design with clear field grouping
- Passenger details section: Name, Age, Gender fields
- Seat assignment display: Auto-populated from selection
- Summary sidebar showing journey details
- Orange "Confirm Booking" button

### Confirmation Page
- Centered card with ticket details
- PNR number prominently displayed
- Train details, passenger info, seat assignments in structured layout
- Download/Print buttons

## Images
- **No Hero Image Required:** This is a utility-focused booking application
- **Icons:** Use Font Awesome via CDN for train, seat, user, calendar icons
- **Train Coach Diagrams:** Simple SVG-based seat grid layouts (not photographic images)

## Mobile Responsiveness
- Stack search fields vertically on mobile
- Seat map: Horizontal scroll with section tabs (Middle/Left/Right)
- Reduce seat box size to 32px on mobile
- Single column forms and results

## Interactions
- **Minimal Animation:** Subtle transitions on hover/click (0.2s ease)
- **Seat Selection:** Immediate visual feedback on click
- **Loading States:** Spinner for search results
- **Validation:** Inline form validation with red error text

## Accessibility
- High contrast ratios for text (WCAG AA minimum)
- Keyboard navigation for seat selection
- ARIA labels for seat status
- Focus indicators on interactive elements