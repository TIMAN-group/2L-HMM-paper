> 1.      How relevant is this submission to the scope of JEDM? (if
>         applicable: to the targeted special issue?)
>
> The topic itself, categorizing subsequences of actions in a learning
> management system, is quite relevant.
>
>
> 2.      How novel is the described research? Are the authors aware of
>         related work?
>
> It is somewhat novel, but the authors do not seem to be adequately aware of
> related work in the methodology contribution. They seem to be even less
> aware of substantive work in education.

Thank you. We agree with your assessment of relevance to JEDM, and concede
that our knowledge of related work in education is a potential blind spot
for us as CS researchers.

> 3.      What is the scientific contribution of this submission? Is it
>         clearly explained, in terms of how the paper advances the EDM field
>         or contributes to related fields?
>
> This paper presents a novel method for learning categories of action
> sequences from MOOC clickstream logs. Although the authors have done a bit
> of background research on approaches to MOOC activity sequences, the
> educational content knowledge is very thin. The approach is under-theorized
> and does not adequately address the “why are you doing this” question.

We agree that we are weak on the educational aspect of the related work. We
have attempted to revise this based on your later comments. We also agree
that we may need to more clearly articulate our answer to the "why"
question from a more education-oriented perspective. Our original
description was perhaps too technically motivated and insufficiently
addresses this particular perspective. From education perspective, the motivation for our work is two-fold: 1) there is a need to understand student behavior in detail in the online education environment (which is challenging due to the scale of education), and the proposed model addresses this need (as an "intelligent assistant" for humans); 2) the naturally available student interaction data contains valuable knowledge/patterns about student behavior, which the proposed model can help reveal.  We hope our revised introduction
more clearly articulates why this is an important problem to tackle.

> The paper is on shaky ground because it attempts to do two things and
> does neither well. The first is develop a new method. The second is apply
> the method to learn about behavior patterns in MOOCs.

We respectfully disagree that we do neither well. We could have done a
better job of framing our work (which we feel we have improved in the
revision), but we feel that the model we use in this work is novel in the
education domain and that the behavior patterns we uncover are useful,
unique, and important. (No existing model can be directly applied to this data to produce the same output as the proposed model produces.) 

> The method itself is a twist on Markov switching models or on mixtures of
> Markov Chains and appears to be very related to the following works, which
> are not referenced:
>
> Hamilton, J. D. (1990). Analysis of time series subject to changes in
> regime. Journal of Econometrics, 45(1-2):39–70.
>
> Song, Y., Keromytis, A. D., & Stolfo, S. J. (2009, February). Spectrogram:
> A Mixture-of-Markov-Chains Model for Anomaly Detection in Web Traffic. In
> NDSS (Vol. 9, pp. 1-15).
>
> Gupta, R., Kumar, R., & Vassilvitskii, S. (2016). On Mixtures of Markov
> Chains. In Advances in Neural Information Processing Systems (pp.
> 3441-3449).
>
>
> The last reference is admittedly recent and used spectral methods. However,
> the important point is that these above references all offer more
> systematic descriptions of model properties, for example by studying the
> recoverability of parameters in a simulation study. (Note that the Gupta et
> al. reference showed that EM estimation was error-prone and needed to be
> run on the order of 1000 times to recover parameters as well as the
> spectral approach.)

We agree that our related work section was weak in the breadth sense and
perhaps focuses too much on MOOC-specific or CS-specific research and did
not cover enough related work in wider domains. We wholeheartedly thank you
for your suggested references, which we have incorporated into a
substantially revised related work section that more clearly articulates
how our model differs from similar models that have been applied in other
domains.

Specifically, we have now called out our model's relation to similar
two-layered approaches applied in other domains, articulated how our model
may be viewed as a special case of a more general Hierarchical Hidden
Markov Model with certain hard constraints, and discussed in more detail
how our model relates to the literature about mixtures of hidden Markov
models.

We have also attempted to do a better job of discussing the potential
limitations and drawbacks of our method, including those related to the
application of the EM algorithm for fitting our model, in a new section
added to the paper.


> 4.      Is the work technically sound? Are there enough methodological
>         details? Are claims convincingly substantiated, either through
>         theoretical argument or empirical data?
>
> The current manuscript does not adequately develop the methodology for
> review on its technical soundness, and therefore the application is
> premature. Much of the substantive conclusions are the results of
> Rorschach-test-y looking at graphs.

