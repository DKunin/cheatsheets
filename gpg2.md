# GPG and stuff

## Run gpg-agent

	eval $(gpg-agent --daemon)

## Export and move keys

	gpg --export-secret-keys > keyfile
	gpg2 --import keyfile

	gpg2 --edit-key // secret-key id
	trust
	save

