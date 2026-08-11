# Lab 5 - Sequencing Quality Control

**Estimated time:** ~90 minutes total (Part 1: ~30 minutes discussion; Part 2:
remaining time for case analysis)

## Learning Objectives

### Objective 1: Interpret sequencing QC metrics

**Purpose — Why this matters:** Understanding what per-base quality scores,
duplication levels, per-base sequence content, and alignment statistics
actually measure is foundational to reading any FastQC/STAR/RSeQC report
correctly.

**Task — What you will do:** In Part 2, you will read the FastQC, STAR, and
RSeQC output provided for five cases and identify and evaluate the metrics
for each.

**Criteria — How you'll know you're succeeding:** You can name and correctly
define at least 2-3 metrics per case, in your own words, without needing to
look up what they measure. You can place them into the appropriate context of
what patterns or biases you might already expect, which represent a genuine
issue, and which can be mitigated.

### Objective 2: Apply knowledge of expected technical artifacts

**Purpose — Why this matters:** Many "abnormal-looking" QC signals are
well-documented, expected artifacts of standard mRNA-seq library prep rather
than genuine problems. Many FastQC modules will show a "fail" for successful
experiments. Common sequencing issues also have distinct signatures that show
up in these statistics. Telling the two apart avoids wasting effort
re-sequencing data that's actually fine, or wasting effort analyzing data that
cannot be rescued.

**Task — What you will do:** In Part 1, you will rank a list of QC concerns by
severity as a group; in Part 2, you will decide, case by case, which flagged
metrics are expected artifacts and which are genuine causes for concern.

**Criteria — How you'll know you're succeeding:** Your Part 1 ranking and Part
2 case write-ups justify each artifact-vs-concern classification with a
specific technical reason (e.g., citing library-prep chemistry or aspects of
the biology that might explain what you observe).

### Objective 3: Analyze and evaluate a full QC report

**Purpose — Why this matters:** Real sequencing QC reports rarely have one
metric that tells the whole story and there are expected biases due to the
underlying sequencing methodology. Drawing a sound overall conclusion requires
weighing several statistics together as well as considering all of the
different steps in most workflows (sequencing quality control, alignment
rates, etc.).

**Task — What you will do:** In Part 2, for each of the five cases, you will
synthesize at least 2-3 cited statistics into a short paragraph judging the
experiment's success.

**Criteria — How you'll know you're succeeding:** Your paragraph for each case
draws a conclusion that follows from the *combination* of cited statistics
and steps, not from any single metric in isolation.

### Objective 4: Justify a decision to proceed or not proceed with the analysis

**Purpose — Why this matters:** Deciding whether to trust a dataset enough to
commit further analysis time to it is a routine judgment call for any
bioinformatics analyst and one that must be defensible and remain the
responsibility of the individual scientist.

**Task — What you will do:** In Part 2, for each case, you will state whether
you would proceed with further analysis and why. Across all five cases, you
will use the provided hint to identify the one validated, high-quality
experiment and speculate on the main issue present in the other cases.

**Criteria — How you'll know you're succeeding:** Each recommendation is
unambiguous (proceed / do not proceed) and traceable to the specific
statistics you cited earlier in that case's write-up. You can suggest at
least one follow-up analysis or experiment that would potentially confirm
your hypothesis as to the cause of the underlying issues seen in the other
cases.

## Task

### Part 1: Discussion (~30 minutes)

Please make small groups of 3-4 with your peers around you and discuss the
following question:

Assume you were given 2x100nt paired-end Illumina sequencing from an mRNA-seq
experiment, rank the following from most concerning to least concerning:

1. Unequal read lengths
2. Average PHRED score <20 in the last 10 bases
3. 15% of reads have identical sequence
4. 50% of reads are multimapped after alignment to the reference
5. 10% of reads are unmapped after alignment to the reference
6. Non-random nucleotide distribution in the first 6 bases
7. Nucleotide frequencies of A, C, G, T are not equal over the entire read
8. Unequal number of forward and reverse reads

### Part 2: Evaluate five distinct experimental cases (remaining time)

In real sequencing experiments, artifacts or issues often arise from
experimental protocols or methodological choices. Before you can be confident
in the biological analysis, it is critical to carefully evaluate the quality
of your sequencing experiment. This is typically done by inspecting the base
quality of the actual reads through a tool like FastQC as well as checking
certain key statistics like alignment rate to the target genome, and
distribution of reads across various features in the reference genome. Some
of these statistics and metrics have clear interpretations (base call
confidence, etc.) while some may show experiment-specific bias that is
expected and can be mitigated or ignored for most downstream purposes.

For the following activity, you have been provided the sequencing quality
control results from FastQC, the alignment rate statistics from STAR, and
statistics on read distribution from RSeQC for five different experiments
(Case A, Case B, Case C, Case D, Case E). Each case has its own directory
(`case_A/` through `case_E/`), containing `fastqc/`, `star/`, and `rseqc/`
subdirectories with the raw tool output, plus a combined `multiqc_report.html`
summarizing all three.

**Assumptions:**

- The data is derived from a real mRNA-seq experiment with poly-A selected,
  100bp paired-end reads.
- The problems represent common issues that arise in sequencing experiments
  due to experimental protocol, library preparation, etc.
- A problem may be a feature of the underlying reads or an issue introduced
  anywhere in the initial workflow (the sequencing reads themselves,
  generation of the genome index, or alignment to the reference genome).
- One case represents an experiment with high-quality reads and successful
  alignment to the reference genome.

In your same groups, for each case, please comment on the output of each
report by specifically citing at least 2-3 statistics / metrics, and a short
paragraph explaining what this means about the success of the underlying
experiment. Then, make a recommendation about what you believe is right or
wrong with the experiment, and whether you will proceed with further analysis
and why. If you believe something is wrong with a case, speculate on the most
likely root cause behind the pattern of statistics you observed (e.g., a
specific library-prep, sequencing, or biological explanation) and suggest a
follow-up step (an additional check, re-analysis, or wet-lab test) that would
confirm that hypothesis. Your singular hint is that one of the cases is a
validated, high-quality experiment.

Use [`worksheet_template.md`](worksheet_template.md) to record your group's
answers for both Part 1 and Part 2.

## AI Use Disclosure (Course Materials)

This README was developed with AI assistance from Claude Sonnet 5, used to
edit existing text for clarity and organization and to suggest the draft
learning objectives above. The accompanying
[`worksheet_template.md`](worksheet_template.md) was fully AI-generated: it is
a fixed fill-in-the-blank template (headings, prompts, and blank fields)
mechanically derived from this README's own Task section and each objective's
inline Criteria, not original narrative or graded content.

The analysis code used to produce this lab's case data was generated with
Claude using a behavior-driven design (BDD) workflow — behavior/test
specifications were written first, then Claude generated implementation code
to satisfy them — and was manually reviewed and tested by the instructor
before use.

All experimental case data and the original lab narrative text were authored
manually by the instructor. AI was used to generate analysis code (via the BDD
workflow above) and the structural worksheet template; it was not used to
generate case data or original narrative content. AI's other role was limited
to editorial revision of existing text and suggesting candidate learning
objectives, both critically reviewed, edited, and validated by the instructor
before inclusion.

**Boundary:** AI was not used to generate case data or grading criteria, and
is not used to evaluate or grade student submissions for this lab. All
AI-generated code was manually reviewed and tested by the instructor before
use.

The instructor reviewed, edited, and takes full responsibility for all
content in this document.
