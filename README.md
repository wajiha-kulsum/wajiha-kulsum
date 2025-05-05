# .github/workflows/update.yml
name: Update README
on:
  schedule:
    - cron: '0 0 * * *'
  workflow_dispatch:
jobs:
  update:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: Wajiha-Kulsum/readme-updater@v1
        with:
          GH_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      - run: |
          git config --global user.name 'GitHub Actions'
          git config --global user.email 'actions@github.com'
          git add .
          git commit -m "Update stats"
          git push
