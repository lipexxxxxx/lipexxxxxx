<h6 align="center">Hi there, I'm felipe <br><br>I am an aspiring software developer at the beginning of my programming journey. I am passionate about technology and constantly looking for new challenges to build my skills. Currently, I am focusing on mastering the fundamentals of coding and exploring modern tech stacks.</h6>

###

<div align="center">
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" height="60" alt="python logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vscode/vscode-original.svg" height="60" alt="vscode logo"  />
</div>

###

<div align="center">
  <a href="https://www.instagram.com/eulipeflyx?igsh=ZXNmaWJhcGtvY3Vu&utm_source=qr" target="_blank">
    <img src="https://img.shields.io/static/v1?message=Instagram&logo=instagram&label=&color=E4405F&logoColor=white&labelColor=&style=for-the-badge" height="25" alt="instagram logo"  />
  </a>
  <a href="44988274090" target="_blank">
    <img src="https://img.shields.io/static/v1?message=Whatsapp&logo=whatsapp&label=&color=25D366&logoColor=white&labelColor=&style=for-the-badge" height="25" alt="whatsapp logo"  />
  </a>
  <a href="www.youtube.com/@Respawnbrr" target="_blank">
    <img src="https://img.shields.io/static/v1?message=Youtube&logo=youtube&label=&color=FF0000&logoColor=white&labelColor=&style=for-the-badge" height="25" alt="youtube logo"  />
  </a>
</div>

###

<img src="https://raw.githubusercontent.com/lipexxxxxx/lipexxxxxx/snake-output/snake.svg" alt="Snake animation" />

###
name: Generate snake animation

on:
  schedule: # execute every 12 hours
    - cron: "* */12 * * *"

  workflow_dispatch:

  push:
    branches:
    - main

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5

    steps:
      - name: generate snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: dist/snake.svg?palette=github-dark


      - name: push snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: snake-output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
