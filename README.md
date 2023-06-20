# Prueba-Clinica-Dental
Evaluación 3
import random

blanqueamientos = []
conductos = []
implantes = []

while True:
    try:
        print("Menú:")
        print("1.- Registrar paciente")
        print("2.- Listar registros")
        print("3.- Buscar por RUT")
        print("4.- Listar según tratamiento")
        print("5.- Salir")

        opc = int(input("Ingrese una opción: "))

        if opc == 1:
            largo = 8
            largo2 = 9
            rut = input("Ingrese RUT paciente: ")
            if (len(rut) == largo or len(rut)==largo2) and rut.isalnum():
                print("RUT correcto")
            else:
                print("RUT incorrecto")
                continue

            nompac = ""
            while not nompac:
                nompac = input("Ingrese nombre paciente: ")

            edad = int(input("Ingrese edad paciente: "))
            while edad < 12:
                print("Paciente debe ser mayor a 12 años")
                edad = int(input("Ingrese edad paciente: "))


            print("1.- Blanqueamiento")
            print("2.- Tratamiento conducto")
            print("3.- Implante dental")
            opc2 = int(input("Ingrese una opción: "))
            if opc2 == 1:
                tratamiento = "Blanqueamiento"
                blanqueamientos.append({"RUT": rut, "Nombre": nompac, "Edad": edad, "Tratamiento": tratamiento})
            elif opc2 == 2:
                tratamiento = "Conducto"
                conductos.append({"RUT": rut, "Nombre": nompac, "Edad": edad, "Tratamiento": tratamiento})
            elif opc2 == 3:
                tratamiento = "Implante"
                implantes.append({"RUT": rut, "Nombre": nompac, "Edad": edad, "Tratamiento": tratamiento})
            else:
                print("Valor incorrecto")
                continue

            print("Paciente registrado exitosamente.")

        elif opc == 2:
            print("Registros de blanqueamiento:")
            for blanqueamiento in blanqueamientos:
                print(blanqueamiento)
                print()

            print("Registros de conductos:")
            for conducto in conductos:
                print(conducto)
                print()
                
            print("Registros de implantes:")
            for implante in implantes:
                print(implante)
                print()

        elif opc == 3:
            rut_paciente = input("Ingrese el RUT del paciente a buscar: ")
            encontrado = False

            for blanqueamiento in blanqueamientos:
                if blanqueamiento["RUT"] == rut_paciente:
                    print("Registro encontrado:")
                    print(blanqueamiento)
                    encontrado = True

            for conducto in conductos:
                if conducto["RUT"] == rut_paciente:
                    print("Registro encontrado:")
                    print(conducto)
                    encontrado = True
            
            for implante in implantes:
                if implante["RUT"] == rut_paciente:
                    print("Registro encontrado:")
                    print(implante)
                    encontrado = True

            if not encontrado:
                print("No se encontró ningún paciente con ese RUT.")

        elif opc == 4:
            print("1.- Blanqueamiento")
            print("2.- Tratamiento Conducto")
            print("3.- Implante Dental")
            opc3 = int(input("Ingrese una opción: "))

            if opc3 == 1:
                print("Reporte de Blanqueamientos:")
                for blanqueamiento in blanqueamientos:
                    print("Reporte médico dental:")
                    print(f"RUT Paciente: {blanqueamiento['RUT']}")
                    print(f"Sr/a: {blanqueamiento['Nombre']}")
                    print(f"Para su tratamiento: {blanqueamiento['Tratamiento']}")
                    print(f"Le hacen falta {random.randint(1, 5)} sesiones por completar.")
                    print()
                print(f"Se generaron {len(blanqueamientos)} reportes de Blanqueamiento.")

            elif opc3 == 2:
                print("Reporte de Tratamientos de Conducto:")
                for conducto in conductos:
                    print("Reporte médico dental:")
                    print(f"RUT Paciente: {conducto['RUT']}")
                    print(f"Sr/a: {conducto['Nombre']}")
                    print(f"Para su tratamiento: {conducto['Tratamiento']}")
                    print(f"Le hacen falta {random.randint(1, 5)} sesiones por completar.")
                    print()
                print(f"Se generaron {len(conductos)} reportes de Tratamiento de conducto.")
                
            elif opc3 == 3:
                print("Reporte de Implantes:")
                for implante in implantes:
                    print("Reporte médico dental:")
                    print(f"RUT Paciente: {implante['RUT']}")
                    print(f"Sr/a: {implante['Nombre']}")
                    print(f"Para su tratamiento: {implante['Tratamiento']}")
                    print(f"Le hacen falta {random.randint(1, 5)} sesiones por completar.")
                    print()
                print(f"Se generaron {len(implantes)} reportes de Implantes.")

            

            else:
                print("Opción incorrecta")

        elif opc == 5:
            break

        else:
            print("Opción incorrecta. Ingrese un número del 1 al 5.")

    except ValueError:
        print("Ingrese un valor correcto.")
