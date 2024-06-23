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



"""2."""
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
