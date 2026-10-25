# Forma — Software Company Website

A responsive software company website built with HTML and CSS for the DigitalHub Git & GitHub collaboration exercise.

## Team

| Student | Name | Responsibility | Feature branch |
| --- | --- | --- | --- |
| A | Abdallah Houeidi | Repository owner, header, hero, heading challenges, review of B's PRs | `feature/header-hero` |
| B | Akram Saeed | Services, footer, review of A's PRs, conflict resolution | `feature/services-footer` |

Student B's name follows the author of the existing services/footer commit. Both students must use their own GitHub accounts for their contributions and reviews.

## Run locally

```bash
git clone https://github.com/abdallahhoueidi/software-company.git
cd software-company
```

Open **`index.html` in the project root** in a modern browser, or use VS Code Live Server. There is no `dist` directory, package installation, or build step. To preview a feature before merge:

```bash
git fetch origin
git switch --track origin/feature/header-hero
```

If the branch already exists locally, use `git switch feature/header-hero` and `git pull --ff-only` instead.

## Files and features

- `index.html`: logo/navigation, hero heading and description, contact CTA, services, approach, contact section, and footer.
- `style.css`: responsive layouts, keyboard focus styles, and reduced-motion support.
- `STUDENT_A_WORKFLOW.md`: exact exercise sequence, remaining team handoffs, command explanations, and submission checklist.

Student A's feature retains the existing visual identity, adds a secondary services link, keeps every navigation link available on mobile, improves CTA contrast, and fixes the illustrative code snippet. Student B owns changes to services and footer.

## Git workflow

`feature branch → pull request → teammate review → dev → final pull request → main`

Start every new feature from the latest `dev`:

```bash
git switch dev
git pull --ff-only origin dev
git switch -c feature/your-feature
# Edit and inspect your work.
git add index.html style.css
git commit -m "Describe the completed change"
git push -u origin feature/your-feature
```

Open a PR targeting `dev`. Your teammate reviews and merges it. Do not push feature code directly to `main` or `dev`. Keep feature branches for evaluation. Create the final `dev` → `main` PR only after both features and collaboration challenges are completed.

## Manual verification

- Check widths of 320px, 375px, 768px, and 1440px; the page must not scroll horizontally.
- Tab through the skip link, brand, navigation, and hero actions; focus must remain visible.
- Confirm Services, Our approach, and contact links reach the correct sections.
- Confirm the contact CTA opens the contact section and the email link uses `mailto:`.
- Verify both students' changes together on `dev` before the final merge.

## Demo details

Forma is a sample brand. `hello@forma.example` is a placeholder, not a working company address. Google Fonts are optional; system fonts are used when unavailable. This is a static practice site with no backend or contact form.
