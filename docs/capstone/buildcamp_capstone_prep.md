# AI Engineering Buildcamp Capstone Preparation

## Title
MealMaster Capstone Preparation Answers (Q1-Q3)

## Project name
MealMaster

## Context
MealMaster is an AI-powered nutrition and meal planning assistant concept focused on practical weekly planning for individuals and families. The goal is to help users create healthier, budget-aware meal plans based on preferences, restrictions, and household context, while keeping recommendations grounded in reliable nutrition sources.

## Final answers for Q1, Q2, Q3
### Q1
I want to work on MealMaster, an AI-powered nutrition and meal planning assistant. It helps individuals and families plan healthier meals that match dietary needs, cuisine preferences, allergies, and budget constraints. The system is intended to save time by generating practical meal plans, suggesting realistic recipes, and tracking nutrition and ingredient usage. It also aims to reduce food waste and support smarter shopping habits, including weekly family shopping and smaller, more frequent refill purchases.

### Q2
I envision MealMaster as a combination of structured nutrition logic, RAG, and AI-assisted planning tools. During onboarding, users provide preferences and household context such as dietary restrictions, health-oriented goals, budget, shopping habits, and available kitchen appliances. A deterministic ingredient and nutrition layer handles nutrient calculations and constraint checks. A RAG pipeline retrieves grounded context from nutrition books, dietary guidelines, and other evidence-based sources to support explanations and recommendation rationale. Agent-like tools handle tasks such as recipe parsing, ingredient normalization, nutrient calculation, shopping list generation, and plan validation, enabling practical weekly plans with traceable reasoning instead of generic text output.

### Q3
Yes, MealMaster benefits from several external data categories: ingredient nutrition databases, health and nutrition books, evidence-based dietary guidelines, recipe datasets, user-submitted recipes, and optionally grocery price data. Together, these data sources improve nutrition accuracy, increase meal-plan realism, strengthen grounded recommendations, and support budget-aware shopping suggestions.

## Notes on how these answers align with MealMaster without exposing confidential implementation details
- The answers describe product direction, data categories, and system architecture at a high level only.
- They intentionally avoid proprietary prompt design, ranking weights, internal heuristics, and security-sensitive implementation details.
- They position MealMaster as a realistic capstone-stage system, not a finished production platform.
- They keep claims practical and planning-oriented, without medical treatment claims.

## Capstone submission versions
### Detailed version
#### Q1
MealMaster is an AI-powered nutrition and meal planning assistant designed to help individuals and families plan healthier meals aligned with dietary needs, cuisine preferences, allergies, and budget. It focuses on practical planning outcomes: useful weekly meal plans, realistic recipe suggestions, and nutrition plus ingredient tracking. It also supports lower food waste and better spending through smarter shopping and refill planning.

#### Q2
MealMaster combines three core layers: deterministic nutrition logic, retrieval-augmented generation (RAG), and AI-assisted planning tools. The deterministic layer handles nutrient calculations and hard constraints. The RAG layer grounds explanations using nutrition books and evidence-based dietary guidance. Planning tools perform operational tasks such as recipe parsing, ingredient normalization, shopping list creation, and constraint validation. This architecture supports explainable weekly meal plans that are practical, not just conversational.

#### Q3
MealMaster uses external data to improve reliability and usefulness: ingredient nutrition datasets for calculation accuracy, dietary guidelines and trusted nutrition literature for grounded recommendations, recipe datasets and user recipes for variety and personalization, and optional grocery price data for budget-aware planning. These categories directly improve plan quality, recommendation grounding, and shopping practicality.

### Short version
#### Q1
MealMaster is an AI nutrition and meal planning assistant for individuals and families, focused on healthier, practical, and budget-aware weekly meal planning.

#### Q2
It combines deterministic nutrition logic, RAG over trusted nutrition sources, and AI planning tools for recipe parsing, nutrient checks, and shopping support.

#### Q3
It uses external nutrition, guideline, recipe, and optional price data to improve accuracy, grounded recommendations, realism, and budget planning.
