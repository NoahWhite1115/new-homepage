---
title: "Fire Drills"
date: 2021-06-14T20:01:00-07:00
draft: false
---

My team does "fire drills" once a month, so I thought I'd take some time to talk about what we do. 

## Background

I don't know where our concept of a fire drill comes from, since it was introduced before I joined the team. A quick google search turned up a few articles that describe a process that's vaguely similar to ours, but not exactly the same. So here's a quick overview to how we do fire drills. At our first weekly team meeting for a month, we pick a service and then a potential problem which could arise with that service. Then, the owners of that service have to sit and watch the rest of the devs try to figure out how to recover from the problem. After 30 or so minutes, the owners and the rest of the devs talk about what went right, what went wrong and what needs to be improved. 

Our fire drills bear some resemblance to the fire drills I've seen mentioned at other organizations, but fire drills at other places seem to be large affairs involving multiple teams recovering from a major simulated disaster. Ours are much smaller, focused primarily on diagnosing basic issues within a service and then performing a rollback or deployment.  

## How to pick a service and a problem

We started with a list of services. This included both internal services owned by us and external services which could cause problems for our services if they went down. For our first few fire drills, we simply picked a random service and then had the owner come up with a hypothetical scenario. This worked well, but coming up with a hypothetical scenario on the spot could be difficult. So eventually, we created a Google sheet full of scenarios, and I built a Slack bot that reads the sheet and posts a random service and scenario right to our team dev channel. 

When coming up with a scenario, the level of detail is up to you. You can keep it as simple as "The service needs to be restarted/rolled back", "Check the logs" or "Check if the service is up". Or you could run more complicated scenario, based on things that have actually happened to the service. I'd recommend the simpler case for any service that isn't super mission critical. If a short outage of your service won't bring everything to a halt, then keep it to surface level details. Your teammates only need enough knowledge of your service to begin debugging; everything else they can figure out if they need to. 

## Why we do them

Fire drills come with a few major benefits for our team. Done regularly, fire drills ensure that anyone on the team could handle the basic day to day administration of a service if all of its owners are on vacation. We're not a large team, with only 5 devs and we're split over several major areas. As a result, we sometimes can get pretty siloed, as everyone focuses on their own projects. Fire drills help to break that siloed behavior and to force us to learn more about each other's services. Things like where a service lives, where it's logs are, how to read those logs, who it's primary users are and how to deploy it are things everyone on a team should know. Fortunately, the average fire drill involves several of these issues, so everyone gets a chance to learn. 

Fire drills also force us to re-examine our documentation. It's always a little embarrassing as a project owner to have to admit that everything the team just did was wrong because your documentation is several months out of date, so they naturally encourage you to make sure your docs are current. They help to point out confusing phrasing too. If it's slowing the team down in a fire drill, it's a good idea to reword it. And they make sure that all of the docs are easy to find and in one place. If they aren't, the team is going to get frustrated very quickly.