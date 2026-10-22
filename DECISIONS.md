## D-002 · Estructura Maven multimódulo
Fecha: 22/10 · It. 0 · Acta: 22/10 · Issue: #4
Contexto: hay dos aplicaciones, servidor y cliente, en un mismo repositorio.
Decisión: pom padre radiodiagnostico con dos módulos: servidor y cliente.
Alternativas: dos repositorios; un solo módulo.
Motivo: un mvn verify construye todo y las versiones se fijan una vez en el padre.
Consecuencias: cada módulo con su versión; al cambiar la del padre, actualizar <parent>.