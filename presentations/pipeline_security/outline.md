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

^ that's what security is about

From a business perspective...
Security is a cost center

From a dev stanpoint...
Security is someone else's problem

From a manager's perspective...
Security is a non-functional requirement, we can put that in the next sprint.

From my perspective...
That sounds a lot like the same crap that was talked about operations a few short years ago

Security, like performance, is often viewed as outside the scope of a CD pipeline as it is difficult to address these concerns in an automated way.

What is this devpos again?
  Culture - Promoting communication between everyone involved in delivering a product
  Automation - Tools and processes that minimize human error
  Measurement - Constant improvement requires measurement
  Sharing - Feedback group as large as the group of people that have influence over the end result

  (yes maybe also Lean, jez)

Where do the security goals fit?
Everywhere! (but probably best to talk about culture)

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
  

Secrets management
Log output and access
Monitoring and alerting related to security


Basic infrastructure security:
http://blog.mailgun.com/security-guide-basic-infrastructure-security/
