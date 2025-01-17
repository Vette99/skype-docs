---
title: lobby
description: lobby represents a view of the participants who have not yet been admitted to an onlineMeeting.
---

# lobby

 _**Applies to:** Skype for Business 2015_


Represents a view of the [participant](participant_ref.md)s who have not yet been admitted to an [onlineMeeting](onlineMeeting_ref.md).
            

## Web Link
<a name = "sectionSection0"> </a>

For more on web links, see [Web links](WebLinks.md).


|**Name**|**Description**|
|:-----|:-----|
|rel|The resource that this link points to. In JSON, this is the outer container.|
|href|The location of this resource on the server, and the target of an HTTP operation.|

## Resource description
<a name = "sectionSection1"> </a>

A [participant](participant_ref.md) in the lobby can be admitted by another participant in the organizer or presenter role.A participant in the lobby who is not admitted will eventually be disconnected.Lobby settings are controlled by the meeting organizer using the accessLevel property of [onlineMeeting](onlineMeeting_ref.md).

### Properties



None

### Links



This resource can have the following relationships.

|**Link**|**Description**|
|:-----|:-----|
|self|The link to the current resource.|
|participant|Represents a remote participant in a [conversation](conversation_ref.md).|

### Azure Active Directory scopes for online applications



The user must have at least one of these scopes for operations on the resource to be allowed.
|**Scope**|**Permission**|**Description**|
|:-----|:-----|:-----|
|Conversations.Receive|Receive conversation invites|Allows the app to receive instant messages, audio, video, and desktop sharing invitations on-behalf of the signed-in user|

## Events
<a name="sectionSection2"></a>

### Added



|**Resource**|**Priority**|**Sender**|**Reason**|
|:-----|:-----|:-----|:-----|
|participant|High|conversation|Indicates that a [participant](participant_ref.md) was added to the lobby.</p><p></p>|
Sample of returned event data.
This sample is given only as an illustration of event syntax. The semantic content is not guaranteed to correspond to a valid scenario.
{
  "_links" : {
    "self" : {
      "href" : "http://sample:80/ucwa/v1/applications/appId/events?ack=1"
    },
    "next" : {
      "href" : "http://sample:80/ucwa/v1/applications/appId/events?ack=2"
    }
  },
  "sender" : [
    {
      "rel" : "conversation",
      "href" : "https://fe1.contoso.com:443/ucwa/v1/applications/192/communication/conversations/137",
      "events" : [
        {
          "link" : {
            "rel" : "participant",
            "href" : "https://fe1.contoso.com:443/ucwa/v1/applications/192/communication/conversations/137/participants/196"
          },
          "in" : {
            "rel" : "lobby",
            "href" : "https://fe1.contoso.com:443/ucwa/v1/applications/192/communication/conversations/137/lobby"
          },
          "type" : "added"
        }
      ]
    }
  ]
}


### Updated



|**Resource**|**Priority**|**Sender**|**Reason**|
|:-----|:-----|:-----|:-----|
|participant|High|conversation|Delivered when the participant resource in lobby is updated.</p><p></p>|
Sample of returned event data.
This sample is given only as an illustration of event syntax. The semantic content is not guaranteed to correspond to a valid scenario.
{
  "_links" : {
    "self" : {
      "href" : "http://sample:80/ucwa/v1/applications/appId/events?ack=1"
    },
    "next" : {
      "href" : "http://sample:80/ucwa/v1/applications/appId/events?ack=2"
    }
  },
  "sender" : [
    {
      "rel" : "conversation",
      "href" : "https://fe1.contoso.com:443/ucwa/v1/applications/192/communication/conversations/137",
      "events" : [
        {
          "link" : {
            "rel" : "participant",
            "href" : "https://fe1.contoso.com:443/ucwa/v1/applications/192/communication/conversations/137/participants/196"
          },
          "in" : {
            "rel" : "lobby",
            "href" : "https://fe1.contoso.com:443/ucwa/v1/applications/192/communication/conversations/137/lobby"
          },
          "type" : "updated"
        }
      ]
    }
  ]
}


### Deleted



