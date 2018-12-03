Super convenient for any issues that may occur with whitespace in your directory and filenames

This will replace <b> ALL <b/> the whitespace (in both the directory names and filenames) with underscores in a specific directory (which you select by inputting the path in the `/insert/path/name` part). Very useful for programs like FSL that require no white space


```

find /insert/path/name  -name "* *" -print0 | sort -rz | \
  while read -d $'\0' f; do mv -v "$f" "$(dirname "$f")/$(basename "${f// /_}")"; done


```
