# Data_view_Unsubscribe
The BusinessUnitUnsubscribes Date View registers all the unsubscribes from emails sent from a specific Marketing Cloud business unit. Other than the Unsubscribe data view which registers global unsubscribes, this data view tracks the unsubscribes per BU. It can help you analyze or automate processes around email subscriptions.
<br>
SELECT
               a.EmailAddress
              ,a.SubscriberKey
              ,j.JobID
              ,j.EmailName
              ,s.EventDate
              ,j.sendclassificationType
              ,j.SendType
              ,a.DateUnsubscribed
              ,a.Status
FROM _Subscribers a
LEFT JOIN _Sent s ON a.SubscriberKey = s.SubscriberKey
LEFT JOIN _Job j ON j.JobID = s.JobID
WHERE a.Status IN ('Unsubscribed', 'Held')
-------------------------------------------------------------------------------------------------------
SELECT
ls.Status,
ls.EmailAddress,
ls.SubscriberKey
FROM TestSubscriberkeyundeliver as se
left join ent._ListSubscribers as ls
on ls.SubscriberKey = se.SubscriberKey
