## Background
In the desktop software, source code are compiled before it become built binaries. The binaries further wrapped with installer and the process is called mastering. Each masters is further packaged into a releasable media before being shipped to the end users. For example, DVD/CD or online installation.

## Publishing System
I'm designing & working on the publishing system. It packages the software into a releasable media based on the requirements of the respective product manager. Currently it supports packaging of TAR, ISO, IMG, which will then be burnt into DVD/CD for historical releases. And on the modern releases, we also supports an online releases to Akamai CDN. For online releases, it separated into different types, Download manager where users get its downloader client and retrieve the actual software with that downloader client. Another type of online releases is the On-Demand Installation Services where user can download the actual software without requiring a separate downloader client. Having a centralized system not only helps to package these media across all of our software releases, but also to control, identify and manage what is being release to the end users.


## High Level Architecture / Diagram
The architecture of the system comprises of a client app, dispatcher server, storage servers, production bots, staging bots, API Server, Database, Dashboard, Media File Server, and Akamai CDN. In high level picture, the main flow will be as follows: The client app will send jobs to a dispatcher which handles the load balancing of jobs and send them to the available bots. Bots do the actual packaging work which will take some time. Inside the bots, it will download the software installer in a very efficient algorithms from the storage servers. Once the media packages is done, it uploads to the media server and staging server. In the staging server, it consolidates packages to upload online media in batches to Akamai CDN. Those are the high level main use case, but inside each server/components, it will handles many other scenario to cater for different use cases.

![architecture_diagram](https://user-images.githubusercontent.com/493668/122426862-2d44fb80-cfc3-11eb-8380-faddeedbed2e.jpg)

