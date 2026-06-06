\## Como acessar seus serviços na VPS — Carbri



\### Informações do servidor



\- \*\*IP:\*\* `SEU\_IP\_VPS`

\- \*\*Sistema:\*\* Ubuntu 22.04 LTS

\- \*\*Usuário:\*\* root



\---



\### Conectar ao servidor



Abre um \*\*PowerShell\*\* e digita:



```

ssh root@SEU\_IP\_VPS

```



Digita a senha root quando pedir.



\---



\### Acessar o n8n



Acessa direto pelo navegador, sem precisar conectar ao servidor:



```

http://SEU\_IP\_VPS:5678

```



\---



## Acesso ao Paperclip

O Paperclip está acessível de qualquer lugar via:
http://2.25.172.117

Usuário: SEUUSUARIO
Senha: SUA_SENHA



\---



\### Segurança — Firewall



O firewall está ativo com as seguintes regras:



|Porta|Serviço|Status|

|---|---|---|

|22|SSH|Aberta|

|5678|n8n|Aberta|

|3100|Paperclip|Fechada (acesso só via túnel SSH)|

|Demais portas|—|Bloqueadas|







\---



\### Troubleshooting



\*\*O n8n não abre no navegador?\*\* Conecta ao servidor e rode:



```

cd \~/n8n \&\& docker compose up -d

```



\*\*O Paperclip não está respondendo?\*\*



Verifica se o serviço está rodando:



```

systemctl status paperclip

```



Deve aparecer `Active: active (running)`.



Se estiver parado, inicia:



```

systemctl start paperclip

```



\*\*Verifica em qual porta o Paperclip está escutando:\*\*



```

journalctl -u paperclip | grep "Server listening"

```



Normalmente é a 3100. Se aparecer outra porta, ajusta o túnel:



```

ssh -L 3100:127.0.0.1:PORTA root@SEU\_IP\_VPS

```



(substitui PORTA pelo número que aparecer)



\*\*Erro "Address already in use" ao criar o túnel?\*\* Fecha todos os PowerShells abertos e abre um novo limpo antes de rodar o comando do túnel.



\*\*Erro "ERR\_FAILED" no navegador mesmo com túnel aberto?\*\* O comando do túnel foi rodado dentro do servidor em vez do Windows local. Abre um PowerShell novo sem fazer nenhum `ssh` antes de rodar o comando do túnel.



\*\*Verifica se o Paperclip está saudável sem abrir o navegador:\*\*



```

curl http://localhost:3100/api/health

```



Deve retornar `"status":"ok"`.



\*\*Reiniciar tudo do zero:\*\*



```

reboot

```



Aguarda 60 segundos, reconecta via SSH e os serviços sobem automaticamente.



