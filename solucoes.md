---
description: >-
  Soluções de problemas de front-end e UI/UX design que interferem na
  usabilidade do produto final.
---

# Soluções

## Mantendo o conteúdo longe da barra de notificação by Juan

> Todas as telas devem ter seu conteúdo disposto apenas abaixo da barra de notificação.

A solução mais prática seria a utilização do componente `<SafeAreaView>`, porém, ele aparentemente só funciona de modo decente em aparelhos iOS.

A solução para aparelhos Android é:

```javascript
const headerHeight = StatusBar.currentHeight;

const estiloExcecao = StyleSheet.create({
	container: {
		paddingTop: headerHeight,
	},
});

```

Onde `container`será utilizado como valor da prop style de qualquer que seja o componente utilizado para encapsular todo o conteúdo da página em questão.

Exemplo:

```javascript
<KeyboardAvoidingView style={[estiloExcecao.container]}>

</KeyboardAvoidingView>
```

## Mantendo o teclado fora dos inputs de formulário

Problema clássico de formulários em mobile: sobreposição do teclado aos inputs do formulário quando esses ganham foco para serem preenchidos.

Para corrigir esse problema, nas telas de formulários, utiliza-se a tag `<KeyboardAvoidingView>` para encapsular o conteúdo das telas que contém formulários.

Por motivos de como esse componente foi construído, é necessário utilizar um pouco de flexbox para que ele funcione corretamente. E depois, devido a como flexbox funciona, é necessário utilizar um pouco mais de flexbox pra fazer com que tudo fique no seu devido lugar k

### Exemplo de Implementação

```javascript
<KeyboardAvoidingView style={[estiloExcecao.container, estilos.tela]}>
			<ScrollView style={estilos.telaInterior}>
			
			</ScrollView>
</KeyboardAvoidingView>
```

Utilizar `ScrollView` dentro de `KeyboardAvoingView` é a uma implementação melhor do que utilizar qualquer outro componente, o `ScrollView` automaticamente "scroll" a tela para colocar o input que está em foco \(sendo preenchido ou clicado\) no topo da tela.

### Estilização

```javascript
tela: tailwind("bg-white flex-1"),
telaInterior: tailwind("flex-1")
```

_Obs: tornar o componente KeyboardAvoidingView funcional é a única razão pela qual tela interior e tela coexistem._

\_\_

