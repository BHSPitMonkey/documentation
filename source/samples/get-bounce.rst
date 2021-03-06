
.. code-block:: bash

    curl -s --user 'api:YOUR_API_KEY' -G \
	https://api.mailgun.net/v3/YOUR_DOMAIN_NAME/bounces/foo@bar.com

.. code-block:: java

 public static ClientResponse GetBounce() {
 	Client client = new Client();
 	client.addFilter(new HTTPBasicAuthFilter("api",
 			"YOUR_API_KEY"));
 	WebResource webResource =
 		client.resource("https://api.mailgun.net/v3/YOUR_DOMAIN_NAME/" +
 				"bounces/foo@bar.com");
 	return webResource.get(ClientResponse.class);
 }

.. code-block:: php

  # Include the Autoloader (see "Libraries" for install instructions)
  require 'vendor/autoload.php';
  use Mailgun\Mailgun;

  # Instantiate the client.
  $mgClient = new Mailgun('YOUR_API_KEY');
  $domain = 'YOUR_DOMAIN_NAME';
  $bounce = 'bob@example.com';

  # Issue the call to the client.
  $result = $mgClient->get("$domain/bounces/$bounce");

.. code-block:: py

 def get_bounce():
     return requests.get(
         "https://api.mailgun.net/v3/YOUR_DOMAIN_NAME/bounces/foo@bar.com",
         auth=("api", "YOUR_API_KEY"))

.. code-block:: rb

 def get_bounce
   RestClient.get("https://api:YOUR_API_KEY"\
                  "@api.mailgun.net/v3/YOUR_DOMAIN_NAME/bounces"\
                  "/foo@bar.com"){|response, request, result| response }
 end

.. code-block:: csharp

 public static IRestResponse GetBounce() {
 	RestClient client = new RestClient();
 	client.BaseUrl = new Uri("https://api.mailgun.net/v2");
 	client.Authenticator =
 		new HttpBasicAuthenticator("api",
 		                           "YOUR_API_KEY");
 	RestRequest request = new RestRequest();
 	request.AddParameter("domain",
 	                     "YOUR_DOMAIN_NAME", ParameterType.UrlSegment);
 	request.Resource = "{domain}/bounces/foo@bar.com";
 	return client.Execute(request);
 }

.. code-block:: go

 func GetBounce(domain, apiKey string) (mailgun.Bounce, error) {
   mg := mailgun.NewMailgun(domain, apiKey, "")
   return mg.GetSingleBounce("foo@bar.com")
 }
