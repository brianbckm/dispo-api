# dispo-api :rocket:
 Looking at the api of the dispo Camera App - just a short walk

## Endpoint
https://dispo.dev/api/v1/graphql


## POST Header
```
content-type:                  application/json                                                                                                                                    
x-apollo-operation-name:       --- Operationname ---                                                                                                                                   
accept:                        */*                                                                                                                                                 
apollographql-client-version:  2.0.2-89                                                                                                                                            
authorization:                 token --- Token ---                                                                              
accept-language:               de-DE, en-DE                                                                                                                                        
accept-encoding:               gzip, deflate, br                                                                                                                                   
content-length:                654                                                                                                                                                 
x-apollo-operation-type:       query                                                                                                                                               
dispo-platform:                iOS                                                                                                                                                 
apollographql-client-name:     app.davidsdisposable.davids-disposable-ios-apollo-ios                                                                                               
user-agent:                    Dispo/89 CFNetwork/1209 Darwin/20.2.0                                                                                                               
dispo-build:                   89                                                                                                                                            
cookie:                        csrftoken= --- Just a CSRFTOKEN here ---
```

## Some Operation Names

UserFollowersList

```
{
    "operationName": "UserFollowersList",
    "query": "query UserFollowersList($cursor: String, $userId: String!) {\n  userFromId(userId: $userId) {\n    __typename\n    followersList(cursor: $cursor) {\n      __typename\n
     ...followingListData\n    }\n  }\n}\nfragment followingListData on UserPage {\n  __typename\n  items {\n    __typename\n    ...followingListUser\n  }\n  hasNext\n 
cursor\n}\nfragment followingListUser on User {\n  __typename\n  ...basicUser\n  following\n}\nfragment basicUser on User {\n  __typename\n  id\n  handle\n  displayName\n  avatar\n
verified\n}",
    "variables": {
        "cursor": null,
        "userId": "user_ID"
    }
}
```

UserFromId
```
{
    "operationName": "UserFromId",
    "query": "query UserFromId($userId: String!) {\n  userFromId(userId: $userId) {\n    __typename\n    ...profileUser\n  }\n}\nfragment profileUser on User {\n  __typename\n 
...basicUser\n  following\n  followerCount\n  score\n  bio\n  mediaCount\n  knownFollowerCount\n  header\n}\nfragment basicUser on User {\n  __typename\n  id\n  handle\n 
displayName\n  avatar\n  verified\n}",
    "variables": {
        "userId": "user_ID"
    }
}
```

FollowerProfileUser
```
{
    "operationName": "FollowProfileUser",
    "query": "mutation FollowProfileUser($follow: Boolean!, $userId: String!) {\n  followUser(follow: $follow, userId: $userId) {\n    __typename\n    ...profileUser\n 
}\n}\nfragment profileUser on User {\n  __typename\n  ...basicUser\n  following\n  followerCount\n  score\n  bio\n  mediaCount\n  knownFollowerCount\n  header\n}\nfragment basicUser
on User {\n  __typename\n  id\n  handle\n  displayName\n  avatar\n  verified\n}",
    "variables": {
        "follow": true,
        "userId": "user_ID"
    }
}
```

### Tools Dispo using
* https://d1o09vdwvdbry2.cloudfront.net - Cloudfront as Image CDN
* sentry.io - Diagnosis
* onesignal.com - For Push Notifications
* mixpanel.com - Analytics


