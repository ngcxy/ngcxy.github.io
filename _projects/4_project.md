---
layout: page
title: 'Custom TCP Protocol for Fast Reliable Transfer'
description: an IP based file-transfer utility overcomes loss and delay
img: assets/img/4/overview.png
importance: 48
category:
giscus_comments: true
---

This is a Lab from Course *Internet and Cloud Computing* by Prof. Young Cho. 
Watch this demo video by one of my teammates on [Youtube](https://youtu.be/Z-tlv-LT8fo)

---

We developed a file transfer program (like scp or ftp) that uses our custom protocol,
and emulated the delay and the loss rate of the link using the delay node. 

### Architecture

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/4/overview.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

The custom protocol is based on datagram socket between the sender and the receiver. 
After handshaking, the sender sends the packets along with the total file size and packet number.
After first transmission completes, client checks the packets and requests for retransmission if there are missing packets.
Sender will transmit the missing packets through UDP.

Multiple threads is implemented for both server and client to enhance link utilization and ensure reliability through packet counting.

Difference with commonly used TCP:
- Only handshake at the beginning, allowing connectionless transfer
- Ensure reliability on the application layer, not protocol itself
- Reduced overhead and less controlled limitations(flow, congestion) compared to TCP

### Test

We tested our system under various different conditions with MTU of 1500 and 9000, utilizing md5 to validate the file integrity.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/4/result.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

