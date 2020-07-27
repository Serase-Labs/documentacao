---
description: Guia de implementação e estilização de inputs.
---

# Input

Inputs são unidades de entrada de texto, a documentação para um formulário \(padrão formado por componentes funcionais e validável\) se encontra \(aqui\)\[Se não tem um link é porque eu ainda não escrevi hehe\]

#### Tipos de Input

* Inputs de texto: fornecidos como componentes nativos do React Native e mais frequentemente utilizados.
* Input de data: _a decidir._

## Input de Texto

### Anatomia





### Implementação

```javascript
<View style={[estilos.containerInput]}>
		<Text style={estilos.labelInput}>Conteúdo do Input</Text>
				<TextInput 
					style={estilos.input} 
					// ... props do Formik
					blurOnSubmit={true}
					keyboard={//tipo de teclado a ser utilizado}
					placeholder={//texto no interior do input}
					placeholderTextColor={"#A0AEC0"}/>

					{errors./*inputName*/ && (
						<Text style={estilos.errorInput}>
										{errors.//inputName}
						</Text>
					)}
</View>
```

### Estilização

```javascript
containerInput: tailwind("w-64 mb-2"),
labelInput: tailwind("text-gray-700 text-base font-bold mb-3"),
input: tailwind("border border-gray-500 rounded w-full py-2 px-3 text-gray-700 text-base"),
errorInput: tailwind("bg-red-100 border border-red-400 text-red-700 px-4 py-2 mt-2 rounded relative"),
```

