#This script is used to Resolve DNS to IP using certain rule sets...

if [ -z "$1" ] || [ -z "$2" ]; then
  echo "[!] Usage: ./url2ip.sh [domain-list-file] [output-file]"
  exit 1
fi
echo "[+] Resolving Domains to IP Addresses..."
while read d || [[ -n $d ]]; do
  ip=$(dig +short $d|grep -oE "\b([0-9]{1,3}\.){3}[0-9]{1,3}\b"|head -1)
  if [ -n "$ip" ]; then
    echo "[+] '$d' => $ip"
    echo $ip >> $2
  else
    echo "[!] '$d' => [RESOLVE ERROR]"
  fi
done < $1
echo -e "\n[+] Removing Duplicates..."
sort $2 | uniq > $2.new
mv $2.new $2
echo -e "\n[+] Done, IP Addresses saved to '$2'."

#End of Script...
