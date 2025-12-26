# Check your webhooks


Once you have requested the [creation of a webhook](https://soporte.kushkipagos.com/hc/es/articles/14807847881747-Crea-un-Webhook), you can check it as follows:

<!-- theme: warning  -->
>Webhooks for card present payments can only be set up through the Console. Webhooks through API are not supported.
>

1. Access the **Developers** tab, from your Administration Console.

![webhooks_desarrolladores](//images.ctfassets.net/mmjbm94f6iyd/6bjUEZ86zGEUnqr6xoZG8h/c95af23fafb87ed8c2011216d4b0b452/Captura_de_Pantalla_2021-07-29_a_la_s__10.12.26.png)

2. Click on the **Webhooks** section. <br/>

![zona-webhooks](//images.ctfassets.net/mmjbm94f6iyd/4O6fWFVMh53yJ99sKehayG/3525b249fa75ec9c1531f56033666a91/2_webhooks.png)

You will see the list of your created webhooks.

![Webhooks_lista](//images.ctfassets.net/mmjbm94f6iyd/2lWfwEWT0DyCujnLaf9DKH/c1f4d1a7dd2069b33d757a05dc9fdf22/Captura_de_Pantalla_2021-07-29_a_la_s__10.12.59.png)

In the list of webhooks you will be able to know the creation date, the identification alias, the means of payment or product for which it is configured, as well as the connection status.

### Check the URLs and events configured in your webhooks
To consult the data with which one of your webhooks was configured, click on the label corresponding to **Connection Status**, whether it has the legend **Successful** or **Failed**.

### Simulate a connection
You can simulate a notification by clicking on the **Simulate connection** button, and entering the means of payment or product, the event and the corresponding code section.

### Edit the headers of your webhooks
Once your webhooks are created, you will be able to add custom headers for each one (additional to the [headers sent by Kushki](introduction.md)), as follows:

1. Click the edit icon to the right of one of your webhooks.  <br/>
    Add a label and a string for your header.
2. Click on **Save Webhook**.  <br/>
    To add another header, click the __+__ button

<!-- theme: info -->

> You can add up to 4 custom headers.