```c
#include "main.h"


t_log* logger;
t_config*config;
char* IP_memoria,*IP_Kernel;
int puertoKernel,pueroMemoria;
int main(int argc, char* argv[]) {
    
    logger=iniciar_logger("EntradasSalidas.log",LOG_LEVEL_DEBUG);

    config=iniciar_config("./EntradasSalidas.config");
       puertoKernel=config_get_int_value(config,"PUERTO_KERNEL");
       IP_Kernel=config_get_string_value(config,"IP_KERNEL");
       IP_memoria=config_get_string_value(config,"IP_MEMORIA");
       pueroMemoria=config_get_int_value(config,"PUERTO_MEMORIA");

    log_info(logger,"Se cargaron las variables corectamente\n");

      int socket_Interfas_A_Kernel= Crear_Conexion(puertoKernel,IP_Kernel);
       log_info(logger,"Se creo el socket de coneccion con el kernel corectamente\n");

      liberar_conexion(socket_Interfas_A_Kernel);
      terminar_programa(logger,config);
    
    return 0;
}
´´´
