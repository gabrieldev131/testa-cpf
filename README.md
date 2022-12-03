# testa-cpf
programa que verificar a validade de um cpf
def f_limpa(cpf):
  novo = ""
  for i in range(len(cpf)):
    if (cpf[i] != "." and cpf[i] != "-"):
      novo += cpf[i]
def f_primeiroDV(c):
  mult = 10
  s = 0
  for i in range(len(c)):
    s += int(c[i])*mult #s = s + c[i]*mult
    mult = mult - 1 #mult -= 1
  resto = s % 11
  if (resto < 2):
    dv = 0
  else: 
    dv = 11 - resto
  return dv

def f_segundoDV(c):
  mult = 11
  s = 0
  for i in range(len(c)):
    s += int(c[i])*mult #s = s + c[i]*mult
    mult = mult - 1 #mult -= 1
  resto = s % 11
  if (resto < 2):
    dv = 0
  else: 
    dv = 11 - resto
  return dv

def f_testaDV(dv,d1,d2):
  if (dv == str(d1)+str(d2)):
    return True
  return False

def f_testaCPF(cpf):
  cpf = f_limpa(cpf)
  cpf2 = cpf[0:9]
  dv = cpf[9:]
  dv1 = f_primeiroDV(cpf2)
  dv2 = f_segundoDV(cpf2+str(dv1))
  return f_testaDV(dv,dv1,dv2)
  
def main():
  cpf = input()
  
  if (f_testaCPF(cpf)):
    print('CPF VÁLIDO')
  else:
    print('CPF INVÁLIDO')
  return 0

if __name__ == "__main__":
  main()
