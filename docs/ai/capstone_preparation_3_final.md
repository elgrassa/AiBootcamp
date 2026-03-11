# Capstone Preparation 3

## Question 1
### Detailed Answer
MealMaster needs a mix of tool-calling, RAG, structured extraction, deterministic calculators, and long-term user state in Supabase. This allows the assistant to plan meals using real household and nutrition data instead of text generation alone.

Planned tools:
1. **Household profile reader** - fetches dietary restrictions, allergies, dislikes, goals, budget, shopping habits, and available appliances.
2. **Pantry and ingredient reader (post-MVP)** - reads pantry items, quantities, and expiry dates.
3. **Recipe search and fetch** - finds recipes by dietary, cuisine, time, and budget constraints, then returns full recipe details.
4. **Nutrition calculator** - deterministically computes calories, macros, and selected micronutrients from structured ingredient data.
5. **Recipe parser and normalizer** - converts recipe text into structured ingredients and canonical mappings.
6. **RAG knowledge lookup** - retrieves grounded context from nutrition books, dietary guidelines, and evidence-based references.
7. **Constraint validator** - checks allergies, diet rules, appliance limits, prep time, and budget.
8. **Shopping list and refill generator (post-MVP)** - creates shopping lists from plan + pantry + shopping frequency.
9. **Cooked-status tracker** - stores whether planned meals were cooked, eaten, or skipped.
10. **Write/update tools** - save approved plans, update pantry state, and store weekly nutrition summaries.

Together, these tools let MealMaster search, retrieve, calculate, validate, explain, and update user state in a practical way.

## Question 2
### Detailed Answer
I implemented a **RAG-based knowledge lookup tool** for MealMaster.

It answers nutrition questions by first retrieving relevant passages from an indexed knowledge base, then generating a grounded response from retrieved content. The index currently includes manually uploaded nutrition books, ingredient interaction knowledge (for example Powerful Pairs), and recipe datasets across cuisines. RAG is important here because nutrition guidance should be evidence-grounded, not generated from model memory alone.

```python
def rag_answer(
    query: str,
    index,
    model: str = "gpt-4o-mini",
    num_results: int = 5,
    source_filter: str | None = None
) -> dict:
    ...
```

Inputs:
- `query`: natural-language nutrition question
- `index`: vector index containing chunked documents
- `model`: LLM used for synthesis
- `num_results`: number of chunks to retrieve
- `source_filter`: optional filter (for example `"powerful_pairs"` or `"recipes"`)

Outputs:
- `answer`: grounded answer
- `sources`: retrieved source references/excerpts
- `nutrients_mentioned`: nutrients identified in the response
- `grounded`: whether the response is directly supported by retrieved content

Sample output:
```json
{
  "answer": "Vitamin C can help improve absorption of plant-based iron.",
  "sources": [{"title": "Nutrition Guide", "excerpt": "..."}],
  "nutrients_mentioned": ["iron", "vitamin_c"],
  "grounded": true
}
```

Main challenges:
1. **Data inconsistency across sources**: nutrient values differ by region, raw vs cooked state, and measurement standards.
2. **Ingestion and normalization quality**: weak normalization can produce contradictory retrieval results.
3. **Chunking mixed document formats**: prose, lists, and tables require different chunking behavior for good retrieval.

Current status: document upload and semantic search are working in prototype form. Next steps are retrieval quality tuning and stronger validation layers (including structured outputs with Pydantic).

## Question 3
### Detailed Answer
Right now MealMaster has **two agent-like workflows**, not yet a fully formal tool-calling agent runtime end to end.

1. **AI Health Coach**: loads recent food logs, nutrient goals, meal analyses, and family profile context; then uses an LLM prompt to generate personalized, practical guidance.
2. **Meal Plan Generator**: uses household constraints, family profiles, pantry context, and filtered recipes to generate a structured weekly plan; the output is passed through deterministic validation and scoring before save.

Safe high-level instructions used:
```text
You are MealMaster's AI assistant.
Help users build practical, nutritious meal plans that fit real-life constraints.
Always read household context first: allergies, dietary restrictions, goals, budget, time limits, and appliances.
Use user food logs and goals when available for nutrition guidance.
Explain clearly, avoid medical claims, and state uncertainty when needed.
For plans, enforce allergen safety, time limits, budget limits, pantry usage, and recipe variety.
Return structured output for meal plans.
Do not save or update plans without explicit user approval.
```

Example interaction:
- **User request:** "How can I improve iron absorption?"
- **Context used:** recent food logs, nutrient goals, recent meal analyses, family profile, Health Coach workflow.
- **Example answer:** "Based on your recent food logs, your iron intake looks below target. A practical step is to pair plant-based iron sources with vitamin C, for example lemon with lentils or tomato with spinach. It also helps to avoid tea or coffee close to iron-rich meals. If you want, I can suggest meals this week that combine iron sources with the right cofactors."

Prototype status:
- Running now: agent-like workflows, deterministic meal-plan validation and scoring.
- Planned next: deeper RAG integration in the runtime path and stronger structured output validation.

## Short Submission Version
### Q1
MealMaster needs a tool stack that combines profile/pantry read tools, recipe search/fetch, deterministic nutrition calculation, recipe normalization, RAG lookup, constraint validation, shopping/refill generation, cooked-status tracking, and write/update tools backed by Supabase state.

### Q2
I implemented a RAG knowledge lookup tool (`rag_answer`) that retrieves nutrition passages from indexed books, guideline references, and recipe data before synthesis. It returns answer, sources, nutrients mentioned, and a grounded flag. Main challenges are source inconsistency, normalization quality, and chunking mixed-format nutrition documents.

### Q3
Current MealMaster uses two agent-like workflows (Health Coach and Meal Plan Generator), with deterministic validation/scoring already in place. It is still prototype-stage, not a fully formal tool-calling runtime yet. Next steps are tighter RAG path integration and stronger structured output validation.
