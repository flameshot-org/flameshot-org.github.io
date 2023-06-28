+++
title = "Protecting your privacy"
description = "Flameshot is a powerful yet simple to use screenshot software."
date = 2021-05-01T18:20:00+00:00
updated = 2021-05-01T18:20:00+00:00
draft = false
weight = 2
sort_by = "weight"
template = "docs/page.html"

[extra]
lead = "Protecting your Privacy"
toc = true
top = false
+++

Flameshot is an easy to use software, and it gives user lots of room to do what they want. This means that some parts of the software may be used carelessly and can potentially affect your privacy. In this page we try to summaries some of the things that you should consider while using Flameshot (and perhaps any other screenshot tool) to improve your workflow in terms of privacy. To re-iterate, in this page we are focusing on Flameshot, but the same can be applied to any other software that can take a screenshot.

## Upload

One of the features that Flameshot provide is the "Image Upload" <img width="24" class="gui-button" src="https://raw.githubusercontent.com/flameshot-org/flameshot/master/data/img/material/black/cloud-upload.svg" /> tool. With this tool you can quickly upload a screenshot to Imgur. We have put enough warnings and safety checks in place to help the user to manage that:
1. Alerting the user before uploading
   ![](/media/content/docs/advanced/protecting-your-privacy/2023-06-27_12-40_upload_without_confirmation.png)
   ![](/media/content/docs/advanced/protecting-your-privacy/2023-06-28_12-03_upload_configmation_window.png)
2. Allowing user to delete the image after being uploaded
   ![](/media/content/docs/advanced/protecting-your-privacy/2023-06-28_12-10_post_upload_window.png)

Of course, you should remember that once something is online, it is not under your control anymore. So use the upload at your own risk.

## Blur and Pixelation

In general, blurring is not a good privacy protector:

> Hill, Steven, Zhimin Zhou, Lawrence K. Saul, and Hovav Shacham. "On the (In) effectiveness of Mosaicing and Blurring as Tools for Document Redaction." Proc. Priv. Enhancing Technol. 2016, no. 4 (2016): 403-417.
> - DOI: <https://doi.org/10.1515/popets-2016-0047>
> - [Researchgate page](https://www.researchgate.net/publication/305423573_On_the_Ineffectiveness_of_Mosaicing_and_Blurring_as_Tools_for_Document_Redaction)

There are already some software that can use some basic machine learning to de-blur the image and get the content out.

In Flameshot we do not suggest using blur for privacy but rather to attract the focus of the viewer to other parts. If you want to protect your privacy, you can use pixelate tool. It is activated when the size of the blur tool is increased. But please note that, [as have been demonstrated](https://github.com/flameshot-org/flameshot/issues/2439), if the pixelation is used and the pixel size is relatively small, it still can contain enough information (especially when the language, font, and font size is known) to find the content of the pixelated area. I personally suggest using a pixel size that is larger than your line height and each pixel covers at least one character.

The pixelation in Flameshot is merged with the blur tool <img width="24" class="gui-button" src="https://raw.githubusercontent.com/flameshot-org/flameshot/master/data/img/material/black/pixelate.svg" /> if the pixel size is 1, then Flameshot uses blur, and if it is larger than 1, it will use pixelation with specified size. To change any tool size, including pixelation tool, you can either use your mouse scroll or you can directly type the number and wait for half a second. Both these methods can be used 1) while drawing the pixelated area, 2) after selecting the tool and before starting drawing, or 3) after the object is drawn, you can deselect any active tool, and then select the object and change the size.

Of course perhaps the safest way is to draw a filled rectangle using the Rectangle tool <img width="24" class="gui-button" src="https://raw.githubusercontent.com/flameshot-org/flameshot/9748ae015ec21db98036860a48fa75e5cccdccaf/img/buttonIconsBlack/square.svg" />.



