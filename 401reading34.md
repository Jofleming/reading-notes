# API Deployment

## Django Settings Best Practices

[Reading](https://djangostars.com/blog/configuring-django-settings-best-practices/)

Different environments. Usually, you have several environments: local, dev, ci, qa, staging, production, etc. Each environment can have its own specific settings (for example: DEBUG = True, more verbose logging, additional apps, some mocked data, etc). You need an approach that allows you to keep all these Django setting configurations.

Sensitive data. You have SECRET_KEY in each Django project. On top of this there can be DB passwords and tokens for third-party APIs like Amazon or Twitter. This data cannot be stored in VCS.

12 Factors is a collection of recommendations on how to build distributed web-apps that will be easy to deploy and scale in the Cloud. It was created by Heroku, a well-known Cloud hosting provider.

As the name suggests, the collection consists of twelve parts:

1. Codebase
2. Dependencies
3. Config
4. Backing services
5. Build, release, run
6. Processes
7. Port binding
8. Concurrency
9. Disposability
10. Dev/prod parity
11. Logs
12. Admin processes

### Django Settings: Best Practices

* Keep settings in environment variables.
* Write default values for production configuration (excluding secret keys and tokens).
* Don’t hardcode sensitive settings, and don’t put them in VCS.
* Split settings into groups: Django, third-party, project.
* Follow naming conventions for custom (project) settings.



## SSH Tutorial

[Reading](https://www.hostinger.com/tutorials/ssh-tutorial-how-does-ssh-work)

SSH, or Secure Shell Protocol, is a remote administration protocol that allows users to access, control, and modify their remote servers over the internet.

SSH service was created as a secure replacement for the unencrypted Telnet and uses cryptographic techniques to ensure that all communication to and from the remote server happens in an encrypted manner. It provides a mechanism for authenticating a remote user, transferring inputs from the client to the host, and relaying the output back to the client.

[Back](README.md)