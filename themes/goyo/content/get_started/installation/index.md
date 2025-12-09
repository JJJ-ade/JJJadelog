+++
title = "Installation"
description = "How to install Goyo and get started."
weight = 1
sort_by = "weight"

[extra]
+++

Goyo is a theme for Zola. To use this documentation, you need to install Zola first. You can install it on various operating systems with a simple command like the one below.

```bash
# macOS Example
brew install zola
```

For more details, please refer to the [official installation guide](https://www.getzola.org/documentation/getting-started/installation/) on the Zola website.

Once you have Zola installed, create a new Zola site as follows:

```bash
zola init your-docs
cd docs
```

You can then run the local development server with the `zola serve` command and view your site at `http://localhost:1111`.

## Install the Goyo Theme

The easiest way to install a theme in Zola is to clone it or add it as a submodule into the `themes` subdirectory of your Zola project.

Clone example

```bash
git clone https://github.com/hahwul/goyo themes/goyo
```

Submodule example

```bash
git submodule add https://github.com/hahwul/goyo themes/goyo
```

## Update the Goyo Theme

If you want to update the Goyo theme to the latest version, you can do so easily:

### If you cloned the theme

If you installed Goyo by cloning the repository directly, you can update it with:

```bash
cd themes/goyo
git pull origin main
```

This will fetch and merge the latest changes from the main branch.

### If you added the theme as a submodule

If you installed Goyo as a git submodule, update it with:

```bash
git submodule update --remote themes/goyo
```

Or for a more comprehensive update of all submodules:

```bash
git submodule sync
git submodule update --remote
```

After updating the submodule, commit the changes to your repository:

```bash
git add themes/goyo
git commit -m "Update Goyo theme to latest version"
git push
```

This will ensure you always have the latest features and fixes from the Goyo theme.

### Automated Updates with GitHub Actions

For projects hosted on GitHub, you can automate theme updates using GitHub Actions. This will create periodic pull requests whenever a new version of Goyo is available.

Create a file at `.github/workflows/update-goyo-theme.yml` in your documentation repository:

```yaml
name: Update Goyo Theme

on:
  schedule:
    # Run every Monday at 9:00 AM UTC
    - cron: "0 9 * * 1"
  workflow_dispatch: # Allow manual trigger

env:
  GIT_USER_NAME: "github-actions[bot]"
  GIT_USER_EMAIL: "github-actions[bot]@users.noreply.github.com"
  THEME_PATH: "themes/goyo"

jobs:
  update-theme:
    runs-on: ubuntu-latest
    permissions:
      contents: write
      pull-requests: write

    steps:
      - name: Checkout repository
        uses: actions/checkout@v4
        with:
          submodules: true
          token: ${{ secrets.GITHUB_TOKEN }}

      - name: Update Goyo submodule
        id: update
        run: |
          git config user.name "${{ env.GIT_USER_NAME }}"
          git config user.email "${{ env.GIT_USER_EMAIL }}"

          # Get current commit hash
          OLD_COMMIT=$(git rev-parse HEAD:${{ env.THEME_PATH }})

          # Update submodule to latest
          git submodule update --remote ${{ env.THEME_PATH }}
          git add ${{ env.THEME_PATH }}

          # Get new commit hash
          NEW_COMMIT=$(git --git-dir=${{ env.THEME_PATH }}/.git rev-parse HEAD)

          # Check if there are changes
          if [ "$OLD_COMMIT" != "$NEW_COMMIT" ]; then
            echo "updated=true" >> $GITHUB_OUTPUT
            echo "old_commit=$OLD_COMMIT" >> $GITHUB_OUTPUT
            echo "new_commit=$NEW_COMMIT" >> $GITHUB_OUTPUT
          else
            echo "updated=false" >> $GITHUB_OUTPUT
          fi

      - name: Create Pull Request
        if: steps.update.outputs.updated == 'true'
        uses: peter-evans/create-pull-request@v6
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
          commit-message: "Update Goyo theme to latest version"
          title: "Update Goyo theme"
          body: |
            This PR updates the Goyo theme to the latest version.

            **Changes:** ${{ steps.update.outputs.old_commit }} → ${{ steps.update.outputs.new_commit }}

            Please review the [Goyo changelog](https://github.com/hahwul/goyo/releases) for details on what's new.

            ---
            *This PR was automatically created by the Update Goyo Theme workflow.*
          branch: update-goyo-theme
          delete-branch: true
          labels: dependencies, documentation
```

The workflow can be customized:
- **Schedule**: Modify the `cron` expression (e.g., `'0 9 * * *'` for daily, `'0 9 1 * *'` for monthly)
- **Manual trigger**: Use the Actions tab in your repository to run it manually
- **Git User**: Change `GIT_USER_NAME` and `GIT_USER_EMAIL` in the `env` section to use your own account
- **Theme Path**: Modify `THEME_PATH` if your theme is installed in a different location
- Ensure your repository settings allow Actions to create pull requests (Settings → Actions → General → Workflow permissions)

## Set the theme in config.toml

This is the final step. Set the theme in your `config.toml` file to use Goyo.

```toml
title = "Your App"
theme = "goyo"
```

Now, when you run Zola, it will use the Goyo theme.

```bash
zola serve
```

However, since you don't have any content yet, you will only see a blank page with a brilliant color. In the next document, we'll create our first page.
