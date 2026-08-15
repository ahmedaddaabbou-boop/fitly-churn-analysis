# Fit.ly Tech — Churn Analysis: Presentation Script
**Audience:** Senior Leadership
**Format:** Talking head, no slides
**Target duration:** 9–10 minutes (~1,350 words)
**Pace note:** Speak at a measured, confident pace. Pause briefly at each `[PAUSE]` marker.

---

## TIMING GUIDE

| Section | Duration |
|---|---|
| Opening & project overview | ~1 min |
| The business problem | ~1 min |
| What we did | ~1 min |
| Finding 1 — Engagement | ~2 min |
| Finding 2 — Free plan churn | ~1.5 min |
| Finding 3 — Support resolution time | ~1.5 min |
| KPI definition & baseline | ~1 min |
| Recommendations | ~1 min |
| Close | ~30 sec |
| **Total** | **~10 min** |

---

## SCRIPT

---

### OPENING — Project Overview
*[~1 minute]*

Good [morning / afternoon].

My name is [Name], and I'm part of the Analytics team here at Fit.ly Tech.

Over the past two quarters, we have seen churn rising across our subscriber base. This is a significant concern for the business — our cost of acquiring new customers is increasing, and every user we lose puts additional pressure on both Marketing and Product to fill that gap.

Leadership asked us to take a close look at the data, understand what is driving this trend, and come back with clear, actionable recommendations heading into next quarter.

That is exactly what I am going to walk you through today. I will cover: what we analysed and how, the three key findings from the data, the metric I recommend we use to track our progress, and four concrete actions the business can take starting this quarter.

`[PAUSE]`

---

### THE BUSINESS PROBLEM
*[~1 minute]*

Before I get into the findings, I want to briefly set the context.

We currently have an overall churn rate of **28.5%**. That means more than one in four of our subscribers has left the platform. For a subscription business, that number has a compounding effect — the longer it stays elevated, the harder it becomes to grow.

The question leadership asked us to answer was: *why are users leaving, and what can we do about it?*

To answer that, we pulled together data from three sources — our account records, our customer support ticket history, and our in-app activity logs. Together, these three datasets gave us a view of who our customers are, how they behave on the platform, and what their support experience looks like.

`[PAUSE]`

---

### WHAT WE DID
*[~1 minute]*

I want to briefly mention the analytical approach, because it matters for how you interpret the findings.

The datasets came from different internal teams and needed significant cleaning before analysis. For example, roughly 40% of churn status records were blank — we treated these as active users, which is the most conservative assumption. The support channel field used a dash character instead of labelling unknown channels. And the join keys between datasets used different names across systems. All of these were resolved before any analysis was run.

For the statistical comparisons, we used non-parametric tests throughout — specifically the Kruskal-Wallis test — because the resolution time data does not follow a normal distribution. Where a test came back significant, we followed up with post-hoc testing to identify which specific groups were driving the result.

This gives us confidence that the findings I am about to share are not artefacts of the data or the method.

`[PAUSE]`

---

### FINDING 1 — Engagement is the dominant churn driver
*[~2 minutes]*

The most important finding from this analysis is straightforward: **users who engage with the platform stay, and users who do not engage leave.**

We measured engagement across four in-app activities — tracking a workout, watching a video, reading an article, and sharing a workout. We then compared activity levels between users who churned and users who remained active.

The difference is stark. Active users generate, on average, more than double the number of in-app events compared to churned users across every single activity type. The largest gap is in workout tracking and workout sharing — churned users contribute almost no activity in these areas at all.

When we look at the total number of in-app events per user, the picture becomes even clearer. The majority of churned users recorded **zero or one events** in the entire observation window. Essentially, they signed up and never really used the product.

We then split users into engagement quartiles — four groups from the least active to the most active — and measured the churn rate in each group. Users in the **lowest engagement quartile churn at 40%**. Users in the second quartile churn at just **6%**. The third and highest quartile churn at around **4%**.

That is a tenfold difference in churn rate between our least and most engaged users. And every one of these differences was confirmed as statistically significant.

The implication is clear: if we can move a user from the lowest engagement bracket into even the second bracket, we can expect to reduce their probability of churning by approximately 34 percentage points.

`[PAUSE]`

---

### FINDING 2 — The Free plan carries the highest churn rate
*[~1.5 minutes]*

The second finding relates to our subscription tiers.

We have four plans: Free, Basic, Enterprise, and Pro. When we look at churn rate by plan, the **Free tier stands out significantly — with a churn rate of 41%**, which is the highest of any segment and well above the overall average of 28.5%.

