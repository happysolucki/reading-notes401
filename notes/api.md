# API Deployment

## Django Settings Best Practices

Optimally, we'd want to do these things when configuring a Django project:

- Keep settings in environment variables
- Write default values for production configuration (excluding secret keys and tokens)
- Split settings into groups: Django, third-party, project
- Follow naming conventions for custom (project) settings

We also want to avoid hardcoding sensitive settings, and not put them in VCS.

## SSH

SSH, or Secure Shell, is a remote administration protocol that allows users to 
control and modify their remote servers over the Internet. The service was created 
as a secure replacement for the unencrypted Telnet and uses cryptographic techniques 
to ensure that all communication to and from the remote server happens in an encrypted 
manner. It provides a mechanism for authenticating a remote user, transferring
inputs from the client to the host, and relaying the output back to the client.
