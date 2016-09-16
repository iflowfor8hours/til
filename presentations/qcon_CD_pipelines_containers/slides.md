# Containers and your pipeline

matt urbanski, contino, qcon 2016

---

# Matt at Contino

Note: I'm Matt Urbanski, the technology principal for a company called Contino. I've been doing CD and devops consulting for about 5 years now, and prior to that was a sysadmin and developer for many more. I grew up in C++ and high frequency finance, which is a sloppy world when it comes to development practices. I was attracted to the relative sanity and consistency of configuration management and good practices of the devops world. Since then, I've worked in retail, banking, insurance, and many other industries, and seen challenges of all types. I have always been interested in the processes around source code to binary to running software, and I like solving the challenges around artifact promotion, configuration management, service discovery, and scaling.

---

# Who is Contino

Note: Contino is a devops consultancy based in London, but recently we opened an office in NY. We're about 50 strong now and 2 and a half years old. We are a well-funded and targeted professional services startup that offers enterprise devops transformations, continuous delivery consulting, cloud migration support, and containerization strategy, among other things. We're a docker premier partner and have a lot of experience with containerization and getting big enterprises into them.

---

# How do continers and pipelines fit together?

Note: Containers have changed the way that many companies build, test, and distribute software. There has been a sprawl of different approaches that integrate containerization and pipeline technologies such as Docker plugins for jenkins, teamcity, go.cd, and every other CI or build tool. The diversity of ways in which I have seen the two concepts used in concert has been staggering, and like everything else with a sudden, massive uptick in popularity, there have been mixed results. 

Note: There is a definite separation of concerns between the use of containers to support your pipeline itself, as opposed to the use of them IN your pipeline for the software you are releasing. When these two things come together, a pattern of reuse often emerges where one enables the other making your infrastructure ultimately simpler to digest and easier to reason about.

---

# Containerization of your pipeline

Note: Containerization of your pipeline itself is the lower hanging of the fruits compared to your applications, as it doesn't require touching your production infrastructure, and can still offer massive gains in productivity and flexibility. What I mean by containerizing your pipline is changing the infrastructure that your pipeline and CI environment run on and turning those machines into containers. The output artifacts themselves remain whatever they were, be it packages, images, tarballs, or whatever, but all build, test, and deployment activities occur inside containers.

---


# Why though?

* Cheap
* Flexible
* Consistent

Note: The advantages of this over static infrastracture are cost savings, increased flexibility, and consistency. 

---

# Cost

Note: The cost savings come in the form of not having to maintain your build infrastructure, not having to keeping it running, configured, and monitored even when you're not using it. Even if your builds are occurring in-house on static machines, containerizing gives you the ability to smoothly leverage or experiment with public or private clouds inexpensively even if that fits the needs of only some of your applications. 

---

# Flexibility and Consistency 

Note: Containerizing your build infrastructure has the added advantage of being able to run builds anywhere that a container can run. Which to me means that my local box has the EXACT SAME configuration and infrastructure that my CI environment does. This ultimately leads to fewer broken builds and happier developers. There are few things that annoy me more than the classic "works on my machine" situation caused by inconsistency in development machine and CI environments. The ability to run all your build infrastructure locally also allows developers and operations people to experiment with it, without disturbing others using it. This brings with it the added advantage of being able to redeploy it whenever or wherever you see fit, getting resilience essentially for free.

---

# Execute!

Note: Start by migrating your build and test slaves and into containers. I'm running with the assumption that we're talking about a web application, but the same applies for mobile applications and to some extent desktop. 

---

Note: I would begin with the Kitchen sink approach and move your whole build slave provisioning process into a container and just move on for the time being. If you have chef, puppet, or ansible managing your build nodes, this will feel heavy handed, but the first pass often is and you can optimize later. You will wind up with FAT containers initially. A consistent build environment that boots fast and disappears when not needed, will feel good and be easier to manage no matter what. This will also get teams used to wrapping builds into containers and feeding the build parameters in via environment variables or runtime parameters. Creating good scripting that lives in version control with your application will encourage virtuous behavior and running builds locally in a known environment before checking things in. Creating easy to understand Dockerfiles or provisioning will also encourage innovation in your build space.

Note: Use separate containers for separate build phases, as you would with traditional, static infrastructure. Begin separating out the concerns and familiarizing yourself and your engineers with how passing data between containers works by way of passing build outputs downstream to other containers.

---

# Traps

Note: Building thin, light, single purpose containers is fun. I am a person with an operations background and a deeply rooted belief in the UNIX philosophy of do one thing and do it well. I have in the past over optimized and wasted far more time trying to get container images under an imaginary limbo stick of 10 megabytes or whatever arbitrary goal I came up with. Not everyone will have this problem, but because there are so many ways to do this, it can be an enormous timesink. Timebox these activities as best you can, as the ROI on this diminishes quickly. If you have a good container base for your application containers, then leveraging that can help in many ways.


---

# Operational complexity

The operational complexity of running containers is initially high, but should not have the same curve as adding more traditional infrastructure that has to be monitored and cared for.

---

# Learning from the past

The advantages of containerizing your application infrastructure have been espoused at length at this conference and just about everywhere else for the past couple of years, so I'm not going to go into detail about that here.

---

# consistency in quality

One of the greatest benefits I've seen to this is having a consistent approach to both your build and deployment environments, and gets engineers thinking about what else can be containerized, to help make and environment that is easy to explain and reason about. It also mitigates provider lock-in, as just about any environment can run a container.

---


