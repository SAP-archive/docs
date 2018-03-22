---
layout: concept
title: Conversation State
permalink: /concepts/conversation-state
---

The conversation state is the state of your bot's conversation with the user. It contains the following information:
- **id**: the id of the conversation provided by Bot Connector, and unique for each user
- **language**: the current language of the conversation, detected by Recast.AI
- **memory**: the data your bot has already collected from the user
- **skill_stack**: the last skill in the skill_stack has priority of execution, and is popped after its actions have been executed
- **skill**: the currently active skill in the conversation
- **skill_occurences**: the number of consecutive messages handled by the current skill. This is set to 0 when the skill is done (actions are executed).
- **participant_data**: an object containing the user information gathered from the channel your bot is connected to (Messenger, Slack,...).

~~~ javascript
 {
    "id": "A_CONVERSATION_ID",
    "language": "en",
    "memory": {
      "person": {
        "fullname": "Francois",
        "raw": "Francois",
        "confidence": 0.95
      }
    },
    "skill_stack": ["get-weather"],
    "skill": "small-talk",
    "skill_occurences": 1
}
~~~
