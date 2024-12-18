[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/skJdUf3s)
# Principles of Programming and Programming Languages
# Mini-Project

See [instructions.md](instructions.md) for submission instructions.

# Using Flask to Learn Functional Programming Principles in Python

## Description

This project is centered around developing a simple but functional ToDo List html application using the Flask software framework in Python. The app allows users to manage tasks by adding, editing, and checking them as complete. It is a good introduction to the Flask software framework, and clearly uses course concepts from PPL. Beyond its actual utility, the project serves to demonstrate functional programming. It includes the concept of functions as values within the context of a web app.

This project in video format gives clear and incremental steps in order to build the web app yourself. It teaches the basics of Flask, especially with creating routes for functionality and rendering HTML templates to display and interact with a to do list. All of this is done while reviewing some course concepts along the way. For example, functions as values are prevalently shown when tasks are toggled via reusable helper functions, improving modularity in the code. 

Overall, the project combines a very simple and common application with the course concepts we've learned this semester. It serves to show how these concepts can be applied in Python to build a practical and scalable app while being simple enough to be learned from and studied. The project makes a good learning tool for software developers to deeper understand both the Flask software framework and functional programming.

## Repository Organization

video-jlettau12
|-- README.md
|-- instructions.md
|-- flasktest.py // a test file to run a web server and see if flask is installed and working
|-- sources.txt // works cited
|-- script.md // video script
|-- recording.mp4 // the final video - vscode doesn't play it with sound, but there is a voiceover, so make sure you can hear it
|-- toDoApp
    |-- app.py // main python program to process todo functions
    |-- templates
        |-- index.html // html file to build the webpage and list
        |-- edit.html // html file to process editing an entry


## Building and Testing Instructions

Assuming python and pip are installed, go to your Windows terminal and enter "python -m pip install flask" to install the flask framework. Then, run it in vscode in the toDoApp folder directory with "python app.py". It will output a link to a web server in the terminal for the final functional product.

## Presentation

- YouTube: https://youtu.be/0kcWs6j9hDQ
- Script: [script.md](script.md)
- Recording: [recording.mp4](recording.mp4).
