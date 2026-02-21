
Brave logo
how to substitute podman for docker compose





Ask
All
Images
News
Videos
Goggles

To substitute Podman for Docker Compose, you have two main options: podman-compose (a Python-based tool) or native podman compose (built into Podman 3.0+). 

Using podman-compose
Install it via pip3 install podman-compose.
Use the same docker-compose.yml files directly.
Run commands like:
podman-compose up -d
podman-compose down --volumes
podman-compose logs -f

Note: Podman expects single internal ports (e.g., 27017) to be quoted: ports: - "27017". 
Using Native podman compose (Recommended)
Available in Podman 3.0+ (and enhanced in later versions).
No extra installation needed if Podman is updated.
Use the same syntax:
podman compose up -d
podman compose down --volumes
podman compose logs -f

Supports Docker Compose v2.2+ and is the future-proof option. 
Important Notes
DNS Resolution: By default, Podman networks may not resolve container names. Install podman-plugins and dnsmasq to fix this. 
Rootless Containers: Podman runs rootless by default—images and data are stored per-user, not system-wide. 
Session Persistence: Containers stop when you log out. Use sudo loginctl enable-linger to keep them running. 
✅ Best Practice: Use podman compose (native) for new projects. Use podman-compose only if you need legacy compatibility. 

AI-generated answer. Please verify critical facts.
Elaborate
What are the key differences between podman-compose and native podman compose?
How do I configure DNS so containers can resolve each other's names?
Does podman compose support Docker Compose v3 features?

Copy

Share



🌐
🌐
🌐
🌐
+2
Ask a follow-up question

🌐
Red Hat
redhat.com › en › blog › compose-podman-pods
Moving from docker-compose to Podman pods
November 20, 2025 - It sounds like the solution for me. I spent some time trying to learn how to write these things and eventually came across the Kompose tool. Kompose converts docker-compose files into Kubernetes definitions.
🌐
Medium
dale-bingham-soteriasoftware.medium.com › how-i-got-my-docker-compose-yml-to-work-switching-to-podman-compose-5252856c6eea
How I got my docker-compose YML to work switching to podman-compose | by Dale Bingham | Medium
December 2, 2022 - Summary: Install podman 4. Install pip3. Install podman-compose. Install podman-plugins. Wrap internal-only single ports in quotes.

Videos
10:15
🌐
YouTube
Docker to Podman – How Podman eases switching - YouTube
October 15, 2024

🌐
youtube.com
Can Podman actually replace Docker for Running Linux ...

🌐
youtube.com
Podman 3 and Docker Compose - How Does the Dockerless ...

🌐
youtube.com
It's Making Me REPLACE Docker...
16:05
🌐
YouTube
Is it time to switch? // Docker vs Podman Desktop - YouTube
January 16, 2024
244K
14:33
🌐
YouTube
It's Making Me REPLACE Docker... - YouTube
October 5, 2023
View all
🌐
Red Hat
redhat.com › en › blog › podman-compose-docker-compose
Podman Compose or Docker Compose: Which should you use in Podman?
November 20, 2025 - Docker Compose was written in Python and communicated with the Docker daemon using its REST API. When Podman was released in 2018, we focused entirely on compatibility with the Docker command-line interface (CLI) and did not include support for the API. Therefore, Podman initially could not be used with Docker Compose.

🌐
Reddit
reddit.com › r/podman › [deleted by user]
what is podman alternative of docker compose?
April 12, 2024 - Red hat has stated that they aren't putting any energy into podman compose. Everything is going into quadlet, as it is an avenue towards kubernetes, and presumably red hat openshift. I use quadlets for rootful and rootless containers and it works well for me. ... Or even docker-compose.
🌐
Podman
lists.podman.io › archives › list › podman@lists.podman.io › thread › 5KXPD6XGPIT465DR25N423X6VW2SWPKJ
podman equivalent for docker-compose? - Podman - Podman List Archives
Docker substitution and file... ... Robert P. J. Day ... was extolling the virtues of podman to a colleague, who seemed interested but asked what the podman-based alternative was for "docker compose". rather than mislead her, i thought i would ask the experts.
🌐
My Developer Planet
mydeveloperplanet.com › 2023 › 06 › 07 › podman-equivalent-for-docker-compose
Podman Equivalent for Docker Compose
May 28, 2023 - In this blog, you will learn how to use Podman with the built-in equivalent for Docker Compose. You will learn how to use Podman ‘kube play’ and how to deploy your Podman Pod to a local…

