name: Generate Snake

on:
  schedule:
    - cron: "0 */12 * * *"   # co 12h
  workflow_dispatch:          # ręczne odpalenie z zakładki Actions
  push:
    branches: [main]

jobs:
  generate:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - name: Generate snake
        uses: Platane/snk@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/snake.svg
            dist/snake-dark.svg?palette=github-dark
            dist/snake-pink.svg?color_snake=%23ff2e88&color_dots=%232a2a35,%233d1f3a,%237a2f5f,%23c73e8a,%23ff2e88

      - name: Push to output branch
        uses: crazy-max/ghaction-github-pages@v4
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
