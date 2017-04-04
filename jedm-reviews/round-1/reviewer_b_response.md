> 1.      How relevant is this submission to the scope of JEDM? (if
>         applicable: to the targeted special issue?)
>
> This submission is very relevant to the scope of JEDM. In particular, the
> work focuses on data mining within the MOOC environment. By analyzing
> student behaviors with MOOC's user-system logs, the authors address issues
> involving student interactions in emerging pedagogical environments.

Thank you. We agree with this assessment of our contribution's relevance to
the JDEM community.

> 2.      How novel is the described research? Are the authors aware of
>         related work?
>
> One of the authors' main innovative claims is their two-layer hidden Markov
> model. The idea of layered hidden Markov models is not new in and of
> itself. They state that " A main technical contribution of this paper is to
> propose a more general HMM ... the major deviation of our model from the
> traditional HMM is that our observations are themselves sequences" This
> idea is presented succinctly on the Wikipedia page for "Layered hidden
> Markov model." Additionally, there appears to be a fair amount of
> literature on two-layer and multi-layer hidden Markov models. “Modeling
> Individual and Group Actions in Meetings: A Two-Layer HMM Framework" by
> Zhang et al. seems to use a similar approach. The authors' related works do
> not reference papers using similar methods in different domains.

Thank you for pointing out this deficiency in our related work. In our
revision, we have attempted to more broadly characterize how similar models
to the one we describe have been used in non-education domains, and we have
add citations for such works (including the one you suggested).

Specifically, we have now called out our model's relation to similar
two-layered approaches applied in other domains, articulated how our model
may be viewed as a special case of a more general Hierarchical Hidden
Markov Model with certain hard constraints, and discussed in more detail
how our model relates to the literature about mixtures of hidden Markov
models.

> The authors do, however, reference other papers that use various methods to
> solve problems in the same domain. In this regard, the authors' results,
> analysis, and figures are both novel and interesting.

Thank you.

> 3.      What is the scientific contribution of this submission? Is it
>         clearly explained, in terms of how the paper advances the EDM field
>         or contributes to related fields?
>
> The main scientific contribution of this submission is the
> temporal/transitional characterization of student learning behaviors. The
> authors' analysis provides detailed insights into student behavior in
> MOOCs. The authors explain in a broad sense that this submission bridges a
> gap in unsupervised learning methods for automatically discovering and
> characterizing student learning behavior patterns. Although the method is
> indeed unsupervised, many of the compelling observations seem to require a
> decent amount of manual investigation into the model's results. That is not
> to say that the outcomes fail to contribute to the EDM field - more so that
> they are simply mischaracterized in the text.

We agree that there is still substantial effort required to extract the
actionable knowledge from the patterns that our method uncovers. When we
say that the method is "unsupervised", we mean that from the machine
learning perspective where this term is used to describe methods that can
be applied to raw training data that have not been annotated by experts. We
did not mean to imply that the knowledge extraction itself requires no
effort on behalf of an instructor. However, we do stand by our claim that
this model substantially reduces the effort that would be required to
extract the same knowledge directly from the action sequence data stream.

We have modified the text (particularly our introduction) to attempt to be
more clear about where the automatic part of the model ends (pattern
discovery) and the manual instructor effort part begins (interpretation and
knowledge discovery on top of these extracted patterns).

> 4.      Is the work technically sound? Are there enough methodological
>         details? Are claims convincingly substantiated, either through
>         theoretical argument or empirical data?
>
> The authors' primary method appears to be technically sound via
> mathematical explanation. They present the definitions of the methods that
> their work is based on (hidden Markov models and the Baum-Welch algorithm),
> and they show fairly clearly how they make a slight modification to prior
> work in order to obtain their results. Additionally, it appears that much
> effort has gone into discovering knowledge from their model's output.

Thank you.

> 5.      Do the authors describe the limitations of their approach in a
>         satisfactory manner?
>
> The authors make few if any references to limitations of their approach in
> the paper. It is not clear what challenges they faced or how they mitigated
> those issues.

