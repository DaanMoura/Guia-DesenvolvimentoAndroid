# RecyclerView

RecyclerView é uma maneira de exibir vários itens na tela sem carregar 
todos os itens, apenas os que vão ser exibidos na tela.

Os exemplos são do app Contatinhos.

Para isso deve ser criado um arquivo de layout, 
``res/layout/filename.xml``, para criar o layout de um elemento.

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="64dp"
    android:id="@+id/container">

    <TextView
        android:id="@+id/tvNome"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:gravity="center_vertical"
        android:textSize="20sp"
        android:layout_marginLeft="16dp"
        android:layout_marginRight="16dp"
        android:text="Nome"/>

</LinearLayout>
```

Colocar a RecyclerView no layout da ListaActivity:

```xml
<android.support.v7.widget.RecyclerView
	android:id="@+id/rvContatinhos"
	android:layout_width="match_parent"
	android:layout_height="match_parent" />
```

Depois é preciso criar uma classe adapter que pede uma lista como 
parâmetro:

```kotlin
package my.package.contatinhos

import android.content.Context
import android.support.v7.widget.RecyclerView
import android.view.View
import android.view.ViewGroup
import android.view.LayoutInflater
import kotlinx.android.synthetic.main.contatinho_item_lista.view.*

class ContatinhoAdapter(val contatinhos: List<String>)
    : RecyclerView.Adapter<ContatinhoAdapter.ViewHolder>() {

    override fun onCreateViewHolder(parent: ViewGroup, viewType: Int): 
ViewHolder {
        val view = 
LayoutInflater.from(parent.context).inflate(R.layout.contatinho_item_lista, 
parent, false)
        return ViewHolder(view)
    }

    override fun getItemCount(): Int {
        return contatinhos.size
    }

    override fun onBindViewHolder(holder: ViewHolder, position: Int) {
        holder.bindView(contatinhos[position])
    }

    class ViewHolder(itemView: View) : RecyclerView.ViewHolder(itemView) {

        fun bindView(contatinhoNome: String) {
            itemView.tvNome.text = contatinhoNome
        }

    }
}
```

Depois basta instanciar um LayoutManager e setar alguns atributos da 
RecyclerView, desta forma:

```kotlin
val adapter = ContatinhoAdapter(listaContatinhos)
val layoutManager = LinearLayoutManager(this)

rvContatinhos.adapter = adapter
rvContatinhos.LayoutManager = layoutManager
```
É possivel personalizar o 
[LayoutManager](https://developer.android.com/reference/android/support/v7/widget/LinearLayoutManager)
e 
[RecyclerView](https://developer.android.com/reference/android/support/v7/widget/RecyclerView).
