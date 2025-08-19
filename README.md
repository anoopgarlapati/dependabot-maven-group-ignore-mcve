# Minimal Maven Tomcat MCVE

This is a minimal Maven project to reproduce a Dependabot ignore rule issue with grouped Tomcat dependencies.

## How to use

- Run `mvn compile` to check the build.

## Steps to Reproduce the Dependabot Ignore Rule Issue

1. Confirm that your `.github/dependabot.yml` file contains:

		```yaml
		version: 2
		updates:
			- package-ecosystem: "maven"
				directory: "/"
				ignore:
					- dependency-name: "*"
						update-types: ["version-update:semver-major"]
		```

2. Push this repository to GitHub.
3. In your GitHub repository, open the "Dependabot" tab.
4. Click **Check for updates** to trigger Dependabot manually.
5. Observe if Dependabot creates a PR to update Tomcat dependencies from 10.x to 11.x, even though the ignore rule should prevent this.

If a PR is created for these major updates, the issue is reproduced and can be shared with the GitHub team for investigation.
