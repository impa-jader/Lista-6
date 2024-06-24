# Lista-6
"""1."""

def search_insert(l: list,n: int)-> int:
    r=0
    r_l=[0,len(l)-1] # lista de 'cotas' para o indice de n
    while l[r]!= n:
        if l[(r_l[1]+r_l[0])//2]==n:
            r=(r_l[1]+r_l[0])//2
            return r
        if r_l[0]==r_l[1]:
            if l[r_l[0]]>n:
                return r_l[0]
            else:
                return r_l[0]+1
        if l[(r_l[1]+r_l[0])//2]>n:
            r_l[1]= (r_l[1]+r_l[0])//2
        if l[(r_l[1]+r_l[0])//2]<n:
            """ Se o numero no indice médio de r_l for menor que t ele se torna a 'cota inferior' """
            if r_l[0]!= (r_l[1]+r_l[0])//2:
                r_l[0]= (r_l[1]+r_l[0])//2
            else:
                """A operação // pega o menor inteiro, assim em uma r_l de dois epentos, isso poderia acontecer:
                    quero: 6
                    r_l[1]=r_l[0]+1
                    l[r_l[0]]==5
                    l[r_l[1]]==7
                    como l[(r_l[1]+r_l[0])//2]==l[(r_l[0]+1+r_l[0])//2]==l[r_l[0]]==5
                    como 5<6, aconteceria de o a operação no if anterior criar um loop, onde r_l[0], fica sendo alterado para seu proprio valor 
                    assim, eu irei somar 1 para que r_l[0]==r_l[1]
                    """
                r_l[0]= (r_l[1]+r_l[0])//2 + 1
    

t = [ 0 , 2 , 3 , 4 , 7 ]
print(search_insert(t,3)) # 2
f = [ 0 , 2 ]
print(search_insert(f,1)) # 1
v = [ 0 , 2 ]
print(search_insert(v,3)) # 2
g = [7]
print(search_insert(g,3))# 0
h= [2]
print(search_insert(h,3))# 1 



"""2.
a)"""
def triangulo_pascal(n):
    linha=1
    linha_anterior=[]
    r=""
    for i in range(n):
        linha_str=""
        esta_linha=[]
        for k in range(i+1):
            if k==0 or k==i:
                linha_str+=" 1"
                esta_linha.append(1)
                continue
            else:
                linha_str+= f" {linha_anterior[k-1]+linha_anterior[k]}"
                esta_linha.append(linha_anterior[k-1]+linha_anterior[k])
        r+= f"{linha_str} \n"
        linha_anterior=esta_linha
    return r
    
print(triangulo_pascal(5))
"""b) 
A complexidade varia pois o primeiro laço for faz n operações, mas cada operação tem um numero maior de complexidade 
Assim perceba que a complexidade equivale a um grande a uma serie da forma 1+...+n= (n+1)*n*1/2=(n^2 +n)/2
Portanto a complexidade é O(n^2)"""

"""3
a) """

"""b)"""

"""c)"""

"""4""" # Falta os negativos
def dict_polinomio(pol: str):
    coisa=""
    lista_pol=[]
    for i in pol:
        if i== "+" or i== "-":
            lista_pol.append(coisa)
            coisa=""
        else:
            coisa+= i
    lista_pol.append(coisa)
    dict={}
    numeros=["0","1","2","3","4","5","6","7","8","9"]
    for k in lista_pol:
        grau_str=""
        coeficiente=1
        coeficiente_str=""
        marcador=0 # quando marcador for igual a um é pois ja definimos o coeficiente
        grau= 0
        for q in k:
            
            if marcador== 0 and q in numeros:
                coeficiente_str+=q
            if q not in numeros:
               marcador=1 
            if marcador!=0 and q in numeros:
                grau_str= q
            grau= int(marcador) # caso o marcador seja 1 e o grau_str não tenha nada então o grau é 1
            if coeficiente_str!="":
                coeficiente= float(coeficiente_str)
            if grau_str!="":
                grau= float(grau_str)
        dict[grau]= coeficiente
    return dict
    
print(dict_polinomio("21x^2+3x+1"))


"""5"""
def str_poly(pol: dict)-> str:
    r=""
    for k in list(pol.keys()):
        if k!=0:
            if pol[k]<0:
                r+=f"{pol[k]}x"
            else:
            r+=f"+{pol[k]}x"
            if k!=1:
            r+=f"^{k}"
        else:
        if pol[k]<0:
            r+=str(pol[k])
        else:
            r+=f"+{pol[k]}"
    return r
p={
    2: 20,
    1: -1,
    0:3
}
print(str_poly(p))
