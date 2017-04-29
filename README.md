# Secure-Instant-Messaging-Chat-Application-
Peer to Peer chat application with End to End security

The architecture is based on client-server model over TCP in which server is the
central node responsible for registration, login and authentication of clients. Server
mantains the database of active users and their session (symmetric) keys that are currently
active. Clients obtain the address of the remote peer from server and authenticate mutually
before communication.
If client1 wants to communicate with client2, it will request server for the details
about remote peer. The server responds granting a ticket to remote client if active. Client1
has to authenticate mutually with remote peer and establish secure channel to initate
messaging. The signaling consists of four major messages LOGIN, LIST, SEND, and LOGOUT.
Messages:
1. LOGIN: LOGIN message is used by client to request the server to authenticate and mark
itself active. Once login is successful, the client will be available for communication with
peer clients.

2. LIST: LIST message is used by clients to request the list of active users who are currently
logged into the server. It can be initiated through LIST command.
3. SEND: SEND message is used by clients to initiate secure messaging channel with remote
peers. The SEND message is initiated through SEND command and consists of two steps:
a. Local peer has to initiate SEND request to server to fetch remote peer details
which can be obtained through the server who grants a ticket to establish connection with
the remote active client. The ticket consists peer client identity, IP address, remote port,
public key of the client who is initiating the chat.
b. Client-Client Authentication using Ticket: Local peer receives ticket from server as
discussed above and initiates a peer to peer connection with remote client. Once the
authentication is complete a secure channel is established for messaging.
4. LOGOUT: LOGOUT message is used to terminate session. It is initiated at client side
through LOGOUT command. The message initiates logout sequence with server and upon
successful logout, client and server will scrap off the session key.
Assumptions
• Public key of the server is available to all the clients.
• Server is trusted
• Clients are already pre-registered at server with strong passwords and server stores
hashed passwords with salting
• Server generates session key for each client at login and is used for further
communication with server through the session and is deleted at logout or
connection termination.

Key/Notations
A: Alice (Client1 Identity)
B: Bob (Client2 identity)
PKA: Public Key of Alice (RSA 2048)
PKB: Public Key of Bob (RSA 2048)
PKs: Public Key of Server (RSA 2048)
PSA: Private Key of Alice (RSA 2048)
KA: Session (Symmetric) key generated by server for client 1 (256 Bit)
KB: Session (Symmetric) key generated by server for client 2 (256 Bit)
KAB: Session (Symmetric) key generated by client2 for client 1 (256 Bit)
IPA: IP address of Alice
IPB: IP address of Bob
R: Challenge
T: Timestamp (T1, T2… etc.)

5
Services provided by application:
1. Perfect Forward Secrecy (PFS) for session
2. P2P messaging thus preventing server to capture or decrypt messages
3. Protection against weak passwords with hashing and salting
4. End-point hiding
5. Protection against Denial of Service (DoS) attacks


Main Contributors

Naveen Yanamaddi
Nithesh Nagaraj

