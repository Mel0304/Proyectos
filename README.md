
class Estudiante:
    
    def __init__(self, nombre, calificaciones, asistencia):
        self.nombre = nombre
        self.calificaciones = calificaciones
        self.asistencia = asistencia

    @classmethod
    def ingresar_datos(cls):
        nombre = input("Ingrese el nombre del estudiante: ")
        calificaciones = [float(x) for x in input("Ingrese las calificaciones del estudiante separadas por coma: ").split(",")]
        asistencia = int(input("Ingrese el número de días de asistencia del estudiante: "))
    
        return cls(nombre, calificaciones, asistencia)

    def calcular_promedio(self):
        return sum(self.calificaciones) / len(self.calificaciones)

    def verificar_aprobacion(self):
        promedio = self.calcular_promedio()
        asistencias_minimas = 0.8 * len(self.calificaciones)

        return promedio >= 3.0 and self.asistencia >= asistencias_minimas

    def sugerir_plan_de_accion(self):
        if not self.verificar_aprobacion():
            promedio = self.calcular_promedio()
            if promedio < 3.0:
                return "El estudiante necesita mejorar el promedio. Se sugiere estudiar más y repasar los temas."
            else:
                return "El estudiante necesita mejorar la asistencia. Se sugiere asistir regularmente a clases."
        else:
            return "El estudiante ha aprobado, ¡felicidades!"
