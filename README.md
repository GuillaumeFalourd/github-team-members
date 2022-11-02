# Github Team Members

[![Security Pipeline](https://github.com/GuillaumeFalourd/github-team-members/actions/workflows/security-pipeline.yml/badge.svg)](https://github.com/GuillaumeFalourd/github-team-members/actions/workflows/security-pipeline.yml) [![Super Linter](https://github.com/GuillaumeFalourd/github-team-members/actions/workflows/super-linter.yml/badge.svg)](https://github.com/GuillaumeFalourd/github-team-members/actions/workflows/super-linter.yml) [![Gitleaks](https://github.com/GuillaumeFalourd/github-team-members/actions/workflows/gitleaks.yml/badge.svg)](https://github.com/GuillaumeFalourd/github-team-members/actions/workflows/gitleaks.yml)

☞ Github Actions to get a GitHub Team Members list :octocat:

_Observation: This action can also be used to check if the workflow `${{ github.actor }}` belongs to the specified team._

## 📚 Usage

### ⚠️ Requirements

This action needs a GitHub token with the `read:org` permission to read organizational team members.

### Fetch all members from Team Slug

```yaml
- id: get-members
  uses: GuillaumeFalourd/github-team-members@v1
  with:
    org_slug: org-slug
    team_slug: team-slug
    token: ${{ secrets.GITHUB_TOKEN }}

- run: "echo ${{ steps.get-members.outputs.members }}"
  shell: bash
```

### Fetch maintainers from Team Slug

```yaml
- id: get-members
  uses: GuillaumeFalourd/github-team-members@v1
  with:
    org_slug: org-slug
    team_slug: team-slug
    role: maintainer
    token: ${{ secrets.GITHUB_TOKEN }}

- run: "echo ${{ steps.get-members.outputs.members }}"
  shell: bash
```

### Check if github.actor belongs to Team Slug

```yaml
- id: get-members
  uses: GuillaumeFalourd/github-team-members@v1
  with:
    org_slug: org-slug
    team_slug: team-slug
    token: ${{ secrets.GITHUB_TOKEN }}

- if: steps.get-members.outputs.actor-belongs-team == 'true'
  run: echo "${{ github.actor }} belongs to Team"
  shell: bash
```

## ▶️ Action Inputs

Field | Mandatory | Default Value | Observation
------------ | ------------  | ------------- | -------------
**org_slug** | NO | - | Organization's name <br/> _e.g: `my-org`_
**team_slug** | NO | - | Team's Slug <br/> _e.g: `my-team`_
**role** | NO | `all` | Members Role <br/> _e.g: `member`, `maintainer` or `all`_
**token** | NO | `${{ github.token }}` | Branch to push the changes back

## ▶️ Action Outputs

Field | Observation
------------ | ------------ 
**data** | Raw member data from GitHub API
**members** | Team members list
**actor-belongs-team** | If the workflow `${{ github.actor }}` belongs to the team. <br/> _e.g: `true` or `false`_

## 🤝 Contributing

☞ If you're interested in contributing to this repository, please follow the [guidelines](https://github.com/GuillaumeFalourd/github-team-members/blob/main/CONTRIBUTING.md)

## 🏅 Licensed

☞ This repository uses the [Apache License 2.0](https://github.com/GuillaumeFalourd/github-team-members/blob/main/LICENSE)

<!-- ### Contribuidores

<a href="https://github.com/GuillaumeFalourd/github-team-members/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=GuillaumeFalourd/github-team-members" />
</a>

(Criado com [contributors-img](https://contrib.rocks)) -->