|**Resource**|**Priority**|**Sender**|**Reason**|
|:-----|:-----|:-----|:-----|
|participant|High|conversation|Indicates that a [participant](participant_ref.md) was removed from the lobby.</p><p>For example, the [participant](participant_ref.md) was admitted to or left the [onlineMeeting](onlineMeeting_ref.md). Note that if the [participant](participant_ref.md) leaves the [onlineMeeting](onlineMeeting_ref.md), a deleted event will be fired by this [participant](participant_ref.md) to indicate the application can release any cached information regarding this [participant](participant_ref.md).</p>|
Sample of returned event data.
This sample is given only as an illustration of event syntax. The semantic content is not guaranteed to correspond to a valid scenario.
{
  "_links" : {
    "self" : {
      "href" : "http://sample:80/ucwa/v1/applications/appId/events?ack=1"
    },
    "next" : {
      "href" : "http://sample:80/ucwa/v1/applications/appId/events?ack=2"
    }
  },
  "sender" : [
    {
      "rel" : "conversation",
      "href" : "https://fe1.contoso.com:443/ucwa/v1/applications/192/communication/conversations/137",
      "events" : [
        {
          "link" : {
            "rel" : "participant",
            "href" : "https://fe1.contoso.com:443/ucwa/v1/applications/192/communication/conversations/137/participants/196"
          },
          "in" : {
            "rel" : "lobby",
            "href" : "https://fe1.contoso.com:443/ucwa/v1/applications/192/communication/conversations/137/lobby"
          },
          "type" : "deleted"
        }
      ]
    }
  ]
}


## Operations



<a name="sectionSection2"></a>

### GET




Returns a representation of a view of the [participant](participant_ref.md)s who have not yet been admitted to an [onlineMeeting](onlineMeeting_ref.md).

#### Request body



None


#### Response body



The response from a GET request contains the properties and links shown in the Properties and Links sections at the top of this page.

#### Synchronous errors



The errors below (if any) are specific to this resource. Generic errors that can apply to any resource are covered in [Generic synchronous errors](GenericSynchronousErrors.md).

|**Error**|**Code**|**Subcode**|**Description**|
|:-----|:-----|:-----|:-----|
|ServiceFailure|500|InvalidExchangeServerVersion|Invalid exchange server version.The exchange mailbox of the server might have moved to an unsupported version for the required feature.|
|Conflict|409|AlreadyExists|The already exists error.|
|Conflict|409|TooManyGroups|The too many groups error.|
|Conflict|409|None|Un-supported Service/Resource/API error.|
|Gone|410|CannotRedirect|Cannot redirect since there is no back up pool configured.|

#### Examples




#### JSON Request




```
Get https://fe1.contoso.com:443/ucwa/v1/applications/192/communication/conversations/137/lobby HTTP/1.1
Authorization: Bearer cwt=PHNhbWw6QXNzZXJ0aW9uIHhtbG5...uZm8
Host: fe1.contoso.com
Accept: application/json

```


#### JSON Response



This sample is given only as an illustration of response syntax. The semantic content is not guaranteed to correspond to a valid scenario.
```
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 2161
{
  "rel" : "lobby",
  "_links" : {
    "self" : {
      "href" : "/ucwa/v1/applications/192/communication/conversations/137/lobby"
    }
  },
  "_embedded" : {
    "participant" : [
      {
        "rel" : "participant",
        "anonymous" : true,
        "inLobby" : true,
        "local" : true,
        "name" : "Joe Smith",
        "organizer" : true,
        "otherPhoneNumber" : "tel:+14251111111",
        "role" : "Attendee",
        "sourceNetwork" : "SameEnterprise",
        "uri" : "sip:john@contoso.com",
        "workPhoneNumber" : "tel:+14251111111",
        "_links" : {
          "self" : {
            "href" : "/ucwa/v1/applications/192/communication/conversations/137/participants/196"
          },
          "admit" : {
            "href" : "/ucwa/v1/applications/192/communication/conversations/137/participants/196/admit"
          },
          "contact" : {
            "href" : "/ucwa/v1/applications/192/people/282"
          },
          "contactPhoto" : {
            "href" : "/ucwa/v1/applications/192/people/282/contactPhoto"
          },
          "contactPresence" : {
            "href" : "/ucwa/v1/applications/192/people/282/contactPresence"
          },
          "conversation" : {
            "href" : "/ucwa/v1/applications/192/communication/conversations/137"
          },
          "demote" : {
            "href" : "/ucwa/v1/applications/192/communication/conversations/137/participants/196/demote"
          },
          "eject" : {
            "href" : "/ucwa/v1/applications/192/communication/conversations/137/participants/196/eject"
          },
          "me" : {
            "href" : "/ucwa/v1/applications/192/me"
          },
          "participantApplicationSharing" : {
            "href" : "/ucwa/v1/applications/192/communication/conversations/137/participants/196/participantApplicationSharing"
          },
          "participantAudio" : {
            "href" : "/ucwa/v1/applications/192/communication/conversations/137/participants/196/participantAudio"
          },
          "participantDataCollaboration" : {
            "href" : "/ucwa/v1/applications/192/communication/conversations/137/participants/196/participantDataCollaboration"
          },
          "participantMessaging" : {
            "href" : "/ucwa/v1/applications/192/communication/conversations/137/participants/196/participantMessaging"
          },
          "participantPanoramicVideo" : {
            "href" : "/ucwa/v1/applications/192/communication/conversations/137/participants/196/participantPanoramicVideo"
          },
          "participantVideo" : {
            "href" : "/ucwa/v1/applications/192/communication/conversations/137/participants/196/participantVideo"
          },
          "promote" : {
            "href" : "/ucwa/v1/applications/192/communication/conversations/137/participants/196/promote"
          },
          "reject" : {
            "href" : "/ucwa/v1/applications/192/communication/conversations/137/participants/196/reject"
          }
        }
      }
    ]
  }
}
```


