# Amazon CloudWatch & SNS ☁️🔔

This section covers **Amazon CloudWatch** and **Amazon SNS**, two AWS services commonly used together for monitoring and notifications.

## Amazon CloudWatch 📊

CloudWatch is an AWS monitoring and observability service used to monitor resources, applications, metrics, and logs.

### Topics Covered

* Metrics
* Logs
* Log Groups & Log Streams
* Alarms
* Dashboards
* EC2 Monitoring

### Hands-On

* Monitored EC2 metrics
* Created CloudWatch alarms
* Explored CloudWatch Logs
* Created monitoring dashboards

---

## Amazon SNS 🔔

Amazon Simple Notification Service (SNS) is a managed messaging service used to send notifications to multiple subscribers.

### Topics Covered

* SNS Topics
* Publishers & Subscribers
* Subscriptions
* Email Notifications
* Message Filtering
* AWS Service Integration

### Hands-On

* Created an SNS Topic
* Created a subscription
* Published test messages
* Configured email notifications
* Integrated SNS with CloudWatch alarms

---

## CloudWatch + SNS

A common monitoring workflow is:

```text
AWS Resource
     ↓
CloudWatch
     ↓
Alarm
     ↓
SNS Topic
     ↓
Email / Notification
```

### Status

✅ CloudWatch Notes Completed
✅ SNS Notes Completed
🔄 Hands-On Practice
