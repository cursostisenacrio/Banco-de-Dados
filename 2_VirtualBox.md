# Instalação e configuração do Oracle Linux 8
## Ambiente de virtualização com Oracle VM VirtualBox

O VirtualBox é um software de virtualização desenvolvido pela Oracle que permite a criação de máquinas virtuais.
Com ele, você pode instalar e executar diferentes sistemas operacionais em um único computador, como rodar Linux dentro do Windows ou Mac dentro do Windows, de forma independente e simultânea.
Isso é especialmente útil para desenvolvedores e profissionais de TI que precisam testar software em diferentes ambientes sem a necessidade de múltiplos hardwares.

Alguns links de referência:

 - [VirtualBox: O que é, para que serve e como usar?](https://blog.infnet.com.br/virtualizacao/virtualbox-o-que-e-para-que-serve-e-como-usar/)
 - [VirtualBox e máquinas virtuais: o que é e como usar | Alura](https://www.alura.com.br/artigos/virtualbox-maquinas-virtuais)
 - [VirtualBox | Software | TechTudo](https://www.techtudo.com.br/tudo-sobre/virtualbox/)
 - [O que é VirtualBOX? - TopGadget](https://www.topgadget.com.br/howto/software/o-que-e-virtualbox.htm)

### Obtendo e instalando

Neste roteiro vamos usar um computador com sistema operacional Windows 10 ou 11, com pelo menos 4 GB de RAM e 120 GB de espaço de armazenamento livre, HDD ou SSD.

Baixe o instalador da versão mais recente do VirtualBox de https://www.virtualbox.org/wiki/Downloads. Usaremos a versão **Windows hosts**.

Uma vez baixado, basta executar o instalador. A instalação segue os procedimentos padrão de outros aplicativos Windows, sem a necessidade de ajustes no percurso.

<p align="center" width="100%"><img src="https://raw.githubusercontent.com/Luferat/MyGistImages/main/oracle/linux/01.png" alt="VirtualBox"></p>

### Imagem ISO do Oracle Linux

Também vamos precisar da imagem ISO do **Oracle Linux 8** que pode ser baixada [aqui](https://yum.oracle.com/oracle-linux-isos.html) ou [aqui](https://edelivery.oracle.com/osdc/faces/SoftwareDelivery). 
Mesmo que existam versões mais novas, baixe a versão 8 mais recente, pois é a que está homologada para o **Oracle Database XE** que usaremos no futuro. 
Na data deste roteiro, a versão mais recente é a `OracleLinux-R8-U10-x86_64-dvd.iso` (Release 8.10).

### Criando uma VM

Com tudo baixado e seguindo os pré requisitos para instalação do **Oracle Linux 8**, disponíveis [aqui](https://docs.oracle.com/en/operating-systems/oracle-linux/8/install/install-PreparingToInstall.html#install-requirements), vamos preparar uma nova VM no VirtualBox.

Siga os passos:

1. Na interface do VirtualBox, clique em `Novo` → <kbd>Ctrl</kbd> + <kbd>N</kbd> para abrir a janela "Nome da máquina virtual e Sistema Operacional";
2. No campo `Nome`, preencha `OracleDBServer` ou algo similar, sem espaços ou caracteres especiais;
3. Não altere a "Pasta" de instalação da VM;
4. Em `Imagem ISO`, clique na seta e escolha `Outro...`;
5. Localize e abra a imagem ISO do **Oracle Linux** que você baixou;
6. Os outros campos devem ficar desabilitados;
7. **IMPORTANTE!** Marque a opção `Pular Instalação Desassistida` para que tenhamos controle total sobre a instalação;
8. Clique em `[Proximo]`;

<p align="center" width="100%"><img src="https://raw.githubusercontent.com/Luferat/MyGistImages/main/oracle/linux/02.png" alt="Configurações iniciais"></p>

9. Na janela "Hardware" ajute a memória para pelo menos `2048 MB` e `2` processadores. Como não vamos usar interface gráfica, isso será suficiente;
10. Clique em `[Proximo]`;
11. Na janela "Disco Virtual" marque `Criar um novo disco rígido virtual agora`;
12. No `Tamanho do disco`, configure pelo menos `120 GB`; `200 GB` é o idel. Não se preocupe porque o espaço é alocado dinâmicamente, portanto, não ocuparaá, realmente, 120 GB;
13. Clique em `[Proximo]`;

<p align="center" width="100%"><img src="https://raw.githubusercontent.com/Luferat/MyGistImages/main/oracle/linux/03.png" alt="Configuração do disco virtual"></p>

14. Na janela "Sumário", revise as configurações e, se necessário, volte para corrigí-las.

<p align="center" width="100%"><img src="https://raw.githubusercontent.com/Luferat/MyGistImages/main/oracle/linux/04.png" alt="VM quase pronta"></p>

### Ajustes na VM

A VM está quase pronta, mas, vamos fazer alguns ajustes para deixá-la mais refinada.

1. Com a nova VM selecionada, clique em `Configurações`;
2. Na guia "Rede", com o "Adaptador 1" selecionado, selecione `Conectado a:` → `Placa em modo Bridge` de forma a manter essa VM na mesma rede local que o hospedeiro;
3. Na guia "Pastas Compartilhadas", clique na pasta com um `+` na direita;
4. Na janela "Acrescentar Compartilhamento", no campo `Caminho da pasta`, clique na seta para baixo e clique em `Outro...`;
5. Navegue até sua pasta `Downloads` e clique em `[Selecionar pasta]`;
6. No campo `Ponto de Montagem`, digite `/mnt/downloads`;
7. Marque a opção `Montar Automaticamente`;
8. Clique em `[Ok]`;

<p align="center" width="100%"><img src="https://raw.githubusercontent.com/Luferat/MyGistImages/main/oracle/linux/05.png" alt="VM quase pronta"></p>

9. Clique em `[Ok]` da janela de "Configurações" para concluir.

Estamos com a VM preparada e no proximo documento vamos instalar o sistema visitante...
