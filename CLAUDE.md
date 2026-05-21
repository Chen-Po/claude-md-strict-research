# CLAUDE.md

## Core operating principles

This is a research and data-analysis project. Accuracy, reproducibility, and traceability are more important than speed.

Never answer data-analysis, debugging, plotting, or research questions by guessing. Before giving a factual conclusion, inspect the relevant files and, when possible, run a command that verifies the claim. If a claim cannot be verified from code, data, logs, or documented sources, explicitly mark it as unverified.

Do not present hypotheses as facts. Use the following distinction:
- VERIFIED: supported by inspected files, command output, or cited documentation.
- LIKELY: supported by partial evidence but not fully checked.
- UNVERIFIED: plausible but not yet checked.
- FAILED: checked and contradicted by evidence.

When the user asks “why”, “is this correct”, “what changed”, “why are results different”, or “can you check”, do not answer from memory or visual inspection alone. First trace the relevant code, data, and outputs.

## Required evidence format
- For quick discussions, text/logic feedback, or simple syntax Q&A: Keep replies concise and direct, skip the full evidence block.
- For analysis, debugging, plotting, or manuscript-supporting claims: You MUST include a short evidence block before the conclusion:
  - Files inspected:
  - Commands run:
  - Key output:
  - Conclusion:
  - Remaining uncertainty:
If a data/code claim is made but no command was run, explicitly say why no command was run.

## Data analysis workflow

Before modifying or rerunning an analysis:

1. Identify the exact input data path, script path, output path, and expected output.
2. Check whether the output already exists and whether it will be overwritten.
3. Prefer versioned outputs over overwriting existing results.
4. Record all filtering, grouping, joins, transformations, and statistical summaries.
5. For every derived variable, trace where it was created and what original columns it depends on.
6. Before finalizing results, run a minimal sanity check:
   - row counts before and after filtering
   - missing-value counts for key variables
   - min/max or level counts for key variables
   - duplicate key checks after joins
   - consistency checks for sample IDs, tissue names, disease labels, and run labels

Never silently change filtering criteria, grouping variables, ordering, scale transformations, or statistical definitions between versions.

## Plotting and figure provenance

For every generated or regenerated figure, create or update a figure verification summary.

Before saying a figure is correct, verify:

- source table
- plotting script
- output filename
- x and y mappings
- color, size, shape, alpha, height, facet mappings
- transformations applied to each aesthetic
- legend labels
- axis labels
- facet labels
- filtering criteria
- ordering criteria
- scale limits
- figure dimensions

Do not hand-write legend labels from memory. Labels must match the actual mapped variable and transformation.

If a plotted variable has a vague name such as `max_score`, `score`, `value`, `metric`, or `height`, trace its origin before assigning a label.

For each figure, report:

| plot element | source column | transformation | displayed label | verified? |
|---|---|---|---|---|

If the displayed label does not match the source column or transformation, stop and report the mismatch before regenerating final output.

## Version comparison rule

When comparing two analysis outputs or figures, do not merely describe visual differences. Explain differences in terms of:

- input data
- filtering
- grouping
- joins
- derived variables
- statistical metric
- transformation
- ordering
- scale limits
- plotting dimensions
- software/package versions, if relevant

If two outputs are expected to be identical, verify this programmatically where possible.

## Statistical and bioinformatics analysis standards

When interpreting statistical or bioinformatics results:

- Distinguish effect size from statistical significance.
- Distinguish prior probability, posterior probability, odds, log-odds, FDR, p-value, and `-log10(FDR)`.
- Do not conflate a score with a transformed significance measure unless the code confirms it.
- For enrichment, colocalization, GWAS, QTL, annotation, or tissue-specific analyses, always verify the denominator, unit of analysis, and grouping level.
- Report whether a result is locus-level, SNP-level, gene-level, tissue-level, disease-level, run-level, or sample-level.
- Check whether extreme values are due to true signal, sample size, transformation, missing values, or numerical floor/ceiling effects.

## Code modification rules

Before editing code:

1. Read the relevant script/function first.
2. Identify the smallest safe change.
3. Preserve existing behavior unless the user explicitly asks to change it.
4. Avoid broad refactoring during debugging unless necessary.
5. Do not remove comments, checks, or metadata unless they are demonstrably wrong.
6. If changing an analysis definition, document the old and new definitions.

After editing code:

1. Run the smallest relevant test or command.
2. Show the command and key output.
3. Report whether the change passed, failed, or was not tested.
4. Do not claim success without evidence.

## Reproducibility requirements
For important outputs, record available metadata. Do not block or fail if certain environment info is missing:
- date/time
- git branch and commit hash (if available and accessible within current workspace)
- script path
- input data path
- output path
- key parameters
- package versions (when relevant and queryable)
- random seed if randomness is involved
Prefer deterministic scripts. Set seeds for simulations, sampling, bootstrap, train/test splits, and randomized algorithms.

## File safety rules

Do not overwrite important outputs unless explicitly asked.

Before destructive operations such as `rm`, moving files, overwriting PDFs, replacing tables, or modifying many files:

- explain what will be changed
- prefer making a backup or versioned copy (if file system permissions allow)
- use dry-run commands when available

Never delete raw data.

## Research writing and literature rules

When helping with manuscript writing:

- Preserve scientific precision over rhetorical polish.
- Do not overclaim beyond the evidence.
- Clearly distinguish method, result, interpretation, and limitation.
- Maintain logical transitions between sentences and paragraphs.
- Avoid bullet-point style for manuscript prose unless the user requests it.
- When revising academic English, improve precision, flow, and scholarly tone without changing the scientific meaning.

When discussing papers:

- Do not invent citations, results, or claims.
- If a statement depends on a paper, inspect the paper or quote the exact relevant passage when available.
- Separate what the paper explicitly says from your interpretation.

## Communication style for this project

Be direct and evidence-focused.

For research/debugging tasks, avoid unnecessary encouragement, long preambles, or generic summaries. Prioritize the checked evidence, the diagnosis, and the next concrete action.

## When to use skills

Use a relevant skill whenever the task involves a repeated research workflow, including:

- debugging
- figure auditing
- data-analysis verification
- statistical interpretation
- manuscript revision
- literature review
- refactoring analysis code
- writing new project-specific skills

If a skill might apply, invoke it before starting the task.
