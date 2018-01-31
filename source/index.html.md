---
title: VEN-U Mobile SDK

#language_tabs: # must be one of https://git.io/vQNgJ
#  - swift

toc_footers:
  - <a href='http://lrsus.com'>Made By LRS</a>

search: true
---

# Introduction

<aside class="notice">
Currently in alpha.
</aside>

VEN-U Mobile SDK provides a way to further customer engagement for companies that are interested in tracking and serving customers by way of their mobile device and the VEN-U locationing solution.

Through the SDK, brands can expand on their existing mobile or loyalty app to interact with the customer who visits them and able to serve them as they broadcast from their phone.

Currently, the VEN-U Mobile SDK is only available for iOS under the Swift language.

# class VenuBroadcast

The VenuBroadcast service enables the iPhone device to broadcast itself according to the company and individual location. According to the unique organization and site location, a unique service number is generated which is forwarded to the VEN-U system once the customer is detected at a table.

<aside class="notice">
Due to limitation of iOS restricting background processes, it is not possible to continue to broadcast if the phone goes to sleep or the app in question is closed. A workaround is currently in discussion.
</aside>

## `public init(orgUUID: String, siteMinor: Int)`

Creates a VenuBroadcast object.

### Parameters

Parameter | Description
--------- | -----------
_orgUUID_ | Organization UUID that must be the same across all VEN-U installs and the mobile app for that site.
_siteMinor_ | 16 bit identifier that should match the mobile ID set across all VEN-U installs. This is used to distinguish mobile customers from table tent customers.

## `public func start() -> Void`

Begins broadcasting. if no service number is set prior to starting, it will generate a service number to use.

## `public func start(serviceNumber: Int, callback: (() -> Void)? = nil) -> Void`

Begins broadcasting according to provided serviceNumber. When service number is being broadcast, optional callback can be used.

Parameter | Description
--------- | -----------
_serviceNumber_ | Service number used to identify mobile customer on site.
_callback_ | Optional function when broadcasting has started.

## `public func stop() -> Void`

Stops broadcasting.

## `public func getServiceNumber() -> Int`

Retrieves service number set when calling `start(serviceNumber: Integer, ...)` or generated number if not set.