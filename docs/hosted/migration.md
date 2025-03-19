# Migrating From an Existing Minder Instance


Determine the profile you want to migrate:
```
minder profile list -o json | jq -r '.profiles[] | .name'
```

Get the profile as yaml:

```
minder profile get -n $NAME -o yaml > $NAME.yaml
```

Find all the ruletypes:
```
minder profile get -n $NAME -o json | \
  jq -r '((.profile.repository // [] | .[]), (.profile.release // [] | .[])) | .name' | \
  sort -u
```

For each ruletype, fetch the data:

```
minder ruletype get -n $RULENAME -o yaml > $RULENAME.yaml
```
