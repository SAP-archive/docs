---
layout: concept
title: Participant data
permalink: /concepts/participant-data
---
 
 Here are the user data collected by the bot for each channel : 
 
| Channel | User's informations in participant | JSON Example |
| ----------------------------- | ---------------------------------- | ------------ |
| `Messenger` | *id, name, first_name, last_name, profile_pic, locale, timezone, gender* | { "first_name": "Peter",<br>"last_name": "Chang",<br>"profile_pic": "https://../13055603_10105219398495383_8237637584159975445_n.jpg",<br> "locale": "en_US",<br> "timezone": -7,<br> "gender": "male" } |
| `Slack` | *id, team_id, name, deleted, color, real_name, tz, tz_label, tz_offset, profile {object}, is_admin, is_owner, is_primary_owner, is_restricted, is_ultra_restricted, is_bot, updated, is_app_user, has_2fa* | { "user": <br>{ "id": "W012A3CDE",<br> "team_id": "T012AB3C4", <br>"name": "spengler",<br> deleted": false,<br> "color": "9f69e7",<br> "real_name":<br> "Egon Spengler", <br>"tz": "America/Los_Angeles",<br> "tz_label": "Pacific Daylight Time",<br> "tz_offset": -25200,<br> "profile": {<br> "avatar_hash": "ge3b51ca72de", <br>"status_text": "Print is dead", <br>"status_emoji": ":books:", <br>"real_name": "Egon Spengler",<br> "display_name": "spengler",<br> "real_name_normalized": "Egon Spengler",<br> "display_name_normalized": "spengler",<br> "email": "spengler@ghostbusters.example.com", <br>"image_24": "https://.../avatar/e3b51ca72dee4ef87916ae2b9240df50.jpg",<br> "image_32": "https://.../avatar/e3b51ca72dee4ef87916ae2b9240df50.jpg", <br> "team": "T012AB3C4"<br> },<br> "is_admin": true,<br> "is_owner": false,<br> "is_primary_owner": false,<br> "is_restricted": false,<br> "is_ultra_restricted": false,<br> "is_bot": false,<br> "updated": 1502138686,<br> "is_app_user": false,<br> "has_2fa": false } } |
| `Kik` | *first_name, last_name, profile_pic_url, profile_pic_last_modified, timezone* | { "first_name":"Peter",<br> "last_name":"Chang", <br>"profil_pic_url":"https://.../13055603_10105219398495383_8237637584159975445_n.jpg",<br> "profil_pic_last_modified":"1502138686",<br> "timezone":"America/Toronto" } |
| `Line` | *userId, displayName, pictureUrl, statusMessage* | { "userId":"U4af4980629...", <br>displayName":"Brown",<br> "pictureUrl":"https://example.com/abcdefghijklmn",<br> "statusMessage":"Hello, LINE!" } |
| `Twitter` | *id, id_str, name, screen_name, location, url, description, derived, protected, verified, followers_count, friends_count, listed_count, favourites_count, statuses_count, created_at, utc_offset, time_zone, geo_enabled, lang, contributors_enabled, profile_background_color, profile_background_image_url, profile_background_image_url_https, profile_background_tile, profile_banner_url, profile_image_url,profile_image_url_https, profile_link_color, profile_sidebar_border_color, profile_sidebar_fill_color, profile_text_color, profile_use_background_image, default_profile, default_profile_image, withheld_in_countries, withheld_scope* | { "id": 6253282,<br> "id_str":"6253282",<br> "name":"Twitter API",<br> "screen_name":"twitterapi",<br> "location":"San Francisco, CA",<br> "url":"https://dev.twitter.com", <br>"description":"The Real Twitter API.",<br> "derived":{ <br>"locations":[{}]<br> },<br> "protected":true,<br> "verified":false, "followers_count":21,<br> "friends_count":32,<br> "listed_count":9274,<br> "favourites_count":13,<br> "statuses_count":42,<br> "created_at":"Mon Nov 29 21:18:15 +0000 2010", <br>"utc_offset":null,<br> "timezone":null,<br> "geo_enabled":true,<br> "lang":"en",<br> "contributors_enabled":false,<br> "profile_background_color":"e8f2f7",<br> "profile_background_image_url":"http://.../twitterapi-bg.png",<br> "profile_background_image_url_https":"https://.../twitterapi-bg.png",<br> "profile_background_tile":false,<br> "profile_banner_url":"https://.../profile_banners/819797/1348102824",<br> "profile_image_url":"http://.../default_profile_normal.png",<br> "profile_image_url_https":"https://.../default_profile_normal.png",<br> "profile_link_color":"0094C2",<br> "profile_sidebar_border_color":"0094C2",<br> "profile_sidebar_fill_color":"a9d9f1",<br> "profile_text_color":"437792",<br> "profile_use_background_image":true,<br> "default_profile":false,<br> "default_profile_image":false,<br> "withheld_in_countries":["GR", "HK", "MY"],<br> "withheld_scope":"user" } |


<br/>In the conversation, the data is used like this :

| Channel | participant_data |
| ------- | ---------------- |
| `Messenger` | { userName:"first_name last_name" } |
| `Slack` | { userName:"real_name" } |
| `Kik` | { userName:"firstName lastName" } |
| `Line` | { userName:"displayName" } |
| `Twitter` | { userName:"name" } |

Some information may not be present, or may be null, if the data has not been supplied by the user.