# gerenciador-de-tarefas-java-console
import java.util.ArrayList;
import java.util.Scanner;

public class GerenciadorDeTarefas {

    static class Tarefa {
        String titulo;
        boolean concluida;

        Tarefa(String titulo) {
            this.titulo = titulo;
            this.concluida = false;
        }

        void marcarComoConcluida() {
            this.concluida = true;
        }

        @Override
        public String toString() {
            return "[ " + (concluida ? "X" : " ") + " ] " + titulo;
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        ArrayList<Tarefa> tarefas = new ArrayList<>();
        int opcao;

        do {
            System.out.println("\n=== GERENCIADOR DE TAREFAS ===");
            System.out.println("1 - Adicionar tarefa");
            System.out.println("2 - Listar tarefas pendentes");
            System.out.println("3 - Listar tarefas concluídas");
            System.out.println("4 - Marcar tarefa como concluída");
            System.out.println("0 - Sair");
            System.out.print("Escolha uma opção: ");
            opcao = scanner.nextInt();
            scanner.nextLine();

            switch (opcao) {
                case 1:
                    System.out.print("Digite o título da tarefa: ");
                    String titulo = scanner.nextLine();
                    tarefas.add(new Tarefa(titulo));
                    System.out.println("Tarefa adicionada com sucesso!");
                    break;
                case 2:
                    System.out.println("\n--- Tarefas Pendentes ---");
                    for (int i = 0; i < tarefas.size(); i++) {
                        if (!tarefas.get(i).concluida) {
                            System.out.println(i + " - " + tarefas.get(i));
                        }
                    }
                    break;
                case 3:
                    System.out.println("\n--- Tarefas Concluídas ---");
                    for (int i = 0; i < tarefas.size(); i++) {
                        if (tarefas.get(i).concluida) {
                            System.out.println(i + " - " + tarefas.get(i));
                        }
                    }
                    break;
                case 4:
                    System.out.print("Digite o índice da tarefa a concluir: ");
                    int indice = scanner.nextInt();
                    if (indice >= 0 && indice < tarefas.size()) {
                        tarefas.get(indice).marcarComoConcluida();
                        System.out.println("Tarefa marcada como concluída!");
                    } else {
                        System.out.println("Índice inválido.");
                    }
                    break;
                case 0:
                    System.out.println("Encerrando...");
                    break;
                default:
                    System.out.println("Opção inválida.");
            }
        } while (opcao != 0);

        scanner.close();
    }
}
