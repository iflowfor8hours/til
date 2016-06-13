
# Containers and your pipeline

matt urbanski, contino, qcon 2016

---

# Who am I

Note: I'm Matt Urbanski, the technology principal for a company called Contino. I've been doing CD and devops consulting for about 5 years now, and prior to that was a sysadmin and developer for many years. I've worked in finance, retail, banking, insurance and many other industries across every continent that needs devops. I have always been interested in the problem of source to binary control of application delivery, and like thinking about the challenges around artifact promotion, configuration management, service discovery, and scaling.

---

# Who is Contino

Note: Contino is a devops consultancy based in London, but very recently opened an office in NY. We're about 50 strong now and 2 and a half years old. We are a well-funded and targeted devops startup that offers enterprise devOps transformations, continuous delivery consulting, cloud infrastructure, and container technology. We also do some custom software delivery projects where appropriate.

---

# What is this about?

How do continers and pipelines fit together?

Miley Cyrus photo?

Note: Containers have changed the way that many companies build, test, and distribute software. There has been a sprawl of different approaches that integrate containerization and pipeline technologies. The diversity of ways in which I have seen the two concepts used in concert has been staggering, and like everything else with a sudden, massive uptick in popularity, mixed results.

I would like to talk about what advantages containerization can offer your software organization in terms of the three knobs speed, quality, and cost, which in my mind is akin to flexibilty.

---

# 

Note: There is a definite separation of concerns between the use of container techology for your pipeline itself, and the use of it IN your pipeline for your software. When these two things come together, a pattern of reuse often emerges where one enables the other making your infrastructure ultimately simpler and easier to reason about, but it is a long road to get there.

---

# Containerization of your pipeline

Note: Containerization of your pipeline itself is the lower hanging of the fruit, as it does not require touching your production infrastructure, and can still offer massive gains in productivity and flexibility. What I mean by containerizing your pipline I mean shifting the infrastructure that your pipeline runs on to containers. The output artifacts themselves remain whatever they were, be it packages or images or tarballs or whatever, but all build, test, and deployment activities occur inside containers.

---

# Experiment

Note: Moving your existing pipeline into Docker containers, piece by piece.


---

# Experiment

Note: Start by migrating your build slaves and testing environment into containers. Begin with the Kitchen sink approach and just toss your whole build slave provisioning process into a container and move on. You will wind up with FAT continers, but a consistent build environment that boots fast and disappears when they are not needed, provided that you can wrap your build in a docker run command and feed the build parameters in via environment variables or runtime parameters.

Note: Use separate containers for build and test, to begin separating out the concerns and familiarizing yourself and your engineers with passing data between containers. Even though these are not ideal as of yet, you can being paring them down

---

# Advantages

---

# Pitfalls and common traps

(pitfall logo)

# 

---



