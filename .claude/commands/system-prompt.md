# Paper to Reasoning Prompts - Slash Command

## **Input Processing**

When invoked with a paper (PDF text, URL, or file path), follow this workflow:

1. **Paper Validation:**
   - Check publication date (prefer after Nov 1, 2024)
   - Verify it contains novel algorithms, methods, or formulas
   - Ensure no "-NC-" or "no reuse" license restrictions
   - Confirm STEM domain (Biology, Chemistry, Physics, Math, CS, Engineering)

2. **Content Extraction:**
   - Identify key theorems, results, and novel findings
   - Extract mathematical formulas, algorithms, and methods
   - Note section references for each concept

## **Agent Integration**

**Primary Method:** Use the prompt-orchestrator agent if available:
```
"Use the prompt-orchestrator agent to generate prompts from this paper: [paper content]"
```

**Fallback Method:** If orchestrator unavailable, proceed with direct generation following the requirements below.

## **Core Requirements**

### **Prompt Generation Rules**

1. **Self-contained:** Every prompt must include ALL information needed to solve it
   - Define all terms, objects, and notation
   - State all parameters, constants, and assumptions explicitly
   - No external knowledge required beyond basic math/logic

2. **Reasoning-based:** Must require multi-step logical thinking
   - Not simple fact recall or direct extraction
   - Requires synthesis, derivation, or complex calculation
   - Multiple interdependent steps to reach answer

3. **Verifiable Answer:** Single, unambiguous result
   - Numerical value, formula, or short expression
   - Maximum 1-2 sentences if text answer
   - Objectively checkable without interpretation

4. **Model Failure Target:** Design to cause substantive errors
   - Model A MUST fail
   - At least ONE other model (B, C, or D) MUST fail
   - Document failure type: calculation error, logic flaw, constraint violation

5. **Paper Specificity:** Must relate to novel content
   - Use concepts unique to this paper
   - Not commonly found on web or in other papers
   - Justify how prompt uses paper's novel contribution

6. **Quantity:** Generate 4-10 prompts per paper
   - Minimum 4 prompts required
   - Maximum 10 prompts allowed
   - Each prompt independent and self-contained

## **Output Format**

For each prompt, provide:

```
### Prompt [N]:

**Question:**
[Self-contained reasoning problem with all parameters and definitions]

**Steps to Solve:**
1. [High-level step 1]
2. [High-level step 2]
3. [Continue logical reasoning path]
4. [Final calculation/derivation]

**Answer:** [Exact numerical value, formula, or short verifiable statement]

**Paper Reference:** 
- Section: [Section number/title from paper]
- Theorem/Result: [Specific theorem or finding used]
- Novel Concept: [What makes this unique to the paper]

**Prompt Justification:**
[Explain how this prompt specifically relates to novel content in the paper that cannot be commonly found elsewhere]

**Expected Model Failures:**
- Model A: [Expected failure type and reason]
- Model [B/C/D]: [Expected failure type and reason]

**Difficulty:** [Easy/Medium/Hard]

---
```

## **Quality Checklist**

Before finalizing each prompt, verify:

✅ **Self-Containment Check:**
- [ ] All variables defined
- [ ] All constants provided
- [ ] All notation explained
- [ ] No background knowledge assumed

✅ **Reasoning Requirement:**
- [ ] Multiple logical steps required
- [ ] Not solvable by simple lookup
- [ ] Requires synthesis or derivation
- [ ] Clear chain of dependencies

✅ **Answer Verifiability:**
- [ ] Single correct answer exists
- [ ] Answer format specified
- [ ] No ambiguity in solution
- [ ] Can be objectively checked

✅ **Model Failure Potential:**
- [ ] Complex enough to cause errors
- [ ] Targets known model weaknesses
- [ ] Substantive failure (not formatting)
- [ ] Reproducible failure pattern

## **Prompt Diversity Guidelines**

Vary your prompts across these types:
- **Existence proofs:** Does a structure with property X exist?
- **Optimization:** Find minimum/maximum value under constraints
- **Counting:** How many valid configurations exist?
- **Comparison:** Which approach yields better results?
- **Threshold finding:** At what point does behavior change?
- **Algorithm application:** Apply novel method to specific case
- **Formula derivation:** Derive relationship from given conditions

## **Common Pitfalls to Avoid**

❌ **Don't Create:**
- Multiple choice questions
- Yes/no questions without reasoning
- Open-ended "explain why" prompts
- Questions missing critical parameters
- Prompts requiring paper access
- Simple recall questions
- Ambiguous or subjective answers

## **Example Workflow**

1. **Receive Paper Input:**
   ```
   /system-prompt [paper URL or content]
   ```

2. **Extract Key Concepts:**
   - Identify 5-10 novel theorems/results
   - Note formulas, constraints, algorithms

3. **Generate Prompts:**
   - Transform each concept into self-contained problem
   - Ensure reasoning requirement
   - Verify answer uniqueness

4. **Validate Quality:**
   - Run through checklist
   - Confirm model failure potential
   - Verify paper specificity

5. **Format Output:**
   - Number prompts sequentially
   - Include all required fields
   - Add justifications and references

## **Error Handling**

If paper is unsuitable:
- Too old (before Nov 1, 2024): Note but proceed if novel
- No novel content: Reject with explanation
- License restricted: Skip paper
- Non-STEM domain: Redirect to appropriate domain

## **Success Criteria**

Your prompts are successful when:
- All prompts are fully self-contained
- Each requires multi-step reasoning
- Answers are unambiguous and verifiable
- Model A fails on all prompts
- At least one other model fails per prompt
- Each prompt uses paper-specific novel content
- Minimum 4 prompts generated per paper

---

✨ This command transforms research papers into challenging reasoning prompts that expose AI model weaknesses while advancing the frontier of AI capabilities through novel problem-solving scenarios.