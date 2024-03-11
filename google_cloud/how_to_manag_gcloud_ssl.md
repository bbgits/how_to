









## first, created a cert using command line

website:[gcloud certificate-manager certificates create &nbsp;|&nbsp; Google Cloud CLI Documentation](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/certificates/create?authuser=1)





To create a certificate managed by Certificate Manager called `api-example-com`, run:

```
gcloud certificate-manager certificates create api-example-com --domains="api.example.com"
```







## Then asked YOU.com:



I was having an issue with the SSL certificate for the html website I have deployed to firebase hosting. I am attempting to fix the issue by using the google cloud CLI to mannually create a new certificate. I've used the CLI to Create the Certificate for the domain in questino (turbotabs.com), and the terminal lconfirmed "Created certificate [new-certificate-name]". My question is that now that I have created the certificate, is there anything else I need to do to deploy it or is that handled already?

[javascript - "Mixed content blocked" when running an HTTP AJAX ...](https://stackoverflow.com/questions/33507566/mixed-content-blocked-when-running-an-http-ajax-operation-in-an-https-page)

![Favicon for stackoverflow.com](https://you.com/proxy?url=https%3A%2F%2Fwww.google.com%2Fs2%2Ffavicons%3Fsz%3D128%26domain%3Dstackoverflow.com)

[stackoverflow.com](https://stackoverflow.com/questions/33507566/mixed-content-blocked-when-running-an-http-ajax-operation-in-an-https-page)

[Firebase Hosting](https://firebase.google.com/docs/hosting)

![Favicon for google.com](https://you.com/proxy?url=https%3A%2F%2Fwww.google.com%2Fs2%2Ffavicons%3Fsz%3D128%26domain%3Dgoogle.com)

[firebase.google.com](https://firebase.google.com/docs/hosting)

[javascript - Page loaded over HTTPS but requested an insecure ...](https://stackoverflow.com/questions/37387711/page-loaded-over-https-but-requested-an-insecure-xmlhttprequest-endpoint)

![Favicon for stackoverflow.com](https://you.com/proxy?url=https%3A%2F%2Fwww.google.com%2Fs2%2Ffavicons%3Fsz%3D128%26domain%3Dstackoverflow.com)

[stackoverflow.com](https://stackoverflow.com/questions/37387711/page-loaded-over-https-but-requested-an-insecure-xmlhttprequest-endpoint)

[Assets/Images not being served... · Issue #9852 · angular/angular-cli ...](https://github.com/angular/angular-cli/issues/9852)

![Favicon for github.com](https://you.com/proxy?url=https%3A%2F%2Fwww.google.com%2Fs2%2Ffavicons%3Fsz%3D128%26domain%3Dgithub.com)

[github.com](https://github.com/angular/angular-cli/issues/9852)

[Troubleshoot Cloud Run issues | Cloud Run Documentation ...](https://cloud.google.com/run/docs/troubleshooting)

![Favicon for google.com](https://you.com/proxy?url=https%3A%2F%2Fwww.google.com%2Fs2%2Ffavicons%3Fsz%3D128%26domain%3Dgoogle.com)

[cloud.google.com](https://cloud.google.com/run/docs/troubleshooting)

[GuzzleHttp Exception cURL error 60: SSL certificate problem ...](https://github.com/guzzle/guzzle/issues/1935)

![Favicon for github.com](https://you.com/proxy?url=https%3A%2F%2Fwww.google.com%2Fs2%2Ffavicons%3Fsz%3D128%26domain%3Dgithub.com)

[github.com](https://github.com/guzzle/guzzle/issues/1935)

After creating the SSL certificate using the Google Cloud CLI, there are a few additional steps you need to take to deploy it for your website on Firebase Hosting. Here's what you need to do:

1. Associate the certificate with your Firebase project: Use the following command to associate the certificate with your Firebase project:
   
   ```cpp
   firebase use --add
   ```
   
   This command will prompt you to select your Firebase project and set it as the default for the current directory.

2. Configure Firebase Hosting to use the SSL certificate: Use the following command to configure Firebase Hosting to use the SSL certificate:
   
   ```cpp
   firebase hosting:ssl:certificates create --domain turbotabs.com --certificate new-certificate-name
   ```
   
   Replace `new-certificate-name` with the name of the certificate you created using the Google Cloud CLI.

3. Deploy your website: Finally, use the Firebase CLI to deploy your website to Firebase Hosting. Run the following command:
   
   ```cpp
   firebase deploy --only hosting
   ```
   
   This command will deploy your website, including the SSL certificate, to Firebase Hosting.

After completing these steps, your website should be deployed with the new SSL certificate.

Please note that it may take some time for the changes to propagate and for the SSL certificate to be fully active. Also, make sure that your DNS records are properly configured to point to Firebase Hosting.

Let me know if you need any further assistance!