🌐
Reddit
reddit.com › r/podman › what's the current canonical way to run docker compose files with podman 4.x?
r/podman on Reddit: What's the current canonical way to run Docker compose files with Podman 4.x?
December 17, 2023 - Hello,I vaguely remember seeing various ways to run Docker compose files with Podman over the years, but didn't pay much attention because I didn't have to use them. Recently, however, I can across a couple of Docker compose files I'd like to experiment with.What is the most current and "canonical" way to run Docker compose files with Podman these days??? Can you suggest some guides on how to do it?And in case versions matter, I know Podman 5.0 just came out, but I'm still on the 4.x series, including 4.6.1 on my Rocky Linux 9 system.
Top answer
1 of 2
15
Nowadays Podman supports docker compose, so on a system with Podman installed you will want to install the docker-compose package. After that you can use the podman compose commands and it won’t complain. Good luck though, I had an awful time getting half my containers working. It’s not exactly the “drop in replacement” for Docker that they market it as.
2 of 2
6
Honestly, skip the compose file and use Quadlet.
🌐
Maverick Kaung
mavjs.org › post › podman-pods-instead-of-docker-compose
Using Podman pods Instead of docker-compose | Maverick Kaung
While in the same directory as this configuration file (named: docker-compose.yaml), you can bring up these applications by executing: ... When podman came out, there was a tool created later on called podman-compose to help ease transition from docker & docker-compose.

🌐
DZone
dzone.com › software design and architecture › containers › podman compose vs docker compose
Podman Compose vs Docker Compose
August 2, 2023 - Take a look at Podman Compose, exploring how to use Compose files according to the Compose Spec in combination with a Podman backend.

Find elsewhere
Google
Bing
Mojeek
🌐
DataCamp
datacamp.com › tutorial › podman-compose
Podman Compose: A Rootless Alternative to Docker Compose | DataCamp
2 weeks ago - Podman Compose parses that file and runs the equivalent podman commands to start your containers. It's doing the translation work for you, so you don't have to manually convert Compose syntax into Podman CLI commands.

🌐
OneUptime
oneuptime.com › blog › post › 2026-01-26-podman-docker-alternative › view
How to Use Podman as Docker Alternative
1 month ago - # Install podman-compose # Python-based tool that reads docker-compose.yml files pip install podman-compose # Or use Podman's built-in compose support (Podman 3.0+) # This provides native compose functionality podman compose --help

🌐
Podman
docs.podman.io › en › v5.6.2 › markdown › podman-compose.1.html
podman-compose — Podman documentation
If you want to change the default behavior or have a custom installation path for your provider of choice, please change the compose_providers field in containers.conf(5) to compose_providers = ["/path/to/provider"]. You may also set the PODMAN_COMPOSE_PROVIDER environment variable.
🌐
My Developer Planet
mydeveloperplanet.com › 2023 › 06 › 21 › podman-compose-vs-docker-compose
Podman Compose vs Docker Compose
May 28, 2023 - In the output after executing the podman-compose command, you can see that a default network docker-compose_default is created. A network alias helloservice-1 is created for container 1 and a network alias helloservice-2 is created for container 2. Enter container 1 and try to access the endpoint of container 2 using the network alias. Beware to use the internal port 8080 instead of the external port mapping to port 8081! $ podman exec -it docker-compose_helloservice-1_1 sh /opt/app $ wget http://helloservice-2:8080/hello Connecting to helloservice-2:8080 (10.89.1.3:8080) saving to 'hello' hello 100% |*********************************************************************************************************************| 13 0:00:00 ETA 'hello' saved

🌐
Medium
medium.com › @i190548 › migrating-from-docker-compose-to-podman-compose-how-to-make-the-switch-8798e6bb496d
Migrating from Docker Compose to Podman Compose: How to Make the Switch | by Azka Iftikhar | Medium
March 22, 2023 - This command will start all of the services defined in your Podman Compose file. You can also use the following command to stop your application: ... In this blog post, we’ve gone over the steps required to migrate from Docker Compose to Podman Compose. While the syntax of Podman Compose is similar to Docker Compose, there are some differences that you’ll need to be aware of.

