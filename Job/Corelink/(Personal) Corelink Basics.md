# Corelink Basics
#cs 


## Breakdown of Echo Client 


Steps:

- Initialize App
- Wait for operation to finish, framework bootstrapping happens asynchronously
- Authenticate with Corelink
- Wait for operation to finish
- Make a request to get the workspace
- Wait..
- Create sender stream for application
- Wait..
- Create receiver stream, can be done in parallel
- Wait..
- Send data.


```cpp
int main(int argc, char** argv)
{
	UNUSED(argc);
	UNUSED(argv);
	UNUSED(std::signal(SIGTERM, &handle_exit));
	UNUSED(std::signal(SIGINT, &handle_exit));

	// now, we try to create necessary network communication mechanisms and set up communication channels with the
	// corelink server note that this step just creates the medium to communicate with corelink - it does not do anything with
	// the corelink API yet.
	app.init_my_app();

	// wait for the operation to finish as all the framework bootstrapping and happens in an async manner.
	wait_for_signal_from_app();
	
	// now that network connections have been established, we need to first authenticate with corelink server.
	// we use client.request(...) method for this which works asynchronously.
	// we cannot issue any further requests unless we are authenticated, so we wait post making the request
	app.authenticate_with_corelink();
	
	// wait for the operation to finish
	wait_for_signal_from_app();
	
	// we are now free to make other requests/ receive push notifications from the server for any special events
	// here we show an example where we make a request to get workspaces
	app.ex_get_workspaces();
	
	// wait for the operation to finish
	wait_for_signal_from_app();
	
	// let us create a sender stream for our application
	app.create_sender();
	
	wait_for_signal_from_app();
	
	// now let us create a receiver stream for our application. these can be created in parallel. we just do it here for
	// demonstration purposes.
	app.create_receiver();
	
	wait_for_signal_from_app();
	
	// let us send some trivial string data indefinitely
	for (int some_num = 0; !exit_app; ++some_num)
	{
		std::string msg{"Hello World"};
		corelink::utils::json head;
		head.append("counter", some_num);
		app.send_data(
			std::vector<uint8_t>(msg.begin(), msg.end()),
			std::move(head)
		);
		std::this_thread::sleep_for(std::chrono::milliseconds(100));
	}
	return 0;
};
```



### Initializing 

