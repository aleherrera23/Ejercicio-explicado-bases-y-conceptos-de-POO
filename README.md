# Lo primero que se realiza es la definicion de una clase abstracta por medio de la cual se definira la estructura de un producto financiero, nombre que como se puede apreciar es el de la clase 
class ProductoFinanciero:
    def __init__(self, nombre, tipo):
        self.nombre = nombre
        self.tipo = tipo

    def obtener_informacion(self):
        pass

# Clase para representar un producto de inversión, como se ve mas adelante la clase de Producto Credito tambien heredara de la clase abstracta, o clase base llamada Producto Financiero
class ProductoInversion(ProductoFinanciero):
    def __init__(self, nombre, tipo, rendimiento):
        super().__init__(nombre, tipo)
        self.rendimiento = rendimiento

    def obtener_informacion(self):
        return f"El {self.tipo} de inversión {self.nombre} tiene un rendimiento esperado del {self.rendimiento}%."

class ProductoCredito(ProductoFinanciero):
    def __init__(self, nombre, tipo, tasa_interes):
        super().__init__(nombre, tipo)
        self.tasa_interes = tasa_interes

    def obtener_informacion(self):
        return f"El {self.tipo} de crédito {self.nombre} tiene una tasa de interés del {self.tasa_interes}%."

# Las funciones que se implementaran acontinuacion tienen los role de mostrar la info de un producto financiero y calcular las ganancias al vender un producto con parametros previamente definidos respectivamente. Ademas en esta funcion se ve reflejado el polimorfismo, debido a que contando con un mismo nombre y lista de parametros cada una de las instancias posteriores ejecuta su propia implementacion del metodo.
def mostrar_informacion(producto):
    print(producto.obtener_informacion())


def calcular_ganancias(cantidad):
    costo_adquisicion = 2500
    costo_venta = 3400
    ganancias_por_unidad = costo_venta - costo_adquisicion
    ganancias_totales = ganancias_por_unidad * cantidad
    return ganancias_totales

# en este punto se crean las instancias de productos financieros específicos, ademas de que fondo inversion y tarjeta credito son objetos de producto inversion y producto credito respectivamente.
fondo_inversion = ProductoInversion("Fondo de Inversión", "producto", 5)
tarjeta_credito = ProductoCredito("Tarjeta de Crédito", "producto", 15)

# aqui se realiza una llamada a la función mostrar informacion con diferentes tipos de productos financieros
mostrar_informacion(fondo_inversion)   # Imprime "El producto de inversión Fondo de Inversión tiene un rendimiento esperado del 5%."
mostrar_informacion(tarjeta_credito)  # Imprime "El producto de crédito Tarjeta de Crédito tiene una tasa de interés del 15%."

cantidad = int(input("Para determinar las ganancias generadas ingrese la cantidad de productos vendidos (de 1 a 50): "))
if cantidad < 1 or cantidad > 50:
    print("Cantidad inválida. Debe ser un número entre 1 y 50.")
else:
    ganancias = calcular_ganancias(cantidad)
    print(f"Las ganancias por vender {cantidad} productos son: {ganancias} COP.")