The three paid tiers — Basic at 24%, Enterprise at 26%, and Pro at 22% — are broadly similar to each other and considerably better retained.

This pattern makes intuitive sense. Free users have made no financial commitment to the product. They have less skin in the game, and it costs them nothing to leave. Paying customers, by contrast, have already decided the product is worth money to them — and that decision is associated with meaningfully higher retention.

The business implication here is twofold. First, converting free users to a paid plan is likely to directly improve their retention, not just our revenue. Second, free users who are not converting are the group most likely to disengage and churn — and they need a different kind of attention.

`[PAUSE]`

---

### FINDING 3 — Churned users experienced significantly longer support resolution times
*[~1.5 minutes]*

The third finding comes from our customer support data.

When we compare the time it takes to resolve a support ticket for churned users versus active users, we see a large and statistically significant difference. **Churned users had a median resolution time of approximately 18 to 19 hours.** Active users had a median resolution time of approximately **7 hours** — roughly one third of that.

This difference holds across all support topics — whether the ticket was about a technical issue, a billing question, an account matter, or something else. The topic itself does not predict resolution time. What predicts resolution time is whether the user eventually churned.

The Kruskal-Wallis H statistic for this comparison is 486 — the largest statistical signal in the entire dataset.

Now, I want to be clear about what this means and what it does not mean. We cannot say from this data alone that slow support *caused* those users to churn. What we can say is that users who churned consistently waited far longer for their issues to be resolved. Whether that experience contributed to their decision to leave — or whether other factors were at play — requires further investigation. But the association is strong enough that improving support resolution time must be on our agenda.

`[PAUSE]`

---

### KPI DEFINITION & BASELINE
*[~1 minute]*

Before I get to recommendations, I want to propose the metric I believe the business should track going forward.

The metric is **Monthly Churn Rate by Segment** — defined as the number of users who cancelled in a given month, divided by the total active users at the start of that month.

Tracking this monthly, broken down by plan tier and engagement quartile, will allow us to see whether our interventions are working — and for which specific groups.

Our current baseline is 28.5% overall. The segments most in need of attention are Free plan users at 41% and our lowest-engagement users at 40%.

**I am recommending a target of below 20% overall by the end of Q4.** That is an ambitious but achievable goal if we act on the findings from this analysis promptly.

`[PAUSE]`

---

### RECOMMENDATIONS
*[~1 minute]*

I have four recommendations for the business.

**First — re-engage low-activity users immediately.** We should implement an automated trigger — a push notification or email — for any user who records no activity for 14 or more days. The focus of that message should be on workout tracking, which has the largest engagement gap between churned and active users. This is a Q3 priority for Product and Marketing.

**Second — launch a Free-to-paid conversion campaign.** The Free plan's 41% churn rate is the clearest low-hanging fruit in this dataset. A time-limited incentive — a discounted first month on Basic or Pro — could move a meaningful number of these users onto paid plans where retention is substantially higher. Marketing should own this.

**Third — investigate and reduce support resolution times.** Churned users waited nearly three times longer than active users for ticket resolution. Customer Support should set a target resolution time and audit the cases that exceeded 18 hours to understand what caused the delays.

**Fourth — build the churn KPI dashboard.** Without ongoing measurement, we cannot know whether any of this is working. Analytics should build the Monthly Churn Rate dashboard — segmented by plan and engagement — and put it in front of leadership on a monthly basis starting next quarter.

`[PAUSE]`

---

### CLOSE
*[~30 seconds]*

To summarise: churn at Fit.ly is being driven primarily by low engagement and, secondarily, by a poor support experience for users who eventually leave. The Free plan is our highest-risk segment. And we have a clear, measurable target — get overall churn below 20% by end of Q4.

The recommendations I have outlined are practical, they are grounded in the data, and they can begin this quarter.

Thank you for your time. I am happy to take any questions.

---

## DELIVERY NOTES

- **Total word count:** ~1,370 words → approximately 9.5–10 minutes at a comfortable pace
- **Practise the pauses** — senior audiences need a moment to absorb numbers before you move on
- **Round your numbers when speaking** — say "roughly 40%" not "40.2%"; say "nearly 19 hours" not "18 to 19 hours" unless emphasising the range
- **Maintain eye contact with the camera**, not your notes — have the script printed or on a second screen at eye level
- **The three findings are your core** — if you run short on time, compress the methodology section, not the findings