<h1>SOAR EDR Project | Intro</h1>

<p align="center">
<img src="https://snipboard.io/6rb2ue.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<h2>Description</h2>
<br />
<p align="center">
welcome to part four of five for the series on the sore EDR project if you haven't seen the previous Parts where we go over how to build out a workflow for this project set up lima charlie and create our detection rule I highly recommend you go and watch that first today our objective is to set up both
0:18
slack and tines and then test our
0:21
connection between lima charlie and Tin
0:24
to make sure that our sore is seeing the
0:26
detection generated by lima charlie
0:30
let's get started to begin you want to
Demo
0:32
head over to slack.com and then click on
0:34
the get started free button and then go
0:37
ahead and create an account do make sure
0:39
that you use a valid email account
0:40
because they will be sending you a
0:42
confirmation code and then once you
0:44
enter that in go ahead and select create
0:46
a workspace so for the workspace name
0:49
I'll call it as my dfir
0:52
ds- EDR click on next and my name is
0:57
indeed demo I'll go ahead and skip this
1:00
step and yeah skip without inviting
1:03
what's your team working on right now
1:06
the best
1:08
project next and start with free and now
1:11
we're set up with slack there's one
1:14
thing I want to do though is add a new
1:16
channel so I'll click add channels
1:19
create a new channel and I'll call this
1:21
as alerts and I'll put this as public
1:26
add people no I do not want to so I'll
1:29
skip that and on our left hand side we
1:31
have a new channel called alerts so what
1:33
this will do is that when we receive a
1:36
detection from Lima Charlie on ties ties
1:40
will then send a message over to slack
1:43
specifically within the alert channel
1:46
because as a sock analyst you would
1:48
probably want to have different channels
1:51
and you'll want to have a dedicated
1:52
channel for your alerts so that is why
1:55
we created an alerts channel so now
1:58
let's head over to tin.com and click on
2:00
sign up now from the sign up it does say
2:02
work email or you can sign up with
2:04
Google or Microsoft but just like slack
2:07
do make sure you have a valid email
2:09
account because they will send you a
2:10
confirmation email once you sign in
2:12
you'll see the screen right here now we
2:15
can go ahead and begin with an example
2:17
but I'll go ahead and select the X to
2:19
exit out I'll click on end tour if we
2:22
take a look on the left hand side these
2:24
are some of the actions that we can use
2:26
to build our story AKA Playbook so for
2:30
example we can use a web hook we can use
2:32
an HTTP request all we need to do is
2:35
just drag it into the storyboard I'll
2:38
delete that delete that and delete that
2:40
there's also some templates so we can
2:42
click on template and these are just
2:45
pre-built templates to use so for
2:47
example we have virus total I can drag
2:50
that over and then when I select it over
2:52
on the right hand side we have some
2:54
options here create a collection there's
2:56
probably a hash lookup as well so I type
2:59
in hash hash get file Behavior we see a
3:02
search for file hash and virus total so
3:05
if I click on that there's a value entry
3:07
for the file hash but we don't need this
3:10
right now I'll go ahead and delete that
3:12
and there's also story libraries so if
3:15
you want to start with a template we can
3:18
do that as well for example if we wanted
3:20
to add a domain to a block list in Z
3:23
scaler we can go ahead and click on that
3:26
and here's our pre-built story we just
3:29
simply have to import it and it will be
3:31
imported into our Playbook or story so
3:34
that's very helpful there's also tools
3:36
so a page group and Note and then if you
3:40
want to head over to the dashboard we
3:41
can click on the tin icon on the top
3:44
left corner so let's go ahead and click
3:46
on that and what I'm going to do is
3:48
actually click on my name and select
3:50
dark mode because this is just a lot
3:52
easier for me on my eyes now that I
3:55
changed it to dark mode Let's go back to
3:57
our story here what we need to do is
4:00
establish the link between lima charlie
4:02
and TI so that way we can know that TI
4:05
is retrieving the detection how do we do
4:08
that let's go ahead and click on the
4:10
simple weather app and I'll go ahead and
4:12
delete that the send email I'll just
4:14
delete that as well start from scratch
4:16
and what I'll be using is a web hook so
4:18
let's go ahead and grab that and I'll
4:21
name the web hook action as retrieve
4:25
detections the description I'll just say
4:29
retrieve
4:30
lima
4:32
charlie detections for the web hook URL
4:35
I'll go ahead and just copy that and now
4:37
let's head over to lima charlie so I'll
4:39
select my organization and where we want
4:42
to go is outputs I'll click on ADD
4:45
output and we got a couple of options
4:48
here we have the events detections
4:50
deployments auto logs artifacts and
4:52
tailored what we're interested in the
4:55
most is detections so this is a stream
4:58
of detections reported by the rule
5:00
engine that's what we want so I'll click
5:02
on select and now we have our
5:04
destination so Amazon S3 CFA
5:08
Azure there's data dog elastic so I'll
5:12
go ahead and select time now let's say
5:14
we didn't have a tin we can also just
5:16
select web hook as well but since we do
5:19
have an application for times let's just
5:21
select that for the name let's put in my
5:24
defer dsor dedr the destination host
5:29
let's paste in the web hook save output
5:33
that's it we got our configuration saved
5:35
but we couldn't detect any recent
5:36
samples moving through this output I'll
5:39
hit
5:40
refresh refresh and there's still
5:43
nothing so what that means is that we
5:44
just need to regenerate our event so
5:47
over on our server I'll type in lasagna
5:50
and hit
5:51
enter this should in theory generate our
5:54
detection so I clicked on refresh and
5:57
here we go we have our my for hack tool
6:00
lasagna and this looks to be pretty good
6:03
let's head over to our timeses and our
6:06
retrieve detections I'll just select
6:09
events and I'll move this up just a
6:12
bit and let's take a look at our most
6:14
recent detection which is the first one
6:17
here so I'll expand that body and look
6:21
at that that's pretty cool we have our
6:24
detection exactly one to one so we have
6:27
our title which is might def for hack
6:29
tool and if we open up the detect event
6:34
we have the command line the file path
6:38
the hash and the username that is pretty
6:42
cool now we can start building our
6:44
Playbook to finally perform some
6:46
automation we should now have accounts
6:48
for slack tines and Lima Charlie and we
6:52
also confirm that the detection is
6:55
showing up in times which means that we
6:57
can begin creating our Playbook and and
6:59
perform some Automation in the next part
7:02
of our series which will be the last
7:04
episode we'll begin creating our
7:06
Playbook by following our workflow that
7:08
we created in part one do think about
7:11
carving some time as it will be a longer
7:14
video and that is it thank you for
7:17
watching and I hope that you're enjoying
7:18
this project series if you are let me
7:21
know by hitting that like button and
7:23
subscribe if you want to remember to
7:26
stay curious and do things differently
7:29
okay
