# Buildcamp Capstone Prep (Detailed)

## Project
MealMaster

## Context
MealMaster is an AI-powered nutrition and meal planning assistant for individuals and families. The goal is to make weekly planning more practical and realistic: meals should fit dietary needs, preferences, allergies, and budget, while staying grounded in reliable nutrition sources.

## Detailed answers (Q1-Q3)

### Q1
I want to work on MealMaster, an AI-powered nutrition and meal planning assistant. It helps individuals and families plan healthier meals that match dietary needs, cuisine preferences, allergies, and budget constraints. The system is meant to save time by generating practical meal plans, suggesting realistic recipes, and tracking nutrition and ingredient usage. It should also help reduce food waste and improve shopping decisions, including both weekly family shopping and smaller refill trips.

### Q2
I see MealMaster as a combination of structured nutrition logic, RAG, and AI-assisted planning tools. During onboarding, users provide preferences and household context such as dietary restrictions, goals, budget, shopping habits, and available kitchen appliances. A deterministic nutrition layer handles nutrient calculations and hard constraints. A RAG pipeline retrieves grounded context from nutrition books, dietary guidelines, and other evidence-based sources to support explanations and recommendation rationale. Tool-like components handle recipe parsing, ingredient normalization, nutrient calculation, shopping list generation, and constraint validation, so the assistant can produce practical weekly plans with clear reasoning instead of only generic output.

### Q3
Yes, MealMaster should use several categories of external data: ingredient nutrition databases, health and nutrition books, evidence-based dietary guidelines, recipe datasets, user-submitted recipes, and optionally grocery price data. These sources improve nutrition accuracy, make plans more realistic, keep recommendations grounded, and support budget-aware shopping decisions.

## Scope and confidentiality note
- This write-up reflects MealMaster's direction at a practical architecture level.
- It intentionally avoids proprietary prompts, ranking logic, internal heuristics, and security-sensitive implementation details.
- It describes a realistic capstone-stage system, not a finished production platform.
- It stays within planning and nutrition-support scope and avoids medical treatment claims.
