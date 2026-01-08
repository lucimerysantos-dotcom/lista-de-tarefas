# Lista de tarefas

print("Bem-vindo ao app Lista de Tarefas. Escolha sua opção:")

#Padrão Singleton 

class ListaTarefas:
    _instancia = None

    def __new__(cls):
        if cls._instancia is None:
            cls._instancia = super().__new__(cls)
            cls._instancia.tarefas = []
        return cls._instancia


#Classes ações da lista

class AdicionarTarefa:
    def executar(self):
        nome = input("Nome da tarefa: ")
        descricao = input("Descrição: ")
        status = "Disponível"
        tarefa = {"nome": nome, "descricao": descricao, "status": status}
        ListaTarefas().tarefas.append(tarefa)
        print("Tarefa adicionada!")


class ListarTarefas:
    def executar(self):
        tarefas = ListaTarefas().tarefas
        if not tarefas:
            print("Nenhuma tarefa cadastrada.")
        else:
            for i, t in enumerate(tarefas):
                print(f"{i + 1} - {t['nome']} | {t['descricao']} | {t['status']}")


class RemoverTarefa:
    def executar(self):
        tarefas = ListaTarefas().tarefas
        numero = int(input("Número da tarefa para remover: "))
        tarefas.pop(numero - 1)
        print("Tarefa removida!")


class AlterarStatus:
    def executar(self):
        tarefas = ListaTarefas().tarefas
        numero = int(input("Número da tarefa: "))

        print("1 - Disponível")
        print("2 - Fazendo")
        print("3 - Feita")

        opcao = input("Escolha o novo status: ")

        if opcao == "1":
            tarefas[numero - 1]["status"] = "Disponível"
        elif opcao == "2":
            tarefas[numero - 1]["status"] = "Fazendo"
        elif opcao == "3":
            tarefas[numero - 1]["status"] = "Feita"

        print("Status atualizado!")


# Abstract Factory 
class FabricaTarefas:
    def criar_acao(self, opcao):
        if opcao == "1":
            return AdicionarTarefa()
        elif opcao == "2":
            return ListarTarefas()
        elif opcao == "3":
            return RemoverTarefa()
        elif opcao == "4":
            return AlterarStatus()
        else:
            return None


# Menu do app

fabrica = FabricaTarefas()

while True:
    print("\n=== LISTA DE TAREFAS ===")
    print("1 - Adicionar tarefa")
    print("2 - Listar tarefas")
    print("3 - Remover tarefa")
    print("4 - Alterar status")
    print("5 - Sair")

    opcao = input("Escolha: ")

    if opcao == "5":
        print("Até logo!")
        break

    acao = fabrica.criar_acao(opcao)

    if acao:
        acao.executar()
    else:
        print("Opção inválida!")
