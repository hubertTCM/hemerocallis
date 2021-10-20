
- bypass invalid SSL certificate in .net core
	```C#
	services.AddHttpClient("HttpClientName", client => {
	// code to configure headers etc..
	}).ConfigurePrimaryHttpMessageHandler(() => {
		var handler = new HttpClientHandler {
			ServerCertificateCustomValidationCallback = (message, cert, chain, errors) => { return true; }
		};
		return handler;
	});
	```
	[reference](https://stackoverflow.com/questions/38138952/bypass-invalid-ssl-certificate-in-net-core)