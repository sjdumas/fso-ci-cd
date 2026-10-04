# Full Stack Open CI/CD

This repository is used for the CI/CD module [part 11](https://courses.mooc.fi/org/uh-cs/courses/full-stack-open-continuous-integration) of the Full Stack Open course.

## Commands

Start by running `npm install` inside the project folder.

- `npm start` to run the webpack dev server
- `npm test` to run tests
- `npm run eslint` to run ESLint
- `npm run build` to make a production build
- `npm run start-prod` to run your production build

## Live Project Link

You can view the project live at [https://fso-pokedex-iod5.onrender.com/](https://fso-pokedex-iod5.onrender.com/).

## Pipeline

The pipeline is defined in `.github/workflows/pipeline.yml`.

- **Pull requests to `main`:** linting, unit tests, the build, and end-to-end tests run in separate jobs. Nothing is deployed.
- **Pushes to `main`** (merged pull requests): once the checks pass, the app is deployed to Render through a deploy hook, and a patch version tag is created.
- **`#skip`:** a commit message containing `#skip` skips the deploy and the tagging.
- **Branch protection:** `main` is protected by a ruleset, so the required checks must pass before a pull request can be merged.
- **Notifications:** Discord messages report failed builds (with commit and run links) and successful deployments.
- **Health check:** `.github/workflows/health_check.yml` pings the live app once a day.

The workflows use two repository secrets: `RENDER_DEPLOY_HOOK` and `DISCORD_WEBHOOK`.

## Exercise 21 (own pipeline)

Exercise 21 is in a separate repository, which builds a similar CI/CD pipeline for my own phonebook application:

- Repository: [https://github.com/sjdumas/fso-phonebook](https://github.com/sjdumas/fso-phonebook)
- Live application: [https://fso-phonebook-ci-cd.onrender.com/](https://fso-phonebook-ci-cd.onrender.com/)
