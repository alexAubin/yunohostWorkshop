# Intro to Self-Hosting with YunoHost

## Recap' of technical notions

- **Router**: device that composes the basic infrastructure of the internet as they relay and route messages between machines ;
- **Server**: a computer running 24/7 and answering requests to provide web pages, email inboxes or instant messages ;
- **VPS**: a virtual private server, meaning a server running somewhere in a datacenter as a virtual machine. You can buy/rent such VPS on providers online like Scaleway or Digital Ocean (though there might be more ethical providers than those...) ;
- **Global IP address**: an address composed of numbers, which identifies a machine on the internet and makes sense on the global scale. You can know your current global IP address on sites like `whatsmyip.com` or `ip.yunohost.org` ;
- **Local IP address**: an address composed of numbers, which indentifies a machine at the scale of a home network. This information setting up a server at home ;
- **Domain name**: a human-readable address composed of names, like `en.wikipedia.org`. This corresponds to a global IP address which in turns generally corresponds to a server ;
- **DNS**: the Domain Name System designates the infrastructure storing the relation between domain names and IP addresses, as well as other informations called DNS records ;
- **Port**: if IP addresses are like building addresses, then ports can be thought of as room number. Ports are complementary to IP addresses and allow programs to discuss with each other across the internet ;
- **Protocol**: a set of formal rules for programs to discuss with each other - much like we generally start conversation with "Hello, how are you ?", say "Please" and "Thank you". HTTP and HTTPS are some well-known protocols (done on port 80 and 443) as well as email (SMTP, IMAP) ;
- **Command line interface**: a way to interact with computers by inputing successive text commands into a terminal to ask the system to perform tasks. While this is more technical than graphical interfaces, it is also arguably more efficient and lightweight in terms of ressources ;
- **SSH**: a protocol typically used to remote control servers via command line interface.
