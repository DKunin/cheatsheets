# Creating master key

```
	gpg --gen-key
```

# Creating sub keys

```
	gpg --edit-key <key ID>
	addkey
	...
	save
```

# Exporting Subkeys

```
	gpg --export-secret-subkeys <subkey ID> > subkeys
```

# Importing secret subkeys

```
	gpg --allow-secret-key-import --import ~/private_key.txt
```
