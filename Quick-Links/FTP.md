# File Transfer Protocols [↑](../README.md#1-aws-cloud-practitioner-notes)

## `Secure File Transfer Protocol (SFTP)`
- SSH File Transfer Protocol
- Not related to traditional FTP. It is a completely different protocol that just happens to have a similar name.
- Uses a single encrypted channel for both commands and data.

### Ports
- Default port: 22 (same as SSH)
- Easier to configure through firewalls because it only uses one port.

### Security
- Uses SSH
- username/password or SSH Keys


## `File Transfer Protocol Secure (FTPS)` 
- Traditional FTP protocol enhanced with TLS/SSL encryption.
- Uses separate channel for commands (control channel) and file data (data channel).

### Ports
- Default Ports:
  - Explicit FTPS: Control on 21, data on separate negotiated ports
  - Implicit FTPS: Control on 990.
- More firewall rules are needed since the data channel ports can vary.

### Security
- Uses SSL (Secure Socket Layer) /TLS (Transport Layer Security) Certificate
- username/password + server's public certificate