Super convenient for any issues that may occur 

This will replace all the whitespace in a specific directory (based on the `/insert/path/name` part) with underscores. Very useful for programs like FSL


```

find /insert/path/name  -name "* *" -print0 | sort -rz | \
  while read -d $'\0' f; do mv -v "$f" "$(dirname "$f")/$(basename "${f// /_}")"; done


```