We agree that we did not adequately address the potential drawbacks and
limitations of our approach. We have added a new section to the paper to
discuss this aspect of the work in detail.

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
> The research is fairly significant in this community. Learning is a dynamic
> process and the authors' transition analysis can help push the community
> into deeper, more complex inquiry into online educational behavior. On the
> other hand, the knowledge discovered by this paper seems to have required
> significant investigation into the model outputs. It is somewhat
> questionable that the community will be able to use this method to
> effectively improve MOOCs at a large scale.

We agree with this assessment---there is still a gap that exists between
this method and the extraction of actionable knowledge. We have made an
effort to more clearly point this out in the work (specifically in our
limitations section), and discuss briefly how this might be addressed by
future work.

> 7.      Does the title of this paper clearly and sufficiently reflect its
>         contents?
>
> The title is simple and mostly accurate. The title could be better if it
> more specifically reflected the unique insights into MOOC student behavior
> that this work develops.

Thank you for this suggestion.

> 8.      Are the presentation, organization and length satisfactory?
>
> The paper is well organized and the length is satisfactory. There are a few
> problems with the presentation. According to the JEDM format, captions for
> tables must occur above the table, while captions for figures must be
> below. Both tables are improperly captioned.

Thanks for pointing this out. We have fixed the table captioning issue.

> There are a few grammatical errors decreasing the readability of the
> paper, mostly near the beginning.

We have re-read and have attempted to revise the beginning of the paper,
but a concrete example of one such mistake we have made would be helpful
for us to take a more focused approach to this revision.

> The style guide mentions that the abstract should be between 100-250
> words, but the abstract in this work is 86 words.

Thank you. We have extended the abstract to discuss more of our findings
in the experimental results section.

> 9.      Can you suggest additions or amendments or an introductory
>         statement that will increase the value of this paper?
>
> Amendments to the introduction and related works would be extremely
> helpful. These sections misrepresent the contributions of the paper.
> Additionally, the related works section is missing acknowledgements of
> literature utilizing layered hidden Markov models. The abstract is a bit
> too short, and focuses much more on the method than the knowledge discovery
> accomplished by this work.

You make good points here. To address these issues in the revision, we have
tried to (1) be more clear about our contribution in the introduction, (2)
amend our related work section to discuss the literature on layered HMMs
and HHMMs, and (3) increase the length of our abstract to highlight some of
the knowledge we uncovered in our experiment section.

> 10.  Can you suggest any reductions in the paper, or deletions of parts?
>
> The sections of this paper are well formed and are not in need of serious
> reductions, besides for amendments to existing parts.

Thank you.

> 11.  Are the illustrations and tables necessary and acceptable?
>
> The figures and tables are well utilized in this paper. For the most part
> they are visually pleasing, though some of the smaller text is overlapped
> by lines. The figures and their descriptions definitely point out the
> potential analysis one can perform using the authors' method.

Getting the visualizations just right has been quite a challenge. We agree
that there are still visibility issues, but we have tried our best to
mitigate these as much as we possibly could.

> 12.  Are the key words and abstracts/summary informative?
>
> 13.  Is the paper (a) acceptable for publication in its present form?  (b)
>      acceptable for publication with minor revisions?  (c) acceptable for
>      publication with major revisions only?  (d) unacceptable for
>      publication, even with major revisions?
>
> This paper is (c) - acceptable for publication with major revisions.
>
> 14.  To what extent does this paper fall within your area of expertise?
>      (X) fully () well () partially () hardly
>
> 15.  Please list any other general comments or specific suggestions below.
>
> The analysis in the "Experiment Results" section is insightful. It is not
> really clear how the comparisons between different figures were made. Did
> the authors manually inspect their figures and draw connections between
> them? Did the model truly "automatically discover and characterize" these
> results? Some of the claims at the beginning of the paper do not feel
> substantiated by the methods and results. The problem is not the research
> itself, but rather the way that the text frames the questions/outcomes.

Thank you for your detailed comments and actionable summary. We agree that
we have not necessarily been clear enough about where the automatic aspects
of our model end and the manual effort requirement begins. We have
attempted in our revision to be more precise about our model's contribution
and to ensure that the claims we make in the beginning of the paper are all
adequately supported by our experiment section.
