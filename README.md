# NPM Version Match

This GitHub Action ensures that the version tag used to trigger workflows matches the version specified in the project's `package.json` file. It's designed to prevent mismatches between git tags and package versions, which can lead to confusion or errors in package publishing processes.

- [NPM Version Match](#npm-version-match)
  - [Features](#features)
  - [Prerequisites](#prerequisites)
  - [Usage](#usage)
  - [Contributing](#contributing)
  - [License](#license)

## Features

- Validates that the git tag version aligns with the version in `package.json`.
- Prevents workflow continuation if a mismatch is detected, ensuring consistency.

## Prerequisites

- Your workflow must have `actions/checkout` and `actions/setup-node` steps before using this action to access the repository code and use Node.js for reading `package.json`.

## Usage

Add the following steps to your GitHub Actions workflow to use the Check Version Match Action:

```yaml
jobs:
  publish:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '20.x'
      - name: Check version match
        uses: nick-y-ito/gha-npm-version-match@v1
      - name: Publish to NPM
        run: npm publish --access public
        env:
          NODE_AUTH_TOKEN: ${{ secrets.NPM_TOKEN }}
```

## Contributing

Contributions are welcome! Please feel free to submit a pull request.

## License

This project is licensed under the GNU Affero General Public License (AGPL). See the [LICENSE](https://github.com/nick-y-ito/gha-npm-version-match/blob/main/LICENSE) file for details.
