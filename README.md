# lista-sort
package main

import (
	"fmt"
	"sort"
)

func reverse(slice []float64) {
	for i, j := 0, len(slice)-1; i < j; i, j = i+1, j-1 {
		slice[i], slice[j] = slice[j], slice[i]
	}
}

func main() {
	var lista []float64
	var n int


	fmt.Print("¿Cuántos valores deseas ingresar en la lista? ")
	fmt.Scan(&n)


	for i := 0; i < n; i++ {
		var valor float64
		fmt.Printf("Ingresa el valor %d: ", i+1)
		fmt.Scan(&valor)
		lista = append(lista, valor)
	}


	sort.Float64s(lista)
	fmt.Println("Lista ordenada:", lista)


	reverse(lista)
	fmt.Println("Lista revertida:", lista)


	var nValor float64
	fmt.Print("Ingresa un valor a agregar a la lista: ")
	fmt.Scan(&nValor)
	lista = append(lista, nValor)
	fmt.Println("Lista después de agregar valor:", lista)


	var vBorrar float64
	fmt.Print("Ingresa el valor a borrar de la lista: ")
	fmt.Scan(&vBorrar)
	for i, v := range lista {
		if v == vBorrar {
			lista = append(lista[:i], lista[i+1:]...)
			break
		}
	}
	fmt.Println("Lista después de borrar valor:", lista)


	var bValor float64
	fmt.Print("Ingresa el valor a buscar en la lista: ")
	fmt.Scan(&bValor)
	encontrado := false
	for _, v := range lista {
		if v == bValor {
			encontrado = true
			break
		}
	}
	if encontrado {
		fmt.Println("Valor encontrado:", bValor)
	} else {
		fmt.Println("Valor no encontrado:", bValor)
	}
}
