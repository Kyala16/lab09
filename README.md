# lab04

**Задание написано в formatter.yml**

![Jokes Card](https://readme-jokes.vercel.app/api)

Status of Last Build:<br>
<img src="https://github.com/Kyala16/lab04/workflows/Formatter/badge.svg?branch=main"><br>

```
#-------------------------------------
#  Lab04 - Work this GitHub Actions
#  @Kyala16
#-------------------------------------

name: Formatter

on:
  push:
    branches: 
    - main

  workflow_dispatch:

jobs:
  Build-library:
    # The type of runner that the job will run on
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2

      - name: Build formatter_lib
        shell: bash
        run: |
          cd formatter_lib
          mkdir build && cd build
          cmake ..
          cmake --build .
          
      - name: Build formatter_ex_lib
        shell: bash
        run: |
          cd formatter_ex_lib
          mkdir build && cd build
          cmake ..
          cmake --build .
      - name: Build solver_lib
        shell: bash
        run: |
          cd solver_lib
          mkdir build && cd build
          cmake ..
          cmake --build .
  
  Hello-world:
    runs-on: ubuntu-latest
    needs: [ Build-library ]
    
    steps:
      - uses: actions/checkout@v2
      
      - name: Build Hello_world
        shell: bash
        run: |
          mkdir build1 && cd build1
          cmake ..
          cmake --build .
  
      - name: writer
        shell: bash
        run: |
          cd build1/hello_world_application
          ./hello_world
  Build-solver:
    runs-on: ubuntu-latest
    needs: [ Build-library ]
    
    steps:
      - uses: actions/checkout@v2
      
      - name: Build solver_application
        shell: bash
        run: |
          mkdir build2 && cd build2
          cmake ..
          cmake --build .
          
      - name: writer
        shell: bash
        run: |
          cd build2/solver_application
          ./solve 1 2 1
```
