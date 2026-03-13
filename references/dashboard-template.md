# Dashboard HTML Template Spec

Generate a single `dashboard.html` file. Self-contained — all CSS inline in `<style>`, no external dependencies.

## Style

- Font: `system-ui, -apple-system, sans-serif`
- Background: `#ffffff`
- Text: `#1a1a1a`
- Borders: `#e5e5e5`
- Accent (deadlines within 7 days): `#dc2626`
- Accent (general links): `#2563eb`
- Max width: `720px`, centered
- Spacing: generous padding (`1.5rem`+), keep it airy
- No rounded corners larger than `6px`, no shadows, no gradients

## Structure

One page, scroll top to bottom. Sections in this order:

```html
<header>
  <h1>NTU {semester} Dashboard</h1>
  <p>Last updated: {YYYY-MM-DD}</p>
</header>

<section id="schedule">
  <h2>Schedule</h2>
  <!-- Weekly timetable as <table> -->
  <!-- Columns: Mon-Fri, Rows: time slots -->
  <!-- Empty cells stay empty, no filler -->
</section>

<section id="deadlines">
  <h2>Upcoming Deadlines</h2>
  <!-- Simple <table> sorted by date -->
  <!-- Columns: Date, Course, Assignment -->
  <!-- Rows within 7 days get class="urgent" (red text) -->
  <!-- Today's deadlines get "TODAY" badge -->
</section>

<section id="courses">
  <h2>Courses</h2>
  <!-- One <article> per course -->
  <article>
    <h3>{course_name} <small><a href="{cool_url}">COOL</a></small></h3>

    <h4>Announcements</h4>
    <ul>
      <li><strong>{title}</strong> <time>{date}</time><br>{summary}</li>
    </ul>

    <h4>Assignments</h4>
    <ul>
      <li><a href="{url}">{name}</a> — due {date}</li>
    </ul>

    <h4>Materials</h4>
    <ul>
      <li><a href="{url}">{filename}</a></li>
    </ul>
  </article>
</section>
```

## Rules

- Keep it simple. No JavaScript unless absolutely needed.
- No dark mode toggle, no animations, no hamburger menus.
- All links open in new tab (`target="_blank"`).
- Dates always `YYYY-MM-DD`.
- If a section has no data, omit it entirely.
- Table cells: left-aligned, no zebra stripes.
- Mobile friendly: table uses `overflow-x: auto` wrapper.
- Print friendly: looks fine when printed as-is.
