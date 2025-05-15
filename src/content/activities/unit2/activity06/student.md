***¿Qué hace esto int *pvar;?***
Esto declara un puntero, el cual no apunta a nada todavía.

***¿Qué hace esto *pvar = var;?***
Esto inicializa/define el puntero, el cual se hace igual a var (una variable).
Esto guarda en la dirección de memoria a la que pvar apunta, el valor de var. Aunque para hacer easo primero debo saber a donde apunto con *pvar.

***¿Qué hace esto var2 = *pvar?***
El contenido de la variable a la que apunto con *pvar, lo guardo en var2.

***¿Qué hace esto pvar = &var3?***
Estamos guardando en pvar la dirección de memoria donde está var3
