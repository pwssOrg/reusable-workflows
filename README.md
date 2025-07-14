
# Reusable workflows
## SCA Scan Base

This repository contains a reusable GitHub Actions workflow (`sca-scan-base.yml`) designed to perform static code
analysis (SCA) scans on Java projects using Maven and Snyk.

## Usage

To use the `sca-scan-base.yml` workflow in your own repository, follow these steps:

1. **Add the Repository as a Workflow Dependency**

   In your repository, create or update your GitHub Actions workflow file (e.g.,
`.github/workflows/snyk-scan.yml`) to call the reusable workflow from this organization repository.

2. **Example Usage:**

   Here's an example of how you can use the `sca-scan-base.yml` in your own repository:

   ```yaml
   name: SCA Scan

   on:
     push:
       branches:
         - main
     pull_request:
       branches:
         - main

   jobs:
     snyk-scan:
       uses: pwssOrg/reusable-workflows/.github/workflows/sca-scan-base.yml@main
       with:
         working-path: './'  # Adjust to the path of your pom.xml file if needed
         name-of-snyk-step: 'Run Snyk Test'
       secrets:
         SNYK_TOKEN: ${{ secrets.SNYK_TOKEN }}
   ```

3. **Set Up Secrets**

   Make sure you have set up a secret named `SNYK_TOKEN` in the repository's GitHub settings with your Snyk API
token.

4. **Adjust Inputs and Paths as Needed**

   - `working-path`: Specify the path to your Maven project directory containing the `pom.xml` file.
   - `name-of-snyk-step`: Customize this field to give a name to the step that runs the Snyk test.

## Contributing

Currently, `sca-scan-base.yml` is the only reusable workflow in this repository. However, members of the pwss
organization are welcome and encouraged to add new reusable workflow files to this repository!

Feel free to contribute improvements or report issues with this reusable workflow. Pull requests are welcome!

## License

See the [LICENSE](LICENSE) file for details.
