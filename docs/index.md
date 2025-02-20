
# herramientas para devs

For full documentation visit [mkdocs.org](https://www.mkdocs.org).

## A

### B

#### C

##### D


Some `code` goes here

### Plain codeblock

A plain codeblock

``` 
Some code here
def myfunction()
//JAJA
```

#### Code for a specific language

Some more code with the `py` at the start

```py
import tensorflow as tf
def whatever()
```

#### Código con título

```py title="bubble_sort.py"
def bubble_sort(items):
    for i in range(len(items)):
        for j in range(len(items) - 1 - i):
            if items[j] > items[j + 1]:
                items[j], items[j + 1] = items[j + 1], items[j]
```

#### Código con título + enumerado

```py linenums="1" title="bubble_sort.py"
def bubble_sort(items):
    for i in range(len(items)):
        for j in range(len(items) - 1 - i):
            if items[j] > items[j + 1]:
                items[j], items[j + 1] = items[j + 1], items[j]
```

#### Código con título + enumerado + highlights

```py hl_lines="2 3" linenums="1" title="bubble_sort.py"
def bubble_sort(items):
    for i in range(len(items)):
        for j in range(len(items) - 1 - i):
            if items[j] > items[j + 1]:
                items[j], items[j + 1] = items[j + 1], items[j]
```

## Icons and Emojis (font awesome se reusa a funcionar correctamente, no usar de preferencia)

:smile:

