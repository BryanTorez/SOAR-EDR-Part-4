<h1>SOAR EDR Project | Intro</h1>

<p align="center">
<img src="https://snipboard.io/6rb2ue.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<h2>Description</h2>
<br />
<p align="center">
Welcome to part four of five for the series on the SOAR EDR project. If you haven't seen the previous parts where we go over how to build out a workflow for this project, set up LimaCharlie, and create our detection rule, I highly recommend you go and see that first.
  
  Today our objective is to set up both Slack and Tines. Then, test our connection between LimaCharlie and Tines to make sure that our SOAR is seeing the detection generated by LimaCharlie. Let's get started.
  
  
  To begin you want to head over to Slack.com. Then, click on "Get Started Free" button. Go ahead and create an account. Do make sure that you use a valid email account, because they will be sending you a confirmation code.
  
  
  Once you enter that in, go ahead and select "Create a Workspace". For the workspace name I'll call it as "MyDFIR-SOAR-EDR". Click on "Next", and my name is going to be  "demo".
  
  I'll go ahead and skip this step. "What's your team working on right now?" I'll type "The best project", then click "Next". Start with free and now we're set up with Slack. There's one thing I want to do though, its to add a new channel.
  
  So I'll click "Add Channels", then "Create a new channel". I'll call this as "alerts" and I'll put this as public. I'll skip adding people, and on our left-hand side we have a new channel called "alerts".
  
  So what this will do is when we receive a detection from LimaCharlie on Tines; Tines will then send a message over to slack. Specifically within the "alert" channel because as a SOC analyst you would probably want to have different channels and you'll want to have a dedicated channel for your alerts, so that is why we created an alerts channel.
  
  So now let's head over to Tines.com and click on "Sign up now" from the signup. You can sign up with Google or Microsoft, but just like Slack do make sure you have a valid email account because they will send you a confirmation email. Once you sign in, you'll see the screen right here.
  
  Now we can go ahead and begin with an example, but I'll go ahead and select the "X" to exit out. I'll click on "End Tour". If we take a look on the left-hand side, these are some of the actions that we can use to build our story, AKA Playbook. So for example, we can use a webhook and we can use an HTTP request.
  
  All we need to do is just drag it into the storyboard. I'll delete everything, except email and weather. There's also some templates so we can click on "Templates", and these are just pre-built templates to use. So for example, we have VirusTotal.
  
  
  We have some options here. We can search up "hash" and click on "Get File Behaviour in VirusTotal". So if I click on that, there's a value entry for the file hash, but we don't need this right now. I'll go ahead and delete that.
  
  So there's file hashes and also story libraries, so if you want to start with a template, we can do that as well. For example, if we wanted to add a domain to a block list in Zscaler, we can go ahead and click on that. Here's our pre-built story.
  
  We just simply have to import it and it will be imported into our Playbook or story, so that's very helpful. There's also tools, a page group, and Notes. If you want to head over to the dashboard, we can click on the Tines icon on the top left corner, so let's go ahead and click on that.
  
  What I'm going to do is click on my name and select dark mode because this is just a lot easier for me on my eyes. Now that I changed it to dark mode, let's go back to our story. What we need to do is establish the link between LimaCharlie and Tines so that way we can know that Tines is retrieving the detection.
  
  So how do we do that? Let's go ahead and click on the simple weather app and I'll go ahead and delete that. For the send email, I'll just delete that as well. So basically start from scratch, and what I'll be using is a web hook. So let's go ahead and grab that.
  
  
  I'll name the web hook action as "Retrieve Detections". For the description, I'll just say "Retrieves LimaCharlie Detections". For the web hook URL, I'll go ahead and just copy that. Now let's head over to LimaCharlie. So I'll select my organization and where we want to go is "Outputs".
  
  I'll click on "Add Output" and we got a couple of options here. We have "Events", "Detections", "Deployments", "Auto Logs", "Artifacts", and "Tailored". What we're interested in the most is "Detections", so this is a stream of detections reported by the rule engine. That's what we want, so I'll click on "Select".
  
  Now we have our "Destination". So we have "Amazon S3", "Apache", "Azure", "Data Dog", and "Elastic". So I'll go ahead and select "Tines". Now let's say we didn't have Tines, we can also just select Webhook as well. Since we do have an application for Tines, let's just select that.
  
  For the name, let's put in "MyDFIR-SOAR-EDR". For the destination host, let's paste in the web hook. Then, click "Save Output". Now we got our configuration saved, but we couldn't detect any recent samples moving through this output. I'll hit refresh, refresh again and there's still nothing.
  
  So what that means is that we just need to re1generate our event so over on our server I'll type in lasagna and hit enter this should in theory generate our detection so I clicked on refresh and here we go we have our my for hack tool lasagna and this looks to be pretty good let's head over to our timeses and our retrieve detections I'll just select events and I'll move this up just a bit and let's take a look at our most recent detection which is the first one here so I'll expand that body and look at that that's pretty cool we have our detection exactly one to one so we have our title which is might def for hack tool and if we open up the detect event we have the command line the file path the hash and the username that is pretty cool now we can start building our Playbook to finally perform some automation we should now have accounts for slack tines and Lima Charlie and we also confirm that the detection is showing up in times which means that we can begin creating our Playbook and and perform some Automation in the next part of our series which will be the last  episode we'll begin creating our Playbook by following our workflow that we created in part one do think about carving some time as it will be a longer video and that is it thank you for watching and I hope that you're enjoying this project series if you are let me know by hitting that like button and subscribe if you want to remember to stay curious and do things differently okay
