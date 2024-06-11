# home-siem-fun

Welcome to the project. Here will be my notes as I go through this process of building and creating my first SIEM in an on-prem environment, (specifically, at home using DNS logs). I have had a couple of ideas for projects just to peak my interest, namely: 
- Honeypot I can test detections on (cloud-based w/cloud-based siem)
- Replicating common attacks against my own virtual machines (think of Kerberoasting/password spray/etc.) to further teach myself on how else I could pick detections based around certain attacks that are common to certain industries/clients 

But let's just have fun with this and see how it progresses. 

# Starting Out 

I'll be starting out by leveraging open source programs available to me, therefore the [Elastic Stack](https://www.elastic.co/elastic-stack/) seems to be my best bet for now while I continue to learn and see what I really want to do and pick up out of this project. Luckily, things can always change over time, and I can build on top of my infrastructure.

I'm currently following a [guide found from Elastic](https://www.elastic.co/guide/en/elastic-stack/current/installing-elastic-stack.html) to install the Elastic Stack. Reading through it, I see the following are what I'll need for my basic at-home setup: 
- Elasticsearch (the engine that will actually do the indexing and analysis on the data I want)
    - I'm choosing to run Elasticsearch on a Docker container to better give myself peak efficiency (and because if I'm going to do a project, let's make things interesting and fun?) 
- Kibana (UI interface that will actually let me play with the data, presumably make the queries within it?)
- Logstash (event processing pipeline that will allow me to modify events to my liking so that my logs are nice and clean)
- Elastic Agent, or Beats 
    - **Agent** _seems to be_ a more generic onboarding agent that I may be able to onboard to anything, however will need more customization. 
    - **Beats** _seems to be_ a more specific log onboarding agent that will be used for common devices.
    - More research to come on these as I go. 

# Doing Things 

Moving along, let's install Elasticsearch through Docker, via another [guide](https://www.elastic.co/guide/en/elasticsearch/reference/8.14/docker.html). Following the steps and my notes below: 

1. Installed Docker Desktop. 
- Need to allocate 4GB of memory, however the option in Docker Desktop that Elastic is suggesting doesn't seem to exist, since according to Docker Desktop, seems that "You are using the WSL 2 backend, so resource limits are managed by Windows." I solved this issue by creating a [_.wslconfig_](https://learn.microsoft.com/en-us/windows/wsl/wsl-config#wslconfig) file via Powershell (New-Item -Name ".wslconfig") within my %UserProfile% directory and setting the contents as follows: [wsl2] memory=4GB 
2. until 6 is copy pasta 
6. [Created an env variable for Windows](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_environment_variables?view=powershell-7.4#use-the-variable-syntax)
7. aaannnddd I don't feel like dealing with the different Powershell quirks so I just found it easier to install wsl and use the provided curl command to validate my Elasticsearch container through API call. 
![Screenshot of the successful validation of the API call that reads: "Tagline: You Know, for Search"](images/tagline.png)