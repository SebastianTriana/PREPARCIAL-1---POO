# Taller: Modificadores de Acceso en Python

Este repositorio contiene la solución a los **20 ejercicios** del taller de Programación Orientada a Objetos en Python, enfocado en **modificadores de acceso, encapsulación, propiedades, herencia, composición y buenas prácticas**.

---

## 📚 Ejercicios

### 1) Opción múltiple
**Respuesta:** Las opciones **A, B y D** son accesibles.  
- A es público.  
- B es protegido, pero accesible.  
- C no es accesible (privado por convención).  
- D es accesible por cómo está escrito.  

---

### 2) `hasattr` en atributos privados
**Salida del programa:**
```
False
True
```

---

### 3) Verdadero/Falso
- a) **Falso**: los atributos en Python pueden accederse desde fuera.  
- b) **Falso**: el *name mangling* no hace imposible el acceso.  
- c) **Verdadero**: se necesita el nombre de la clase para acceder con *name mangling*.  

---

### 4) Herencia de atributos protegidos
Imprime:
```
abc
```

---

### 5) Ejecución de contadores
Imprime:
```
2
1
```

---

### 6) Uso de `__slots__`
El programa genera **error** porque `y` no está definido en `__slots__`.  

---

### 7) Refactor con atributo protegido
```python
class B:
    def __init__(self):
        self._dato = 99
```

---

### 8) `hasattr` y privados
**Salida:**
```
True
False
True
```

---

### 9) Acceso con *name mangling*
```python
class S:
    def __init__(self):
        self.__data = [1, 2]

    def size(self):
        return len(self.__data)

s = S()
print(s._S__data)  # Acceso con name mangling
```

---

### 10) Uso de `dir`
Devuelve `_D__a` porque `__a` fue renombrado internamente por *name mangling*.  

---

### 11) Cuenta con saldo no negativo
```python
class Cuenta:
    def __init__(self, saldo):
        self._saldo = 0
        self.saldo = saldo

    @property
    def saldo(self):
        return self._saldo

    @saldo.setter
    def saldo(self, value):
        if value >= 0:
            self._saldo = value
        else:
            print("El saldo no puede ser negativo")
```

---

### 12) Termómetro
```python
class Termometro:
    def __init__(self, temperatura_c):
        self._c = float(temperatura_c)

    @property
    def temperatura_f(self):
        return self._c * 9/5 + 32
```

---

### 13) Usuario con nombre validado
```python
class Usuario:
    def __init__(self, nombre):
        self._nombre = nombre

    @property
    def nombre(self):
        return self._nombre

    @nombre.setter
    def nombre(self, valor):
        if not isinstance(valor, str):
            raise TypeError("El nombre debe ser de tipo string")
        self._nombre = valor
```

---

### 14) Registro inmutable
```python
class Registro:
    def __init__(self):
        self.__items = []

    def add(self, x):
        self.__items.append(x)

    @property
    def items(self):
        return tuple(self.__items)
```

---

### 15) Motor con validación
```python
class Motor:
    def __init__(self, velocidad):
        self._velocidad = 0
        self.velocidad = velocidad

    @property
    def velocidad(self):
        return self._velocidad

    @velocidad.setter
    def velocidad(self, value):
        if 0 < value < 200:
            self._velocidad = value
        else:
            raise ValueError("La velocidad debe estar entre 0 y 200")
```

---

### 16) Uso de `_atributo` vs `__atributo`
- `_atributo`: indica que el atributo es **protegido**, se recomienda no modificarlo desde fuera, pero sigue accesible.  
- `__atributo`: indica que el atributo es **privado**, se aplica *name mangling* para ocultarlo mejor y evitar colisiones en herencia.  

---

### 17) Buffer inmutable
```python
class Buffer:
    def __init__(self, data):
        self._data = list(data)

    def get_data(self):
        return tuple(self._data)
```

---

### 18) Herencia con *name mangling*
```python
class A:
    def __init__(self):
        self.__x = 1

class B(A):
    def get(self):
        return self._A__x
```

---

### 19) Composición y fachada
```python
class _Repositorio:
    def __init__(self):
        self._datos = {}

    def guardar(self, k, v):
        self._datos[k] = v

    def _dump(self):
        return dict(self._datos)

class Servicio:
    def __init__(self):
        self.__repo = _Repositorio()

    def guardar(self, k, v):
        self.__repo.guardar(k, v)
```

---

### 20) ContadorSeguro
```python
class ContadorSeguro:
    def __init__(self, n=0):
        self._n = n

    def inc(self):
        self._n += 1
        self.__log()

    @property
    def n(self):
        return self._n

    def __log(self):
        print("tick")

c = ContadorSeguro(0)
c.inc()  # tick
c.inc()  # tick
print(c.n)  # 2
```

---

## ✨ Autor
**Sebastián Triana**
