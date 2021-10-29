#Projeto Desenvolvido por Rafaella Nunes e Livia Lavynia

# funcao para salvar os contatos em arquivo
def savecontacts(lista):
    archive = open("contatos.txt", "w")

    for contatos in lista:
        archive.write(f"{contatos['nome']}#{contatos['email']}#{contatos['telefone']}\n")

    archive.close()


# funcao para carregar contatos
def carregar():
    lista = list()
    try:
        archive = open("contatos.txt", "r")

        for a in archive.readlines():
            b = a.strip().split("#")
            contato = {'email': b[1],
                       'nome': b[0],
                       'telefone': b[2]
                       }
            lista.append(contato.copy())

        archive.close()
    except FileNotFoundError:
        pass

    return lista


# funcao para definir se o email ja esxite
def contact(lista, email):
    if len(lista) > 0:
        for contato in lista:
            if contato['email'] == email:
                return True

    return False


# Definindo funcoes secundarias
def add(lista):
    while True:
        email = input('Digite o e-mail do seu contato:  ')

        # garantia de que o email eh unico
        if not contact(lista, email):
            break
        else:
            print('E-mail ja cadastrado, tente novamente.')

    contato = {'email': email,
               'nome': input('Digite o nome do contato:  '),
               'telefone': input('Digite o numero de telefone do contato:  ')
               }
    lista.append(contato.copy())
    print(f'Contato {contato["nome"]} cadastrado com sucesso!')


def change(lista):
    if len(lista) > 0:
        email = input('Digite o email do contato que você deseja modificar: ')
        if contact(lista, email):
            print('O contato foi encontrado, essas são as informações cadastradas: ')
            for contato in (lista):
                if contato['email'] == email:
                    print('Nome: {}'.format(contato['nome']))
                    print('Email: {}'.format(contato['email']))
                    print('Telefone: {}'.format(contato['telefone']))
                    print('============\n')

                    print('== AVISO: não é permitido que o e-mail seja alterado! ==\n')
                    contato['nome'] = input('Digite o novo nome: ')
                    contato['telefone'] = input('Digite o novo número de telefone: ')

        else:
            print('Não há nenhum contato cadastrado com email: {}\n'.format(email))
    else:
        print('Nao ha contatos no sistema')


def delete(lista):
    if len(lista) > 0:
        email = input('Digite o email do contato que você deseja excluir: ')
        if contact(lista, email):
            print('O contato foi encontrado, essas são as informações cadastradas: ')
            for i, contato in enumerate(lista):
                if contato['email'] == email:
                    print('Nome: {}'.format(contato['nome']))
                    print('Email: {}'.format(contato['email']))
                    print('Telefone: {}'.format(contato['telefone']))
                    print('============\n')

                    del lista[i]
                    print('Contato excluído com sucesso!')
                    break
        else:
            print('Não há nenhum contato cadastrado com email: {}\n'.format(email))
    else:
        print('Nao ha contatos no sistema')


def search(lista):
    if len(lista) > 0:
        email = input('Digite o email do contato que você deseja buscar: ')
        if contact(lista, email):
            print('O contato foi encontrado, essas são as informações cadastradas: ')
            for contato in (lista):
                if contato['email'] == email:
                    print('Nome: {}'.format(contato['nome']))
                    print('Email: {}'.format(contato['email']))
                    print('Telefone: {}'.format(contato['telefone']))
                    print('============\n')
                    break

        else:
            print('Não há nenhum contato cadastrado com email: {}\n'.format(email))
    else:
        print('Nao ha contatos no sistema')


def listc(lista):
    if len(lista) > 0:
        for i, contato in enumerate(lista):
            print(f'Contato {i + 1}:')
            print(f'\tNome: {contato["nome"]}')
            print(f'\tNumero: {contato["telefone"]}')
            print(f'\tE-mail: {contato["email"]}')
            print('============')

    else:
        print('Nao ha contatos no sistema')


# --- definindo funcao principal ---
def main():
    lista = carregar()
    while True:
        print("--- Agenda de Contatos ---")
        print('Digite 1 para adicionar contato')
        print('Digite 2 para alterar contato')
        print('Digite 3 para excluir contato')
        print('Digite 4 para buscar contato')
        print('Digite 5 para listar contatos')
        print('Digite 6 para sair')
        aux = int(input('Digite a opção que você deseja:    '))
        if aux == 1:
            add(lista)
            savecontacts(lista)
        elif aux == 2:
            change(lista)
            savecontacts(lista)
        elif aux == 3:
            delete(lista)
            savecontacts(lista)
        elif aux == 4:
            search(lista)
        elif aux == 5:
            listc(lista)
        elif aux == 6:
            print('Você saiu do sistema')
            break
        else:
            print("Opção inválida!")


# --- chamando função principal ---
main()
