# repository2
Practice 
name: Update Templates

on:
  workflow_dispatch:


jobs:
  build:
runs-on: ubuntu-latest
timeout-minutes: 15

steps:
- uses: actions/checkout@v3
  
- name: Sync Templates
run: |
  git submodule update --init
  cd gitignore
  git pull origin master
- name: Create Pull Request
uses: peter-evans/create-pull-request@v4
with:
  token: ${{ secrets.GITHUB_TOKEN }}
  commit-message: Sync Templates Submodule
  title: Sync Templates Submodule
  branch: sync_templates
  base: master
