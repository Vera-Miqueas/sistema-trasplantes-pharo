### Ejemplo 1.



| centro paciente donante evaluador resultado |



centro := CentroTrasplantes conNombre: 'Hospital San Martín'.



paciente := Persona conDni: 22345671 nombre: 'Lucía' apellido: 'Gómez' fechaNacimiento: (Date year: 1990 month: 7 day: 14).

donante := Persona conDni: 22345672 nombre: 'Pedro' apellido: 'Gómez' fechaNacimiento: (Date year: 1988 month: 5 day: 9).



centro agregaPaciente: paciente fechaIngreso: (Date year: 2000 month: 3 day: 9).

centro agregaDonante: donante.

centro asociaPaciente: paciente conDonante: donante.



paciente registraEstudio: (AnalisisDeSangre conGrupoSanguineo: #A).

donante registraEstudio: (AnalisisDeSangre conGrupoSanguineo: #A).



"Crossmatch positivo → rechazo directo"

paciente registraEstudio: (EstudioCrossmatch conResultado: #positivo) con: donante.



paciente registraEstudio: (EstudioSerologicoCompleto conResultado: #apto).

donante registraEstudio: (EstudioSerologicoCompleto conResultado: #apto).



evaluador := EvaluadorCompatibilidad new.

evaluador agregaCriterioObligatorio: CriterioABO new.

evaluador agregaCriterioObligatorio: CriterioCrossmatch new.

evaluador agregaCriterioObligatorio: CriterioSerologias new.



centro evaluadorCompatibilidad: evaluador.



resultado := centro compatibilidad: paciente con: donante.

Transcript show: 'Caso 1 (Crossmatch positivo): '; show: resultado; cr.











### Ejemplo 2.



| centro paciente donante evaluador resultado |



centro := CentroTrasplantes conNombre: 'Hospital Cullen'.



paciente := Persona conDni: 42345671 nombre: 'Ana' apellido: 'López' fechaNacimiento: (Date year: 1992 month: 8 day: 10).

donante := Persona conDni: 42345672 nombre: 'Sofía' apellido: 'Martínez' fechaNacimiento: (Date year: 1990 month: 12 day: 2).



centro agregaPaciente: paciente fechaIngreso:(Date year: 2000 month: 3 day: 2).

centro agregaDonante: donante.

centro asociaPaciente: paciente conDonante: donante.



paciente registraEstudio: (AnalisisDeSangre conGrupoSanguineo: #O).

donante registraEstudio: (AnalisisDeSangre conGrupoSanguineo: #O).

paciente registraEstudio: (EstudioCrossmatch conResultado: #negativo) con: donante.



"Serología indica infección (no apto)"

paciente registraEstudio: (EstudioSerologicoCompleto conResultado: #noApto).

donante registraEstudio: (EstudioSerologicoCompleto conResultado: #apto).



evaluador := EvaluadorCompatibilidad new.

evaluador agregaCriterioObligatorio: CriterioABO new.

evaluador agregaCriterioObligatorio: CriterioCrossmatch new.

evaluador agregaCriterioObligatorio: CriterioSerologias new.



centro evaluadorCompatibilidad: evaluador.



resultado := centro compatibilidad: paciente con: donante.

Transcript show: 'Caso 3 (Serología no apta): '; show: resultado; cr.













### Ejemplo 3.



| centro paciente donante evaluador resultado |

centro := CentroTrasplantes conNombre: 'Hospital Italiano'.

paciente := Persona conDni: 52345671 nombre: 'Diego' apellido: 'Fernández' fechaNacimiento: (Date year: 2000 month: 4 day: 4).

donante := Persona conDni: 52345672 nombre: 'Martín' apellido: 'Fernández' fechaNacimiento: (Date year: 1998 month: 6 day: 8).



centro agregaPaciente: paciente fechaIngreso: (Date year: 2001 month: 6 day: 8).

centro agregaDonante: donante.

centro asociaPaciente: paciente conDonante: donante.



paciente registraEstudio: (AnalisisDeSangre conGrupoSanguineo: #A).

donante registraEstudio: (AnalisisDeSangre conGrupoSanguineo: #A).



paciente registraEstudio: (EstudioCrossmatch conResultado: #negativo) con: donante.

paciente registraEstudio: (EstudioSerologicoCompleto conResultado: #apto).

donante registraEstudio: (EstudioSerologicoCompleto conResultado: #apto).



paciente registraEstudio: (EstudioTipificacionHLA conA: #(A2 A3) b: #(B7 B44) dR: #(DR1 DR4)).

donante registraEstudio: (EstudioTipificacionHLA conA: #(A2 A3) b: #(B7 B44) dR: #(DR1 DR4)).



paciente estatura: 1.70; peso: 70.

donante estatura: 1.73; peso: 74.



evaluador := EvaluadorCompatibilidad new.

evaluador agregaCriterioObligatorio: CriterioABO new.

evaluador agregaCriterioObligatorio: CriterioCrossmatch new.

evaluador agregaCriterioObligatorio: CriterioSerologias new.

evaluador agregaCriterioDeseable: CriterioHLA new conPonderacion: 80.

evaluador agregaCriterioDeseable: CriterioEdad new conPonderacion: 10.

evaluador agregaCriterioDeseable: CriterioTamanoCorporal new conPonderacion: 10.



centro evaluadorCompatibilidad: evaluador.



resultado := centro compatibilidad: paciente con: donante.

Transcript show: 'Caso 4 (Totalmente apto): '; show: resultado; cr.



