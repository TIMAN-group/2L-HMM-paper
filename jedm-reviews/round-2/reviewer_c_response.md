﻿> I still can’t give this paper a recommendation to publish. The main
> contribution of this paper is a methodology, and this method is not
> developed adequately in section 3.3.2.

We felt that our explanation in Section 3.3.2 was adequate because our
modification to the existing Hidden Markov Model only occurs in changing
the output distribution from what is traditionally a categorical
distribution or a (multivariate) Gaussian to instead be a Markov chain.
Thus, any existing derivation of a discrete-valued Hidden Markov Model
applies, except that the output distribution b(o_t) is changed from a
categorical distribution to a Markov Chain in order to model sequences
instead of discrete values.

In the revision, we have updated this section to hopefully be a bit more
clear about this modification and how to reason about the two new update
equations.

> I cannot know whether or not to believe that it works without either a
> more detailed derivation or at the very least a simulation study.

It is unclear what exactly your concerns are here.

Can you clarify 1) what specific derivation you are looking for, and 2)
what kind of simulation study you had in mind?

Here are a few possibilities that we can think of, along with our responses:

1) You were looking for a proof of convergence of our algorithm (EM algorithm).

Response: All EM algorithms are theoretically guaranteed to converge to a
local maximum; see the following reference:

Dempster, A.P.; Laird, N.M.; Rubin, D.B. (1977). "Maximum Likelihood from
Incomplete Data via the EM Algorithm". Journal of the Royal Statistical
Society, Series B. 39 (1): 1–38. JSTOR 2984875. MR 0501537.

Our algorithm is a special case of EM algorithm, thus it is also guaranteed
to converge.

2) You were looking for a "proof" that our model (an HMM) will actually be
able to capture meaningful patterns in the data.

Response: The maximum likelihood estimate of an HMM would lead to
parameters that give the data the maximum likelihood, thus frequently
occurring patterns in the data can be expected to have high probabilities
according to the estimated model, which enables "discovery" of frequent
patterns. Thus in this sense, our model is also theoretically guaranteed to
"work".

Besides, in general, HMMs have been widely used in many domains with great
success (e.g., speech recognition). Our work applies the general idea of
HMM to a specific application problem in EDM. Note that whether the
discovered frequent patterns are actually useful in an application is an
orthogonal question and we have provided some qualitative and quantitative
evaluation results in the paper, though much more work is still needed in
this direction.

> Equations 9-10 are not a proof, and the notation in them is not consistent
> with the text.

We have attempted to make this more clear in the revision, but we did not
find the prior equations inconsistent with the text, so we cannot be sure
we have solved this problem for you.

If this is still a problem in the revision, in what way is the notation
inconsistent with the text? Can you be more specific? We are unclear as to
where in the description of the EM algorithm updating equations we have
lost you.

Note that if you were looking for a proof of convergence of the algorithm
or a proof why Equations 9-10 can lead to a correct solution to our
optimization problem, this is guaranteed by a general theoretical result
about the EM algorithm (see our response to your previous point).

> In referencing prior art, the authors do not even attempt to
> explain the relationship of the current approach to regime-switching
> (Hamilton, 1990), which seems like the obvious ancestor,

We have added some discussion about the relationship here in the revision
(see paragraph 2 of section 2).

From our perspective, this regime-switching approach is the same as a
hidden Markov model with a particular choice of output distribution (namely
the multivariate Gaussian or an auto-regressive model) in order to model
their real-valued vector data. In that sense, our model is a
"regime-switching" model where instead of the outputs being real-valued
vectors, they are discrete-valued sequences. We then model these sequences
as being generated by a Markov chain. In other words, the distinct
"regimes" our model switches between (what we call the latent states) are
Markov chains over the actions students take in the log data.

>  ...or why they would call something a two-layer HMM when that term is
>  already used to mean something else (Zhang, 2004).

We would prefer to not change the name unless you feel this is a large
enough problem to prohibit publication. We feel that two-layer HMM is still
an adequate description of our model that is succinct and accurate, and
there are other pressures to keep this naming at this point (e.g. the
upcoming EDM conference presentation with the current title/abstract).

In the event that this is still a sticking point with you after this
revision, and you do feel that this overlap is egregious enough to prohibit
our publication, here are a few alternative names we could use instead:

1. Hidden Markov Model with Markov Process Outputs (HMM-MPO)

