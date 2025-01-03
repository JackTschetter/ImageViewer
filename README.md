# BCIMGVIEW

![License](https://img.shields.io/badge/license-MIT-blue.svg)  
![Version](https://img.shields.io/badge/version-1.0.0-green.svg)

## Table of Contents

- [About the Project](#about-the-project)
- [Vulnerability I](#vulnerability-i)
- [Vulnerability II](#vulnerability-ii)
- [Vulnerability III](#vulnerability-iii)
- [Vulnerability IV](#vulnerability-iv)
- [Vulnerability V](#vulnerability-v)
- [Tools Used](#tools-used)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Usage](#usage)
- [Results and Evaluation](#results-and-evaluation)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)
- [Acknowledgments](#acknowledgments)

---

## About the Project

This project was created for teaching the class CSCI 4271W --- Designing and Developing Secure Software at UMN Twin Cities. I developed and taught from this project during Spring Semester 2024. 

BCIMGVIEW is the latest and greatest product from badly coded industries! It is an image viewer inspired by eye of gnome. BCIMGVIEW supports the following three bitmap image formats.
<li>BC-Raw, with the file extension .bcraw, is an uncompressed true color format similar to bcimgview’s internal representation and to PPM.</li>
<li>BC-Progressive, extension .bcprog, is intended for transmitting images over low- bandwidth network connections, like web sites in the 1990s. Colors are represented with single bytes from a 6x6x6 color cube, and scanlines are sent in an interleaved order.</li>
<li>BC-Flat, extension.bcflat, is a losslessly compressed true color format that separately encodes the red, green, and blue channels. The differences between adjacent samples in a scan line are computed and then one or more differences are encoded with a fixed dictionary of variable-length binary codewords.</li><br>

The source code for bcimgview, some sample images in the various supported formats, and pre compiled Linux x86-64 binary of the most recent release are open source and available for download from this repository.

---

## Tools Used

- **Operating System**: Linux. Perhaps in the future other compatible Unix variants.
- **Programming Language(s)**: C
- **Libraries**: The GUI portion uses the GTK 3 family of GUI libraries.

---

## Getting Started

### Prerequisites

- A machine running Ubuntu 22.04. The program should on most recent Linux systems, although the supported configuration is Ubuntu 22.04.

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/project-name.git
   cd project-name

---

## Usage

## Vulnerability I --- Insecure/user controlled format string

### Summary

## Vulnerability II --- Integer Overflow

### Summary

## Vulnerability III --- Incorrect usage of do-while loops

### Summary

## Vulnerability IV --- Incorrect decompression logic

### Summary

This attack was caused by incorrect decompression logic in .bcflat encoded files leading to a stack buffer overflow (potentially) leading to arbitrary code execution.

This was by far the most subtle of all 4 attacks. Some might call it the most beautiful! Of roughly 70 students in this course, only 2 found and exploited this vulnerability perfectly. It is also notable because it was the only one of the 4 intentionally planted vulnerabilities which led to a buffer overflow on the stack. All the other buffer overflows were on the heap.

## Vulnerability V --- CSS Injection

### Summary

This was not actually an attack in the most literal sense of the word. Cascading Style Sheets (CSS) is not a Turing complete language, so this vulnerability does not actually have the potential to cause things like arbitrary code execution or elevation of privilege.

In the wild however CSS injections can still be problematic. One such example could be an attacker using a CSS injection attack to display harmful advertisements on your website.

In our case the offending portion of the code is highlighted below. The vulnerability stems directly from a careless usage of environment variables on line 1954.<br><br>
<img src="./assets/css_injection_code.png" alt="CSS Injection Code" width="45%" height="45%">

### Executing the Attack

This "attack" rests on the insecure use of the envirnoment variable BC_BGCOLOR above. To understand the attack let us first consider the intended functionality of the program. Below is the command to run the image viewer and display the image maze.bcprog, along with the expected output. **NOTE** these two images show case the normal/intended behavior of the program. <br><br>
<img src="./assets/maze_command.png" alt="maze_command" width="30%" height="30%"><br><br>

<img src="./assets/maze.png" alt="maze" width="30%" height="30%"><br><br>

Below is the command for the CSS injection, along with the output. This command takes advantage of the insecure usage of an environment variable to cleverly inject our own information about styling. It is not a full attack since it does not cause arbitrary code execution, or elevation of privilege, but it does constitute cyber vandalism nonetheless. <br><br>
<img src="./assets/css_injection_command.png" alt="CSS Injection" width="30%" height="30%"><br><br>

<img src="./assets/css_injection_result.PNG" alt="CSS Injection Result" width="30%" height="30%"><br><br>

## Contact
