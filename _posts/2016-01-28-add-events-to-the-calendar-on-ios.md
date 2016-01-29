---
title: Add Events to the Calendar on iOS
author: Tim
layout: post
categories:
  - How-To
tags:
  - ios
  - calendar
  - swift
---

So you have event information that you want to put into a calendar on iOS. Let's say you have a local struct that keeps track of events your app manages, like football games.

<!--more-->

{% highlight swift %}
struct MyEvent {
    let id: Int
    let title: String
    let startTime: NSDate
    let endTime: NSDate
}
{% endhighlight %}

Perhaps you've got a button in your interface that lets a user add any football game to their favorites list, and when they do you'll try adding it to their calendar as well.

{% highlight swift %}
if addedToFavorites {
    addEventToUserCalendar(myEvent)
} else {
    removeEventFromUserCalendar(myEvent)
}
{% endhighlight %}

First we'll get our authorization status for working with calendar events. From there we'll ask the user for permission to work with their calendar if we've never done so before. Once we have authorization, then the fun begins.

{% highlight swift %}
func addEventToUserCalendar(myEvent: MyEvent) {
    let status = EKEventStore.authorizationStatusForEntityType(.Event)
    let eventStore = EKEventStore()
    switch status {
    case .NotDetermined:
        eventStore.requestAccessToEntityType(.Event) { authorized, error in
            if authorized {
                showEventInUserCalendar(myEvent)
            }
        }
    case .Authorized:
        showEventInUserCalendar(myEvent)
    case .Restricted, .Denied:
        break
    }
}
{% endhighlight %}

We'll create a calendar event from our own event struct and then present a view controller that will let the user edit and save it to the calendar of their choice.

{% highlight swift %}
func showEventInUserCalendar(myEvent: Event) {
    // Create calendar event
    let calendarEvent = EKEvent(eventStore: eventStore)
    calendarEvent.title = myEvent.title
    calendarEvent.startDate = myEvent.startTime
    calendarEvent.endDate = myEvent.endTime
    let fifteenMinutesBefore: NSTimeInterval = -1 * 15 * 60
    let calendarAlarm = EKAlarm(relativeOffset: fifteenMinutesBefore)
    calendarEvent.addAlarm(calendarAlarm)

    // Setup edit view controller
    let editViewController = EKEventEditViewController()
    editViewController.eventStore = eventStore
    editViewController.event = calendarEvent
    editViewController.editViewDelegate = self
    self.presentViewController(editViewController, animated: true, completion: nil)
}
{% endhighlight %}

Once the user saves the event to their calendar, we'll get a callback.

{% highlight swift %}
extension MyViewController: EKEventEditViewDelegate {

    func eventEditViewController(controller: EKEventEditViewController, didCompleteWithAction action: EKEventEditViewAction) {
        if let calendarEvent = controller.event where action == .Saved {
            // Save calendarEvent.eventIdentifier somewhere nice
        }
        self.dismissViewControllerAnimated(true, completion: nil)
    }

}
{% endhighlight %}

Later we can delete the event from their calendar using the identifier we saved. To simplify, I've left the authorization checks out of this method.

{% highlight swift %}
func removeEventFromUserCalendar(event: Event) {
    guard let calendarEventId = // Retrieve it from somewhere nice
    guard let event = eventStore.eventWithIdentifier(calendarEventId) else { return }
    _ = try? eventStore.removeEvent(event, span: .ThisEvent)
}
{% endhighlight %}

Those are the basics of taking the custom event data from your app and adding them to the user's calendar.

_What kind of events are you saving? Leave a comment below to let me know._
