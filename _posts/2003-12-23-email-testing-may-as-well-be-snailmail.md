---
title: Email testing may as well be Snailmail
author: Tim
layout: post
permalink: /2003/12/23/email-testing-may-as-well-be-snailmail/
categories:
  - Impressions
tags:
  - email
  - testing
---
Our current implementation of testing emails received is WAY too slow!! It uses a sleep loop to watch an IMAP inbox for a message with a particular subject. There are several problems.

  * The mailbox needs to be cleaned of all test e-mails before each test, in case a stray message of the same subject was left by a failed previous test: TIME CONSUMING
  * The current mail server we use to deliver test e-mails takes more than 1 minute per message.
  * All testing is blocked until the e-mail arrives for the current test. Any way to make parallel tests would really help. Any way to have asynchronously look for an e-mail and then fail a test after it&#8217;s passed might help too.

The merits of testing the actual IMAP/POP inbox for a message are highly debatable too. Unit testing usually should use mock objects to fake complex parts of the system, but this is funtional end-to-end testing. So what should it do? Is it useful? We&#8217;re up to 67 minutes of test time. This is getting ridiculous.
