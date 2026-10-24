# Project Pulse implementation plan

## Goal

Build a lightweight, polished static dashboard that helps Mona's contributors see
which projects are active, who owns them, their current status, recent activity,
and priority. The dashboard must launch in a browser on its frontend rather than
showing a directory listing.

## File assignments

| File | Assignment |
| --- | --- |
| `app/project-data.json` | Coder: provide a top-level `projects` array; each project has `name`, `owner`, `status`, `recentActivity`, and `priority`. |
| `app/index.html` | Coder: create the accessible page structure, load the stylesheet and project data, and render visible cards using the `project-card` class. |
| `app/styles.css` | Designer: define the responsive visual system, hierarchy, card layout, badges, and accessible contrast. Coder integrates styling hooks with the page structure. |
| `.vscode/launch.json` | Coder: configure the named dashboard launch and browser URL after confirming the app directory and page path. |

## Responsibilities

- **Planner:** confirm requirements, assign file ownership, identify dependencies
  and risks, and define validation expectations.
- **Designer:** shape information hierarchy, responsive behavior, accessible
  presentation, and polished card and status/priority treatments. Own
  `app/styles.css` and coordinate the required class hooks with the Coder.
- **Coder:** implement `app/index.html`, `app/project-data.json`, and
  `.vscode/launch.json`; integrate the Designer's CSS hooks; handle loading
  errors visibly; and validate the integrated app.
- **Orchestrator:** coordinate phases and file scopes, resolve integration
  issues, and verify the final result against this plan.

## Phases and dependencies

1. **Agree on the interface.** Confirm project fields, card markup hooks, status
   and priority categories, and the app's `app/` directory layout. This is a
   prerequisite for parallel implementation.
2. **Create content and presentation.** The Coder can prepare
   `app/project-data.json` while the Designer develops `app/styles.css` against
   the agreed class hooks. The Coder builds `app/index.html` to load the data,
   render project cards, and connect the stylesheet. The data contract and
   markup hooks must remain consistent.
3. **Integrate and launch.** After the page and app directory are established,
   the Coder creates `.vscode/launch.json` to serve from `app/` and open
   `index.html`. The Orchestrator checks the integrated UI and launch behavior.
4. **Validate and hand off.** Run the checks below, resolve failures, and
   document the result.

## Parallel work decisions

- Once the data shape and markup hooks are agreed, the Designer can work on
  `app/styles.css` in parallel with the Coder's project data and HTML.
- HTML and CSS integration depends on shared class names and structure; the
  Designer and Coder must coordinate those before finalizing either file.
- `.vscode/launch.json` can be drafted independently, but final validation must
  wait until the app path and `index.html` are present.
- Final integrated validation is sequential and follows all implementation.

## Validation expectations

- `app/project-data.json` parses as JSON, has a top-level `projects` array, and
  every project contains `name`, `owner`, `status`, `recentActivity`, and
  `priority`.
- `app/index.html` has the exact title `Project Pulse`, references
  `styles.css` and `project-data.json`, and renders visible project cards with
  the `project-card` class and each required project field.
- `app/styles.css` contains `.dashboard` and `.project-card`, uses
  `border-radius` and `box-shadow`, and adapts to narrower screens with readable
  contrast.
- `.vscode/launch.json` parses as strict JSON and defines `Run Project Pulse
  Dashboard`; it serves from `app/` using `python3 -m http.server 5500` and opens
  `http://localhost:%s/index.html`.
- Preview the launch configuration and confirm the Project Pulse frontend
  appears instead of a directory listing. Confirm project data loads and
  loading errors are communicated clearly.
