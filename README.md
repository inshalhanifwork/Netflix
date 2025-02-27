# Netflix

install.packages("ggplot2")
install.packages("dplyr")

library(ggplot2) library(dplyr)

df <- Netflix.Engagement.Dataset

head(df) # Shows first few rows str(df) # Shows structure of dataset

df$Churn.Status <- as.factor(df$Churn.Status) df$Payment.History <- as.factor(df$Payment.History) df$Subscription.Plan <- as.factor(df$Subscription.Plan)

# Customer Churn Analysis

ggplot(df, aes(x = Churn.Status, fill = Churn.Status)) + geom_bar() + labs(title = "Customer Churn Analysis", x = "Churn Status", y = "Count of Customers") + theme_minimal()

# Churn Status vs Subscription Length

ggplot(df, aes(x = Churn.Status, fill = as.factor(df$Subscription.Length..Months.))) + geom_bar(position = "dodge") + labs(title = "Churn Status vs Subscription Length", x = "Churn Status", y = "Count", fill = "Subscription Length (Months)") + theme_minimal()

# Churn Status vs Engagement Rate

ggplot(df, aes(x = Churn.Status, fill = as.factor(df$Engagement.Rate..1.10.))) + geom_bar(position = "dodge") + labs(title = "Churn Status vs Engagement Rate", x = "Churn Status", y = "Count", fill = "Engagement Rate") + theme_minimal()

Description of the Graph: "Churn Status vs Engagement Rate"
This bar chart compares customer engagement levels for those who have churned ("Yes") and those who have not churned ("No"). The x-axis represents the churn status, while the y-axis represents the number of customers. Different colors represent different engagement rates.

Key Insights:
Similar Distribution: The engagement rate distribution is similar for both churned and non-churned customers.
Higher Engagement Does Not Prevent Churn: Even customers with higher engagement levels still churn, indicating that engagement alone does not ensure retention.
Balanced Proportions: Each engagement level has a similar count across both churned and retained customers.
Implications:
Content quality, pricing, or external factors may influence churn more than just engagement.
Additional factors like customer experience, payment flexibility, and service satisfaction need to be analyzed.

# Churn Status vs Payment History

ggplot(df, aes(x = Churn.Status, fill = df$Payment.History..On.Time.Delayed.)) + geom_bar(position = "dodge") + labs(title = "Churn Status vs Payment History", x = "Churn Status", y = "Count", fill = "Payment History") + theme_minimal()

# Churn Status vs Number of Subscribers
ggplot(df, aes(x = Churn.Status)) + geom_bar(fill = "steelblue") +
geom_text(stat = "count", aes(label = ..count..), vjust = -0.5) +
labs(title = "Churn Status vs Number of Subscribers", x = "Churn Status", y = "Number of Subscribers") + theme_minimal()

## Churn analysis revealed that 50.7% (1,778 users) have canceled their subscription, while 49.3% (1,728 users) have retained it. The high churn rate indicates a need for improved retention strategies. Personalized content, flexible pricing, and engagement initiatives can help reduce churn. Additionally, analyzing payment history may provide insights into whether delayed payments contribute to cancellations. These findings can assist Netflix in enhancing user experience and minimizing churn.

## What factors influence whether a customer churns or stays subscribed?
Engagement Rate: Higher engagement does not always prevent churn.
Number of Subscribers: Churn is not significantly affected by total subscribers.
Payment History: Customers with delayed payments are more likely to churn.
Subscription Length: Short-term subscribers have a higher churn rate.
🔹 Solutions:

Offer discounts for long-term subscriptions.
Implement reminders or flexible payment options.
Enhance customer experience through better content and support.

## How does daily watch time impact customer satisfaction?
High engagement indicates active users, but churn still occurs.
Watch time alone does not ensure satisfaction; content quality and service reliability matter.
🔹 Solutions:

Gather customer feedback to identify dissatisfaction causes.
Personalize recommendations to improve user experience.
Improve content variety, pricing, and service quality.

