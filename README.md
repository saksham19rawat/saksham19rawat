### I'm Saksham Rawat

🎓 Final-year Electrical Engineering student  
💻 Learning Verilog 
---
🛠️ **Tech Stack**  
- Languages: `C` `Python` `Verilog`

- Tools: `Vivado` `Xilinx ISE` `LTspice` `Ngspice` `Xschem`
  
- Platforms: `GitHub`, `HDL Bits`, `Linux`

---

### 🌐 Connect with me

<a href="mailto:sakshamrawatb26@gmail.com"><img src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white"/></a>

<a href="" target="_blank"><img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white"/></a>
[![HDLBits Profile](https://img.shields.io/badge/HDLBits-View%20My%20Work-blue?style=for-the-badge)](https://hdlbits.01xz.net/wiki/Special:VlgStats/Me)


name: Generate pacman animation

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
      - name: generate pacman-contribution-graph.svg
        uses: abozanona/pacman-contribution-graph@main
        with:
          github_user_name: ${{ github.repository_owner }}


      - name: push pacman-contribution-graph.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}


---


