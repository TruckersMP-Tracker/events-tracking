# Event Tracking System

The approach to data collection for events is contingent upon the specific circumstances of each event. Distinct techniques are employed due to the impracticality of using the same information storage approach for event servers as for simulation servers, specifically in tracking players joining or leaving a server. Consequently, data collection is exclusive to events hosted on event servers. For events on simulation servers, tracking becomes challenging. To address this, we focus on tracking players in cities or along a route, rather than monitoring every player joining or leaving the server. It's important to note that the accuracy of our collection on simulation servers may not be as high as with event servers.

## Event Servers

When an event takes place on an event server, we meticulously track every player joining and leaving the server. Subsequently, we scrutinise their movement data to ascertain whether they were present in either the start or end city or both. Following this analysis, we confidently establish their presence based on the frequency of appearances in the start or end city. You can access our findings via our API or request an event overview via our Discord bot. **However, we strongly advise against generating an event overview unless you are an advanced user, as it can be intricate.**

## Simulation Servers

Unlike event servers, simulation servers tend to have far more players. Therefore, tracking every single one of them isn't ideal. Especially since we're only after those who attended your event. To combat this, we only look at players in the start and end city. We may also, if calculatable, work with a bounding box covering the area of the route. However, we will usually stick with just looking at the start and end cities. This means that we will see everyone that comes in and out of both the aforementioned cities. It's important to note that companies outside of the start city, i.e., considered in a separate city, will **not be covered** unless a route bounding box covers an area including said company.

## Tracking Bans At Events

As a general rule, we track every ban regardless of where your event is hosted. This means that we'll track every person that gets banned on event servers and simulation servers. By tracking bans, what we mean is we'll check if, when somebody leaves, their account is showing as banned. If it is, we'll consider them as having been banned in-game. For event servers, we'll include the names of every user at the time they were banned. For simulation servers, we'll include the name of every user that's banned and their last known location if calculatable. **These tracking rules apply to event-tracked bans only.**

## When We Don't Track

For events on simulation server 1, tracking is forbidden for convoys operating in or around Calais, Dusseldorf, or Duisburg. This includes the adjoining roads and the infamous Calais - Duisburg (C-D) Road. For events on ProMods, tracking is forbidden for convoys operating in or around Kirkenes & Kirkenes Quarry. We also forbid any tracking on events that contravene rule §2.6. Events that include any of these areas, on any of the aforementioned excluded servers, will not undergo tracking. This is mainly due to the sheer number of people in these areas and because their occurrence directly contravenes TruckersMP rules. We may also limit tracking on event servers when the event is official in nature. Effectively meaning, we won't track events including, but not limited to Freeroam or TMP birthday celebrations. For official convoys where the expected player attendance is greater than 250, we will only store the id, gameId, Name, and City name of each player.

## Tracking Periods

Tracking will start sometime before the end of 2023, and we aim to begin tracking automatically as soon as an event server comes online and/or its the advertised meetup_at time. We track with an update interval of 30 seconds. This means that in the time leading up to departure when the meetup_at time is 30 mins before, we will have checked things 60 times.

## When Will Tracking Stop?

We will stop tracking your event once it's two hours after the advertised departure time, or after the event server goes offline. Whatever applies and happens first. Once stopped, tracking cannot be restarted unless a new event begins.

## Data Storage And Retention

After an event, raw data is compressed into a more readable version. This more [readable version](https://github.com/TruckersMP-Tracker/events-tracking/blob/main/json/examples/event_test/compressed_test_doc.json) is stored separately from the raw data and serves as the data used for our API. This means that the data accessible via our API is:

```json
{
  "MpId": 2,
  "Event": 19029,
  "Start": true,
  "End": true
}
```

We will hold onto raw data in its raw form until 30 days after an event. We will then anonymise said data or delete it, depending on the reliance on the data. Raw data is accessible by the organising party of any such event. Raw data doesn't, in itself, contain any information that could identify a person in a way that could inflict harm, contravene TruckersMP rules, or require its immediate after-recording deletion. Therefore, we feel it safe to retain said raw data for 30 days. The aforementioned 'more-readable' version or 'compressed' version is retained permanently. We retain this on a per-user basis, i.e., each user has their own document in our DB per event they're an attendee of. The purpose of this data's permanent retention is to ensure we can operate. An example raw-data document can be found [here](https://github.com/TruckersMP-Tracker/events-tracking/blob/main/json/examples/event_test/raw_test_doc.json).

## What Should Our Data Be Used For?

The purpose of our data is to give VTCs and organising parties the ability to see attendance data. It also allows VTCs that offer incentives for attending events to correctly see which users have indeed attended events. Our data shouldn't be used in any other way than the ways mentioned above. If you're found to be using our data in a way that contravenes this, your access to said data and systems will be **permanently removed**.

## What You Cannot Do With Our Data?

You cannot use data held by us to harass, stalk, insult, gain an advantage over others, unless considered acceptable by ourselves and organisers, or any other malicious or unsavoury use case. You may also not use data held by us to break any TruckersMP rule and/or break TruckersMP's Privacy Policy.

## Unaffiliation Notice

We're not affiliated with TruckersMP, SCS, ProMods, TruckersFM, or any other parties. We're a solo party operating with the sole intent of providing unseen yet useful stats to the community. All data that passes through our hands is considered public up until the point of its privation at source, i.e., the user deletes their account and/or removes said information from their profile.
