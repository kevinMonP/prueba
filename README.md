 # 1) Diferencia entre CTE y VISTA

CTE (Common Table Expression): Es temporal, solo existe durante la ejecución de la consulta. Se usa para dividir consultas complejas, mejorar la legibilidad o implementar recursividad.

Vista: Es un objeto almacenado en la base de datos, reutilizable y permanente hasta que se elimine.



 # 2) ¿Qué son las uniones SQL y por qué son importantes para el análisis de datos?. Indique los tipos de Uniones que se usan en SQL. ¿Puede explicar la diferencia entre LEFT OUTER JOIN e INNER JOIN? ¿Qué es una Self Join?

Son operaciones que permiten combinar filas de dos o más tablas según una condición
los que vimos: INNER JOIN, LEFT JOIN, RIGHT JOIN


 # 3) ¿Puede explicar qué es una clave principal en SQL? ¿Puede una clave principal ser compuesta? De ser así, proporcione un ejemplo.


Es un Campo que identifica de Manera única una fila

SELECT employee_id, department_id
FROM hr.job_history; 


 # 4) ¿Cuál es la diferencia entre WHERE y un HAVING en SQL?

WHERE filtra filas antes del agrupado
HAVING filtra después de agrupar


 # 5) ¿Qué es la normalización en bases de datos SQL?. ¿Cuáles son las diferentes formas normales?


 # 6) ¿Qué es un índice en SQL y por qué se utiliza?
son estructuras que agilizan la búsqueda de datos en una tabla de base de datos
Se utiliza porque La creación de índices optimiza las consultas WHERE, JOIN y ORDER BY

 # 7) ¿Cómo se agrupan los resultados utilizando funciones agregadas? ¿Cómo pueden las funciones agregadas afectar el rendimiento de las consultas?

Se agrupa con GROUP BY ejemplo: select job_id,sum(salary) from employees group by job_id;
Pueden afectar rendimiento en tablas grandes, ya que requieren escanear y procesar los Datos.

 # 8) Comparta una historia sobre una ocasión en la que utilizó subconsultas con éxito para simplificar la recuperación de datos complejos.



 # 9) Explique el concepto de transacciones en SQL. ¿Qué son las propiedades ACID?

Una transacción es un conjunto de operaciones que se aplican juntas: se confirman todas o se deshacen todas.

ACID: Atomicidad (todo-o-nada), Consistencia (respeta reglas/constraints), Aislamiento (transacciones no se interfieren), Durabilidad (persisten tras confirmarse).
Evita datos parciales o corruptos ante errores o caídas.
En Oracle, el aislamiento por defecto suele ser READ COMMITTED.


 # 10) Puede explicar el proceso para administrar índices para poder garantizar un rendimiento eficiente de las consultas en Oracle?

Ayuda: Revisar el plan de ejecución para ver si un índice podría mejorar el rendimiento.





 # 11) ¿Cómo se puede realizar lógica condicional en una sentencia SQL?

Ayuda: Saber usar los CASE.

Se hace con CASE (estándar): evalúa condiciones y devuelve distintos valores (como un IF).

Puede usarse en SELECT, WHERE, ORDER BY y para agregación condicional

 # 12) ¿Cuándo es mejor usar triggers en vez de procedimientos almacenados?


Usa triggers cuando la lógica debe ejecutarse automáticamente en cada INSERT/UPDATE/DELETE.

Utiliza un procedimiento almacenado para agrupar lógica compleja o reutilizable, ejecutar tareas específicas a petición y permitir la interacción del usuario con parámetros de entrada y salida. 





Entrevista Laboral:

Querys
------


 # 1)

SELECT d.department_id,
       e.employee_id
FROM departments d
LEFT JOIN employees e ON e.department_id = d.department_id
ORDER BY d.department_id, e.employee_id;

 # 2)

SELECT department_id
FROM employees
GROUP BY department_id
HAVING COUNT(*) > 10;


 # 3)

UPDATE employees
SET salary = ROUND(salary * 1.06)
WHERE job_id = 'IT_PROG';


 # 4)

select e.first_name, e.Last_name, e.Salary, e.department_id
from employees e
where e.job_id = (select job_id from employees where first_name = 'Willian' and last_name = 'Smith')
order by e.last_name ;
