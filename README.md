# extend-trial-jetbrains-linux
A script to reset the 30-day trial period of JetBrains products on Linux.

`extend-trial-jetbrains-linux.sh`

```bash
#!/bin/bash

# Array of JetBrains products
products=("WebStorm" "IntelliJ" "CLion" "Rider" "GoLand" "PhpStorm" "Resharper" "PyCharm")

# Loop through each product and delete eval folder and options.xml
for product in "${products[@]}"; do
    for dir in "$HOME"/."$product"*; do
        if [ -d "$dir/config/eval" ]; then
            echo "Removing eval folder from $dir"
            rm -rf "$dir/config/eval"
        fi

        if [ -f "$dir/config/options/other.xml" ]; then
            echo "Removing other.xml from $dir"
            rm -f "$dir/config/options/other.xml"
        fi
    done
done

# Optionally delete JetBrains config folder
if [ -d "$HOME/.config/JetBrains" ]; then
    echo "Removing JetBrains config folder"
    rm -rf "$HOME/.config/JetBrains"
fi

echo "Cleanup completed."

```
