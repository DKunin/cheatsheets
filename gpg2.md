# GPG and stuff

## Run gpg-agent

	eval $(gpg-agent --daemon)

## Export and move keys

	gpg --export-secret-keys > keyfile
	gpg2 --import keyfile

	gpg2 --edit-key // secret-key id
	trust
	save

## Pinentry 

    echo "pinentry-program /usr/bin/pinentry-mac" > ~/.gnupg/gpg-agent.conf

## Reload Agent

    gpg-connect-agent reloadagent /bye