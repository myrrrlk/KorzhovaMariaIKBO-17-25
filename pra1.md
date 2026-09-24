задание 1
решение
grep -o '^[^:]*' /etc/passwd | sort  

задание 2
решение
grep -v '^#' /etc/protocols | awk '{print $2, $1}' | sort -rn | head -5

задание 3
решение
#!/bin/bash

text="$1"

length=${#text}
line=$(printf '%*s' $((length + 2)) '' | tr ' ' '-')

echo "+$line+"
echo "| $text |"
echo "+$line+"


задание 4
решение 
#!/bin/end bash
grep -oE '\b[A-Za-z_][A-Za-z0-9_]*\b' "$1" | sort -u

задание 5
решение
#!/bin/bash
chmod +x "$1"
sudo cp "$1" /usr/local/bin/

задание 6
#!/bin/bash 
for file in *.c *.js *.py; do
[ -e "$file" ] || continue 
first_line=$(head -n 1 "$file")
case "$file" in
*.c|*.js)
if echo "$first_line" | grep -Eq '^[[:space:]]*(//|/\*)'; then 
echo "$file: комментарий есть"
else
echo "$file: комментария нет"
fi
;;
*.py)
if echo "$first_line" | grep -Eq '^[[:space:]]*#'; then 
echo "$file: комментарий есть" 
else 
echo "$file: комментария нет" 
fi 
;; 
esac
done
задание 7

#!/bin/bash

if [ -z "$1" ]; then
echo "Укажите путь"
exit 1
fi
find "$1" -type f -exec sha256sum {} + | sort | uniq -w 64 -D

задание 8

#!/bin/bash

find . -maxdepth 1 -type f -name "*.$1" -print0 | tar --null -cf archive.tar -T -
задание 9

#!/bin/bash
find . -maxdepth 1 -type f -name "*.$1" -print0 | tar --null -cf archive.tar -T -

задание 10
#!/bin/bash

find "$1" -maxdepth 1 -type f -empty -print
