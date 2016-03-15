"It is not necessary to change. Survival is not mandatory."
W. Edwards Deming


"release my changes faster"
"lower time to market"
"increase colloboration between silos"
"reduce waste costs"
"make more money"

^ that's what devops is for.

"protect my customers"
"minimize the damage a bad actor can have"
"protect my reputation"
"don't get me sued"
"prevent attacks from happening"
"respond to attacks"
"know when an attack is happening"

Defend, detect, and react.

^ that's what security is about

From a business perspective...
Security is a cost center

From a dev stanpoint...
Security is someone else's problem

From an operations stanpoint...
MY stuff is secure, it's those asshats in DB/development/vendor/OS who can't get their side worked out

From a manager's perspective...
Security is a non-functional requirement, we can put that in the next sprint.

From my perspective...
That sounds a lot like the same crap that was talked about operations a few short years ago

Security, like performance, is often viewed as outside the scope of a CD pipeline as it is difficult to address these concerns in an automated way.

What is this devops again?
  Culture - Promoting communication between everyone involved in delivering a product
  Automation - Tools and processes that minimize human error
  Measurement - Constant improvement requires measurement
  Sharing - Feedback group as large as the group of people that have influence over the end result

  (yes maybe also Lean, jez)

Where do the security goals fit?
Everywhere! (but probably best to talk about culture)

Leaving out technology decisions that we can talk about later, the important take home is that we need to change to create the environment that security can thrive in.

Increase trust and transparency between Developers, Security, and ops. How? 

Data, automation, Raising visibility! Tools that everyone has access to and reasons to look at. Dashboards, info radiators, etc. I generally don't care about things unless I can do something about them.

Security is a culture too, and a kind of secretive one at that too. To make this culture pervasive, we need a vision or a galvanizing message that people can rally behind. 

What is your bug reporting process like?

There are the tick the box style things that anyone has to do, external penetration testing at regular intervals, static analysis of code, automated pen testing with OWASP ZAP, regular access and account audits (how many former employees are on internal mailing lists?), but these are processes that would generally be implemented top down, or by your security team. 

Keep your shit updated.

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
