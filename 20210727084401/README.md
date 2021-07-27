# script to get a list of all the functions in a script

This script i found may be useful to add to completion to scrape for the
files. Not sure if it works with completion. Needs to be tested.

get_functions() {
    # Usage: get_functions
    IFS=$'\n' read -d "" -ra functions < <(declare -F)
    printf '%s\n' "${functions[@]//declare -f }"
}
