def computador_escolhe_jogada(n, m):
    if n <= m:
        return n
    else:
        return n % (m + 1)


def usuario_escolhe_jogada(n, m):
    while True:
        jogada = int(input("Quantas peças você vai tirar? "))
        if 1 <= jogada <= m and jogada <= n:
            return jogada
        else:
            print("Oops! Jogada inválida. Tente de novo.")


def partida():
    # Inicia uma partida do jogo NIM.

    n = int(input("Quantas peças? "))
    m = int(input("Limite de peças por jogada? "))

    vez_do_computador = False
    if n % (m + 1) == 0:
        print("Você começa!")
    else:
        print("Computador começa!")
        vez_do_computador = True

    while n > 0:
        if vez_do_computador:
            jogada = computador_escolhe_jogada(n, m)
            print("O computador tirou", jogada, "peças.")
        else:
            jogada = usuario_escolhe_jogada(n, m)
            n -= jogada
        print("Restam", n, "peças no tabuleiro.")
        vez_do_computador = not vez_do_computador

    if vez_do_computador:
        print("Você ganhou!")
    else:
        print("O computador ganhou!")


def campeonato():
    # Realiza um campeonato com três partidas.
    vitorias_usuario = 0
    vitorias_computador = 0

    for i in range(3):
        print("**** Rodada", i+1, "****")
        partida()
        if vez_do_computador:
            print("Vez do computador!")
            vitorias_usuario += 1
        else:
            vitorias_computador += 1

    print("**** Final do campeonato ****")
    print("Placar: Você {} X {} Computador")


if __name__ == "__main__":
    print("Bem-vindo ao jogo do NIM! Escolha:")
    print("1 - para jogar uma partida isolada")
    print("2 - para jogar um campeonato")

    opcao = int(input("Sua opção: "))

    if opcao == 1:
        partida()
    elif opcao == 2:
        campeonato()
