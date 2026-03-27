# Fortify 3rd-party action wrapper generator

This repo contains a generator workflow that reads the organization's allowed actions list and generates composite wrapper actions under `actions/<owner>-<repo>/v<major>/action.yml`. GitHub Action workflows within the github.com/fortify organization should not use 3rd-party actions directly, but instead use the wrapper actions provided in this repository.

Quick usage instructions:
- All allowed actions should be listed under `Allow or block specified actions and reusable workflows` at https://github.com/organizations/fortify/settings/actions
- Ideally, allowed action versions should be specified by SHA, not version tags/branches
- Whenever the list of allowed actions is updated, the `Generate third-party composite actions` workflow in this repository must be triggered
- The workflow will output warnings for outdated SHA references
- The workflow will output warnings for non-SHA action references, including the corresponding SHA, allowing for easily updating the allow list to use the appropriate SHA