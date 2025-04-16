### Description:

The project currently has numerous outdated dependencies, leading to vulnerability warnings and increased complexity.

```
373 packages are looking for funding
  run `npm fund` for details

28 vulnerabilities (11 low, 11 moderate, 4 high, 2 critical)

To address issues that do not require attention, run:
  npm audit fix

To address all issues possible (including breaking changes), run:
  npm audit fix --force

Some issues need review, and may require choosing
a different dependency.

Run `npm audit` for details.
```

The goal of this ticket is to update all dependencies to their latest versions and remove any that are unused. **This must be done one by one, not all at once**, to avoid breaking the app.

Use the [`react-router-saas-template`](https://github.com/janhesters/react-router-saas-template) as a reference for inspiration on updating dependencies (request access from Jan if it’s not open source).

The process should be methodical: update testing dependencies first (e.g., `Vitest`, `Playwright`, `React Testing Library`), then linting (ESLint & Prettier), then styling libraries like `Shadcn` (adopting its new look), then other dependencies like Prisma/CLI, and so on. For each dependency, review its necessity, uninstall if unused, and verify the app still works. The end result should be **a project with no vulnerability warnings, updated stylings, and reduced complexity**.

### Tasks:

1. **Prepare and Reference Template:**

   - Check out the `react-router-saas-template` for guidance on dependency updates and how to configure them.
   - If not open source, request access from Jan via `#social-kit-engineering`.

2. **Update Testing Dependencies:**

   - Create a feature branch (e.g., `update-testing-deps`).
   - Update `Vitest`, `Playwright`, and `React Testing Library` to their latest versions.
   - Refer to `react-router-saas-template` for `Vitest` configuration.
   - Run the full test suite and `npm audit` to verify no issues.
   - Create a PR.

3. **Update Shadcn (Styling Library):**

   - Create a feature branch (e.g., `update-shadcn`).
   - Bump all `Shadcn` packages to the latest version.
   - Reinstall packages and update stylings to adopt the new look (e.g., better dark mode inputs).
   - Test styling across the app; ensure no breaks occur.
   - Notify the design-team in `#social-kit-product` about styling changes.
   - Create a PR.

4. **Review and Remove Unused Dependencies:**

   - For each dependency in `package.json`, evaluate if it’s used or needed.
   - If unused, uninstall it, run tests, and confirm the app still works.
   - Document removals in the PR description.
   - Create a PR.

5. **Update Remaining Dependencies:**

   - Batch other dependencies like the examples above.
   - Create feature branches for other dependency updates (e.g., `prisma-dependency-updates`, `aws-sdk-dependency-updates` etc.).
   - Bump each to its latest version, one at a time.
   - Run tests and `npm audit` after each update.
   - Create a PR for each other batch.

6. **Finalize and Document:**
   - Ensure no vulnerability warnings remain (`npm audit` clean).
   - Update `README.md` with the new dependency versions and update process.
   - When each PR is merged, ensure that production still works and nothing was broken.

### Acceptance Criteria:

- [ ] All dependencies are updated to their latest versions.
- [ ] No vulnerability warnings appear in `npm audit`.
- [ ] The app adopts the new `Shadcn` styling (e.g., improved dark mode inputs) where green-lit by design team.
- [ ] Unused dependencies are removed.
- [ ] The app still functions (and all tests pass).
- [ ] Updates are done incrementally, with one PR per dependency group.
- [ ] Project documentation reflects any changes (updated `README.md` if necessary).

**Tip:** We also have [this draft article](https://janhesters.com/blog/how-to-set-up-react-router-v7-for-production-in-2025) that can help you with some of the setups of the tools (e.g. linting, testing).
