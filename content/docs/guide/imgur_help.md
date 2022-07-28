+++
title = "Imgur help"
description = "Here we explain some of the Imgur-related issues and topics."
date = 2022-07-29T00:26:24+03:00
updated = 2022-07-29T00:26:24+03:00
draft = false
weight = 2
sort_by = "weight"
template = "docs/page.html"

[extra]
lead = 'Here we explain some of the Imgur-related issues and topics.'
toc = true
top = true
+++


## Creating your own custom Client ID

In Flameshot we have provided our uses a common Client ID with which they can upload their screenshot without creating their own accounts on Imgur, but considering the sheer volume of our ever growing users it can happen more often that the users get an error similar to the following from Imgur which indicates that our hourly quota is full:

> Error transferring https://api.imgur.com/3/image?title=&description=2022-07-12_12-26 - server replied: nginx

To mittigate that, since version 11.0.0, users can use their own Client ID. This way their quota would be independent of other FLamehsot users. To create your own Client ID, lyou can follow the following steps:

1. Login to your Imgur account
2. go to <https://api.imgur.com/oauth2/addclient>
3. register a new application with the following settings:
   ![](/media/content/docs/guide/imgur_help/2022-07-27_20-33_create_client_id_01.png)
4. Copy the "Client ID" of the application you created:
   ![](/media/content/docs/guide/imgur_help/2022-07-27_20-36_create_client_id_02.png)
5. paste it in the correct place in the Flameshot config:
   ![](/media/content/docs/guide/imgur_help/2022-07-27_20-37_create_client_id_03.png)

In case you ever forget your Client ID, you can always find it in <https://imgur.com/account/settings/apps>
    ![](/media/content/docs/guide/imgur_help/2022-07-27_20-39_create_client_id_04.png)
More information available in <https://api.imgur.com> .
