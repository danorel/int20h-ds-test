# int20h-ds-test
Hackathon Int20h test: summary

Our team has managed to provide 3 different studies:
1. <a href="#statistical-based">Statistical-based approach</a>
2. <a href="#model-based">Model-based approach</a>
3. <a href="#event-introspection">Event introspection</a>

### Studies

#### <div id="statistical-based">Statistical-based approach</div>

...write conclusions here...

#### <div id="model-based">Model-based approach</div>

...write conclusions here...

#### <div id="event-introspection">Event introspection</div>

Another approach that we took to gain insight into the reasons for subscription cancellation is data and event introspection.

Due to the fact that some event types also provide event attributes as additional information, we decided to try to loook whether some of this additional information can be used for the purposes of our task. During this stage we inspected more closely both event types and event attributes.
We looked at the attributes of each event type and possible values of this attributes. 

As a result, we discovered several facts that helped us in other stages:
1. We found that both `Sign Up Success` and `Sign Up Error` events had an attribute for `Method` of sign up. We discovered that while some error events occurred for majority of methods(`Email`, `Google`, `Facebook`) there were no error events for `Apple` method. As this finding could mean that there can be issues with application registration that are specific to some methods, we have decided to take additional look at the distribution of `Payment Method`, `Signup Method` and user platform to check whether subscription cancelling happens more often on some of the platform. However, result was negative.

1. 



It was also discovered that only around 250 users from all dataset have canceled their subscription. Therefore we took statistically representable randomly selected subset of users and looked through their application usage history manually. This way we were hoping to gain some insights both on possible reasons for subscription cancellation and 

### Conclusions

As a result of our research, we combined our conclusions from 3 different studies into 1 list of possible reasons, why the users cancel their subscription (sorted from the most correlated to the least):
1. 
2. 
3.
...
