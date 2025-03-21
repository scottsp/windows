# windows
Comandos Windows

---

~~~
setx /S ts003 /U dominio\user /P senha /m PATH "C:\Program Files (x86)\Common Files\Oracle\Java\javapath;C:\app\client\adm\product\19.0.0\client_1\bin;C:\Windows\system32;C:\Windows;C:\Windows\System32\Wbem;C:\Windows\System32\WindowsPowerShell\v1.0\;"
~~~

/s - Especifica sistema remoto.

/u - Usuário.

/p - Senha.

/m - Altarar variável de ambiente, se não colocar altera variável local.

Essa configuração é salva no registro do Windows em:
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\Environment

---

Para descobrir o nome do dispositivo ethernet:
~~~
netsh interface ipv4 show addresses
~~~

Para alterar a placa de rede "Conexão Local" para DHCP:
~~~
netsh interface ipv4 set address "Conexão local" dhcp
~~~

Para colocar um IP estatico:
~~~
netsh interface ipv4 set address "Conexão local" static 192.242.0.119 255.255.252.0 192.242.3.2
~~~

DNS1:
~~~
netsh interface ipv4 set dnsserver "Conexão Local" static 192.242.3.15 primary
~~~

DNS2
~~~
netsh interface ipv4 add dnsserver "Conexão Local" static 192.242.3.18
~~~

---

Para liberar uma porta pelo firewall do Windows:
~~~
netsh advfirewall firewall add rule name="permite VNC" protocol=tcp dir=in localport=5900 action=allow
~~~

---

Para parar o Kaspersky Antivirus
~~~
klpsm.exe stop_avp_service
~~~

Para iniciar o Kaspersky Antivirus
~~~
klpsm.exe start_avp_service
~~~

---

CORRIGIR A INSTALAÇÃO DO WINDOWS

~~~
sfc /scannow
dism /Online /Cleanup-image /Restorehealth - Usa o Windows Update para restaurar
~~~

---

RENOMEAR ESTAÇÕES WINDOWS COM NETDOM
~~~
netdom renamecomputer <Computer> /newname:<NewComputerName> /userd:braspar\adm /passwordd:* [/reboot[:<Delay>]] [{/help | /?}]
~~~

ADICIONAR ESTAÇÕES WINDOWS NO DOMÍNIO
~~~
netdom join <Computer> {/d: | /domain:}<Domain> [/ou:<OUPath>] [{/ud: | /userd:}[<Domain>\]<User> [{/pd: | /passwordd:}{<Password>|*}]] [/reboot[:,Delay>]] [/help | /?]
~~~

REMOVER ESTAÇÕES WINDOWS DO DOMÍNIO
~~~
netdom remove <computer> {/d: | /domain:}<Domain> [/reboot[:<Delay>]] [/help | /?]
~~~

---

LISTA INFORMAÇÕES DO USUÁRIO NO DOMÍNIO
~~~
net user nome.usuário /domain
~~~

---

MOSTRA A ÚLTIMA INICIALIZAÇÃO DO SISTEMA VIA PROMPT DE COMANDO
~~~
systeminfo | find "Tempo de Inicialização do Sistema"
~~~

---

DESINSTALAR PROGRAMAS VIA DOS
~~~
WMIC product WHERE name="NAME OF YOUR PROGRAM" CALL uninstall
Echo Y|WMIC product WHERE name="NAME OF YOUR PROGRAM" CALL uninstall
~~~

---

Windows 7: Falha no logon do Serviço de Perfil de Usuário

HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\ProfileList

Localizar o registro com o fim ".bak", excluir o atual e renomear retirando o .bak. Reiniciar o PC

---

Aumentar o limite de anexo do outlook de 10MB (padrão) para 50MB

HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Outlook\Preferences

- Procure pela entrada "MaximumAttachmentSize"
- Caso não tenha, clique com o botão direito > Novo : Chave DWORD.
- Digite o nome MaximumAttachmentSize e coloque o valor de 51200 e clique em OK

---

Configurar Windows para localizar o mouse (https://www.hardware.com.br/noticias/nunca-mais-perca-o-cursor-do-mouse-de-vista-com-esse-truque-do-windows.html)

- Pressione as teclas Windows + S e digite "mouse";
- Acesse Configurações do mouse e clique em "Configurações adicionais do mouse";
- Na aba Opções do ponteiro, marque a caixa "Mostrar local do ponteiro quanto CTRL foi pressionada".
