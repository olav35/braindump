+++
title = "Data Council.ai Conference Notes"
author = ["Jethro Kuan"]
lastmod = 2019-07-17T11:20:40+08:00
draft = false
math = true
+++

## Taking recommendation technology to the masses - Le Zhang (Microsoft) {#taking-recommendation-technology-to-the-masses-le-zhang--microsoft}

Challenges:

1.  Limited Resource
2.  Fragmented solutions

<https://github.com/Microsoft/recommenders> contains modular functions
for model creation, data manipulation, evaluation etc.

-   SVD, SAR, ALS, NCF, Wide&Deep, xDeepFM, DKN etc.


### Collaborative Filtering {#collaborative-filtering}

Memory based method:

1.  Microsoft Smart Adaptive Recommendation (SAR) algorithm

Model based methods

1.  Matrix factorization methods
    1.  Singular Value decomposition
    2.  Spark ALS

2.  Neural network-based methods
    1.  Restricted Boltzmann Machine (RBM)
    2.  Neural Collaborative Filtering (NCF)


### [SAR](https://github.com/microsoft/Product-Recommendations/blob/master/doc/sar.md) ([ipynb](https://github.com/microsoft/recommenders/blob/master/notebooks/02%5Fmodel/sar%5Fdeep%5Fdive.ipynb)) {#sar--ipynb}

-   Item-to-item similarity matrix via co-occurence
-   User-to-item affinity matrix via co-occurence of user-item interactions
    -   weighted by interaction type and time decay:

\begin{equation}

\end{equation}

-   Free from machine learning and feature collection
-   Explainable results


### Neural Collaborative Filtering (NCF) {#neural-collaborative-filtering--ncf}

-   Neural network based architecture to model latent features
-   Generalization of MF based method


### Content-based Filtering {#content-based-filtering}

-   "Content" can be user/item features, review comments, knowledge
    graph etc.
-   Mitigates cold-start issue
-   Feature vector can be highly sparse

e.g. Factorization machines

\begin{equation}
  \hat{y}(\mathbf{x}) = w\_0 + \sum\_{i=1}^{n} w\_i x\_i +
  \sum\_{i=1}^{n}\sum\_{j=i+1}^n \langle v\_i, v\_j \rangle x\_i x\_j
\end{equation}


#### <span class="org-todo todo TODO">TODO</span> xDeepFM {#xdeepfm}

<a id="892cd5bf0eb9a5acd1874032ba4ca28c" href="#guo17_deepf" title="Guo, Tang, Ye, , Li \&amp; He, Deepfm: a Factorization-Machine Based Neural Network  for Ctr Prediction, {CoRR}, v(), (2017).">(Guo et al., 2017)</a><a>, </a><a id="e4d627ce64d7fbf933655db85b3057e0" href="#lian18_xdeep" title="Lian, Zhou, Zhang, , Chen, Xie, Sun \&amp; Guangzhong, Xdeepfm: Combining Explicit and Implicit Feature  Interactions for Recommender Systems, {CoRR}, v(), (2018).">(Lian et al., 2018)</a>


### <span class="org-todo todo TODO">TODO</span> Deep Knowledge-aware Network <a id="fef749252ffc4be87873f182cdba0fad" href="#wang18_dkn" title="Wang, Zhang, Xie, \&amp; Guo, Dkn: Deep Knowledge-Aware Network for News  Recommendation, {CoRR}, v(), (2018).">(Wang et al., 2018)</a> {#deep-knowledge-aware-network}

Multi-channel word-entity aligned knowledge aware CNN


### Operationalizing a real-time recommender {#operationalizing-a-real-time-recommender}

-   containerize model serving, use Kubernetes to autoscale


## Scaling Data Science Teams - Miguel Rios (Twitter) {#scaling-data-science-teams-miguel-rios--twitter}

-   9-year longitudinal study of scaling data science at Twitter

2 models of DS teams in engineering-driven organizations:

