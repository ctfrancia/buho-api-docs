+++
date = '2025-01-09T09:55:52+01:00'
draft = true
title = 'Tournaments'
+++

# Tournaments
This chapter defines tournaments and their properties.

A tournament is as defined as a competition involving a group of players or teams competing against each other to win a prize or title.
The tournament is played in a series of matches, with the winner of each match advancing to the next round, and the loser being eliminated from the competition.
The tournament continues in this manner until only one player or team remains, who is declared the winner of the tournament.

## Get All Tournaments
This endpoint will return all tournaments that are currently active regardless of domain.


## Create a Tournament
This endpoint will create a tournament.
### Request
```json
```
**Method**: `POST`

**Endpoint**: `/v1/tournament/new`

**Fields Mandatory**:
- `name` (string) - the name of the tournament
- `start_date` (string | RFC3339) the start date of the tournament
- `end_date` (string | RFC3339) - the end date of the tournament

**NOTES**:
- The `start_date` and `end_date` must be in RFC3339 format.
- The `start_date` and `end_date` can be the same day but not the same time.


**Fields Optional**:
- `description` (string) - the description of the tournament
- `location` (string) - the location of the tournament
- `website` (string) - the website of the tournament
- `prize` (string) - the prize of the tournament
- `rules` (string) - the rules of the tournament
- `format` (string) - the format of the tournament
- `time_control` (string) - the time control of the tournament
- `rounds` (int) - the number of rounds in the tournament
- `players` (int) - the number of players in the tournament
- `rating` (int) - the rating of the tournament
- `organizer` (string) - the organizer of the tournament
- `contact` (string) - the contact of the tournament
- `email` (string) - the email of the tournament
- `phone` (string) - the phone of the tournament
- `facebook` (string) - the facebook of the tournament
- `twitter` (string) - the twitter of the tournament
- `instagram` (string) - the instagram of the tournament
- `youtube` (string) - the youtube of the tournament
- `twitch` (string) - the twitch of the tournament
- `discord` (string) - the discord of the tournament

#### Resources
- [RFC3339](https://datatracker.ietf.org/doc/html/rfc3339)
- [How to do RFC3339 JS](https://www.shecodes.io/athena/1913-convert-time-in-rfc3339-format-in-javascript#:~:text=The%20toISOString()%20method%20of,is%20the%20same%20as%20RFC3339.)




### Response
```json
{
    "ID": "sdfgf-23423-23423-23423",
    "CreatedAt": "2025-01-08T12:02:33+01:00",
    "UpdatedAt": "2025-01-08T12:02:33+01:00",
    "DeletedAt": null,
    "name": "foo",
    "start_date": "2025-01-09T12:02:33+01:00",
    "end_date": "2025-01-09T13:02:33+01:00",
}
```
**Status Code**: `201`

**Fields**:
- `ID` (string | UUID) - the ID of the tournament that was created

#### NOTES
The resonse will return back everything that was sent in the request. If the consumer wants to perform an update


## Update a Tournament
This endpoint will update a tournament for all that is metadata. For images/qr codes, please use the upload endpoint.
