
menu = """

[d] Depositar
[s] Sacar
[e] Extrato
[q] Sair

=> """

saldo = 2000
limite = 500
extrato = ""
numero_saques = 0
LIMITE_SAQUES = 3

while True:

    opcao = input(menu)

    if opcao == "d":
        valor = float(input("Qual o valor que deseja depositar: "))

        if valor > 0:
            saldo += valor
            extrato += f"Depósito: R$ {valor:.2f}\n "
            print("Valor depositado com sucesso.")

        else:
            print("O valor informado é inválido.")

    elif opcao == "s":
        valor = float(input("Qual o valor que deseja sacar: "))

        excedeu_saldo = valor > saldo
        print("Valor sacado com sucesso.")

        excedeu_limite = valor > limite

        excedeu_saques = numero_saques >= LIMITE_SAQUES

        if excedeu_saldo:
            print("Você não tem saldo suficiente na conta.")

        elif excedeu_limite:
         print("O valor do saque excedeu o limite de saque por dia. ")

        elif excedeu_saques:
           print("Número máximo de saques exedido por dia.")


        elif valor > 0:
            saldo -= valor
            extrato += f"Saque: R$ {valor:.2f}\n"
            numero_saques += 1

        else:
            print("Operação não pode ser realizada, o valor informado é invalido.")  

    elif opcao == "e":
        print("\n================ EXTRATO ================")
        print("Não foram realizadas movimentações." if not extrato else extrato)
        print(f"\nSaldo: R$ {saldo:.2f}")
        print("==========================================")

    elif opcao == "q":
        break

    else:
        print("Operação inválida, por favor selecione novamente a operação desejada.")
