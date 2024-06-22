# Lista-6
"""1."""

def search_insert(l: list,n: int)-> int:
    r=0
    r_l=[0,len(l)-1]
    while l[r]!= n:
        if l[(r_l[1]+r_l[0])//2]>n:
            r_l[1]= (r_l[1]+r_l[0])//2
        if l[(r_l[1]+r_l[0])//2]<n:
            """ Se o numero no indice médio de r_l for menor que t ele se torna a 'cota inferior' """
            if r_l[0]!= (r_l[1]+r_l[0])//2:
                r_l[0]= (r_l[1]+r_l[0])//2
            else:
                """A operção // pega o menor inteiro, assim em uma r_l de dois epentos, isso poderia acontecer:
                    quero: 6
                    r_l[1]=r_l[0]+1
                    l[r_l[0]]==5
                    l[r_l[1]]==7
                    como l[(r_l[1]+r_l[0])//2]==l[(r_l[0]+1+r_l[0])//2]==l[r_l[0]]==5
                    como 5<6, aconteceria de o a operação no if anterior criar um loop, onde r_l[0], fica sendo alterado para seu proprio valor 
                    
                    """
                r_l[0]= (r_l[1]+r_l[0])//2 + 1
            if r_l[0]==r_l[1]:
                r=
            
        if l[(r_l[1]+r_l[0])//2]==n:
            r=(r_l[1]+r_l[0])//2
        return r
    

t = [ 0 , 2 , 3 , 4 , 7 ]
print(search_insert(t,3))
