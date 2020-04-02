# Iptables

Liste les règles: `iptables -n -L -v --line-numbers`  
Liste **NAT** rules: `iptables -L -t nat`    
Liste toutes les règles : `iptables-save`  
Supprimer une règle: `iptables -D <table> <rule_nb>` EX:`iptables -D INPUT 1`  
