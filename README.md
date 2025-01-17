# HS2023-Exercise08

This repository contains a collection of tools and workflows specifically designed to acquaint students with the fundamental aspects of using Git and GitHub. The primary goal of this exercise is to provide students with practical experience in using Git for version control, while also familiarizing them with the process of contributing to projects in a simulated environment. The scripts and automated workflows included herein facilitate a semi-automated assessment of this practical exercise.


## Overview of the Repository

This repository is structured to support the exercise workflow. It includes:

`submit.sh` & `submit.ps1`: Scripts that students are required to execute on their local machines to generate submissions. These scripts accept the student's email address and produce a file in the submissions folder, using the SHA256 hash of their email as the filename.

`.github/workflows`: Automated checks configured to validate each submission upon the creation of a pull request.

`submissions`: The folder where the files generated by the submission scripts are collected.

`helpers`: This folder contains a suite of auxiliary scripts for both setting up the exercise and facilitating the final assessment.

`hashes.txt`: A list of SHA256 hashes of the mail addresses of the students. Used for validating the submissions.


## Submission Scripts

We provide two scripts for making submissions:

- `submit.ps1`: A PowerShell script for Windows users.
- `submit.sh`: A Bash script for Unix/Linux and macOS users.

These scripts ask for the email address, process it, and then create a file in the submissions directory. The filename is a hash of the student's email address. The students need to use their university mail address with which they are enrolled into the lecture.


## Making a Submission

To make a submission, students should:

1. Fork this repository.
2. Clone the forked repository to their local machine.
3. Run the appropriate submission script.
4. Commit the changes made by the script.
5. Push the commit back to their forked repository on GitHub.
6. Create a pull request to the original repository.

If a student's pull request passes the checks, their submission is considered valid.


## GitHub Actions Workflows

This repository uses GitHub Actions to automatically validate submissions. The workflow checks that:

- Each pull request adds exactly one new file to the submissions directory.
- That the submission corresponds to the hashed email address of a participant.


## Setup and Assessment Process

This section outlines how to setup the repository and asses the submissions.

### Setup (generating hashes file)

To setup the exercise, a CSV file with the participants of the lecture needs to be exported from the ADAM system. This CSV contains for columns: 

- The role of the participant in the course (ignored by the scripts)
- The last name of the participant
- The first name of the participant
- The email address of the participant. 

The file needs to be named `teilnehmer.csv` and has to be placed in the folder `helpers` next to the `python3 create_hashes_file.py ` script. The `hashes.txt` file is then generated by executing:

```pyhon
python3 create_hashes_file.py 
```

The `hashes.txt` file needs to be committed and pushed to GitHub.


### Assessment

First, all Pull Requests that have passed the checks need to be merged. The submissions can then be assessed using the `evaluate.py` script:

```pyhon
python3 evaluate.py 
```

For this, the `teilnehmer.csv` needs to be placed in the folder `helpers` next to the `evaluate.py` script. The scripts generate a file with the name `valid_submissions.csv` containing a list of all students who have passed the exercise.



## Contributing to the Repository

Although this repository is primarily intended for educational use, we welcome suggestions for improvement or correction.


## License

This repository and its contents are licensed under the Apache 2.0 License. For more details, please see the LICENSE file.