While there are many results that do indeed require qualitative assessment
of latent state representations and transitions, we disagree that this
makes the method technically unsound. Our goal is to uncover patterns that
exist in this massive clickstream log data, which without a model are
prohibitively expensive for instructors to discover. We view our model as a
component in a human-machine collaborative system in which the
computational techniques employed by the machine are applied to do what
they are good at (namely, uncovering statistical patterns/trends) and the
human effort is leveraged to interpret the patterns and turn them into actionable knowledge.

> There are selective statistical tests performed which violate some basic
> principles of statistical practice.

We feel that we cannot adequately address this criticism without a clear
articulation of exactly where in the paper such mistakes were made, and
what the proper practice should be in those cases. We would thus benefit greatly from more elaboration on this point.

> The issue of temporal grain size/resolution seems important, but is very
> mysterious once the method is actually described. As it is sold, one would
> expect the model itself to determine when the (latent) state has switched.
> But it appears that the authors simply chose a cutoff to divide sequences
> into “one day’s worth of activity.” Why is that a reasonable choice? And
> why should tomorrow’s latent state depend on today’s state (which they do
> in a HMM)?

Choosing the cutoff points for what defines a browsing session is indeed
an important assumption that will impact the patterns that are uncovered.
However, rather than viewing this as a weakness, we can view this as a
strength in the sense that this decision depends entirely on the
granularity of the patterns you wish to discover (following our vision of building a software tool based on the proposed model for use as an intelligent assistant for humans). 

The model still does determine when the latent state switches, but you are
correct in the sense that when it is allowed to determine a switch occurs
is dependent on how the data is segmented and is not completely flexible in
the model itself. It _is_ flexible in the sense that you can change the
segmentation strategy you employ on the sequence data before running the
model, though.

We have attempted in the revision to do a better job of explaining this
assumption, and why we chose the segmentation strategy we did for our
experiments. We also briefly discuss when it might be appropriate to chose
a different segmentation depending on the kinds of patterns you wish to
uncover.

We have also attempted to address the segmentation strategy problem as a
whole in the new section of the paper dedicated entirely to the discussion
of the limitations and potential drawbacks with our approach.

> Also, the semantics/combinatorics is unclear. The authors make
> it sound like the observable “state” is a sequence, which would suggest a
> staggering cardinality of the observable variable (O(10^L) for sequences of
> length L). Rather, it seems that the observable is one of N possible Markov
> chains, corresponding to the cardinality of latent variable.

We do not believe there is an issue here. The observable variable is indeed
a sequence. The cardinality of the set of all such sequences is indeed
exponentially large in the number of available actions for a sequence.
However, the way that we model the _generation_ of these sequences, and
thus the space of model parameters, is as you describe. Each sequence is
modeled as being generated from one of the K Markov models: its initial
state is chosen based on the initial state distribution, and then each
subsequent action is chosen by sampling a transition from the current state
to the next state.

I will attempt to make an analogy with text documents. The space of all
possible English journal articles is unfathomably large, but we can still
model the generation of these articles using simpler statistical models. If
we have a discrete distribution over words, we can model the generation of
a document as repeatedly sampling the next word in the document from this
discrete distribution. This model is obviously naive and doesn't capture
everything we know about how documents are generated, but it is
"sufficient" in the sense that for any text document, the contents of it
can in fact be modeled by repeated sampling of words from some
distribution that covers its vocabulary. We do not require exponentially
many parameters to model document generation in this setting, and similarly
in this paper we do not require exponentially many parameters to model
sequence generation because we make a strong assumption about the kind of
parametric model that is used to generate the observed sequences.

> While the idea of breaking up a longer sequence of observed actions into
> shorter subsequences which are each characterized by a latent state is
> interesting, the usefulness of this approach in the present paper is less
> clear. The authors overstate the degree to which this method will help to
> automatically infer student behaviors, as much of the interpretability of
> the results still rests on human readings of the Markov chains.

We have attempted to modify the paper to be more precise about our claims
about what is automatically discovered and what is manually discovered. We
still feel, however, that this method is useful in the sense that these
patterns cannot be discovered from the raw clickstream data manually by
instructors without the application of a model that can provide statistical
summaries of the data such as the ones provided by our model, and no existing model can be used directly to generate the same behavior patterns as what our model generates. 

> Moreover, the discoveries do not go beyond obvious findings like
> “watching video” states and “reading forum thread” states.

