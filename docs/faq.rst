Frequently Asked Questions
==========================

Overall
-------

Why don't you implement support for ... ?
*****************************************

This app is just about authentication. Anything that is project
specific, such as making choices on what to display in a profile page,
or, what information is stored for a user (e.g. home address, or
favorite color?), is beyond scope and therefore not offered.

This information is nice and all, but... I need more!
*****************************************************

Here are a few third party resources to help you get started:

- https://dev.to/gajesh/the-complete-django-allauth-guide-la3
- https://learndjango.com/tutorials/django-allauth-tutorial
- https://www.youtube.com/watch?v=2QLAc7RJ99s
- https://speakerdeck.com/tedtieken/signing-up-and-signing-in-users-in-django-with-django-allauth
- https://stackoverflow.com/questions/tagged/django-allauth
- https://github.com/aellerton/demo-allauth-bootstrap
- https://github.com/danihodovic/django-allauth-ui

I think I found a security issue... now what?
*********************************************

Please report security issues only to django-allauth-security@googlegroups.com.
This is a private list only open to long-time, highly trusted django-allauth
developers, and its archives are not public.

You may also want to subscribe to django-allauth-announce@googlegroups.com to
get notified about security releases.


Troubleshooting
---------------

The /accounts/ URL is giving me a 404
*************************************

There is no such URL. Try ``/accounts/login/`` instead.

When I attempt to login I run into a 404 on /accounts/profile/
**************************************************************

When you end up here you have successfully logged in. However, you
will need to implement a view for this URL yourself, as whatever is to
be displayed here is project specific. You can also decide to redirect
elsewhere:

https://docs.djangoproject.com/en/dev/ref/settings/#login-redirect-url

When I sign up I run into connectivity errors (connection refused et al)
************************************************************************

You probably have not got an email (SMTP) server running on the
machine you are developing on. Therefore, ``allauth`` is unable to send
verification mails.

You can work around this by adding the following line to
``settings.py``::

    EMAIL_BACKEND = 'django.core.mail.backends.console.EmailBackend'

This will avoid the need for an SMTP server as emails will be printed
to the console. For more information, please refer to:

https://docs.djangoproject.com/en/dev/ref/settings/#email-host


Why did you just close my issue?
********************************

Time is limited and I have to pick my battles. Please do not file the following
types of issues:

- **Support questions, installation instructions, "How do I...?":** please direct
  these questions elsewhere, for example here:
  https://stackoverflow.com/questions/tagged/django-allauth

- **Documentation related complaints:** while the documentation can most certainly be
  improved, I am adhering to the debatable principle that keeping open issues
  around with respect to documentation is not very helpful in improving things.
  Please step in and file a pull request if you feel there is something unclear.

- **Project specific integration trouble:** In cases where ``allauth`` is just
  one piece of the puzzle and for example a stack trace indicates another
  module crashing, please try to come up stripped version of the issue where it
  is clear that ``allauth`` is the one that is misbehaving.

- **Social login trouble:** There are many reasons why the social login for a
  provider is not working for you. Common causes are errors in setting up the
  credential for the OAuth app and/or having setup invalid callback URLs. Filing
  issues stating that things are not working for you is not very helpful. It is
  simply not feasible to debug your specific setup. If you really do think that
  there is an issue in ``allauth``, please do the initial debugging and analysis
  yourself, and, provide detailed information in the issue. If the issue does
  not point to any concrete issue in ``allauth``, it is likely to get closed.
