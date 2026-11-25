# Econ 3916 PS5: The Recommendation

**To the head of risk:**

The vendor's deal should not be signed just because of the 93% accuracy number, since a model that approves everyone gets 92.9% on this data and still catches zero defaults. When only 7% of loans default, accuracy can't tell a good model from a useless one, so the vendor should send its predicted probabilities on a test set and be judged on how much money it saves.

A simple LASSO model shows what a real model is worth compared to approving everyone. Its accuracy is the same as the null model, but its AUC of 0.714 and PR AUC of 0.186, compared to about 0.07 for random guessing, show it does pick up real risk. A random forest did no better and only disagreed with LASSO on one test loan, so the simpler model makes more sense and is easier to explain to a regulator.

The best threshold is 0.14 instead of the usual 0.5. That number assumes a default loses 60% of the loan and turning down a good applicant loses 8% of the loan in interest plus 250 dollars in reputational cost. With those costs, the 0.14 cutoff cuts test set losses from 1,328,838 dollars to 1,102,710 dollars, and the model's probabilities line up well with real default rates near that cutoff, so the threshold holds up.

The one thing that would change this answer is the real loss on a default, because if it's much lower than 60%, the best threshold moves back toward 0.5 and most of the savings go away.
