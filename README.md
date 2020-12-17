# Buildpack for building and deploying the portal on Heroku.

Given that the Portal is currently hosted by the [Ditto-web monorepo](https://github.com/getditto/ditto-web) and that it has it's own set of very specific constraints, we were not able to use any of the community buildpacks to build and deploy the portal, and had to provide this buildpack instead for this.

The buildpack is mainly based on the [Rust Heroku buildpack](https://github.com/emk/heroku-buildpack-rust), on which small adjustments have been made to build the portal.

The main adjustments done on the original buildpack are:

- Language detection no longer relies on a Rust project existing at the project root. Instead we check that the Rust project is found inside `portal_server`.
- Other than compiling the Rust project, we also make sure to copy the necessary static assets to the target directory for the binary execution to work. These static assets are basically: the `www` folder and the `organizations.json` file.
