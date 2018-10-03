# Intents

Intents são ações no android que abre uma outra activity (do próprio app 
ou de outro app)

# Intents Explicítas

Intent explicíta é um intent em que você especifica qual Activity será 
iniciada. É usada quando for preciso abrir uma Activity do app.

```kotlin
val abreOutraActivity = Intent(this, OutraActivity::class.java)
startActivity(abreOutraActivity)
```

Você pode passar informações entre Activities com ``putExtra()``

O exemplo é com String, mas pode ser usado outros tipos de dados

```kotlin
val abreOutraActivity = Intent(this, OutraActivity::class.java)
abreOutraActivity.putExtra("nomeDoExtra", string_que_vou_passar)
startActivity(abreOutraActivity)
```

```kotlin
val myString: String? = intent.getStringExtra("nomeDoExtra")
// Conferir se é nula ao usar myString
```

Iniciar outra atividade não precisa ser algo unidirecional. Pode-se 
também 
iniciar outra atividade e receber um resultado de volta. Para receber um 
resultado, chame ``startActivityForResult()`` (em vez de 
``startActivity()``).

[Veja mais sobre Activites 
Results](https://developer.android.com/training/basics/intents/result)






