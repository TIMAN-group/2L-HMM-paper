> 1.      How relevant is this submission to the scope of JEDM? (if
>         applicable: to the targeted special issue?)
>
> Submission is very relevant to the scope of JEDM. Authors provide a novel,
> more granual method for modelling student's behaviour in an online course.
> The technique is derived from hidden Markov models (HMMs) builds on earlier
> applications of similar models in MOOCs (Kizilcec et al. 2013, Faucon et
> al. 2016 and others). The technique can be potentially used in any MOOC or
> other online learning environments. Authors provide example uses of the
> technique.
>
> 2.      How novel is the described research? Are the authors aware of
>         related work?
>
> HMMs are well-known and have been already extensively applied in
> educational research. The main contribution of the paper is a new way to
> model states. Instead of treating every user's activity as a state they
> model entire sequence as a state in the higher level HMM. This techniques
> have been already used in practice to model complex transitions, yet that's
> the first application of such models in education (to my best knowledge).
> Authors do refer to existing works and to potentially related educational
> studies.

We thank you for, and agree with, your assessment of the suitability of our
work to the scope of JEDM and the novelty of our research.

> 3.      What is the scientific contribution of this submission? Is it
>         clearly explained, in terms of how the paper advances the EDM field
>         or contributes to related fields?
>
> The key contribution is the more detailed modelling technique, potentially
> capturing two levels of iteraction with a MOOC platform: sequence of
> low-level activities and a major task transitions like solving an
> assignment or viewing forum. Compared to previous studies, authors allow
> change of high level states, which can potentially model transitions
> between engagement levels.
>
> It is clearly stated how the paper advances existing modelling techniques.
> It is however not clear how do they advance educational practice.

We agree that we may not have been clear enough about how applying our
model can potentially lead to advances in educational practice.  We have
added text to the article, particularly in the introduction, to attempt to
more clearly articulate what we believe our educational contribution is:
providing a framework for automatic student behavioral pattern discovery as
a component in a human-machine collaborative system to enable instructors
to extract knowledge from data that is otherwise being un(der)-utilized.

There remains a gap between the modeling technique and educational practice
impact, but we envision that the proposed model can eventually lead to a useful system being built to allow instructors and education researchers to "see" the detailed behavior of students via mining the vast amount of student interaction data that is naturally available on various online education platforms. 


> 4.      Is the work technically sound? Are there enough methodological
>         details? Are claims convincingly substantiated, either through
>         theoretical argument or empirical data?
>
> Paper is technically sound and methodology is explain with great detail.
> Moreover, source code is provided which allows replication of the whole
> study as well as using the technique on other datasets. The methodological
> argument can be technically heavy for educational researchers and authors
> could consider moving some details to appendix or suplementary materials,
> focusing on the high level perspective. A figure illustrating the high
> level idea in the introduction section would simplify understanding and
> following the argument.

Thank you for pointing this out. We agree that the technical modeling
details may be overwhelming for people with little exposure to statistical
techniques like the EM algorithm or CS techniques like dynamic programming.
However, we believe that these details about the data mining aspect of our
model are important enough that they belong in the main text of the
article.

> 5.      Do the authors describe the limitations of their approach in a
>         satisfactory manner?
>
> Authors discuss potential future work, yet they do not comment enough on
> limitations. They introduce a rather complex model and a direct limitation
> of such approach is a potential need of a large dataset for fitting the
> data. Authors don't discuss potential problems of fitting or ways to
> validate the model. There is no clear comparsion with existing models (they
> are discussed in the introduction but not compared in the results).

This assessment is valid, and all of the limitations you have identified
are indeed potential issues with application of our model (or any
sufficiently complex statistical model). We have added an additional
section to the paper to discuss the limitations and drawbacks of our model
and how they might be addressed in practice.

> 6.      How significant is the research? Will the paper be likely to have
>         an impact on the community?
>
> I do believe that unsupervised techniques are key to better understand
> behaviour of students in MOOCs. It is however difficult to estimate
> potential impact of this technique on the community.

We feel this difficulty may be due to our failure to adequately describe
what we feel our concrete educational contribution is. We hope that our
efforts to clarify this will alleviate this concern.

> 7.      Does the title of this paper clearly and sufficiently reflect its
>         contents?
>
> Yes, the title is clear and reflects contents of the paper.
>
> 8.      Are the presentation, organization and length satisfactory?
>
> Yes, the presentation, organization and length are absolutely accurate.

Thank you.

> 9.      Can you suggest additions or amendments or an introductory
>         statement that will increase the value of this paper?
>
> The parts which are not sufficiently covered are:
> * applications: Authors mention potential log analysis software they want
>   to develop, yet even there it's not clearly stated what would be the
>   value for the end-user. Other applications would simplify following the
>   paper and make it more interesting for the educational community.

We have attempted to better articulate what we feel the major application
of this model is for the educational community specifically.

> * validation: Authors present results of fitting the model to existing
>   courses, but there is no way of telling how good is the fit. There are no
>   comparisons with other models.

This is indeed true, but we felt it is also non-obvious how one should
compare our method with prior art for modeling MOOC student behavior when
our approach is substantially different.

We could compare the log likelihood or perplexity that our model achieves
on our data at convergence with that of another more simple statistical
model, but this comparison in general will be unfair due to our model
having more free parameters and may not provide any real insights beyond "a
more complicated model fits training data better".

> 10.  Can you suggest any reductions in the paper, or deletions of parts?
>
> Possibly the technical part could be moved to a supplement, but I don't
> have a strong opinion on that.

> 11.  Are the illustrations and tables necessary and acceptable?
>
> Yes, although labels on page 12 are difficult to read. I would also add an
> illustration in the introduction, when authors are introducing the high
> level idea of the two-level HMM.

We think the idea of adding an explanatory figure to the introduction is a
very good one, and we will do so.

> 12.  Are the key words and abstracts/summary informative?
>
> 13.  Is the paper ( ) acceptable for publication in its present form?  (X)
> acceptable for publication with minor revisions?  ( ) acceptable for
> publication with major revisions only?  ( ) unacceptable for publication,
> even with major revisions?
>
> Paper is acceptable for publication with minor revisions mentioned above
>
> 14.  To what extent does this paper fall within your area of expertise?
> (X) fully () well ( ) partially ( ) hardly

Thank you for your detailed comments and suggestions.

> 15.  Please list any other general comments or specific suggestions below.
>
> Methods are technically great. The main critique here is that authors
> should pay extra attention to show how to validate the model and how to use
> the result in practice. One can fit any model to any data, but not every
> fit is useful. Even in unsupervised learning we need to show that one can
> draw actionable value from the fit.

We agree with this assessment, and we hope that our revised version more
clearly articulates what we believe our concrete educational contribution
is and how this model may be used in practice.
