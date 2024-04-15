from tkinter import ttk
from tkinter.ttk import*
from tkinter import*
from tkinter import messagebox

# cores
co0 = '#f0f3f5' # Preta
co1 = '#f0f3f5' #cinza
co2 = '#feffff' # branca
co3 = '#38576b' # valor
co4 = '#403d3d' # letra
co5 = '#6f9fbd' # azul
co6 = '#ef5350' # vermelha
co7 = '#93cd95' # verde

# criando janela
janela = Tk()
janela.title ("")
janela.geometry('500x450')
janela.configure(background=co1)
janela.resizable(width=FALSE, height=FALSE)
style = Style(janela)
style.theme_use("clam")


########### Frames ###########

frame_cima = Frame(janela, width=500, height=50, bg=co3, relief="flat")
frame_cima.grid(row=0, column=0, pady=1, padx=0, sticky=NSEW)

frame_baixo = Frame(janela, width=500, height=150, bg=co1, relief="flat")
frame_baixo.grid(row=1, column=0, pady=1, padx=0, sticky=NSEW)

frame_tabela = Frame(janela, width=500, height=248, bg=co2, relief="flat")
frame_tabela.grid(row=2, column=0, columnspan=2, padx=10, pady=1, sticky=NW)


# Configurando frame cima

c_nome = Label(frame_cima, text='Lista Telefonica', anchor=NE, font=('arial 20 bold'), bg=co3, fg=co2)
c_nome.place(x=5, y=5)

c_linha = Label(frame_cima, text='', width=500, anchor=NE, font=('arial 1'), bg=co1, fg=co1)
c_linha.place(x=0, y=45)


# Configurando frame com interação do Nome

l_nome = Label(frame_baixo, text='Nome *', anchor=NW, font=('Ivy 10'), bg=co1, fg=co4)
l_nome.place(x=10, y=20)
e_nome = Entry(frame_baixo, width=25, justify='left', relief=FLAT, font=('', 10), highlightthickness=1)
e_nome.place(x=80, y=20)

# Configurando frame com interação do Sexo da pessoa

l_sexo = Label(frame_baixo, text='Sexo *', anchor=NW, font=('Ivy 10'), bg=co1, fg=co4)
l_sexo.place(x=10, y=50)
c_sexo = Combobox(frame_baixo, width=27)
c_sexo['value'] = ('F', 'M',)
c_sexo.place(x=80, y=50)

# Configurando frame com interação com Telefone

l_tel = Label(frame_baixo, text='Telefone *', anchor=NW, font=('Ivy 10'), bg=co1, fg=co4)
l_tel.place(x=10, y=80)
e_tel = Entry(frame_baixo, width=25, justify='left', relief=FLAT, font=('', 10), highlightthickness=1)
e_tel.place(x=80, y=80)


# Configurando frame com interação com e-mail

l_email = Label(frame_baixo, text='E-mail *', anchor=NW, font=('Ivy 10'), bg=co1, fg=co4)
l_email.place(x=10, y=110)
e_email = Entry(frame_baixo, width=25, justify='left', relief=FLAT, font=('', 10), highlightthickness=1)
e_email.place(x=80, y=110)


# Configurando botão de Pesquisa

l_procurar = Button(frame_baixo, text='Procurar ', font=('Ivy 8 bold'), bg=co1, fg=co4, relief=RAISED, overrelief=RIDGE)
l_procurar.place(x=290, y=20)
e_procurar = Entry(frame_baixo, width=16, justify='left', relief=FLAT,  font=('', 10), highlightthickness=1)
e_procurar.place(x=365, y=21)

# Configurando botão de Ver Dados

l_dados = Button(frame_baixo, text='Ver Dados ', font=('Ivy 8 bold'), bg=co1, fg=co4, relief=RAISED, overrelief=RIDGE)
l_dados.place(x=290, y=50)

# Configurando botão de Adicionar

l_adicionar = Button(frame_baixo, text='Adicionar ', font=('Ivy 8 bold'), bg=co1, fg=co4, relief=RAISED, overrelief=RIDGE)
l_adicionar.place(x=400, y=50)

# Configurando botão de Atualizar

l_atualizar = Button(frame_baixo, text='Atualizar ', font=('Ivy 8 bold'), bg=co1, fg=co4, relief=RAISED, overrelief=RIDGE)
l_atualizar.place(x=400, y=80)


# Configurando botão de Deletar

l_deletar = Button(frame_baixo, text='Deletar ', font=('Ivy 8 bold'), bg=co1, fg=co4, relief=RAISED, overrelief=RIDGE)
l_deletar.place(x=400, y=110)


# Configurando frame tabela

dados_h = ['Nome', 'Sexo', 'Telefone', 'E-mail']

dados = [['Nicolas', 'M', '123', 'nico@gmail.com'], ['Maria', 'F', '321', 'maria@gmail.com']]

tree = ttk.Treeview(frame_tabela, selectmode='extended', columns=dados_h, show='headings')

vsb = ttk.Scrollbar(frame_tabela, orient='vertical', command=tree.yview)

hsb = ttk.Scrollbar(frame_tabela, orient='horizontal', command=tree.xview)

tree.configure(yscrollcommand=vsb.set, xscrollcommand=hsb.set)

tree.configure(yscrollcommand=vsb.set, xscrollcommand=hsb.set)

tree.grid(column=0, row=0, sticky='nsew')
vsb.grid(column=1, row=0, sticky='ns')
hsb.grid(column=0, row=1, sticky='ew')



tree.heading(0,text='Nome', anchor=NW)
tree.heading(1,text='Sexo', anchor=NW)
tree.heading(2,text='Telefone',anchor=NW)
tree.heading(3,text='E-mail',anchor=NW)

tree.column(0,width=120,anchor='nw')
tree.column(1,width=50,anchor='nw')
tree.column(2,width=100,anchor='nw')
tree.column(0,width=120,anchor='nw')

for item in dados:
    tree.insert('','end',values=item)

janela.mainloop()
