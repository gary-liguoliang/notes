---
layout: post 
title: how to reactivate Google domains - "Domain is not serving because its email address is not verified"
tags:
- Google domains
---

## issue

my domain at `Google Domians` is not working with this error message:
```
Domain is not serving because its email address is not verified. Resend verification email
```

looks like I need to verify my email in the whois info, unluckily, I used a `info@my-domain.com`, this is a typical [Circular dependency](https://en.wikipedia.org/wiki/Circular_dependency):

 - in order to reactivate my domain, I need to access my email
 - in order to access my email, I need to reactivate my domain
 
 since I cannot access `info@my-domain.com`, why don't just update the email address to my gmail? the change will require a verification!
  - I still cannot access my `info@my-domain.com` to approve the whois info update
  - I can use the phone number to verify the change, however, my phone number is not valid anymore!
  
 then I contacted the help, which responses me in 2 minutes, the solution is:
  - update my phone number first, this will not require a verification. 
  - updte my email address, use my phone to verify the change. 
 and it works. 
 
 ## conclusion
  - prefer to use a gmail instead of a xx@my-domain.com in your whois info
  - update you whois info promptly. 
