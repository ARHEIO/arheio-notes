---
title: Useful Bash Commands

---
# Useful Bash Script Recipes

For when you need to do something and can't be bothered Googling it

### I want to store the result of a script as a variable

      #!/bin/sh
      # ./script.sh
    
      FILE_LOCATION=$1
      FILE_DIR=$(echo $FILE_LOCATION | sed 's:/[^/]*$::')
      
      echo $FILE_DIR

Running `./script.sh src/index.ts` prints `src`

### I want to ensure the script was passed an arg

`#$` is the number of args passed, so check that we were passed 0 args

      if [ $# -eq 0 ]; then
        echo "No arguments supplied"
        exit 1
      fi
    

You can be fancy and check for a specific number of args

      if [ $# -ne 1 ]; then
        echo "Must supply exactly one argument"
        exit 1
      fi

fin

***