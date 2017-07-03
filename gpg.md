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

## Links
- [Creating keys](http://www.void.gr/kargig/blog/2013/12/02/creating-a-new-gpg-key-with-subkeys/)
