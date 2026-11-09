# Práctica 0: crear un clúster con Minikube

### Propósito

Crear un clúster local de tres nodos con el driver de Docker, comprobar sus
componentes básicos y practicar las operaciones de pausa, detención y borrado de
Minikube.

Esta práctica no contiene manifiestos YAML. Antes de completar el recorrido podrás ejecutar aquí la aplicación real de la calculadora: el clúster se crea con Minikube antes
de poder enviar objetos a la API de Kubernetes.

## 1. Comprobar Docker

Comprueba que Docker está instalado, se puede conectar con el daemon y el usuario tiene los permisos necesarios.

```bash
docker info
```

## 2. Comprobar Minikube

Muestra la versión instalada de Minikube.

```bash
minikube version
```

## 3. Comprobar kubectl

Comprueba que la CLI de Kubernetes está instalada.

```bash
kubectl version --client
```

Si `docker info` devuelve un error de permisos, corrige el acceso de tu usuario al
daemon de Docker antes de continuar.

## 4. Crear el clúster

Desde una terminal ejecuta:

Minikube crea un nodo de plano de control y dos nodos de trabajo con 2048 MiB cada uno.

```bash
minikube start --driver=docker --memory=2048 --nodes=3
```

Se usa el perfil predeterminado `minikube`.

## 5. Consultar el estado de Minikube

Comprueba si el perfil local está activo y muestra el estado de sus componentes.

```bash
minikube status
```

## 6. Consultar la información del clúster

Muestra la dirección de la API de Kubernetes y los servicios principales accesibles.

```bash
kubectl cluster-info
```

## 7. Verificar los nodos

El resultado esperado es una lista de tres nodos en estado `Ready`.

```bash
kubectl get nodes -o wide
```

## 8. Listar los namespaces

Observa los espacios de sistema creados por Kubernetes.

```bash
kubectl get namespaces
```

## 9. Listar los Pods de sistema

Comprueba los Pods instalados por Minikube en todos los namespaces.

```bash
kubectl get pods --all-namespaces
```

## 10. Pausar el clúster

Suspende los recursos sin eliminar los nodos ni la configuración.


```bash
minikube pause
```

## 11. Reanudar el clúster

Reanuda los recursos después de haber pausado el clúster.

```bash
minikube unpause
```

## 12. Detener el clúster

Apaga los nodos y conserva su configuración y datos.

```bash
minikube stop
```

## 13. Reiniciar el clúster

Vuelve a iniciar el perfil existente.

```bash
minikube start
```

## 14. Eliminar el clúster

No ejecutes este paso si vas a continuar con las demás prácticas. Elimina los nodos, perfiles y datos locales del clúster cuando termines todo el recorrido.


```bash
minikube delete
```

Este último comando elimina los nodos y datos del clúster local.
