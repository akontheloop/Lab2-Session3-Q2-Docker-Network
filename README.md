# Lab 2 – Session 3 – Question 2
## Docker Network: Communication Between Containers

### Objective
Demonstrate:
- Communication between two containers through a Docker network.
- Communication using container names.
- Communication using container IP addresses.

## 1. Create a Docker network

```bash
docker network create mynetwork
```

## 2. Create two containers connected to the network

```bash
docker run -dit --name container1 --network mynetwork alpine
docker run -dit --name container2 --network mynetwork alpine
docker ps
```

## 3. Test communication using container names

```bash
docker exec container1 ping -c 4 container2
```

**Observation:** Ping replies were received, demonstrating name-based communication through the user-defined Docker network.

## 4. Find container2's IP address

```bash
docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' container2
```

IP address observed during this lab:

```text
172.21.0.3
```

## 5. Test communication using IP address

```bash
docker exec container1 ping -c 4 172.21.0.3
```

**Observation:** Ping replies were received from `172.21.0.3`, demonstrating IP-based communication between containers.

## 6. Final verification

```bash
docker network inspect mynetwork
docker ps
```

## Conclusion

A custom Docker network was created and two Alpine containers were connected to it. Communication was successfully tested between the containers using both the container name (`container2`) and its IP address (`172.21.0.3`).
