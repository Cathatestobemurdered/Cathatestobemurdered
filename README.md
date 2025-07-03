# Hi there, I'm Alaia! <img src="https://raw.githubusercontent.com/MartinHeinz/MartinHeinz/master/wave.gif" width="30px">


![Undergrad](https://img.shields.io/badge/Undergrad-SCAU-blue)
![Internship](https://img.shields.io/badge/Internship-Edelman-blue)

- I am working as a analysis intern in the [DXI China team]([https://lab.plopes.org](https://www.edelmandxi.com/)) at Edelman.
- My areas of interest include Blockchain, risk analytics and machine learning.
- I am seeking opportunities for a graduate studies in the field of technologgy.

[Email](mailto:Alaiazhan@163.com) |  [Linkedin](https://www.linkedin.com/in/Yingyunzhan0731/)

## Languages & Techologies

![Python](https://img.shields.io/badge/-Python-000?&logo=Python)
![C](https://img.shields.io/badge/-C-000?&logo=C)
![SQL](https://img.shields.io/badge/-SQL-000?&logo=MySQL)
![R](https://img.shields.io/badge/-R-000?&logo=r)
![HTML](https://img.shields.io/badge/-HTML-000?&logo=html5)
![PyTorch](https://img.shields.io/badge/-PyTorch-000?&logo=PyTorch)
![Figma](https://img.shields.io/badge/-Figma-000?&logo=figma)
![Arduino](https://img.shields.io/badge/-Arduino-000?&logo=arduino)
name: generate animation

on:
  # run automatically every 24 hours
  schedule:
    - cron: "0 */24 * * *" 
  
  # allows to manually run the job at any time
  workflow_dispatch:
  
  # run on every push on the master branch
  push:
    branches:
    - master
    
  

jobs:
  generate:
    runs-on: ubuntu-latest
    timeout-minutes: 10
    

steps:
      # generates a snake game from a github user (<github_user_name>) contributions graph, output a svg animation at <svg_out_path>
      - name: generate github-contribution-grid-snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
                  
      # push the content of <build_dir> to a branch
      # the content will be available at https://raw.githubusercontent.com/<github_user>/<repository>/<target_branch>/<file> , or as github page
      - name: push github-contribution-grid-snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          
