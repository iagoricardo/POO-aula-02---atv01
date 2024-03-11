class Produto:
  def __init__(self, nome, codigo, preco, quantidade):
      self.nome = nome
      self.codigo = codigo
      self.preco = preco
      self.quantidade = quantidade

  def __str__(self):
      return f"Nome: {self.nome}\nCódigo: {self.codigo}\nPreço: R${self.preco:.2f}\nQuantidade: {self.quantidade}"

  def adicionar_quantidade(self, quantidade):
      self.quantidade += quantidade

  def remover_quantidade(self, quantidade):
      if quantidade <= self.quantidade:
          self.quantidade -= quantidade
      else:
          print(f"Erro: Quantidade a remover ({quantidade}) maior que a quantidade disponível ({self.quantidade}).")

class Alimento(Produto):
  def __init__(self, nome, codigo, preco, quantidade, data_validade):
      super().__init__(nome, codigo, preco, quantidade)
      self.data_validade = data_validade

  def __str__(self):
      return super().__str__() + f"\nData de Validade: {self.data_validade}"

class Eletronico(Produto):
  def __init__(self, nome, codigo, preco, quantidade, marca, garantia):
      super().__init__(nome, codigo, preco, quantidade)
      self.marca = marca
      self.garantia = garantia

  def __str__(self):
      return super().__str__() + f"\nMarca: {self.marca}\nGarantia: {self.garantia}"

def main():
  # Criando alguns produtos
  produto1 = Produto("Caneta", "123", 2.50, 10)
  alimento1 = Alimento("Leite", "456", 3.00, 5, "2024-03-31")
  eletronico1 = Eletronico("Smartphone", "789", 1000.00, 2, "Samsung", "1 ano")

  # Imprimindo informações dos produtos
  print(f"**Produto 1:**\n{produto1}")
  print(f"\n**Alimento 1:**\n{alimento1}")
  print(f"\n**Eletrônico 1:**\n{eletronico1}")

  # Adicionando e removendo quantidades
  produto1.adicionar_quantidade(5)
  alimento1.remover_quantidade(3)
  eletronico1.remover_quantidade(1)

  # Imprimindo informações dos produtos após alterações
  print(f"\n**Produto 1 (após adicionar 5 unidades):**\n{produto1}")
  print(f"\n**Alimento 1 (após remover 3 unidades):**\n{alimento1}")
  print(f"\n**Eletrônico 1 (após remover 1 unidade):**\n{eletronico1}")

if __name__ == "__main__":
  main()
