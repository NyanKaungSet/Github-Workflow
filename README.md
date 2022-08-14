# Table of Contents <a id="top"></a>
1. [Introduction](#Introduction)
1. [Snake Animation](#Snake_Animation)
2. [3D Profile Contribution](#3D_Profile_Contribution)

# Introduction <a id="Introduction"></a>
Here I tested cool things for readme profiles.
<hr>


# Snake Animation <a id="Snake_Animation"></a>
<img src="https://raw.githubusercontent.com/NyanKaungSet/Github-Workflow/b2d924b635f0c57f07ec18852ecf97e944af8816/github-contribution-grid-snake.svg">

- Name your main branch as `master` or change the line 14 `master` ro `main`
- Then Create another branch named `output`
- Create `/.github/snake.yml` in main branch
- Paste the following codes in that file

```yml
name: generate snake animation

on:
  # run automatically every 24 hours
  schedule:
    - cron: "0 */24 * * *" 
  
  # allows to manually run the job at any time
  workflow_dispatch:
  
  # run on every push on the master branch
  push:
    branches:
    - master # or main
    
  

jobs:
  generate:
    runs-on: ubuntu-latest
    timeout-minutes: 10
    
    steps:
      # generates a snake game from a github user (<github_user_name>) contributions graph, output a svg animation at <svg_out_path>
      - name: generate github-contribution-grid-snake.svg
        uses: Platane/snk/svg-only@v2
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark

      # push the content of <build_dir> to a branch
      # the content will be available at https://raw.githubusercontent.com/<github_user>/<repository>/<target_branch>/<file> , or as github page
      - name: push github-contribution-grid-snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v2.6.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

- Run the Workflow in action.
- If it is successful, it will create 2 svg, 1 for dark mode another one for light mode.

***Original source : <a href="https://github.com/Platane/snk">Platane</a>***
<hr>

# 3D Profile Contribution <a id="3D_Profile_Contribution">
<img src="profile-3d-contrib/profile-gitblock.svg">

- Create `/.github/profile-3d.yml`
- Paste the following codes in that file

```yml
name: GitHub-Profile-3D-Contrib

on:
  schedule:
    - cron: "0 18 * * *"
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    name: generate-github-profile-3d-contrib
    steps:
      - uses: actions/checkout@v2
      - uses: yoshi389111/github-profile-3d-contrib@0.6.0
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          USERNAME: ${{ github.repository_owner }}
      - name: Commit & Push
        run: |
          git config user.name github-actions
          git config user.email github-actions@github.com
          git add -A .
          git commit -m "generated"
          git push
```

- Run the Workflow in action.
- If it is successful, it will create 10 svg in profile-3d-contributions file.
  
***Original source : <a href="https://github.com/yoshi389111/github-profile-3d-contrib/tree/main">yoshi389111</a>***
<hr>
  
[Back To Top](#top)
  
<h1 align="center">
  <a href="https://git.io/typing-svg">
    <img src="https://readme-typing-svg.herokuapp.com?font=VT323&size=50&color=FFFFFF&background=363636&center=true&vCenter=true&width=800&height=80&lines=Thanks+For+Visiting!">
  </a>
</h1>
