# Práctica 0: crear un clúster con Minikube

### Propósito

Crear un clúster local de tres nodos con el driver de Docker, comprobar sus
componentes básicos y practicar las operaciones de pausa, detención y borrado de
Minikube.

Esta práctica no contiene manifiestos YAML. Antes de completar el recorrido podrás ejecutar aquí la aplicación real de la calculadora: el clúster se crea con Minikube antes
de poder enviar objetos a la API de Kubernetes.

## 1. Comprobar los requisitos

Docker debe responder sin errores y las dos herramientas deben estar instaladas:

```bash
docker info
```

Comprueba que Docker está instalado, se puede conectar con el daemon y el usuario tiene los permisos necesarios.

```bash
minikube version
```

Muestra la versión instalada de Minikube.

```bash
kubectl version --client
```

Si `docker info` devuelve un error de permisos, corrige el acceso de tu usuario al
daemon de Docker antes de continuar.

## 2. Crear el clúster

Desde una terminal ejecuta:

```bash
minikube start --driver=docker --memory=2048 --nodes=3
```

Se usa el perfil predeterminado `minikube`. Minikube crea un nodo de plano de
control y dos nodos de trabajo. Cada nodo recibe 2048 MiB de memoria.

## 3. Verificar el resultado

```bash
minikube status
```

Comprueba si el perfil local está activo y muestra el estado de sus componentes.

```bash
kubectl cluster-info
```

Muestra la dirección de la API de Kubernetes y los servicios principales accesibles.

```bash
kubectl get nodes -o wide
```

El resultado esperado de `kubectl get nodes` es una lista de tres nodos en estado
`Ready`. Para observar los recursos que Minikube instaló por defecto:

```bash
kubectl get namespaces
```

Lista los namespaces existentes, incluidos los espacios de sistema creados por Kubernetes.

```bash
kubectl get pods --all-namespaces
```

## 4. Administrar el ciclo de vida

Ejecuta estos comandos uno por uno cuando quieras probar cada operación:

```bash
minikube pause
```

Suspende los recursos del clúster sin eliminar los nodos ni la configuración.

```bash
minikube unpause
```

Reanuda los recursos después de haber pausado el clúster.

```bash
minikube stop
```

Apaga los nodos del clúster y conserva su configuración y datos.

```bash
minikube start
```

Vuelve a iniciar el perfil existente después de haberlo detenido.

## Limpieza

No elimines el clúster si vas a continuar con las demás prácticas. Cuando hayas
terminado todo el recorrido puedes borrarlo con:

```bash
minikube delete
```

Este último comando elimina los nodos y datos del clúster local.
