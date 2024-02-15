# Milestone-Automation
Automatically adds a Milestone to a pull requests or issue, based on the name/pattern of the Milestone.

# Usage
Example `milestones.yml` (no regex)
```yml
name: Milestone Automation

on:
  pull_request:
    types:
      - opened
  issues:
    types:
      - opened

jobs:
  run:
    name: Add Milestone
    runs-on: ubuntu-latest
    steps:
      - uses: Julexar/Milestone-Automation@1.0
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
          milestone: "Milestone Name"
```

Example `milestones.yml` (with regex)
```yml
name: Milestone Automation

on:
  pull_request:
    types:
      - opened
  issues:
    types:
      - opened

jobs:
  run:
    name: Add Milestone
    runs-on: ubuntu-latest
    steps:
      - uses: Julexar/Milestone-Automation@1.0
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
          milestone: "/^v\d+\.\d+$/"
          regex: 'true'
```

# Inputs

| Name          | Description                                                              | Required | Default |
| ------------- | ------------------------------------------------------------------------ | -------- | ------- |
| `token`       | GitHub Token. You can get one [here](https://github.com/settings/tokens) | `true`   |         |
| `milestone`   | Name of the Milestone or Regular Expression                              | `true`   |         |
| `regex`       | Tigger pattern matching using Regular Expression                         | `false`  | `false` |
