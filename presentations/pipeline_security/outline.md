"t is not necessary to change. Survival is not mandatory."
W. Edwards Deming

This is a threat that I most often see in signatures blocks in emails from consultants, and in fearmongering blog posts about... selling consulting services. It's never really bothered me until I started writing this presentation and I came across it. 
Something about it screams inflexiblity even though it states that change is necessary for survival. Let's examine the positions that devops and security take and how we might leverage one to uplift the other.

"release my changes faster"
"lower time to market"
"increase colloboration between silos"
"reduce waste costs"
"make more money"
"ah-hah to $$$ is faster"

^ that's what devops is for.

"I protect my customers"
"We minimize the damage a bad actor can have"
"I protect my comapnies reputation"
"I haven't been sued!"
"We prevent attacks from happening"
"respond to attacks"
"know when an attack is happening"

Defend, detect, and react.

^ that's what security is about

From these personas...

Security looks like a different problem from a different perspectives. 

From a business perspective...
Security is a cost center
Security is a non-functional requirement, we can put that in the next sprint.

From a dev stanpoint...
Security is someone else's problem
I don't have control of the system or how it's deployed so it's not my problem.

From an operations stanpoint...
MY stuff is secure, it's those asshats in DB/development/vendor/OS who can't get their side worked out

Think big java or OS updates and the testing that has to go into pushing that update, in the devops world who's job is that? Painless upgrades to chef 11 for anyone who remembers ancient history?

From my perspective...
That sounds a lot like the same crap that was talked about operations a few short years ago
Security, like performance, is often viewed as outside the scope of a CD pipeline as it is difficult to address these concerns in an automated way.

The socialization of devops hinged on CALMS

What is this devops again?
  John Willis in 2010
  Culture - Promoting communication between everyone involved in delivering a product
  Automation - Tools and processes that minimize human error
  Lean - using lean practices to eliminate waste
  Measurement - Constant improvement requires measurement
  Sharing - Feedback group as large as the group of people that have influence over the end result

  (yes maybe also Lean, jez)

when I looked at these initially, I saw a lot of things that needed to happen. When I look at them now after a few years of experience doing devops transformations at organizations, and devops maturity assesments and working on teams that do perform and deliver really well is that it kind of all boils down to something much less scientific. Namely empathy and understanding.

The ability for an individual to see things through another persons (in this case role's) eyes is critical to making people able to work together.

Where do the security goals fit?
Everywhere! (but probably best to talk about culture)

Increase trust and transparency between Developers, Security, and ops. How? 

Operational complexity is the difficulty to reason about and react to a running application or system and it's state.

This is luckily the easiest one. This is around tools and automation.

So for example, you read a CVE for NGINX. You want to know at a glance, which, if any nodes are vulnerable. You as an operator or maintainer of cookbooks or modules or whatever automation, might be able to find this information instantly. Does everyone else who reads CVE's have that capacity to check? 

What about not from your provisioning, detecting anomalies or snowflakes, do you know how to do that? Is there a report to run somehow? What about other packages or software. Even worse, what about librarires your applications are built against? 

This tiny consideration for others, empowers them to do something about it other than just writing you an email and hoping for the best. They can write an email, pull request, whatever change management process you use, and hopefully help themselves fix the problem they are worried about.

This extends as far as you want it to, monitoring, logging, alerting, historical data, all that good stuff. How is it socailized across your org?

Learning from past mistakes

This one can be hard to nail down, but a lot of the narrative of decision making in software can be traced through how tests are written and bugs are caught. I know it's impossible to write a test case for everything, but when you upgrade a service or introduce a change to a critical piece of infrastructure, your commit message or test case can be the key difference between that getting reverted when something unrelated breaks and getting sued because of a known exploit, and someone getting up and talking to you about what possible solutions there might be other than to roll back a critical security patch.

What is your bug reporting process like?

Knowing when something is wrong is critical to fixing it. 

This can be tackled in a lot of different ways. Do the folks that care about security have the same access to spin up and test environments locally as your developers do? Can they contribute to your build and release pipeline? Maybe they want to add some automated testing for CVEs using static analysis, OWASP ZAP, or add some IDS or honeypots to your application. Do they know how? If not, then that's kind of on you to fix.

Increase trust and transparency between Developers, Security, and ops. How? 

Security is a culture too, and a kind of secretive one at that too. To make this culture pervasive, we need a vision or a galvanizing message that people can rally behind. 

Leaving out technology decisions that we can talk about later, the important take home is that we need to change to create the environment that security can thrive in.

Data, automation, Raising visibility! Tools that everyone has access to and reasons to look at. Dashboards, info radiators, etc. I generally don't care about things unless I can do something about them.

There are the tick the box style things that anyone has to do, external penetration testing at regular intervals, static analysis of code, automated pen testing with OWASP ZAP, regular access and account audits (how many former employees are on internal mailing lists?), but these are processes that would generally be implemented top down, or by your security team. 

Keep your shit updated, 3rd party stuff.

Security games and drills are awesome. At a previous client we had these all the time with different results. Lost laptops, compromised keys, cert expiration. These things

Those are the jobs of the security folks 

Security as a culture, let's start small.

Changes we can make to our team to make security a focus and a priority?

Typically low hanging fruit
  Automated patching, are you using unattended upgrades?
  How many are familiar with hardening.io? (sane defaults for operating systems)

Secrets management
Log output and access
Monitoring and alerting related to security

So what the hell is a devops/security talk going to have in it?

Security in the pipeline
  Application security, how to test?
    Does OWASP zap deliver value?
    Does gauntlt deliver value?
  Regression tests, do you write them when bugs are discovered?
  Static code analysis tools?
  Pushing secrets to git?

Security of the pipeline
  Who can deploy?
  Who has access to see and change the pipeline components?
    Are all the environments the same? (I'LL BET YOUR JENKINS USERS AREN'T)
  Who has access to artifact store per environment?
  Who has access to change and update the secrets?
  Key rotation and deployment strategies?
  How do components communicate?

Security as process
  Security sprints?
  Configuration audits with risk analysis
  Patch levels and vulnerability subscriptions
  Critical updates auto installed?

Security Culture

Basic infrastructure security:
http://blog.mailgun.com/security-guide-basic-infrastructure-security/

Letting the tools do the heavy lifting.
