/*
UFPB - Universidade Federal da Paraíba
Curso: Ciências da Computação
Aluno: João Henrique Alves de Sousa
Matricula: 20230012690
Disciplina: Estrutura de dados
Professor Gilberto Farias
Período: 2024.1
Atividade 4 Estrutura lista encadeada
*/
package main;

import java.util.Scanner;

public class Main {
    
    public static class FilaCircular {
    public int[] fila;
    public int nelementos;
    public int inicio;
    public int fim;
    public int tamMax;

    public FilaCircular() {
        inicio = 0;
        fim = -1;
        nelementos = 0;
        tamMax = 10;
        fila = new int[tamMax];
    }

    public void inserirNoFim(int elemento) {
        if (cheia()) {
            System.out.println("A fila esta cheia.Retorna erro!!!");
            return;
        }
        fim = (fim + 1) % tamMax;
        fila[fim] = elemento;
        nelementos++;
    }

    public int removerNoInicio() {
        if (vazia()) {
            System.out.println("A fila esa vazia.Retorna erro!!!");
            return -1;
        }
        int elementoRemovido = fila[inicio];
        inicio = (inicio + 1) % tamMax;
        nelementos--;
        return elementoRemovido;
    }

    public int consultarInicio() {
        if (vazia()) {
            System.out.println("A fila esta vazia.Retorna erro!!!");
            return -1;
        }
        return fila[inicio];
    }

    public boolean vazia() {
        return nelementos == 0;
    }

    public boolean cheia() {
        return nelementos == tamMax;
    }

    public void imprimirFila() {
        if (vazia()) {
            System.out.println("A fila esta vazia.\n");
            return;
        }
        System.out.print("Fila: ");
        for (int i = 0; i < nelementos; i++) {
            int indice = (inicio + i) % tamMax;
            System.out.print(fila[indice] + " ");
        }
        System.out.println("\n");
    }
}

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        FilaCircular fila = new FilaCircular();

        System.out.println("Digite o numero do caso de teste:");
        System.out.println("Caso 1: Fila vazia");
        System.out.println("Caso 2: Fila com tamanho maximo = 10, "
                + "numero de elementos = 5, fila = {1,2,3,4,5}");
        System.out.println("Caso 3: Fila cheia tamanho maximo = 10, "
                + "numero de elementos = 10, fila = {1,2,3,4,5,6,7,8,9,10}");
        int n = scanner.nextInt();
        while (n != 1 && n != 2 && n!=3) {
            System.out.println("Numero invalido, tente novamente:");
            n = scanner.nextInt();
        }

        switch (n) {
            case 1:
                System.out.println("\nA FILA ESTA VAZIA");
                break;
            case 2:
                fila.inserirNoFim(1);
                fila.inserirNoFim(2);
                fila.inserirNoFim(3);
                fila.inserirNoFim(4);
                fila.inserirNoFim(5);
                System.out.println("\nA fila contem elementos {1,2,3,4,5}");
                break;
            case 3:
                fila.inserirNoFim(1);
                fila.inserirNoFim(2);
                fila.inserirNoFim(3);
                fila.inserirNoFim(4);
                fila.inserirNoFim(5);
                fila.inserirNoFim(6);
                fila.inserirNoFim(7);
                fila.inserirNoFim(8);
                fila.inserirNoFim(9);
                fila.inserirNoFim(10);
                System.out.println("A fila contem elementos {1,2,3,4,5,6,7,8,9,10}");
            default:
                break;
        }
        
        System.out.println("Digite o numero que sera inserido no fim da fila: ");
        int p = scanner.nextInt();
        fila.inserirNoFim(p);
        System.out.println("Novo tamanho: " + fila.nelementos);
        fila.imprimirFila();
        
        System.out.println("Remover do inicio da fila" );
        System.out.print("Elemento removido: ");
        System.out.println(fila.removerNoInicio());
        System.out.println("Novo tamanho: " + fila.nelementos);
        fila.imprimirFila();
        
        System.out.print("Consultar inicio da fila: ");
        System.out.println(fila.consultarInicio());
        
        System.out.println("A fila esta vazia? " + fila.vazia());
        System.out.println("A fila esta cheia? " + fila.cheia());
        
    }
}