#### XML Request




```
Get https://fe1.contoso.com:443/ucwa/v1/applications/192/communication/conversations/137/lobby HTTP/1.1
Authorization: Bearer cwt=PHNhbWw6QXNzZXJ0aW9uIHhtbG5...uZm8
Host: fe1.contoso.com
Accept: application/xml

```


#### XML Response



This sample is given only as an illustration of response syntax. The semantic content is not guaranteed to correspond to a valid scenario.
```
HTTP/1.1 200 OK
Content-Type: application/xml
Content-Length: 2660
<?xml version="1.0" encoding="utf-8"?>
<resource rel="lobby" href="/ucwa/v1/applications/192/communication/conversations/137/lobby" xmlns="http://schemas.microsoft.com/rtc/2012/03/ucwa">
  <property name="rel">lobby</property>
  <resource rel="participant" href="/ucwa/v1/applications/192/communication/conversations/137/participants/196">
    <link rel="admit" href="/ucwa/v1/applications/192/communication/conversations/137/participants/196/admit" />
    <link rel="contact" href="/ucwa/v1/applications/192/people/282" />
    <link rel="contactPhoto" href="/ucwa/v1/applications/192/people/282/contactPhoto" />
    <link rel="contactPresence" href="/ucwa/v1/applications/192/people/282/contactPresence" />
    <link rel="conversation" href="/ucwa/v1/applications/192/communication/conversations/137" />
    <link rel="demote" href="/ucwa/v1/applications/192/communication/conversations/137/participants/196/demote" />
    <link rel="eject" href="/ucwa/v1/applications/192/communication/conversations/137/participants/196/eject" />
    <link rel="me" href="/ucwa/v1/applications/192/me" />
    <link rel="participantApplicationSharing" href="/ucwa/v1/applications/192/communication/conversations/137/participants/196/participantApplicationSharing" />
    <link rel="participantAudio" href="/ucwa/v1/applications/192/communication/conversations/137/participants/196/participantAudio" />
    <link rel="participantDataCollaboration" href="/ucwa/v1/applications/192/communication/conversations/137/participants/196/participantDataCollaboration" />
    <link rel="participantMessaging" href="/ucwa/v1/applications/192/communication/conversations/137/participants/196/participantMessaging" />
    <link rel="participantPanoramicVideo" href="/ucwa/v1/applications/192/communication/conversations/137/participants/196/participantPanoramicVideo" />
    <link rel="participantVideo" href="/ucwa/v1/applications/192/communication/conversations/137/participants/196/participantVideo" />
    <link rel="promote" href="/ucwa/v1/applications/192/communication/conversations/137/participants/196/promote" />
    <link rel="reject" href="/ucwa/v1/applications/192/communication/conversations/137/participants/196/reject" />
    <property name="rel">participant</property>
    <property name="anonymous">True</property>
    <property name="inLobby">True</property>
    <property name="local">True</property>
    <property name="name">Joe Smith</property>
    <property name="organizer">True</property>
    <property name="otherPhoneNumber">tel:+14251111111</property>
    <property name="role">Attendee</property>
    <property name="sourceNetwork">SameEnterprise</property>
    <property name="uri">sip:john@contoso.com</property>
    <property name="workPhoneNumber">tel:+14251111111</property>
  </resource>
</resource>
```


