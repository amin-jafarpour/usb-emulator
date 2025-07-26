## Packet Types
Each transaction is composed of one or more packet types.
### Token Packets: SETUP, IN, OUT
### Data Packets: DATA0, DATA1, DATA2, MDATA
### Handshake Packets: ACK, NAK, STALL, NYET
### Special Packets: PRE, ERR, PING, SPLIT


---------------------------------------------------------------------------------------


Each USB transaction is made up of one or more tokens.
There are four types of tokens. 
Each token starts with a SYNC field and ends with EOP (End of Packet). 
### Token
- Used by host to communicate intentions. 
#### IN
- Declares that hosts wants to receive content.
#### OUT
- Declares that host wants to send content.
- \[Packet ID\]\[Device Address\]\[Endpoint Number\]\[CRC\]
#### SETUP
- Declares that a 8-byte control packet packet.
#### Start of Frame (SOF)
- Contains frame number for synchronization. 
#### PING
- Asks host whether it is ready to accept content.
- Host needs to send an ACK to signal it is ready.
#### SPLIT
- Used to split a high-speed transaction into multiple low/full-speed pieces via a USB hub.
- Allows host to talk to low/full-speed devices through a high-speed hub.
### Data
#### DATA0
- Detects duplicates/retries.
#### DATA1
- Detects duplicates/retries.
#### DATA2
- Used for high-speed isochronous transfers.
#### MDATA
Used for split transactions and high-speed bulk/control.
### Handshake
- Used to acknowledge success or failure of a data transaction.
#### ACK
- cknowledges successful receipt of data.
#### NAK
- Receiver not ready to send/receive data; tells host to retry later.
#### STALL
- Endpoint has encountered a condition that prevents further communication.
- Requires host intervention (often reset or driver recovery).
#### NYET
- Used in split or pipelined transfers.
- Device acknowledges that it's received the data but not ready for the next packet.
### Special
#### PRE
- Marks the start of a low-speed transaction on a full-speed bus.
#### ERR
- Used in split transactions to indicate an error during the completion phase.
#### EXIT
- Reserved for future protocol extensions.



