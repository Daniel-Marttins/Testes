# passo a passo para resolver nosso desafio
import pyautogui
import pyperclip
import time

#Tempo/delays
pyautogui.PAUSE  = 1

# Passo 1: Entrar no sistema da empresa(Link do drive)
pyautogui.press('win')
pyautogui.write('microsoft')
pyautogui.press('enter')
pyperclip.copy('https://drive.google.com/drive/folders/149xknr9JvrlEnhNWO49zPcw0PW5icxga')
pyautogui.hotkey('ctrl','v')
pyautogui.press('enter')

#Carregar o sistema (demora 5 segundos)
time.sleep(5)

# Passo 2: Navegar no sistema(ate a pasta expotar)
# pode se usar dentro do mesmo parametro a função "clicks = qntd" para a qntd de vezes a se clicar 
pyautogui.click(x=339, y=270, clicks=2)


# Passo 3: Fazer o download da base de vendas
time.sleep(3)
pyautogui.click(x=361, y=325)
pyautogui.click(x=1010, y=160)
pyautogui.click(x=791, y=560)

time.sleep(3)

# Passo 4: Importar a base de vendas pro python
# Diretorio / caminho / local
# Armazenar o valor / Variavel
import pandas as pd

tabela = pd.read_excel(r'C:\Users\Daniel\Downloads\Vendas - Dez.xlsx')
print(tabela)

# Passo 5: Calcular o faturamento e quantidade de produtos vendidos(os indicadores)
faturamento = tabela['Valor Final'].sum()
qtde_produtos = tabela['Quantidade'].sum()

# Passo 6: Enviar email para diretoria
pyautogui.press('win')
pyautogui.write('microsoft')
pyautogui.press('enter')
pyperclip.copy('https://mail.google.com/mail/u/0/#inbox')
pyautogui.hotkey('ctrl','v')
pyautogui.press('enter')
time.sleep(6)
pyautogui.click(x=77, y=170)
pyautogui.write('lahorrytakashi@gmail.com')
pyautogui.press('tab')
pyautogui.press('tab')
pyautogui.write('Relatorio de vendas')
pyautogui.press('tab')

#escrever email
texto = f"""Prezados, Bom dia

O faturamento de ontem foi de R$: {faturamento}
A quantidade de produtos foi de: {qtde_produtos}

Abraços
Daniel Martins
"""
pyperclip.copy(texto)
pyautogui.hotkey('ctrl','v')

#enviar email
pyautogui.hotkey('ctrl','enter')


a = pyautogui.position()
