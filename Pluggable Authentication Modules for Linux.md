Pam is a system of libraries that unify the handling of authentication tasks for different services or apps inside Linux. The most important aspect of PAM is that it make it easy to configure different approaches for authentication in a dynamic way for multiple services. From the standpoint of the system administrator, the configuration files bridge the gap between the apps and the inner workings of PAM.

There are 4 main modules in PAM that are related to each other but handle different aspects of the libraries. Those are the following:

1. Auth: This module is in charge of authenticating a user and handling the response to the challenge issued by the authenticator.
2. Account: This module validates the limits and permissions set on the account that succesfully authenticated. Checking passwords is not done here but on auth.
3. Password: The password module handles password changes according to different rules set up by the system admin.
4. Session: Sets up session settings like limits, environment variables, message of the day, etc.

# pam.conf

A pam.conf file is read after an app that uses pam authentication is started. The file or files in pam.conf.d will define how authentication takes place and what happens if any authentication fails. The syntax is the following:

```pam.conf
service type control module-path module-arguments
```

If a file inside pam.conf.d is used, the syntax is the same, but the service field will be ommitted, as the name of the service will be the name of the file.

- Service: The name of the service is usually the name of the application like su or login.
- type: The management group that the rule corresponds to. Valid fields are auth, account, password, and session. If one of the valid fields is prepended with a -, loading errors will fail silently.
- control: What happens if the rule fails. 
	- required: Returns failure after the remaining stacked modules have been invoked.
	- requisite: Like required, but if failure occurs, control is returned to the application or to the superior PAM stack.
	- sufficient: If it succeeds and previous modules succeeded as well, it returns success.
	- optional: The success or failure is only important if this is the only module available.
	- include: Include all lines of given type from the configuration file specified as an argument to this control.
	- substack: Differs from include in the evaluation of the done and die actions in a substack does not cause skipping the rest of the complete module stack, but only of the substack. (No idea what this means).
- module-path: the full filename of the PAM to be used by the application, or a relative pathname from the default module location: /llb/security or /lib64/security/
- module-arguments: space separated list of tokens that can be used to modify the specific behavior of a PAM. Such arguments will be docuemnted for each individual module. 



