import random

class Concursante:
    def __init__(self, nombre):
        self.nombre = nombre
        self.tiempo_respuesta_clasificatoria = random.randint(10, 60)
        self.premio_obtenido = 0
        self.ultima_pregunta_correcta = 0
        self.comodines_utilizados = {
            "50/50": random.randint(0, 1),
            "ayuda_del_publico": random.randint(0, 1),
            "llamada_a_un_amigo": random.randint(0, 1)
        }

    def responder_preguntas(self):
        valores_preguntas = {
            15: 300000000, 14: 100000000, 13: 50000000, 12: 20000000, 11: 12000000,
            10: 10000000, 9: 7000000, 8: 5000000, 7: 3000000, 6: 2000000,
            5: 1000000, 4: 500000, 3: 300000, 2: 200000, 1: 100000
        }
        seguros = {5: 1000000, 10: 10000000}

        for i in range(1, 16):
            respuesta_verificar = self.generar_respuesta()
            respuesta_pregunta = self.generar_respuesta()

            if respuesta_verificar == respuesta_pregunta:
                if i in valores_preguntas:
                    self.premio_obtenido = valores_preguntas[i]
                    self.ultima_pregunta_correcta = i
                if i in seguros:
                    self.premio_obtenido = seguros[i]
            else:
                break

    def generar_respuesta(self):
        return random.choice(['A', 'B', 'C', 'D'])

class Concurso:
    def __init__(self):
        self.participantes = {
            "Lunes": [],
            "Martes": [],
            "Miércoles": [],
            "Jueves": [],
            "Viernes": []
        }

    def agregar_participante(self, concursante, dia):
        self.participantes[dia].append(concursante)

    def simular_concurso(self, num_participantes):
        nombres = ["Juan", "Ana", "Carlos", "Laura", "Miguel", "Isabel"]

        for _ in range(num_participantes):
            nombre_aleatorio = random.choice(nombres)
            concursante = Concursante(nombre_aleatorio)
            concursante.responder_preguntas()

            dias = list(self.participantes.keys())
            random.shuffle(dias)
            for dia in dias:
                if len(self.participantes[dia]) < 3: 
                    self.agregar_participante(concursante, dia)
                    break
            else:
                break  

concurso_semana = Concurso()

for dia in range(5):
    num_participantes = random.randint(2, 3) 
    concurso_semana.simular_concurso(num_participantes)

    print(f"\nParticipantes del día {dia + 1}:")
    for idx, concursante in enumerate(concurso_semana.participantes[f"Lunes"], start=1):
        print(f"\nDatos del concursante {idx}:")
        print(f"Nombre: {concursante.nombre}")
        print(f"Tiempo de respuesta en la clasificatoria: {concursante.tiempo_respuesta_clasificatoria} segundos")
        print(f"Premio obtenido: ${concursante.premio_obtenido}")
        print(f"Última pregunta contestada correctamente: {concursante.ultima_pregunta_correcta}")
        print(f"Comodines utilizados: {concursante.comodines_utilizados}")

valor_emisiones_semana = []
valor_total_semana = 0

for dia, participantes in concurso_semana.participantes.items():
    valor_emision_dia = sum(concursante.premio_obtenido for concursante in participantes)
    valor_emisiones_semana.append(valor_emision_dia)
    valor_total_semana += valor_emision_dia
    print(f"\nValor otorgado en la emisión del día {dia}: ${valor_emision_dia}")

print(f"\nValor total otorgado a todos los concursantes durante esa semana: ${valor_total_semana}")
