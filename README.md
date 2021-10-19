# apigee-x-react-template

This is a sample react template for an Apigee X developer portal using the
Apigee API.

## Getting started with the client

To try the react frontend template out, just clone and run the client with test
data like this:

```ssh
cd client
npm start
```

Currently the API documentation is hard-coded to the petshop sample for testing
purposes.  The API documentation is currently rendered using the excellent
[RapiDoc](https://mrin9.github.io/RapiDoc/) project.

## Getting started with the service

The service directory contains a nodejs project that integrates with a real
Apigee X org using the [Apigee
API](https://cloud.google.com/apigee/docs/reference/apis/apigee/rest).

To authenticate with Apigee X, you should set environment variables (either
locally using an .env file, or in a Dockerfile) for the org, service email, and
service private key.

```env
APIGEE_ORG=<<Apigee org name>>
SERVICE_ACCOUNT_EMAIL=<<GCP service account email>>
SERVICE_ACCOUNT_KEY=<<GCP service account private key>>
```

The service will use the configuration to fetch published API products and offer
them for developers to enable for their credentials.

The API products offered in the portal are currently configured in a YAML file
in **config/apiportal.yaml**.  This should of course be changed to your API
products matching the names configured in Apigee.

To deploy, first build the client (which copies the output into the service
public directory), and then start the service like this:

```ssh
cd client
./build.sh
cd ../service
npm start
```
