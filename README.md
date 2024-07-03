# AlgoritmosDeOrdenamientos
Los métodos de ordenamiento son algoritmos diseñados para organizar los registros de una tabla en un orden secuencial específico basado en algún criterio. Estos métodos pueden ser iterativos o recursivos dependiendo de su naturaleza y forma de ejecución. A continuación, se presentan algunos de los métodos de ordenamiento más comunes, junto con sus características principales y ejemplos en Python:

# 1. Método de Ordenamiento de la Burbuja (BubbleSort)
El Ordenamiento de Burbuja es un algoritmo simple que compara cada elemento de la lista con el siguiente, intercambiándolos si están en el orden incorrecto. Este proceso se repite hasta que no se necesiten más intercambios, indicando que la lista está ordenada.

python
Copiar código
from random import sample

lista = list(range(100))
vectorbs = sample(lista, 8)

def bubblesort(vectorbs):
    print("El vector a ordenar es:", vectorbs)
    n = len(vectorbs)
    
    for i in range(n-1): 
        for j in range(0, n-i-1):
            if vectorbs[j] > vectorbs[j+1]:
                vectorbs[j], vectorbs[j+1] = vectorbs[j+1], vectorbs[j]
                
    print("El vector ordenado es:", vectorbs)

![Bubble-sort](https://github.com/MatiViglianco/AlgoritmosDeOrdenamientos/assets/105290418/c9def85a-1ec3-4243-a201-4b6555ba4ab0)

https://www.youtube.com/watch?v=Q7MAO9h3oV4


# 2. Método de Ordenamiento por Selección (SelectionSort)
Este método busca el elemento menor en la lista no ordenada y lo coloca al principio. Luego, repite el proceso con los elementos restantes.

python
Copiar código
from random import sample

lista = list(range(100))
vectorselect = sample(lista, 8)

def selectionsort(vectorselect):
    print("El vector a ordenar es:", vectorselect)
    n = len(vectorselect)
    
    for i in range(n):
        minimo = i
        for j in range(i+1, n):
            if vectorselect[minimo] > vectorselect[j]:
                minimo = j
        vectorselect[i], vectorselect[minimo] = vectorselect[minimo], vectorselect[i]
    
    print("El vector ordenado es:", vectorselect)

![Selection_sort_animation](https://github.com/MatiViglianco/AlgoritmosDeOrdenamientos/assets/105290418/afc760cd-72f7-4751-9d1e-3a6b4911675f)

# 3. Método de Ordenamiento por Inserción (InsertionSort)
Este método recorre la lista y toma cada elemento actual, insertándolo en la posición correcta en la parte ya ordenada de la lista.

python
Copiar código
from random import sample

lista = list(range(100))
vectorins = sample(lista, 8)

def insertionsort(vectorins):
    print("El vector a ordenar con inserción es:", vectorins)
    n = len(vectorins)
    
    for i in range(1, n):
        elemento = vectorins[i]
        j = i - 1
        while j >= 0 and elemento < vectorins[j]:
            vectorins[j + 1] = vectorins[j]
            j -= 1
        vectorins[j + 1] = elemento
        
    print("El vector ordenado con inserción es:", vectorins)

![Insertion_sort_animation](https://github.com/MatiViglianco/AlgoritmosDeOrdenamientos/assets/105290418/e3b0c1d0-843c-4644-b57d-53fb0a6b8135)

# 4. Método de Ordenamiento Shell (ShellSort)
El método Shell es una mejora del InsertionSort. Compara elementos separados por un intervalo y reduce este intervalo en cada iteración hasta finalizar con un InsertionSort simple.

python
Copiar código
from random import sample

lista = list(range(100))
vectorshell = sample(lista, 8)

def shellsort(vectorshell):
    print("El vector a ordenar con shell es:", vectorshell)
    n = len(vectorshell)
    gap = n // 2
    
    while gap > 0:
        for i in range(gap, n):
            temp = vectorshell[i]
            j = i
            while j >= gap and vectorshell[j - gap] > temp:
                vectorshell[j] = vectorshell[j - gap]
                j -= gap
            vectorshell[j] = temp
        gap //= 2
        
    print("El vector ordenado con shell es:", vectorshell)

![Sorting_shellsort](https://github.com/MatiViglianco/AlgoritmosDeOrdenamientos/assets/105290418/344e7e3c-7f24-42e2-9915-4a5498f5e565)


# 5. Método de Ordenamiento por Mezcla (MergeSort)
El MergeSort divide la lista en dos sublistas, las ordena recursivamente y luego las mezcla en una sola lista ordenada.

python
Copiar código
from random import sample

lista = list(range(100))
vectormerge = sample(lista, 8)

def mergesort(vectormerge):
    print("El vector a ordenar con merge es:", vectormerge)

    def merge_sort(vectormerge):
        if len(vectormerge) > 1:
            mid = len(vectormerge) // 2
            left = vectormerge[:mid]
            right = vectormerge[mid:]
            
            merge_sort(left)
            merge_sort(right)
            
            i = j = k = 0
            
            while i < len(left) and j < len(right):
                if left[i] < right[j]:
                    vectormerge[k] = left[i]
                    i += 1
                else:
                    vectormerge[k] = right[j]
                    j += 1
                k += 1
                
            while i < len(left):
                vectormerge[k] = left[i]
                i += 1
                k += 1
                
            while j < len(right):
                vectormerge[k] = right[j]
                j += 1
                k += 1
                
    merge_sort(vectormerge)
    print("El vector ordenado con merge es:", vectormerge)

![Merge_sort_animation](https://github.com/MatiViglianco/AlgoritmosDeOrdenamientos/assets/105290418/2554f01f-e602-486f-9be9-9153ba6b6a2a)

# 6. Método de Ordenamiento Rápido (QuickSort)
El QuickSort selecciona un elemento como pivote y divide la lista en dos sublistas alrededor del pivote. Este proceso se repite recursivamente.

python
Copiar código
from random import sample

lista = list(range(100))
vectorquick = sample(lista, 8)

def quicksort(vectorquick):
    print("El vector a ordenar con quick es:", vectorquick)
    
    def partition(vectorquick, low, high):
        pivot = vectorquick[low]
        left = low + 1
        right = high
        
        while True:
            while left <= right and vectorquick[right] >= pivot:
                right -= 1
            while left <= right and vectorquick[left] <= pivot:
                left += 1
            if left <= right:
                vectorquick[left], vectorquick[right] = vectorquick[right], vectorquick[left]
            else:
                break
                
        vectorquick[low], vectorquick[right] = vectorquick[right], vectorquick[low]
        return right
    
    def quick_sort(vectorquick, low, high):
        if low < high:
            pi = partition(vectorquick, low, high)
            quick_sort(vectorquick, low, pi-1)
            quick_sort(vectorquick, pi+1, high)
            
    quick_sort(vectorquick, 0, len(vectorquick)-1)
    print("El vector ordenado con quick es:", vectorquick)


![Quicksort](https://github.com/MatiViglianco/AlgoritmosDeOrdenamientos/assets/105290418/adff1929-b073-4217-9572-b3089d265a63)

# 7. Método de Ordenamiento por Montones (HeapSort)
El HeapSort construye un montón a partir de la lista y luego extrae los elementos del montón uno por uno para formar la lista ordenada.

python
Copiar código
from random import sample

lista = list(range(100))
vectorheap = sample(lista, 8)

def heapsort(vectorheap):
    print("El vector a ordenar con heap es:", vectorheap)
    n = len(vectorheap)
    
    def heapify(vectorheap, n, i):
        largest = i
        left = 2 * i + 1
        right = 2 * i + 2
        
        if left < n and vectorheap[i] < vectorheap[left]:
            largest = left
        if right < n and vectorheap[largest] < vectorheap[right]:
            largest = right
        if largest != i:
            vectorheap[i], vectorheap[largest] = vectorheap[largest], vectorheap[i]
            heapify(vectorheap, n, largest)
    
    for i in range(n//2 - 1, -1, -1):
        heapify(vectorheap, n, i)
    
    for i in range(n-1, 0, -1):
        vectorheap[i], vectorheap[0] = vectorheap[0], vectorheap[i]
        heapify(vectorheap, i, 0)
        
    print("El vector ordenado con heap es:", vectorheap)

![heapsort](https://github.com/MatiViglianco/AlgoritmosDeOrdenamientos/assets/105290418/e1f7ecf8-3c33-4b7a-b1d7-7d24b82b9c0a)


# 8. Método de Ordenamiento del Peine (CombSort)
El CombSort mejora el BubbleSort comparando elementos separados por una distancia mayor que uno y reduciendo esta distancia en cada iteración.

python
Copiar código
from random import sample

lista = list(range(100))
vectorcomb = sample(lista, 8)

def combsort(vectorcomb):
    print("El vector a ordenar con comb es:", vectorcomb)
    n = len(vectorcomb)
    gap = n
    swapped = True
    
    while gap != 1 or swapped:
        gap = max(1, int(gap / 1.25))
        swapped = False
        
        for i in range(n - gap):
            if vectorcomb[i] > vectorcomb[i + gap]:
                vectorcomb[i], vectorcomb[i + gap] = vectorcomb[i + gap], vectorcomb[i]
                swapped = True
                
    print("El vector ordenado con comb es:", vectorcomb)

![Comb_sort](https://github.com/MatiViglianco/AlgoritmosDeOrdenamientos/assets/105290418/aa9bd0e8-ca0c-417d-b7aa-96458dd6db7a)


# 9. Método de Ordenamiento Bidireccional (CocktailSort)
El CocktailSort es una variación del BubbleSort que ordena la lista en ambas direcciones, hacia adelante y hacia atrás, en cada pasada.

python
Copiar código
from random import sample

lista = list(range(100))
vectorcocktail = sample(lista, 8)

def cocktailsort(vectorcocktail):
    print("El vector a ordenar con cocktail es:", vectorcocktail)
    n = len(vectorcocktail)
    swapped = True
    start = 0
    end = n - 1
    
    while swapped:
        swapped = False
        for i in range(start, end):
            if vectorcocktail[i] > vectorcocktail[i + 1]:
                vectorcocktail[i], vectorcocktail[i + 1] = vectorcocktail[i + 1], vectorcocktail[i]
                swapped = True
        if not swapped:
            break
        swapped = False
        end -= 1
        for i in range(end - 1, start - 1, -1):
            if vectorcocktail[i] > vectorcocktail[i + 1]:
                vectorcocktail[i], vectorcocktail[i + 1] = vectorcocktail[i + 1], vectorcocktail[i]
                swapped = True
        start += 1
        
    print("El vector ordenado con cocktail es:", vectorcocktail)

![sort-graph](https://github.com/MatiViglianco/AlgoritmosDeOrdenamientos/assets/105290418/405c0e6d-3d24-4ee2-b9e2-b983e3cde8e8)

# Eficiencia de rendimiento
M1 = Máquina 1 (1 nucleo, 1GB de RAM) M2 = Máquina 2 (2 nucleos, 2GB de RAM)

Tenemos el siguiente gráfico:
![allAlgorithms_M1_M2](https://github.com/MatiViglianco/AlgoritmosDeOrdenamientos/assets/105290418/37bb68cd-c51c-48ec-86ea-e538ec9cf326)
La gráfica compara el rendimiento de distintos algoritmos de ordenamiento en dos máquinas con diferentes configuraciones de hardware. Las conclusiones clave son:

## Rendimiento General:
M2, con más núcleos y memoria, generalmente tiene un mejor rendimiento que M1.
## Escalabilidad de Algoritmos:
Algoritmos como MergeSort y QuickSort muestran una menor diferencia en el rendimiento entre las dos máquinas, lo que sugiere que escalan mejor con el aumento del tamaño de la lista.
## Impacto del Hardware:
Algoritmos más simples como BubbleSort e InsertionSort se ven más afectados por las limitaciones del hardware, mostrando una mayor diferencia en el tiempo de ejecución entre M1 y M2.
Estas observaciones pueden ayudar a elegir el algoritmo de ordenamiento más adecuado según la configuración del hardware y el tamaño de los datos a procesar.


# Comparación según la cantidad de iteraciones e intercambios del algoritmo
Otra forma de comparar los algoritmos de ordenamiento es analizandolos según la cantidad de comparaciones e intercambios que deben realizar para cumplir su cometido, hemos analizado algunos de ellos con la calculadora correspondiente y encontrado de esta forma, los datos para realizar la siguiente tabla y gráfico:

![MetodosdeOrdenamiento](https://github.com/MatiViglianco/AlgoritmosDeOrdenamientos/assets/105290418/e4fc04d2-c974-4da9-97b0-cc12219a6f87)

## Eficiencia en Iteraciones:
Algunos algoritmos, como el Ordenamiento Rápido (QuickSort) y el Ordenamiento por Mezcla (MergeSort), requieren menos iteraciones comparados con métodos tradicionales como el Ordenamiento de Burbuja.
## Intercambios Minimizados:
El Ordenamiento por Selección y el Ordenamiento Shell destacan por minimizar la cantidad de intercambios necesarios para ordenar los elementos.
## Optimización de Burbuja:
El Ordenamiento de Burbuja Mejorado y el Ordenamiento de Peine (CombSort) son variantes que buscan mejorar la eficiencia del Ordenamiento de Burbuja tradicional.
## Comparación Visual:
La gráfica proporciona una comparación visual rápida de la eficiencia de los algoritmos en términos de iteraciones e intercambios, facilitando la selección del método más adecuado según el caso de uso.

Estos puntos resaltan las diferencias clave en la eficiencia de los algoritmos de ordenamiento y pueden servir como base para una presentación o análisis más detallado.

# Aqui tienes una pagina interactiva con varios algoritmos:
https://visualgo.net/en/sorting

Estos métodos de ordenamiento abarcan una variedad de técnicas y principios algorítmicos que son útiles en diferentes contextos de programación y análisis de datos. Cada uno tiene sus propias ventajas y desventajas en términos de complejidad temporal y espacial, por lo que es importante elegir el método adecuado según la situación específica.
