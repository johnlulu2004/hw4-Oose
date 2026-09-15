# Problem Statement

People who regularly make food at home tend to have many issues when deciding what to cook, especially if they are on a strict diet to gain/lose weight. A lot of the time, the food in the refrigerator might seem too complicated to come up with a dish, so many people end up ordering takeout for the convenience. Because of this, the food in the refrigerator gets left there for many days until the person goes to the grocery store again. Existing applications like Allrecipes and SuperCook are built around posting recipes for other strangers to view. However, these recipes are predetermined and don't focus on what is exactly in your fridge at the moment. This could lead to common missing ingredients like spices and vegetables leaves the user with the job of figuring out which recipes are realistic given what they have on hand. CookBook handles this issue and allow users to not have to consistently return to the grocery store to pick up missing ingredients. It bridges the gap between recipes that are popular and posted online with recipes that the user can actually make with their pantry/fridge ingredients.

# Potential Clients

Home cooks who want to clean out their fridge before going grocery shopping again

Students who cook for themselves and want quick meal-ideas

Busy parents who need to plan meals for the week without spending a lot of time browsing recipes

Workers who came back from a long day and want to make something new without having to innovate themselves

# Proposed Solution

CookBook is a web application where users can post, browse, search, and manage cooking recipes like a typical recipe platform, but it also acts on the ingredients a user actually has. Users can snap a photo of their fridge or pantry (or type a quick list) and CookBook will surface recipes ranked by how few ingredients they're missing. It also learns from what a user views and saves, and uses that to generate a personalized weekly meal plan. Separately, users can upload a photo of a finished dish and CookBook will use computer vision to guess the ingredients and generate a draft recipe, turning a photo into a usable recipe instead of requiring manual entry.

# Functional Requirements

## Must haves:

-As a user, I want to create an account and log in, so that my recipes, saved items, and preferences are tied to me.

-As a user, I want to post a new recipe with a title, ingredients, steps, and recipe type, so that I can share it with other users.

-As a user, I want to update or delete recipes I've posted, so that I can fix mistakes or remove recipes I no longer want public.

-As a user, I want to search and filter recipes by title keywords, ingredients, or recipe type, so that I can quickly find something relevant to what I want to cook.

-As a user, I want to save or favorite recipes, so that I can find them again later without searching.

## Nice to haves:

-As a user, I want to enter or photograph the ingredients I currently have, so that CookBook can show me recipes ranked by fewest missing ingredients (the fridge-to-recipe matcher).

-As a user, I want CookBook to generate a weekly meal plan based on the recipes I've viewed and saved, so that I don't have to plan meals myself from scratch.

-As a user, I want to upload a photo of a dish and have CookBook suggest a recipe (ingredients and steps) from it, so that I can recreate meals I didn't cook myself without manually writing out a recipe.

-As a user, I want to rate and comment on recipes, so that I can share feedback and help other users decide what to cook.

-As a user, I want to filter search results by dietary restriction (e.g. vegetarian, gluten-free), so that I only see recipes that fit my diet.

## Non-functional Requirements:

-Search and filter results should return in under 2 seconds under normal load

-The system should support a growing recipe catalog and user base without needing an architecture rewrite, since search and recommendation features get more useful as the dataset grows.

-The interface should be simple enough that a first-time user can post or search for a recipe without instructions.

-The web-app should have a safety fallback to handle if images/photos don't generate.

-User accounts and any uploaded photos should be protected behind authentication, and users should only be able to edit or delete their own recipes.

# Software Architecture & Technology Stack:

- Frontend: React. I'm most comfortable with it and it is the standard for frontend these days due to the components
- Backend: Node.js with Express. Handles CRUD operations, search/filter logic, and orchestration of the computer vision features for translating fridge images into ingredient count.
- Database: PostgreSQL for structured data (users, recipes, ingredients, saved items) 
- computer vision / AI: Most likely a service/api instead of manually creating a machine learning model
- Hosting: AWS for deployment and object storage


# Similar Apps: 
Allrecipes: A large recipe catalog with search, ratings, and user reviews. CookBook differs by acting on ingredients the user already has rather than only supporting keyword/ingredient search across a static catalog.

SuperCook: An ingredient-based recipe search app where users type in what they have. CookBook differentiates itself with the photo-based ingredient detection and the image-to-recipe feature, which SuperCook does not offer.


