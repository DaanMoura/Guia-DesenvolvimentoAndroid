# Glide

O Glide é uma biblioteca para carregar imagens no android facilmente.
Para usar deve-se importar o glide no ``build.graddle`` (module: app)

```gradle
apply plugin: 'kotlin-kapt'

dependencies {
  ...
  implementation 'com.github.bumptech.glide:glide:4.6.1'
  kapt 'com.github.bumptech.glide:compiler:4.6.1'
  ...
}
````

Criar uma classe ``GlideModule``

```kotlin
package my.package

import com.bumptech.glide.annotation.GlideModule
import com.bumptech.glide.module.AppGlideModule

@GlideModule
class GlideModule : AppGlideModule()
```

E para usar basta usar a função ``GlideApp`` desta forma:
```kotlin

GlideApp.with(this) //Context 
        .load(caminho_para_foto)) //Passa o caminho da foto ou URL
        .placeholder(caminho_para_placeholder) //Caso não seja possível carregar a foto, será carrega esse placeholder
        .circleCrop() //Tipo de corte (circleCrop é apenas um, de vários tipo) 
        .into(myImageView) //ImageView destino
````
