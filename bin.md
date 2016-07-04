# Bin commands for misc apps

## Add folder to Alfred scope
```
    defaults write com.alfredapp.Alfred scope.paths -array-add "/opt/homebrew-cask/Caskroom"
```

## Migrate caskroom 
```
    mv /opt/homebrew-cask/Caskroom /usr/local
```