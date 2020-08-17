---
description: >-
  Imagens pequenas que passam uma mensagem de conteúdo, facilitando a
  compreensão do resultado de um clique.
---

# Ícones

#### Como devem ser utilizados?

Ícones devem ser utilizados majoritariamente em botões/situações de toque, nas seguintes situações:

* Botões de ícone - botões em que todo o conteúdo é um ícone.
* Botões com ícones - botões em que o conteúdo é um ícone e uma palavra que ajuda na compreensão da função engatilhada.
* Em componentes terciários de tela que abrirão uma modal informativa. Por exemplo, botões de "precisa de ajuda?" ou de "está perdido?".

O uso de ícones para indicar informação só deve acontecer se previamente o ícone houver sido utilizado para indicar o mesmo conteúdo final.

#### Como não devem ser utilizados?

Ícones não-clicáveis \(utilizados para indicar informação\) não devem ser utilizados "coloridos" ou em "sistema". Devem ser utilizados da cor do texto que acompanham e indicam, para reduzir a chance de serem confundidos com uma área clicável.

## Implementação

Para utilizar ícones da maneira mais eficiente, substituímos os arquivos .png por arquivos de origem .svg.

Muitos são os benefícios de utilização de .svg em produção - [explicação sobre svg's e seus benefícios](https://www.w3schools.com/graphics/svg_intro.asp) - e nesse caso o principal deles é a possibilidade de personalização, eliminando o estorvo de manter 4 versões \(arquivos png\) para uma mesma imagem, simplesmente porque ela precisava estar em cores diferentes em telas diferentes do aplicativo.

Para fazer uso de svg's, no entanto, é necessário recorrer uma biblioteca \(react-native-svg\) pois o React Native não lida com elas por enquanto.

### Trecho SVG Original

```markup
<svg fill="none" viewBox="0 0 24 24" stroke="currentColor">
    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" 
        d="M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z">
    </path>
</svg>
```

### Trecho SVG Utilizado

A biblioteca renderiza os elementos SVG's com componentes que o React Native entende. _Por isso, a pasta ícones está cheia de arquivos .js e não de arquivos .svg._

```javascript
<Svg strokeWidth="1.5" height="100%" width="100%" viewBox="0 0 24 24" color="#718096">
			<Path stroke="currentColor" strokeLinecap="round" strokeLineJoin="round"
						d="M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z">
			</Path>
</Svg>
```

Para que do primeiro código, chegue-se ao segundo de forma a ser reconhecido pelo React Native, é necessário:

1. Substituir os componentes em minúscula \(por exemplo, paths e circle\) por componentes em maiúscula vindos da biblioteca react-native-svg \(por exemplo, Path e Circle.
2. Substituir as propriedades com hífen \(por exemplo, stroke-width\) por sua escrita em camelcase \(por exemplo, strokeWidth\).

> A propriedades stroke deve sempre existir no caso de ícones e ser sempre igual a "currentColor". Recomendo colocá-la no componente SVG e não nos subcomponentes \(por exemplo, um Path\).

Esse trecho de SVG editado, deve ser inserido em um arquivo de classe componente de onde será importado e utilizado.

#### Template de arquivo de SVG

> Inserir na pasta react/src/assets/icones

```javascript
import Svg, { Path } from "react-native-svg";
// Lembre-se de requisitar os componentes que irá utilizar apenas

import React from "react";
import { View, StyleSheet } from "react-native";

export default class /*Icone<definicao>*/ extends React.Component {
	render() {
		return (
			<View style={[StyleSheet.absoluteFill,{ alignItems: "center", justifyContent: "center" },]}>
				// Insira aqui o trecho de SVG com as devidas alterações para renderizção
			</View>
		);
	}
}
```

#### Importação do Ícone na página em que será utilizado

Levando em consideração o exemplo do Ícone Informação definido nas últimas seções.

```javascript
import IconeInformacao from "../assets/icons/IconeInformacao";
```

## Estilização

Os ícones são definidos para obedecerem um tamanho natural de 24px pela propriedade viewBox: "0 0 24 24", mas podem ocupar qualquer tamaho a que sejam submetidos sem sofrerem grandes deformações.

Devido as propriedades height:"100%" e width:"100%", elas sempre ocuparam todo o espaço disponível no componente que as encapsula.

Por exemplo:

```javascript
<View style={tailwind("h-8 w-8")}>
    <IconeMenu />
</View>
```

Nesse caso, o ícone menu ocupará todo o espaço equivalente a h-8 e w-8.

Esse trecho foi retirado de um botão de ícone - o ícone corresponde todo o seu conteúdo. A View presente encapsula apenas o ícone e é por sua vez encapsulada por um componente de toque que será responsável por dar "padding" ao ícone.

```javascript
<TouchableOpacity style={tailwind("w-10 h-10 p-1 bg-gray-200 rounded")}>
					// A classe p-1 garante que o ícone não irá tocar as bordas do botão
					<View style={tailwind("h-8 w-8")}>
										<IconeMenu />
					</View>
</TouchableOpacity>
```

## Ícones Coloridos

Muitos ícones aparecem no aplicativo em mais de uma cor e como citado previamente essa era a principal motivação para utilização de SVG's.

### Implementação

Para ícones multicoloridos, a solução é utilizar uma propriedade que indica o caso de uso em que o ícone está sendo requisitado. Na classe de declaração, essa propriedade modifica o valor da propriedade color do componente Svg.

```javascript
// ...

export default class IconeDespesa extends React.Component {
	constructor(props) {
		super(props);
		this.color = props.uso == "sistema" ? "#2A4365" : "#E53E3E";
	}
	
	// ...
}

```

### Estilização

Comumente os ícones são utilizados na cor primária azul \(o primeiro valor na análise ternária\) ou em sua versão colorida \(segundo valor na análise ternária\),

> Ao construir classes para novos ícones, favor checar a biblioteca de ícones já existentes e garantir que os valores utilizados para cores estão corretos. Para tal, verifique a sessão de ícones do arquivo Figma assets.

