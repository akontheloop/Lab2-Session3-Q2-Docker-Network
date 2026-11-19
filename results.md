# Results and Observations

## Docker Network
- Created a custom Docker network named `mynetwork`.
- Connected `container1` and `container2` to the network.

## Name-based Communication
- Executed `docker exec container1 ping -c 4 container2`.
- Ping was successful.
- **Result:** Containers communicated through the Docker network using the container name.

## IP-based Communication
- Inspected `container2` and obtained IP address `172.21.0.3`.
- Executed `docker exec container1 ping -c 4 172.21.0.3`.
- Ping was successful.
- **Result:** Containers communicated using the container IP address.

## Conclusion
Communication between two Docker containers on a user-defined network was successfully demonstrated using both container names and IP addresses.
