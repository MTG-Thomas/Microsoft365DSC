# Microsoft365DSC

This fork manages Microsoft 365 tenant configuration through PowerShell DSC. Resources and shared modules live in `Modules/Microsoft365DSC/`; `ResourceGenerator/` and `generator/` generate resources; `Tests/` contains the validation harness. Read [.github/copilot-instructions.md](.github/copilot-instructions.md), [contributing guidance](.github/CONTRIBUTING.md), and the workload examples before editing a resource.

The current default branch is `Dev` (capital D). Start feature branches from the exact current default ref; do not modify or directly commit to `master`. Existing prose says `dev`; resolve case against Git refs rather than creating a second branch.

Track the task with the available planning surface, make focused changes, reconsider the diff, and present changes to the user before marking work completed. The old guide names `manage_todo_list`; availability of that particular tool is not a prerequisite. Keep credentials out of commits; document placeholders and required manual setup.

## Verification

Use Windows and the dependency/setup sequence in [.github/workflows/Unit Tests.yml](.github/workflows/Unit%20Tests.yml). From repository root, import `./Tests/TestHarness.psm1` with `Import-Module ./Tests/TestHarness.psm1 -Force`; run `Invoke-QualityChecksHarness` and `Invoke-TestHarness -IgnoreCodeCoverage`. Check returned failure counts; successful invocation alone does not prove success.

Resource names follow `<Workload><Resource>`, with `MSFT_` prefixes and `.schema.mof` schemas. Update the corresponding tests under `Tests/Unit/Microsoft365DSC/` and resource examples with behavior changes.

Tenant-facing full-circle/integration workflows can change remote configuration. Do not treat them as local unit checks or run them without the exact authorized tenant scope. Publishing to PowerShell Gallery is a release operation, separate from a validated source change.
