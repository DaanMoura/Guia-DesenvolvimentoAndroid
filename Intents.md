# Intents

Intents são ações no android que abre uma outra activity (do próprio app 
ou de outro app)

# Intents Explícitas

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

[Veja mais sobre Activities 
Results](https://developer.android.com/training/basics/intents/result)

# Intent Implícitas

Intent Implícita é uma intent em que não se sabe qual app irá realizar.

Por exemplo, para abrir um site, pode ser aberto pelo Chrome, Firefox, ou 
qualquer outro navegador instalado no dispositívo. O que o programador 
precisa fazer é apenas pedir uma ação ao sistema (mandar email, telefonar, 
abir mapa, abrir site, tirar foto ... ), o resto o sistema irá gerenciar.

Exemplo de intent para mandar email:
```kotlin
fun composeEmail(addresses: Array<String>, subject: String, attachment: 
Uri) {
    val intent = Intent(Intent.ACTION_SEND).apply {
        type = "*/*"
        putExtra(Intent.EXTRA_EMAIL, addresses)
        putExtra(Intent.EXTRA_SUBJECT, subject)
        putExtra(Intent.EXTRA_STREAM, attachment)
    }
    if (intent.resolveActivity(packageManager) != null) {
        startActivity(intent)
    }
}
```

Dependendo da intent, pode ser necessário muito código (ex.: tirar foto 
com qualidade), adicionar 
[permissões](https://developer.android.com/guide/topics/permissions/overview) 
(telefonar), entre outros. Portanto é importante verificar a 
documentação do android ao adicionar uma intent implícita

### Uri

Cada intent explícita tem uma uri, que serve como um identificador e
contém informações úteis

Uma Uri tem esse formato:
```
[scheme:][//authority][path][?query][#fragment]
```

exmplos de uri:
```
mailto:java-net@java.sun.com
http://java.sun.com/j2se/1.3/docs/guide/index.html
news:comp.lang.java
```

[Veja mais sobre 
Uri](https://developer.android.com/reference/java/net/URI)

### Intent Filter

Para anunciar quais intents implícitos o aplicativo pode receber, declare 
um ou mais filtros de intents para cada um dos componentes do aplicativo 
com um elemento <intent-filter> no arquivo de manifesto.

Por exemplo, abaixo há uma declaração de atividade com um filtro de 
intents para receber um intent ACTION_SEND quando o tipo de dados for 
texto:

```xml
<activity android:name="ShareActivity">
    <intent-filter>
        <action android:name="android.intent.action.SEND"/>
        <category android:name="android.intent.category.DEFAULT"/>
        <data android:mimeType="text/plain"/>
    </intent-filter>
</activity>
```

[Saiba mais sobre Intent 
Filter](https://developer.android.com/guide/components/intents-filters)


