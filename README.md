# Event and Ban Tracking System

## Introduction

The way we collect data for events depends on an event's circumstances. The difference in techniques comes because it'd be illogical for us to store the same information we store for event servers for simulation servers.

### Event Servers

When an event is on an event server, we track every player that joins and leaves the server. We then compare their movement data to see if they were in either the start or end city or both. Afterward, we confidently determine their presence based on the frequency of appearances in the start or end city. You can view our findings via our API or request an event overview via our Discord bot. **However, we recommend that unless you're an advanced user, not to generate an event overview as it can be quite confusing.**

### Simulation Servers

Simulation servers tend to have more players. Therefore, tracking every single one of them isn't ideal, especially since we're only interested in those who attended your event. To combat this, we focus on players in the start and end city or, if calculatable, work with a bounding box covering the area of the route. Generally, we stick with looking at the start and end cities.

### Tracking Bans

As a general rule, we track every ban regardless of where your event is hosted. This means that we'll track every person that gets banned on event servers and simulation servers. We check if, when somebody leaves, their account is showing as banned.

### When We Don't Track

For events on simulation 1, tracking is forbidden for convoys operating in or around Calais, Dusseldorf, or Duisburg. This includes the adjoining roads and the infamous Calais - Duisburg (C-D) Road. For events on ProMods, tracking is forbidden for convoys operating in or around Kirkenes & Kirkenes Quarry. We also forbid any tracking on events that contravene rule §2.6. Events that include any of these areas, on any of the aforementioned excluded servers, will not be subject to tracking. We may also limit tracking on event servers when the event is official in nature. For official convoys where the expected player attendance is greater than 250, we will only store the id, gameId, Name, and City name of each player.

### Tracking Periods

Tracking will start sometime before the end of 2023, and we aim to begin tracking automatically as soon as an event server comes online and/or its the advertised meetup_at time. We track with an update interval of 30 seconds.

### Tracking End

We will stop tracking your event once it's two hours after the advertised departure time or after the event server goes offline, whichever happens first. Once stopped, tracking cannot be restarted unless a new event begins.
