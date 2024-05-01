# Trabalho
Trabalho 1 
from abc import ABC, abstractmethod

class Categoria:
    def __init__(self, id, nome):
        self.id = id
        self.nome = nome

class Produto(ABC):
    def __init__(self, modelo, cor, preco, categoria):
        self.modelo = modelo
        self.cor = cor
        self.preco = preco
        self.categoria = categoria

    def getInformacoes(self):
        return f"Modelo: {self.modelo}, Cor: {self.cor}, Preço: {self.preco}, Categoria: {self.categoria.nome}"

    @abstractmethod
    def cadastrar(self):
        pass

class Desktop(Produto):
    def __init__(self, modelo, cor, preco, categoria, potenciaDaFonte):
        super().__init__(modelo, cor, preco, categoria)
        self._potenciaDaFonte = potenciaDaFonte

    def getInformacoes(self):
        return super().getInformacoes() + f", Potência da Fonte: {self._potenciaDaFonte}"

    def getPotenciaDaFonte(self):
        return self._potenciaDaFonte

    def setPotenciaDaFonte(self, potencia):
        self._potenciaDaFonte = potencia

    def cadastrar(self):
        # Lógica para cadastrar um Desktop
        pass

class Notebook(Produto):
    def __init__(self, modelo, cor, preco, categoria, tempoDeBateria):
        super().__init__(modelo, cor, preco, categoria)
        self.__tempoDeBateria = tempoDeBateria

    def getInformacoes(self):
        return super().getInformacoes() + f", Tempo de Bateria: {self.__tempoDeBateria}"

    def getTempoDeBateria(self):
        return self.__tempoDeBateria

    def setTempoDeBateria(self, tempo):
        self.__tempoDeBateria = tempo

    def cadastrar(self):
        # Lógica para cadastrar um Notebook
        pass

# Testando as classes
if __name__ == "__main__":
    categoria1 = Categoria(1, "Eletrônicos")
    desktop1 = Desktop("Desktop 1", "Preto", 2500, categoria1, "500W")
    notebook1 = Notebook("Notebook 1", "Prata", 3500, categoria1, "8 horas")

    print(desktop1.getInformacoes())
    print(notebook1.getInformacoes())
