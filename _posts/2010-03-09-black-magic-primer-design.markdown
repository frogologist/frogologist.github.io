---
layout: post
title:  "The black magic of primer design"
date:   2010-03-09 10:39:29 +1000
categories: science
---

Designing PCR primers can feel like hunting for the Holy Grail. 

My co-supervisor introduced me to Invitrogen's free OligoPerfect design tool and handed me a modest list of parameters and guidelines. I happily used the tool to design several primers from Genbank sequences, and most of them yielded satisfactory experimental results.

Through my reading of peer-reviewed articles and web resources, I learned about self- and cross-dimerisation of primers. Poorly designed primers can bind to themselves instead of their genetic targets, thus sabotaging the PCR experiment. More sophisticated design or analysis tools can predict such dimers and provide [Gibbs free energy](https://en.wikipedia.org/wiki/Gibbs_free_energy) (delta G) calculations to indicate the strength of each dimer interaction, but different tools give different values. OligoPerfect does not offer such functionality at all.

I started using the design tool Primer3 and Premier Biosoft's NetPrimer to check the primers for dimers and other flaws. Designing "good" primers became difficult because I couldn't reconcile my co-supervisor's preferences with the additional dimer rules.

One thing the tools have in common is poor user experience. They do not permit batch analysis of primer pairs, so you're stuck with a laborious copy-paste-click routine.

Science forums are full of questions about primer design, and there's no easy answer that fits every project. Researchers develop their own rules of thumb and resort to tweaking the experimental conditions (such as the concentration of magnesium ions) to work around primer dimers. 

I lacked the financial budget and project time to purchase and test multiple primers for one target, so it was up to me which parameters to preserve and which to loosen. Should I favour a primer pair with a higher risk of dimerisation but fewer undesirable nucleotide patterns (such as `GGG` or `TCTCTC`), or vice versa?

Learning more about primer design reduced my confidence in the process and increased my unease about scientific research. I wished I could investigate and refine the method itself instead of applying it to my laboratory's scientific questions.