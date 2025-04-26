milestone-setter
---

The Milestone Setter is a GitHub Actions workflow designed to automate the creation and assignment of milestones to pull requests based on branch names. This tool helps streamline project management by ensuring that milestones are consistently applied, making it easier to track progress and manage releases.

---

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Getting Started](#getting-started)
- [Usage](#usage)
- [License](#license)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Getting Started
---
To use this workflow, include the `the9ball/milestone-setter/.github/workflows/milestone-setter.yaml@v0.1.0` workflow in your repository.

```yaml
on:
  pull_request:
    types:
      - opened
      - reopened
      - edited # for base branch change

jobs:
  call:
    uses: the9ball/milestone-setter/.github/workflows/milestone-setter.yaml@v0.1.1
    permissions:
      contents: write # for creating milestone
      pull-requests: write
    with:
      branch_name_filter: "(feature|release)/.*"
```

Usage
---

```yaml
on:
  pull_request:
    types:
      - opened
      - reopened
      - edited # for base branch change

jobs:
  call:
    uses: the9ball/milestone-setter/.github/workflows/milestone-setter.yaml@v0.1.1
    permissions:
      contents: write # for creating milestone
      pull-requests: write
    with:
      # Regular expression representing the branch name.
      # Compliant with Bash syntax.
      branch_name_filter: "(feature|release)/.*"

      # GitHub token.
      # Basically, no need to specify.
      # Defaults to ${{ github.token }} if not provided.
      token: ''

      # Target repository
      # Basically, no need to specify.
      # Defaults to ${{ github.repository }} if not provided.
      repository: ''

      # Specify the prefix/suffix of the milestone to be created.
      milestone_prefix: ''
      milestone_suffix: ''
```

License
---
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
