# Containers and your pipeline

matt urbanski, contino, qcon 2016

---

# Matt at Contino

Note: I'm Matt Urbanski, the technology principal for a company called Contino. I've been doing CD and devops consulting for about 5 years now, and prior to that was a sysadmin and developer for many years. I've worked in finance, retail, banking, insurance and many other industries across every continent that needs devops. I have always been interested in the problem of source to binary control of application delivery, and like thinking about the challenges around artifact promotion, configuration management, service discovery, and scaling.

---

# Who is Contino

Note: Contino is a devops consultancy based in London, but recently we opened an office in NY. We're about 50 strong now and 2 and a half years old. We are a well-funded and targeted professional services startup that offers enterprise devops transformations, continuous delivery consulting, cloud infrastructure, and containerization. 

<!-- .slide: data-background="./image1.png" -->

---

# How do continers and pipelines fit together?

Note: Containers have changed the way that many companies build, test, and distribute software. There has been a sprawl of different approaches that integrate containerization and pipeline technologies such as Docker plugins for jenkins, teamcity, and every other CI tool. The diversity of ways in which I have seen the two concepts used in concert has been staggering, and like everything else with a sudden, massive uptick in popularity, there have been mixed results. 


---

# 

Note: There is a definite separation of concerns between the use of containers to support your pipeline itself, as opposed to the use of it IN your pipeline for the software you are releasing. When these two things come together, a pattern of reuse often emerges where one enables the other making your infrastructure ultimately simpler to digest and easier to reason about.

---

# Containerization of your pipeline

Note: Containerization of your pipeline itself is the lower hanging of the fruits, as it doesn't require touching your production infrastructure, and can still offer massive gains in productivity and flexibility. What I mean by containerizing your pipline is changing the infrastructure that your pipeline runs on and turning those machines into containers. The output artifacts themselves remain whatever they were, be it packages or images or tarballs or whatever, but all build, test, and deployment activities occur inside containers.

---


# Why though?

* Cheap
* Flexible
* Consistent

Note: The advantages of this over static infrastracture are cost savings, increased flexibility, and consistency. 

---

# Cost

Note: The cost savings come in the form of not having to maintain your build infrastructure, keeping it running, fed, and watered even when you're not using it, assuming you're running your build infrastructure in a public cloud. Even if you aren't and have your builds occuring in-house, on static machines, the ability to leverage public or private clouds


---

# Flexibility and Consistency 

Note: Containerizing your build infrastructure has the added advantage of being able to run builds anywhere that a container can run. Which to me means that my local box has the EXACT SAME configuration and infrastructure that my CI does. This ultimately leads to fewer broken builds and happier developers. There are few things that annoy me more than the classic "works on my machine" situation caused by inconsistency in build and deployment environments. The ability to run all your build infrastructure locally also allows developers and operations people to experiment with it, without disturbing others using it.

---

# Execute!

Note: Start by migrating your build and test slaves and into containers. I'm running with the assumption that we're talking about a web application, but the same applies for mobile applications and to some extent desktop. 

---

Note: I would begin with the Kitchen sink approach and move your whole build slave provisioning process into a container and move on. If you have chef, puppet, or ansible managing your build nodes, this will feel heavy handed, but the first pass often is. You will wind up with FAT containers initially. A consistent build environment that boots fast and disappears when not needed, will feel good and get teams used to wrapping builds in a docker run command and feed the build parameters in via environment variables or runtime parameters. Creating good scripting that lives in version control with your application will encourage virtuous behavior and running builds locally in a known environment before checking in. 


---

Note: Use separate containers for build and test, to begin separating out the concerns and familiarizing yourself and your engineers with passing data between containers. Even though these are not ideal as of yet, you can being paring them down.

---

# Traps

(pitfall logo)

Note: Building thin, light, single purpose containers is fun. As a person with an operations background and a deeply rooted belief in UNIX philosophy of do one thing and do it well, I have in the past over optimized and wasted far more time trying to get container images under an imaginary limbo stick of 10 megabytes or whatever arbitrary goal I came up with. Not everyone will have this problem, but because there are so many ways to do this, it can be an enormous timesuck. Timebox these activities as best you can, as the ROI on this diminishes quickly.

---

# 

and lower overhead to running a production like environment 



I would like to talk about what advantages containerization can offer your software organization in terms of the three knobs speed, quality, and cost, which in my mind is akin to flexibilty.
