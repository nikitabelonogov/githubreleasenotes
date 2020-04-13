#!/bin/bash

set -ueo pipefail ${DEBUG:+-x}


remote=$(git config --get remote.origin.url)
host=$(echo "${remote}" | cut -d'@' -f2 | cut -d':' -f1)
organisation=$(echo "${remote}" | cut -d':' -f2 | cut -d'/' -f1)
repository=$(echo "${remote}" | cut -d'/' -f2 | cut -d'.' -f1)

if [ -z "${access_token}" ]; then
	echo "Generate and/or enter a personal access token"
	echo "https://help.github.com/en/github/authenticating-to-github/creating-a-personal-access-token-for-the-command-line"
	read -s -p "token: " access_token
	echo
fi

outfile="${outfile:-RELEASENOTES.md}"

echo "Fetching releases from https://${host}/${organisation}/${repository}/releases"
releases=$(curl --silent --header "Authorization: token ${access_token}" "https://${host}/api/v3/repos/${organisation}/${repository}/releases")

echo "Forming notes to ${outfile}"
 jq '.[] | select(.body != "") | "# "+.name+"\n["+.tag_name+"]("+.html_url+")\n> "+.published_at+"\n"+.body+"\n\n"' -r <<< "${releases}" > ${outfile}