While it is indeed sometimes challenging to discover what the meaning of a
state is, we argue that there are more non-obvious findings later in the
section, where we discover that a student's probability of being in one
particular state that indicates more diverse activity when taking quizzes
correlates negatively with grade outcomes.

> It’s hard to say this from reviewing the figures alone, but the states
> seem to be characterized almost entirely by the self-loops in the Markov
> chain. If that is the case, then surely simpler averaging methods are
> reasonable.

It is indeed the case that the latent state transitions are _mostly_
described by self-loops, but we make a claim in table 2 that the latent
state transition probabilities are also important in that the "low"
performing students tend to transition out of state 2 more than the
"perfect" performing students (essentially saying that students that get
perfect quiz scores are more likely to continue to participate heavily in
the forum between browsing sessions compared to students that performed
poorly on quizzes). You can also see this visibly if you compare Figure
5(b) and Figure 5(c)'s edge weight from transitioning from state 2 to state
1, which is significantly darker in 5(c) than 5(b).

> 5.      Do the authors describe the limitations of their approach in a
>         satisfactory manner?
>
> I would not say so. The authors seem to suggest that this method solves all
> of the problems of inferring behavior in MOOC learner data.

We did not intend to come across this way. We have added a new section to
the paper that discusses the limitations and drawbacks of our approach, and
how these might be addressed in practice. We have also attempted to better
highlight what gaps remain in this section and in our future work.

Specifically, we address what we feel are the two major classes of
limitations of our method. The first class relates to technical challenges
and drawbacks due to the particular statistical framework we have proposed
and the methods we used to perform parameter estimation. This section also
details some implementation challenges related to numerical stability in
the face of very small emission probabilities. The second class relates
more to the interpretability of the patterns we uncover with the current
model formulation and addresses issues like the pre-processing used to
segment the action sequences and its impact on the discovered patterns, the
parameter K for the number of states and its impact on the discovered
patterns, and the difficulty in choosing the "correct" settings. We also
acknowledge the manual effort that is still required to go from discovered
patterns to actionable knowledge.

> 6.      How significant is the research? Will the paper be likely to have
>         an impact on the community?
>
> The method is not convincingly developed, and the results offer no insights
> that seem to merit this approach. If at least the method were better
> described, I think the community might find useful applications of it.

We appreciate this feedback. We have attempted to better describe the model
and more clearly articulate why this particular approach is important
and novel compared to other approaches.


> 7.      Does the title of this paper clearly and sufficiently reflect its
>         contents?
>
> I would suggest that the authors consider an alternative to the name
> “two-layer hidden Markov model.” The model does not have two hidden layers,
> and the mixture/switching of Markov chains seems more apt. The abbreviation
> TL for two-layer also seems ill-advised, since three-layer would have the
> same result.

Perhaps "layers" is making it seem too close to neural network literature,
but we do feel that there are two different "levels" of pattern extraction,
one which models the within-session patterns and one that models the
between-session patterns.

Thanks for pointing out the potential ambiguity in our abbreviation. We
hadn't considered this since we only focused on two layers. We have
switched the abbreviation to 2L-HMM instead to avoid this ambiguity.


> 8.      Are the presentation, organization and length satisfactory?
>
> The introductory section should be shortened, since the details on prior
> work are delayed for too long.

Thank you for the suggestion.

> 9.      Can you suggest additions or amendments or an introductory
>         statement that will increase the value of this paper?
>
> The method needs significantly more rigorous development.  Stylistically,
> the authors should try to be less boastful about the utility of this
> method, which is much more dubious than they make out.

We have attempted to be more clear in the introduction about exactly the
contributions we are making that are sufficiently supported by our existing
experiment results.

> 10.  Can you suggest any reductions in the paper, or deletions of parts?
>
> I don’t think it is necessary to reproduce


> 11.  Are the illustrations and tables necessary and acceptable?
>
> Table 2 has serious flaws. The counts are not independent.

We would benefit greatly from a concrete suggestion on how to improve the
reporting in table 2.

> 12.  Are the key words and abstracts/summary informative?
>
> 13.  Is the paper (c) acceptable for publication with major revisions only
>
> 14.  To what extent does this paper fall within your area of expertise?  (
>      ) fully (X) well ( ) partially ( ) hardly
>
> 15.  Please list any other general comments or specific suggestions below.

Thank you again for your detailed comments. We hope that our revised
manuscript adequately addresses your concerns.
