# General

  | Object | Path |
  | - | - | 
  | [Campaign](#campaign) | `/livechat/campaigns` |
  | [Canned Message](#canned-message) | `/livechat/cannedMessages` |  
  | [Canned Message Category](#canned-message-category) | `/livechat/cannedMessageCategories` |  
  | [Department](#department) | `/livechat/departments` |  
  | [Auto Allocation](#auto-allocation) | `/livechat/autoAllocation` |  
  | [Custom Away Status](#custom-away-status) | `/livechat/customAwayStatus` |  
  | [Ban](#ban) | `/livechat/bans` | 
  | [Conversion Action](#conversion-action) | `/livechat/conversionActions` | 
  | [Visitor Segmentation](#visitor-segmentation) | `/livechat/visitorSegments` |
  | [Visitor SSO Settings](#visitor-sso-settings) | `/livechat/visitorSSO` |
  | [Live Chat Config](#live-chat-config) | `/livechat/configs` |
  | [Secure Forms](#secure-form) | `/livechat/secureForms` |
  | [Webhooks](#webhooks) | `/livechat/webhooks` |
  | [Custom Variables](#custom-variables) | `/livechat/customVariables` |
  | [Agent](#agent) | `/livechat/agents` |
  | [Chat](#chat) | `/livechat/chats` |
  | [Message](#message) | `/livechat/messages` |
 
# Campaign
  You need `Manage Campaigns` permission to manage campaigns and customize the settings for a campaigns.
  - `Campaigns` - Campaigns Manage
    + `GET /api/v1/livechat/campaigns` - Get list of campaigns
    + `POST /api/v1/livechat/campaigns` - Create a new campaign
    + `PUT /api/v1/livechat/campaigns/{id}` - Update a campaign
    + `DELETE /api/v1/livechat/campaigns/{id}` - Remove a campaign
  - `Campaign Settings` - setting of campaign
    + `GET /api/v1/livechat/campaigns/{id}/code` - Get installation code for a campaign
    + `GET /api/v1/livechat/campaigns/{id}/chatButton` - Get settings of ChatButton for a campaign
    + `PUT /api/v1/livechat/campaigns/{id}/chatButton` - Update settings of ChatButton for a campaign
    + `GET /api/v1/livechat/campaigns/{id}/chatWindow`  - Get settings of ChatWindow for a campaign
    + `PUT /api/v1/livechat/campaigns/{id}/chatWindow`  - Update settings of ChatWindow for a campaign
    + `GET /api/v1/livechat/campaigns/{id}/preChat`  - Get settings of PreChat for a campaign
    + `PUT /api/v1/livechat/campaigns/{id}/preChat`  - Update settings of PreChat for a campaign
    + `GET /api/v1/livechat/campaigns/{id}/postChat` - Get settings of PostChat for a campaign
    + `PUT /api/v1/livechat/campaigns/{id}/postChat` - Update settings of PostChat for a campaign
    + `GET /api/v1/livechat/campaigns/{id}/offlineMessage`  - Get settings of OfflineMessage for a campaign
    + `PUT /api/v1/livechat/campaigns/{id}/offlineMessage`  - Update settings of OfflineMessage for a campaign
    + `GET /api/v1/livechat/campaigns/{id}/invitation`  - Get settings of invitation for a campaign
    + `PUT /api/v1/livechat/campaigns/{id}/invitation`  - Update settings of invitation for a campaign
    + `GET /api/v1/livechat/campaigns/{id}/invitation/autoInvitations/{autoInvitation_id}`  - Get a autoInvitation for a campaign
    + `POST /api/v1/livechat/campaigns/{id}/invitation/autoInvitations`  - Create a new auto invitation for a campaign
    + `PUT /api/v1/livechat/campaigns/{id}/invitation/autoInvitations/{autoInvitation_id}`  - Update a auto invitation for a campaign
    + `GET /api/v1/livechat/campaigns/{id}/agentWrapup`  - Get settings of Agent Wrap Up for a campaign
    + `PUT /api/v1/livechat/campaigns/{id}/agentWrapup`  - Update settings of Agent Wrap Up for a campaign
    + `GET /api/v1/livechat/campaigns/{id}/RoutingRules` - Get settings of Routing Rules for a campaign
    + `PUT /api/v1/livechat/campaigns/{id}/RoutingRules` - Update settings of Routing Rules for a campaign
    + `GET /api/v1/livechat/campaigns/{id}/RoutingRules/customRules/{customeRule_id}` - Get a custom rule for a campaign
    + `POST /api/v1/livechat/campaigns/{id}/RoutingRules/customRules` - Create a new custom rule for a campaign
    + `PUT /api/v1/livechat/campaigns/{id}/RoutingRules/customRules/{customeRule_id}` - Update a custom rule for a campaign
    + `GET /api/v1/livechat/campaigns/{id}/language`  Get settings of Language for a campaign
    + `PUT /api/v1/livechat/campaigns/{id}/language`  Update settings of Language for a campaign

## Campaigns
### Model
#### Campaign JSON Format
  Campaign is represented as simple flat JSON objects with the following keys:  

  | Name | Type | Read-only | Mandatory | Description |    
  | - | - | :-: | :-: | - | 
  | `id` | integer  | yes | no | id of the campaign |
  | `name` | string  | no | yes | name of the campaign |
  | `description` | string  | no | no | description of the campaign |
  | `language` | string  | no | yes | language of the campaign |

### Endpoint
#### Get list of campaigns

  `GET /api/v1/livechat/campaigns`
  - Parameters: No parameters
  - Response: An array of [Campaign](#campaign-json-format)

#### Create a new campaign
  
  `POST /api/v1/livechat/campaigns`
  - Parameters: [Campaign](#campaign-json-format)
  - Response: [Campaign](#campaign-json-format)

#### Update a campaign
    
  `PUT /api/v1/livechat/campaigns/{id}`
  - Parameters: Campaign Object
  - Response: [Campaign](#campaign-json-format)

#### Remove a campaign 
  
  `DELETE /api/v1/livechat/campaigns/{id}`
  - Parameters锛歂o parameters.
  - Response: 200 OK
 
## Installation Code

### Endpoint
#### Get installation code of a campaign
  
  `GET /api/v1/livechat/campaigns/{id}/code`
 
  - Parameters: No parameters
  - Response
    - `code` - installation code for the campaign.


## Chat Button

### Model
#### Chat Button JSON Format
  Chat Button is represented as simple flat JSON objects with the following keys:  

  | NameN| Type | Read-only | Mandatory | Description | 
  | - | - | :-: | :-: | - | 
  | `type` | string | no | yes | type of the button, including `adaptive`, `image` and `textLink`. |
  | `isHideOffline` | boolean | no | no | whether the chatButton is visible when no agent is online.`true` means that button is invisible. |
  | `isUseDomainRestriction` | boolean | no | no | whether the domain restriction is enable or not. |
  | `allowedDomains` | array | no | no | an array of domains/urls, on which the chat button is visible. |
  | `adaptive.themeColor` | string | no | no | the theme color of chatbutton, available when `type` is `adaptive`. |
  | `adaptive.icon` | string | no | no | icon of the chat button, available when `type` is `adaptive`. | 
  | `image.type` | string | no | no |  `gallery` or `custom` |
  | `image.onlineImageId` | int | no | no | id of the image when any agents are on line, available when `type` is `image`. |
  | `image.offlineImageId` | int | no | no | id of the image when no agent is on line, available when `type` is `image`. |
  | `image.isFloat` | boolean | no | no |    whether the chat button is float or not, available when `type` is `image`. |
  | `image.position.type` | string | no | no | position of the chat button, including `centered`, `topLeft`, `topMiddle`, `topRight`, `buttomLeft`, `buttomMiddle`, `buttomRight`, `leftMiddle` and `rightMiddle`, available when `type` is `image`. |
  | `image.position.x` | string | no | no | coordinate y of the button, allowed as a number or percentage like `10` or `10%`, available when `type` is `image`. |
  | `image.position.y` | string | no | no | coordinate x of the button, allowed as a number or percentage like `10` or `10%`, available when `type` is `image`. |
  | `image.mobile.type` | string | no | no | the type of button on mobile device, including `text` and `image`, available when `type` is `image`. |
  | `image.mobile.onlineText` | string | no | no | the content of text on mobile device when online, available when `image.mobile.type` is `text`and `type` is `image`. |
  | `image.mobile.offlineText` | string | no | no | the content of text on mobile device when no agent is on line, available when `image.mobile.type` is `text`and `type` is `image`. |
  | `image.mobile.themeColor` | string | no | no | the theme color of chatbutton on mobile device, available when `image.mobile.type` is `text`and `type` is `image`. |
  | `image.mobile.onlineImageId` | string | no | no | the id of image on mobile device when any agents are online, available when `image.mobile.type` is `image`and `type` is `image`. |
  | `image.mobile.offlineImageId` | string | no | no | the id of image on mobile device when no agent is on line, available when `image.mobile.type` is `image` and `type` is `image`. |
  | `image.mobile.position` | string | no | no | position of the chat button on mobile device, including `bottomLeft`, `bottomMiddle`, `bottomRight`, `leftMiddle`, `RightMiddle`, `leftBottom` and `rightBottom`, available when `image.mobile.type` is `image` and `type` is `image`. |
  | `textLink.text` | string | no | no | the content of the text link, available when `type` is `textLink`. |

### Endpoint
#### Get ChatButton configuration of a campaign
  
  `GET /api/v1/livechat/campaigns/{id}/chatButton`
  - Parameters: No parameters
  - Response: [Chat Button](#chat-button-json-format)
 
#### Update ChatButton configuration for a campaign

  `PUT /api/v1/livechat/campaigns/{id}/chatButton`
  - Parameters: [Chat Button](#chat-button-json-format)
  - Response: [Chat Button](#chat-button-json-format)


## Chat Window

### Model
#### Chat Window JSON Format
  Chat Window is represented as simple flat JSON objects with the following keys:  
 
  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - | 
  | `style` | string | no | yes | style of the window's theme, including `classic`, `simple` and `bubble`. |
  | `color` | string | no | yes | color of the window's theme. |
  | `type` | string | no | yes | type of the chat window, including `embedded` and `popup`. |
  | `customCSS` | string | no | no | the content of custom css. |
  | `popup.title` | string | no | no | title of the chat window, available when `type` is `popup`. |
  | `options.isCanPrintTranscript` | boolean | no | no | chat details can be printed |
  | `options.isCanEmailTranscript` | boolean | no | no | chat transcripts can be emailed to visitors |
  | `options.email.isFromAgent` | boolean | no | no | whether email is setted from agent email or from a specified address. |
  | `options.email.fromEmail` | string | no | no | a specified email for from address. |
  | `options.email.fromName` | string | no | no | a specified name for from address. |
  | `options.isCanSwitchToOffline` | boolean | no | no | allow visitors to switch to Offline Message Window while waiting for chat. |
  | `options.isCanSendFile` | boolean | no | no | whether the agent can send file or not. |
  | `options.isCanAudioChat` | boolean | no | no | whether the agent can use audio chat. |
  | `options.isCanVideoChat` | boolean | no | no | whether the agent can use video chat. |
  | `advanced.isAutoEndChatWhenVisitorInactivity` | boolean | no | no | whether chat ends automatically if visitors don't respond. |
  | `advanced.timeAutoEndChatWhenVisitorInactivity` | integer | no | no | the time the chat will be ended after visitor inactivity, the unit is minute. |
  | `advanced.isAutoSendTranscriptToEmail` | boolean | no | no | whether the agent can send transcript email after chat ending. |
  | `advanced.transcriptEmailAddress` | string | no | no | the email address for sending transcript email. |
  | `advanced.transcriptEmailSubject` | string | no | no | the subject address for sending transcript email. |
  | `advanced.greetingMessage` | string | no | no | the content of greeting message. |
  | `advanced.isUseCustomJS` | boolean | no | no | whether the agent can add custom js to chat window or not. |
  | `advanced.customJS` | string | no | no | the content of custom javascript. |
  | `header.type` | string | no | no | type of the header, including `agentInfo`, `bannerImage` when `style` is `classic`, including `agentInfo`, `bannerImage` and `avatarAndLogo` when `style` is `simple`. |
  | `header.agentInfo.isShowAvatar` | boolean | no | no | whether the avatar of the agent is visible or not, available when `style` is `classic`or `simple` and `header.type` is `agentInfo` or `avatarAndLogo`. |
  | `header.agentInfo.isShowTitle` | boolean | no | no | whether the title of the agent is visible or not, available when `style` is `classic`or `simple` and `header.type` is `agentInfo`. |
  | `header.agentInfo.isShowBio` | boolean | no | no | whether the bio of the agent is visible or not, available when `style` is `classic`or `simple` and `header.type` is `agentInfo`. |
  | `header.banner.imageType` | string | no | no | `custom` or `gallery` |
  | `header.banner.imageId` | int | no | no | id of the image in the header of chat window, available when `style` is `classic`or `simple` and `header.type` is `bannerImage`. |
  | `header.avatarAndLogo.isShowAvatar` | boolean | no | no | whether the agent avatar is visible or not, available when `style`
  | `header.avatarAndLogo.isShowLogo` | boolean | no | no | whether the logo of the company is visible or not, available when `style` is `classic` and `header.type` is `avatarAndLogo`. |
  | `header.avatarAndLogo.logoImageId` | int | no | no | id of the company logo image in the header of chat window, available when `style` is `classic` and `header.type` is `avatarAndLogo`. |
  | `body.isShowAvatar` | boolean | no | no | whether the avatar of the agent is visible or not in the messsage body, available when `style` is `classic`or `simple`. |
  | `body.isShowBackground` | boolean | no | no | whether the texture and picture of the background is visible or not in the messsage body, available when `style` is `classic`or `simple`. |
  | `body.backgroudImageId` | int | no | no | id of the company image in the message body, available when `style` is `classic`or `simple`. |
 
### Endpoint 
#### Get ChatWindow configuration of a campaign

  `GET /api/v1/livechat/campaigns/{id}/chatWindow`
  - Parameters: No parameters
  - Response: [Chat Window](#chat-window-json-format)

#### Update ChatWindow configuration of a campaign

  `PUT /api/v1/livechat/campaigns/{id}/chatWindow`
  - Parameters: [Chat Window](#chat-window-json-format)
  - Response: [Chat Window](#chat-window-json-format)

## Pre-Chat

### Model
#### Pre-Chat JSON Format

  Pre-Chat is represented as simple flat JSON objects with the following keys:  

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - |
  | `isEnable` | boolean | no | yes | whether the pre-chat is enable or not. |
  | `header.isShowTeamName` | boolean | no | no | whether the team name is visible or not in the header. |
  | `header.teamName` | string | no | no | the team name display in the header. |
  | `header.isShowAvatars` | boolean | no | no | whether the avatar of the agent is visible or not in the header. |
  | `greetingMessage` | string | no | no | content of greeting message. |
  | `socialLogin.isUseGoogle` | boolean | no | no | whether google is enable or not in social login. |
  | `socialLogin.isUseFacebook` | boolean | no | no | whether facebook is enable or not in social login. |
  | `isRememberVisitorInfo` | boolean | no | no | whether visitor info is remembered or not from pre-chat form. |
  | `fieldLayout` | string | no | yes | the layout style of field display, including `vertical` and `horizontal`. |
  | `fields` | Array | no | no | an array of [field](#field-json-format) object |

#### Field JSON Format

  Field is represented as simple flat JSON objects with the following keys:  

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - |
  | `id` | integer | yes | no | id of the field |
  | `name` | string | no | yes | name of the field |
  | `type` | string | no | yes | the [type](#field-type) of the field |
  | `isSystem` | boolean | yes | no | whether the field is system field or not. |
  | `isVisible` | boolean | no | no | whether the field is visible or not. |
  | `isRequired` | boolean | no | no | whether the field is required or not when submiting the form |
  | `options` | string | no | no | the options of the field. |

#### Field Type
  Field Type is one key of the following keys:    

  | Name | isSystem | Description |
  | - | :-: | - |
  | `name` | yes | Name field, `Pre Chat Form` or `Offline Message Form` only. |
  | `email` | yes | Email field, `Pre Chat Form` or `Offline Message Form` only. |
  | `phone` | yes | Phone field, `Pre Chat Form` or `Offline Message Form` only. |
  | `company` | yes | Company field, `Pre Chat Form` or `Offline Message Form` only. |
  | `product` | yes | Product and Service field, `Pre Chat Form` only. |
  | `department` | yes | Department field, `Pre Chat Form` or `Offline Message Form` only. |
  | `ticket` | yes | Ticket field, `Pre Chat Form` or `Offline Message Form` only.  |
  | `rating` | yes | Rating field, `Post Chat Form` only. |
  | `comment` | yes | Comment field, `Post Chat Form` only. |
  | `subject` | yes | Subject field, `Offline Message Form` only. |
  | `content` | yes | Content field, `Offline Message Form` only. |
  | `attachment` | yes | Attachment field, `Offline Message Form` only. |
  | `cardNumber` | yes | card number field , `Secure Form` only. |
  | `expirationDate` | yes | expiration date field, `Secure Form` only |
  | `cscOrCvv` | yes | csc/cvv field , `Secure Form` only |
  | `nameOnCard` | yes | name on card field , `Secure Form` only |
  | `text` | no | Text field.  |
  | `textarea` | no | Textarea field.  |
  | `radio` | no | Radio Box field.  |
  | `checkbox` | no | Check Box field.  |
  | `select` | no | Drop Down List field.  |
  | `checkboxList` | no | Check Box List field.  |


### Endpoint
#### Get Pre-Chat configuration of a campaign

  `GET /api/v1/livechat/campaigns/{id}/prechat`
  - Parameters: No parameters
  - Response: [Pre-Chat](#pre-chat-json-format)

#### Update Pre-Chat configuration for a campaign

  `PUT /api/v1/livechat/campaigns/{id}/prechat`
  - Parameters: [Pre-Chat](#pre-chat-json-format)
  - Response: [Pre-Chat](#pre-chat-json-format)

## Post-Chat

### Model
#### Post-Chat JSON Format
  Post-Chat is represented as simple flat JSON objects with the following keys:  

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - |
  | `isEnable` | boolean | no | yes | whether the post-chat is enable or not. |
  | `greetingMessage` | string | no | no | content of greeting message. |
  | `fieldLayout` | string | no | no | the layout style of field, including `vertical` and `horizontal`. |
  | `fields` | Array | no | no | an array of [field](#field-json-format) object


### Endpoint

#### Get Post-Chat configuration of a campaign

  `GET /api/v1/livechat/campaigns/{id}/postchat`
  - Parameters: No parameters
  - Response: [Post-Chat](#post-chat-json-format)
  
#### Update Post-Chat configuration of a campaign

  `PUT /api/v1/livechat/campaigns/{id}/postchat`
  - Parameters: [Post-Chat](#post-chat-json-format)
  - Response: [Post-Chat](#post-chat-json-format)

## Offline Message

### Model
#### Offline Message JSON Format 
  Offline Message is represented as simple flat JSON objects with the following keys:  

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - |
  | `isUseOwnPage`| boolean | no | yes | whether the custom offline message page is used or not. |
  | `page.url`| string | no | no | url of custom offline message page. |
  | `page.isOpenInNewWindow` | boolean | no | no | whether open the custom offline message page in a new window or not. |
  | `greetingMessage` | string | no | no | content of greeting message.
  | `header.isShowTeamName` | boolean | no | no | whether the name of the agent is visible or not in the header. |
  | `header.isShowAvatar` | boolean | no | no | whether the avatar of the agent is visible or not in the header. |
  | `header.teamName` | string | no | no | the team name display in the header. |
  | `fieldLayout` | string | no | no | the layout style of field, including `vertical` and `horizontal`. |
  | `fields` | Array | no | no | an array of [field](#field-json-format) object |

### Endpoint
#### Get OfflineMessage configuration of a campaign

  `GET /api/v1/livechat/campaigns/{id}/offlineMessage`
  - Parameters: No parameters
  - Response: [Offline Message](#offline-message-json-format)

#### Update OfflineMessage configuration of a campaign

  `PUT /api/v1/livechat/campaigns/{id}/offlineMessage`
  - Parameters: [Offline Message](#offline-message-json-format)
  - Response: [Offline Message](#offline-message-json-format)

## Invitation
### Model
#### Invitation Window JSON Format    
  Invitation Window is represented as simple flat JSON objects with the following keys:  

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - | 
  | `message.content` |string  | no | no | content of invitation message. |
  | `message.font` |string  | no | no | the font of text. |
  | `message.bold` | boolean  | no | no | whether the text is bold or not. |
  | `message.fontsize` |string  | no | no | the size of text. |
  | `message.italic` | boolean  | no | no | whether the text is italic or not. |
  | `message.color` |string  | no | no | the color of text. |
  | `popup.position` |string  | no | no | the position of invitation window, including `centered`, `centeredWithOverlay`, `topLeft`, `topMiddle`, `topRight`, `buttomLeft`, `buttomMiddle`, `buttomRight`, `leftMiddle` and `rightMiddle`. |
  | `popup.imageType` | string | no | no | `custom` or `gallery` |
  | `popup.imageId` | int  | no | no | id of invitation image. |
  | `popup.messageFrame.x` |float  | no | no | coordinate x of the text area |
  | `popup.messageFrame.y` |float  | no | no | coordinate y of the text area |
  | `popup.messageFrame.width` |float  | no | no | width of the text area |
  | `popup.messageFrame.height` |float  | no | no | height of the text area |
  | `popup.closeFrame.x` |float  | no | no | coordinate x of the close area |
  | `popup.closeFrame.y` |float  | no | no | coordinate y of the close area |
  | `popup.closeFrame.width` |float  | no | no | width of the close area |
  | `popup.closeFrame.height` |float  | no | no | height of the close area |

#### Auto Invitation JSON Format
  Auto Invitation is represented as simple flat JSON objects with the following keys:  

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - | 
  | `id` | integer | yes | no | id of the auto invitation. |
  | `name` | string | no | yes | name of auto invitation. |
  | `isEnable` | boolean | no | no | whether the auto invitation is enable or not. |
  | `isPopupOnlyOneTime` | boolean | no | no | whether pop up only one time during one visit |
  | `invitationWindow` | [InvitationWindow](#invitation-window-json-format) | no | no | an invitation window json object. |
  | `conditions` | [Conditions](#conditions-json-format) | no | no | an trigger condition json object. |

#### Conditions JSON Format
  Conditions is represented as simple flat JSON objects with the following keys:  

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - | 
  | `when` | string | no | no | when the rule is triggered, including `all`, `any` and `logicalExpression` |
  | `logicalExpression` | string | no | no | the logical expression of the conditions |
  | `list` | array | no | no |an array of [condition](#condition-json-format) |

#### Condition JSON Format
  Condition is represented as simple flat JSON objects with the following keys:  

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - |
  | `number` | int | no | yes | the number of the condition, used in logic expression |
  | `field` | string  | no | yes | the name of visitor field |
  | `operator` | string  | no | yes | a comparison operator |
  | `value` | string  | no | yes | the value of a visitor field |


### Endpoint
#### Get invitation configuration of a campaign

  `GET /api/v1/livechat/campaigns/{id}/invitation`
  - Parameters: No parameters
  - Response
    - `style` - the layout style of invitation window, including `bubble`, `popup` and `chatwindow`
    - `autoInvitations` - an array of [Auto invitation](#auto-invitation-json-format) json object.
    - `manualInvitation` - [Invitation window](#invitation-window-json-format) json object

#### Update Invitation style of a campaign

  `PUT /api/v1/livechat/campaigns/{id}/invitation`
  - Parameters
    - `style` - the layout style of invitation window, including `bubble`, `popup` and `chatwindow`
  - Response 
    - `style` - the layout style of invitation window, including `bubble`, `popup` and `chatwindow`
    - `autoInvitations` - an array of [Auto invitation](#auto-invitation-json-format) json object.
    - `manualInvitation` - [Invitation window](#invitation-window-json-format) json object

#### Update manualInvitation for a campaign

  `PUT /api/v1/livechat/campaigns/{id}/invitation/manualInvitation`
  - Parameters: [Invitation Window](#invitation-window-json-format)
  - Response: [Invitation Window](#invitation-window-json-format)
 
#### Get an auto invitation for a campaign
   
  `GET /api/v1/livechat/campaigns/{id}/invitation/autoInvitations/{autoInvitation_id}`
  - Parameters: No parameters
  - Response: [Auto invitation](#auto-invitation-json-format)
  
#### Create a new auto invitation for a campaign
   
  `POST /api/v1/livechat/campaigns/{id}/invitation/autoInvitations`
  - Parameters: [Auto invitation](#auto-invitation-json-format)
  - Response: [Auto invitation](#auto-invitation-json-format)

#### Update an auto invitation for a campaign
  
  `PUT /api/v1/livechat/campaigns/{id}/invitation/autoInvitations/{autoInvitation_id}`
  - Parameters: [Auto invitation](#auto-invitation-json-format)
  - Response: [Auto invitation](#auto-invitation-json-format)

#### Delete an auto invitation for a campaign

  ` DELETE /api/v1/livechat/campaigns/{id}/invitation/autoInvitations/{auto_invitation_id}`
  - Parameters: No parameters
  - Response: 200 OK

## Agent Wrapup

### Endpoint
#### Get agent wrapup of a campaign

  `GET /api/v1/livechat/campaigns/{id}/agentWrapup`
  - Parameters: no parameters
  - Response: an array of [Field](#field-json-format)

#### Update agent wrapup for a campaign

  `PUT /api/v1/livechat/campaigns/{id}/agentWrapup`
  - Parameters: an array of [Field](#field-json-format)
  - Response: an array of [Field](#field-json-format)


## Routing Rule

### Model
#### Routing Rule JSON Format
  Route Rule is represented as simple flat JSON objects with the following keys:  

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - |
  | `isEnable` | boolean | no | yes |whether the routing rules is enable or not.
  | `type` |string | no | no |the type of routing, including `simple` and `rules`. |
  | `simpleRouteToObject` | string | no | no | the rule of route , including `department` and `agent` |
  | `simpleRouteToId` | integer | yes | no | id of the route object |
  | `simpleRoutePriority` | string | no | no | the priority of the route object, including `lowest`, `low`, `normal`, `high` and `highest`. |
  | `rules` | array | yes | no | an array of [Custom Rule](#custom-rule-json-format) json object. |
  | `failType` | string | no | no |the type of fail routing, including `route` and `offlineMessage`. |
  | `fail.routeTobject` | string | no | no | the rule of fail route , including `department` and `agent` |
  | `fail.routeToId` | integer | yes | no | id of the route object |
  | `fail.routePriority` | string | no | no | the priority of fail route object, including `lowest`, `low`, `normal`, `high` and `highest`. |
  | `fail.offlineMessageEmails` | string  | no | no | redirect them to Offline Message Window and forward their messages to the email |

#### Custom Rule JSON Format
  Custom Rule is represented as simple flat JSON objects with the following keys:  

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - |
  | `id` | integer | yes | no | id of the custom rule |
  | `order` | integer | no | no | order of the custom rule |
  | `isEnable` | boolean | no | yes |whether the custom rule is enable or not. |
  | `name` | string | no | yes |name of the custom rule |
  | `conditions` | [Conditions](#conditions-json-format)  | no | no | an trigger condition json object. |
  | `routeToObject` | string | no | yes | type of the route, including `agent` and `department`, value `department` is available when config of department is open. |
  | `routeToId` | integer | yes | yes | id of the route object |
  | `routePriority` | string | no | no | the priority of the route object, including `lowest`, `low`, `normal`, `high` and `highest`. |
  
### Endpoint
#### Get Routing Rules of a campaign

  `GET /api/v1/livechat/campaigns/{id}/routingrules`
  - Parameters: No parameters
  - Response: [Routing Rule](#routing-url-json-format)

#### Update Routing Rules for a campaign

  `PUT /api/v1/livechat/campaigns/{id}/routingrules`
  - Parameters: [Routing Rule](#routing-url-json-format)
  - Response: [Routing Rule](#routing-url-json-format)

#### Get a custom rule of a campaign

  `GET /api/v1/livechat/campaigns/{id}/routingrules/customrules/{custom_rule_id}`
  - Parameters: No parameters
  - Response: [Custom Rule](#custom-rule-json-format)

#### Create a new custom rule for a campaign

  `POST /api/v1/livechat/campaigns/{id}/routingrules/customrules`
  - Parameters: [Custom Rule](#custom-rule-json-format)
  - Response: [Custom Rule](#custom-rule-json-format)

#### Update a custom rule for a campaign

  `PUT /api/v1/livechat/campaigns/{id}/routingrules/customrules/{custom_rule_id}` 
  - Parameters: [Custom Rule](#custom-rule-json-format)
  - Response: [Custom Rule](#custom-rule-json-format)

#### Delete a custom rule for a campaign

  `DELETE /api/v1/livechat/campaigns/{id}/routingrules/customrules/{custom_rule_id}`
  - Parameters: No parameters
  - Response: 200 OK


## Language
### Model
#### Campaign Language JSON Format
  Language is represented as simple flat JSON objects with the following keys:  

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - |
  | `isUseDefaultLanguageText` | boolean | no | yes | whether use default language text or not. |
  | `isRTL` | boolean | no | no | whether the language is from right to left. |
  | `languageTexts` | array | no | no | an array of [Language Text](#language-text-json-format) |

#### Language Text JSON Format   
  Language Text is represented as simple flat JSON objects with the following keys:  

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - |
  | `category` | string | yes | yes | the module of custom language, including `buttons`, `fields`, `prompts`, `systemMessages`, `audioChat`, `videoChat`, `screenSharing`, `transcriptEmail`, `mobile`, `embedded` and `chatbot`. |
  | `name` | string | yes | yes | the name of the language item |
  | `defaultText` | string | yes | no | the default text of field of the custom language. |
  | `currentText` | string | no | no | current text of field of the custom language. |
  | `macros` | string | yes | no | macors which used in the field of the custom language. |

### Endpoint
#### Get Language for a campaign

  `GET /api/v1/livechat/campaigns/{id}/language`
  - Parameters: No parameters
  - Response: [Campaign Language](#campaign-language-json-format)
    
#### Update settings of Language for a campaign

  `PUT /api/v1/livechat/campaigns/{id}/language`
  - Parameters: [Campaign Language](#campaign-language-json-format)
  - Response: [Campaign Language](#campaign-language-json-format)

# Canned Message
  You need `Manage Pulbic Canned Messages` permission to manage canned message.
  + `GET /api/v1/livechat/cannedMessages` -get list of canned Message
  + `GET /api/v1/livechat/cannedMessages/{id}`  -get a single canned Message
  + `POST /api/v1/livechat/cannedMessages` -create a new canned Message
  + `PUT /api/v1/livechat/cannedMessages/{id}`  -update a canned Message
  + `DELETE /api/v1/livechat/cannedMessages/{id}`  -remove a canned Message
    
## Model
### Canned Message JSON Format
  Canned Message is represented as simple flat JSON objects with the following keys:  

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - |
  | `id` | integer | yes | no | id of the canned message. |
  | `name` | string | no | yes | name of the canned message. |
  | `message` | string | no | yes | content of the canned message. |
  | `shortcuts` | string | no | no | shortcuts of the canned message. |
  | `categoryId` | integer | no | no | id of the category of the canned message, default is `0` |
  | `isPrivate` | boolean | no | no | whether the canned message is private or not, default is `false` |
    
## Endpoint
### Get list of canned messages

  `GET /api/v1/livechat/cannedMessages`
  - Parameters: No parameters
  - Response: An array of [Canned Message](#canned-message-json-format)
    
### Get a single canned message 

  `GET /api/v1/livechat/cannedMessages/{id}`
  - Parameters: No parameters
  - Response: [Canned Message](#canned-message-json-format)
    
### Create a new canned message 

  `POST /api/v1/livechat/cannedMessages`
  - Parameters: [Canned Message](#canned-message-json-format)
  - Response: [Canned Message](#canned-message-json-format)
    
### Update a canned message 

  `PUT /api/v1/livechat/cannedMessages/{id}`
  - Parameters: [Canned Message](#canned-message-json-format)
  - Response: [Canned Message](#canned-message-json-format)
    
### Remove a canned message 

  `DELETE /api/v1/livechat/cannedMessages/{id}`
  - Parameters: No parameters
  - Response: 200 OK   
    
# Canned Message Category
  You need `Manage Pulbic Canned Messages` permission to manage canned message category.
  + `GET /api/v1/livechat/cannedMessageCategories` -get list of canned Messages Categories
  + `GET /api/v1/livechat/cannedMessageCategories/{id}`  -get a single canned Messages Category
  + `POST /api/v1/livechat/cannedMessageCategories` -create a new canned Messages Category
  + `PUT /api/v1/livechat/cannedMessageCategories/{id}`  -update a canned Messages Category
  + `DELETE /api/v1/livechat/cannedMessageCategories/{id}`  -remove a canned Messages Category
    
## Model
### Canned Message Category JSON Format
  Canned Message Category is represented as simple flat JSON objects with the following keys:  

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - |
  | `id` | integer  | yes | no |id of the canned message category. |
  | `name` | string  | no | yes |name of the canned message category. |
  | `parentId` | integer  | no | yes | id of the parent category of the canned message category. |
  | `isPrivate` | string  | no | yes | whether the canned message category is private or not. |

## Endpoint
### Get list of canned message categories

  `GET /api/v1/livechat/cannedMessageCategories`
  - Parameters: No parameters
  - Response: An array of [Canned Message Category](#canned-message-category-json-format)
    
### Get a single canned message category

  `GET /api/v1/livechat/cannedMessageCategories/{id}`
  - Parameters: No parameters
  - Response: [Canned Message Category](#canned-message-category-json-format)
    
### Create a new canned message category

  `POST /api/v1/livechat/cannedMessageCategories`
  - Parameters: [Canned Message Category](#canned-message-category-json-format)
  - Response: [Canned Message Category](#canned-message-category-json-format)
    
### Update a canned message category
 
  `PUT /api/v1/livechat/cannedMessageCategories/{id}`
  - Parameters: [Canned Message Category](#canned-message-category-json-format)
  - Response: [Canned Message Category](#canned-message-category-json-format)
    
### Remove a canned message category
 
  `DELETE /api/v1/livechat/cannedMessageCategories/{id}`
  - Parameters: No parameters
  - Response: 200 OK   
    
# Department
  You need `Manage Settings` permission to manage department.
  + `GET /api/v1/livechat/departments` -get list of departments
  + `GET /api/v1/livechat/departments/{id}`  -get a single department
  + `POST /api/v1/livechat/departments` -create a new department
  + `PUT /api/v1/livechat/departments/{id}`  -update a department
  + `DELETE /api/v1/livechat/departments/{id}`  -remove a department
    
## Model
### Department JSON Format
  Department is represented as simple flat JSON objects with the following keys:  

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - |
  | `id` | integer | yes | no |id of the department. |
  | `name` | string | no | yes |name of the department. |
  | `description` | string | no | no |description of the department. |
  | `agents` | array | no | no | an array of agent in the department. |
  | `groups` | array | no | no | an array of group in the department. |
  | `allocationRule` | string | no | no | rule of chat allocation, including `load banlancing` , `round robin` and `capability weighted`. |
  | `isLastChattedPreferred` | boolean | no | no |whether last-chatted agent is prefer or not. |
  | `backupDepartmentId` | integer | no | no | id of back up department |
  | `offlineMessageTo` | string | no | no | object which mail offline messages of the department to, including `allAgents` and `emailAddresses` |
  | `emailAddresses` | string | no | no | the email addresses which mail offline messages of the department to |

## Endpoint
### Get list of departments 

  `GET /api/v1/livechat/departments`
  - Parameters: No parameters
  - Response: An array of [Department](#department-json-format)
    
### Get a single department 

  `GET /api/v1/livechat/departments/{id}`
  - Parameters: No parameters
  - Response: [Department](#department-json-format)
    
### Create a new department 

  `POST /api/v1/livechat/departments`
  - Parameters: [Department](#department-json-format)
  - Response: [Department](#department-json-format)
    
### Update a department 

  `PUT /api/v1/livechat/departments/{id}`
  - Parameters: [Department](#department-json-format)
  - Response: [Department](#department-json-format)
    
### Remove a department
  `DELETE /api/v1/livechat/departments/{id}`
  - Parameters: No parameters
  - Response: 200 OK   


# Custom Away Status
  You need `Manage Settings` permission to manage custom away status.
  + `GET /api/v1/livechat/customAwayStatus` - get list of custom away status
  + `GET /api/v1/livechat/customAwayStatus/{id}` - get a single custom away status
  + `POST /api/v1/livechat/customAwayStatus` - create a new custom away status
  + `PUT /api/v1/livechat/customAwayStatus/{id}` - update a custom away status
  + `DELETE /api/v1/livechat/customAwayStatus/{id}` - remove a custom away status

## Model
### Custom Away Status JSON Format
  Custom Away Status is represented as simple flat JSON objects with the following keys:  

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - |
  | `id` | integer | yes | no | id of the custom away status. |
  | `name` | string | no | yes | name of the custom away status. |
  | `isVisible` | boolean | no | no | whether the custom away status is visible or not. |


## Endpoint
### Get list of custom away status 
 
  `GET /api/v1/livechat/customAwayStatus`
  - Parameters: No parameters
  - Response: An array of [Custom Away Status](#custom-away-status-json-format)

### Get a single custom away status 

  `GET /api/v1/livechat/customAwayStatus/{id}`
  - Parameters: No parameters
  - Response: [Custom Away Status](#custom-away-status-json-format)

### Create a new custom away status 

  `POST /api/v1/livechat/customAwayStatus`
  - Parameters: [Custom Away Status](#custom-away-status-json-format)
  - Response: [Custom Away Status](#custom-away-status-json-format)

### Update a custom away status 

  `PUT /api/v1/livechat/customAwayStatus/{id}`
  - Parameters: [Custom Away Status](#custom-away-status-json-format)
  - Response: [Custom Away Status](#custom-away-status-json-format)
    
### Remove a custom away status 

  `DELETE /api/v1/livechat/customAwayStatus/{id}`
  - Parameters: No parameters
  - Response: 200 OK   
    
# Ban
  You need `Manage Ban List` permission to manage ban list.
  + `GET /api/v1/livechat/bans` -get list of bans
  + `GET /api/v1/livechat/bans/{id}`  -get a single ban
  + `POST /api/v1/livechat/bans` -create a new ban
  + `PUT /api/v1/livechat/bans/{id}`  -update a ban
  + `DELETE /api/v1/livechat/bans/{id}`  -remove a ban

## Model
### Ban JSON Format
  Ban is represented as simple flat JSON objects with the following keys:  

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - |
  | `id` | integer  | yes | no |id of the ban. |
  | `type` | string  | no | yes | type of ban, including `visitor` and `ip` |
  | `visitorId` | string | no | no | visitor's id of the ban if `type` is `visitor`  | 
  | `ipAddress` | string  | no | yes | ip address of the ban if `type` is `ip`, it can be a specific ip `192.168.8.113` or ip range `192.168.8.0/24` or `192.168.8.0-192.168.8.255` |
  | `comment` | string  | no | no | comment of the ban. |

## Endpoint
### Get list of bans

  `GET /api/v1/livechat/bans`
  - Parameters: No parameters
  - Response: An array of [Ban](#ban-json-format)

### Get a single ban

  `GET /api/v1/livechat/bans/{id}`
  - Parameters: No parameters
  - Response: [Ban](#ban-json-format)

### Create a new ban 

  `POST /api/v1/livechat/bans`
  - Parameters: [Ban](#ban-json-format)
  - Response: [Ban](#ban-json-format)

### Update a ban

  `PUT /api/v1/livechat/bans/{id}`
  - Parameters: [Ban](#ban-json-format)
  - Response: [Ban](#ban-json-format)

### Remove a ban

  `DELETE /api/v1/livechat/bans/{id}`
  - Parameters: No parameters
  - Response: 200 OK   

# Conversion Action
  You need `Manage Settings` permission to manage conversion action.
  + `GET /api/v1/livechat/conversionsActions` -get list of visitor segments
  + `GET /api/v1/livechat/conversionsActions/{id}`  -get a visitor segment
  + `POST /api/v1/livechat/conversionsActions` -create a new visitor segment

## Model
### Conversion Action JSON Format
  Conversion Action is represented as simple flat JSON objects with the following keys:  

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - |
  | `id` | integer | yes | no |id of the conversion action. |
  | `name` | string | no | yes |  name of the conversion action. |
  | `isEnable` | boolean | no | no | whether the conversion action is enable or not. |
  | `type` | string | no | no | type of the conversion action, including `url`, `customVariable` and `api`. |
  | `customVariable` | string  | no | no |  the name of the custom variable, available when `type` is `customVariable`. |
  | `matchType` | string | no | no |  match type of the conversion action, available when `type` is `customVariable` or `url`. |
  | `matchValue` | string | no | no |  match value of the conversion action, available when `type` is `customVariable` or `url`. |
  | `isCaseSensitive` | boolean | no | no |  whether the conversion action is case sensitive or not, available when `type` is `url`. |
  | `isAssignValue` | boolean | no | no |  whether a value is assigned for the conversion action or not. |
  | `isAssignValueFromCustomVariable` | boolean | no | no |  whether the value for assigning to the conversion action is come from a assigned value or a custom variable, `true` means from custom variable |
  | `assignValue` | string | no | no |  the value assigned for the conversion action |
  | `customVariableForAssignValue` | string | no | no |  the value come from the custom variable |


## Endpoint
### Get list of conversion actions

  `GET /api/v1/livechat/conversionsActions`
  - Parameters: No parameters
  - Response: An array of [Conversion Action](#conversion-action-json-format)

### Get a single conversion action

  `GET /api/v1/livechat/conversionsActions/{id}`
  - Parameters: No parameters
  - Response: [Conversion Action](#conversion-action-json-format)

### Create a new conversion action

  `POST /api/v1/livechat/conversionsActions`
  - Parameters: [Conversion Action](#conversion-action-json-format)
  - Response: [Conversion Action](#conversion-action-json-format)

### Update a conversion action

  `PUT /api/v1/livechat/conversionsActions/{id}`
  - Parameters: [Conversion Action](#conversion-action-json-format)
  - Response: [Conversion Action](#conversion-action-json-format)

# Visitor Segmentation
  You need `Manage Settings` permission to manage visitor segmentation.
  + `GET /api/v1/livechat/visitorSegments` -get list of visitor segments
  + `GET /api/v1/livechat/visitorSegments/{id}`  -get a visitor segment
  + `POST /api/v1/livechat/visitorSegments` -create a new visitor segment
  + `PUT /api/v1/livechat/visitorSegments/{id}`  -update a visitor segment
  + `DELETE /api/v1/livechat/visitorSegments/{id}`  -remove a visitor segment

## Model
### Visitor Segmentation JSON Format
Visitor Segmentation is represented as simple flat JSON objects with the following keys:  

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - |
  | `id` |integer  | yes | no |id of the visitor segment.
  | `name` |string  | no | yes | name of the visitor segment.
  | `color` |string  | no | no | color of the visitor segment
  | `isEnable` |boolean  | no | no | whether the visitor segment is enable or not.
  | `priority` |int  | no | no | priority of the visitor segment.
  | `description` |string  | no | no | description of the visitor segment.
  | `conditions` |[Conditions](#conditions-json-format)  | no | no | an trigger condition json object. |
  | `notification` | string or object  | no | no | `none` or `{"agents":[1,2,3]}` or `{"agents": [1,2]"}` |

## Endpoint
### Get list of visitor segmentation

  `GET /api/v1/livechat/visitorSegmentations`
  - Parameters: No parameters
  - Response: An array of [Visitor Segmentation](#visitor-segmentation-json-format)

### Get a single visitor segmentation

  `GET /api/v1/livechat/visitorSegmentations/{id}`
  - Parameters: No parameters
  - Response: [Visitor Segmentation](#visitor-segmentation-json-format)

### Create a new visitor segmentation 

  `POST /api/v1/livechat/visitorSegmentations`
  - Parameters: [Visitor Segmentation](#visitor-segmentation-json-format)
  - Response: [Visitor Segmentation](#visitor-segmentation-json-format)

### Update a visitor segmentation

  `PUT /api/v1/livechat/visitorSegmentations/{id}`
  - Parameters: [Visitor Segmentation](#visitor-segmentation-json-format)
  - Response: [Visitor Segmentation](#visitor-segmentation-json-format)

### Remove a visitor segmentation

  `DELETE /api/v1/livechat/visitorSegmentations/{id}`
  - Parameters: No parameters
  - Response: 200 OK   

# Visitor SSO Settings
  You need `Manage Settings` permission to setting sso for a site.
  + `GET /api/v1/livechat/visitorSSO` -Get sso settings of visitor
  + `PUT /api/v1/livechat/visitorSSO`  -Update configuration of visitor

## Model
### SSO Data Mapping JSON Format
Data Mapping is represented as simple flat JSON objects with the following keys:  

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - |
  | `ssoAttribute` |string  | no | yes | SSO attribute name |
  | `comm100Field` |string  | no | yes | comm100 field name |

### Campaign SSO Options JSON Format
SignIn Options is represented as simple flat JSON objects with the following keys:  

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - |
  | `campaignId` |integer  | yes | no |id of the campaign. |
  | `signInType` |string  | no | no | type of the sign in, including `no`, `optional` and `required`. |
  | `isSkipPrechat` |boolean  | no | no | whether the pre-chat form is skipped when visitors sign in. |

### Visitor SSO Settings JSON Format
Visitor SSO Settings is represented as simple flat JSON objects with the following keys:  

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - |
  | `siteId` |integer  | yes | no |id of the site which the visitor sso belongs to. |
  | `isEnable` |boolean  | no | yes |  whether visitor sso is enable or not. |
  | `signInUrl` |string  | no | no | url which visitor sign in |
  | `idpCertificate` | string  | no | no | base64 of the Identity Provider Verification Certificate content. |
  | `idpCertificateFileName` |string  | no | no |  file name of the certificate. |
  | `dataMappings` |array  | no | no |  an array of [SSO Data mapping](#sso-data-mapping-json-format) |
  | `campaignSSOOptions` |array  | no | no |  an array of [SignIn Options](#singin-options-json-format) |

## Endpoint
### Get sso settings of visitor

  `GET /api/v1/livechat/visitorSSO`
  - Parameters: No parameters
  - Response: [Visitor SSO Settings](#visitor-sso-settings-json-format)

### Update sso settings of visitor

  `PUT /api/v1/livechat/visitorSSO`
  - Parameters: [Visitor SSO Settings](#visitor-sso-settings-json-format)
  - Response: [Visitor SSO Settings](#visitor-sso-settings-json-format)


# Auto allocation
 You need `Manage Settings` permission to config for a site.
  + `GET /api/v1/livechat/autoAllocation` - Get auto allocation configuration 
  + `PUT /api/v1/livechat/autoAllocation`  - Update auto allocation configuration 
## Model

### Auto Allocation JSON format

  Auto Allocation is represented as simple flat JSON objects with the following keys:

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - |
  | `isEnable` | boolean | no | yes | whether the auto allocation is enable or not. |
  | `allocationRule` | string | no | no | rule of chat allocation, including `load banlancing` 銆乣round robin` and `capability weighted` |
  | `isLastChattedPreferred` | boolean | no | no | whether last-chatted agent is prefer or not |
  | `isMaxChatForAllAgents` | boolean | no | no | whether to set the same maximum number of chats for all agents |
  | `maxChatForAllAgents` | integer | no | no | maximum number of chats of all agents |
  | `isAllocateChatWhenAgentInAudioVideo` | boolean | no | no | whether allocate chats to agents who are having audio or video chats |
  | `isAllowAgentManualAcceptChat` | boolean | no | no | whether allow agent manual accept chat in agent console |

  ## Endpoint 

  ### Get auto allocation configuration 

  `GET /api/v1/livechat/autoAllocation`
  - Parameters: No Parameters
  - Response: [Auto Allocation](#auto-allocation-json-format)

  ### Update auto allocation configuration

  `PUT /api/v1/livechat/autoAllocation`
  - Parameters: [Auto Allocation](#auto-allocation-json-format)
  - Response: [Auto Allocation](#auto-allocation-json-format)


# Live Chat Config
  You need `Manage Settings` permission to config for a site.
  + `GET /api/v1/livechat/configs` -Get configuration for a site
  + `PUT /api/v1/livechat/configs`  -Update configuration of a site

### Live Chat Config JSON Format
  Live Chat Config is represented as simple flat JSON objects with the following keys:  

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - |
  | `siteId` | integer  | yes | no |id of the site which the configuration belongs to. |
  | `isEnableMultipleCampaigns` | boolean  | no | no |  whether multiple campaigns are enable or not in the site. |
  | `isEnableAutoAllocation` | boolean  | no | no | whether auto allocation is enable or not in the site. |
  | `isEnableCustomAwayStatus` | boolean  | no | no | whether custom away status is enable or not in the site. |
  | `isEnableDepartment` | boolean  | no | no | whether department is enable or not in the site. |
  | `isEnableAutoTranslation` | boolean  | no | no |  whether auto translation is enable or not in the site. |
  | `isEnableAudioAndVideoChat` | boolean  | no | no |  whether audio&video chat is enable or not in the site. |
  | `isEnableVisitorSegmentation` | boolean  | no | no |  whether visitor segmentation is enable or not in the site. |
  | `isEnableVisitorSSO` | boolean  | no | no |  whether visitor SSO is enable or not in the site. | 
  | `isEnableCreditCardMasking` | boolean  | no | no |  whether Credit card masking is enable or not in the site. |
  | `isEnableCustomVariables` | boolean  | no | no |  whether custom variables are enable or not in the site.
  | `isEnableSalesforce` | boolean  | no | no |  whether Salesforce integration is enable or not in the site.
  | `isEnableZendesk` | boolean  | no | no |  whether Zendesk integration is enable or not in the site.
  | `isEnableGoogleAnalytics` | boolean  | no | no |  whether Google Analytics integration is enable or not in the site.
  | `isEnableGotoMeeting` | boolean  | no | no |  whether GotoMeeting integration is enable or not in the site.
  | `isEnableJoinme` | boolean  | no | no |  whether Joinme integration is enable or not in the site.

### Get configurationuration for a site

  `GET /api/v1/livechat/configs`
  - Parameters: No parameters
  - Response: Site Config Json Object.

### Update configuration of a site

  `PUT /api/v1/livechat/configs`
  - Parameters: te Config Json Object.
  - Response: Site Config Json Object.

# Secure Form
  + `GET /api/v1/livechat/secureForms` -get list of secure forms
  + `GET /api/v1/livechat/secureForms/{id}`  -get a secure form
  + `POST /api/v1/livechat/secureForms` -create a new secure form
  + `PUT /api/v1/livechat/secureForms/{id}`  -update a secure form
  + `DELETE /api/v1/livechat/secureForms/{id}`  -remove a secure form

## Model
### Secure Form JSON Format
Secure Form is represented as simple flat JSON objects with the following keys:  

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - |
  | `id` | integer  | yes | no | id of the secure form. |
  | `name` | string  | no | yes | name of the secure form. |
  | `description` | string  | no | no | description of the secure form. |
  | `fields` | array | no | no | an array of [Field](#field-json-format) |


## Endpoint
### Get list of secure forms

  `GET /api/v1/livechat/secureForms`
  - Parameters: No parameters
  - Response: An array of [Secure Form](#secure-form-json-format)

### Get a single secure form

  `GET /api/v1/livechat/secureForms/{id}`
  - Parameters: No parameters
  - Response: [Secure Form](#secure-form-json-format)

### Create a new secure form

  `POST /api/v1/livechat/secureForms`
  - Parameters: [Secure Form](#secure-form-json-format)
  - Response: [Secure Form](#secure-form-json-format)

### Update a secure form

  `PUT /api/v1/livechat/secureForms/{id}`
  - Parameters: [Secure Form](#secure-form-json-format)
  - Response: [Secure Form](#secure-form-json-format)

### Remove a secure form

  `DELETE /api/v1/livechat/secureForms/{id}`
  - Parameters: No parameters
  - Response: 200 OK   

# Webhook
  + `GET /api/v1/livechat/webhooks` - Get list of webhooks
  + `POST /api/v1/livechat/webhooks` - Create a new webhook
  + `PUT /api/v1/livechat/webhooks/{id}` - Update a webhook
  + `DELETE /api/v1/livechat/webhooks/{id}`  - Remove a webhook

## Model
### Webhook JSON Format
Webhook is represented as simple flat JSON objects with the following keys:  

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - |
  |`id` | integer  | yes | no | id of the webhook. |
  |`event`| string  | no | yes | event of webhook, including `offlineMessageSubmitted`, `chatStarted`, `chatEnded` and `chatWrappedUp`. |
  |`targetUrl`| string  | no | yes |  target url of the webhook. |

## Endpoint
### Get list of webhooks

  `GET /api/v1/livechat/webhooks`
  - Parameters: No parameters
  - Response: An array of [Webhook](#webhook-json-format)

### Create a new webhook

  `POST /api/v1/livechat/webhooks`
  - Parameters: [Webhook](#webhook-json-format)
  - Response: [Webhook](#webhook-json-format)

### Update a webhook

  `PUT /api/v1/livechat/webhooks/{id}`
  - Parameters: [Webhook](#webhook-json-format)
  - Response: [Webhook](#webhook-json-format)

### Remove a webhook

  `DELETE /api/v1/livechat/webhooks/{id}`
  - Parameters: No parameters
  - Response: 200 OK   

# Custom Variables
  + `GET /api/v1/livechat/customVariables` -Get list of custom variables
  + `POST /api/v1/livechat/customVariables` -Create a new custom variable
  + `PUT /api/v1/livechat/customVariables/{id}`  -Update a custom variable
  + `DELETE /api/v1/livechat/customVariables/{id}`  -Remove a custom variable

## Model
### Custom Variable JSON Format
Custom Variable is represented as simple flat JSON objects with the following keys:  

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - |
  | `id` | integer  | yes | no | id of the custom variable. |
  | `name` | string  | no | yes | name of the custom variable |.
  | `type` | string  | no | yes | type of the custom variable., including `text`, `integer` and `decimal`. |
  | `value` | string  | no | nos | value of the custom variable. |
   |`hyperlink` | string  | no | no |  hyperlink of the custom variable. |

### Get list of Custom Variables

  `GET /api/v1/livechat/customVariables`
  - Parameters: No parameters
  - Response: An array of [Custom Variable](#custom-variable-json-format)

### Create a new Custom Variable

  `POST /api/v1/livechat/customVariables`
  - Parameters: [Custom Variable](#custom-variable-json-format)
  - Response: [Custom Variable](#custom-variable-json-format)

### Update a Custom Variable

  `PUT /api/v1/livechat/customVariables/{id}`

  - Parameters: [Custom Variable](#custom-variable-json-format)
  - Response: [Custom Variable](#custom-variable-json-format)

### Remove a Custom Variable

  `DELETE /api/v1/livechat/customVariables/{id}`
  - Parameters: No parameters
  - Response: 200 OK   

# Agent 
  - `GET /api/v1/livechat/agents/{id}` -Get agent info in livechat  
  - `PUT /api/v1/livechat/agents/{id}` -Update agent info in livechat

## Model
### Agent JSON Format
 Agent is represented as simple flat JSON objects with the following keys:  

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - |
  | `id` | integer  | yes | yes | id of the agent.
  | `status` | string  | no | no | status of the agent, including `online`, `away`, `offline` and custom away status defined by site |
  | `ongoingChats` | string  | yes | no | total number of ongoing chats the agent has |
  | `departments` | array  | no | no | an array of department id |
  | `maxChatsCount` | integer  | no | no | the maximum number of concurrent chats that will be automatically routed to the agent when Auto Accept Chat Requests is enabled |
  | `isAcceptAllocation` | boolean | no | no | whether the agent accept auto allocation |

### Get agent info in livechat  

  `GET /api/v1/livechat/agents/{id}`
  - Parameters: No parameters
  - Response: [Agent](#agent-json-format)

### Update agent info in livechat

  `PUT /api/v1/livechat/agents/{id}`
  - Parameters: [Agent](#agent-json-format)
  - Response: [Agent](#agent-json-format)

# Chat
  + `Get /api/v1/livechat/chats` - Get chats list.
  + `Get /api/v1/livechat/chats/{chat_id}` - Get a single chat.

## Model
### Custom Field Value JSON Format
 Custom field is represented as simple flat JSON objects with the following keys:  

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - |
  | `id` | integer  | yes | no | id of the custom field. |
  | `name` | string | no | yes | name of the custom field. |
  | `value` | string | no | no | value of the custom field. |

### Custom Variable Value JSON Format
 Custom variable is represented as simple flat JSON objects with the following keys:  

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - | 
  | `id` | integer  | yes | no | id of the custom variable. |
  | `name` | string | no | yes | name of the custom variable. |
  | `value` | string | no | no | value of the custom variable. |

### Attachment Json Foramt
 Attachment is represented as simple flat JSON objects with the following keys:  

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - | 
  | `name` | string | no | yes | name of the attachment. |
  | `uri` | string | no | no | uri of the attachment. |

### Chat Message Json Format 
  Chat Message is represented as simple flat JSON objects with the following keys:

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - | 
  | `time` | datetime  | no | no | the time of this message sent |
  | `sender` | string | no | no | name of this message's sender |
  | `type` | stirng | no | no | type of this message, maybe `agent` or `visitor` or `system` |
  | `content` | string | no | no | content of this message's sender |

### Chat Wrapup Json Format
  Chat Wrapup is represented as simple flat JSON objects with the following keys:

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - | 
  | `category` | string | no | no | category of this chat's wrapup |
  | `comment` | stirng | no | no | comment of this chat's wrapup |
  | `fields` | array | no | no | array of [Custom Field Value](#custom-field-value-json-format) |

### Post-Chat Survey Json Format
  Post Chat Survey is represented as simple flat JSON objects with the following keys:

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - | 
  | `ratingGrade` | string | no | no | rating grade of this chat's suevey |
  | `ratingComment` | stirng | no | no | rating comment of this chat's suevey |
  | `fields` | array | no | no | array of [Custom Field Value](#custom-field-value-json-format) |

### Chat JSON Format 
 Chat is represented as simple flat JSON objects with the following keys:  

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - |  
  | `id` | integer  | yes | yes | id of the chat. |
  | `ssoUserId` | string | yes | no | sso id of visitor |
  | `name` | string | no | no | name of the visitor |
  | `email` | string | no | no | email of the visitor |
  | `department` | string | no | no | department the visitor selected in the pre-chat window. Agent can also update the value while chatting with visitors. |
  | `agents` | array | no | no | agent name who participate in the chat |
  | `prechatFields` | array | no | no | values of custom fields entered by visitors in the pre-chat window. An array of [Custom Field Value](#custom-field-value-json-format). |
  | `customVariables` | array | no | no | information of custom variables captured from the web page visitors viewed. An array of [Custom Variable Value](#custom-variable-value-json-format). |
  | `requestTime` | datetime | no | no | time when the chat requested |
  | `waitingTime` | string | no | no | amount of time a visitor has been waiting before his/her chat request was accepted |
  | `endTime` | datetime | no | no | time when the chat ended |
  | `chatTranscript` | array | no | no | array of [Chat Message](#chat-message-json-format) |
  | `attachments` | array | no | no | files the operator send to the visitor or vice versa as well as the screenshots sent to the operator by the visitor through Comm100 Screen  Capture. An array of [Attachment](#attachment-json-foramt) |
  | `postChat` | [Post-Chat Survey](#post-chat-survey-json-format) | no | no | post chat survey of this chat |
  | `wrapup` | [Chat Wrapup](#chat-wrapup-json-format) | no | no | agent wrapup for this chat |


## Endpoint
### Get chats list
- End Point 
  `Get /api/v1/livechat/chats`

- Parameters: 
  - `timeFrom` - the beginning of query time
  - `timeTo` - the end of the query time
  optional锛�
  - `timezone` - time zone of the `timeFrom` and `timeTo`, defaults to UTC time
  - `agentId` - id of the agent who participate in the chat.
  - `departmentId` - id of the department which the chat belongs to.
  - `categoryId` - id of the category which the chat belongs to 
  - `keywords` - the key words of inquiring the chat
  + `conditions` - the condition list of inquiring the chat `conditions[0][field]=agent&conditions[0][operate]=is&conditions[0][value]=michael`
    - `field` - field name of the condition.
    - `operate` - operate expression of the condition.
    - `value` - the value correspond with the field
  - `pageIndex` -the page index of query.
  - `pageSize` - the page size of this query. defaults to 10, maximum is 500

  

- Response 
  - `total` - total count of the list.
  - `previousPage` - url of the previous page.
  - `nextPage` - url of the next page.
  - `chats` - an array of [Chat](#chat-json-format)


### Get a single chat

  `Get /api/v1/livechat/chats/{id}`
  - Parameters: No parameter.
  - Response: [Chat](#chat-json_format)


# Offline Message
  + `Get /api/v1/livechat/offlineMessages` -Get Offline messages list.

## Model
### Offline Message JSON format
 Offline Message is represented as simple flat JSON objects with the following keys:  

  | Name | Type | Read-only | Mandatory | Description |
  | - | - | :-: | :-: | - |  
  | `id` | integer  | yes | yes | id of the chat. |
  | `time` | datetime | yes | no | time of this offline message submitted. |
  | `ssoUserId` | string | yes | no | sso id of visitor |
  | `name` | string | no | no | name of the visitor |
  | `email` | string | no | no | email of the visitor |
  | `department` | string | no | no | department of this offline message |
  | `agent` | string | no | no | agent of this offline message belong |
  | `content` | string | no | no | content of this offline message |
  | `fields` | array | no | no | values of custom fields entered by visitors in the offline message window. An array of [Custom Field Value](#custom-field-value-json-format). |
  | `customVariables` | array | no | no | information of custom variables captured from the web page visitors viewed. An array of [Custom Variable Value](#custom-variable-value-json-format). |
  | `attachment` | [Attachment](#attachment-json-foramt) | no | no | attachment submitted in the offline message |


## Endpoint
### Get messages list

  `Get /api/v1/livechat/offlineMessages` 

  - Parameters: 
    - `timeFrom` - the beginning of query time
    - `timeTo` - the end of the query time
    optional锛�
    - `timezone` - time zone of the `timeFrom` and `timeTo`, defaults to UTC time
    - `campaignId` - id of the campaign which the offline message
    - `departmentId` - id of the department which the offline message belong
    - `agentId` - id of the agent that this offline message belong 
    - `visitorSegmentation` - id of the visitor segment which visitor belongs to.
    - `keywords` - the key words of inquiring the  offline message.
    - `pageIndex` -the page index of query.
    - `pageSize` - the page size of this query, defautls to 10, maximum is 500

  - Response 
    - `total` -total count of the list.
    - `previousPage` -url of the previous page.
    - `nextPage` -url of the next page.
    - `offlineMessages` - an array of [Offline Message](#offline-message-json-format)

# Missed & Refused Chats
## Get missed and refused chats list

  `Get /api/v1/livechat/missedAndRefusedChats`

  - Parameters
    - `timeFrom` - the beginning of query time
    - `timeTo` - the end of the query time
  optional锛�
    - `timezone` - time zone of the `timeFrom` and `timeTo`, defaults to UTC time
    - `type` - type of the chat, including `missed` and `refused`.
    - `campaignId` - id of the campaign which the message of the chat happened in.
    - `departmentId` - id of the department which the chat belongs to.
    - `visitorSegmentation` - id of the visitor segment which visitor belongs to.
    - `pageIndex` -the page index of query.
    - `pageSize` - the page size of this query, defautls to 10, maximum is 500

  - Response 
    - `total` -total count of the list.
    - `previousPage` -url of the previous page.
    - `nextPage` -url of the next page.
    - `missedAndRefusedChats` - list
      + `type` - type of the chat, including `missed` and `refused`.
      + `chat` - [Chat](#chat-json_format)

# Agent chats

## get agent chats list

  `Get /api/v1/livechat/agentChats`

  - Parameters: 
    - `timeFrom` - the beginning of query time
    - `timeTo` - the end of the query time
    optional锛�
    - `timezone` - time zone of the `timeFrom` and `timeTo`, defaults to UTC time
    - `agentId` - id of the agent who paticipate in the chat.
    - `keywords` - the key words of inquiring the chat

  - Response 
    - `agentChats` - `array` agent chats list
      + `agents` - `array`, agent names of the agent chat conversation
      + `transcript` - `array`
        - `time` - `datetime`, time of this message was sent
        - `sender` - `string`, sender name of this message
        - `content` - `string`, content of this message
