# Import External Content

The Sunbird platform allows users with Content Creator role permissions to create content and upload content from external sources to the Sunbird content library. You can upload content from external websites such as YouTube, Dailymotion, etc. This section explains the procedure to enable a Sunbird instance to host content from external sources.

### Intended Audience <a href="#intended-audience" id="intended-audience"></a>

Instance administrator

### Prerequisite <a href="#prerequisite" id="prerequisite"></a>

Ensure that the following is enabled for Sunbird instance to host content from external domains:

* You are logged in as the organization administrator
* You have access to set the environment variables

### Whitelisting a Domain <a href="#whitelisting-a-domain" id="whitelisting-a-domain"></a>

There are legal considerations to be taken care of before whitelisting any domain on Sunbird. Such information will be updated soon.

### Configuring the Domain <a href="#configuring-the-domain" id="configuring-the-domain"></a>

To enable a Sunbird instance to host content from external source:

1. Set the **sunbird\_extcont\_whitelisted\_domains** variable in the **Player Service** to whitelist an external website. Add the variable into the config file.

> Example: To allow an instance to host content from an external source such as **Wordpress**, configure the environment variable in the following format: SUNBIRD\_EXTCONT\_WHITELISTED\_DOMAINS: env.sunbird\_extcont\_whitelisted\_domains ||’wordpress.com’

On successful configuration of the external domain, the content creators of the organization can upload content from external sources.

For details on uploading Sunbird Content.
