# Monster Ground - Unity 3D FPS Game 

>This is a 3D action game created by benchmarking the steam game Vampire Survival. 
<p>
  <a><img src="https://img.shields.io/badge/unity3d-2020.3.33f1-blue?style=flat-square&logo=unity"></a>
</p>

## 🎯 Play Game
<!-- BEGIN LATEST DOWNLOAD BUTTON -->
name: "Download Button Action"

on:
  release:
    types:
      - published
  workflow_dispatch:

jobs:
  release:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2

      - name: Get latest release
        id: get-latest-release
        uses: InsonusK/get-latest-release@v1.0.1
        with:
          myToken: ${{ github.token }}
          view_top: 1

      - name: Readme Download Button Action
        env:
          GITHUB_USER: "Team-NRE"
          REPO: "MonsterGround"
          FORMAT: "zip"
          VERSION: "${{ steps.get-latest-release.outputs.tag_name }}"
          COLOR: "blue"
          BEGIN_TAG: "<!-- BEGIN LATEST DOWNLOAD BUTTON -->"
          END_TAG: "<!-- END LATEST DOWNLOAD BUTTON -->"
        run: |
          UPDATE=$(cat README.md | perl -0777 -pe 's#(${{ env.BEGIN_TAG }})(?:.|\n)*?(${{ env.END_TAG }})#${1}\n[![Download ${{ env.FORMAT }}](https://custom-icon-badges.herokuapp.com/badge/-Download-${{ env.COLOR }}?style=for-the-badge&logo=download&logoColor=white "Download ${{ env.FORMAT }}")](https://github.com/${{ env.GITHUB_USER }}/${{ env.REPO }}/archive/${{ env.VERSION }}.${{ env.FORMAT }})\n${2}#g')
          echo "${UPDATE}" > README.md

      - uses: EndBug/add-and-commit@v7
        with:
          message: "docs(readme): Bump download button version to ${{ steps.get-latest-release.outputs.tag_name }}"
          default_author: github_actions
          branch: main
<!-- END LATEST DOWNLOAD BUTTON -->

## 📽 Game Screen
  * Start
  
![start](https://user-images.githubusercontent.com/92200057/172681127-2d7ac5c5-329f-4a42-ade0-9f000c532912.png)
  
  * Stage Mummy
  
![Stage Mummy](https://user-images.githubusercontent.com/92200057/172681705-a6a7e04e-1571-4e60-b133-24ec803d0d89.png)
  
  * Stage Spider
  
![Stage Spider](https://user-images.githubusercontent.com/92200057/172681776-15d155b4-0b2c-4e24-aff8-0282ca6bc3cd.png)
  
  * Stage Zombie
  
![Stage Zombie](https://user-images.githubusercontent.com/92200057/172681790-d429db97-79a5-4872-9548-eeb5ae943ccc.png)
  
  * Stage Boss
  
![Stage Boss](https://user-images.githubusercontent.com/92200057/172681794-bab760ee-7f36-40e7-b028-1702b665b884.png)

## 📢 YouTube
https://www.youtube.com/watch?v=extglroDbYg

## ⚙ Development Environment
 * OS : Windows 10
 * Tool : Unity 3D 2020.3.33f1
 
## 🚀 Feature
 * 3D Action Game 
 * The stage format consists of 4 levels, the last of which you have to fight the dragon which is the boss monster.
 * Tool (A variety of free Unity assets)

## 🚀 How to Play
 1) Each stage has a different monster, and the more you clear, the stronger it will attack. Shoot and kill or dodge monsters before they attack.
 2) You have to break the portals in the north, south, east, west, and south and enter the portal created in the center before you can move on to the next stage.
 3) Strengthen your character by level up or eating 18 random items that are generated every 30 seconds.
 4) After the last boss breaks the dragon, you win! 

## ✔ Acknowledgments
 * It is for the 2022-1 Sungkyul University VR/AR Game Competition 1st Place
 
## ✔ License
Copyright © 2022-Team NRE - Sungkyul University.
