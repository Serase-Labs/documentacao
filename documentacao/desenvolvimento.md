---
description: >-
  Passo a passo para iniciar o desenvolvimento e realizar commit no repositório
  (do jeito certo).
---

# ⌨ Desenvolvimento

### Passo 01: Clonando o repositório

Os repositórios do trabalho agora pertencem a uma organização no Github o que significa que `github.com/eumsmo/serase` não é mais o endereço para clonar o repositório.

O endereço [https://github.com/Serase-Labs](https://github.com/Serase-Labs) também não é a resposta porque não é possível clonar toda a organização.

Felizmente só um dos repositórios precisa ser clonado para desenvolvimento, o repositório com o nome do aplicativo, `serase`. 

* Clonando pelo GitKraken
  1. Abra o aplicativo
  2. 
* Clonando pela linha de comando 😎

  1. Navegue até a pasta onde quer que o aplicativo seja clonado

  _Obs: não crie uma pasta para clonar o aplicativo, o git cria uma pasta quando está clonando um repositório automaticamente._

  * Digite o seguinte comando:

     `shell git clone https://github.com/Serase-Labs/serase.git`

#### 🥳 Eba, clonei o repositório!

#### Eita, não tem nada no repositório... 😮

É porque você está na master, uma branch que só sera populada quando o aplicativo estiver em estados mais funcionais\(?\). Para quebrar códigos, favor se dirigir a branch da tela na qual você está trabalhando.

### Passo 02: Indo para a branch que eu quero

* Mudando de branch pelo GitKraken
  1. Clique duas vezes na branch que você deseja trabalhar
* Mudando de branch pela linha de comando 😎

  1. Navegue até o repositório do trabalho \(algo do tipo C:\ ...\serase\react\)
  2. Digite o comando

     `git checkout <nomedabranchdesejada>`

  Por exemplo: `git checkout dev` te levará para a branch dev.

### Passo 03: npm install

Como a pasta `node_modules`está inserida no `.gitignore` - por motivos de ninguém merece dar commit no node\_modules todo dia - antes de começar a rodar o aplicativo, após a clonagem é necessário rodar o comando que instalará todas as dependências.

Quando tiver certeza que a sua linha de comando está no repositório correto, rode o comando:

```bash
npm install
```

### Passo 04: Expo

Pra ter certeza que o aplicativo foi instalado corretamente, abre ele no Expo mesmo que você não queira visualizar ele agora.

Para tal, rode o comando:

```bash
expo start
```

Uma janela mágica do seu navegar se abrirá, nela, terá um QR Code que deve ser lido com o seu telefone, ou um que você roubou de alguém para fim de testes, usando o [aplicativo da Expo](https://play.google.com/store/apps/details?id=host.exp.exponent&hl=en).

Se tudo deu certo até aqui, agora você tem um aplicativo rodando no seu telefone.

Agora é só partir pro abraço, abre o VSCode e vrau neles ✌

👇 Mais abaixo tem uma sessão \(em desenvolvimento\) sobre possíveis erros durante o processo que pode ajudar caso depois de tudo isso você ainda não tenha conseguido rodar o aplicativo.

## ⚠Erros Comuns \(meus\)

### Rodar o npm install no repositório errado

O comando `npm install` não deve ser rodado na pasta do aplicativo e sim dentro da pasta react - independente da branch em que você se encontrar.

 Quando mesmo após rodar o comando você ainda não conseguir executar o aplicativo, procure pelo arquivo `package.json` e `package-lock.json` - esses são os arquivos responsáveis por contar para o `npm install` exatamente o que instalar - se eles não estão no caminho no qual você está rodando o caminho, ele não vai funcionar 😁

