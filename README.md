# Fortune Teller

A simple client-server application that provides fortune telling services over TCP. Ask a yes/no question and receive a mystical response!

## Overview

This project implements a classic Magic 8-Ball style fortune teller using C socket programming. The server listens for client connections, receives questions, and responds with randomly selected fortunes from a predefined set of 20 responses.

## Features

- **TCP Client-Server Architecture**: Reliable communication using TCP sockets
- **Random Fortune Responses**: 20 different mystical responses including positive, negative, and neutral answers
- **Simple Protocol**: Send a question, receive a formatted response
- **Concurrent Support**: Server handles multiple client requests sequentially
- **Error Handling**: Graceful error handling for network and file operations

## Files

- `server.c` - The fortune teller server implementation
- `client.c` - The client application for asking questions
- `responses.txt` - Contains the 20 fortune responses
- `Makefile` - Build configuration
- `client.md` - Detailed design documentation

## Building

To compile both the server and client:

```bash
make all
```

To compile individually:

```bash
make server
make client
```

To clean build artifacts:

```bash
make clean
```

## Usage

### Starting the Server

Run the server in one terminal:

```bash
./server
```

The server will start listening on port 11609 and display:
```
Server listening on port 11609...
```

### Running the Client

In another terminal, connect to the server:

```bash
./client <hostname>
```

Where `<hostname>` is the server's hostname or IP address (use `localhost` for local testing).

Example session:
```bash
$ ./client localhost
Enter your (yes/no) question: Will I get full marks in this assignment?
Q: "Will I get full marks in this assignment?"
R: "Signs point to yes"
```

## Fortune Responses

The server randomly selects from 20 possible responses:

**Positive Responses:**
- It is certain
- It is decidedly so
- Without a doubt
- Yes, definitely
- You may rely on it
- As I see it, yes
- Most likely
- Outlook good
- Yes
- Signs point to yes

**Neutral/Try Again:**
- Reply hazy try again
- Ask again later
- Better not tell you now
- Cannot predict now
- Concentrate and ask again

**Negative Responses:**
- Don't count on it
- My reply is no
- My sources say no
- Outlook not so good
- Very doubtful

## Technical Details

### Network Configuration
- **Protocol**: TCP
- **Port**: 11609
- **Maximum Message Length**: 256 bytes

### Server Behavior
- Listens continuously for client connections
- Handles one client at a time
- Reads questions from clients
- Responds with formatted question and random fortune
- Closes connection after each response

### Client Behavior
- Connects to specified server
- Prompts user for a yes/no question
- Sends question to server
- Displays formatted response
- Terminates after receiving response

## Error Handling

The application handles various error conditions:

- **Network Errors**: Socket creation, connection, and communication failures
- **File Errors**: Issues reading the responses file
- **Input Validation**: Checks for proper command line arguments
- **Connection Issues**: Graceful handling of server unavailability

## Example Output Format

```
Q: "Will it rain tomorrow?"
R: "Very doubtful"
```

## Development

### Prerequisites
- GCC compiler
- POSIX-compliant system (Linux, macOS, etc.)
- Basic networking support

### Compilation Flags
- `-Wall`: Enable all warnings
- `-g`: Include debugging information

## Testing

Test the application by:

1. Starting the server in one terminal
2. Running multiple client instances with different questions
3. Verifying random responses for the same question
4. Testing error conditions (invalid hostnames, server not running, etc.)

## Author

**Kethan Pilla**  
CS440-1 Assignment #1

## Collaborators

stumpati

## Resources

- w3Schools
- Manual pages (arc4random, printf, style)
- Beej's Guide to Network Programming (bgnet)

## License

This project is for educational purposes as part of a computer science networking course.
