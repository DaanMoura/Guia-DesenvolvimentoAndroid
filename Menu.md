# Menu
- É um arquivo ``res/menu/nome_do_menu.xml``.
- ``app:showAsAction``
	- Always
	- Never
	- ifRoom
		- se caber
- ``app:orderInCategory``
	- Prioridade

```kotlin
override fun onCreateOptionsMenu(menu: Menu): Boolean {
    val inflater: MenuInflater = menuInflater
    inflater.inflate(R.menu.game_menu, menu)
    return true
}

override fun onOptionsItemSelected(item: MenuItem): Boolean {
    // Handle item selection
    return when (item.itemId) {
        R.id.new_game -> {
            newGame()
            true
        }
        R.id.help -> {
            showHelp()
            true
        }
        else -> super.onOptionsItemSelected(item)
    }
}
```
