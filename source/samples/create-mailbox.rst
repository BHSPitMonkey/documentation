
.. code-block:: bash

    curl -s --user 'api:YOUR_API_KEY' \
	https://api.mailgun.net/v3/YOUR_DOMAIN_NAME/mailboxes \
	-F mailbox='alice@YOUR_DOMAIN_NAME' \
	-F password='supasecret'

.. code-block:: java

 public static ClientResponse CreateMailbox() {
 	Client client = Client.create();
 	client.addFilter(new HTTPBasicAuthFilter("api",
 			"YOUR_API_KEY"));
 	WebResource webResource =
 		client.resource("https://api.mailgun.net/v3/YOUR_DOMAIN_NAME" +
 				"/mailboxes");
 	MultivaluedMapImpl formData = new MultivaluedMapImpl();
 	formData.add("mailbox", "alice@YOUR_DOMAIN_NAME");
 	formData.add("password", "secret");
 	return webResource.type(MediaType.APPLICATION_FORM_URLENCODED).
 		post(ClientResponse.class, formData);
 }

.. code-block:: php

  # Include the Autoloader (see "Libraries" for install instructions)
  require 'vendor/autoload.php';
  use Mailgun\Mailgun;

  # Instantiate the client.
  $mgClient = new Mailgun('YOUR_API_KEY');
  $domain = 'YOUR_DOMAIN_NAME';

  # Issue the call to the client.
  $result = $mgClient->post("$domain/mailboxes", array(
      'mailbox'  => 'alice@YOUR_DOMAIN_NAME',
      'password' => 'secret'
  ));

.. code-block:: py

 def create_mailbox():
     return requests.post(
         "https://api.mailgun.net/v3/YOUR_DOMAIN_NAME/mailboxes",
         auth=("api", "YOUR_API_KEY"),
         data={"mailbox": "alice@YOUR_DOMAIN_NAME",
               "password": "secret"})

.. code-block:: rb

 def create_mailbox
   RestClient.post "https://api:YOUR_API_KEY"\
   "@api.mailgun.net/v3/YOUR_DOMAIN_NAME/mailboxes",
   :mailbox => "alice@YOUR_DOMAIN_NAME",
   :password => "secret"
 end

.. code-block:: csharp

 public static IRestResponse CreateMailbox() {
 	RestClient client = new RestClient();
 	client.BaseUrl = new Uri("https://api.mailgun.net/v2");
 	client.Authenticator =
 		new HttpBasicAuthenticator("api",
 		                           "YOUR_API_KEY");
 	RestRequest request = new RestRequest();
 	request.AddParameter("domain",
 	                     "YOUR_DOMAIN_NAME", ParameterType.UrlSegment);
 	request.Resource = "{domain}/mailboxes";
 	request.AddParameter("mailbox", "alice@YOUR_DOMAIN_NAME");
 	request.AddParameter("password", "secret");
 	request.Method = Method.POST;
 	return client.Execute(request);
 }

.. code-block:: go

 // Not supported
