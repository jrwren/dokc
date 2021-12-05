---
title: Failing Digital Ocean Kubernetes Challenge
published: true
description:
tags: failure, digitalocean, kubernetes
cover_image: https://harborbeachlighthouse.org/wp-content/uploads/2017/11/IMG_0396-1.jpg
---

Goal: Vanilla k8s install

The first thing is signing up with Digital Ocean. Apparently, I've never used their product, so I had to signup. When entering my credit card information, I'm a little disappointed that they don't support the autofill features of my browser. I was able to autofill the CC number, but I had to type my name and address.

Apparently, this page attempts to verify identity using the CC and it does it before clicking submit. The "Save Payment Method" button is disabled if it cannot verify that the card details are correct, but it doesn't feedback about what is invalid. I use this CC everywhere on the internet but DOs form will not validate for me. I wonder how much money DO is leaving on the table by not accepting valid cards and identity. I know everything on this form is correct. I use the exact same details to buy things all over the internet. DO doesn't accept it.

It took me a good couple of minutes of staring at the form to realize the CVC is required and not filled in. Terrible UX. DO should be ashamed. There was NO feedback. What should have happened: the field should have been red, there should have been a \* next to the field. There should have been text which said, "CVC required". I'm starting to see why there are only 6 requests in the GH repo so far.

Now that I see the welcome page and can access the control panel, I'm going to follow this to get a k8s cluster up. https://docs.digitalocean.com/products/kubernetes/quickstart/

I'm in Ann Arbor, MI and so I am not going to use the default Amsterdam region and instead I'll select NYC3.

There is a warning by default that says `Important: You have reached the 1 Droplet limit on your account. Request Increase` I click the request button and say I want 3 droplets. Since I'm new to DO and not 100% sure what a droplet is, I'm a little surprised, but I guess I'll assume that a droplet is not a container like I thought, but is a VM. I want 3 VMs because I know that I need at least that many to run a k8s cluster.

I also change the node type since I won't be doing much with this cluster. The $10/mo nodes seem like plenty.

The "Create Cluster" button is disabled. No feedback on the form again. I wonder if DO is using some web framework that doesn't support Safari. I thought the web was beyond this at this point, but either DO web devs aren't eating their own dog food, or they ignore users like me. :cry:

I try lowering the node count from 3 to 1. This pops up a "Recommended:
A minimum of 2 nodes is required to prevent downtime during upgrades or maintenance. Request Increase" message. Ok, that makes sense, but... the plus button to increase the node count is disabled. I can't use that, but I can type 2 into the textbox and the message goes away.

At this point, I do find it strange that AWS will let me rack up a giant bill as soon as they have my billing info, but DO is limiting me to 1 droplet OOTB, even though they have my billing info AND my account has a $60 credit on it. 🤔

At this point I give up and leave this form and start exploring my account. Settings has the droplet listed too so I try to raise it there. Same thing, it looks like a human reviews these raise requests. I wonder what AWS limits are like by default and I search for it. I see something about 20 instances per region. Seems more reasonable.

I can't move on, so I'll have to wait.

About an hour later I received this email:

```
Thank you so much for reaching out to us for getting the Droplet limit increased, Unfortunately, your account does not qualify for the requested limit based on our internal assessment guidelines.

We would be happy to consider your request for a higher Droplet limit after you have established additional billing history with us with no instances of abuse.

We hope you would understand we have these guidelines in place to ensure the stability of our platform.
```

Well, I guess I won't be playing with k8s on DO.
