# AircrackCluster-Client
Server repo: [https://github.com/hurrhnn/AircrackCluster-Server](https://github.com/hurrhnn/AircrackCluster-Server)

AircrackCluster helps you crack passwords faster.

## Requirements
**aircrack-ng** & **Java 8 and later versions** must be installed on the system.

## Client Concept
```
1. Get address and port to connect socket to args[0], args[1].
2. Bench for 5 seconds and send results separately.
3. Receive `BENCH_RESULT OK`.

4. Send `FILE_BYTE OK` and receive byte count.
5. Send `FILE_READY OK` and receive cap file.
6. Send `FILE_RECV OK` if byte matches.
6-1. Send `RETRY` from No. 4. If you receive `DROP`, kill the program.

7. Send `INF_READY OK` and receive BSSID and ESSID strings.
8. Send `INF_RECV OK`.

9. Send `DICT_SIZE OK` and receive it.
10. Send `DICT_READY OK` and receive `DICT` as many times as you can.

11. Send `AIRCRACK_RESULT FAIL` or `AIRCRACK_RESULT OK, PASSWORD`.
11-1. If receive `FAIL`, Do it again from No. 9.
```

## Usage
0. build [AircrackCluster-Server](https://github.com/hurrhnn/AircrackCluster-Server) and run at server first.
1. run `java -jar AircrackCluster-Client-1.0-all.jar [IP or Hostname] 6974` to connect to server.
2. Use the [AircrackCluster-Client](https://github.com/hurrhnn/AircrackCluster-Client/tree/master/build/libs) to connect to the server.
3. When all nodes are connected, each node starts cracking.
