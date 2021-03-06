# VoiceIt2-Perl

A Perl wrapper for VoiceIt's new API2.0 featuring Voice + Face Verification and Identification.

* [Getting Started](#getting-started)
* [Installation](#installation)
* [API Calls](#api-calls)
  * [Initialization](#initialization)
  * [User API Calls](#user-api-calls)
      * [Get All Users](#get-all-users)
      * [Create User](#create-user)
      * [Get User](#check-if-user-exists)
      * [Get Groups for User](#get-groups-for-user)
      * [Delete User](#delete-user)
  * [Group API Calls](#group-api-calls)
      * [Get All Groups](#get-all-groups)
      * [Create Group](#create-group)
      * [Get Group](#get-group)
      * [Delete Group](#delete-group)
      * [Group exists](#check-if-group-exists)
      * [Add User to Group](#add-user-to-group)
      * [Remove User from Group](#remove-user-from-group)      
  * [Enrollment API Calls](#enrollment-api-calls)
      * [Get All Enrollments for User](#get-all-enrollments-for-user)
      * [Delete Enrollment for User](#delete-enrollment-for-user)
      * [Create Audio Enrollment](#create-voice-enrollment)
      * [Create Video Enrollment](#create-video-enrollment)
  * [Verification API Calls](#verification-api-calls)
      * [Audio Verification](#voice-verification)
      * [Face Verification](#face-verification)
      * [Video Verification](#video-verification)
  * [Identification API Calls](#identification-api-calls)
      * [Audio Identification](#voice-identification)
      * [Video Identification](#video-identification)

## Getting Started

Sign up for a free Developer Account at <a href="https://voiceit.io/signup" target="_blank">VoiceIt.io</a> and activate API 2.0 from the settings page. Then you should be able view the API Key and Token. You can also review the HTTP Documentation at <a href="https://api.voiceit.io" target="_blank">api.voiceit.io</a>.

## Installation 

You can download this repository and add its contents to your root project folder.
Please make sure you have the HTTP::Commons module installed. We prefer you do so through cpan;
start cpan by typing "cpan" into terminal. Then type:
```
install HTTP::Request::Common
```
In case you do not have LWP::UserAgent, install it through cpan:
```
install Bundle::LWP
```

## API Calls
This is a curtailed documentaition of the API; For a complete list of all the API calls, please refer to the official API 2 docs: https://api.voiceit.io/

### Initialization
Initialize a VoiceIt Object with your own API key and token
```perl
require voiceIt2;
 my $myVoiceIt = voiceIt2->new("YOUR_KEY","YOUR_TOKEN");
 ```

### API calls

### User API Calls

#### Get All Users

Get all the users associated with the apiKey
```perl
$myVoiceIt->getAllUsers();
```

#### Create User

Create a new user
```perl
$myVoiceIt->createUser();
```

#### Check if User Exists

Check whether a user exists for the given userId(begins with 'usr_')
```perl
$myVoiceIt->getUser("USER_ID_HERE");
```

#### Delete User

Delete user with given userId(begins with 'usr_')
```perl
$myVoiceIt->deleteUser("USER_ID_HERE");
```

#### Get Groups for User

Get a list of groups that the user with given userId(begins with 'usr_') is a part of
```perl
$myVoiceIt->getGroupsForUser("USER_ID_HERE");
```

### Group API Calls

#### Get All Groups

Get all the groups associated with the apiKey
```perl
$myVoiceIt->getAllGroups();
```

#### Get Group

Returns a group for the given groupId(begins with 'grp_')
```perl
$myVoiceIt->getGroup("GROUP_ID_HERE");
```

#### Check if Group Exists

Checks if group with given groupId(begins with 'grp_') exists
```perl
$myVoiceIt->groupExists("GROUP_ID_HERE");
```

#### Create Group

Create a new group with the given description
```perl
$myVoiceIt->createGroup("Your Group Description");
```

#### Add User to Group

Adds user with given userId(begins with 'usr_') to group with given groupId(begins with 'grp_')
```perl
$myVoiceIt->addUserToGroup("GROUP_ID_HERE", "USER_ID_HERE");
```

#### Remove User from Group

Removes user with given userId(begins with 'usr_') from group with given groupId(begins with 'grp_')

```perl
$myVoiceIt->removeUserFromGroup( "GROUP_ID_HERE", "USER_ID_HERE");
```

#### Delete Group

Delete group with given groupId(begins with 'grp_'), note: This call does not delete any users, but simply deletes the group and disassociates the users from the group

```perl
$myVoiceIt->deleteGroup("GROUP_ID_HERE");
```

### Enrollment API Calls

#### Get All Enrollments for User

Gets all enrollment for user with given userId(begins with 'usr_')

```perl
$myVoiceIt->getAllEnrollmentsForuser("USER_ID_HERE");
```

#### Delete Enrollment for User

Delete enrollment for user with given userId(begins with 'usr_') and enrollmentId(integer)

```perl
$myVoiceIt->deleteEnrollment( "USER_ID_HERE", "ENROLLMENT_ID_HERE");
```

#### Create Voice Enrollment

Create audio enrollment for user with given userId(begins with 'usr_') and contentLanguage('en-US','es-ES' etc.). Note: File recording need to be no less than 1.2 seconds and no more than 5 seconds

```perl
$myVoiceIt->createVoiceEnrollment("USER_ID_HERE", "CONTENT_LANGUAGE_HERE", "FILE_PATH");
```

#### Create Face Enrollment

Create audio enrollment for user with given userId(begins with 'usr_') and contentLanguage('en-US','es-ES' etc.). Note: File recording need to be no less than 1.2 seconds and no more than 5 seconds

```perl
$myVoiceIt->createFaceEnrollment("USER_ID_HERE", "FILE_PATH");
```

#### Create Video Enrollment

Create video enrollment for user with given userId(begins with 'usr_') and contentLanguage('en-US','es-ES' etc.). Note: File recording need to be no less than 1.2 seconds and no more than 5 seconds

```perl
$myVoiceIt->createVideoEnrollment("USER_ID_HERE", "CONTENT_LANGUAGE_HERE",  "FILE_PATH");
```

### Verification API Calls

#### Voice Verification

Verify user with the given userId(begins with 'usr_') and contentLanguage('en-US','es-ES' etc.). Note: File recording need to be no less than 1.2 seconds and no more than 5 seconds

```perl
$myVoiceIt->voiceVerification("USER_ID_HERE", "CONTENT_LANGUAGE_HERE",  "FILE_PATH");
```

#### Face Verification 
```perl 
$myVoiceIt->faceVerification("USER_ID_HERE, "FILE_PATH");
```

#### Video Verification

Verify user with given userId(begins with 'usr_') and contentLanguage('en-US','es-ES' etc.). Note: File recording need to be no less than 1.2 seconds and no more than 5 seconds
```perl
$myVoiceIt->videoVerification("USER_ID_HERE", "CONTENT_LANGUAGE_HERE",  "FILE_PATH");
```

### Identification API Calls

#### Voice Identification

Identify user inside group with the given groupId(begins with 'grp_') and contentLanguage('en-US','es-ES' etc.). Note: File recording need to be no less than 1.2 seconds and no more than 5 seconds

```perl
$myVoiceIt->voiceIdentification("GROUP_ID_HERE", "CONTENT_LANGUAGE_HERE",  "FILE_PATH");
```

#### Video Identification

Identify user inside group with the given groupId(begins with 'grp_') and contentLanguage('en-US','es-ES' etc.). Note: File recording need to be no less than 1.2 seconds and no more than 5 seconds

```perl
$myVoiceIt->videoIdentification("GROUP_ID_HERE", "CONTENT_LANGUAGE_HERE",  "FILE_PATH");
```

## Author

Hassan Ismaeel, hassan@voiceit.io

## License

VoiceIt2-Perl is available under the MIT license. See the LICENSE file for more info.
