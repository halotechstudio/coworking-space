# Coworking Space Management: Design

Status: white-label product demo by HALO Studio; calls marked **(my call)** are open to change.

## Intent and why

Multi-branch coworking operators run members, managers and the head office through separate tools. This product gives one system for the whole flow: a member finds and books a desk, gets in, pays, and asks for help; a branch manager runs the floor; an admin runs the business across branches. It is white label: any operator's name, colour and branches drop in through `brand.js` (or `?brand=&accent=&branch=` URL parameters for sales previews).

## Market basis

- Typical product types: dedicated desks, hot desks, private cabins, meeting rooms, day passes, virtual office, monthly memberships with 24/7 access.
- Typical amenities: coffee and tea, printing, lockers, outdoor areas, high-speed internet.
- Indian desk pricing commonly sits around ₹5,000–₹11,000 per seat per month. The demo uses sample prices, labelled as sample.

## Goals

1. Show the three apps (customer mobile, manager mobile, admin web) as a working, clickable simulation.
2. Cover the full coworking operation: booking, access, billing, community, support, staffing, and reporting.
3. Look polished enough to present.

## Non-goals

- No real backend, payments, door hardware, or auth. Everything is mock data in the browser.
- No operator's real branding. The default brand is the neutral "Coworking Space".

## Anti-goals

- A demo that looks like a generic template with no coworking-specific flows.
- Screens that look clickable but do nothing.

## Constraints

- Plain HTML/CSS/JS, no build step, opens by double-click.
- Mobile apps render inside a phone frame; admin is a desktop web layout that collapses on narrow screens.
- Presentation tomorrow: must run offline.

## Approaches considered

1. **Three separate HTML files, shared style (chosen).** Each app opens alone; a hub `index.html` links them. Simple to present, each app can be shown fullscreen.
2. Single-page app with role switch. Less code duplication but harder to show side by side and more fragile live.
3. Figma-style static mockups. Fast but not clickable; rejected because the brief asked for a simulation.

**Picked: 1** (my call). Reason: easiest to demo and to explain in a presentation.

## Feature scope (what a coworking space needs managed)

### Customer app (mobile)
- Home: membership status, today's booking, quick actions, community feed.
- Book: pick branch, desk type (hot desk, dedicated desk, cabin, meeting room), date, time slot.
- Access: door QR pass to unlock, guest pass for visitors.
- Wallet: invoices, pay due, auto-renewal, receipts.
- Community: events, announcements, member directory.
- Support: raise request (cleaning, maintenance, IT, F&B), track status.
- Profile: plan details, upgrade or downgrade, company/GST details.

### Manager app (mobile)
- Floor overview: occupancy by zone, live check-ins.
- Check-ins and guest management: approve visitor, print or send guest pass.
- Booking approvals and room schedule.
- Tickets: assign and resolve support requests.
- Members: list, status, add member, pending dues.
- Events: create and track RSVP.
- Shift and cafe stock check.

### Admin app (web)
- Dashboard: revenue, occupancy, churn, open tickets across branches.
- Branches: list, capacity, desks and rooms per branch, pricing per branch.
- Plans and pricing: plan catalogue, add-ons, discounts.
- Members / CRM: member profiles, contracts, lifecycle (lead, trial, active, churned).
- Billing: invoices, payments, overdue, GST, refunds.
- Staff and roles: managers, staff, permissions (**my call**: role-based, 4 roles).
- Inventory: cafe and supplies per branch.
- Reports: occupancy trend, revenue, utilisation by desk type.
- Access and devices: doors, smart locks, access logs (sim only).
- Audit log.

## Data model (mock)

- Branch: id, name, area, capacity, zones.
- Desk/Room: id, branch, type, status (free, booked, occupied, maintenance).
- Member: id, name, company, plan, status, dues.
- Booking: id, member, resource, start, end, status (pending, confirmed, checked-in, done).
- Invoice: id, member, amount, GST, status.
- Ticket: id, member, category, priority, status, assignee.
- Event: id, branch, title, date, capacity, RSVPs.

## What's left to the builder

- Exact visual styling and icons (inline SVG, no external CDN, to stay offline).
- Sample data values.
- Interaction depth: each screen must respond to taps/clicks with a visible state change.

## Next step

Build three HTML files plus an `index.html` hub and a shared `brand.js`. Verify each in the browser. The superpowers:writing-plans step is skipped for this sim (**my call**): the design is small enough to build directly, and the user asked for implementation tomorrow.
