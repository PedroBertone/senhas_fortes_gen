# senhas_fortes_gen
Gerador de senhas fortes for Python

import random
import string

def gerar_senha(tamanho=12):
    caracteres = string.ascii_letters + string.digits + string.punctuation
    senha = ''.join(random.choice(caracteres) for _ in range(tamanho))
    return senha

def main():
    try:
        qtd = int(input("Quantas senhas você quer gerar? "))
        tam = int(input("Qual o tamanho das senhas? (recom. 12+) "))
        salvar = input("Deseja salvar em arquivo? (s/n): ").lower()

        senhas = []
        for i in range(qtd):
            senha = gerar_senha(tam)
            print(f"Senha {i+1}: {senha}")
            senhas.append(senha)

        if salvar == 's':
            with open("senhas_geradas.txt", "w") as f:
                for s in senhas:
                    f.write(s + "\n")
            print("\n[✔] Senhas salvas em 'senhas_geradas.txt'")

    except ValueError:
        print("⚠️ Entrada inválida. Use apenas números inteiros.")

if __name__ == "__main__":
    main()
