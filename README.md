# Projeto-inicial

# ====== CRIAR PASTA DO PROJETO ======
mkdir gerenciador_tarefas && cd gerenciador_tarefas

# ====== ARQUIVO PRINCIPAL ======
cat << 'EOF' > main.py
import os

ARQUIVO_TAREFAS = "tarefas.txt"

def carregar_tarefas():
    if not os.path.exists(ARQUIVO_TAREFAS):
        return []
    with open(ARQUIVO_TAREFAS, "r", encoding="utf-8") as f:
        return [linha.strip() for linha in f.readlines()]

def salvar_tarefas(tarefas):
    with open(ARQUIVO_TAREFAS, "w", encoding="utf-8") as f:
        for tarefa in tarefas:
            f.write(tarefa + "\n")

def adicionar_tarefa():
    tarefa = input("Digite a nova tarefa: ")
    tarefas.append(tarefa)
    salvar_tarefas(tarefas)
    print("✅ Tarefa adicionada!")

def listar_tarefas():
    if not tarefas:
        print("📂 Nenhuma tarefa encontrada.")
        return
    print("\n📋 Lista de Tarefas:")
    for i, tarefa in enumerate(tarefas, start=1):
        print(f"{i}. {tarefa}")

def remover_tarefa():
    listar_tarefas()
    try:
        indice = int(input("Digite o número da tarefa a remover: ")) - 1
        if 0 <= indice < len(tarefas):
            removida = tarefas.pop(indice)
            salvar_tarefas(tarefas)
            print(f"❌ Tarefa '{removida}' removida!")
        else:
            print("⚠ Número inválido.")
    except ValueError:
        print("⚠ Entrada inválida.")

# Programa principal
tarefas = carregar_tarefas()

while True:
    print("\n=== GERENCIADOR DE TAREFAS ===")
    print("1 - Adicionar tarefa")
    print("2 - Listar tarefas")
    print("3 - Remover tarefa")
    print("0 - Sair")

    opcao = input("Escolha uma opção: ")

    if opcao == "1":
        adicionar_tarefa()
    elif opcao == "2":
        listar_tarefas()
    elif opcao == "3":
        remover_tarefa()
    elif opcao == "0":
        print("👋 Saindo...")
        break
    else:
        print("⚠ Opção inválida.")
EOF

# ====== README ======
cat << 'EOF' > README.md
# Gerenciador de Tarefas (Python)

Um simples gerenciador de tarefas para rodar no terminal.

## Funcionalidades
- Adicionar novas tarefas
- Listar tarefas
- Remover tarefas
- Salvar tudo em `tarefas.txt`

## Como usar
1. Clone o repositório:
   ```bash
   git clone https://github.com/seuusuario/gerenciador_tarefas.git
