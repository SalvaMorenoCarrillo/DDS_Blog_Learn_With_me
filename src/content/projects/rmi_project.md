---
title: 'Send a message using java sockets'
description: 'This is a simple project where you will learn to stablish a socket conection using java '
pubDate: 'Oct 15 2023'
heroImage: '/JavaSt1.png'
---
<P>
With this simple project we will learn how to create client, a server and stablish a conection between them using Java Sokets.
<P>
<P>
Setting up the server
<p>
<p>

/Code

    import java.io.*;
    import java.net.*;

    class Server {
	    public static void main(String[] args)
	    {
		    try {
		
			    // establish connection
			    ServerSocket serversocket
			    	= new ServerSocket(1346);// Port nº

			    System.out.println("waiting for request....");

			    // Socket object to accept all the connections
			    Socket socket = serversocket.accept();

			    System.out.println("Request Accepted...");
    
			    // Printstream to print all the data
			    PrintStream ps
			    	= new PrintStream(socket.getOutputStream());

			    BufferedReader br = new BufferedReader(
			    	new InputStreamReader(System.in));
		
			    System.out.println(
			    	"Input the data at the server...");
		
			    // Printing bufferedreader data
			    ps.print(br.readLine());
			    socket.close();
			    serversocket.close();
		    }
		    catch (IOException e) {
		
			    // Catch block for data stream errors
			    System.out.println("Not found data for socket"
			    				+ e);
		    }
	    }
    }

<p>

Now we set Up the Client.


// Client program

    import java.io.*;
    import java.net.*;

    class Client {

	// driver function
	public static void main(String[] args)
	{
		try {
		
			// Create socket object by passing id address
			// and port number establish connection
			Socket socket = new Socket("localhost", 1346);
			System.out.println(
				"Connected Successfully.....");

			// Buffer reader to get all the input stream
			BufferedReader bs = new BufferedReader(
				new InputStreamReader(socket.getInputStream()));
			System.out.println("Response from Server.....");

			// Print response from server
			System.out.println("Client Side : "
							+ bs.readLine());
			// Close the connection
			socket.close();
		}
		catch (UnknownHostException e) {
		
			// Catch block for IP errors
			System.out.println("IP not found for" + e);
		}
		catch (IOException e) {
		
			// Catch block for data stream errors
			System.out.println("Not found data for socket"
							+ e);
		}
	}
    }
<p>
Now you can send messages back and forth with the sever in your local host.    
<p>
Try experimenting a bit see what you can do.
<p>
Have fun!!