2. Markov Chain Hidden Markov Model (distinguishing it from Discrete Hidden
   Markov Models, Continuous Hidden Markov Models, or Vector Hidden Markov
   Models), where the first part of the name is reflecting the form of the
   observation distribution: sequence valued (Markov Chain), categorical valued
   (Discrete), real-valued (Continuous), or vector-valued (Vector).

3. Sequence-valued Hidden Markov Model

We would appreciate your input on which of these is appropriate (or perhaps
you providing a naming of your own design) so as to ensure that you will be
satisfied with the naming choice we make with as few revision cycles as
possible.

> The technical limitations section 5.1 is not adequate either in my
> opinion. The smallness of observation probabilities is not the issue, the
> issue appears to be that an exponentially large number of probabilities
> are being estimated. Maybe I’m wrong about this, but, given the absence
> of a derivation, it’s impossible to know.

It is unclear to us why you believe there is "an exponentially large number
of probabilities are being estimated", so would appreciate your further
clarification.

Our best guess is that you were concerned that our HMM, when viewed as a
mixture model for sequence data, would involve a large number of allocation
probabilities of an observed sequence to all possible latent state
transitions. That is, if we have K states and a sequence of T symbols, we'd
have K^T possible state transitions. Conceptually, we would be computing
the posterior probability of all these possible transitions given the
observed sequence in the EM algorithm. This is indeed true (conceptually),
but in reality, we do NOT have to actually compute all of them because of
the possibility of simplifying the computation cleverly using the Baum
Welch algorithm, which is a special case of EM algorithm for HMMs where
the Markovian assumption of state transitions was leveraged to simplify the
computation and allow us to have a polynomial algorithm (see the
explanation in https://en.wikipedia.org/wiki/Baum%E2%80%93Welch_algorithm).
The intuition is that all the history information up to a time point can
often be summarized with just K variables corresponding to the K states
(thus enabling us to essentially "ignore" many combinations in the past
history) since the "future" behavior only depends on the current state.

If your concern is about the parameters of the model itself, then there are
a polynomial number of probabilities to be estimated as we already
explained in the paper and repeated here again to further clarify.
Specifically, if we have N different actions in the action space A and we
set the number of latent states to K, we have

(a) K + K^2 variables for learning the initial state distribution (first
    term) and the transition matrix between the latent states (second term),

(b) For each latent state, N + N^2 variables for learning the initial action
    distribution (first term) and the transition matrix between the actions

Thus the total number of parameters is K + K^2 + KN + KN^2. This is not
exponential, but polynomial in K and N.

We also note that we attempted to explain the number of parameters in
section 3.2:

"We can write the parameters for the first-order Markov model
associated with latent state u as λ^(u) = (π^(u) , A^(u)) where π^(u)
indicates the initial probability vector of length |*A*| and A^(u) is an
|*A*|×|*A*| matrix indicating the transition probabilities between each
pair of actions from *A*."

--> This corresponds to item (b) above.

"In our model, we let Λ = (π, A, λ^(1), ... ,λ^(K)) where π and A are the
parameters of a first-order Markov model over the latent states and each
λ^(i) consists of the parameters for the first-order Markov model over
action sequences for latent state i. Thus π (without superscripts) is an
initial probability vector of length K and A (without superscripts) is a K
× K transition probability matrix, analogous to the case with the
individual first-order Markov model parameters λ^(i) for each latent
state."

--> The last sentence here corresponds to item (a) above.

We regret that this has been unclear. As we mention the number of
parameters for traditional HMMs in section 3.3.1, we have added an explicit
mention of the number of parameters to section 3.3.2 in a similar way,
echoing the description of the parameter space from section 3.2.

> There are many other points I would take issue with (education arguments;
> the statistics of table 2, which I already called foul; etc.), but they are
> all moot if I don’t know whether or not the model itself can be trusted.

We still need more elaboration on this point if you hope to have us fix
what you feel is incorrect with the statistics in table 2. If you could
please tell us not only what is specifically wrong with the table (as we
did not fully understand your prior comments), but how exactly we should go
about fixing it, this will help us come closer to being publishable with
fewer revision cycles.

If we aren't given specific directions in how to improve this, we feel our
only choice is to remove the hypothesis testing entirely from the paper,
which weakens the arguments we are trying to make substantially.

> The inadequate derivation and absence of a simulation study are a
> deal-breaker for me.

We do not understand what you mean by a simulation study. What experiments,
specifically, are you suggesting we perform?