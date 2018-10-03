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


