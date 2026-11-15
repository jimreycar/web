# -Métodos-sobrecargados-

class Vehiculo:
    def __init__(self, marca, modelo, precio):
        self.marca = marca
        self.modelo = modelo
        self.precio = precio

    def calcular_costo(self, impuesto=0, descuento=0):
        """
        Calcula el costo final del vehículo.
        Permite aplicar impuestos y descuentos.
        """

        # Validar el precio
        if self.precio < 0:
            raise ValueError("El precio no puede ser negativo.")

        # Validar el impuesto
        if not isinstance(impuesto, (int, float)):
            raise TypeError("El impuesto debe ser numérico.")

        if not 0 <= impuesto <= 100:
            raise ValueError(
                "El impuesto debe estar entre 0 y 100."
            )

        # Validar el descuento
        if not isinstance(descuento, (int, float)):
            raise TypeError("El descuento debe ser numérico.")

        if not 0 <= descuento <= self.precio:
            raise ValueError(
                "El descuento debe estar entre 0 y el precio."
            )

        # Calcular el subtotal
        subtotal = self.precio - descuento

        # Calcular el impuesto
        valor_impuesto = subtotal * (impuesto / 100)

        # Calcular el costo final
        costo_total = subtotal + valor_impuesto

        return costo_total


# Crear un objeto de la clase Vehiculo
vehiculo = Vehiculo("Toyota", "Corolla", 80000000)

# 1. Calcular costo básico
costo_basico = vehiculo.calcular_costo()

# 2. Calcular costo con impuesto del 19 %
costo_impuesto = vehiculo.calcular_costo(impuesto=19)

# 3. Calcular costo con descuento
costo_descuento = vehiculo.calcular_costo(
    descuento=5000000
)

# 4. Calcular costo con impuesto y descuento
costo_completo = vehiculo.calcular_costo(
    impuesto=19,
    descuento=5000000
)


# Mostrar los resultados
print("SISTEMA DE COSTOS DE VEHÍCULOS")
print("--------------------------------")

print(f"Vehículo: {vehiculo.marca} {vehiculo.modelo}")

print(f"Costo básico: ${costo_basico:,.2f}")

print(f"Costo con impuesto: ${costo_impuesto:,.2f}")

print(f"Costo con descuento: ${costo_descuento:,.2f}")

print(
    f"Costo con impuesto y descuento: "
    f"${costo_completo:,.2f}"
)
