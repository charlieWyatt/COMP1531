## channels_create_v1 (Raymond Li, z5308491):
    Based on the other associated outputs for other functions, the details of each 
    channel will have the id, name, public status, a list of admin/owner members, a list of all 
    members and a list to hold messages. As it is not stated if the owner should also belong 
    in the all_members list it is assumed that all_members include all members regardless of status. 
    There are no other details that seem obvious to add as of Iteration 1 however it should be 
    no problem to add them into the create function later. 

## channels_list_v1 (Raymond Li, z5308491):
    For channels_list_v1, we check if the auth_user_id is valid. Although providing a user id that
    has not been created to the function would reveal no data, we implemented it anyway as it can
    be used to inform users if they have provided an incorrect ID on accident. 

## channels_listall_v1 (Raymond Li, z5308491):
    For channels_listall_v1, it does not specify in spec if it should return all channels within
    Dreams regardless of its public status. As it does not say to restrict this list to only 
    public servers and no other functions seem to care about the public status of the channels 
    as of Iteration 1 we assumed it should just return all channels. It also doesn't specify who 
    would use this command, a regular user should probably not see private channels but perhaps 
    a moderator of Dreams would find it useful to have a list of all the channels. At the moment
    the auth_user_id parameter is given to this function but there is no information about what 
    to do with it. Maybe in future iterations the instructions will specify to differentiate 
    between different user positions and the functionality can be adjusted then.  


# auth.py assumptions 
## Auth_register_v2 (Charlie Wyatt, z5194905):
1.  At registration, it is assumed a new session is created.

# channel.py assumptions
## channel_messages_v1 (Jason Peng, z5310746):
1. Within the list of dictionaries(message), it was assumed that the two components
   of message, 'u_id' and 'time_created' would be changed/updated in the function
   messages_send_v1 which is not a function that is implemented in iteration 1.
2. Since no messages are current sent (message_send_v1 is not implemeneted), 
   code would still have to be written under the condition that messages are 
   /will be sent.
3. The return values 'start' and 'end' was initially interpretated as an integer which is used
   to diplay the number of messages returned and what messages are returned. Since it was not
   specified in 6.1.1 Data Types it was easy to misunderstand that they are returned as dictionaries.

## channel_join_v2 (Eugenius Widjaja z5312461)
- if user is already in the channel then return and do nothing

## channel_invite_v2 (Eugenius Widjaja z5312461)
- Assume that all 'owner users' are also inside 'all users' in a channel's user lists
- if user is already in the channel then return and do nothing

# user.py assumptions
## user_profile_setname_v1 (Eugenius Widjaja z5312461)
- Assumes that the user's handle stays the same after changing their names

## users_all_v1 (Eugenius Widjaja z5312461)
- Assumes that users_all_v1 returns the same data per user that user_profile_v1 does

## user_profile_setemail (Eugenius Widjaja z5312461)
- Assumes that if new email is same as the user's current email it will error in the same way as if another user was using it

## user_profile_sethandle (Eugenius Widjaja z5312461)
- Assumes that if new handle is same as the user's current handle it will error in the same way as if another user was using it

## user_stats (Eugenius Widjaja z5312461)
- Assumes that if there are no channels, msgs and dms, then the involvement rate will be 0

# message.py assumptions
## message_share_v1 (Jason Peng z5310746)
- Assumes that og_message_id will never be invalid
- Assumes that either channel_id or dm_id are always -1

## message_send_v1 (Jason Peng z5310746)
- Assumes that a message that is sent can be empty (if the message string = '')

## message_senddm_v1 (Jason Peng z5310746)
- Assumes that a message that is sent can be empty (if the message string = '')

# Other.py assumptions
## search_v2 (Charlie Wyatt z5194905)
- Assumes the match with the query string and the messages is not case sensitive
