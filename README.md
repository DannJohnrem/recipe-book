# 📖 Recipe Book App — Build Guidelines

**Stack:** Laravel (+ Livewire or Blade) + MySQL (Herd)

---

## 1. Project Setup
- `laravel new recipe-book`
- Configure `.env` + DB connection
- Install Breeze (`composer require laravel/breeze --dev` → `php artisan breeze:install`)
- Pumili ng stack: Livewire o plain Blade

## 2. Data Structure Planning
- `recipes`: title, description, servings, prep_time, cook_time, image_path, user_id
- `ingredients`: name (master list)
- `recipe_ingredients` (pivot): recipe_id, ingredient_id, quantity, unit
- `categories`: name (many-to-many sa recipes)

## 3. Migrations & Models
- Gawin lahat ng migrations
- Relationships:
  - `Recipe belongsTo User`
  - `Recipe belongsToMany Ingredient` (with pivot: `withPivot('quantity', 'unit')`)
  - `Recipe belongsToMany Category`
- `php artisan migrate`

## 4. Seeders & Factories
- RecipeFactory, IngredientFactory, CategoryFactory
- Seed ~20 recipes na may random ingredients

## 5. Basic CRUD (Recipes)
- Index (list/grid view)
- Create/Edit form na may dynamic ingredient rows (add/remove)
- Delete w/ confirmation

## 6. Ingredient & Category Management
- CRUD para sa master list, o "create on the fly" habang gumagawa ng recipe

## 7. Search & Filter
- Search by title
- Filter by category / ingredient
- Practice: query scopes, `whereHas()`

## 8. Recipe Detail Page
- Full recipe view + ingredients w/ quantities
- Optional: scale servings feature (recompute quantities kung 2x servings)

## 9. Image Upload
- Laravel Storage upload
- Validation (type, size)
- Thumbnail sa index, full image sa detail page

## 10. Polish/Extras (optional)
- Favorite/bookmark recipes per user
- Print-friendly view or PDF export (DomPDF)
- Rating system (1-5 stars)

---

## Suggested Session Order
1. Setup + migrations + models
2. Seeders + index view
3. Create/Edit form (dynamic ingredients)
4. Search/filter
5. Detail page + image upload
6. Extras
