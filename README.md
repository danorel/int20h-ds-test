# int20h-ds-test
Hackathon Int20h test: summary

Our team has managed to provide 3 different studies:
1. [Statistical-based approach](#model-based-approach)
2. [Model-based approach](#model-based-approach)
3. [Event introspection](#event-introspection)

### Studies

#### Statistical-based approach

...write conclusions here...

#### Model-based approach 

In [this study](./study.model-based.ipynb), we changed the initial statement of the problem, where we needed to find the correlation between events/properties with subscription cancellation events. Instead, we are trying to predict whether the user will cancel the subscription or not based on his current profile and events on the platform.

We used a `RandomForestClassifier` as a model for this formulated binary classification problem because it helps to find the list of the most prioritized events/properties from the user profile.

Moreover, we rely on our model because we tested it on the train/test split of the initial dataset. We measure the quality of the model using a precision metric on true-positives predictions (precision = *76%* on true-positives, precision = *100%* on true-negatives). We concluded that our model doesn't overfit, which is why we can trust our results.

Finally, after receiving a prioritized list of events/properties, we interpreted them and formulated *top-5* logical conclusions:
1. "Subscription Premium Renew", "Order": undesirable automatic subscription renewal often motivates users to make refunds.
2. "State": a possible scenario where the government regulates some U.S. regions in the car-related sphere, which leads to the user leak.
3. "Platform", "Model", and "Manufacture": an application on different platforms and operational systems may contain some irritative bugs and errors.
4. "Chat Conversation Opened": sometimes, a support department doesn't respond to the user-initiated chats.
5. "Account History Transaction Details", "Calculator View": users tend to cut their costs after making expense calculations and reviewing transaction history. 

#### Event introspection

Another approach that we took to gain insight into the reasons for subscription cancellation is data and event introspection.

Due to the fact that some event types also provide event attributes as additional information, we decided to try to loook whether some of this additional information can be used for the purposes of our task. During this stage we inspected more closely both event types and event attributes.
We looked at the attributes of each event type and possible values of this attributes. 

As a result, we discovered several facts that helped us in other stages:
1. We found that both `Sign Up Success` and `Sign Up Error` events had an attribute for `Method` of sign up. We discovered that while some error events occurred for majority of methods(`Email`, `Google`, `Facebook`) there were no error events for `Apple` method. As this finding could mean that there can be issues with application registration that are specific to some methods, we have decided to take additional look at the distribution of `Payment Method`, `Signup Method` and user platform to check whether subscription cancelling happens more often on some of the platform. However, result was negative.

1. We have also discovered that the structure of json fields containing event attributes has slight variations. Some of the 2-word event attributes have incosistency with their naming in scope of lowercase/uppercase lettering scheme (e.g. `Membership Type`, `Membership type`). This discovery helped us correct issue during other investigations.

1. We found that refund event happened in approximately 20 cases. That gave us the idea to look manually at some of the subscription cancelling cases to look for possible obvious patterns.

After discussing the event introscection results we discovered that only around 250 users from all dataset have canceled their subscription. Therefore we took statistically representable randomly selected subset of users and looked through their application usage history manually. This way we were hoping to gain some insights both on possible reasons for subscription cancellation and common user behaviour and action sequence. 

We found the following:
1. There is a big proportion of users that cancelled their subscription after a month of subscription but just several days before their monthly subscription would be renewed
1. Some of the users cancel subscription after some time of usage without any obvious technical issue and without close renewement payment date.
1. Many cases of users that cancelled their subscription and that don't fall in previous categories follow the same pattern of steps (`Open Wallet` -> `Open Conversation with Support` -> `Cancel Subscription`). This can indicate that there might be a cancellation reason that is connected with some unexpected expenses that make people write to support and then cancel their subscription. It could be either some transactional issue or for example unexpected increase in fees that user didn't know about. Because of the small number of refund cases (~20), the second theory may look more favourable.

### Conclusions

As a result of our research, we combined our conclusions from 3 different studies into 1 list of possible reasons, why the users cancel their subscription (sorted from the most correlated to the least):
1. 
2. 
3.
...
