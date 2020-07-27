# Telas

### Mantendo o conteúdo longe da barra de notificação

> Todas as telas devem ter seu conteúdo disposto apenas abaixo da barra de notificação.

A solução mais prática seria a utilização do componente &lt;SafeAreaView&gt;, porém, ele aparentemente só funciona de modo decente em aparelhos iOS.

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
<KeyboardAvoidingView style={[estiloExcecao.container, estilos.tela]}>

</KeyboardAvoidingView>
```

### 