🌐
Better Stack
betterstack.com › community › guides › scaling-docker › podman-compose
Podman Compose Tutorial for Beginners | Better Stack Community
If you run into errors, check for Docker-specific features like build.context quirks or named volumes that may behave slightly differently under Podman. Podman Compose is a versatile tool for managing multi-container applications, offering a secure and lightweight alternative to Docker Compose.

🌐
Oracle
docs.oracle.com › en › learn › podman-compose › index.html
Use Compose Files with Podman
February 28, 2024 - Install the podman-docker package. ... Installing Compose in a standalone manner as described here requires using docker-compose instead of the standard syntax used when using the Docker utility of docker compose. In other words substitute the docker compose up syntax with docker-compose up instead.
🌐
Ovyerus
ovyerus.com › posts › podman-from-docker
Moving to Podman from Docker & Docker Compose - Ovyerus
... Besides this, Podman acts almost exactly how you would expect Docker would, which is really cool. Podman also provide their own alternative to Docker Compose called Podman Compose.

🌐
Oracle
docs.oracle.com › en › learn › ol-podman-compose › index.html
Use Compose Files with Podman on Oracle Linux
October 3, 2025 - Install the podman-docker package, which enables Podman to work natively with Docker commands. ... Download and install Compose standalone.
🌐
DEV Community
dev.to › arafetki › podman-the-docker-alternative-or-fierce-competitor-4n3h
Podman : An Alternative To Docker ? - DEV Community
June 19, 2023 - Pod compose utilizes the same syntax allowing you to define and manage multi-container applications using the same approach or even using existing "docker-compose.yml" files. As for Docker desktop, Podman also comes with Podman desktop offering enhanced features that make it more powerful and streamlined.

🌐
Stack Overflow
stackoverflow.com › questions › 70804231 › podman-equivalent-to-docker-compose-environment-variable-substitution
Podman equivalent to Docker Compose environment variable substitution - Stack Overflow
Top answer
1 of 1
1
In your example, you can use bash shell expansion:
IMAGE_TAG="v0.0.0"
printf "
version: '2.2'
services:
  example-service:
    image: busybox:${IMAGE_TAG:-latest}
    scale: ${REPLICAS:-1}
    command: ls
"
Yields:
version: '2.2'
services:
  example-service:
    image: busybox:v0.0.0
    scale: 1
    command: ls
kubectl (!) supports piping stdin directly (and podman may too), so you can in theory (though it's nearly always better to persist the output to a file so that you can commit a record of what you apply):
IMAGE_TAG="v0.0.0"
printf "
version: '2.2'
services:
  example-service:
    image: busybox:${IMAGE_TAG:-latest}
    scale: ${REPLICAS:-1}
    command: ls
" \
| kubectl apply --filename=-
I have begun using yq to template my YAML files but previous simply used sed. Using the former, you can use a YAML query syntax to path to values that you want to replace and, with sed, of course, regular expressions. Helm and other (Kubernetes) tools use Go templating to solve a similar problem and it remains something of an outstanding issue (unless you're happy to adopt *nix's philosophy of having tools that do one thing well)
Next
What's the current canonical way to run Docker compose files with Podman 4.x?
🌐
reddit.com › r › podman › comments › 1bk4nee › whats_the_current_canonical_way_to_run_docker
Nowadays Podman supports docker compose, so on a system with Podman installed you will want to install the docker-compose package. After that you can use the podman compose commands and it won’t complain. Good luck though, I had an awful time getting half my containers working. It’s not exactly the “drop in replacement” for Docker that they market it as. Answer from Deleted User on reddit.com

Resources
Brave Search Premium
Brave Search Help
Transparency Report
Report a security issue
Status
Products
Brave Browser
Brave Search
Brave Wallet
Brave Talk
Brave Firewall + VPN
Brave Playlist
Brave News
Brave Rewards
Brave Search API
Brave Ads
Policies
Privacy Policy
Terms of Use