embedded model
: data scientists part of a smaller team, with other
    engineers
    -   Pros:
        -   Dedicated data science resourcing
        -   Alignment between DS and the rest of the team
        -   One roadmap, fewer dependencies
        -   Data science has a more natural "seat at the table"
    -   Cons:
        -   Rigid resourcing (harder to move DS between teams)
        -   Barriers for collaboration between data scientists
        -   Manager may not have domain knowledge (typically an EM)
        -   Risk of Data Science being a support or service to eng. team


centralized model
: data scientists manageed by a data science
    manager, supporting the product teams
    -   Pros:
        -   Data scientists working together (collaboration and knowledge sharing)
        -   DS manager has domain knowledge (between career dev)
        -   Resources can be rebalanced to meet customer demand
        -   Advocacy for better and consistent tech (tooling, datasets,
            etc.)
    -   Cons:
        -   Coordiantion between teams (DS and stakeholder) becomes more complicated
        -   In eng. centric orgs the DS teams need to influence org roadmap
        -   Risk of data science work not being aligned with product
        -   Company needs to support one more function

Best of both worlds: centralized org with embedded teams

E.g.

-   Growth Eng (with centralized DS)
-   Product Eng (with centralized DS)
-   Health Eng (with centralized DS)

-   Centralized proceses, common resources

Challenges:

1.  Everyone has at least 2 teams - centralized DS team, and part of the
    product team
    1.  Risk of meeting and planning overload
    2.  Which is their main team?
2.  Risk of mismatch of expectation between DS leadership and product leadership

How to scale this hybrid org structure to ~100 Data Scientists?

~ Create more layers of abstraction:

-   Split teams into pillars

"A product as a system":

```text
Growth DS -> Product DS -> Revenue Science
                ^^^
Insights, metrics, data enigneering, data visualization
```

Twitter organizes into:

-   Growth
-   Product
-   Health
-   Foundational DS

team charters
Swimlanes - clear differentiation between teams
Working agreement - what to expect from other teams? (e.g.
interactions between data engineering & notifications ds team)

-   How does the data eng team receive requests?
-   What is the SLA of a dataset request?
-   What would be the ownership structure for the request?
-   On what basis this request will be prioritized?

**Create clear communication channels**

-   Have team meetings at all levels
-   Have recurrent sessions to review ongoing projects
-   Have fun with each other - quarterly offsites and other activities

**Build and strengthen your leadership team**

-   Leadership team is their **first team**
-   Have staff meeting, and keep an open standing agenda
-   Do leadership offsites and working sessions (twitter does it monthly
    on a specific topic)
-   Make this reponsible for managing your org's relationship with
    stakeholders

TLDR: align teams with objectives, build structures of your teams:
team charters, working agreements, swimlanes, and strong leadership
team


### Questions: Thoughts on self-servicing (end-to-end) data scientists {#questions-thoughts-on-self-servicing--end-to-end--data-scientists}

-   Moving away from end-to-end


### Question: How to bridge gap in understanding between data eng and data scientists {#question-how-to-bridge-gap-in-understanding-between-data-eng-and-data-scientists}

-   strong overlap in skill set between data eng and scientists e.g.
    engineers are taught to build data pipelines early when joining
    Twitter
-   job of the DS manager


##  {#}

# Bibliography
<a id="guo17_deepf"></a>Guo, H., Tang, R., Ye, Y., Li, Z., & He, X., *Deepfm: a factorization-machine based neural network for ctr prediction*, CoRR, *()*,  (2017).  [↩](#892cd5bf0eb9a5acd1874032ba4ca28c)

<a id="lian18_xdeep"></a>Lian, J., Zhou, X., Zhang, F., Chen, Z., Xie, X., & Sun, G., *Xdeepfm: combining explicit and implicit feature interactions for recommender systems*, CoRR, *()*,  (2018).  [↩](#e4d627ce64d7fbf933655db85b3057e0)

<a id="wang18_dkn"></a>Wang, H., Zhang, F., Xie, X., & Guo, M., *Dkn: deep knowledge-aware network for news recommendation*, CoRR, *()*,  (2018).  [↩](#fef749252ffc4be87873f182cdba0fad)